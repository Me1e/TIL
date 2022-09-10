# 배열과 오브젝트의 성능 평가

## Big O of Object

- Insertion - O(1)
- Removal - O(1)
- Searching - O(N)
  - value로 접근
- Access - O(1)
  - key로 접근

## Big O of Object Methods

- Object.keys - O(N)
- Object.values - O(N)
- object.entries - O(N)
- hasOwnProperty - O(1)

## Big O of Arrays

- Insertion - 상황에 따라..
- Removal - 상황에 따라..
- Searching - O(N)
- Access - O(1)

## Big O of Array Operations

- push - O(1)
- pop - O(1)
- shift - O(N)
- unshift - O(N)
- concat - O(N)
- slice - O(N)
- splice - O(N)
- sort - O(N \* logN)
- forEach/map/filter/reduce/etc. - O(N)
