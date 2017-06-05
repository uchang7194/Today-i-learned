# 모듈 패턴
 - 자바스크립트 소스를 모듈 단위로 관리하거나 라이브러리 등을 만들 때 사용하는 모듈패턴
 - 사용목적 : 서버개발을 하거나 라이브러리, API를 개발할 때 유용하게 사용.
 - 하나의 대표 글로벌 변수 안에 여러 함수를 두는 것이 모듈패턴
 ```javascript
 //jQuery $
 $.get("/api/unikys").done(function (return) {
     var unikys = result;
     console.log(unikys);
 })
 ```
 
 ## 기본 패턴
 ```javascript
 (function (window){
     var myLibrary = {
         helloWorld: function (){
            alert('helloWorld');
         },
         hello: {
             world: function (){
                 alert('Hello Module!!!');
             }
         }
     }

     //window객체의 myLibrary라는 변수에 myLibrary를 넘긴다.
     window.myLibrary = myLibrary;
     
 }(window));
 ```
 - 글로벌 변수에 모듈 패턴을 할당하는 형태
 ```javascript 
 var myLibrary = (function (window) {
    var myLibrary = {
        
    };

    return myLibrary;
 }(window));
 ```

 - 객체 표현식으로 모듈 패턴을 할당하는 형태
 ```javascript
 var myLibrary = (function (window){
     return {

     };
 }(window));
 ```
 - 다양한 기능들을 가지는 모듈패턴의 용도를 명확히 구분하기 위해서 모듈패턴을 확장하여 네임스페이스로 활용하는 것이 일반적.
 - 네임스페이스 생성 방법
 ```javascript
 (function (windows, undefined) {
    var _myLibrary = window.myLibrary;
    
    if(!_myLibrary) {
        _myLibrary = {};
    }
    if(!_myLibrary.unikys) {
        _myLibrary.unikys = {};
    }

    _myLibrary.unikys.sayHello = function() {
        alert('Hello, my name is Unikys');
    };

    window.myLibrary = _myLibrary;
 }(window))
 ```
 