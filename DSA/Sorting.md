# Insertion Sort 
Insertion Sort is a simple comparison-based sorting algorithm that works by building a sorted portion of the array incrementally. At each step, the current element is compared with elements in the sorted portion and inserted at the correct position by shifting larger elements to the right. It is widely used in hybrid sorting algorithms like TimSort.

### Working:  
  - For each index `i`:
      - Assume left side `0 .... i-1` is *sorted*
      - Pick element `arr[i]`: *key*
      - Shifts all element greater than *key* to right 
      - Insert *key* at correct position

### **`Algorithm`**:
  ```text
    for i from 1 to n-1:
        key = arr[i]
        j = i-1

        while j >= 0 and arr[j] > key:
            arr[j+1] = arr[j]
            j--
        
        arr[j+1] = key
  ``` 

### **`Code`**:
  ```python
    def insertion_sort(arr):
        n = len(arr)
    
        for i in range(1, n):
            key = arr[i]
            j = i - 1
            
            # Shift elements greater than key
            while j >= 0 and arr[j] > key:
                arr[j + 1] = arr[j]
                j -= 1
            
            # Insert key at correct position
            arr[j + 1] = key
        
        return arr
  ``` 
  
### Important Points:
- It's `in-place` (no extra memory)
- It's `stable` (preserves order of equal elements)
- Works best for small and nearly sorted data
- **Best Case**: `O(n)`
  - Already sorted
- **Worst Case**: `O(n²)`
  - Reversed sorted
- **Average Case**: `O(n²)` 
- **Space Complexity**: `O(1)`

### When to Use:
- Array is small (n <= 50 - 100) and already sorted
- One needs an stable sorting algorithm
- If question says: **nearly sorted**, **few elements out of place**, **online sorting (data comes one by one)**
  
![Insertion-Sort](/Image/DSA/Insertion-Sort.png)

# Bubble Sort
Bubble Sort is a comparison-based sorting algorithm that repeatedly swaps adjacent elements if they are in the wrong order. After each pass, the largest element moves to its correct position. It is stable and in-place but inefficient with O(n²) time complexity in average and worst cases. An optimized version can detect already sorted arrays and run in O(n).

### Working:  
  - For each index `i`:
      - Compare adjacent elements `arr[j]` and `arr[j+1]`
      - If left > right → `swap`
      - After each *pass*, the **largest** element moves to the *end*
- Repeat until no swaps occur (array becomes sorted)

### **`Algorithm`**:
  ```text
    for i in range(n):
        for j in range(0, n-i-1):
            if arr[j] > arr[j+1]:
                swap(arr[j], arr[j+1])
  ``` 

### **`Code`**:
  ```python
    def bubble_sort(arr):
        n = len(arr)

        for i in range(n):
            swapped = False  # Optimization: track if swap happens

            # Last i elements are already sorted
            for j in range(0, n - i - 1):

                # Compare adjacent elements
                if arr[j] > arr[j + 1]:
                    # Swap
                    arr[j], arr[j + 1] = arr[j + 1], arr[j]
                    swapped = True

            # If no swaps → already sorted
            if not swapped:
                break

        return arr
  ``` 
  
### Important Points:
- It's `in-place` (no extra memory)
- It's `stable` (preserves order of equal elements)
- Works by repeated adjacent swapping
- Largest element bubbles to end after each pass
- **Best Case**: `O(n)`
  - Already sorted (with swapped optimization)
- **Worst Case**: `O(n²)`
  - Reversed sorted
- **Average Case**: `O(n²)` 
- **Space Complexity**: `O(1)`

### When to Use:
- Very small arrays (n <= 10–20)
- When simplicity is more important than performance
- If question says: **adjacent swaps**, **minimum adjacent swaps**, **number of passes** [`Bubble sort idea may apply conceptually`]
![Bubble Sort](/Image/DSA/Bubble-Sort.png)


# Selection Sort
Selection Sort is a comparison-based sorting algorithm that works by repeatedly selecting the smallest element from the unsorted portion and placing it at the correct position. It performs O(n²) comparisons in all cases and makes only O(n) swaps. It is not adaptive and not stable but is useful in scenarios where the number of swaps must be minimized.

### Working:  
  - For each index `i`:
      - Assume current position `i` should have the **minimum element**
      - Find the **minimum element** in the remaining array `i+1 ... n-1`
      - Swap it with `arr[i]`
