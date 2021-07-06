## 스프링 웹 개발 기초
* 정적 컨텐츠 
* MVC와 템플릿 엔진 
* API 

<br> 

### 정적 컨텐츠
> 예제 코드 작성 후
* 웹 브라우저에서 local:host:8080/hello-static.html 로 연결 시도
* 내장 톰캣 서버가 요청을 받고 우선 스프링 컨테이너에 가서 hello-static이 있는지 찾아봄.
* hello-static이라는 컨트롤러가 없는 것을 확인하고 resources안에 hello-static.html을 찾아서 반환함.
* 내용을 일일히 만들어서 web browser에 그대로 내려줌.
  
<br> 

### MVC와 템플릿 엔진
* MVC : Model + View + Controller 
* 템플릿 엔진 : html을 동적으로 바꿔서 내려주는 것
* 가장 많이 쓰임.
> 예제 코드 작성 후
* 웹 브라우저에서 local:host:8080/hello-mvc.html 로 연결 시도
* 내장 톰캣 서버가 요청을 받고 Controller에 매핑이 되어있는 hello-mvc 메소드를 찾아냄
* return을 할 때 이름은 hello-template, model은 key는 name, value는 spring으로 ViewResolver에게 보내줌.
* ViewResolver는 hello-template이라는 이름을 가진 html을 발견하고 Thymeleaf(템플릿 엔진)에게 처리를 부탁함.
* Thymeleaf가 렌더링을 해서 변환한 페이지를 반환함.

### API
* JSON이라는 데이터 포맷으로 클라이언트에게 데이터를 전달하는 방식.
* 실행 결과는 MVC와 별 다를 바 없어 보이나, 페이지 소스를 보면 차이가 난다. html언어 없이 그냥 입력한 데이터를 바로 페이지에 띄운다.
> 예제 코드 작성 후
* 웹 브라우저에서 local:host:8080/hello-mvc.html 로 연결 시도
* 내장 톰캣 서버가 요청을 받고 Controller에 매핑이 되어있는 hello-api 메소드를 찾아냄
* 그런데 해당 메소드에 @ResponseBody annotation이 붙어있음. 
* HTTP의 BODY에 문자 내용을 직접 반환하게 됨. 근데 예제 코드 기준으로는 객체를 반환 하게 됨.
* ViewResolver 대신 HttpMessageConverter가 작동하여 단순 문자면 StringConverter, 객체면 JsonConverter가 동작함.
