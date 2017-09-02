* [Visualization](https://www.toptal.com/developers/sorting-algorithms/)
* k Sorted - A partially sorted array, where each element is no more than `k` positions away from it's fully-sorted position
* Stable algorithms preserve element order when the sort value is the same

## Topological Sort

* Used with graphs

## Bubble Sort

* Works by going through a list and swapping any adjacent values that are out of order
* Slow, but easy to implement. Generally only used for education.
* May be practical if the elements are already almost sorted, but not better than insertion sort
* Helps tell you how well a list is sorted
* Stable

### Complexity

### Time

* Worst-case: `O(n^2)`
* Average-case: `O(n^2)`
* Best-case: `O(n)` - (List is already sorted)

### Space

* `O(1)`

### Implementation

```js
function bubbleSort(array){
    var swapped;
    do {
        swapped = false;
        for (var i = 0; i < array.length - 1; i++) {
            // If this value is greater than the next one
            if (array[i] > array[i + 1]){
                // Swap them
                var temporary = array[i];
                array[i] = array[i+1];
                array[i + 1] = temporary;
                swapped = true;
            }
        }
    } while (swapped);
}
```

## Selection Sort

* Works by incrementally sorting the list from start to finish
* Not stable

### Complexity

### Time

* Best, average, and worst - `O(n^2)`

### Space

* `O(1)`

### Implementation

```js
function selectionSort(array){
    var minimum;

    for (let i = 0; i < array.length; i++){
        minimum = i;

        //check the rest of the array to see if anything is smaller
        for (let j = i + 1; j < array.length; j++){
            if (array[j] < array[min]){
                minimum = j;
            }
        }

        //if the minimum isn't in this position, swap it
        if (i != minimum){
            let temporary = array[i];
            array[i] = array[minimum];
            array[minimum] = temporary;
        }
    }

    return array;
}
```

## Insertion Sort

* Works by gradually building a sorted list, and figuring out where each successive element belongs in that list
* Natural sort
* Efficient for small data sets
* Stable

### Complexity

#### Time

* Best-case: `O(n)`
* Average-case: `O(n^2)`
* Worst-case: `O(n^2)`

#### Space

`O(1)`

### Implementation

```js
function insertionSort(array){
    for (let i = 1; i < array.length; i++){
        // Make room for where the next element goes
        for (var j = i - 1; j >= 0 && (array[j] > array[i]); j--){
            array[j + 1] = array[j];
        }
        // Put the new element in
        array[j + 1] = array[i];
    }
}
```

## Shellsort

* Named after Donald Shell
* Based on insertion sort
* Works by comparing distant elements rather than close ones, decreasing the distance each time
* Basically an insertion sort of every nth element
* Gets efficiency by loosely pre-sorting the list
* After each iteration, the list is k-sorted by the gap number
* Not stable

### Components

* Ciura's sequence (optimal average gaps) - [701, 301, 132, 57, 23, 10, 4, 1]
* Sedgewick's algorithm - Dynamically determine the size of gaps

### Complexity

### Time

* Heavily dependent on which gaps are used
* Worst-case: `O(n^2)` with a bad gap sequence, `O(n log n)` with a good gap sequence
* Best-case: `O(n log n)`

### Space

* `O(n)`

### Implementation

```js
function shellSort(list){
    // Initial gap value
    var gap = 1;
    while (gap < list.length / 3){
        gap = 3 * gap + 1;
    }

    while (gap >= 1){
        // Iterate from the gap number (4) to end of the list (10)
        for (let currentPosition = gap; position < list.length; i++){
            // From the current position, recursively swap position/gap pairs until they aren't out of order
            for (let j = currentPosition; j >= gap && list[j] < list[j - gap]; j -= gap){
                // Swap
                let temporary = list[j];
                list[j] = list[j - gap];
                list[j - gap] = temporary;
            }
        }
        // Update gap value
        gap = (gap - 1) / 3;
    }
}
```

## Mergesort

* Divide the list into sublists, starting with a size of 1, then Repeatedly merge sublists until there is only one left
* In its worse case, it does significantly better than quicksort's average case
* Highly parallelizable
* Stable

### Complexity

#### Time

* Best case: `O(n log n)`
* Average case: `O(n log n)`
* Worst case: `O(n log n)`

#### Space

* `O(1)` - In place
* `O(n)` - Parallel

### Top-down

### Bottom-up

## Heapsort

## Quicksort

* Ideally runs 2-3 times faster than mergesort and heapsort
* Not stable

### Complexity

#### Time

* Best case: `O(n log n)`
* Average case: `O(n log n)`
* Worst case: `O(n^2)`

#### Space

* Worst-case: `O(n)`
* Average-case: `O(log n)`
