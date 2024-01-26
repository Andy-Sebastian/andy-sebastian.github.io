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