- Repeat for entire array

### **`Algorithm`**:
  ```text
    for i from 0 to n-1:
        min_index = i

        for j from i+1 to n-1:
            if arr[j] < arr[min_index]:
                min_index = j

        swap(arr[i], arr[min_index])
  ``` 

### **`Code`**:
  ```python
    def selection_sort(arr):
        n = len(arr)

        for i in range(n):
            min_index = i  # Assume current index is minimum

            # Find minimum in remaining array
            for j in range(i + 1, n):
                if arr[j] < arr[min_index]:
                    min_index = j

            # Swap with correct position
            arr[i], arr[min_index] = arr[min_index], arr[i]

        return arr
  ``` 
  
### Important Points:
- It's `in-place` (no extra memory)
- `NOT stable` (can change order of equal elements)
- Performs minimum number of swaps
- Always scans full unsorted part to find minimum
- **Best Case**: `O(n²)`
  - Already sorted (with swapped optimization)
- **Worst Case**: `O(n²)`
  - Reversed sorted
- **Average Case**: `O(n²)` 
- **Space Complexity**: `O(1)`

### When to Use:
- Small arrays (n ≤ 50–100)
- When number of swaps must be minimized
- If question says: **Find minimum repeatedly**, **Minimize number of swaps**, **Place smallest element first**
![Selection Sort](/Image/DSA/Selection-Sort.png)

s

# Max Heap - Insertion & Deletion
A Max Heap is a complete binary tree where each node is greater than or equal to its children. Insertion is performed by adding the element at the end and restoring the heap property using heapify-up. Deletion (extract max) removes the root and restores the heap property using heapify-down. Both operations take O(log n) time due to the height of the tree.

### Working:  
  - A Max Heap is a complete binary tree where:
    - Parent ≥ Children
  - Represented using an array - For index i:
    - Left child → 2*i + 1
    - Right child → 2*i + 2
    - Parent → (i-1)//2

### Insertion: (`Heapify-Up / Bubble-Up`)
- Insert new element at the end
- Compare with parent
- If greater → swap
- Repeat until heap property is satisfied

### **`Algorithm`**:
  ```text
    insert(value):
        add value at end
        i = last index

        while i > 0 and arr[parent(i)] < arr[i]:
            swap(arr[i], arr[parent(i)])
            i = parent(i)
  ``` 

### **`Code`**:
  ```python
    def heap_insert(heap, value):
        heap.append(value)
        i = len(heap) - 1

        # Bubble up
        while i > 0:
            parent = (i - 1) // 2

            if heap[parent] < heap[i]:
                heap[parent], heap[i] = heap[i], heap[parent]
                i = parent
            else:
                break

        return heap
  ``` 
### Deletion: (`Delete Max / Heapify-Down`)
- Remove root (maximum element)
- Replace root with last element
- Heapify down:
  - Swap with larger child
  - Repeat until heap property is restored

### **`Algorithm`**:
  ```text
    delete_max():
        if heap empty:
            return

        root = arr[0]
        arr[0] = last element
        remove last element

        i = 0
        while i has child:
            largest = i

            if left child > arr[largest]:
                largest = left

            if right child > arr[largest]:
                largest = right

            if largest == i:
                break

            swap(arr[i], arr[largest])
            i = largest

        return root
  ``` 

### **`Code`**:
  ```python
    def heap_delete(heap):
        if len(heap) == 0:
            return None

        root = heap[0]

        # Move last element to root
        heap[0] = heap[-1]
        heap.pop()

        i = 0
        n = len(heap)

        # Heapify down
        while True:
            left = 2 * i + 1
            right = 2 * i + 2
            largest = i

            if left < n and heap[left] > heap[largest]:
                largest = left

            if right < n and heap[right] > heap[largest]:
                largest = right

            if largest == i:
                break

            heap[i], heap[largest] = heap[largest], heap[i]
            i = largest

        return root
  ``` 

### Important Points:
- Max Heap ensures largest element at root
- Insert → heapify up
- Delete → heapify down
- Always maintain complete binary tree
- Implemented using array (not pointers)
- **Insertion**: `O(log n)`
  - Already sorted (with swapped optimization)
- **Deletion**: `O(log n)`
  - Reversed sorted
- **Access max**: `O(1)` 
- **Space Complexity**: `O(1)` - (Inplace array)

