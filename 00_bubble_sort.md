### 📅 Discovered Date : 1956

### 📃 Detailed Description
Bubble Sort is one of the simplest sorting algorithms. It works by repeatedly stepping through the list to be sorted, comparing each pair of adjacent items, and swapping them if they are in the wrong order. The pass through the list is repeated until no swaps are needed, indicating that the list is sorted.

This algorithm gets its name because smaller elements "bubble" to the top of the list while larger elements sink to the bottom. Although Bubble Sort is easy to understand and implement, it is not suitable for large datasets as its average and worst-case time complexity is quite high.

### 🔹 Algorithm Steps:
1. Start at the beginning of the array.
2. Compare the first two elements. If the first is greater than the second, swap them.
3. Move to the next pair of elements, and repeat step 2.
4. Continue until the end of the array is reached. The last element will now be the largest.
5. Repeat the process for the remaining elements, excluding the last element, until the array is sorted.

### 🔹 Complexity:
- **Time Complexity:** O(n^2) in the average and worst cases.
- **Space Complexity:** O(1) as it is an in-place sorting algorithm.

### 💻 Java Code Snippet

=== "C++"

    ```c++
        #include <iostream>
        using namespace std;
        int main()
        {
            int arr[10], i, j, temp;
            cout<<"Enter the elements of the array: ";
            for (i = 0; i < 10; i++)
            {
                cin>>arr[i];
            }
            for (i = 0; i < 10; i++)
            {
                for (j = i + 1; j < 10; j++)
                {
                    if (arr[i] > arr[j])
                    {
                        temp = arr[i];
                        arr[i] = arr[j];
                        arr[j] = temp;
                    }
                }
            }
            cout<<"The sorted array is: ";
            for (i = 0; i < 10; i++)
            {
                cout<<arr[i]<<" ";
            }
            return 0;
        }
    ```

=== "java"

    ```java
        public class BubbleSort {
            public static void bubbleSort(int[] array) {
                int n = array.length;
                boolean swapped;
                for (int i = 0; i < n - 1; i++) {
                    swapped = false;
                    for (int j = 0; j < n - i - 1; j++) {
                        if (array[j] > array[j + 1]) {
                            // swap temp and arr[i]
                            int temp = array[j];
                            array[j] = array[j + 1];
                            array[j + 1] = temp;
                            swapped = true;
                        }
                    }
                    // If no two elements were swapped by inner loop, then break
                    if (!swapped) break;
                }
            }
        
            public static void main(String[] args) {
                int[] array = {64, 34, 25, 12, 22, 11, 90};
                bubbleSort(array);
                System.out.println("Sorted array: ");
                for (int value : array) {
                    System.out.print(value + " ");
                }
            }
        }
    ```
