# Algorithms

## 数据结构和算法的分类

算法分类：

硬计算类算法：精确求解
面试、笔试、比赛考察的都是硬计算类的算法

软计算类算法：更注重解决问题，而不是精确求解
神经网络、概率理论、支持向量机、模糊逻辑、进化计算、混沌理论等

数据结构分类：

连续结构

跳转结构

任何一个数据结构一定是这两个结构拼出来的！没有例外！

## 选择、冒泡、插入排序

```java
// 数组中交换i和j位置的数
public static void swap(int[] arr, int i, int j) {
    if (arr == null || arr.length <= 1) {
        return;
    }

    int temp = arr[i];
    arr[i] = arr[j];
    arr[j] = temp;
}
```

**选择排序**：i\~n-1的范围上，找到最小值并放在i位置，然后在i+1\~n-1的范围上继续

```java
public int[] selectionSort(int[] arr) {
    if (arr == null || arr.length <= 1) {
        return arr;
    }

    int n = arr.length;
    for (int i = 0; i < n - 1; i++) {
        // 在i ~ n-1的范围上找到最小值
        int minIndex = i;
        for (int j = i + 1; j < n; j++) {
            if (arr[j] < arr[minIndex]) {
                minIndex = j;
            }
        }
        // 把最小值放在i上
        swap(arr, i, minIndex);
    }

    return arr;
}
```

**冒泡排序**：0\~i范围上，相邻位置较大的数滚下去，最大值来到i，然后在0\~i-1的范围上继续

```java
public int[] bubbleSort(int[] arr) {
    if (arr == null || arr.length <= 1) {
        return arr;
    }

    // 在0 ~ n-1的范围上找到最大值，放在n-1的位置上
    // 然后在0 ~ n-2的范围上找到最大值，放在n-2的位置上
    int n = arr.length;
    for (int i = n - 1; i > 0; i--) {
        for (int j = 0; j < i; j++) {
            if (arr[j] > arr[j + 1]) {
                swap(arr, j, j + 1);
            }
        }
    }

    return arr;
}
```

**插入排序**：0\~i范围上已经有序，新来的数从右到左滑到不再小的位置插入，然后继续

```java
public int[] insertSort(int[] arr) {
    if (arr == null || arr.length <= 1) {
        return arr;
    }

    int n = arr.length;
    for (int i = 1; i < n; i++) {
        // 0 ~ i-1已经有序了
        // 新来的数是[i]
        // 从右向左划入到最小的位置，然后停止
        for (int j = i - 1; j >= 0 && arr[j] > arr[j + 1]; j--) {
            swap(arr, j, j + 1);
        }
    }

    return arr;
}
```

## 对数器

## 二分搜索

```java
public boolean binarySearch(int[] arr, int num) {
    if (arr == null || arr.length == 0) {
        return false;
    }

    int L = 0;
    int R = arr.length - 1;
    int mid = 0;

    while (L <= R) {
        // >>1 表示除以2
        // (R - L) >> 1 等同于 (R - L) / 2 但位运算的速度更快
        // 这样写是为了防止溢出
        mid = L + ((R - L) >> 1);
        if (arr[mid] == num) {
            return true;
        } else if (arr[mid] > num) {
            R = mid - 1;
        } else {
            L = mid + 1;
        }
    }

    return false;
}
```

### 在有序数组arr中判断num是否存在

```java

```

### 在有序数组arr中找>=num的最左位置

```java
 public int findFirstGreaterOrEqual(int[] arr, int num) {
    if (arr == null || arr.length == 0) {
        return -1;
    }

    int L = 0;
    int R = arr.length - 1;
    int mid = 0;
    int index = -1;

    while (L <= R) {
        mid = L + ((R - L) >> 1);
        if (arr[mid] >= num) {
            index = mid;
            R = mid - 1;
        } else {
            L = mid + 1;
        }
    }

    return index;
}
```

### 在有序数组arr中找<=num的最右位置

```java
public int findFirstLessOrEqual(int[] arr, int num) {
    if (arr == null || arr.length == 0) {
        return -1;
    }

    int L = 0;
    int R = arr.length - 1;
    int mid = 0;
    int index = -1;

    while (L <= R) {
        mid = L + ((R - L) >> 1);
        if (arr[mid] <= num) {
            index = mid;
            L = mid + 1;
        } else {
            R = mid - 1;
        }
    }

    return index;
}
```

### 二分搜索不一定发生在有序数组上（比如寻找峰值问题）

>单侧必有/单侧必没有 就可以用二分搜索

```java
public int findPeakElement(int[] arr) {
    if (arr == null || arr.length == 0) {
        return -1;
    }
    if (arr.length == 1) {
        return 0;
    }
    if (arr[0] > arr[1]) {
        return 0;
    }
    if (arr[arr.length - 1] > arr[arr.length - 2]) {
        return arr.length - 1;
    }

    int L = 1;
    int R = arr.length - 2;
    int mid = 0;
    int index = -1;

    while (L <= R) {
        mid = L + ((R - L) >> 1);
        if (arr[mid] > arr[mid - 1] && arr[mid] > arr[mid + 1]) {
            index = mid;
            break;
        } else if (arr[mid] > arr[mid - 1]) {
            L = mid + 1;
        } else {
            R = mid - 1;
        }
    }

    return index;
}
```

## 时间复杂度 && 空间复杂度

基础概念：

时间复杂度是一个函数，用来描述算法的运行时间和数据量大小的关系  
是一个和数据量有关、只要高阶，不要低阶和常数的操作次数表达式  
不要低阶和常数是因为当数据量很大的时候，高阶项的影响要大的多

在严格固定流程的算法中，强调最差情况  
在用随机流程作为重要部分的算法中，要看平均或者期望情况，最差情况没有意义

1. O(1): 常数时间复杂度。无论输入的规模如何，执行时间都保持不变。例如，访问数组的元素。  
2. O(log n): 对数时间复杂度。每次操作都会减少输入的规模。例如，二分查找。  
3. O(n log n): 线性对数时间复杂度。例如，快速排序和归并排序。  
4. O(n): 线性时间复杂度。执行时间与输入的规模n成正比。例如，遍历一个数组。  
5. O(n²): 平方时间复杂度。执行时间与输入的规模n的平方成正比。例如，嵌套循环遍历二维数组。  
6. O(2^n), O(n!): 指数时间复杂度和阶乘时间复杂度。这些复杂度的算法通常在输入规模稍大时就无法在合理时间内完成。例如，旅行商问题的暴力解法。

空间复杂度也是一个函数，用来描述算法运行时额外需要的内存空间和数据量大小的关系

1. O(1): 常数空间复杂度。无论输入的规模如何，所需的存储空间都保持不变。例如，交换两个变量的值。  
2. O(n): 线性空间复杂度。所需的存储空间与输入的规模n成正比。例如，创建一个长度为n的数组。  
3. O(n²): 平方空间复杂度。所需的存储空间与输入的规模n的平方成正比。例如，创建一个n*n的二维数组。

>最优解：先满足时间复杂度，然后尽量少用空间

扩展知识：

1. 时间复杂度的均摊：主要用于一些特殊的数据结构，如：动态数组、并查集、单调队列、单调栈、哈希表等  
在这些数据结构中，有些操作可能导致较高的时间复杂度，但是发生频率很低，所以将时间复杂度均摊到其他时间复杂度上，从而得到一个平均的时间复杂度  

2. 不要用代码结构来判断时间复杂度，一个while也可以实现冒泡排序，有些算法使用了多层嵌套循环，但是时间复杂度为O(N)

