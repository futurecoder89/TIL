- SLF4J - http://www.slf4j.org   <br>
- Logback - http://logback.qos.ch <br>

로그 라이브러리는 Logback, Log4J, Log4J2 등등 수 많은 라이브러리가 있는데, 그것을 통합해서
인터페이스로 제공하는 것이 바로 SLF4J 라이브러리다.
쉽게 이야기해서 SLF4J는 인터페이스이고, 그 구현체로 Logback 같은 로그 라이브러리를 선택하면 된다. <br>
실무에서는 스프링 부트가 기본으로 제공하는 Logback을 대부분 사용한다 <br>
<br>
**로그 선언** <br>
-private Logger log = LoggerFactory.getLogger(getClass());<br>
-private static final Logger log = LoggerFactory.getLogger(Xxx.class)<br>
-@Slf4j : 롬복 사용 가능<br><br>
**로그 호출**<br>
-log.info("hello")<br>
-System.out.println("hello")<br>
-log.debug("data={}", data) {}안에 레벨을 설정하면된다<br>
-시스템 콘솔로 직접 출력하는 것 보다 로그를 사용하면 다음과 같은 장점이 있다. 실무에서는 항상 로그를
사용해야 한다.<br>

#hello.springmvc 패키지와 그 하위 로그 레벨 설정할수있다. application.properties에 추가하면된다<br>
logging.level.hello.springmvc={} trace,debuf,info,warn,error
<br><br>
**로그가 출력되는 포멧**<br>
- 시간, 로그 레벨, 프로세스 ID, 쓰레드 명, 클래스명, 로그 메시지<br><br>
**로그 레벨 설정을 변경해서 출력 결과를 보자.** <br>
- LEVEL: TRACE > DEBUG > INFO > WARN > ERROR <br>
- 개발 서버는 debug 출력 <br>
- 운영 서버는 info 출력 <br>


**로그 사용시 장점** <br>
쓰레드 정보, 클래스 이름 같은 부가 정보를 함께 볼 수 있고, 출력 모양을 조정할 수 있다.
로그 레벨에 따라 개발 서버에서는 모든 로그를 출력하고, 운영서버에서는 출력하지 않는 등 로그를 상황에
맞게 조절할 수 있다.
시스템 아웃 콘솔에만 출력하는 것이 아니라, 파일이나 네트워크 등, 로그를 별도의 위치에 남길 수 있다. 
특히 파일로 남길 때는 일별, 특정 용량에 따라 로그를 분할하는 것도 가능하다.
성능도 일반 System.out보다 좋다. (내부 버퍼링, 멀티 쓰레드 등등) 그래서 실무에서는 꼭 로그를
사용해야 한다.
