@RequestMapping <br>
  1.RequestMappingHandlerMapping <br>
    RequestMappingHandlerMapping 은 스프링 빈 중에서 @RequestMapping 또는 @Controller 가 <br>
    클래스 레벨에 붙어 있는 경우에 매핑 정보로 인식한다. <br>
  2.RequestMappingHandlerAdapter  <br>
    스프링 requestmapping 어노테이션은 핸들러와 핸들러를 처리할 수 있는 핸들러 어댑터 조회를 자동으로 해준다.  <br>
 <br>
@Controller   <br>
  스프링이 자동으로 스프링 빈으로 등록한다. (내부에 @Component 애노테이션이 있어서 컴포넌트 스캔의 대상이 됨) <br>
  스프링 MVC에서 애노테이션 기반 컨트롤러로 인식한다. -> RequestMappingHandlerMapping이 핸들러의 대상으로 조회한다는 말이다. <br>
  -> 1. ComponentScan의 대상이되고 2.RequestMappingHandlerMapping의 대상이 된다 <br>

@RestController <br>
@Controller 는 반환 값이 String 이면 뷰 이름으로 인식된다. 그래서 뷰를 찾고 뷰가 랜더링 된다.<br>
@RestController 는 반환 값으로 뷰를 찾는 것이 아니라, HTTP 메시지 바디에 바로 입력한다. 
따라서 실행 결과로 ok 메세지를 받을 수 있다. @ResponseBody 와 관련이 있다  <br><br>

@RequestMapping("/springmvc/v1/members/new-form") ModelAndView 메서드명() { return new ModelAndView("경로" ex)"new-form"); <br>
  요청 정보를 매핑한다. 해당 URL이 호출되면 이 메서드가 호출된다. 애노테이션을 <br>
  기반으로 동작하기 때문에, 메서드의 이름은 임의로 지으면 된다. <br>
 <br>
@RequestMapping은 스프링에서 HTTP METHOD를 제한해두지않았다.  <br>
하지만 단순조회는 get으로 변경이나 저장은 post로 하는 것이 좋은 설계이다. <br>
->@GetMapping @PostMapping <br>
 <br>
@RequestParam 사용 <br>
스프링은 HTTP 요청 파라미터를 @RequestParam 으로 받을 수 있다. <br>
@RequestParam("username") 은 request.getParameter("username") 와 거의 같은 코드라 <br>
생각하면 된다. <br>
물론 GET 쿼리 파라미터, POST Form 방식을 모두 지원한다 <br>
```
  @PostMapping("/save")
    public String save(
            @RequestParam("username") String username,
            @RequestParam("age") int age,
            Model model) {
        Member member = new Member(username, age);
        memberRepository.save(member);

        model.addAttribute("member", member);
        return "save-result";
    }
```

PathVariable(경로 변수) 사용

 * PathVariable 사용
 * 변수명이 같으면 생략 가능
 * @PathVariable("userId") String userId -> @PathVariable userId
 */
```
@GetMapping("/mapping/{userId}")
public String mappingPath(@PathVariable("userId") String data) {
 log.info("mappingPath userId={}", data);
 return "ok";
}
```