```java
public int[] bubbleSort(int[] arr) {
    if (arr == null || arr.length <= 1) {
        return arr;
    }

    int i = 0;
    int n = arr.length;
    while (0 < n - 1) {
        if (arr[i] > arr[i + 1]) {
            swap(arr, i, i + 1);
        }

        if (i < n - 1) {
            i++;
        } else {
            i = 0;
            n--;
        }
    }

    return arr;
}

public void testTimeComplexity() {
    int n = 100000;

    long start = System.currentTimeMillis();
    for (int i = 1; i <= n; i++) {
        for (int j = 1; j <= n; j += i) {

        }
    }
    long end = System.currentTimeMillis();
    System.out.println("O(nlogN)的时间复杂度: " + (end - start) + "ms");

    start = System.currentTimeMillis();
    for (int i = 1; i <= n; i++) {
        for (int j = 1; j <= n; j ++) {

        }
    }
    end = System.currentTimeMillis();
    System.out.println("O(N^2)的时间复杂度: " + (end - start) + "ms");
}
```

## 链表

### 单列表、双列表及其反转

1. 按值传递、按引用传递
    值传递：在调用函数时将实际参数复制一份传递到函数中，这样函数中如果对参数进行修改，将不会影响到实际参数  
    引用传递：在调用函数时将实际参数的内存地址直接传递到函数中，那么函数中对参数的修改，将直接影响到实际的参数

2. 单链表、双链表的定义
    单链表：由一系列节点组成，每个节点包含一个指向下一个节点的指针和一个值  
    双链表：由一系列节点组成，每个节点包含一个指向下一个节点的指针、一个指向上一个节点的指针和一个值

链表：

```java
    public static class ListNode {
        int val;
        ListNode next;

        ListNode() {
        }

        ListNode(int x) {
            val = x;
        }

        public ListNode(int val, ListNode next) {
            this.val = val;
            this.next = next;
        }

        @Override
        public String toString() {
            StringBuilder sb = new StringBuilder();
            ListNode current = this;
            while (current != null) {
                sb.append(current.val);
                current = current.next;
                if (current != null) {
                    sb.append(" -> ");
                }
            }
            return sb.toString();
        }
    }

    public static ListNode createListNode(int[] arr) {
        if (arr == null || arr.length == 0) {
            return null;
        }
        ListNode head = new ListNode(arr[0]);
        ListNode current = head;
        for (int i = 1; i < arr.length; i++) {
            current.next = new ListNode(arr[i]);
            current = current.next;
        }
        return head;
    }

    public static class DoubleListNode {
        int val;
        DoubleListNode next;
        DoubleListNode prev;

        DoubleListNode(int x) {
            val = x;
        }

        public DoubleListNode(int val, DoubleListNode next, DoubleListNode prev) {
            this.val = val;
            this.next = next;
            this.prev = prev;
        }
    }
```

反转单链表：

```java
    public static ListNode reverseList(ListNode head) {
        ListNode prev = null;
        ListNode next = null;

        while (head != null) {
            next = head.next;
            head.next = prev;
            prev = head;
            head = next;
        }

        return prev;
    }
```

反转双链表：

```java
    public static DoubleListNode reverseDoubleList(DoubleListNode head) {
        DoubleListNode prev = null;
        DoubleListNode next = null;

        while (head != null) {
            next = head.next;
            head.next = prev;
            head.prev = next;
            prev = head;
            head = next;
        }

        return prev;
    }
```

### 将两个升序链表合并为一个新的 **升序** 链表并返回

```java
     public static ListNode mergeTwoLists(ListNode head1, ListNode head2) {
        if (head1 == null && head2 == null) {
            return null;
        } else if (head1 == null) {
            return head2;
        } else if (head2 == null) {
            return head1;
        }


        // 第一个值小的做头
        // prev表示已经排序号的最后一个节点
        ListNode head = head1.val <= head2.val ? head1 : head2;
        ListNode cur1 = head.next;
        ListNode cur2 = head == head1 ? head2 : head1;
        ListNode prev = head;

        while (cur1 != null && cur2 != null) {
            if (cur1.val <= cur2.val) {
                prev.next = cur1;
                cur1 = cur1.next;
            } else {
                prev.next = cur2;
                cur2 = cur2.next;
            }
            prev = prev.next;
        }
        prev.next = cur1 != null ? cur1 : cur2;
        return head;
    }
```

### 两个链表相加

```java
    public static ListNode addTwoNumber(ListNode head1, ListNode head2) {
        ListNode ans = null, cur = null;
        int carry = 0;
        for (int sum, val; head1 != null || head2 != null; head1 = head1 == null ? null : head1.next, head2 = head2 == null ? null : head2.next) {
            sum = (head1 == null ? 0 : head1.val) + (head2 == null ? 0 : head2.val) + carry;

            val = sum % 10;
            carry = sum / 10;

            if (ans == null) {
                ans = new ListNode(val);
                cur = ans;
            } else {
                cur.next = new ListNode(val);
                cur = cur.next;
            }
        }
        if (carry == 1) {
            cur.next = new ListNode(1);
        }
        return ans;
    }
```

### 划分链表

```java
    public static ListNode partition(ListNode head, int x) {
        ListNode leftHead = null, leftTail = null;
        ListNode rightHead = null, rightTail = null;
        ListNode next = null;
        while (head != null) {
            next = head.next;
            head.next = null;
            if (head.val < x) {
                if (leftHead == null) {
                    leftHead = head;
                } else {
                    leftTail.next = head;
                }
                leftTail = head;
            } else {
                if (rightHead == null) {
                    rightHead = head;
                } else {
                    rightTail.next = head;
                }
                rightTail = head;
            }
            head = next;
        }

        if (leftHead == null) {
            return rightHead;
        }
        leftTail.next = rightHead;
        return leftHead;
    }
```

## 队列、栈

### 队列的介绍

队列是一种线性数据结构，它遵循FIFO（First In First Out，先进先出）的原则。这意味着第一个被添加到队列中的元素将是第一个被移除的元素。队列的主要操作包括offer（或enqueue，添加元素到队尾）和poll（或dequeue，移除队头元素）

### 栈的介绍

栈是一种特殊的线性数据结构，它遵循LIFO（Last In First Out，后进先出）的原则。这意味着最后一个被添加到栈中的元素将是第一个被移除的元素。栈的主要操作包括push（添加元素到栈顶）和pop（移除栈顶元素）

### 队列的链表实现和数组实现

队列的链表实现:

```java
    // 直接用Java内部的实现
    // LinedList是双向链表，常数操作慢
    // 单链表就能实现队列
    public static class Queue1 {

        public Queue<Integer> queue = new LinkedList<>();

        // 调用任何方法之前，线判断链表是否为空
        public boolean isEmpty() {
            return queue.isEmpty();
        }

        // 添加元素到尾部
        public void offer(int num) {
            queue.offer(num);
        }

        // 返回头部元素
        public int poll() {
            return queue.poll();
        }

        // 返回头部元素，但是不弹出
        public int peek() {
            return queue.peek();
        }

        // 放回当前队列中有几个数
        public int size() {
            return queue.size();
        }
    }
```

队列的数组实现：

```java
    // 实际刷题时更常见的写法，常数时间好
    // 如果可以确定加入操作的总次数不超过n，那么可以用
    // 一般笔试、面试都有一个明确的数据量，所以这是最常用的方式
    public static class Queue2 {
        public int[] queue;
        public int l;
        public int r;

        public Queue2(int n) {
            queue = new int[n];
            l = 0;
            r = 0;
        }

        public boolean isEmpty() {
            return l == r;
        }

        public void offer(int num) {
            queue[r++] = num;
        }

        public int poll() {
            return queue[l++];
        }

        public int head() {
            return queue[l];
        }

        public int tail() {
            return queue[r - 1];
        }

        public int size() {
            return r - l;
        }
    }
```

