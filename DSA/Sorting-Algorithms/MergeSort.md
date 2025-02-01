# Merge Sort
Merge Sort is a **divide and conquer** algorithm that splits an array into smaller subarrays, sorts them, and then merges them back together. It is widely used due to its efficiency and stability.

## Working Principle of Merge Sort
1.  **Divide**: Recursively split the array into two halves until each subarray has only one element.
2.  **Conquer**: Sort and merge the subarrays step by step.
3.  **Combine**: Merge the sorted subarrays to form a fully sorted array.

![img_mergesort_long](https://github.com/user-attachments/assets/8bc97200-973e-4504-b9e2-013e6459728a)

## Java Implementation 

```Java 
public class Main {
    public static void mergeSort(int[] arr, int lb, int ub) {
        if (lb < ub) {
            int mid = (ub + lb) / 2;
            mergeSort(arr, lb, mid);
            mergeSort(arr, mid + 1, ub);
            merge(arr, lb, mid, ub);
        }
    }

    public static void merge(int[] arr, int lb, int mid, int ub) {
        int i = lb;
        int j = mid + 1;
        int k = 0;
        int[] b = new int[ub - lb + 1];

        // Merging the two halves into b[]
        while (i <= mid && j <= ub) {
            if (arr[i] < arr[j]) {
                b[k] = arr[i];
                i++;
            } else {
                b[k] = arr[j];
                j++;
            }
            k++;
        }

        // Copy remaining elements from left subarray
        while (i <= mid) {
            b[k] = arr[i];
            i++;
            k++;
        }

        // Copy remaining elements from right subarray
        while (j <= ub) {
            b[k] = arr[j];
            j++;
            k++;
        }

        // Copy sorted elements back to original array
        for (int p = 0; p < b.length; p++) {
            arr[lb + p] = b[p];
        }
    }

    public static void main(String[] args) {
        int[] arr = {10, 3, 25, 33, 12, 15};
        mergeSort(arr, 0, arr.length - 1);
        
        // Print sorted array
        for (int i : arr) {
            System.out.print(i + " | ");
        }
    }
}
```


---
## **Example: Sorting [12, 8, 9, 3, 11, 5, 4]**
Let's walk through how `i` and `j` work while merging.

### **Step 1: Divide the Array**
Original: **[12, 8, 9, 3, 11, 5, 4]** **==>** **[12]** **[8]** **[9]** **[3]**  **[11]**  **[5]**  **[4]**
  
### **Step 2: Merging the Subarrays**
**Merging [12] and [8]:**  
- Compare: `12 > 8`, so `8` comes first, followed by `12`.  
- Result: `[8, 12]`  

**Merging [9] and [3]:**  
- Compare: `9 > 3`, so `3` comes first.  
- Result: `[3, 9]`  

**Merging [8, 12] and [3, 9]:**  
- Compare: `i = 0 (8)` vs `j = 0 (3)`, pick `3`  
- Compare: `i = 0 (8)` vs `j = 1 (9)`, pick `8`  
- Compare: `i = 1 (12)` vs `j = 1 (9)`, pick `9`  
- Copy remaining `12`  
- Result: `[3, 8, 9, 12]`  

**Merging [11] and [5]:**  
- Compare: `11 > 5`, so `5` comes first.  
- Result: `[5, 11]`  

**Merging [5, 11] and [4]:**  
- Compare: `i = 0 (5)` vs `j = 0 (4)`, pick `4`  
- Copy remaining `[5, 11]`  
- Result: `[4, 5, 11]`  

---

### **Step 3: Final Merge**
**Merging [3, 8, 9, 12] and [4, 5, 11]:**  
- Compare: `i = 0 (3)` vs `j = 0 (4)`, pick `3`  
- Compare: `i = 1 (8)` vs `j = 0 (4)`, pick `4`  
- Compare: `i = 1 (8)` vs `j = 1 (5)`, pick `5`  
- Compare: `i = 1 (8)` vs `j = 2 (11)`, pick `8`  
- Compare: `i = 2 (9)` vs `j = 2 (11)`, pick `9`  
- Compare: `i = 3 (12)` vs `j = 2 (11)`, pick `11`  
- Copy remaining `12`  
- **Final Sorted Array:** `[3, 4, 5, 8, 9, 11, 12]`  

---

## **How `i` and `j` Work During Merging**
- `i` starts at the first element of the **left** subarray.
- `j` starts at the first element of the **right** subarray.
- At each step, the **smaller** element between `arr[i]` and `arr[j]` is added to the new merged array.
- When all elements from one subarray are exhausted, the remaining elements from the other subarray are directly copied.

---

## Time and Space Complexity

## Time Complexity
| Case         | Time Complexity |
|-------------|----------------|
| Best Case   | O(n log n)      |
| Average Case | O(n log n)      |
| Worst Case  | O(n log n)      |

✅ **Why O(n log n)?**
- The array is divided into halves recursively, which takes **log n** time.
- The merging step takes **O(n)** time for each level.
- Since there are **log n** levels, total time = **O(n log n)**.

## Space Complexity
✅ **O(n)**
- Extra space is needed for temporary arrays during merging.

## **When to Use Merge Sort?**
✅ Works well for large datasets  
✅ **Stable sort** (preserves order of equal elements)  
✅ Efficient for **linked lists**  
❌ Not in-place (requires extra memory)  
❌ Not ideal for small arrays (Insertion Sort is better for small inputs).
---

### **Conclusion**
Merge Sort efficiently sorts an array by dividing it into smaller parts, sorting them recursively, and merging them back together in sorted order. The use of `i` and `j` pointers helps in merging two halves efficiently.

---
**Happy Coding! 🚀**
---
if needed watch : https://www.youtube.com/watch?v=jlHkDBEumP0&t=456s&pp=ygUQbWVyZ2Ugc29ydCBqZW5ueQ%3D%3D
