# ALgorithms

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

## 单列表、双列表及其反转

1. 按值传递、按引用传递
    值传递：在调用函数时将实际参数复制一份传递到函数中，这样函数中如果对参数进行修改，将不会影响到实际参数  
    引用传递：在调用函数时将实际参数的内存地址直接传递到函数中，那么函数中对参数的修改，将直接影响到实际的参数

2. 单链表、双链表的定义
    单链表：由一系列节点组成，每个节点包含一个指向下一个节点的指针和一个值  
    双链表：由一系列节点组成，每个节点包含一个指向下一个节点的指针、一个指向上一个节点的指针和一个值

链表：

```java
    public class ListNode {
        int val;
        ListNode next;

        ListNode(int x) {
            val = x;
        }

        public ListNode(int val, ListNode next) {
            this.val = val;
            this.next = next;
        }
    }

    public class DoubleListNode {
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
    public ListNode reverseList(ListNode head) {
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
    public DoubleListNode reverseDoubleList(DoubleListNode head) {
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

将两个升序链表合并为一个新的 **升序** 链表并返回

```java
    public ListNode mergeTwoLists(ListNode head1, ListNode head2) {
        if (head1 == null && head2 == null) {
            return null;
        } else if (head1 == null) {
            return head2;
        } else if (head2 == null){
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
