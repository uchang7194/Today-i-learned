# 메모리 누수

## garbage collection
 - 참조되지 않은 값은 모두 제거한다.
 - 하지만 그렇지 않은 경우도 있다.

 ### reference-count 알고리즘
 - 참조를 하지 않는 Object들을 모두 제거하는 알고리즘이다.
 - reference-count 알고리즘은 참조-세기라는 2012년 이전 garbage 컬렉션의 알고리즘이다( IE6, 7 )
 - 문제점은 참조가 순환이 된다면 메모리 누수가 일어나게 된다.
 ```javascript
 function f(){
    var o = {};
    var o2 = {};
    o.a = o2; // o는 o2를 참조한다.
    o2.a = o; // o2는 o를 참조한다.
    
    return "azerty";
    }
 
 f();
 ``` 
 - 위의 함수를 실행하면 o, o2의 변수에 할당 되어 있는 Object가 garbage 컬렉션에 의해 지워져야 하지만 지워지지 않는다. 왜냐하면 위의 소스를 보면 o.a가 o2를 가리키고 있고 o2.a가 o를 가리키고 있는 순환구조이기 때문이다.
 - 이 문제를 해결하기 위해 2012년 기준으로 모든 브라우저는 Mark-and-Sweep 알고리즘을 사용한다.

 ### Mark-and-Sweep 알고리즘
 - root(전역객체)로 부터 참조 되지 않는 모든 객체를 제거하는 알고리즘.
 - 참조-세기 알고리즘이 닿을 수 없는(순환 참조) Object를 제거하지 못한다면 표시하고-쓸기 알고리즘은 root객체가 닿을 수 없는 Object라면 제거하기 때문에 좀더 효율적이다. 


 [참고자료](https://developer.mozilla.org/ko/docs/Web/JavaScript/Memory_Management)