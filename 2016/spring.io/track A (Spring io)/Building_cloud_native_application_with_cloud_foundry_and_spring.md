# Building Cloud Native applications with cloud foundary and spring
## 회고
* spring cloud 사용한 구현
* 개념적인 부분 기존에 공유된 부분가 다르지 않음.
* **MSA에 필요한 개념적인 부분을 Spring cloud가 지원을 해주는 장점이 있다.**
* 각각의 micro service의 인증을 위해서 각가 OAuth기반의 인증을 제공
* FK의 경우, Message Queue에서 보관해서 다른 마이크로서비스에서 참조가능하다.
* 각각의 micro service를 잘깨 찢고, 잘개 찢어진 micro service를 work flow에 구성한다.
work flow중에 오류가 나면, step을 그만둔다.

## 소개
* 발표자 : Kenny Bastani (Pivotal), Spring advocate team
  - Twitter : @kabastani
  - kbastani@pivotal.io
* Cloud nate java 참여자에게 pdf로 제공 짱!
* [kenny블로그|www.kennybastani.com]
  - 해당 사이트에 오늘 소개된 발표내용이 포함되어 있다.
  - **run.pivotal.io에 60일동안 build 할 수 있는 기능 제공**
  - 로컬에서 docker기반으로 MSA 실습할 수 있는 소스도 구성되어 있다.

## Agenda
* micro service 개념, cloud향 어플리케이션 어떻게 만들어야 하는가
* spring boot
* spring cloud 설정
* RESTFul microservice
* Microservice Reference App
  - Kenny가 만든 이커머스 sample app이 있음
  - 어떻게 spring cloud와 spring boot를 이용해서 cloud app을 만들수 있는가 확인 가능

## 배경
* Monolith architecture 문제
* SOA로 변경
  - 각각의 Service 팀은 존재하나 Data store는 공유
  - 각 서비스들로 Data를 공유하다 보니, 데이터나 스키마 변경시 다른팀에 영향이 없는지 확인하는데 공수가 많아짐
* Microservice 변경
  - **[중요] 전체 서비스에서 발생하는 트랜잭션을 어떻게 추적을 할 것인가? 어떻게 재연을 할 것인가?**
  - one service : one database
  - 각각의 service에서 공유해야 하는 정보들의 경우, shared cache가 필요 (ex. CouchBase 사용)
  - 각각의 서비스에 맞게 database구조를 가질 수 있다. (ex. user 인증 : rdb / 별점 서비스 : hdfs, 분석)

## Service Discovery
Monolith to Microservice
### 1. Configuration server
* Eureka 서비스 (Netflix에 제공하는 오픈소스)
 - 증설되는 마이크로서비스 컴포넌트가 추가 되는 경우, 어떻게 새로운 정보를 추가하는지 중요하다.
 - 추가되는 정보를 eureka를 통해서 쉽게 관리 가능
### 2. Discover Server
* 각각의 service를 수행을 하려면 어떤 service로 routing 해야하는지 필요한 값을 공유해주는 서버

## Spring initializer
Spring boot기반에 손쉬운 프로젝트 생성을 해주는 서비스
### Dependencies에 추가
** 아래에 dependency가 어떤 역할을 하는지 확인해보자! **
#### 1) micro service 1개 생성
* Actuator
 - 해당 microservice가 어떻게 동작하는지 확인가능한 서비스
* Rest Repositories
* Eureka Discovery
#### 2) Eureka server
**discovery service로 역할을 수행, client side에 로드 밸런싱 역할을 수행가능하다.**
* eureka server

## HA Proxy와 차이점
* HA Proxy같은 proxy서버의 경우, 설정을 변경하면 refresh해야 한다.
* 단, Eureka를 사용하면 인프라 레벨이 아닌 코드 레벨에서 동일한 기능을 동작 가능하다.
* 일정 시간 단위로 refresh되기 때문에, nice하다

## spring cloud
Spring boot 프로젝트를 만들어서 아래에 기능을 손쉽게 사용가능하다.
* netfilx oss, amazon service
* zookeeper, consul, cloud foundary

## API Gateway
Edge service

## Circuit Breakers
일종의 두꺼비집 같은 것. 각각의 service status를 모니터링하고 있다가, 200이 아니면 연결을 끊고,
자기가 오류 메세지를 대신 전달한다.
* Monolith : 각각의 서비스중에 하나라도 정상동작하지 않는다면 전체가 에러
* Microserverice page display : Circuite Breaker가 모니터링하고 있다가 동작이 정상이 아니면, 대신 자기가 오류 메세지 또는 상태를 전달한다

## Distributed Tracing
크롬 베이스, spring cloud가 현재 microservice가 어떻게 동작하는지, 응답속도가 어떻게 되는지 모니터링 해서 보여준다.
