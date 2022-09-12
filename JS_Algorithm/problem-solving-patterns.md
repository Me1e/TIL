# 문제 해결 패턴

## Frequency counter

### 1) Same frequency

- Write a function called `same`, which accepts two arrays. The function should return true if every value in the array has it's corresponding value squared in the second array. The frequency of values must be the same.
- Examples:

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
- Examples:

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
