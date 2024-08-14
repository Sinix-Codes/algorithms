#### 📅 Discovered Date: 1960
#### 📃 Detailed Description

Quick Sort is a highly efficient and widely used sorting algorithm. It employs a divide-and-conquer strategy to sort an array. The algorithm works by selecting a 'pivot' element from the array and partitioning the other elements into two sub-arrays, according to whether they are less than or greater than the pivot. The sub-arrays are then sorted recursively.

* 🔹 Algorithm Steps:
Choose a pivot element from the array.
Partition the array into two sub-arrays: elements less than the pivot and elements greater than the pivot.
Recursively apply Quick Sort to the sub-arrays.
Combine the sorted sub-arrays and pivot into a single sorted array.
* 🔹 Complexity:
Time Complexity: O(n log n) on average, O(n^2) in the worst case.
Space Complexity: O(log n) due to the recursion stack.

#### 💻 Java Code Snippet
```
public class QuickSort {
    public static void quickSort(int[] array, int low, int high) {
        if (low < high) {
            int pi = partition(array, low, high);
            quickSort(array, low, pi - 1);
            quickSort(array, pi + 1, high);
        }
    }

    private static int partition(int[] array, int low, int high) {
        int pivot = array[high];
        int i = (low - 1);
        for (int j = low; j < high; j++) {
            if (array[j] < pivot) {
                i++;
                int temp = array[i];
                array[i] = array[j];
                array[j] = temp;
            }
        }
        int temp = array[i + 1];
        array[i + 1] = array[high];
        array[high] = temp;
        return i + 1;
    }

    public static void main(String[] args) {
        int[] array = {10, 7, 8, 9, 1, 5};
        quickSort(array, 0, array.length - 1);
        System.out.println("Sorted array:");
        for (int value : array) {
            System.out.print(value + " ");
        }
    }
}
