 # Object.create();
  - Prototype을 통한 상속방식의 문제점을 해결하기 위해 Object.create() 함수를 사용한다.
  - IE9, Chrome5, FireFox4, Safari5, Mobile FF4, Android 지원, Mobile Opera11.50, Mobile Safari 지원 이상 호환
  ```javascript
  //Object.create 함수
  Object.create = function (o) {
    function F() {}
    F.prototype = o; // <---
    return new F();
  }
  ```
  - 함수의 인자를 넘겨주는 부분이 prototype
  - 객체의 인스턴스와 인스턴스간의 상속을 강조하는 것이 특징

  ## Object.create()는 객체의 상속에서 InstanceOf함수로 상속받은 객체를 확인 할 수 없다.
   - 객체간의 상속에서는 Object.getPrototypeOf함수를 사용하면 객체의 prototype을 확인할 수 있다.
   ```javascript
   console.log("Object.create()에서 prototype으로 설정한 객체".isPrototypeOf("Object.create()의 return값을 받은 변수"));
   ```
  ## Object.create()의 객체 초기화
   - 2번째 인자를 `선택적`으로 받아 초기화 할 수 있다.
   ```javascript
   var unikys = Object.create(Person.prototype, {
       //기본 속성을 변경하지 않으면 read only
       name: {
           value: "Unikys"
       }
   });

   //기본 속성 변경
   var unikys = Object.create(Person.prototype, {
       name: {
           value: "Unikys" 
           configurable: true, 
           enumerable: true,
           writable: true
       }
   });
   ```
   - Object.defineProperty 설정 파라미터
     - value : 설정할 속성의 값 [default: undefined]
     - configurable : 속성을 지우거나 value 속성 이외의 설정 속성을 바꿀지 여부 [default: false]
     - enumerable : for-in 루프에서 해당 속성도 참조할지 여부 [default: false]
     - writable : 속성의 값을 설정 가능 여부 [default: false]
     - get 속성을 참조하게 되면 참조용으로 호출할 `함수` [default: undefined]
     - set 속성을 설정하게 되면 설정용으로 호출할 `함수` [default: undefined]

  ## Object.create()와 new 키워드 조합
   - 생성자의 연결이 깨지는 것을 보안
   ```javascript 
   Unikys.prototype = Object.create(Person.prototype, {
        constructor: {
            value: Unikys
        }
   });

   var unikys = new Unikys();
   ```