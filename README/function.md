# 함수
 ### 함수는 1급 객체다
 - 런타임 중 실행할 수 있다.
 - 변수에 할당할 수 있고 다른 변수에 참조를 복사 할 수 있으며 확장 가능하고 몇몇 특별한 경우를 제외하면 삭제할 수 있다.
 - 다른 함수의 인자값으로 전달 할 수 있고 다른 함수의 반환값이 될 수 있다.
 - 자기 자신의 프로퍼티와 메소드를 가질 수 있다.

 ### 함수는 유효범위(지역)를 제공한다.

 ## 용어정리

 ### 기명 함수 표현식
 ```javascript
 var add = function add(a, b) {
     return a + b;
 }
 ```

 ### 무명 함수 표현식, 익명 함수
 ```javascript
 var add = function (a, b) {
     return a + b;
 }
 ```

 ### 기명 함수와 익명 함수의 차이점
 - 함수 객체의 name 프로퍼티의 유무
 
 ### name 프로퍼티
 - 함수 선언문, 기명 함수 표현식을 사용하면 name 프로퍼티가 정의됨.
 - 익명 함수를 사용할 때 IE: undefined | Webkit, Firefox: 빈 문자
 - name 프로퍼티 값을 이름표로 사용하여 디버깅 할 때 사용.

 ### 함수 선언문과 표현식의 `호이스팅 방식`
 - 함수 선언식은 변수와 정의된 함수 모두 호이스팅 된다.
 - 함수 표현식은 변수는 호이스팅 되지만 정의된 함수는 호이스팅 되지 않는다.
 ```javascript
 function foo() {
     alert('global foo');
 }
 function bar() {
     alert('global bar');
 }

 function hoistMe() {
     console.log(typeof foo);
     console.log(typeof bar);

     foo();
     bar();

     function foo() {
         alert('local foo');
     }
     var bar = function() {
         alert('local bar');
     }
 }

 hoistMe();
 ```

 ### 콜백 패턴
 - 함수 표현식의 결과를 변수에 정의하지 않고 함수에 전달하는 방식
 ```javascript
 // 범용함수에서의 콜백함수
 var findNodes = function(callback) {
    var i = 10000, nodes = [], found;

    if(typeof callback !== "function") {
        callback = false;
    }

    while(i) {
        i -= 1;

        /*
            logic.....
        */
        if(callback) {
            callback(found);
        }

        nodes.push(found);
    }

    return nodes;
 }

 var hide = function(node) {
     node.style.display = "node";
 }

 findNodes(hide);
 ```

 ### 객체의 메서드를 사용한 콜백 함수의 문제점 
 - this가 가리키는 것이 불분명함. ex) 콜백이 사용되는 함수가 전역의 함수라면 this는 전역객체를 가리킨다.
 - 해결하기 위해서는 객체를 바인딩하는 것이 필요.

 ### 비동기 이벤트 리스너
 - 보통 클라이언트 측 브라우저 프로그래밍은 이벤트 처리방식이다. 비동기적으로 이벤트가 처리가 가능하다. 

 ### 타임아웃
 - setInterval, setTimeout, clearInterval 함수들은 콜백함수를 사용하는 함수.

 ### 라이브러리에서의 콜백
 - 콜백은 라이브러리를 설계할 때 매우 강력하다.
 - 연결고리 역할로써 콜백 함수를 사용하라.

 ### 즉시 실행 함수
 > 함수가 선언되자마자 실행되도록 하는 문법
 ```javascript  
 (function(){

 }());
 ```
 - 함수 표현식으로 선언한다.
 - 함수가 즉시 실행될 수 있도록 마지막에 괄호쌍을 추가.
 - 전체 함수를 괄호로 감싼다.(함수를 변수에 할당하지 않을 경우에만 필요)