### 栈的数组实现

栈的java内部实现和数组实现：

```java
    // 直接调用Java内部的实现
    // 底层是动态数组，所以是常数时间不好
    public static class Stack1 {
        Stack<Integer> stack = new Stack<>();

        // 调用任何方法之前，线判断栈是否为空
        public boolean isEmpty() {
            return stack.isEmpty();
        }

        // 添加元素到栈顶
        public void push(int num) {
            stack.push(num);
        }

        // 返回栈顶元素并弹出
        public int pop() {
            return stack.pop();
        }

        // 返回栈顶元素但是不弹出
        public int peek() {
            return stack.peek();
        }

        // 返回当前栈中有几个数
        public int size() {
            return stack.size();
        }
    }

    // 实际刷题时更常见的写法，常数时间好
    // 如果可以保证同时在栈里的元素个数不超过n，那么可以用
    // 也就是发生弹出操作之后，空间可以复用
    // 一般笔试、面试都有一个明确的数据量，所以这是最常用的方式
    public static class Stack2 {
        public int[] stack;
        public int size;

        public Stack2(int n) {
            stack = new int[n];
        }

        public void push(int num) {
            stack[size++] = num;
        }

        public int pop() {
            return stack[--size];
        }

        public int peek() {
            return stack[size - 1];
        }

        public int size() {
            return size;
        }
    }
```

### 环形队列用数组实现

设计一个环形队列：

```java
    // 设计循环队列
    public static class MyCircularQueue {
        public int[] queue;
        public int l, r, size, limit;

        public MyCircularQueue(int n) {
            queue = new int[n];
            l = 0;
            r = 0;
            size = 0;
            limit = n;
        }

        public boolean enQueue(int value) {
            if (isFull()) {
                return false;
            }
            queue[r] = value;
            r = r == limit - 1 ? 0 : (r + 1);
            size++;
            return true;
        }

        public boolean deQueue() {
            if (isEmpty()) {
                return false;
            }
            l = l == limit - 1 ? 0 : (l + 1);
            size--;
            return true;
        }

        public int Front() {
            if (isEmpty()) {
                return -1;
            }
            return queue[l];
        }

        public int Rear() {
            if (isEmpty()) {
                return -1;
            }
            return r == 0 ? queue[limit - 1] : queue[r - 1];
        }

        public boolean isEmpty() {
            return size == 0;
        }

        public boolean isFull() {
            return size == limit;
        }
    }
```

### 栈和队列的相互实现

用两个栈实现队列：

```java
    // 用两个栈实现队列
    // 测试链接：https://leetcode.cn/problems/implement-queue-using-stacks/
    public static class MyQueue {
        public Stack<Integer> stack1;
        public Stack<Integer> stack2;

        public MyQueue() {
            stack1 = new Stack<>();
            stack2 = new Stack<>();
        }

        // 倒数据
        // 从in栈 把数据倒入out栈
        // 两个原则：
        // 1.out空了，才能倒数据
        // 2.如果倒数据，in必须倒完
        public void pushToPop() {
            if (stack2.isEmpty()) {
                while (!stack1.isEmpty()) {
                    stack2.push(stack1.pop());
                }
            }
        }

        public void push(int x) {
            stack1.push(x);
            pushToPop();
        }

        public int pop() {
            pushToPop();
            return stack2.pop();
        }

        public int peek() {
            pushToPop();
            return stack2.peek();
        }

        public boolean empty() {
            return stack1.isEmpty() && stack2.isEmpty();
        }
    }
```

用队列实现栈：

```java
    // 用队列实现栈
    // 测试链接：https://leetcode.cn/problems/implement-stack-using-queues/
    public static class MyStack {

        public Queue<Integer> queue;

        public MyStack() {
            queue = new LinkedList<>();
        }

        public void push(int x) {
            int size = queue.size();
            queue.offer(x);
            for (int i = 0; i < size; i++) {
                queue.offer(queue.poll());
            }
        }

        public int pop() {
            return queue.poll();
        }

        public int top() {
            return queue.peek();
        }

        public boolean empty() {
            return queue.isEmpty();
        }
    }
```

### 最小栈

最小栈实现1：

```java
    // 最小栈-实现1
    // 测试链接：https://leetcode.cn/problems/bao-han-minhan-shu-de-zhan-lcof
    public static class MinStack1 {

        public Stack<Integer> dataStack;
        public Stack<Integer> minStack;

        public MinStack1() {
            dataStack = new Stack<>();
            minStack = new Stack<>();
        }

        public void push(int x) {
            dataStack.push(x);
            if (minStack.isEmpty() || x <= minStack.peek()) {
                minStack.push(x);
            } else {
                minStack.push(minStack.peek());
            }
        }

        public void pop() {
            dataStack.pop();
            minStack.pop();
        }

        public int top() {
            return dataStack.peek();
        }

        public int getMin() {
            return minStack.peek();
        }
    }
```

最小栈实现2：

```java
    // 最小栈-实现2
    // 测试链接：https://leetcode.cn/problems/bao-han-minhan-shu-de-zhan-lcof
    public static class MinStack2 {

        public int[] dataStack;
        public int[] minStack;
        public int MAXSIZE = 8001;
        public int size;

        public MinStack2() {
            dataStack = new int[MAXSIZE];
            minStack = new int[MAXSIZE];
            size = 0;
        }

        public void push(int x) {
            dataStack[size] = x;
            if (size == 0) {
                minStack[size] = x;
            } else {
                minStack[size] = Math.min(minStack[size - 1], x);
            }
            size++;
        }

        public void pop() {
            size--;
        }

        public int top() {
            return dataStack[size - 1];
        }

        public int getMin() {
            return minStack[size - 1];
        }
    }
```

### 双端队列

双端队列-链表实现：

```java
    // 双端队列-链表实现
    public static class MyCircularDeque1 {
        public Deque<Integer> deque = new LinkedList<>();
        public int size;
        public int limit;

        public MyCircularDeque1(int k) {
            size = 0;
            limit = k;
        }

        public boolean insertFront(int value) {
            if (isFull()) {
                return false;
            } else {
                deque.offerFirst(value);
                size++;
                return true;
            }
        }

        public boolean insertLast(int value) {
            if (isFull()) {
                return false;
            } else {
                deque.offerLast(value);
                size++;
                return true;
            }
        }

        public boolean deleteFront() {
            if (isEmpty()) {
                return false;
            } else {
                size--;
                deque.pollFirst();
                return true;
            }
        }

        public boolean deleteLast() {
            if (isEmpty()) {
                return false;
            } else {
                size--;
                deque.pollLast();
                return true;
            }
        }

        public int getFront() {
            if (isEmpty()) {
                return -1;
            } else {
                return deque.peekFirst();
            }
        }

        public int getRear() {
            if (isEmpty()) {
                return -1;
            } else {
                return deque.peekLast();
            }
        }

        public boolean isEmpty() {
            return size == 0;
        }

        public boolean isFull() {
            return size == limit;
        }
    }
```

双端队列-数组实现:

