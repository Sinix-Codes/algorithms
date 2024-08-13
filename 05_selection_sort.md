#### 📅 Discovered Date: 1956
#### 📃 Detailed Description
Selection Sort is an in-place comparison sorting algorithm. The algorithm divides the input list into two parts: the sub-list of items already sorted and the sub-list of items remaining to be sorted. The algorithm proceeds by finding the smallest element from the unsorted sub-list and swapping it with the leftmost unsorted element.

* 🔹 Algorithm Steps:
Start with the first element as the minimum.
Compare this minimum with the remaining elements.
If a smaller element is found, set it as the new minimum.
Swap the minimum element with the first element.
Repeat for the remaining unsorted elements.
* 🔹 Complexity:
Time Complexity: O(n^2).
Space Complexity: O(1).

#### 💻 Java Code Snippet
```
public class SelectionSort {
    public static void selectionSort(int[] array) {
        int n = array.length;
        for (int i = 0; i < n-1; i++) {
            int min_idx = i;
            for (int j = i+1; j < n; j++)
                if (array[j] < array[min_idx])
                    min_idx = j;

            int temp = array[min_idx];
            array[min_idx] = array[i];
            array[i] = temp;
        }
    }

    public static void main(String[] args) {
        int[] array = {64, 25, 12, 22, 11};
        selectionSort(array);
        System.out.println("Sorted array:");
        for (int value : array) {
            System.out.print(value + " ");
        }
    }
}
