 # Array Method
  ### concat
  - 2개 이상의 배열을 하나의 배열에 합쳐주는 메소드
  - array1.concat(array2, arrat3, ..., arrayX)

  ### constructor
  - 객체가 Object 생성자의 prototype으로써 기본적으로 가지고 있는 것
  - Array() 생성자와 linking시켜주는 역할

  ### copyWithin
  - 배열의 내용 중 연속된 특정한 elements를 뽑아서 배열의 index만큼 elements들을 반복해서 값 복사를 시키는 함수.
  - array.copyWithin(target, start, end)

  ### entries
  - 배열의 각 인덱스에 대한 key/value 쌍을 가지는 새로운 Array Iterator 객체를 반환합니다.
  ```javascript
    var fruits = ["Banana", "Orange", "Apple", "Mango"];
    var entries = fruits.entries();
    console.log(entries.next().value); // [0, "Banana"]
    console.log(entries.next().value); // [1, "Orange"]
    console.log(entries.next().value); // [2, "Apple"]
    console.log(entries.next().value); // [3, "Mango"]
  ```

  ### every
  - 조건식을 통해 배열의 모든 elements를 체크한다.
  - array.every(function(currentValue, index, arr), thisValue);
  ```javascript
    function checkAdult(age) {
      return age >= 18;
    }
    array.every(checkAdult);
  ```
  
  ### fill 
  - 하나의 리터럴 값을 배열의 모든 element에 채운다.
  - array.fill(value, start, end);
  
  ### filter
  - 특정한 조건식으로 배열안의 내용을 걸러서 출력하게 할 수 있는 함수
  ```javascript
  var words = ["spray", "limit", "elite", "exuberant", "destruction", "present"];

  var longWords = words.filter(function(word){
    return word.length > 6;
  })

  // Filtered array longWords is ["exuberant", "destruction", "present"]
  ```

  ### find
  - 특정한 조건에 맞는 배열의 첫번째 값을 반환하는 함수
  ```javascript
  function isBigEnough(element) {
    return element >= 15;
  }

  [12, 5, 8, 130, 44].find(isBigEnough); // 130
  ```

  ### findIndex 
  - 특정한 조건에 맞는 배열의 첫번째 값의 인덱스를 반환하는 함수
  ```javascript
  [1,2,3].findIndex(function(x) { x == 2; });
  // Returns an index value of 1
  ```

  ### foreach
  - Array의 프로토타입으로 가지고 있는 반복문
  - function callbackfn(value, index, array1)
  ```javascript
  // Create an array.
  var numbers = [10, 11, 12];

  // Call the addNumber callback function for each array element.
  var sum = 0;
  numbers.forEach(
      function addNumber(value) { sum += value; }
  );

  document.write(sum);
  // Output: 33
  ```

  ### includes
  - ES6
  - 전달된 문자열이 문자열 개체에 포함되어 있는지 여부를 나타내는 부울 값을 반환
  ```javascript
  // Returns true 
  "abcde".includes("cd")
  "abcde".includes("cd", 2)

  // Returns false
  "abcde".includes("CD")
  "abcde".includes("cd", 3)
  ```