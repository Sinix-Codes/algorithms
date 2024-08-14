#### 📅 Discovered Date: 1964
#### 📃 Detailed Description
Heap Sort is a comparison-based sorting algorithm that uses a binary heap data structure. It is similar to selection sort, where we first find the maximum element and place it at the end. We repeat the same process for the remaining elements.

* 🔹 Algorithm Steps:
Build a max heap from the input data.
Extract the root (maximum element) from the heap and replace it with the last item.
Reduce the size of the heap and heapify the root.
Repeat the process for the remaining elements.
* 🔹 Complexity:
Time Complexity: O(n log n).
Space Complexity: O(1).

#### 💻 Java Code Snippet
```
public class HeapSort {
    public void heapSort(int array[]) {
        int n = array.length;
        for (int i = n / 2 - 1; i >= 0; i--)
            heapify(array, n, i);
        for (int i = n - 1; i > 0; i--) {
            int temp = array[0];
            array[0] = array[i];
            array[i] = temp;
            heapify(array, i, 0);
        }
    }

    void heapify(int array[], int n, int i) {
        int largest = i;
        int left = 2 * i + 1;
        int right = 2 * i + 2;
        if (left < n && array[left] > array[largest])
            largest = left;
        if (right < n && array[right] > array[largest])
            largest = right;
        if (largest != i) {
            int swap = array[i];
            array[i] = array[largest];
            array[largest] = swap;
            heapify(array, n, largest);
        }
    }

    public static void main(String[] args) {
        int array[] = {12, 11, 13, 5, 6, 7};
        HeapSort hs = new HeapSort();
        hs.heapSort(array);
        System.out.println("Sorted array:");
        for (int value : array) {
            System.out.print(value + " ");
        }
    }
}
