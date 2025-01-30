# Insertion Sort

Insertion Sort is a simple and intuitive sorting algorithm that builds the final sorted array one element at a time. 
It works similarly to how you might sort a hand of playing cards: you pick one card at a time and insert it into its correct position in the sorted part of your hand. Let’s break it down in detail.

## Working Principle of Insertion Sort

1. Start from the second element (index `1`) because a single element (index `0`) is already sorted.
2. Compare the current element (`key`) with elements before it.
3. If a previous element is greater than `key`, shift it to the right.
4. Insert the `key` into its correct position.
5. Repeat the process for all elements.

## **Step-by-Step Example**
Let's sort the array **`{10, 9, 12, 4, 15}`** using Insertion Sort.

## **Initial Array:**
**` 10 | 9 | 12 | 4 | 15 `**
### **Pass 1 (`i = 1`, key = 9)**
- Compare `9` with `10` → `9 < 10`, shift `10` to the right.
- Insert `9` in the correct position.

**`9 | 10 | 12 | 4 | 15`**
  
### **Pass 2 (`i = 2`, key = 12)**
- Compare `12` with `10` → `12 > 10`, no shifting needed.

**`9 | 10 | 12 | 4 | 15`**

### **Pass 3 (`i = 3`, key = 4)**
- Compare `4` with `12`, shift `12` right.
- Compare `4` with `10`, shift `10` right.
- Compare `4` with `9`, shift `9` right.
- Insert `4` at the beginning.

**`4 | 9 | 10 | 12 | 15`**


### **Pass 4 (`i = 4`, key = 15)**
- Compare `15` with `12` → `15 > 12`, no shifting needed.

**`4 | 9 | 10 | 12 | 15`**


### **Final Sorted Array**

**`4 | 9 | 10 | 12 | 15`**
---

## **Java Implementation**
```java
class InsertionSort {
    public static void insertionAlgo(int[] arr) {
        int n = arr.length;
        for (int i = 1; i < n; i++) {
            int key = arr[i];
            int j = i - 1;
            while (j >= 0 && arr[j] > key) {
                arr[j + 1] = arr[j];
                j = j - 1;
            }
            arr[j + 1] = key;
        }
        for (int i : arr) {
            System.out.print(i + " | ");
        }
    }

    public static void main(String[] args) {
        int[] array = {10, 9, 12, 4, 15};
        insertionAlgo(array);
    }
}
```
## **Time Complexity**
| Case        | Time Complexity |
|------------|----------------|
| Best Case (Already Sorted) | **O(n)** |
| Average Case | **O(n²)** |
| Worst Case (Reversed Order) | **O(n²)** |

## **Advantages**
✅ Simple and easy to implement.  
✅ Efficient for small or nearly sorted arrays.  
✅ In-place sorting (requires no extra space).  

## **Disadvantages**
❌ Inefficient for large datasets due to **O(n²)** time complexity.  
