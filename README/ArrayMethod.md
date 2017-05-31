 ## Array Method
  - concat
    - 2개 이상의 배열을 하나의 배열에 합쳐주는 메소드
    - array1.concat(array2, arrat3, ..., arrayX)

  - constructor
    - 객체가 Object 생성자의 prototype으로써 기본적으로 가지고 있는 것
    - Array() 생성자와 linking시켜주는 역할

  - copyWithin
    - 배열의 내용 중 연속된 특정한 elements를 뽑아서 배열의 index만큼 elements들을 반복해서 값 복사를 시키는 함수.
    - array.copyWithin(target, start, end)

  - entries
    - 배열의 각 인덱스에 대한 key/value 쌍을 가지는 새로운 Array Iterator 객체를 반환합니다.
  ```javascript
    var fruits = ["Banana", "Orange", "Apple", "Mango"];
    var entries = fruits.entries();
    console.log(entries.next().value); // [0, "Banana"]
    console.log(entries.next().value); // [1, "Orange"]
    console.log(entries.next().value); // [2, "Apple"]
    console.log(entries.next().value); // [3, "Mango"]
  ```

  - every
    - 조건식을 통해 배열의 모든 elements를 체크한다.
    - array.every(function(currentValue, index, arr), thisValue);
  ```javascript
    function checkAdult(age) {
      return age >= 18;
    }
    array.every(checkAdult);
  ```
  
  - fill 
    - 하나의 리터럴 값을 배열의 모든 element에 채운다.
    - array.fill(value, start, end);