---
title:  "Symphonic MPD [5] 라즈베리파이3 용 v0.9.6 사용기"
excerpt: "혹시나 SMPD를 사용할 분들을 위한 미리 먼저 사용하면서 알아낸 정보를 공유합니다."

categories:
  - SMPD
tags:
  - [라즈베리파이, MPD]

toc: true
toc_sticky: true
 
date: 2021-11-05
last_modified_at: 2021-11-05
---
혹시나 SMPD를 사용할 분들을 위한 미리 먼저 사용하면서 알아낸 정보를 공유합니다.

SMPD는 라즈베리파이3B(3B+) 용과 4B용이 별도로 있습니다. 라즈베리파이3용은 v0.9.6 을 마지막으로 더 이상 업그래이드가 없고 계획도 없습니다. 개발자가 추가 개발 계획이 없다고 공식적으로 오래전에 발표를 했습니다.

라즈베리파이4가 출시된지 상당시간이 지났지만 아직 라즈베리파이 3 기기도 많이 사용하고 있어서 코드를 남겨둔 것 같습니다.

볼루미오나 기타 배포판과 달리 SMPD는 하드웨어 수준의 튜닝이 많이 적용되어 있습니다. 볼루미오의 경우 32bit 버전이면 라즈베리파이3,4 모두 사용할 수 있는데 SMPD는 부팅 자체가 안됩니다. 

라즈베리파이 4의 경우 초기 하드웨어 결함등으로 Rev1.0, 1.1, 1.2, 1.3, 1.4 등으로 업그래이드가 되었는데 SMPD의 경우 개발당시의 보드인 Rev1.1, Rev1.2 만 공식적으로 지원합니다. Rev1.4의 경우 부팅조차 안됩니다.

오늘은 라즈베리파이3 버전인 v0.9.6 버전만 다루겠습니다.

SMPD는 이름에서 알 수 있듯이 MPD를 기반으로 했습니다. 다른 일본인 개발자가 만든 LightMPD 도 MPD 기반이고 최대한 가볍게 만들어졌듯이 SMPD는 매우 가볍습니다. 부팅속도는 마이크로 코드를 이용한 piCorePlayer 보다도 더 빠른 것 같습니다. 10초가 안걸리는 것 같습니다. 정말 빠릅니다.

High Res 음원 재생중에 TOP를 실행해서 프로세서 부하등을 확인해 봤습니다. load average, task, %Cpu 를 보면 극도로 낮은 사용률을 볼 수 있습니다. 배포판 중에서 이렇게 낮은 것은 처음봤습니다. 아마도 낮은 Latency를 위해서 Kernel Level의 튜닝이 이루어진 것 같습니다.

![smpd v0.9.6 01](/assets/images/smpd-v096-01.png)

MPD를 사용해본 경험이 있다면 쉽게 사용할 수 있습니다.

콘트롤은 초경량 웹인터페이스인 ympd가 탑재되어 있습니다. 웹에 접속해서 사운드 장치 선택, NAS 마운트, 재생 콘트롤이나 셧다운 등을 할 수 있습니다. 화면은 깔끔한 편입니다. 몇가지 브라우저와 스마트폰에서 테스트해봤는 화면 잘나옵니다. 일본어 표시 검증이 되었기 때문에 당연히 한글도 문제없이 잘 표시됩니다.

![smpd v0.9.6 02](/assets/images/smpd-v096-02.png)

NAS (NFS, CIFS) 장치의 음원을 마운트할 때 네트웍 대역폭을 분석해서 최적의 옵션으로 마운트하도록 합니다. 

![smpd v0.9.6 03](/assets/images/smpd-v096-03.png)

대시보드로 튜닝여부를 확인할 수 있습니다. SMPD 포럼에 그래프의 의미를 물어 보니 긴 막대기들이 가로축(Latency) 500 ns 나노세크 이하에 몰려 있는 것이 좋다고 합니다.

![smpd v0.9.6 04](/assets/images/smpd-v096-04.png)

MPD, Airplay, Spotify 이렇게 3가지가 포함되어 있습니다.

MPD는 NAS 마운트 후에 DB업데이트하면 됩니다. 시간 좀 걸리구요. 포럼에 USB HDD를 연결해서 사용하는 분들이 간혹 있는데 저는 개인적으로 비추천입니다. 

