# gulp에 대해 알아보자~~~~~~~~~~~~~~`
[전부 여기서 가져옴](http://programmingsummaries.tistory.com/356)

## gulp란?
> Gulp는 streaming build system을 표방한다. 즉, Node의 스트림 기능으로 인해 이득을 얻는 빌드 시스템.

### Build System 
- 빌드 시스템은 프로젝트를 development, production, testing 등의 다른 빌드들로 빌드해준다. 

## gulp 설치 과정
1. npm init
 - package.json 파일을 자동으로 생성해준다.

2. npm install gulp -g
 - gulp를 전역으로 설치하는게 좋다고 한다. 이유는 인터넷이 되지 않는 환경에서는 전역에 설치한 gulp를 복사해서 설치할 수 있기 때문.

3. gulp 및 몇가지 디펜던시를 프로젝트에 설치하기
 - npm install gulp --save-dev
 - `--save-dev`: 이 플래그를 추가하면 디펜던시들을 devDependecy로써만 설치하게 된다. 이유는 gulp와 관련 디펜던시들은 어플리케이션 개발 과정까지만 필요하기 때문.
   - gulp의 플러그인을 설치할 때도 사용해야함.

## Folder Structure
 - src(source), dist(distribution) 
   - src: src폴더는 아무런 처리를 하지 않은 파일들이 들어가게 된다.
   - dist: gulp에 의해서 빌드된 파일들이 들어가게 된다.
     - `dist`폴더는 .gitignore에 추가한 뒤 직접 빌드한다.

 1. gulpfile.js
   > gulp의 설정이 담겨진 파일.
   - gulpfile에서 gulp와 gulp plugin을 사용하기 위해서는 npm으로 설치하고 require을 통해 해당 gulp나 plugin의 객체를 받아와서 사용을 해야한다.

 2. gulp.task(name, deps, func) 
   > gulp가 해야할 역할을 설정.
   - name: task의 이름을 지정(이름에는 공백x)
   - deps: 현재 선언하고 있는 task를 수행하기 전에 먼저 실행되어야하는 task들의 배열 (생략가능)
   - func: 실제 수행할 task의 내용을 정의하는 function

 3. gulp.src(files)
   > gulp.src(files)는 파일이나 파일의 경로들이 포함된 배열 또는 string이다.
   - js/**/*.js: 와일드카드 형태, js/폴더와 내부폴더의 .js파일들을 모두 긁어오게 된다.

 4. gulp.pipe(...)
   > plie를 사용해서 task들의 결과물들을 function들에게 전달해줄 수 있다.
   ```javascript
   gulp.src('public/src/js/*.js')
       .pipe(stripDebug())
       .pipe(uglify())
       .pipe(concat('script.js'))
       .pipe(gulp.dest('public/dist/js'))
   ```
   1. gulp.src는 public/src/js 폴더의 모든 js파일을 긁어온다.
   2. 그 다음 stripDebug에게로 파이핑(piping) 해준다.(striptDebug는 모든 console.log들과 alert들을 제거해준다.)
   3. 그 다음 uglify로 파이핑 해준다.(uglify는 javascript를 압축해준다.)
   4. 그 다음2번 3번의 결과로 console.log와 alert가 제거되고 압축된 모든 파일들을 script.js파일 하나로 병합해준다.
   5. 마지막으로 이 파일을 gulp.dest()로 보내준다. 이 파일이 output파일로 쓰여진다.

   