```java
    // 双端队列-数组实现
    public static class MyCircularDeque2 {
        public int[] deque;
        public int l, r, size, limit;

        public MyCircularDeque2(int k) {
            deque = new int[k];
            l = r = size = 0;
            limit = k;
        }

        public boolean insertFront(int value) {
            if (isFull()) {
                return false;
            } else {
                if (isEmpty()) {
                    l = r = 0;
                    deque[0] = value;
                } else {
                    l = l == 0 ? (limit - 1) : (l - 1);
                    deque[l] = value;
                }
                size++;
                return true;
            }
        }

        public boolean insertLast(int value) {
            if (isFull()) {
                return false;
            } else {
                if (isEmpty()) {
                    l = r = 0;
                    deque[0] = value;
                } else {
                    r = r == limit - 1 ? 0 : (r + 1);
                    deque[r] = value;
                }
                size++;
                return true;
            }
        }

        public boolean deleteFront() {
            if (isEmpty()) {
                return false;
            } else {
                l = (l == limit - 1) ? 0 : (l + 1);
                size--;
                return true;
            }
        }

        public boolean deleteLast() {
            if (isEmpty()) {
                return false;
            } else {
                r = r == 0 ? (limit - 1) : (r - 1);
                size--;
                return true;
            }
        }

        public int getFront() {
            if (isEmpty()) {
                return -1;
            } else {
                return deque[l];
            }
        }

        public int getRear() {
            if (isEmpty()) {
                return -1;
            } else {
                return deque[r];
            }
        }

        public boolean isEmpty() {
            return size == 0;
        }

        public boolean isFull() {
            return size == limit;
        }
    }
```

## 二叉树

二叉树：

```java
    public static class TreeNode {
        int val;
        TreeNode left;
        TreeNode right;

        TreeNode() {
        }

        TreeNode(int val) {
            this.val = val;
        }

        TreeNode(int val, TreeNode left, TreeNode right) {
            this.val = val;
            this.left = left;
            this.right = right;
        }
    }
```

### 二叉树的先序、中序、后序遍历(递归实现)

递归：

```java
    public static void f(TreeNode f) {
        if (f == null) {
            return;
        }
        // 1
        f(f.left);
        // 2
        f(f.right);
        // 3
    }
```

先序遍历：

```java
    // 先序遍历 递归序
    public static void preOrder(TreeNode head) {
        if (head == null) {
            return;
        }

        System.out.println(head.val);
        preOrder(head.left);
        preOrder(head.right);
    }
```

中序遍历：

```java
    // 中序遍历 递归序
    public static void inOrder(TreeNode head) {
        if (head == null) {
            return;
        }

        preOrder(head.left);
        System.out.println(head.val);
        preOrder(head.right);
    }
```

后序遍历：

```java
    // 后序遍历 递归序
    public static void postOrder(TreeNode head) {
        if (head == null) {
            return;
        }

        preOrder(head.left);
        preOrder(head.right);
        System.out.println(head.val);
    }
```

### 二叉树遍历的非递归实现和复杂度分析

用栈实现二叉树的先序遍历

```java
    // 用栈实现先序遍历
    // https://leetcode.cn/problems/binary-tree-preorder-traversal/
    public static void preOrder(TreeNode head) {
        if (head != null) {
            Stack<TreeNode> stack = new Stack<>();
            stack.push(head);
            while (!stack.isEmpty()) {
                head = stack.pop();
                System.out.println(head.val);
                if (head.right != null) {
                    stack.push(head.right);
                }
                if (head.left != null) {
                    stack.push(head.left);
                }
            }
        }
    }
```

用栈实现二叉树的中序遍历

```java
    // 用栈实现中序遍历
    // https://leetcode.cn/problems/binary-tree-inorder-traversal/
    public static void inOrder(TreeNode head) {
        if (head != null) {
            Stack<TreeNode> stack = new Stack<>();
            while (!stack.isEmpty() || head != null) {
                if (head != null) {
                    stack.push(head);
                    head = head.left;
                } else {
                    head = stack.pop();
                    System.out.println(head.val);
                    head = head.right;
                }
            }
            System.out.println();
        }
    }
```

用一个栈实现二叉树的后序遍历

```java
    // 用一个栈实现后序遍历
    // https://leetcode.cn/problems/binary-tree-postorder-traversal/
    public static void postOrderOneStack(TreeNode head) {
        if (head != null) {
            Stack<TreeNode> stack = new Stack<>();
            stack.push(head);
            while(!stack.isEmpty()) {
                TreeNode curr = stack.peek();
                if (curr.left != null && head != curr.left && head != curr.right) {
                    stack.push(curr.left);
                } else if (curr.right != null && head != curr.right) {
                    stack.push(curr.right);
                } else {
                    System.out.println(curr.val);
                    head = stack.pop();
                }
            }
        }
    }
```

用两个栈实现二叉树的后序遍历

```java
    // 用两个栈实现后序遍历
    // https://leetcode.cn/problems/binary-tree-postorder-traversal/
    public static void postOrderTwoStack(TreeNode head) {
        if (head != null) {
            Stack<TreeNode> stack = new Stack<>();
            Stack<TreeNode> collect = new Stack<>();
            stack.push(head);
            while (!stack.isEmpty()) {
                head = stack.pop();
                collect.push(head);
                if (head.left != null) {
                    stack.push(head.left);
                }
                if (head.right != null) {
                    stack.push(head.right);
                }
            }
            while (!collect.isEmpty()) {
                System.out.println(collect.pop().val);
            }
        }
    }
```

遍历二叉树复杂度分析

- 时间复杂度O(n)，递归和非递归都是每个节点遇到有限次，所以是O(n)
- 额外空间复杂度O(h)，递归和非递归都需要二叉树高度h的空间来保存路径
- 存在时间复杂度为O(n)，空间复杂度为O(1)的遍历：Morris遍历

## 算法笔试处理输入输出

常见的笔试风格：

1. 填函数风格(leetcode)
2. acm风格(笔试、比赛最常见)

    - 规定数据量用BufferedReader、StreamTokenizer、PrintWriter
    - 按行读用BufferedReader、PrintWriter，读取之后手动拆分
    - 不要用Scanner、System.out,IO效率慢

3. 不推荐：临时动态空间
4. 推荐：全局静态空间

填函数风格:

```java
// 展示填函数风格的测试方式
// 子矩阵的最大累加和问题，不要求会解题思路，后面的课会讲
// 测试链接 : https://www.nowcoder.com/practice/840eee05dccd4ffd8f9433ce8085946b
public class Code01_FillFunction {

    public int sumOfSubMatrix(int[][] mat, int n) {
        return maxSumSubmatrix(mat, n, n);
    }

    // 求子矩阵的最大累加和，后面的课会讲
    public static int maxSumSubmatrix(int[][] mat, int n, int m) {
        int max = Integer.MIN_VALUE;
        for (int i = 0; i < n; i++) {
            // 需要的辅助数组，临时动态生成就可以
            int[] arr = new int[m];
            for (int j = i; j < n; j++) {
                for (int k = 0; k < m; k++) {
                    arr[k] += mat[j][k];
                }
                max = Math.max(max, maxSumSubarray(arr, m));
            }
        }
        return max;
    }

    // 求子数组的最大累加和，后面的课会讲
    public static int maxSumSubarray(int[] arr, int m) {
        int max = Integer.MIN_VALUE;
        int cur = 0;
        for (int i = 0; i < m; i++) {
            cur += arr[i];
            max = Math.max(max, cur);
            cur = cur < 0 ? 0 : cur;
        }
        return max;
    }

}
```

规定数据量:

