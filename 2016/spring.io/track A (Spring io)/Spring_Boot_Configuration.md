![](https://github.com/gregor77/conference/blob/master/2016/spring.io/spring_configuration.jpg)

## 적용 가능성
* 기존에 @Profile를 사용해서 cache(internal/external) 구분햇는데..
 - @Conditional으로 변경 가능할 듯 (각 cache의 property가 있을때만 Bean으로 등록하도록)
 - 단, 조건이 통과하는 구현체는 생성 필요. Condition interface 구현
 - **@Profile이 어차피 @Conditional 구현이기 때문에.. 크게 차이가 없기는 하다..**

## @EnableAutoConfiguration
META-INF/spring.factories 파일을 참조해서, 모든 클래스를 로딩한다.
**단, 해당파일에 정의된 모든 클래스를 컨테이너에 등록하는 것은 아니다.**
* 지난번에, mtda-portal 수행시, log level을 debug로 하고 수행했을때, 사용하지 않는 클래스를
로딩하는 이유가 이 때문이다.

## @Conditional
Spring boot는 @Conditional*을 사용해서, 의존성을 구현함.
@Profile 도 내부에서 @Conditional을 사용해서 구현되어 있음.
### 확장
* @ConditionalOnBean
  - 해당 Bean을 사용하려면 Datasource가 미리 선언되어 있어야 하는 경우 사용 가능하다

## 커스텀 모듈 만들기
Spring Configuration을 이해해서 커스텀 모듈을 생성 가능.
```
  1. spring.factories 파일을 만들어서, 커스텀 Configuration 파일을 추가한다.
  2. 사용하고자 하는 프로젝트에서 dependency만 추가한다.
```
* **spring 버전 4이상에서 spring boot를 사용할 수 있다. spring 4이상에서 smurf-mtda 재구성가능하다.**
datasource 정의 체크도 가능.
* 이를 활용하면 잘게잘게 jar를 만들게 되면, plugin 구성을 하는 것처럼 필요할때 마다 그룹을 구성해서 재활용이 가능하다.

## 커스텀 모듈 만들때 주의사항
깔끔할 수는 있지만, 내부에서 어떤 일을 하는지 눈에 보이지 않는다.
* [추천] 자기가 사용하는 소스를 확인해보는 것을 추천
  - 의존성이 있는 소스에 @Conditional* 관련된 조건을 알 필요가 있다.
  - 로그로 Condition 조건을 확인하기 위해서는 log level 변경이 필요하다
  - log.level.springframework.boot = debug

## QnA
