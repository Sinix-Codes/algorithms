#### 📅 Discovered Date: 1946
#### 📃 Detailed Description
Binary Search is a highly efficient algorithm for finding an item from a sorted array. It works by repeatedly dividing the search interval in half. If the value of the search key is less than the item in the middle of the interval, the search continues in the lower half; otherwise, it continues in the upper half.

* 🔹 Algorithm Steps:
Start with the middle element of the array.
If the middle element equals the search key, the search is successful.
If the search key is less than the middle element, repeat the search on the lower half.
If the search key is greater than the middle element, repeat the search on the upper half.
Continue until the search key is found or the sub-array size becomes zero.
* 🔹 Complexity:
Time Complexity: O(log n).
Space Complexity: O(1) for the iterative version.
#### 💻 Java Code Snippet
```
public class BinarySearch {
    public static int binarySearch(int[] array, int key) {
        int low = 0, high = array.length - 1;
        while (low <= high) {
            int mid = low + (high - low) / 2;
            if (array[mid] == key)
                return mid;
            if (array[mid] < key)
                low = mid + 1;
            else
                high = mid - 1;
        }
        return -1;
    }

    public static void main(String[] args) {
        int[] array = {2, 3, 4, 10, 40};
        int result = binarySearch(array, 10);
        if (result == -1)
            System.out.println("Element not present");
        else
            System.out.println("Element found at index: " + result);
    }
}
