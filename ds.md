# 2.数据结构&算法



## 数据结构



### 链表



**链表的基本操作-单链表**

增：在某个结点后面添加

删：删除某个结点后面的结点

查：①根据索引查找值②查找与特定值相等的结点



**链表的基本操作-双向链表**

增：

①在某个结点后面添加 

②在某个结点前面添加(O(1)，单链表需要O(n))



删：

①删除某个结点后面的结点

②删除某个结点(O(1)，单链表需要O(n))



查：

①查找前驱结点(O(1)，单链表需要O(n))

②根据索引查找值

③查找与特定值相等的结点



```c
typedef struct node_s{
    int val;
    struct node_s* next;
} Node;

typedef struct linkedlist_s{
	Node *head;
    Node *tail;
    int size;
} LinkedList;

// 创建空链表
LinkedList* create_list(){
    return (LinkedList*)calloc(1, sizeof(LinkedList));
}

void destroy_list(LinkedList *list){
    // 释放结点空间
    Node *curr = list->head;
    while(curr != NULL){
        Node *next = curr->next;
        free(curr);
        curr = next;
    }
    // 释放LinkedList结构体
    free(list);
}

void add_before_head(LinkedList *list, int val){
	// 创建新结点
    Node* newNode = (Node*)malloc(sizeof(Node));
    newNode->val = val;
    newNode->next = list->head;
    list->head = newNode;
    // 判断链表是否为空
    if(list->tail == NULL){
        list->tail = newNode;
    }
    // 更新size
    list->size++;
}

void add_behind_tail(LinkedList *list, int val){
    // 创建新结点
    Node* newNode = (Node*)malloc(sizeof(Node));
    newNode->val = val;
    newNode->next = NULL;
    
    // 判断链表是否为空
    if(lsit->size == 0){
        list->head = newNode;
        list->tail = newNode;
    } else{
        list->tail->next = newNode;
        list->tail = newNode;
    }
    list->size++;
}

bool remove(LinkedList *list, int val);		// 删除第一个和val相等的结点

int indexOf(LinkedList *list, int val){
    Node *curr = list->head;
    for(int i=0;i<list->size;i++, cur = cur->next){
        if(cur->val == val) return i;
    }
    // 没找到匹配的
    return -1;
}
```





### 栈

后进先出的结构。



**栈的基本操作**

```c
typedef struct node_s{
    int val;
    struct node_s *next;
} Node;

void push(Node **top, int val){	// 为什么用二级指针，因为需要改变的是top指针本身的值(栈顶指针改变)，而不是top指针指向的对象。
    // 创建新结点
    Node *newNode = (Node*)malloc(sizeof(Node));
    
    // 初始化结点
    newNode->val = val;
    
    // 头插法
    newNode->next = *top;
    *top = newNode;
}

int pop(Node **top){
    // 保存原栈顶指针
    Node *old_top = *top;
    int result = old_top->val;
    
    // 更新栈顶指针
    *top = (*top)->next;
    free(old_top);
    return result;
}

bool isEmpty(Node *top){
    return top == NULL;
}

int peek(Node *top){	// 查看栈顶元素的值
    if(isEmpty(top)) exit(1);
    return top->val;
}
```





### 队列

队列是一种操作受限的线性表。

一端插入(队尾)，另一端删除(队头)。FIFO



**作用：**

广度优先遍历

缓存



**队列的基本操作**

```c
// enqueue 入队
// dequeue 出队
// peek 
// isEmpty
// isFull

#define N 100
typedef struct{
	int elements[N];
    int front;
    int rear;
}Queue;

// 创建空队列
Queue* QueueCreate(){
    return (Queue*)calloc(1, sizeof(Queue));
}

void QueueDestory(Queue *q);

void enqueue(Queue *q, int val){
    q->elements[q->rear] = val;
    // 更新rear的值
    q->rear = (q->rear+1) % N;
}

int dequeue(Queue *q){
    int result = q->elements[q->rear];
    q->front = (q->front + 1) % N;
    return result;
}

int peek(Queue *q){
    return q->elements[q->front];
}

bool isEmpty(Queue *q){
    return q->front == q->rear;
}

bool isFull(Queue *q){
    return q->front == (q->rear+1) % N;
}
```



**Q1：为什么用数组实现队列的时候要使用循环数组？**

因为如果固定队头/队尾，那么入队/出队的时间复杂度就是O(n)。

如果队头队尾不固定，那么入队出队操作其实会浪费队列前面的空间。因为一直出队，队头就会一直往后移。

因此这两种方式，要么浪费时间，要么浪费内存空间。

更好的解决方法是用循环数组。



### 哈希表

键值对。

核心底层：**数组 + 链表**，数组里的每一格叫「桶 bucket」

**流程一句话**

1. 拿`key`丢进**哈希函数**，算出一个整数；
2. 对数组长度取模，得到数组下标，找到对应的桶；
3. ✅ 桶空：直接放进去
4. ❌ 桶里已有数据（**哈希冲突**）：挂在这个桶后面的链表上
5. 查询：同样算哈希定位桶，再遍历链表比对 key

