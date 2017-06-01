# Prototype
 - 프로토타입 동작 방식 
  
  ```
    ┏━━━━━━━━━━┓
      [생성자]      [linking]    ┏━━━━━━━━━━━━━━━━━━┓
      prototype ━━━━━━━━━━━━━━>   [prototype object]
                                      Object 객체 
     __proto__  ━━━━━━━━━━━━━━>                               
                <━━━━━┓          ┗━━━━━━━━━━━━━━━━━━┛  
    ┗━━━━━━━━━━┛      ┃                 ＾ ＾
         ┃            ┃                  ┃ ┃ 
        new           ┃                  ┃ ┃   
         ┃            ┃                  ┃ ┃ [linking] 
         ˇ            ┃                  ┃ ┃ [method, property를 가져와서 사용]   
    ┏━━━━━━━━━━━━┓    ┃                  ┃ ┃
        [객체]     ━━━┃━━━━━━━━━━━━━━━━━━━━┛ 
      constructor ━━━━┛                  ┃  
      __proto__ ━━━━━━━━━━━━━━━━━━━━━━━━━┛
    ┗━━━━━━━━━━━━┛
  ```

  - Prototype : 객체의 원형인 prototype을 이용하여 새로운 객체를 만들어내는 프로그래밍 기법.(원형을 이용하여 객체를 확장하는 방법)
      - 어떠한 객체가 만들어지기 위해 그 객체의 모태가 되는 것
      - javaScript는 prototype을 이용한 cloning과 객체를 확장해 나가는 방식을 통해 새로운 객체를 생성.
      - javascript의 prototype 객체의 확장은 옵저버 패턴을 따른다.
      - Prototype property 
        - 객체가 생성될 때 생성된 객체는 prototype이라는 property를 가지고 있는데 이 property는 객체 자신의 모태가 되는 prototype 객체를 가리키고 있다.
        - 모든 객체는 Object 객체의 prototype을 기반으로 확장 되었기 때문에 이 연결의 끝은 prototype Object이다. 
      - Prototype Property가 가리키고 있는 Prototype Object
        - 객체의 Prototype Property를 변경하려면 Prototype Object를 사용해야 한다. ex) Object.prototype.VALUE
      - 객체의 원형을 의미하는 Prototype Link
        - 상위에서 물려받은 객체의 프로토타입에 대한 정보

## hasOwnProperty
  - 객체의 속성을 보여주는 함수 (함수는 제외)
  ```javascript
  for (prop in unikys) {
	unikys.hasOwnProperty(prop) && console.log("unikys[" + prop + "] = " + unikys[prop]);
  }
  ```
## 장단점

### 장점

- 생성자 안에 속성을 부여하는 방식은 속성이 적을 때 사용하는게 좋다. 이유는 생성자 안에 바로 속성을 부여하게 되면 그 속성들 자체가 메모리의 공간을 차지하기 때문에 속성을 많이 적용할 때는 prototype을 통해 사용하는 것이 좋다. 
- 속성의 내용을 변경하려는 경우 prototype은 한번만 처리하면 전부 바뀌지만 생성자안의 속성은 전부 다 일일이 바꿔줘야하는 단점이 있다. 
- hasOwnProperty는 생성자의 method를 구별하지 못하기 때문에 생성자에 hasOwnProperty를 사용하더라도 method를 보여주게 된다.

### 단점

- 이해하기 어렵다
- prototype chain을 따라서 검색하는 속성 탐색시간이 길어진다.
- 되도록이면 prototype에 있는 값들은 기본값으로만 활용하고 객체 자체의 속성으로 활용하는 것이 좋다.
