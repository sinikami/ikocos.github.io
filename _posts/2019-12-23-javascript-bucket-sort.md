---
title: JavaScript Bucket Sort
layout: post
categories: js
tags:
- javascript
- algorithm
---

#### create buckets

>  **set buckets range**
>  
> ```
> const bucketRange: number = 10;
> ```
> 
> **set  bucketSize**
> 
>  ```
>  const bucketSize: number = Math.floor(Math.max(...array) / bucketRange) + 1;
>  ```
>
> **generate buckets**
> ```
> const buckets = Array.from({ length: bucketSize }, () => []);
> ```
> 
> **fill buckets**
> 
>  ```
>  for (const value of arr) {
>   const idx: number = Math.floor(value / bucketRange);
>   const bucket: any[] = buckets[idx];
>   bucket.push(value);
> }
> ```
> 
> **sort sigle bucket**
> 
>  ```
>  buckets.filter(x => x.length > 0).map(x => InsertionSort(x));
>  ```


#### Full Source

```javascript

export const BucketSort = (arr: any[]) => {
  const bucketRange: number = 10;
  const bucketSize: number = Math.floor(Math.max(...arr) / bucketRange) + 1;

  const buckets = Array.from({ length: bucketSize }, () => []);
  for (const value of arr) {
    const idx: number = Math.floor(value / bucketRange);
    const bucket: any[] = buckets[idx];
    bucket.push(value);
  }
  buckets.filter(x => x.length > 0).map(x => InsertionSort(x));

	 return  [].concat(...buckets);

};


```