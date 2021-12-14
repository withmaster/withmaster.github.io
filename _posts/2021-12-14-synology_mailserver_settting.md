---
title:  "Synology DSM 7.0에서 메일 서비스 이용하기"
excerpt: "Synology DSM 7.0에서 mailplus server를 설정해서 나만의 도메인을 메일에도 사용해보기"

toc: true
toc_sticky: true
toc_label: "주요 목차"

categories:
  - 장치
tags:
  - NAS
  - tips
---


## Why?

- 일을 하다보면 회사 업무 외의 일을 할 때가 있고, personal branding 차원에서 개별 도메인에 연결된 메일이 있으면 좋겠다는 생각을 종종하게 된다.
- 개인적인 추천은 [google workspace](https://workspace.google.com/intl/ko/products/gmail/?utm_source=google&utm_medium=cpc&utm_campaign=1010746-Workspace-APAC-KR-ko-BKWS-EXA-Golden&utm_content=text-ad-none-none-DEV_c-CRE_470902874128-ADGP_Hybrid%20%7C%20BKWS%20-%20EXA%20%7C%20Txt%20~%20G%20Suite-KWID_43700058413758937-kwd-836977539265&userloc_1009871-network_g=&utm_term=KW_%EA%B5%AC%EA%B8%80%20suite&gclid=CjwKCAiA-9uNBhBTEiwAN3IlNHmXLs3y_4Z2aeh1x1AWLR-mT-asDud3S6o53sfbsYJzJ0NdCeWM7RoCBX4QAvD_BwE&gclsrc=aw.ds)의 맞춤 e-mail 서비스를 이용하는게 설정이 굉장히 편하기 때문에 아주 좋은 선택이다.  다만, NAS를 사용하고 있으니 mail server를 설정해서 사용해보고자 한다.
- 굉장히 어려울 것으로 예상했었지만, 메일 송신 수신 기능이 되게만 하는건 생각보다 쉽다.

## 주요 참고 자료

- [Synology 지식 센터](https://kb.synology.com/ko-kr/search?os_versions%5B%5D=2&services%5B%5D=Synology_MailPlus&date_range=y&page=2)
    1. 시스템 : DSM 7.0
    2. 패키지 : Synology MailPlus
    3. 날짜 범위 : 작년
    - e-mail 작동 방식을 이해하고 싶다면 [여기](https://kb.synology.com/ko-kr/DSM/tutorial/How_to_set_up_MailPlus_Server_on_your_Synology_NAS)를 참조하자.
- 블로그 `Gumu's treasure box`
    - 설정만을 원한다면 이걸 보면 됩니다.
    
    - [시놀로지 NAS, 메일서버 구현하기 1탄(Mail plus 설치, 설정) - Gumu's treasure box](https://gumu.kr/blog/165/mailplus1/)
    
- 유투브 - `[50대 컴쟁이] baseyou 21`
    - 자세히 알고 싶다면 여기를 참고하시면 좋습니다.
    
    - [시놀로지NAS 메일서버 셋팅하기#1(이렇게하면 끝)-개요 및 구성](https://www.youtube.com/watch?list=PLHblzO-P7e_y0M2Qy11d_VWD32PuRRbX2&v=WlgK3OkZPKI&feature=emb_title)
    

## What?

1. 도메인 네임(domain name)
    - [카페24](https://www.cafe24.com/login/)
    - 개별적으로 구매한 도메인 네임(domain name)은 필수입니다.
    - 개인적으로는 `.com` 을 추천하지만, `.co.kr` 이나 `.kr`도 괜찮다고 봅니다.
    - 설명을 위해서 가상의 도메인 네임 `example.com` 을 사용할 예정입니다.
2. NAS 서버
    - 가지고 있는 synology를 이용하겠지만, qnap도 가능합니다.
3. ip 주소
    - 고정 ip가 있으면 좋지만, 돈도 들고 하니 유동 ip를 사용하겠습니다.
    - ip주소는 ip공유기 설정에서 확인할 수 있구요.
    설명을 위해서 가상의 ip인 `123.123.123.123`을 사용할 겁니다.
        
        ![Untitled](https://withmaster.github.io/assets/images/2021-12-14-synology_mailserver_settting/Untitled.png)
        
## How?
### DNS 설정([cafe24](https://www.cafe24.com/login/))

- 왼쪽 창 `DNS 관리` - `example.com` 선택 - 선택한 도메인 `DNS 관리` 선택

    ![Untitled](https://withmaster.github.io/assets/images/2021-12-14-synology_mailserver_settting/Untitled%201.png)

- 네임서버(DNS) 관리
    1. A 레코드 관리
        1. 첫번째
            - 도메인 `example.com`
            - IP `123.123.123.123`
        2. 두번째
            - 도메인 `www.example.com`
            - IP `123.123.123.123`
    2. MX 레코드 관리
        - 도메인 `example.com`
        - 메일서버IP `123.123.123.123`
        - 우선순위 `10`
    3. SPF 레코드 관리
        - 호스트명: `example.com`
        - SPF: `v=spf1 ip4:123.123.123.123 ~all`
        - 자세한 설정은 KISA의 [SPF 작성 도우미](https://spam.kisa.or.kr/white/sub3.do)를 참조했습니다.
    4. TXT 레코드 관리
        - DKIM 설정
            - 호스트명: `DKIM선택기 접두어_domain.example.com`
            - TXT: `v=DKIM1; k=rsa; p=생성된 공용키`
            - [참고 자료](https://kb.synology.com/ko-kr/DSM/help/MailPlus-Server/mailplus_server_multiple_domains?version=7)
            - Synology mailplus server 설정
                - Synology mailplus server - 도메인 - 편집 - 일반 - 고급 이동
                    1. 아웃바운드 e-mail에서 DKIM 서명 활성화 - 체크
                    2. `DKIM 선택기 접두어`: `example` 
                        - 마음에 드는 문자열을 입력하면 됩니다.
                - 공용 키 생성 - 선택
                - DKIM 키 길이
                    - 길 수록 좋습니다.
                    - DNS 관리 메뉴에서 입력 길이를 제한하는 경우가 있으며, cafe24의 경우에는 2048을 선택하고 생성하면 길이를 초과하므로 1024를 선택하면 됩니다. 물론 2048을 이용해서 생성한 키를 넣는 방법도 있습니다.
                    - `생성된 공용 키`
                        
                        ![Untitled](https://withmaster.github.io/assets/images/2021-12-14-synology_mailserver_settting/Untitled%202.png)
                        
        - dmarc 설정
            - 호스트명 : `_dmarc.example.com`
            - `v=DMARC1; p=quarantine; pct=20; rua=mailto:my_mail@gmail.com`
            - my_mail@gmail.com은 자기가 사용하는 메일을 입력하면 됩니다.    
            ![Untitled](https://withmaster.github.io/assets/images/2021-12-14-synology_mailserver_settting/Untitled%203.png)
    

### 공유기 포트 포워딩 설정([iptime](http://192.168.0.1/))

- [Synology Knowledge center 참조](https://kb.synology.com/ko-kr/DSM/help/MailPlus-Server/mailplus_server_creation?version=7)
    
    ![Untitled](https://withmaster.github.io/assets/images/2021-12-14-synology_mailserver_settting/Untitled%204.png)
    
- 고급 설정 - NAT/라우터 관리 - 포트포워드 설정
    - 규칙이름 : 알아서 설정하면 됩니다.
    - 내부 IP 주소 : NAS에 할당된 IP
    - 외부포트, 내부포트는 25, 110, 143... 등등을 설정했습니다.
    
        ![Untitled](https://withmaster.github.io/assets/images/2021-12-14-synology_mailserver_settting/Untitled%205.png)
    

### 서버 설정(Synology)

1. 프로그램 설치
    - synology maiplus server와 synology mailplus를 설치합니다.
    - mailplus server가 mail server의 고급 버전입니다. [차이점 비교](https://kb.synology.com/ko-kr/DSM/tutorial/Differences_between_MailPlus_and_Mail_Server)는 여기를 참고하세요.
    
        ![Untitled](https://withmaster.github.io/assets/images/2021-12-14-synology_mailserver_settting/Untitled%206.png)
    
2. synology maiplus server 설정
    - 서버관리
    - 위협 모니터
    - 도메인
        
        ![Untitled](https://withmaster.github.io/assets/images/2021-12-14-synology_mailserver_settting/Untitled%207.png)
        
    - 메일배달
        
        ![Untitled](https://withmaster.github.io/assets/images/2021-12-14-synology_mailserver_settting/Untitled%208.png)
        
    - 서비스
        - 프로토콜
            
            ![Untitled](https://withmaster.github.io/assets/images/2021-12-14-synology_mailserver_settting/Untitled%209.png)
            
        - MailPlust 클라이언트
            
            ![Untitled](https://withmaster.github.io/assets/images/2021-12-14-synology_mailserver_settting/Untitled%2010.png)
            
    - 보안
        - 스팸 방지
            
            ![Untitled](https://withmaster.github.io/assets/images/2021-12-14-synology_mailserver_settting/Untitled%2011.png)
            
        - 인증
            
            ![Untitled](https://withmaster.github.io/assets/images/2021-12-14-synology_mailserver_settting/Untitled%2012.png)
            
        - 내용 검색
        - 데이터 보호
    - 대기열 및 감사
    - 라이센스 및 계정
        - [참고 자료](https://kb.synology.com/ko-kr/DSM/help/MailPlus-Server/mailplus_server_license?version=7)
        
        ![Untitled](https://withmaster.github.io/assets/images/2021-12-14-synology_mailserver_settting/Untitled%2013.png)
        
    - 개인용
        - [참고 자료](https://kb.synology.com/ko-kr/DSM/help/MailPlus-Server/mailplus_server_personal?version=7)

## 마무리

- 위와 같이 설정하고, 메일을 보내니 잘 가고 잘 옵니다.
- 인증서와 관련된 부분은 [여기](https://gumu.kr/blog/218/mailplus3/)를 참고하세요.
- 다만, 내가 보낸 메일은 스팸함으로 들어가니, 이와 관련되어 처리가 필요합니다.
    - Reverse DNS 등록
        
        [Reverse DNS 등록 방법](https://hope.pe.kr/119)
        
        [](https://dms.kornet.net/login)
        
    - White Domain 등록
        
        [White Domain 소개 < White Domain / SPF : 불법스팸대응센터](https://spam.kisa.or.kr/white/sub1.do)
        
- DSM 6.x에서 DSM 7.0으로 넘어오면서 mailplus server의 인터페이스가 조금 바뀌는 헤매기는 했지만, 다행히 마무리 했네요.