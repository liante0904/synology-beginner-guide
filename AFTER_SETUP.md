
### **외부망에서 접근 가능한** 시놀로지 세팅하기 절차
1. 내부 고정 아이피 설정(DHCP)
2. DDNS 설정(외부 -> 라우터, **QuickConnect의 경우** 외부-> 시놀로지 설정)
  - [정품 사용자를 위한 Synology의 QuickConnect 설정](https://www.synology.com/ko-kr/knowledgebase/SRM/help/SRM/RouterApp/internet_quickconnect)
  - 라우터 제조사의 DDNS를 활용한 방법
    - [ASUS 공유기의 DDNS 설정 방법](https://www.noip.com/support/knowledgebase/setting-ddns-asus-router/)
    - [ipTIME 공유기의 DDNS 설정 방법](http://iptime.com/iptime/?page_id=67&pageid=1&mod=document&keyword=ddns&uid=7307)
    - 이외의 대부분의 제조사에서도 DDNS를 제공하고 있습니다. **공유기 관리자 페이지(콘솔)** 에서 확인 해보세요!
3. DDNS 설정 확인을 위해 지인 혹은 스마트폰의 WiFi 기능을 끄고 설정한 DDNS 주소를 접속했을 때, 공유기 설정 콘솔에 접근 할 수 있다면 성공입니다!
4. 만약 올바르게 포트 포워딩에 대해 이해하고 있다면 DDNS와 포트로 접속 했을 때.. 사용자가 포워딩한 프로그램으로 연결됩니다.
    - 서버 192.168.1.10, Webdav(5005)포트로 가정한다면
    - 내부에서 192.168.1.10:5005 로 포트로 접근했을 때 내부에서 webdav는 별다른 설정없이도 접근이 가능합니다.
    - 외부에서 webdav를 접근하기 위해서는 DDNS + 포트 포워딩 두가지의 설정이 되어 있어야합니다.
        - DDNS는 **외부망 -> 라우터** 까지의 접근을 위한 설정이며
        - 포트 포워딩은 **라우터 -> 서버** 로의 접근을 위한 설정입니다.
    - 만약 외부 포트(라우터) 4000을 -> (내부)192.168.1.10의 5005 포트로 포워딩 해두었다면
    - 사용자는 http://myNAS-DDNS.add.ress:4000 으로 접속을 시도 했을 때
    - 내가 포트 포워딩한 192.168.1.10의 5005 프로그램(webdav)로 포워딩 됨을 확인할 수 있습니다.
5. 이것을 이해하지 못했거나.. 생각한대로 동작하지 않는다면 **네트워킹과 보안지식** 로 다시 이동해서 숙지해주세요.
6. 내부 포트와 외부 포트를 서로 같아도 되지만 보안을 위해 외부와 내부 포트를 다르게 설정해주세요.
    - 보통 내부 포트는 프로토콜에서 제공하는 기본 포트를 고치지 않고
    - 외부 포트를 사용자가 정의하고.. 내부는 기본값(default)로 세팅하여 사용하는 것이  보편적인 패턴입니다.



### SSL(HTTPS)
- [클리앙 철이씨님의 무료 duckdns를 시놀로지에 등록해 봅시다](https://www.clien.net/service/board/cm_nas/9177427)

### Reverse Proxy(역방향 프록시)
- [클리앙 명량중년님의 시놀로지 역방향 프록시로 port 번호 없이 사용하기](https://www.clien.net/service/board/cm_nas/10938224)
