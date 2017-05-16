netsh wlan show networks mode=bssid

&nbsp;

- 현재 연결 가능한 모든 WiFi 정보를 보여줌
- 각 WiFi 별로 SSID, BSSID, 인증방법, 암호화방법, 신호세기, 버전(802.11n, g 등), 채널, 속도 등을 보여줌
- SSID는 unique하지 않으나 가독성이 높고 BSSID는 unique하나 가독성 떨어지므로(MAC주소 형식) 두 가지를 조합하여 WiFi 이름으로 사용하면 될 듯함
- 만약 "무선 자동구성 서비스가 실행되고 있지 않다"는 오류가 뜨면 Windows 시작창에서 service.msc(구성 요소 서비스) 실행하고 서비스(로컬) → WLAN AutoConfig 를 우측클릭하여 "시작"하면 해결됨
- 약 1분 간격으로 주기적으로 리스트를 refresh(rescan)함
- 하지만 현재 WiFi AP에 연결된 상태라면 주기적으로 rescan하지 않으므로 위 명령을 실행하여도 최신 정보를 얻지 못함. 따라서 아래와 같이 WiFi NIC을 비활성화 후 → 다시 활성화하면 1~2초 내로 refresh됨

&nbsp;

① netsh wlan show networks

- NIC 이름 ("Interface name:" 뒤에 보이는 값) 확인

② netsh interface set interface name="**<①에서 확인한 NIC 이름>**" admin=disabled

③ netsh interface set interface name="**<①에서 확인한 NIC 이름>**" admin=enabled

④ netsh wlan show networks mode=bssid

&nbsp;

이 방법의 단점은 잠시 연결을 끊어야 한다는 것인데 다음과 같은 이유로 크게 문제가 될 것 같지는 않음

- 자동연결설정을 해 두었다면 1~2초 내에 다시 연결될 것임
- 이미 믿을만한 WiFi에 연결되었다면 굳이 다른 WiFi를 검사할 필요는 없으므로 주변의 WiFi를 검사해야 할 때는 연결하지 않은 상태로 검사하는 상황이라고 가정해도 됨


&nbsp;


그 외에 유용한 명령어:

&nbsp;

netsh wlan show all

- 현재 연결된 WiFi 및 기존에 저장된 profile에 대한 정보 보여줌


&nbsp;


netsh 명령은 마지막 파라미터 자리에 ?를 넣으면 그 자리에서 사용할 수 있는 모든 옵션을 볼 수 있음

예) netsh wlan ? 하면 "netsh wlan" 뒤에 올 수 있는 모든 옵션이 리스팅 되며

netsh wlan show ? 하면 "netsh wlan show" 뒤에 올 수 있는 모든 옵션이 리스팅 됨

