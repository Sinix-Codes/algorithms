#### 📅 Discovered Date: 1946
#### 📃 Detailed Description
Insertion Sort is a simple and intuitive sorting algorithm that builds the final sorted array one item at a time. It is much less efficient on large lists than more advanced algorithms like Quick Sort or Merge Sort, but it has advantages in simplicity and performance on small datasets.

* 🔹 Algorithm Steps:
Start with the second element of the array.
Compare it with the elements before it and insert it into its correct position.
Repeat the process for all elements in the array.
* 🔹 Complexity:
Time Complexity: O(n^2).
Space Complexity: O(1).

#### 💻 Java Code Snippet

```
public class InsertionSort {
    public static void insertionSort(int[] array) {
        for (int i = 1; i < array.length; i++) {
            int key = array[i];
            int j = i - 1;
            while (j >= 0 && array[j] > key) {
                array[j + 1] = array[j];
                j = j - 1;
            }
            array[j + 1] = key;
        }
    }

    public static void main(String[] args) {
        int[] array = {12, 11, 13, 5, 6};
        insertionSort(array);
        System.out.println("Sorted array:");
        for (int value : array) {
            System.out.print(value + " ");
        }
    }
}