1T 이상의 음원이면 SD 메모리 파티션을 확장해서 모두 사용하도록 해야 용량 부족이 생기지 않습니다. 1T 이하면 확장하지 않아도 됩니다.

MPD 클라언트로 ympd (웹) 이 아니라 Windows 에 Cantata 나 스마트폰 앱 (yaMPC) 을 사용하려면 SMPD의 설정을 변경해야 합니다. 기본적으로 MPD는 외부 연결이 막혀있기 때문입니다. putty 로 접속 (pi/raspberry) 후에 /etc/mpd.conf 파일을 열어서 port..., bind_to_.... 앞의 # 을 제거 후 저장 후 mpd 서버스를 재시작 하거나 SMPD를 재부팅하면 됩니다.

![smpd v0.9.6 05](/assets/images/smpd-v096-05.png)

웹인터페이스 대신 아이폰 yaMPC 앱을 사용할 수 있습니다.

![smpd v0.9.6 06](/assets/images/smpd-v096-06.png){: width="50%" height="50%"}{: .align-center}

전 아이폰으로 AirPlay 로 애플 뮤직을 재생해 봤는데 마음에 들었습니다. 아이폰을 소스로 많이 사용하지 않았는데 애플 뮤직이 무손실으로 업그래이드가 되어서 앞으로 많이 사용해야할 듯합니다.  유투브 음악도 Airplay로 앰프로 바로 재생하는 것이 편리합니다.  

![smpd v0.9.6 07](/assets/images/smpd-v096-07.png){: width="50%" height="50%"}{: .align-center}

Spotify 는 가입이 안되어 있어서 테스트를 못했지만 별도의 설정 메뉴가 있는것으로 봐서 잘 작동하리라 생각합니다.

가장 아쉬운 부분은 DLNA/UPNP를 지원하지 않는 부분입니다. 아무래도 초기 개발시 Latency 를 최소화에 중점을 두다 보니 최소한의 기능 (주로 일본내 사용자의 주로 사용하는 환경)에 중점을 두지 않았었나 생각해 봅니다.

DLNA/UPNP 미디어 서버나 LMS 와 연계하려면 UPNP 렌더러가 필요합니다. 더구나 우리나라의 기형적인(?) 인터넷 라디오를 지원하려면 이 상태에서는 청취가 불가능합니다.

SMPD 포럼에도 UPNP 지원을 위한 upmpdcli 설치에 대한 글들이 몇 개 올라와 있는데 꽤 오래된 글입니다. upmpdcli 설치를 시도해 봤는데 실패했습니다.

문제는 SMPD v0.9.6 이 워낙 오래된 데비안 배포판을 기준으로 만들어져 있습니다. (Debian Jessie) 그리고 upmpdcli 사이트 관리자가 무슨일이 있는지 사이트 인증서가 2020년 말에 만료가 되었는데 갱신을 하고 있지 않아서 upmpdcli 바이너리 패키지를 설치할 수가 없습니다.ㅠㅠ

upmpdcli 소스를 컴파일하면 되는데 SMPD가 너무 오래된 배포판이라서 쉽지가 않아서 그냥 SMPD가 아닌 집에서 상시 켜놓는 다른 리눅스 머신(NAS)에 설치했습니다. 

이제 Linn Kazoo 를 이용해서 Minim Server 의 음원을 재생할 수 있습니다. 국내 라디오도 셋팅을 했는데 KBS Classic FM은 재생이 안되고 CBS 음악 FM 은 재생이 됩니다. 아마도 SMPD의 MPD 때문이거나 뭔가 패키지가 빠져서 그런 것 같은데 원인을 찾아봐야 할 것 같습니다.

![smpd v0.9.6 08](/assets/images/smpd-v096-08.png){: width="50%" height="50%"}{: .align-center}

 Mconnect 에서 Qobuz, Tidal 을 사용할 수 있습니다. 플라시보인지 음질도 더 좋은 것 같습니다.^^ 

![smpd v0.9.6 09](/assets/images/smpd-v096-09.png){: width="50%" height="50%"}{: .align-center}

저가형 i2s 슬레이브 방식의 DAC에서 이 정도면 본전을 뽑고도 남을 정도의 음질인 것 같습니다....