```java
// 展示acm风格的测试方式
// 子矩阵的最大累加和问题，不要求会解题思路，后面的课会讲
// 每一组测试都给定数据规模
// 需要任何空间都动态生成，在大厂笔试或者比赛中，这种方式并不推荐
// 测试链接 : https://www.nowcoder.com/practice/cb82a97dcd0d48a7b1f4ee917e2c0409?
// 请同学们务必参考如下代码中关于输入、输出的处理
// 这是输入输出处理效率很高的写法
// 提交以下的code，提交时请把类名改成"Main"，可以直接通过

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.io.PrintWriter;
import java.io.StreamTokenizer;

public class Code02_SpecifyAmount {

    public static void main(String[] args) throws IOException {
        // 把文件里的内容，load进来，保存在内存里，很高效，很经济，托管的很好
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        // 一个一个读数字
        StreamTokenizer in = new StreamTokenizer(br);
        // 提交答案的时候用的，也是一个内存托管区
        PrintWriter out = new PrintWriter(new OutputStreamWriter(System.out));
        while (in.nextToken() != StreamTokenizer.TT_EOF) { // 文件没有结束就继续
            // n，二维数组的行
            int n = (int) in.nval;
            in.nextToken();
            // m，二维数组的列
            int m = (int) in.nval;
            // 装数字的矩阵，临时动态生成
            int[][] mat = new int[n][m];
            for (int i = 0; i < n; i++) {
                for (int j = 0; j < m; j++) {
                    in.nextToken();
                    mat[i][j] = (int) in.nval;
                }
            }
            out.println(maxSumSubmatrix(mat, n, m));
        }
        out.flush();
        br.close();
        out.close();
    }

    // 求子矩阵的最大累加和，后面的课会讲
    public static int maxSumSubmatrix(int[][] mat, int n, int m) {
        int max = Integer.MIN_VALUE;
        for (int i = 0; i < n; i++) {
            // 需要的辅助数组，临时动态生成
            int[] arr = new int[m];
            for (int j = i; j < n; j++) {
                for (int k = 0; k < m; k++) {
                    arr[k] += mat[j][k];
                }
                max = Math.max(max, maxSumSubarray(arr, m));
            }
        }
        return max;
    }

    // 求子数组的最大累加和，后面的课会讲
    public static int maxSumSubarray(int[] arr, int m) {
        int max = Integer.MIN_VALUE;
        int cur = 0;
        for (int i = 0; i < m; i++) {
            cur += arr[i];
            max = Math.max(max, cur);
            cur = cur < 0 ? 0 : cur;
        }
        return max;
    }

}
```

按行读:

```java
// 展示acm风格的测试方式
// 测试链接 : https://www.nowcoder.com/exam/test/70070648/detail?pid=27976983
// 其中，7.A+B(7)，就是一个没有给定数据规模，只能按行读数据的例子
// 此时需要自己切分出数据来计算
// 请同学们务必参考如下代码中关于输入、输出的处理
// 这是输入输出处理效率很高的写法
// 提交以下的code，提交时请把类名改成"Main"，可以直接通过

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.io.PrintWriter;

public class Code04_ReadByLine {

    public static String line;

    public static String[] parts;

    public static int sum;

    public static void main(String[] args) throws IOException {
        BufferedReader in = new BufferedReader(new InputStreamReader(System.in));
        PrintWriter out = new PrintWriter(new OutputStreamWriter(System.out));
        while ((line = in.readLine()) != null) {
            parts = line.split(" ");
            sum = 0;
            for (String num : parts) {
                sum += Integer.valueOf(num);
            }
            out.println(sum);
        }
        out.flush();
        in.close();
        out.close();
    }

}

```

全局静态空间:

```java
// 展示acm风格的测试方式
// 子矩阵的最大累加和问题，不要求会解题思路，后面的课会讲
// 每一组测试都给定数据规模
// 任何空间都提前生成好，一律都是静态空间，然后自己去复用，推荐这种方式
// 测试链接 : https://www.nowcoder.com/practice/cb82a97dcd0d48a7b1f4ee917e2c0409?
// 请同学们务必参考如下代码中关于输入、输出的处理
// 这是输入输出处理效率很高的写法
// 提交以下的code，提交时请把类名改成"Main"，可以直接通过

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.io.PrintWriter;
import java.io.StreamTokenizer;
import java.util.Arrays;

public class Code03_StaticSpace {

    // 题目给定的行的最大数据量
    public static int MAXN = 201;

    // 题目给定的列的最大数据量
    public static int MAXM = 201;

    // 申请这么大的矩阵空间，一定够用了
    // 静态的空间，不停复用
    public static int[][] mat = new int[MAXN][MAXM];

    // 需要的所有辅助空间也提前生成
    // 静态的空间，不停复用
    public static int[] arr = new int[MAXM];

    // 当前测试数据行的数量是n
    // 当前测试数据列的数量是m
    // 这两个变量可以把代码运行的边界规定下来
    public static int n, m;

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StreamTokenizer in = new StreamTokenizer(br);
        PrintWriter out = new PrintWriter(new OutputStreamWriter(System.out));
        while (in.nextToken() != StreamTokenizer.TT_EOF) {
            n = (int) in.nval;
            in.nextToken();
            m = (int) in.nval;
            for (int i = 0; i < n; i++) {
                for (int j = 0; j < m; j++) {
                    in.nextToken();
                    mat[i][j] = (int) in.nval;
                }
            }
            out.println(maxSumSubmatrix());
        }
        out.flush();
        br.close();
        out.close();
    }

    // 求子矩阵的最大累加和，后面的课会讲
    public static int maxSumSubmatrix() {
        int max = Integer.MIN_VALUE;
        for (int i = 0; i < n; i++) {
            // 因为之前的过程可能用过辅助数组
            // 为了让之前结果不干扰到这次运行，需要自己清空辅助数组需要用到的部分
            Arrays.fill(arr, 0, m, 0);
            for (int j = i; j < n; j++) {
                for (int k = 0; k < m; k++) {
                    arr[k] += mat[j][k];
                }
                max = Math.max(max, maxSumSubarray());
            }
        }
        return max;
    }

    // 求子数组的最大累加和，后面的课会讲
    public static int maxSumSubarray() {
        int max = Integer.MIN_VALUE;
        int cur = 0;
        for (int i = 0; i < m; i++) {
            cur += arr[i];
            max = Math.max(max, cur);
            cur = cur < 0 ? 0 : cur;
        }
        return max;
    }

}
```

## 递归及master公式

### 递归

1. 从思想上理解递归：通过画调用图，有助于分析递归
2. 从实际上理解递归：递归底层通过系统栈实现
3. 任何递归都一定可以改成非递归，不用系统栈，自己压栈
4. 递归改成非递归的必要性：
    - 在实际生产中几乎一定要改，除非确定数据量再大，递归也不一定深，例如：归并排序、快速排序、线段树、很多的平衡树
    - 在算法笔试或者比赛中，能通过就不用改

```java
    public static void main(String[] args) {
        int[] arr = {3, 8, 7, 6, 4, 5, 1, 2};
        System.out.println("数组最大值 : " + maxValue(arr));
    }

    public static int maxValue(int[] arr) {
        return f(arr, 0, arr.length - 1);
    }

    // 递归算法
    // 获取arr[l....r]范围上的最大值
    public static int f(int[] arr, int l, int r) {
        if (l == r) {
            return arr[l];
        }
        int m = (l + r) / 2;
        int lmax = f(arr, l, m);
        int rmax = f(arr, m + 1, r);
        return Math.max(lmax, rmax);
    }
```

### master公式

master公式是用来估算递归算法的复杂度的公式

T(n) = a*T(n/b) + T(n^c)  
a,b,c都是常数

- 所有子问题规模相同的递归才能用master公式
- 如果log(b, a) > c,复杂度为O(N^log(b, a))
- 如果log(b, a) < c,复杂度为O(N^c)
- 如果log(b, a) = c,复杂度为O(N^c * logN)

_一个补充:_ T(n) = 2\*T(n/2) + T(n\*logn) 时间复杂度是O(N*((logN)^2))  

