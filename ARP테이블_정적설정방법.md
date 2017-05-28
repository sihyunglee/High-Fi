arp -s 명령어로는 정적 설정이 안 되는 경우가 있으며(예: 게이트웨이), 이럴 때 아래와 같이 netsh 명령으로 추가

&nbsp;

netsh interface ip add neighbors "인터페이스이름" IP주소 MAC주소 

&nbsp;

예를 들어 아래와 같이 3개의 NIC가 있을 때

&nbsp;

netsh interface show interface 

&nbsp;

관리 상태      상태              종류               인터페이스 이름

===========================================================&nbsp;

사용             연결됨            전용               VMware Network Adapter VMnet1&nbsp;

사용             연결됨            전용               VMware Network Adapter VMnet8&nbsp;

**사용             연결됨            전용               이더넷**&nbsp;

===========================================================

&nbsp;

마지막 인터페이스에 192.168.0.1과 90-9f-33-17-71-84를 정적으로 설정하고자 한다면

&nbsp;

netsh interface ip add neighbors "이더넷" 192.168.0.1 90-9f-33-17-71-84

&nbsp;