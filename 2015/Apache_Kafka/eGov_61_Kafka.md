# 분산 메시지 시스템 Apache Kafka 시작하기
평소 기술에 관심이 많은 선배님이 Kafka 주제로하는 기술세미나가 있는데 관심있으면 같이 가보자고 추천해서, 처음으로 "표준프레임
워크 오픈커뮤니티"에 대해서 알게 되었다. 해당 커뮤니티에서는 **정기적으로 기술 세미나를 진행하고 있었고, 기술 세미나 공지가 뜨면, 댓글로 참가 신청을 하면 된다.**

[참고] [61회 기술세미나 참가 신청 ](http://open.egovframe.kr/cop/bbs/selectBoardArticle.do?bbsId=BBSMSTR_000000000014&nttId=16779)

## 세미나 정보
**Apache Kafka(아파치 카프카)**는 LinkedIn에서 개발된 분산 메시징 시스템으로써 2011년에 오픈소스로 공개되었다. **분산 환경에서 대용량의 실시간 로그처리에 특화되어 있다는 점과 복사본을 다른 노드에 저장을 통해서 장애에 대한 대응성 또한 뛰어난 특징이 있다.**

* 주제 : 분산 메시지 시스템 아파치 카프카 시작하기
* 일시: 2015.10.26(월) 19:00 ~ 21:00 (120분)
* 내용  
  - Apach Kafka 소개 및 설치
  - Apach Kafka 구성요소 설명 및 구현
  - Kt IoT Makers 소개 및 데모
* 발표자 소개 : 고재도 강사
  - 現 표준프레임워크 오픈커뮤니티 커미터
  - 現 Kt Convergence  연구소 전임연구원
  - 現 GDG Korea WebTech 운영자

## 느낀점
#### 1. 시작하기 전에
세미나 당일 집합교육 중이었기 때문에 교육이 끝나자마자 D.CAMP까지 걸어갔다. 평소에 앱으로 부터 메세지를 분산처리 환경에 수집하고, 데이터를 분석하는 일련의 프로세스에 대해서 관심이 있었다. **전체를 볼 수 있는 눈이 작았고, 많은 기술들과 그 기술들이 만들어놓은 생태계를 가늠하는것 조차 어려워 기회가 되면 세미나 참석을 하려는 편이다.**

빨리 가야 겠다는 생각으로 열심히 걷다보니, 저녁도 깜빡하고 D.CAMP에 제일 먼저 도착했다. 저녁을 못 먹고 갔는데 다행히 샌드위치와 음료를 준비해주셔서 맛있게 먹고 기분 좋은 상태에서 세미나를 들을 수 있었다.

운영 스텝분들이 설문 조사도 하고 있었다. 설문지 내용은 어떻게 이 세미나를 알게 되었는가? 오픈 커뮤니티 리더들이 있는데, 그들과 함께 활동을 한다면 프로젝트 수행, 개발자 토론회, 멘토링 등 중에서 어떤 것을 하면 좋겠는가? 라는 질문이 주였다. 커뮤니티 리더 중에 **토비의 스프링의 저자, 이일민 님도 있었다.**

설문 조사를 하면서 더 나은 세미나를 위해 노력하는 사람들이 멋져 보였다. 다음에 기회가 되면 고수님들과 함께하는 활동을 하면 재미있을 것 같았다. 그리고 다음에 올때는 나도 주위에 관심있는 후배와 함께 와야겠다. 이번에 선배님을 통해서 좋은 기회를 얻은 것처럼 나도 다른 누군가에게 좋은 기회를 함께 하고 싶어졌다.

![](https://github.com/gregor77/conference/blob/master/2015/Apache_Kafka/image/enterance.jpg)
![](https://github.com/gregor77/conference/blob/master/2015/Apache_Kafka/image/seminar1.jpg)

#### 2. 세미나 관련
그림에서 Kafka가 있는 위치가 Message broker 역할을 수행하며, Active MQ, Rabbit MQ든 상황에 따라 그 역할을 대신 할 수 있다.

![](https://github.com/gregor77/conference/blob/master/2015/Apache_Kafka/image/Apache_Kafka.png)

Kafka는 전통적인 메세지 서버인 Active MQ, Rabbit MQ와 비교해서 장점은?

* 복제가 쉽기 때문에 메세지가 아주 많은 곳에 적합하다.
* 메세지가 많으면 많을 수록, 전통적인 메세지 서버에 비해서 성능이 우수하다.
* Kafka는 disk 기반에 메세지가 저장되므로, 메모리에 메세지가 관리되는 전통적인 메세지 서버에 비해서 손실이 없다.

![](https://github.com/gregor77/conference/blob/master/2015/Apache_Kafka/image/compare_performance.png)

**가장 좋았던 점은, 스프링 부트와 java를 기반의 퀵 스타트 소스를 직접 보며, 실제 개발시에 어떻게 적용할 수 확인할 수 있었던 점이다.** 이 시간을 통해서 업무에 적용할 때 많은 인사이트를 얻을 수 있었다.

개인 사정 때문에 세미나 마지막 부분에 나와야 해서, SK IoT Framework에 적용사례는 듣지 못한 점이 개인적으로는 아쉬웠다. 발표 자료를 보니, 시간을 기준으로 많이 데이터가 많이 발생하는 센서의 메세지 수집에 Kafka를 적용한 것으로 보였다. 센서등의 IoT의 경우 짧은 시간에 많은 양의 데이터가 수집되므로 Active MQ, Rabbit MQ에 비해서 Kafka가 더 적합하다는 생각이 들었다.

이번 세미나를 통해서 Real time app으로 부터 Kafka를 통해서 메세지를 수집하고, Hadoop File system 기반에서 hive, spark, elastic search 를 통한 데이터 분석의 연결고리가 그려저서 개인적으로는 만족스러운 시간이었다.

## Kafka 관련 자료
* [Apache Kafka 공식 홈페이지](http://kafka.apache.org/)
* [inpoq Kafka 관련 기사](http://www.infoq.com/articles/apache-kafka)
* [세미나 발표 자료](http://open.egovframe.go.kr/cop/bbs/selectBoardArticle.do?bbsId=BBSMSTR_000000000015&nttId=16844)
* [세미나 현장 사진](http://open.egovframe.kr/cop/bbs/selectBoardArticle.do?bbsId=BBSMSTR_000000000014&nttId=16863)
* [Apache Kafka 소개 및 정리](http://epicdevs.com/17)