以下面这个递归算法为例：

```java
    // 获取arr[l....r]范围上的最大值
    public static int f(int[] arr, int l, int r) {
        if (l == r) {
            return arr[l];
        }
        int m = (l + r) / 2;
        int lmax = f(arr, l, m);
        int rmax = f(arr, m + 1, r);
        return Math.max(lmax, rmax);
    }
```

T(n) = T(n/2) + T(n/2) + T(1)  =>  T(n) = 2*T(n/2) + T(1)  
其中 a = 2; b = 2; c = 0  
因为 log (b, a) = log (2, 2) = 1 > c  
所以这个递归算法的时间复杂度是O(N)，和通过遍历获取最大值的算法的复杂度一样

如果在上面这个递归算法返回结果之前打印所有数组元素：

```java
    // 获取arr[l....r]范围上的最大值
    public static int f(int[] arr, int l, int r) {
        if (l == r) {
            return arr[l];
        }
        int m = (l + r) / 2;
        int lmax = f(arr, l, m);
        int rmax = f(arr, m + 1, r);
        for (int j : arr) {
            System.out.println("i = " + j);
        }
        return Math.max(lmax, rmax);
    }
```

那么最终的master公式就会变成： T(n) = 2\*T(n/2) + T(n)  
其中 a = 2; b = 2; c = 1  
因此 log (b, a) =  c = 1  
所以这个递归算法的时间复杂度是O(N*logN)

## 归并排序

- 左部分排好序、右部分排好序，利用merge过程使整体有序
- merge过程：谁小就拷贝谁，直到两边的数字耗尽，将剩下的部分拷贝回原数组
- 有递归实现和非递归实现
- 时间复杂度是：O(N * logN)，通过master公式算出
- 额外空间复杂度是：O(N)，因为需要辅助数组帮助完成merge过程
- 递归排序的时间复杂度优于O(N^2)是因为比较的行为没有被浪费
- 原地归并排序可以把额外空间复杂度变为O(1)，但是时间复杂度会变成O(N^2)，所以原地归并排序没有必要

```java

// 归并排序，填函数练习风格
// 测试链接 : https://leetcode.cn/problems/sort-an-array/

public class MergeSort2 {

    public static int MAX_LENGTH = 50001;
    public static int[] help = new int[MAX_LENGTH];

    public static int[] sortArray(int[] nums) {
        if (nums.length > 1) {
            // mergeSort1为非递归方法
            // mergeSort2为递归方法
            // 用哪个都可以
            // mergeSort1(nums);
            mergeSort2(nums);
        }
        return nums;
    }


    // 归并排序非递归版
    // 时间复杂度O(n * log n)
    // 空间复杂度O(n)
    public static void mergeSort1(int[] arr) {
        // 一共发生O(log n)次
        for (int l, m, r, step = 1; step < arr.length; step <<= 1) {
            // 内部分组merge，时间复杂度O(n)
            l = 0;
            while (l < arr.length) {
                m = l + step - 1;
                if (m + 1 > arr.length) {
                    break;
                }
                r = Math.min(l + (step << 1) - 1, arr.length - 1);
                merge(arr, l, m, r);
                l = r + 1;
            }
        }
    }

    // 归并排序递归版
    // 假设l...r一共n个数
    // T(n) = 2 * T(n/2) + O(n)
    // a = 2, b = 2, c = 1
    // 根据master公式，时间复杂度O(n * log n)
    // 空间复杂度O(n)
    public static void mergeSort2(int[] arr) {
        sort(arr, 0, arr.length - 1);
    }

    public static void sort(int[] arr, int l, int r) {
        if (l == r) {
            return;
        }
        int m = (l + r) / 2;
        sort(arr, l, m);
        sort(arr, m + 1, r);
        merge(arr, l, m, r);
    }

    // l....r 一共有n个数
    // O(n)
    public static void merge(int[] arr, int l, int m, int r) {
        int i = l;
        int a = l;
        int b = m + 1;
        while (a <= m && b <= r) {
            help[i++] = arr[a] <= arr[b] ? arr[a++] : arr[b++];
        }
        // 左侧指针、右侧指针，必有一个越界、另一个不越界
        while (a <= m) {
            help[i++] = arr[a++];
        }
        while (b <= r) {
            help[i++] = arr[b++];
        }
        for (i = l; i <= r; i++) {
            arr[i] = help[i];
        }
    }

}
```

## 归并分治

原理：

1. 思考一个问题在大范围上的答案是否等于：左部分的答案 + 右部分的答案 + 跨越左右产生的答案
2. 在计算“跨越左右产生的答案”时，如果加上左、右各自有序这个设定，是否会获得计算的便利性
3. 如果以上两点都成立，那么该问题很可能会被归并分治解决(话不说满，因为总有很毒的出题人)
4. 求解答案的过程中只要加入归并排序就可以了，因为要让左、右各自有序，来获得计算的便利性

补充：

1. 一些能用归并分治解决的问题，往往也可以用线段树、树状数组等解法，而且时间复杂度也是最优的
2. 归并分支不仅可以解决简单题，还可以解决很多较难的问题，只要符合上面说的特征，比如：二维空间里任何两点间的最短距离问题
3. 还有一个常考的算法：“整块分治”

求数组最小和：

```java
// 小和问题
// 测试链接 : https://www.nowcoder.com/questionTerminal/edfe05a1d45c4ea89101d936cac32469
// 请同学们务必参考如下代码中关于输入、输出的处理
// 这是输入输出处理效率很高的写法
// 提交以下的code，提交时请把类名改成"Main"，可以直接通过

public class MergeSort_SmallSum {
    public static int MAX_LENGTH = 100001;

    public static int[] arr = new int[MAX_LENGTH];

    public static int[] help = new int[MAX_LENGTH];

    public static int n;

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        PrintWriter pw = new PrintWriter(new OutputStreamWriter(System.out));
        StreamTokenizer st = new StreamTokenizer(br);
        while (st.nextToken() != StreamTokenizer.TT_EOF) {
            n = (int) st.nval;
            for (int i = 0; i < n; i++) {
                st.nextToken();
                arr[i] = (int) st.nval;
            }

            pw.println(smallSum(0, n - 1));

        }
        pw.flush();
        pw.close();
    }

    // 结果比较大，用int会溢出的，所以返回long类型
    // 特别注意溢出这个点，笔试常见坑
    // 返回arr[l...r]范围上，小和的累加和，同时请把arr[l..r]变有序
    // 时间复杂度O(n * log n)
    public static long smallSum(int l, int r) {
        if (l == r) {
            return 0;
        }
        int m = (l + r) / 2;
        return smallSum(l, m) + smallSum(m + 1, r) + merge(l, m, r);
    }

    // 返回跨左右产生的小和累加和，左侧有序、右侧有序，让左右两侧整体有序
    // arr[l...m] arr[m+1...r]
    public static long merge(int l, int m, int r) {
        // 统计部分
        long ans = 0;
        for (int j = m + 1, i = l, sum = 0; j <= r; j++) {
            while (i <= m && arr[i] <= arr[j]) {
                sum += arr[i++];
            }
            ans += sum;
        }

        // 排序部分
        int i = l;
        int a = l;
        int b = m + 1;
        while (a <= m && b <= r) {
            help[i++] = arr[a] <= arr[b] ? arr[a++] : arr[b++];
        }
        while (a <= m) {
            help[i++] = arr[a++];
        }
        while (b <= r) {
            help[i++] = arr[b++];
        }
        for (i = l; i <= r; i++) {
            arr[i] = help[i];
        }

        return ans;
    }
}
```

