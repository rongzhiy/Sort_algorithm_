# 本仓库是对下面的视频进行简单实现

【只有程序员懂】 [https://www.bilibili.com/video/BV1hM4y127NH](https://www.bilibili.com/video/BV1Tk4y1v7SJ)

【原视频连接】：https://www.youtube.com/watch?v=kPRA0W1kECg

【原视频作者主页】：http://panthema.net/2013/sound-of-sorting/


> 原作者以C++实现，本仓库算是一种补充，欢迎各位大佬提出改进意见。


如果有任何问题可以随时交流! 如果对你有帮助，请别忘了给我一个star，非常感谢。


![](https://th.bing.com/th/id/OIP.5SgxDxkPLkRhGpMFrb9nGAAAAA?w=195&h=195&c=7&r=0&o=5&pid=1.7)


# Java版本

# 十大经典排序算法
1、稳定排序：如果 a 原本在 b 的前面，且 a == b，排序之后 a 仍然在 b 的前面，则为稳定排序。

2、非稳定排序：如果 a 原本在 b 的前面，且 a == b，排序之后 a 可能不在 b 的前面，则为非稳定排序。

3、原地排序：原地排序就是指在排序过程中不申请多余的存储空间，只利用原来存储待排数据的存储空间进行比较和交换的数据排序。

4、非原地排序：需要利用额外的数组来辅助排序。

5、时间复杂度：一个算法执行所消耗的时间。

6、空间复杂度：运行完一个算法所需的内存大小

![image.png](https://cdn.nlark.com/yuque/0/2022/png/1143997/1666869803626-7596c007-6f00-4eec-9ef4-460666bd17a9.png#averageHue=%23f8c08b&clientId=u6cd6aba5-3633-4&from=paste&id=u56cc7b24&name=image.png&originHeight=596&originWidth=951&originalType=url&ratio=1&rotation=0&showTitle=false&size=144088&status=done&style=none&taskId=u1fb4f938-93bb-475d-aabb-a80ff8f33a7&title=)
#### 
十大排序中的稳定排序
冒泡排序（bubble sort） — O(n2) 插入排序 （insertion sort）— O(n2) 归并排序 （merge sort）— O(n log n)
#### 十大排序中的非稳定排序
面试考察中一般问快排，选择，希尔，堆这几种非稳定排序
选择排序 （selection sort）— O(n2) 希尔排序 （shell sort）— O(n log n) 堆排序 （heapsort）— O(n log n) 快速排序 （quicksort）— O(n log n)
# 0 冒泡排序
冒泡排序（Bubble Sort）也是一种简单直观的排序算法。它重复地走访过要排序的数列，一次比较两个元素，如果他们的顺序错误就把他们交换过来。走访数列的工作是重复地进行直到没有再需要交换，也就是说该数列已经排序完成。这个算法的名字由来是因为越小的元素会经由交换慢慢“浮”到数列的顶端。
作为最简单的排序算法之一，冒泡排序给我的感觉就像 Abandon 在单词书里出现的感觉一样，每次都在第一页第一位，所以最熟悉。冒泡排序还有一种优化算法，就是立一个 flag，当在一趟序列遍历中元素没有发生交换，则证明该序列已经有序。但这种改进对于提升性能来说并没有什么太大作用。
## 1. 算法步骤

1. **比较相邻的元素。如果第一个比第二个大，就交换他们两个。**
2. **对每一对相邻元素作同样的工作，从开始第一对到结尾的最后一对。这步做完后，最后的元素会是最大的数。**
3. **针对所有的元素重复以上的步骤，除了最后一个。**
4. **持续每次对越来越少的元素重复上面的步骤，直到没有任何一对数字需要比较。**
## 2. 动图演示
[![](https://cdn.nlark.com/yuque/0/2022/gif/1143997/1651483986496-562f61f6-f286-43c0-8b88-2915c6c6cccf.gif#averageHue=%23d2e2e8&clientId=ub18ff80c-db7d-4&from=paste&id=uee614fca&originHeight=257&originWidth=826&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u532c8b6a-8cbd-4dd1-9030-488199376b5&title=)](https://static.javajike.com/img/suanfa/paixu/bubbleSort.gif)
## 3. 什么时候最快
当输入的数据已经是正序时（都已经是正序了，我还要你冒泡排序有何用啊）。
## 4. 什么时候最慢
当输入的数据是反序时（写一个 for 循环反序输出数据不就行了，干嘛要用你冒泡排序呢，我是闲的吗）。
## 5、实现
```java
public class BubbleSort implements IArraySort {

    @Override
    public int[] sort(int[] sourceArray) throws Exception {
        // 对 arr 进行拷贝，不改变参数内容
        int[] arr = Arrays.copyOf(sourceArray, sourceArray.length);

        for (int i = 1; i < arr.length; i++) {
            // 设定一个标记，若为true，则表示此次循环没有进行交换，也就是待排序列已经有序，排序已经完成。
            boolean flag = true;

            for (int j = 0; j < arr.length - i; j++) {
                if (arr[j] > arr[j + 1]) {
                    int tmp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = tmp;

                    flag = false;
                }
            }

            if (flag) {
                break;
            }
        }
        return arr;
    }
}

```
```python
def bubbleSort(arr):
    for i in range(1, len(arr)):
        for j in range(0, len(arr)-i):
            if arr[j] > arr[j+1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]
    return arr
```

# 1 选择排序
选择排序是一种简单直观的排序算法，无论什么数据进去都是 O(n²) 的时间复杂度。所以用到它的时候，数据规模越小越好。唯一的好处可能就是不占用额外的内存空间了吧。
## 1. 算法步骤

1. 首先在未排序序列中找到最小（大）元素，存放到排序序列的起始位置
2. **再从剩余未排序元素中继续寻找最小（大）元素，然后放到已排序序列的末尾。**
3. 重复第二步，直到所有元素均排序完毕。
## 2. 动图演示
[![](https://cdn.nlark.com/yuque/0/2022/gif/1143997/1651484061753-cb0b5931-d7c6-4f9f-a93e-be7dc065b4be.gif#averageHue=%23d0e1e8&clientId=ub18ff80c-db7d-4&from=paste&id=u815be2d0&originHeight=248&originWidth=811&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=ua6a6bf93-91ed-45cd-89c6-8528d4f69fe&title=)](https://static.javajike.com/img/suanfa/paixu/selectionSort.gif)

```java
public class SelectionSort implements IArraySort {

    @Override
    public int[] sort(int[] sourceArray) throws Exception {
        int[] arr = Arrays.copyOf(sourceArray, sourceArray.length);

        // 总共要经过 N-1 轮比较
        for (int i = 0; i < arr.length - 1; i++) {
            int min = i;

            // 每轮需要比较的次数 N-i
            for (int j = i + 1; j < arr.length; j++) {
                if (arr[j] < arr[min]) {
                    // 记录目前能找到的最小值元素的下标
                    min = j;
                }
            }

            // 将找到的最小值和i位置所在的值进行交换
            if (i != min) {
                int tmp = arr[i];
                arr[i] = arr[min];
                arr[min] = tmp;
            }

        }
        return arr;
    }
}
```
```python
def selectionSort(arr):
    for i in range(len(arr) - 1):
        # 记录最小数的索引
        minIndex = i
        for j in range(i + 1, len(arr)):
            if arr[j] < arr[minIndex]:
                minIndex = j
        # i 不是最小数时，将 i 和最小数进行交换
        if i != minIndex:
            arr[i], arr[minIndex] = arr[minIndex], arr[i]
    return arr
```

# 2 插入排序
插入排序的代码实现虽然没有冒泡排序和选择排序那么简单粗暴，但它的原理应该是最容易理解的了，因为只要**打过扑克牌**的人都应该能够秒懂。插入排序是一种最简单直观的排序算法，它的工作原理是通过构建有序序列，对于未排序数据，在已排序序列中从后向前扫描，找到相应位置并插入。
插入排序和冒泡排序一样，也有一种优化算法，叫做拆半插入。
## 1. 算法步骤

1. 将第一待排序序列第一个元素看做一个有序序列，把第二个元素到最后一个元素当成是未排序序列。
2. 从头到尾依次扫描未排序序列，将扫描到的每个元素插入有序序列的适当位置。（如果待插入的元素与有序序列中的某个元素相等，则将待插入元素插入到相等元素的后面。）
## 2. 动图演示
[![](https://cdn.nlark.com/yuque/0/2022/gif/1143997/1651484129258-8d0209a2-f1d2-4908-90ae-062c70be44e6.gif#averageHue=%23ececec&clientId=ub18ff80c-db7d-4&from=paste&id=u994b7432&originHeight=505&originWidth=811&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u33321728-0fcf-48ce-bed2-4f0b31d19c7&title=)](https://static.javajike.com/img/suanfa/paixu/insertionSort.gif)

```java
public class InsertSort implements IArraySort {

    @Override
    public int[] sort(int[] sourceArray) throws Exception {
        // 对 arr 进行拷贝，不改变参数内容
        int[] arr = Arrays.copyOf(sourceArray, sourceArray.length);

        // 从下标为1的元素开始选择合适的位置插入，因为下标为0的只有一个元素，默认是有序的
        for (int i = 1; i < arr.length; i++) {

            // 记录要插入的数据
            int tmp = arr[i];

            // 从已经排序的序列最右边的开始比较，找到比其小的数
            int j = i;
            while (j > 0 && tmp < arr[j - 1]) {
                arr[j] = arr[j - 1];
                j--;
            }

            // 存在比其小的数，插入
            if (j != i) {
                arr[j] = tmp;
            }

        }
        return arr;
    }
}
```
```python
def insertionSort(arr):
    for i in range(len(arr)):
        preIndex = i-1
        current = arr[i]
        while preIndex >= 0 and arr[preIndex] > current:
            arr[preIndex+1] = arr[preIndex]
            preIndex-=1
        arr[preIndex+1] = current
    return arr
```

# 3 希尔排序
希尔排序，也称递减增量排序算法，是插入排序的一种更高效的改进版本。但希尔排序是非稳定排序算法。
希尔排序是基于插入排序的以下两点性质而提出改进方法的：

- 插入排序在对几乎已经排好序的数据操作时，效率高，即可以达到线性排序的效率；
- **但插入排序一般来说是低效的，因为插入排序每次只能将数据移动一位；**

希尔排序的基本思想是：先将整个待排序的记录序列分割成为若干子序列分别进行直接插入排序，待整个序列中的记录“基本有序”时，再对全体记录进行依次直接插入排序。
## 1. 算法步骤

1. 选择一个增量序列 t1，t2，……，tk，其中 ti > tj, tk = 1；
2. 按增量序列个数 k，对序列进行 k 趟排序；
3. 每趟排序，根据对应的增量 ti，将待排序列分割成若干长度为 m 的子序列，分别对各子表进行直接插入排序。仅增量因子为 1 时，整个序列作为一个表来处理，表长度即为整个序列的长度。

```java
public class ShellSort implements IArraySort {

    @Override
    public int[] sort(int[] sourceArray) throws Exception {
        // 对 arr 进行拷贝，不改变参数内容
        int[] arr = Arrays.copyOf(sourceArray, sourceArray.length);

        int gap = 1;
        while (gap < arr.length/3) {
            gap = gap * 3 + 1;
        }

        while (gap > 0) {
            for (int i = gap; i < arr.length; i++) {
                int tmp = arr[i];
                int j = i - gap;
                while (j >= 0 && arr[j] > tmp) {
                    arr[j + gap] = arr[j];
                    j -= gap;
                }
                arr[j + gap] = tmp;
            }
            gap = (int) Math.floor(gap / 3);
        }

        return arr;
    }
}
```
```python
def shellSort(arr):
    import math
    gap=1
    while(gap < len(arr)/3):
        gap = gap*3+1
        while gap > 0:
            for i in range(gap,len(arr)):
                temp = arr[i]
                j = i-gap
                while j >=0 and arr[j] > temp:
                    arr[j+gap]=arr[j]
                    j-=gap
                    arr[j+gap] = temp
                    gap = math.floor(gap/3)
                    return arr
}
```
# 4 归并排序
归并排序（Merge sort）是建立在归并操作上的一种有效的排序算法。该算法是采用**分治法**（Divide and Conquer）的一个非常典型的应用。
作为一种典型的分而治之思想的算法应用，归并排序的实现由两种方法：
– 自上而下的递归（所有递归的方法都可以用迭代重写，所以就有了第 2 种方法）；
– 自下而上的迭代；
在《数据结构与算法 JavaScript 描述》中，作者给出了自下而上的迭代方法。但是对于递归法，作者却认为：
However, it is not possible to do so in JavaScript, as the recursion goes too deep for the language to handle.
然而，在 JavaScript 中这种方式不太可行，因为这个算法的递归深度对它来讲太深了。
说实话，我不太理解这句话。意思是 JavaScript 编译器内存太小，递归太深容易造成内存溢出吗？还望有大神能够指教。
和选择排序一样，归并排序的性能不受输入数据的影响，但表现比选择排序好的多，因为始终都是 O(nlogn) 的时间复杂度。代价是需要额外的内存空间。
## 2. 算法步骤

1. 申请空间，使其大小为两个已经排序序列之和，该空间用来存放合并后的序列；
2. 设定两个指针，最初位置分别为两个已经排序序列的起始位置；
3. 比较两个指针所指向的元素，选择相对小的元素放入到合并空间，并移动指针到下一位置；
4. 重复步骤 3 直到某一指针达到序列尾；
5. 将另一序列剩下的所有元素直接复制到合并序列尾。
## 3. 动图演示
[![](https://cdn.nlark.com/yuque/0/2022/gif/1143997/1651484241040-4810d936-830e-417f-bcc5-289bd73a210f.gif#averageHue=%23ececec&clientId=ub18ff80c-db7d-4&from=paste&id=u5f22969b&originHeight=505&originWidth=811&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u4a5c1d77-58a5-4acc-908e-0965f680309&title=)](https://static.javajike.com/img/suanfa/paixu/mergeSort.gif)

```java
public class MergeSort implements IArraySort {
    
    @Override
    public int[] sort(int[] sourceArray) throws Exception {
        // 对 arr 进行拷贝，不改变参数内容
        int[] arr = Arrays.copyOf(sourceArray, sourceArray.length);
        
        if (arr.length < 2) {
            return arr;
        }
        int middle = (int) Math.floor(arr.length / 2);
        
        int[] left = Arrays.copyOfRange(arr, 0, middle);
        int[] right = Arrays.copyOfRange(arr, middle, arr.length);
        
        return merge(sort(left), sort(right));
    }
    
    protected int[] merge(int[] left, int[] right) {
        int[] result = new int[left.length + right.length];
        int i = 0;
        while (left.length > 0 && right.length > 0) {
            if (left[0] <= right[0]) {
                result[i++] = left[0];
                left = Arrays.copyOfRange(left, 1, left.length);
            } else {
                result[i++] = right[0];
                right = Arrays.copyOfRange(right, 1, right.length);
            }
        }
        
        while (left.length > 0) {
            result[i++] = left[0];
            left = Arrays.copyOfRange(left, 1, left.length);
        }
        
        while (right.length > 0) {
            result[i++] = right[0];
            right = Arrays.copyOfRange(right, 1, right.length);
        }
        
        return result;
    }
    
}
```

```python
def mergeSort(arr):
    import math
    if(len(arr)<2):
        return arr
    middle = math.floor(len(arr)/2)
    left, right = arr[0:middle], arr[middle:]
    return merge(mergeSort(left), mergeSort(right))

def merge(left,right):
    result = []
    while left and right:
        if left[0] <= right[0]:
            result.append(left.pop(0));
        else:
            result.append(right.pop(0));
    while left:
        result.append(left.pop(0));
    while right:
        result.append(right.pop(0));
    return result
```
# 5 快速排序
快速排序是由东尼·霍尔所发展的一种排序算法。在平均状况下，排序 n 个项目要 Ο(nlogn) 次比较。在最坏状况下则需要 Ο(n2) 次比较，但这种状况并不常见。事实上，快速排序通常明显比其他 Ο(nlogn) 算法更快，因为它的内部循环（inner loop）可以在大部分的架构上很有效率地被实现出来。
快速排序使用分治法（Divide and conquer）策略来把一个串行（list）分为两个子串行（sub-lists）。
快速排序又是一种分而治之思想在排序算法上的典型应用。本质上来看，快速排序应该算是在冒泡排序基础上的递归分治法。
快速排序的名字起的是简单粗暴，因为一听到这个名字你就知道它存在的意义，就是快，而且效率高！它是处理大数据最快的排序算法之一了。虽然 Worst Case 的时间复杂度达到了 O(n²)，但是人家就是优秀，在大多数情况下都比平均时间复杂度为 O(n logn) 的排序算法表现要更好，可是这是为什么呢，我也不知道。好在我的强迫症又犯了，查了 N 多资料终于在《算法艺术与信息学竞赛》上找到了满意的答案：
快速排序的最坏运行情况是 O(n²)，比如说顺序数列的快排。但它的平摊期望时间是 O(nlogn)，且 O(nlogn) 记号中隐含的常数因子很小，比复杂度稳定等于 O(nlogn) 的归并排序要小很多。所以，对绝大多数顺序性较弱的随机数列而言，快速排序总是优于归并排序。
## 1. 算法步骤

1. 从数列中挑出一个元素，称为 “基准”（pivot）;
2. 重新排序数列，所有元素比基准值小的摆放在基准前面，所有元素比基准值大的摆在基准的后面（相同的数可以到任一边）。在这个分区退出之后，该基准就处于数列的中间位置。这个称为分区（partition）操作；
3. 递归地（recursive）把小于基准值元素的子数列和大于基准值元素的子数列排序；

递归的最底部情形，是数列的大小是零或一，也就是永远都已经被排序好了。虽然一直递归下去，但是这个算法总会退出，因为在每次的迭代（iteration）中，它至少会把一个元素摆到它最后的位置去。
## 2. 动图演示
[![](https://cdn.nlark.com/yuque/0/2022/gif/1143997/1651484281896-5332e56d-195b-483d-a258-231c3fb72cba.gif#averageHue=%23d0e1e8&clientId=ub18ff80c-db7d-4&from=paste&id=u52d3e9e2&originHeight=252&originWidth=811&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=ubb985c15-b245-4805-822a-b8cce791de9&title=)](https://static.javajike.com/img/suanfa/paixu/quickSort.gif)

```java
public static void quickSort(int[] array, int low, int high) {

        /**
         * 分析：
         * 1.选定一个基准值，array[low]
         * 2.右指针从右向左遍历high--，查找比基准值小的数据，左指针从左向右low++，查找比基准值大的数据
         * 3.如果指针未相遇，交换左右两值位置，如果指针相遇，则替换基准值的位置
         * 4.左递归，右递归
         */
        // 方法退出条件,指针相遇或错过
        if (low >= high) {
            return;
        }
        // 1. 指定基准值和左右指针记录位置
        int pivot = array[low];
        int l = low;
        int r = high;
        int temp = 0;
        // 2. 遍历条件，左右指针位置
        while (l < r) {
            // 2.1 右侧遍历
            while (l < r && array[r] >= pivot) {
                r--;
            }
            // 2.2 左侧遍历
            while (l < r && array[l] <= pivot) {
                l++;
            }
            // 2.3 l指针还在r指针右侧，尚未相遇
            if (l < r) {
                temp = array[l];
                array[l] = array[r];
                array[r] = temp;
            }
        }
        // 3. 当左右指针相遇，交换基准值位置
        array[low] = array[l];
        array[l] = pivot;
        // 4. 根据条件左侧递归遍历
        if (low < l) {
            quickSort(array, low, l - 1);
        }
        // 5. 根据条件右侧递归遍历
        if (r < high) {
            quickSort(array, r + 1, high);
        }
        
    }

//测试
public static void main(String[] args) {
        int[] arr = {-9, 78, 0, 0, 1, 0, 3, -1, 23, -56, 7};
        quickSort(arr, 0, arr.length - 1);
        System.out.println(Arrays.toString(arr));
    }


```

```java
def quickSort(arr, left=None, right=None):
    left = 0 if not isinstance(left,(int, float)) else left
    right = len(arr)-1 if not isinstance(right,(int, float)) else right
    if left < right:
        partitionIndex = partition(arr, left, right)
        quickSort(arr, left, partitionIndex-1)
        quickSort(arr, partitionIndex+1, right)
    return arr

def partition(arr, left, right):
    pivot = left
    index = pivot+1
    i = index
    while  i <= right:
        if arr[i] < arr[pivot]:
            swap(arr, i, index)
            index+=1
        i+=1
    swap(arr,pivot,index-1)
    return index-1

def swap(arr, i, j):
    arr[i], arr[j] = arr[j], arr[i]
```

#  6 堆排序
堆排序（Heapsort）是指利用堆这种数据结构所设计的一种排序算法。堆积是一个近似完全二叉树的结构，并同时满足堆积的性质：即子结点的键值或索引总是小于（或者大于）它的父节点。堆排序可以说是一种利用堆的概念来排序的选择排序。分为两种方法：

1. 大顶堆：每个节点的值都大于或等于其子节点的值，在堆排序算法中用于升序排列；
2. 小顶堆：每个节点的值都小于或等于其子节点的值，在堆排序算法中用于降序排列；

堆排序的平均时间复杂度为 Ο(nlogn)。
## 1. 算法步骤

1. 将待排序序列构建成一个堆 H[0……n-1]，根据（升序降序需求）选择大顶堆或小顶堆；
2. 把堆首（最大值）和堆尾互换；
3. 把堆的尺寸缩小 1，并调用 shift_down(0)，目的是把新的数组顶端数据调整到相应位置；
4. 重复步骤 2，直到堆的尺寸为 1。
## 2. 动图演示
[![](https://cdn.nlark.com/yuque/0/2022/gif/1143997/1651484423608-b4640e51-93fa-404d-af3e-a5f27c736078.gif#averageHue=%232d2800&clientId=ub18ff80c-db7d-4&from=paste&id=uf1ba5acc&originHeight=364&originWidth=547&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u152042bd-c64a-4645-bdea-37b6a5010a1&title=)](https://static.javajike.com/img/suanfa/paixu/heapSort.gif)

```java
public class HeapSort implements IArraySort {

    @Override
    public int[] sort(int[] sourceArray) throws Exception {
        // 对 arr 进行拷贝，不改变参数内容
        int[] arr = Arrays.copyOf(sourceArray, sourceArray.length);

        int len = arr.length;

        buildMaxHeap(arr, len);

        for (int i = len - 1; i > 0; i--) {
            swap(arr, 0, i);
            len--;
            heapify(arr, 0, len);
        }
        return arr;
    }

    private void buildMaxHeap(int[] arr, int len) {
        for (int i = (int) Math.floor(len / 2); i >= 0; i--) {
            heapify(arr, i, len);
        }
    }

    private void heapify(int[] arr, int i, int len) {
        int left = 2 * i + 1;
        int right = 2 * i + 2;
        int largest = i;

        if (left < len && arr[left] > arr[largest]) {
            largest = left;
        }

        if (right < len && arr[right] > arr[largest]) {
            largest = right;
        }

        if (largest != i) {
            swap(arr, i, largest);
            heapify(arr, largest, len);
        }
    }

    private void swap(int[] arr, int i, int j) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }

}
```
```python
def buildMaxHeap(arr):
    import math
    for i in range(math.floor(len(arr)/2),-1,-1):
        heapify(arr,i)

def heapify(arr, i):
    left = 2*i+1
    right = 2*i+2
    largest = i
    if left < arrLen and arr[left] > arr[largest]:
        largest = left
    if right < arrLen and arr[right] > arr[largest]:
        largest = right

    if largest != i:
        swap(arr, i, largest)
        heapify(arr, largest)

def swap(arr, i, j):
    arr[i], arr[j] = arr[j], arr[i]

def heapSort(arr):
    global arrLen
    arrLen = len(arr)
    buildMaxHeap(arr)
    for i in range(len(arr)-1,0,-1):
        swap(arr,0,i)
        arrLen -=1
        heapify(arr, 0)
    return arr
```
# 7 计数排序
计数排序的核心在于将输入的数据值转化为键存储在额外开辟的数组空间中。作为一种线性时间复杂度的排序，**计数排序要求输入的数据必须是有确定范围的整数。**
## 1. 动图演示
[![](https://cdn.nlark.com/yuque/0/2022/gif/1143997/1651484519437-6698d608-ee17-4926-bca6-f73c7865f161.gif#averageHue=%23ededed&clientId=u0a851962-4261-4&from=paste&id=u1df18e1a&originHeight=557&originWidth=1012&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u9b609c0b-af47-403f-b945-730991c1c20&title=)](https://static.javajike.com/img/suanfa/paixu/countingSort.gif)

```java
public class CountingSort implements IArraySort {
    
    @Override
    public int[] sort(int[] sourceArray) throws Exception {
        // 对 arr 进行拷贝，不改变参数内容
        int[] arr = Arrays.copyOf(sourceArray, sourceArray.length);
        
        int maxValue = getMaxValue(arr);
        
        return countingSort(arr, maxValue);
    }
    
    private int[] countingSort(int[] arr, int maxValue) {
        int bucketLen = maxValue + 1;
        int[] bucket = new int[bucketLen];
        
        for (int value : arr) {
            bucket[value]++;
        }
        
        int sortedIndex = 0;
        for (int j = 0; j < bucketLen; j++) {
            while (bucket[j] > 0) {
                arr[sortedIndex++] = j;
                bucket[j]--;
            }
        }
        return arr;
    }
    
    private int getMaxValue(int[] arr) {
        int maxValue = arr[0];
        for (int value : arr) {
            if (maxValue < value) {
                maxValue = value;
            }
        }
        return maxValue;
    }
    
}

```

```python
def countingSort(arr, maxValue):
    bucketLen = maxValue+1
    bucket = [0]*bucketLen
    sortedIndex =0
    arrLen = len(arr)
    for i in range(arrLen):
        if not bucket[arr[i]]:
            bucket[arr[i]]=0
        bucket[arr[i]]+=1
    for j in range(bucketLen):
        while bucket[j]>0:
            arr[sortedIndex] = j
            sortedIndex+=1
            bucket[j]-=1
    return arr
```

# 8 桶排序
桶排序是计数排序的升级版。它利用了函数的映射关系，高效与否的关键就在于这个映射函数的确定。为了使桶排序更加高效，我们需要做到这两点：

1. 在额外空间充足的情况下，尽量增大桶的数量
2. 使用的映射函数能够将输入的 N 个数据均匀的分配到 K 个桶中

同时，对于桶中元素的排序，选择何种比较排序算法对于性能的影响至关重要。
## 1. 什么时候最快
当输入的数据可以均匀的分配到每一个桶中。
## 2. 什么时候最慢
当输入的数据被分配到了同一个桶中。

```java
public class BucketSort implements IArraySort {

    private static final InsertSort insertSort = new InsertSort();

    @Override
    public int[] sort(int[] sourceArray) throws Exception {
        // 对 arr 进行拷贝，不改变参数内容
        int[] arr = Arrays.copyOf(sourceArray, sourceArray.length);

        return bucketSort(arr, 5);
    }

    private int[] bucketSort(int[] arr, int bucketSize) throws Exception {
        if (arr.length == 0) {
            return arr;
        }

        int minValue = arr[0];
        int maxValue = arr[0];
        for (int value : arr) {
            if (value < minValue) {
                minValue = value;
            } else if (value > maxValue) {
                maxValue = value;
            }
        }

        int bucketCount = (int) Math.floor((maxValue - minValue) / bucketSize) + 1;
        int[][] buckets = new int[bucketCount][0];

        // 利用映射函数将数据分配到各个桶中
        for (int i = 0; i < arr.length; i++) {
            int index = (int) Math.floor((arr[i] - minValue) / bucketSize);
            buckets[index] = arrAppend(buckets[index], arr[i]);
        }

        int arrIndex = 0;
        for (int[] bucket : buckets) {
            if (bucket.length <= 0) {
                continue;
            }
            // 对每个桶进行排序，这里使用了插入排序
            bucket = insertSort.sort(bucket);
            for (int value : bucket) {
                arr[arrIndex++] = value;
            }
        }

        return arr;
    }

    /**
     * 自动扩容，并保存数据
     *
     * @param arr
     * @param value
     */
    private int[] arrAppend(int[] arr, int value) {
        arr = Arrays.copyOf(arr, arr.length + 1);
        arr[arr.length - 1] = value;
        return arr;
    }

}
```
# 9 基数排序
基数排序是一种非比较型整数排序算法，其原理是将整数按**位数**切割成不同的数字，然后按每个位数分别比较。由于整数也可以表达字符串（比如名字或日期）和特定格式的浮点数，所以基数排序也不是只能使用于整数。
## 1. 基数排序 vs 计数排序 vs 桶排序
基数排序有两种方法：
这三种排序算法都利用了桶的概念，但对桶的使用方法上有明显差异案例看大家发的：

- 基数排序：根据键值的每位数字来分配桶；
- 计数排序：每个桶只存储单一键值；
- 桶排序：每个桶存储一定范围的数值；
## 2. LSD 基数排序动图演示
[![](https://cdn.nlark.com/yuque/0/2022/gif/1143997/1651484620126-ba6f802a-8db9-442b-9813-82c7998ec49b.gif#averageHue=%23ebebeb&clientId=u0a851962-4261-4&from=paste&id=u575f247f&originHeight=574&originWidth=1012&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=uac888605-90a3-4fa2-9aa6-3d0db8421de&title=)](https://static.javajike.com/img/suanfa/paixu/radixSort.gif)

```java
/**
 * 基数排序
 * 考虑负数的情况还可以参考： https://code.i-harness.com/zh-CN/q/e98fa9
 */
public class RadixSort implements IArraySort {

    @Override
    public int[] sort(int[] sourceArray) throws Exception {
        // 对 arr 进行拷贝，不改变参数内容
        int[] arr = Arrays.copyOf(sourceArray, sourceArray.length);

        int maxDigit = getMaxDigit(arr);
        return radixSort(arr, maxDigit);
    }

    /**
     * 获取最高位数
     */
    private int getMaxDigit(int[] arr) {
        int maxValue = getMaxValue(arr);
        return getNumLenght(maxValue);
    }

    private int getMaxValue(int[] arr) {
        int maxValue = arr[0];
        for (int value : arr) {
            if (maxValue < value) {
                maxValue = value;
            }
        }
        return maxValue;
    }

    protected int getNumLenght(long num) {
        if (num == 0) {
            return 1;
        }
        int lenght = 0;
        for (long temp = num; temp != 0; temp /= 10) {
            lenght++;
        }
        return lenght;
    }

    private int[] radixSort(int[] arr, int maxDigit) {
        int mod = 10;
        int dev = 1;

        for (int i = 0; i < maxDigit; i++, dev *= 10, mod *= 10) {
            // 考虑负数的情况，这里扩展一倍队列数，其中 [0-9]对应负数，[10-19]对应正数 (bucket + 10)
            int[][] counter = new int[mod * 2][0];

            for (int j = 0; j < arr.length; j++) {
                int bucket = ((arr[j] % mod) / dev) + mod;
                counter[bucket] = arrayAppend(counter[bucket], arr[j]);
            }

            int pos = 0;
            for (int[] bucket : counter) {
                for (int value : bucket) {
                    arr[pos++] = value;
                }
            }
        }

        return arr;
    }

    /**
     * 自动扩容，并保存数据
     *
     * @param arr
     * @param value
     */
    private int[] arrayAppend(int[] arr, int value) {
        arr = Arrays.copyOf(arr, arr.length + 1);
        arr[arr.length - 1] = value;
        return arr;
    }
}

```
```python
def radix(arr):

    digit = 0
    max_digit = 1
    max_value = max(arr)
    #找出列表中最大的位数
    while 10**max_digit < max_value:
        max_digit = max_digit + 1

    while digit < max_digit:
        temp = [[] for i in range(10)]
        for i in arr:
            #求出每一个元素的个、十、百位的值
            t = int((i/10**digit)%10)
            temp[t].append(i)

        coll = []
        for bucket in temp:
            for i in bucket:
                coll.append(i)

        arr = coll
        digit = digit + 1

    return arr
```