### When to Use:
- Small arrays (n ≤ 50–100)
- When number of swaps must be minimized
- If question says: **Find k largest / k smallest elements**, **Top K elements**, **Streaming data (continuous input)**, **Priority-based processing**, **Repeated min/max extraction**
![Max Heap Insertion Deletion](/Image/DSA/Max-Heap.png)


# Heap Sort
Heap Sort is a comparison-based sorting algorithm that uses a binary heap data structure. It first converts the array into a max heap and then repeatedly extracts the maximum element and places it at the end of the array. It has a time complexity of O(n log n) in all cases and works in-place but is not stable.

### Working:  
  - Convert array into a Max Heap
  - The largest element will be at the root
  - Swap root with last element
  - Reduce heap size
  - Heapify the root again
  - Repeat until array is sorted

### **`Algorithm`**:
  ```text
    heap_sort(arr):
        n = length of arr

        # Step 1: Build Max Heap
        for i from n//2 - 1 down to 0:
            heapify(arr, n, i)

        # Step 2: Extract elements one by one
        for i from n-1 down to 1:
            swap(arr[0], arr[i])
            heapify(arr, i, 0)


    heapify(arr, n, i):
        largest = i
        left = 2*i + 1
        right = 2*i + 2

        if left < n and arr[left] > arr[largest]:
            largest = left

        if right < n and arr[right] > arr[largest]:
            largest = right

        if largest != i:
            swap(arr[i], arr[largest])
            heapify(arr, n, largest)
  ``` 

### **`Code`**:
  ```python
    def heapify(arr, n, i):
        largest = i
        left = 2 * i + 1
        right = 2 * i + 2

        # Check left child
        if left < n and arr[left] > arr[largest]:
            largest = left

        # Check right child
        if right < n and arr[right] > arr[largest]:
            largest = right

        # Swap and continue heapifying
        if largest != i:
            arr[i], arr[largest] = arr[largest], arr[i]
            heapify(arr, n, largest)


    def heap_sort(arr):
        n = len(arr)

        # Build Max Heap
        for i in range(n // 2 - 1, -1, -1):
            heapify(arr, n, i)

        # Extract elements
        for i in range(n - 1, 0, -1):
            # Move current max to end
            arr[0], arr[i] = arr[i], arr[0]

            # Heapify reduced heap
            heapify(arr, i, 0)

        return arr
  ``` 
  
### Important Points:
- Uses Max Heap
- Sorting is done in-place
- Repeatedly extracts maximum element
- Does not preserve stability
- **Best Case**: `O(n log n)`
- **Worst Case**: `O(n log n)`
- **Average Case**: `O(n log n)` 
- **Space Complexity**: `O(1)`

### When to Use:
- Memory is limited (in-place sorting needed)
- When guaranteed O(n log n) is required
- Avoiding worst-case of Quick Sort
- When working with heap-based problems
- If question says: **Repeated max/min extraction**, **Working with priority queues**, **“Sort using heap” explicitly mentioned**
![Heap Sort](/Image/DSA/Heap-Sort-Sorting.png)


# Radix Sort
Radix Sort is a non-comparison-based sorting algorithm that processes elements digit by digit using a stable sorting algorithm such as Counting Sort. It achieves linear time complexity under certain constraints and is efficient for sorting integers with fixed digit lengths. Stability is essential for its correctness.

### Working:  
  - Sort numbers digit by digit (from least significant to most significant)
  - Use a stable sorting algorithm (Counting Sort) at each digit
  - Process digits:
    - Units → Tens → Hundreds → ...
  
### **`Algorithm`**:
  ```text
    radix_sort(arr):
        max_num = maximum element in arr
        exp = 1   # 1, 10, 100, ...

        while max_num // exp > 0:
            counting_sort(arr, exp)
            exp = exp * 10


    counting_sort(arr, exp):
        output = new array of size n
        count[0..9] = 0

        # Count occurrences
        for each element:
            digit = (arr[i] // exp) % 10
            count[digit]++

        # Prefix sum
        for i from 1 to 9:
            count[i] += count[i-1]

        # Build output (reverse for stability)
        for i from n-1 to 0:
            digit = (arr[i] // exp) % 10
            output[count[digit] - 1] = arr[i]
            count[digit]--

        copy output to arr
  ``` 