翻转对：

```java
// 翻转对数量
// 测试链接 : https://leetcode.cn/problems/reverse-pairs/
public class MergeSort_ReversePairs {

    public static int MAX_LENGTH = 50001;

    public static int[] arr = new int[MAX_LENGTH];

    public static int[] help = new int[MAX_LENGTH];

    public static int reversePairs(int[] nums) {
        return count(nums, 0, nums.length - 1);
    }

    // 统计l...r范围上，翻转对的数量，同时l...r范围统计完后变有序
    // 时间复杂度O(n * log n)
    public static int count(int[] arr, int l, int r) {
        if (l == r) {
            return 0;
        }
        int m = (l + r) / 2;
        return count(arr, l, m) + count(arr, m + 1, r) + merge(arr, l, m, r);
    }

    public static int merge(int[] arr, int l, int m, int r) {
        // 统计部分
        int ans = 0;
        for (int i = l, j = m + 1, sum = 0; i <= m; i++) {
            while (j <= r && (long) arr[i] > (long) arr[j] * 2) {
                sum++;
                j++;
            }
            ans += sum;
        }

        // 正常merge
        int i = l;
        int a = l;
        int b = m + 1;
        while (a <= m && b <= r) {
            help[i++] = arr[a] <= arr[b] ? arr[a++] : arr[b++];
        }
        while (a <= m) {
            help[i++] = arr[a++];
        }
        while (b <= r) {
            help[i++] = arr[b++];
        }
        for (i = l; i <= r; i++) {
            arr[i] = help[i];
        }
        return ans;
    }
}
```

## 随机选择算法

经典随机快速排序流程：

1. 选择一个元素作为"基准"（pivot），在经典快速排序中基准一半是第一个元素或者是最后一个元素或者是中间的元素。
2. 将所有小于等于"基准"的元素移动到"基准"的左边，所有大于"基准"的元素移动到"基准"的右边。这个操作称为分区操作（partition），完成后，基准元素所处的位置就是最终排序后它应该在的位置。  
3. 对"基准"左边和右边的两个子集，不断重复第一步和第二步，直到所有子集只剩下一个元素。

荷兰国旗问题优化随机快速排序  
荷兰国旗问题优化后的过程：  
在当前范围上选择一个数字x，利用荷兰国旗问题进行数组的划分，\<x \=x \>x  
对\<x范围重复这个过程，对\>x范围重复这个过程

荷兰国旗问题的优化点：选出一个数字x，数组在划分时会搞定所有值是x的数字

### 时间复杂度和空间复杂度

选择的数字是当前范围上的固定位置，比如范围上的最右数字，那么就是普通快速排序
选择的数字是当前范围上的随机位置，那么就是随机快速排序

普通快速排序，时间复杂度O(n^2)，额外空间复杂度O(n)
随机快速排序，时间复杂度O(n * logn)，额外空间复杂度O(logn)

关于复杂度的分析，进行定性的说明，定量证明略，因为证明较为复杂

## 堆结构和堆排序

完全二叉树：完全二叉树是一种特殊的二叉树，其中除了最后一层外，每一层都被完全填满，而且最后一层的节点都尽可能地靠左排列  
堆结构：堆结构是一种基于完全二叉树的数据结构  
大根堆：其中每个父节点的值都大于或等于其子节点的值。换句话说，堆中的最大元素位于根节点  
小根堆：其中每个父节点的值都小于或等于其子节点的值。换句话说，堆中的最小元素位于根节点  

堆中i节点的父节点：(i-1)/2  
i的左孩子：i\*2 + 1  
i的右孩子：i\*2 + 2  

堆排序  

- 从顶到底建堆，时间复杂度O(n \*log n)，log1 + log2 + log3 + … + logn -> O(n \* logn)  
    或者用增倍分析法：建堆的复杂度分析 + 子矩阵数量的复杂度分析  
- 从底到顶建堆，时间复杂度O(n)，总代价就是简单的等比数列关系，为啥会有差异？简单图解一下  
- 建好堆之后的调整阶段，从最大值到最小值依次归位，时间复杂度O(n *log n)  

时间复杂度O(n \* log n)，不管以什么方式建堆，调整阶段的时间复杂度都是这个，所以整体复杂度也是这个  
额外空间复杂度是O(1)，因为堆直接建立在了要排序的数组上，所以没有什么额外空间  

## 哈希表、有序表和比较器的用法

### 哈希表

哈希表的用法（认为是集合，根据值来做key 或者 根据内存地址做key）  
HashSet和HashMap原理一样，有无伴随数据的区别  

1. HashSet:
    - HashSet是基于哈希表实现的集合类。
    - 它存储唯一的元素，不允许重复值。
    - HashSet没有顺序，不保证元素的存储顺序与插入顺序相同。
    - 适用于需要快速查找并且不需要维护键-值对关系的场景。

2. HashMap:
    - HashMap也是基于哈希表实现的集合类，但是它存储的是键-值对。
    - 每个元素都有一个唯一的键和对应的值。
    - HashMap不保证顺序，不保证键-值对的存储顺序与插入顺序相同。
    - 适用于需要根据键快速查找对应值的场景。

增、删、改、查时间为O(1)，但是大常数  
所以当key的范围是固定的、可控的情况下，可以用数组结构替代哈希表结构  

### 有序表和比较器

有序表的用法（认为是集合，但是有序组织）  
TreeSet和TreeMap原理一样，有无伴随数据的区别  
增、删、改、查 + 很多和有序相关的操作(floor、ceilling等)，时间为O(log n)  
有序表比较相同的东西会去重，如果不想去重就加入更多的比较策略（比较器定制）。堆不会去重。  
有序表在java里就是红黑树实现的  
AVL树、SB树、替罪羊树、Treap、Splay、跳表等等很多结构都可实现同样功能  

比较器：定制比较策略。用在排序、堆、有序表等很多需要序的结构中都可使用  
定义类、直接Lamda表达式  

字典序的概念：字典序是按照字母表顺序排列的顺序  
如果长度相同，按照字典中字母的顺序来进行比较  
如果长度不同，将长度较短的字符串用空格或者其他字符进行补齐，使得两个字符串的长度相等，然后再进行比较  

## 堆结构常见题

### 合并K个有序链表

### 线段最多重合问题

### 让数组整体累加和减半的最少操作次数

## 基数排序

## 重要排序算法总结

稳定性  
排序算法的稳定性是指：同样大小的样本在排序之后不会改变原始的相对次序  
稳定性对基础类型对象来说毫无意义  
稳定性对非基础类型对象有意义，可以保留之前的相对次序  

| 算法  | 时间复杂度 | 空间复杂度 | 稳定性 |
| :------: | :------: | :------: |  :------: |
|   SelectionSort   |   O(N^2)      |   O(1)   |   无   |
|   BubbleSort      |   O(N^2)      |   O(1)   |   有   |
|   InsertionSort   |   O(N^2)      |   O(1)   |   有   |
|   MergeSort       |   O(N*logN)   |   O(N)   |   有   |
|   QuickSort       |   O(N*logN)   |   O(logN)|   无   |
|   HeapSort        |   O(N)        |   O(1)   |   无   |
|   CountSort       |   O(N)        |   O(M)   |   有   |
|   RadixSort       |   O(N)        |   O(M)   |   有   |

基于比较的排序，目前不存在时间复杂度为O(n * logn)，空间复杂度低于O(n)，还具有稳定性的算法  
课外排序算法(TimSort、ShellSort)  

在数据量非常小的情况下可以做到非常迅速：插入排序  
性能优异、实现简单且利于改进，并且不在乎稳定性：随机快排  
性能优异、不在乎额外空间、有稳定性：归并排序  
性能优异、额外空间复杂度O(1)、没有稳定性：堆排序

