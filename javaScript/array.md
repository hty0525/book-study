# 배열 메서드

## 🧑🏻‍💻 원본 배열을 직접 수정하는 메서드

<br>

### 1. shift() - 배열의 천번째 원소를 삭제하고, 결과값으로 삭제된 원소 값을 반환

```
const arr = [1, 2, 3, 4, 5];

console.log(arr.shift()); // 1
console.log(arr); // [2, 3, 4, 5]

```

### 2. unshift() - 배열의 첫번째 인덱스에 원소를 추가하고, 결과값으로 배열의 새로운 길이를 반환

```
const arr = [1, 2, 3, 4, 5];

console.log(arr.unshift(6, 7)); // 7
console.log(arr); // [6, 7, 1, 2, 3, 4, 5]

```

### 3. push() - 배열의 마지막 인덱스에 원소를 추가하고, 결과값으로 새로운 길이를 반환

```
const arr = [1, 2, 3, 4, 5];

console.log(arr.push(6, 7)); // 7
console.log(arr); // [1, 2, 3, 4, 5, 6, 7]

```

### 4. pop() - 배열의 마지막 인덱스에 해당하는 원소를 삭제하고, 그 값을 결과 값으로 반환

```
const arr = [1, 2, 3, 4, 5];

console.log(arr.pop()); // 5
console.log(arr); // [1, 2, 3, 4]

```

### 5. splice() - 배열의 원소를 추가하거나 기존 요소를 삭제 또는 교체해 배열 데이터를 변경합니다. 결과값으로 삭제된 원소의 배열을 반환합니다.

- start
  배열의 변경을 시작할 index 배열의 길이보다 큰 값일 경우 배열의 길이로 설정 음수인 경우 배열의 끝에서부터 요소를 센다. <br>예 ) array.splice(-n) -> array.length -n과 같다. <br>값의 절대값이 배열의 길이보다 큰 경우 0으로 설정

- deleteCount(Optional)
  배열에서 제거할 요소의 수
  <br>생략하거나 값이 array.length - start보다 클 경우 start 부터의 모든 요소를 제거
  <br>0이하의 값을 설정 할 경우 어떤 요소도 제거하지 않음, 이 경우 최소한 하나의 새로운 요소를 추가해야한다.
- item1, item2, ...(Optional)
  배열에 추가할 요소<br>
  생략할 경우 요소를 제거하기만 한다. <br>
- 결과 값 -> 제거한 요소를 담은 배열, 아무것도 제거하지 않을 경우 빈 배열을 반환

출처 : <a href="https://tocomo.tistory.com/31" target="_blank">일본 도쿄에서 개발하며 놀고먹을 생각인 블로그</a>

요소만 제거

```
const arr = [1, 2, 3, 4, 5];

console.log(arr.splice(0,2)); // [1,2] 0번째부터 2개 제거
console.log(arr); // [3,4,5]

```

<br>
요소 제거 후 추가

```
const arr = [1, 2, 3, 4, 5];

console.log(arr.splice(0, 2, 6, 7, 8)); // [1, 2] 0번째부터 2개 제거한 값
console.log(arr); // [6, 7, 8, 3, 4, 5] 제거된 위치로부터 요소 추가

```

<br>
요소 제거 하지 않고 추가

```
const arr = [1, 2, 3, 4, 5];

console.log(arr.splice(0, 0, 6, 7, 8)); // [] 제거된 값이 없기 때문에 빈 배열 반환
console.log(arr); // [6, 7, 8, 1, 2, 3, 4, 5] 시작요소부터 추가

```

### 6. sort() - 배열의 원소를 정렬시켜 줍니다. 문자의 유니코드 값에 따라 정렬되며, 숫자도 문자로 반환하여 정렬하는 것을 유의해야 함

```
const arr = [1, 2, 4, 3, 5, 10000];

arr.sort();
console.log(arr); // [ 1, 10000, 2, 3, 4, 5 ] 유니코드 값에 따라 정렬되기 때문에 이렇게 나옴

```

숫자 정렬하기

```
const arr = [1, 2, 4, 3, 5, 10000];

arr.sort((a, b) => a - b); // 값이 더 작은게 앞으로 오게 오름차순으로 정렬
console.log(arr); // [ 1, 2, 3, 4, 5, 10000 ]
```

```
const arr = [1, 2, 4, 3, 5, 10000];

arr.sort((a, b) => b - a ); // 값이 더 큰게 앞으로 오게 내림차순으로 정렬
console.log(arr); // [ 10000, 5, 4, 3, 2, 1 ]
```

<br>
한글 정렬하기 - 유니코드값으로 비교를 하지 못하기 때문에 localeCompare을 사용하여 비교를 하는 것으로 생각된다.

<br>

> localeCompare란?
>
> 참조 문자열이 정렬 순으로 지정된 문자열 앞 혹은 뒤에 오는지 또는 동일한 문자열인지 나타내는 수치를 반환합니다.\
> 앞에 온다면 양수 뒤에온다면 음수 같다면 0을 반환한다.

<br>

```
const arr = ["별", "달", "태양", "은하수"];

arr.sort((a, b) => a.localeCompare(b));
console.log(arr); //[ '달', '별', '은하수', '태양' ]

```

<br>

영어 정렬하기

```
const arr = ["d", "f", "c", "t", "T", "A"];

arr.sort();
console.log(arr);
//[ 'A', 'T', 'c', 'd', 'f', 't' ] 대문자가 소문자보다 값이 작기 때문에 대문자가 항상 앞에온다.
//대,소 문자 구분없이 하고 싶다면.

arr.sort((a, b) => {
  if (a.toUpperCase() > b.toUpperCase()) return 1;
  if (a.toUpperCase() < b.toUpperCase()) return -1;
  if (a.toUpperCase() === b.toUpperCase()) return 0;
});
console.log(arr); //[ 'A', 'c', 'd', 'f', 't', 'T' ]


```
