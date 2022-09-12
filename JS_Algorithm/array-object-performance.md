# 배열과 오브젝트의 성능 평가

## Big O of Object

- Insertion - O(1)
- Removal - O(1)
- Searching - O(n)
  - value로 접근
- Access - O(1)
  - key로 접근

## Big O of Object Methods

- Object.keys - O(n)
- Object.values - O(n)
- object.entries - O(n)
- hasOwnProperty - O(1)

## Big O of Arrays

- Insertion - 상황에 따라..
- Removal - 상황에 따라..
- Searching - O(n)
- Access - O(1)

## Big O of Array Operations

- push - O(1)
- pop - O(1)
- shift - O(n)
- unshift - O(n)
- concat - O(n)
- slice - O(n)
- splice - O(n)
- sort - O(n \* log n)
- forEach/map/filter/reduce/etc. - O(n)