## 异或运算

### 异或运算性质

1. 异或运算就是无进位相加
2. 异或运算满足交换律、结合律，也就是同一批数字，不管异或顺序是什么，最终的结果都是一个
3. 0^n=n，n^n=0
4. 整体异或和如果是x，整体中某个部分的异或和如果是y，那么剩下部分的异或和是x^y

这些结论最重要的就是性质1，所有其他结论都可以由这个结论推论得到

其中第性质4相关的题目最多，利用区间上异或和的性质

#### 题目1 交换两个数

```java
public class SwapExclusiveOr {

    public static int swap(int a, int b) {
        a = a ^ b;
        b = a ^ b;
        a = a ^ b;
        return a;
    }

    // 如果 i == j 会出错
    // 只有 i 和 j 有不同的内存地址时才能完成交换
    public static void swap(int[] arr, int i, int j) {
        arr[i] = arr[i] ^ arr[j];
        arr[j] = arr[i] ^ arr[j];
        arr[i] = arr[i] ^ arr[j];
    }
}
```

#### 题目2 不用任何判断语句和比较操作，返回两个数的最大值

```java
// 不用任何判断语句和比较操作，返回两个数的最大值
// 测试链接 : https://www.nowcoder.com/practice/d2707eaf98124f1e8f1d9c18ad487f76

public class GetMaxWithoutJudge {

    public static void main(String[] args) {
        int a = Integer.MAX_VALUE;
        int b = Integer.MIN_VALUE;
        System.out.println(getMax1(a, b));
        System.out.println(getMax2(a, b));
    }

    // 必须保证n一定是0 或 1
    // 输入 1 返回 0
    // 输入 0 返回 1
    public static int flip(int n) {
        return n ^ 1;
    }

    // 返回输入参数n的符号
    // 非负数返回1
    // 负数返回0
    public static int sign(int n) {
        // n >>> 31 的意思是将变量 n 的二进制表示向右移动 31 位，移动后左边空出的位用0填充
        // 实际上是获取n的符号位，如果n是非负数，返回1，如果n是负数，返回0
        return flip(n >>> 31);
    }

    // 存在溢出问题 c的值超过2^32
    public static int getMax1(int a, int b) {
        int c = a - b;
        // c为非负数    returnA 1   returnB 0
        // c为负数      returnA 0   returnB 1
        int returnA = sign(c);
        int returnB = flip(returnA);
        return returnA == 1 ? a : b;
//        return a * returnA + b * returnB;
    }

    public static int getMax2(int a, int b) {
        int c = a - b;
        int signA = sign(a);
        int signB = sign(b);
        int signC = sign(c);
        // 判断A和B，符号是不是不一样，如果不一样diffAB=1，如果一样diffAB=0
        int diffAB = signA ^ signB;
        // 判断A和B，符号是不是一样，如果一样sameAB=1，如果不一样sameAB=0
        int sameAB = flip(diffAB);
        // returnA的条件
        // a和b的符号不同，且a为非负数。
        // a和b的符号相同，且c为非负数
        int returnA = diffAB * signA + sameAB * signC;
        int returnB = flip(returnA);
        return returnA * a + returnB * b;
    }
}
```

#### 题目3 找到缺失的数字

```java
// 找到缺失的数字
// 测试链接 : https://leetcode.cn/problems/missing-number/
public class MissingNumber {

    // 性质4 整体异或和如果是x，整体中某个部分的异或和如果是y，那么剩下部分的异或和是x^y
    public static int missingNumber(int[] nums) {
        int eorHas = 0;
        int eorAll = 0;
        for (int i = 0; i < nums.length; i++) {
            eorHas ^= nums[i];
            eorAll ^= i;
        }
        eorAll ^= nums.length;
        return eorAll ^ eorHas;
    }
}
```

#### 题目4 数组中1种数出现了奇数次，其他的数都出现了偶数次，返回出现了奇数次的数

```java
// 数组中1种数出现了奇数次，其他的数都出现了偶数次
// 返回出现了奇数次的数
// 测试链接 : https://leetcode.cn/problems/single-number/
public class SingleNumber {

    // 性质3 任何数和自己异或的结果是0
    public static int singleNumber(int[] nums) {
        int ans = 0;
        for (int num : nums) {
            ans = ans ^ num;
        }
        return ans;
    }

}
```

#### 题目5 数组中有2种数出现了奇数次，其他的数都出现了偶数次，返回这2种出现了奇数次的数

Brian Kernighan算法 - 提取出二进制状态中最右侧的1

```java
// 数组中有2种数出现了奇数次，其他的数都出现了偶数次
// 返回这2种出现了奇数次的数
// 测试链接 : https://leetcode.cn/problems/single-number-iii/
public class DoubleNumber {

    public static void main(String[] args) {
        // 帮助理解Brian Kernighan算法
        // 正整数的原码、反码、补码都相同
        // 正整数按位取反得到的数和反码是不同的，这是两个不同的概念
        // 正整数按位取反得到的结果,并不是这个正数的反码,而是该正数对应负值的补码表示
        int demo = 10;
        System.out.println(demo);
        System.out.println(~demo);
        System.out.println(~demo + 1);
        System.out.println(Integer.toBinaryString(demo));// 原码
        System.out.println(Integer.toBinaryString(~demo));// 取反
        System.out.println(Integer.toBinaryString(~demo + 1));// 取反 + 1
        System.out.println(Integer.toBinaryString(-demo));// 负数
        System.out.println(Integer.toBinaryString(demo & (-demo)));// Brian Kernighan算法
        // 按位与操作中，对应位上只有两个都是 1 的情况下结果才是 1，否则为 0
    }

    // 思路是因为存在两种数出现奇数次
    // 所以这两个数的二进制肯定有一位是不同的
    // 通过Brian Kernighan算法提取出二进制里最右侧的1
    // 然后和这个1按位与不同的数就是其中一个数
    public int[] singleNumber(int[] nums) {
        int eorAB = 0;
        for (int num : nums) {
            eorAB ^= num;
        }
        // Brian Kernighan算法
        // 提取出二进制里最右侧的1
        int rightOne = eorAB & (-eorAB);
        int eorAny = 0;
        for (int num : nums) {
            if ((num & rightOne) == 0) {
                eorAny ^= num;
            }
        }
        return new int[]{eorAny, eorAny ^ eorAB};
    }

}
```

#### 题目6 数组中只有1种数出现次数少于m次，其他数都出现了m次，返回出现次数小于m次的那种数

```java
// 数组中只有1种数出现次数少于m次，其他数都出现了m次
// 返回出现次数小于m次的那种数
// 测试链接 : https://leetcode.cn/problems/single-number-ii/
// 注意 : 测试题目只是通用方法的一个特例，课上讲了更通用的情况
public class OneKindNumberLessMTimes {

    // 思路是用一个额外的数组来记录这个数字的二进制表示中每一位上1出现的次数
    // 计数数组中数量小于m的就是要找的数
    public static int singleNumber(int[] nums, int m) {
        int[] count = new int[32];
        for (int num : nums) {
            for (int i = 0; i < 32; i++) {
                // 统计每个数的二进制表示中每一位上1出现的次数
                count[i] += (num >> i) & 1;
            }
        }
        int ans = 0;
        for (int i = 0; i < 32; i++) {
            // 获取二进制中出现次数小于m的1
            if (count[i] % m != 0) {
                // 将变量 ans 的第 i 位设置为1
                ans |= 1 << i;
            }
        }
        return ans;
    }

}
```
