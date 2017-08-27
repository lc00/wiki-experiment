## Topological Sort

* Used with graphs

## Bubble Sort

* Works by going through a list and swapping any adjacent values that are out of order
* Slow, but easy to implement. Generally only used for education.
* May be practical if the elements are already almost sorted, but not better than insertion sort
* Helps tell you how well a list is sorted

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

### Complexity

### Time

* Best, average, and worst - `O(n^2)`

### Space

* `O(n^2)`

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

### Complexity

#### Time

* Best-case: `O(n)`
* Average-case: `O(n^2)`
* Worst-case: `O(n^2)`

#### Space

`O(n)`

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

## Mergesort

### Top-down

### Bottom-up

## Quicksort
