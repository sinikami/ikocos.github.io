---
title: Coding exercise - bubble sort
layout: post
categories: js
tags:
- bubble sort
- javascript
- typescript
---

```javascript

  // practice bubble sort
  // get a value to compare every element
  const data = [2, 3, 4, 6, 1, 8, 9];
  // swap values
  const swap = (array: any[], from: number, to: number) => {
    const tmp = array[from];
    array[from] = array[to];
    array[to] = tmp;
    return array;
  };
	
  /*
  1. imagine it is a pool that contains numbers.
  2. choose a value from the bottom and compare with each value above.
  3. smaller value will bubble up.
  */
  const size = data.length;
  for (let j = size; j >= 0; j--) {// get value from the bottom
    for (let i = j; i < size; i++) {// compare to the value  above
      if (data[i] < data[j]) swap(data, i, j); // if it is small, it is going up
    }
  }


Result:  [ 1, 2, 3, 4, 6, 8, 9 ]


```