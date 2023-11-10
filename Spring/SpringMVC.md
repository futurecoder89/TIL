동작 순서  <br>
1. 핸들러 조회: 핸들러 매핑을 통해 요청 URL에 매핑된 핸들러(컨트롤러)를 조회한다.  <br>
2. 핸들러 어댑터 조회: 핸들러를 실행할 수 있는 핸들러 어댑터를 조회한다. <br>
3. 핸들러 어댑터 실행: 핸들러 어댑터를 실행한다. <br>
4. 핸들러 실행: 핸들러 어댑터가 실제 핸들러를 실행한다. <br>
5. ModelAndView 반환: 핸들러 어댑터는 핸들러가 반환하는 정보를 ModelAndView로 변환해서 <br>
반환한다. <br>
6. viewResolver 호출: 뷰 리졸버를 찾고 실행한다. <br>
JSP의 경우: InternalResourceViewResolver 가 자동 등록되고, 사용된다. <br>
7. View 반환: 뷰 리졸버는 뷰의 논리 이름을 물리 이름으로 바꾸고, 렌더링 역할을 담당하는 뷰 객체를 <br>
반환한다. <br>
JSP의 경우 InternalResourceView(JstlView) 를 반환하는데, 내부에 forward() 로직이 있다. <br>
8. 뷰 렌더링: 뷰를 통해서 뷰를 렌더링 한다. <br>
   <br>![mvc](https://github.com/futurecoder89/TIL/assets/115630753/451b1f42-894f-415d-922c-5692fc94f8df)