**时间复杂度**

- 理想情况（哈希均匀，冲突很少）：查找 / 插入 / 删除 **O(1)**
- 最坏情况（全部冲突挤在一条链表）：退化成链表，O (n)



**Q1：想要查找某个key的value，为什么不直接用数组？**

数组本身有个超级厉害的特性：按下标访问，O (1) 瞬间拿到元素 比如 `arr[5]`，计算机直接跳去第 5 个位置，不需要从头挨个遍历。 

但数组有个致命缺点：下标是数字，我们的 key 不一定是数字。

我们的目标：**把任意类型的 key，变成一个数组下标**，这个转换函数就是【哈希函数】



**Q2：那为什么数组的每个格子（桶 bucket）要挂链表？**

不同的 key，哈希算出来的下标可能一样，也就是哈希冲突。

于是就设计成： 数组每个位置不是存单个数据，而是存**一条链表的头指针**。

这样**同一个下标可以存放多个冲突的 key**，不会覆盖丢失数据。



**Q3：那为什么这个结构查找很快？**

查找分两步：

1. 对查找的 key 做哈希函数 → 取模 → 算出数组下标，**一步定位到对应的桶（O (1)）**
2. 只遍历**这一个桶里面的链表**，挨个比对 key，找到目标

对比两种极端情况：

- 没有冲突：桶里链表只有 1 个元素，找到桶直接拿到，**O(1)**
- 冲突很少：每个桶链表都很短，遍历开销极小，近似 O (1)

对比普通链表查找：普通链表要**从头遍历全部 N 个元素，最坏 O (N)** 对比有序数组二分查找：二分是 O (logN)，比哈希理想情况慢



**哈希表的基本操作**

`V get(K key);`

根据key，获取value。

1. 根据hash函数，找到key的索引

2. 遍历链表，key存在，返回key对应的val(key不存在则返回特殊值)



`V put(K key, V value);`

1. 根据hash函数，找到key的索引
2. 遍历链表，更新key对应的value(key不存在则添加键值对)



`V remove(K key);`

1. 根据hash函数，找到key的索引
2. 遍历链表，key存在则删除结点(kv)



```c
#define N 2043
typedef char* K;
typedef int V;

typedef struct entry_s{
    K key;
    V value;
    struct entry_s* next;
}Entry;

typedef struct{
    Entry* table[N];
}HashMap;

HashMap* HashMapCreate(){
    return (HashMap*)calloc(1,sizeof(HashMap));
}

void HashMapDestroy(HashMap* map){
    // 释放所有结点
    for(int i = 0; i < N; i++){
        Entry *curr = map->table[i];
        while(curr != NULL){
            // 保存后继结点
            Entry *next = curr->next;
            free(curr);
            curr = next;
        }
    }
    // 释放HashMap结构体
    free(map);
}

int hash(char* key);	// 根据key获取索引

V get(K key){
    // 1.根据key获取索引
    int idx = hash(key);
    Entry *curr = map->table[idx];
    // 2.遍历链表
    while(curr != NULL){
        // 判断key是否存在，存在则拿到并返回这个值
        if(strcmp(key, curr->key) == 0){
            return curr->value;
        }
        curr = curr->next;
    }
    // 不存在这样的key
    return -1;
}

V put(K key, V value){
    // 1.根据key获取索引
    int idx = hash(key);
    Entry *curr = map->table[idx];
    // 2.遍历链表
    while(curr != NULL){
        // 判断key是否存在,存在则更新值
        if(strcmp(key, curr->key) == 0){
            V old_value = curr->value;
            curr_value = value;
            return old_value;
        }
        curr = curr->next;
    }
    // 不存在这样的key,添加结点,头插法
    // 创建键值对
    Entry *entry = (Entry*)malloc(sizeof(Entry));
    entry->key = key;
    entry->value = value;
    entry->next = map->table[idx];
    // 更新链表的头结点
    map->table[idx] = entry;
    return -1;
}

V remove(K key){
    // 1.根据key获取索引
    int idx = hash(key);
    Entry *prev = NULL;
    Entry *curr = map->table[idx];
    // 2.遍历链表
    while(curr != NULL){
        // 判断key是否存在，存在则拿到并返回这个值
        if(strcmp(key, curr->key) == 0){
            // 删除结点
            if(prev == NULL){
                map->table[idx] = curr->next;
            } else{
                prev->next = curr->next;
            }
            // 释放空间
            V removeValue = curr->value;
            free(curr);
            return removeValue;
        }
        prev = curr; 
        curr = curr->next;
    }
    // 不存在这样的key
    return -1;
}
```





### 二叉树

**二叉树：**每个结点最多有2个孩子

**叶子结点**：没有孩子的结点/NULL结点(2种说法都有)



#### **二叉树的遍历**

**深度优先遍历**

先序遍历：根-左-右

中序遍历：左-根-右

后序遍历：左-右-根



**广度优先遍历**

层级遍历



#### 二叉树的建树