### **`Code`**:
  ```python
    def counting_sort(arr, exp):
        n = len(arr)
        output = [0] * n
        count = [0] * 10

        # Count occurrences of digits
        for i in range(n):
            digit = (arr[i] // exp) % 10
            count[digit] += 1

        # Prefix sum
        for i in range(1, 10):
            count[i] += count[i - 1]

        # Build output (reverse for stability)
        for i in range(n - 1, -1, -1):
            digit = (arr[i] // exp) % 10
            output[count[digit] - 1] = arr[i]
            count[digit] -= 1

        # Copy back
        for i in range(n):
            arr[i] = output[i]


    def radix_sort(arr):
        max_num = max(arr)
        exp = 1

        while max_num // exp > 0:
            counting_sort(arr, exp)
            exp *= 10

        return arr
  ``` 
  
### Important Points:
- Uses Counting Sort internally
- Sorting is done digit by digit
- Must use stable sort at each step
- Works best for integers or fixed-length data
- **Best Case**: `O(d * (n + k))`
  - d = number of digits
  - k = range of digits (0–9 → k=10)
- **Worst Case**: `O(d * (n + k))`
- **Average Case**: `O(d * (n + k))` 
- **Space Complexity**: `O(n + k)`
  - If `d` is small → behaves like `O(n)`

### When to Use:
- When sorting large number of integers
- When numbers have fixed number of digits
- When range is limited (like digits 0–9)
- When linear time sorting is needed
- If question says: **sort integers efficiently**, **linear time sorting**, **digits / positions matter**
![Radix Sort](/Image/DSA/Radix-Sort.png)

# Bucket Sort
Radix Sort is a non-comparison-based sorting algorithm that processes elements digit by digit using a stable sorting algorithm such as Counting Sort. It achieves linear time complexity under certain constraints and is efficient for sorting integers with fixed digit lengths. Stability is essential for its correctness.

### Working:  
  - Divide elements into buckets (groups) based on value range
  - Sort each bucket individually (usually using Insertion Sort)
  - Concatenate all buckets to get final sorted array
  
### **`Algorithm`**:
  ```text
    bucket_sort(arr):
        n = length of arr
        create n empty buckets

        # Put elements into buckets
        for each element x in arr:
            index = floor(n * x)   # (for values in range [0,1])
            insert x into bucket[index]

        # Sort each bucket
        for each bucket:
            sort(bucket)

        # Concatenate all buckets
        result = []
        for each bucket:
            append all elements to result

        return result
  ``` 

### **`Code`**:
  ```python
    def bucket_sort(arr):
        n = len(arr)
        if n == 0:
            return arr

        # Create empty buckets
        buckets = [[] for _ in range(n)]

        # Put elements into buckets
        for num in arr:
            index = int(n * num)  # assuming num in [0,1)
            buckets[index].append(num)

        # Sort each bucket
        for bucket in buckets:
            bucket.sort()  # or use insertion sort

        # Concatenate buckets
        result = []
        for bucket in buckets:
            result.extend(bucket)

        return result
  ``` 
  
### Important Points:
- Works best when data is uniformly distributed
- Uses divide into buckets + sort individually
- Often combined with Insertion Sort inside buckets
- Not a comparison sort globally
- **Best Case**: `O(n)`
- **Worst Case**: `O(n²)`
- **Average Case**: `O(n + k)` - All elements go into one bucket
- **Space Complexity**: `O(n + k)`
  - If `d` is small → behaves like `O(n)`

### When to Use:
- When near linear time is needed
- Numbers are uniformly distributed
- Values fall within a known range
- Sorting floating point numbers
- If question says: **numbers in range [0,1]**, **uniform distribution**, **floating point numbers**
![Bucket Sort](/Image/DSA/Bucket-Sort.png)

# Shell Sort
Radix Sort is a non-comparison-based sorting algorithm that processes elements digit by digit using a stable sorting algorithm such as Counting Sort. It achieves linear time complexity under certain constraints and is efficient for sorting integers with fixed digit lengths. Stability is essential for its correctness.

### Working:  
  - Improvement over Insertion Sort
  - Instead of comparing adjacent elements, compare elements at a gap
  - Gradually reduce gap until it becomes 1
  - Final pass (gap = 1) behaves like Insertion Sort, but array is already nearly sorted
  
