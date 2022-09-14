# 문제 해결 패턴

## Frequency counter

### 1) Same frequency

- Write a function called `same`, which accepts two arrays. The function should return true if every value in the array has it's corresponding value squared in the second array. The frequency of values must be the same.

  ```js
  same([1, 2, 3], [4, 1, 9]); // true
  same([1, 2, 3], [1, 9]); // false
  same([1, 2, 1], [4, 4, 1]); // false (must be same frequency)
  ```

- O(n^2)의 시간복잡도를 가지는 방법

  ```js
  function same(arr1, arr2) {
    if (arr1.length !== arr2.length) {
      return false;
    }
    for (let i = 0; i < arr1.length; i++) {
      let correctIndex = arr2.indexOf(arr1[i] ** 2);
      if (correctIndex === -1) {
        return false;
      }
      arr2.splice(correctIndex, 1);
    }
    return true;
  }
  ```

- O(n)의 시간복잡도를 가지는 방법

  ```js
  function same(arr1, arr2) {
    if (arr1.length !== arr2.length) {
      return false;
    }
    let frequencyCounter1 = {};
    let frequencyCounter2 = {};
    for (let val of arr1) {
      frequencyCounter1[val] = (frequencyCounter1[val] || 0) + 1;
    }
    for (let val of arr2) {
      frequencyCounter2[val] = (frequencyCounter2[val] || 0) + 1;
    }
    for (let key in frequencyCounter1) {
      if (!(key ** 2 in frequencyCounter2)) {
        return false;
      }
      if (frequencyCounter2[key ** 2] !== frequencyCounter1[key]) {
        return false;
      }
    }
    return true;
  }
  ```

### 2) Valid anagram

- Given two strings, write a function to determine if the second string is an anagram of the first. An anagram is a word, phrase, or name formed by rearranging the letters of another, such as _cinema_, formed from _iceman_.

  ```js
  validAnagram("", ""); // true
  validAnagram("aaz", "zza"); // false
  validAnagram("anagram", "nagaram"); // true
  validAnagram("rat", "car"); // false
  validAnagram("awesome", "awesom"); // false
  validAnagram("qwerty", "qeywrt"); // true
  validAnagram("texttwisttime", "timetwisttext"); // true
  ```

  > Note: You may assume the string contains only lowercase alphabets.

- My solution : O(n)

  ```js
  function validAnagram(str1, str2) {
    if (str1.length !== str2.length) {
      return false;
    }
    let fc1 = {};
    let fc2 = {};
    for (let s of str1) {
      fc1[s] = (fc1[s] || 0) + 1;
    }
    for (let s of str2) {
      fc2[s] = (fc2[s] || 0) + 1;
    }
    for (let key in fc1) {
      if (!(key in fc2)) {
        return false;
      }
      if (fc1[key] !== fc2[key]) {
        return false;
      }
    }
    return true;
  }
  ```

- Insturctor's solution: O(n)

  ```js
  function validAnagram(first, second) {
    if (first.length !== second.length) {
      return false;
    }
    const lookup = {};
    for (let i = 0; i < first.length; i++) {
      let letter = first[i];
      // if letter exists, increment, otherwise set to 1
      lookup[letter] ? (lookup[letter] += 1) : (lookup[letter] = 1);
    }
    for (let i = 0; i < second.length; i++) {
      let letter = second[i];
      // can't find letter or letter is zero then it's not an anagram
      if (!lookup[letter]) {
        return false;
      } else {
        lookup[letter] -= 1;
      }
    }
    return true;
  }
  ```

## Multiple pointers

### 1) An example

- Write a function called `sumZero` which accepts a `sorted` array of integers. The function should find the `first` pair where the sum is 0. Return an array that includes both values that sum to zero or undefined if a pair does not exist.

  ```js
  sumZero([-3, -2, -1, 0, 1, 2, 3]); // [-3, 3]
  sumZero([-2, 0, 1, 3]); // undefined
  sumZero([1, 2, 3]); // undefined
  ```

- O(n^2)의 시간복잡도를 가지는 방법

  ```js
  function sumZero(arr) {
    for (let i = 0; i < arr.length; i++) {
      for (let j = i + 1; j < arr.length; j++) {
        if (arr[i] + arr[j] === 0) {
          return [arr[i], arr[j]];
        }
      }
    }
  }
  ```

- O(n)의 시간복잡도를 가지는 방법

  ```js
  function sumZero(arr) {
    let left = 0;
    let right = arr.length - 1;
    while (left < right) {
      let sum = arr[left] + arr[right];
      if (sum === 0) {
        return [arr[left], arr[right]];
      } else if (sum > 0) {
        right--;
      } else {
        left++;
      }
    }
  }
  ```
