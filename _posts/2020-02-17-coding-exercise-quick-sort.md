---
title: Coding exercise - quick sort
layout: post
category: js
tags:
- javascript
- typescript
- quick sort
---

### what is Quicksort

According to Wikipedia, Quicksort Developed by British computer scientist Tony Hoare in 1959 and published in 1961.  it can be about two or three times faster than its main competitors, merge sort and heapsort.

Quicksort is a [divide-and-conquer](https://en.wikipedia.org/wiki/Divide-and-conquer_algorithm) algorithm. It works by selecting a 'pivot' element from the array and partitioning the other elements into two sub-arrays, according to whether they are less than or greater than the pivot. The sub-arrays are then sorted recursively. This can be done in-place, requiring small additional amounts of memory to perform the sorting.

Generally, there are two schemes Lomuto partition scheme and Hoare partition scheme.
Figure out in [WIKI:](https://en.wikipedia.org/wiki/Quicksort)

Let's  discuss about Hoare partition scheme here.

we need four steps to complete this sorting process.
> 1. to choose a pivot
> 2. to partition array by the pivot point
> 3.  recursively apply the steps above



Let's write code using Javascript(TypeScript).

```javascript

// Define a Sort function

const Sort = (arr: number[], left: number, right: number) => {
  // stop if remained the length of array less than 2
  if (left < right) {
    const pi = Partition(arr, left, right);
    // recursively apply sort function
    if (pi > 0) {

      Sort(arr, left, pi);
      Sort(arr, pi + 1, right);

    }
  }
};

// We need a swap function

const Swap = (arr: number[], origin: number, target: number) => {
  const temp: number = arr[origin];
  arr[origin] = arr[target];
  arr[target] = temp;

};
// Define a pivot function

const Pivot = (left: number, right: number): number => {
  // set the middle index to pivot

  return Math.round((left + right) / 2);

};

// Add last function partitioning
const Partition = (arr: number[], left: number, right: number) => {
  const pi = Pivot(left, right);
  const pv = arr[pi];
  let i = left - 1;
  let j = right + 1;
  while (i < j) {
    // left -> pivot   loop when the value less then pivot value
    do {
      i++;
    } while (arr[i] < pv);

    // right -> pivot  loop when the value great then pivot value
    do {
      j--;
    } while (arr[j] > pv);
		
    if (i > j) return j;
    if (arr[i] > arr[j]) Swap(arr, i, j);
  }
  return -1;
};

const Main = () => {

  // Define an unsorted array.
  const array: number[] = [2, 4, 3, 5, 6, 8, 9, 7, 10, 2];

  Sort(array, 0, array.length - 1);

  console.log(array);
};

Main();


Result:  [ 2, 2, 3, 4, 5, 6, 7, 8, 9, 10 ];

```