### **`Algorithm`**:
  ```text
    shell_sort(arr):
        n = length of arr
        gap = n // 2

        while gap > 0:
            for i from gap to n-1:
                temp = arr[i]
                j = i

                while j >= gap and arr[j-gap] > temp:
                    arr[j] = arr[j-gap]
                    j = j - gap

                arr[j] = temp

            gap = gap // 2
  ``` 

### **`Code`**:
  ```python
    def shell_sort(arr):
        n = len(arr)
        gap = n // 2

        while gap > 0:
            # Perform gapped insertion sort
            for i in range(gap, n):
                temp = arr[i]
                j = i

                # Shift elements until correct position found
                while j >= gap and arr[j - gap] > temp:
                    arr[j] = arr[j - gap]
                    j -= gap

                arr[j] = temp

            # Reduce gap
            gap //= 2

        return arr
  ``` 
  
### Important Points:
- Generalization of Insertion Sort
- Uses gap-based comparison
- Reduces large disorder early
- Final pass ensures complete sorting
- **Best Case**: `O(n log n)` - (depends on gap sequence)
- **Worst Case**: `O(n²)`
- **Average Case**: `O(n^1.3 to n^1.5)`
- **Space Complexity**: `O(1)`
  - Performance depends on gap sequence

### When to Use:
- Medium-sized arrays
- When a simple algorithm better than insertion sort is needed
- When memory is limited (in-place required)
- When data is partially sorted
- If question says: **reducing disorder in steps**, **Improve insertion sort**, **Want faster than O(n²) but simpler than merge/quick**
![Shell Sort](/Image/DSA/Shell-Sort.png)

# Counting Sort
Counting Sort is a non-comparison-based sorting algorithm that counts the frequency of elements and uses prefix sums to determine their positions in the sorted array. It achieves linear time complexity under limited range conditions and is stable, making it useful in algorithms like Radix Sort.

### Working:  
  - Count how many times each element appears
  - Use counts to determine correct positions
  - Place elements directly into sorted output
  - (No comparisons → uses frequency counting)
  
### **`Algorithm`**:
  ```text
    counting_sort(arr):
        find max element (k)

        create count array of size k+1 (initialize 0)

        # Step 1: Count frequency
        for each element x in arr:
            count[x]++

        # Step 2: Prefix sum
        for i from 1 to k:
            count[i] += count[i-1]

        # Step 3: Build output (reverse for stability)
        for i from n-1 to 0:
            output[count[arr[i]] - 1] = arr[i]
            count[arr[i]]--

        copy output to arr
  ``` 

### **`Code`**:
  ```python
    def counting_sort(arr):
        if not arr:
            return arr

        max_val = max(arr)
        count = [0] * (max_val + 1)
        output = [0] * len(arr)

        # Step 1: Count frequency
        for num in arr:
            count[num] += 1

        # Step 2: Prefix sum
        for i in range(1, len(count)):
            count[i] += count[i - 1]

        # Step 3: Build output (reverse for stability)
        for i in range(len(arr) - 1, -1, -1):
            num = arr[i]
            output[count[num] - 1] = num
            count[num] -= 1

        # Copy back
        for i in range(len(arr)):
            arr[i] = output[i]

        return arr
  ``` 
  
### Important Points:
- Non-comparison sorting
- Works only for integers in a limited range
- Uses extra memory (count array)
- Can be made stable (by reverse traversal)
- **Best Case**: `O(n + k)`
  - d = number of elements
  - k = range of values (max-element)
- **Worst Case**: `O(n + k)`
- **Average Case**: `O(n + k)` 
- **Space Complexity**: `O(n + k)`
  - If `k` is small → behaves like `O(n)`

### When to Use:
- Medium-sized arrays
- When a simple algorithm better than insertion sort is needed
- When memory is limited (in-place required)
- When data is partially sorted
- If question says:  **Elements in small range**, **Values between 0 and k**, **Sort in linear time**, **Frequency-based problems**, **Elements are integers**, **Range k is small compared to n**, **Need linear time sorting**, **Used inside Radix Sort**
![Counting Sort](/Image/DSA/Counting-Sort.png)

# Quick Sort
Quick Sort is a divide-and-conquer sorting algorithm that selects a pivot element, partitions the array around the pivot, and recursively sorts the subarrays. It has an average time complexity of O(n log n) but degrades to O(n²) in the worst case. It is in-place but not stable and is widely used due to its efficiency in practice.