回想小学学过的三视图的概念：仅凭单个视角的视图是无法确定物体的实际形状的。二叉树也具有类似的性质。

单靠某一种遍历方式的结点排列模式，无法确定树的具体形状。



#### 二叉搜索树(BST)

左子树所有结点的key值都小于根结点的key值

右子树所有结点的key值都大于根结点的key值

并且左右子树都是二叉搜索树



**Q1：如果判断一棵二叉树是不是BST？**

中序

**Q2：二叉搜索树的好处有什么？**

二叉搜索树的查找，插入，删除的时间复杂度是和树的高度相关O(h)

**Q3：如果一棵BST有N个结点，那么它最小的高度是多少？**

完全二叉树。

普通的二叉搜索树的高度不一定是O(logn)这个级别。

平衡二叉搜索树

AVL树：对任意一个结点，它的左子树和右子树的高度相差不超过1

红黑树：能够保证树的高度是O(logn)级别的





#### 红黑树





## 算法



### 二分查找

前提条件：

1. 数据有序
2. 随机访问



```c
// 递归方式
int search(int arr[], int left, int right, int key){
    // 边界条件
    if(left > right) return -1;
    int mid = left + (left - right >> 1); // 防止溢出, 找到中间元素的索引
    if(key < arr[mid])
        return search(arr, left, mid - 1, key);
    else if(key > arr[mid])
        return search(arr, mid + 1, right, key);
    return mid;
}

int binary_search(int arr[], int n, int key){
    return search(arr, 0, n-1, key);
}
```



```c
// 循环方式
int binary_search(int arr[], int n, int key){
    int left = 0, right = n - 1;
    while(left <= right){
        int mid = left + (left - right >> 1); // 防止溢出, 找到中间元素的索引
        if(key < arr[mid])
            right = mid - 1;
        else if(key > arr[mid])
            left = mid + 1;
        else 
            return mid;
    }
    return -1;
}
```



**二分查找的局限性：**

依赖的是顺序表结构，也就是数组。

必须是有序的数据。

不适合动态数据。(动态数据查找适合用哈希表、平衡二叉树)





### 冒泡排序

原理：

1. 比较相邻的元素，如果前一个比后一个大，就交换次序。
2. 对每对相邻元素做同样的工作，从第一对到最后一对。



```c
#define N 10

void bubble_sort(int arr[], int n);

int main(){
    int arr[N] = {5,8,7,1,2,0,4,9,6,3};
}

void bubble_sort(int arr[], int n){
    // i表示冒泡的次数
    for(int i = 1; i < N; i++){
        bool isSorted = true;
        for(int j = 0; j < N - i; j++){
            if(arr[j] > arr[j+1]){
                swap(arr, j, j + 1);
            }
        }
        // 冒泡之后，判断isSorted
        // 如果一次冒泡循环发现一次swap都不需要，说明已经是排序好的了，可以提前结束
        if(isSorted) return;
    }
}
```



**时间复杂度：**

​	最好情况：原数组有序，O(n)

​	最坏情况：原数组逆序，O(n^2)



**空间复杂度：**O(1)，原地排序





### 选择排序

表现最稳定的排序算法之一，因为无论什么数据进去都是O(n^2)的时间复杂度。

**工作原理：**

首先在未排序序列中找到最小(大)元素，存放到排序序列的起始位置。

然后，再从剩余未排序元素中继续寻找最小(大)元素，然后放到排序列表的后面。

以此类推，直到所有元素均排序完毕。

```c
void selection_sort(int arr[], int n){
    for(int i = 1; i < n; i++){
        int minIndex = i - 1;
        for(int j = i; j < N; j++){
            // 更新索引
            if(arr[j] < arr[minIndex]) minIndex = j;
        }
        // 交换 i-1 和minIndex所在位置的元素
        swap(arr, i-1, minIndex);
    }
}
```



**时间复杂度：**

​	比较次数：n(n-1)/2

​	交换次数：n - 1



**空间复杂度：**O(1)，原地排序





### 插入排序

**工作原理：**

1. 把数组分成两部分：【左边有序区】 + 【右边无序区】。

2. 每次取出无序区的第一个元素，把它插入到左边有序区里正确的位置；

3. 不断扩大有序区，直到全部有序。

```c
void insertion_sort(int arr[], int n){
    // i代表无序区第一个元素，arr[0..i-1]有序
	for(int i = 1; i < n; i++){
        int val = arr[i]; // 保存待插入的值
        int j = i - 1;    // 有序区最后一个元素
        while(j >= 0 && arr[j] > val){
            arr[j+1] = arr[j]; // 有序区里大于val的值往后挪
            j--;
        }
        // j == -1 || arr[j] <= val
        arr[j+1] = val;	// 把备份好的val填入空位。
    }
}
```



**时间复杂度：**

最好情况：原数组有序O(n)

​	比较次数：n - 1

​	交换次数：0



最坏情况：原数组逆序O(n^2)

​	比较次数：n(n-1)/2

​	交换次数：n(n-1)/2



**当元素基本有序的时候，性能非常好。**



**空间复杂度：**O(1)，原地排序