### Working:  
  - Pick a pivot element
  - Partition array into:
        - Elements < pivot
        - Elements > pivot
  - Place pivot at its correct position
  - Recursively apply same process on left and right parts
  
### **`Algorithm`**:
  ```text
    quick_sort(arr, low, high):
        if low < high:
            p = partition(arr, low, high)

            quick_sort(arr, low, p-1)
            quick_sort(arr, p+1, high)


    partition(arr, low, high):
        pivot = arr[high]
        i = low - 1

        for j from low to high-1:
            if arr[j] < pivot:
                i++
                swap(arr[i], arr[j])

        swap(arr[i+1], arr[high])
        return i+1
  ``` 

### **`Code`**:
  ```python
    def partition(arr, low, high):
        pivot = arr[high]  # Choose last element as pivot
        i = low - 1

        for j in range(low, high):
            if arr[j] < pivot:
                i += 1
                arr[i], arr[j] = arr[j], arr[i]

        # Place pivot at correct position
        arr[i + 1], arr[high] = arr[high], arr[i + 1]
        return i + 1


    def quick_sort(arr, low, high):
        if low < high:
            p = partition(arr, low, high)

            quick_sort(arr, low, p - 1)
            quick_sort(arr, p + 1, high)

        return arr
  ``` 
  
### Important Points:
- Uses divide and conquer
- Partitioning is the core step
- In-place sorting
- Performance depends on pivot selection
- **Best Case**: `O(n log n)`
- **Worst Case**: `O(n²)` (bad pivot choices)
- **Average Case**: `O(n log n)` 
- **Space Complexity**: `O(log n)` (recursion stack)

### When to Use:
- General-purpose sorting
- When average performance matters
- In-memory sorting and Large datasets
- If question says:  **Partitioning problems**, **Divide array into two parts**, **Quick Select (kth smallest)**, **Partition-based logic**
![Quick Sort](/Image/DSA/Quick-Sort-Sorting.png)

# Merge Sort
Counting Sort is a non-comparison-based sorting algorithm that counts the frequency of elements and uses prefix sums to determine their positions in the sorted array. It achieves linear time complexity under limited range conditions and is stable, making it useful in algorithms like Radix Sort.

### Working:  
  - Divide array into two halves
  - Recursively sort both halves
  - Merge the sorted halves into a single sorted array
  
### **`Algorithm`**:
  ```text
    merge_sort(arr):
        if size <= 1:
            return

        mid = n // 2
        left = arr[0...mid-1]
        right = arr[mid...n-1]

        merge_sort(left)
        merge_sort(right)

        merge(left, right, arr)


    merge(left, right, arr):
        i = j = k = 0

        while i < len(left) and j < len(right):
            if left[i] <= right[j]:
                arr[k] = left[i]
                i++
            else:
                arr[k] = right[j]
                j++
            k++

        copy remaining elements
  ``` 

### **`Code`**:
  ```python
    def merge_sort(arr):
        if len(arr) <= 1:
            return arr

        mid = len(arr) // 2
        left = arr[:mid]
        right = arr[mid:]

        # Recursively sort halves
        merge_sort(left)
        merge_sort(right)

        # Merge step
        i = j = k = 0

        while i < len(left) and j < len(right):
            if left[i] <= right[j]:
                arr[k] = left[i]
                i += 1
            else:
                arr[k] = right[j]
                j += 1
            k += 1

        # Copy remaining elements
        while i < len(left):
            arr[k] = left[i]
            i += 1
            k += 1

        while j < len(right):
            arr[k] = right[j]
            j += 1
            k += 1

        return arr
  ``` 
  
### Important Points:
- Uses divide and conquer
- Always splits array into halves
- Merge step is the key operation
- Stable sorting algorithm
- **Best Case**: `O(n log n)`
- **Worst Case**: `O(n log n)`
- **Average Case**: `O(n log n)` 
- **Space Complexity**: `O(n)`

### When to Use:
- When stable sorting is required
- When guaranteed O(n log n) is needed
- Sorting linked lists
- External sorting (large data / disk)
- If question says:  **Divide array into halves**, **Merging sorted data**, **Count inversions**, **Merge k sorted arrays**, **External sorting**
![Merge Sort](/Image/DSA/Merge-Sort-Sorting.png)