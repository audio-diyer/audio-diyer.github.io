---
title:  "Symphonic MPD [6] 라즈베리파이 4B에 설치 및 사용기"
excerpt: "라즈베리파이 4B용으로 포럼에 올라와 있는 버전은 v1.0.7 버전인데 라즈베리파이 4B Rev1.1 또는 Rev1.2 버전 전용입니다. 문제는 새로 구매하는 라즈베리파이의 경우 Rev1.4 일 가능성이 매우 높습니다."

categories:
  - SMPD
tags:
  - [라즈베리파이, MPD]

toc: true
toc_sticky: true
 
date: 2021-11-07
last_modified_at: 2021-11-07
---
라즈베리파이 3B+ 에 이어서 4B에도 설치를 했습니다.​

라즈베리파이 4B용으로 포럼에 올라와 있는 버전은 v1.0.7 버전인데 라즈베리파이 4B Rev1.1 또는 Rev1.2 버전 전용입니다. 문제는 새로 구매하는 라즈베리파이의 경우 Rev1.4 일 가능성이 매우 높습니다. 아마도 중고로 구매하는 것이 아니라면 Rev1.4 일 가능성이 높고 구매시 Rev 를 사전에 확인 할 수 있는 방법이 없습니다.

라즈베리파이 Rev1.1, Rev 1.2 라고 해도 개발자가 권장하는 펌웨어 버전을 맞춰주면 좋다고 하니 라즈4 펌웨어부터 권장 버전으로 설치하고 SMPD를 부팅해 주면 좋습니다. 

라즈베리파이4가 Rev1.4 일 경우 SMPD 가 부팅이 안됩니다. 이것 때문에 정말 많은 삽질을 했습니다. 다음 과정대로 진행하면 부팅을 할 수 있습니다.

# 1. 펌웨어 업그래이드
여러가지 방법이 있지만 가장 단순한 방법은 Recovery Image 를 이용한 방법입니다. SD 메모리를 Fat32 으로 포맷을 한 후에 아래 링크의 파일을 다운 받아서 압축을 푼 뒤에 SD 메모리에 복사합니다. 라즈베리파이에 랜선과 DAC를 모두 뽑은 상태에서 SD 메모리를 넣고 전원을 넣으면 펌웨어 업그래이드 작업이 진행됩니다. Activity LED (녹색)이 반복적으로 깜빡거리면 업그래이드 작업이 끝난 것입니다.

[라즈베리파이 복구 디스크](https://github.com/raspberrypi/rpi-eeprom/releases/download/v2021.04.29-138a1-disk-images/rpi-boot-eeprom-recovery-2021-04-29-vl805-000138a1-sd.zip)

# 2. 패치
포럼에서 SMPD v1.0.7 버전 이미지를 다운로드 받은 후에 Ether 로 SD 메모리에 이미지를 굽습니다. 이미지가 구워지면 아래 패치 파일을 압축을 풀에서 SD 메모리에 복사를 합니다. (일부 파일은 덮어쓰기를 하도록 합니다.)

[smpd-107-firmware_20201227.zip](/assets/downloads/smpd-107-firmware_20201227.zip)

이제 만들어진 SD 메모리로 라즈베리파이4 를 부팅하면 부팅이됩니다. 정상 부팅 여부를 확인하는 방법은 부팅이 성공하면 전원 LED (적색) 이 꺼집니다. 

# 3. 기본 설정 작업
부팅이 끝나면 http://smpd.local 로 접속해서 웹에서 기본 설정 작업을 진행하면 됩니다.

먼저 i2s 사운드 장치를 선택 후에 재부팅합니다. 앰프가 연결되어 있다면 사운드 장치가 올바로 설정되면 부팅 후에 시작음이 스피커를 통해서 출력됩니다.

![smpd v1.0.10 01](/assets/images/smpd-v100-01.png)

v1.0.7 을 v1.0.10 으로 업그래이드를 할 수 있습니다. Setting 에서 Update 를 클릭하면 인터넷을 통해서 업데이트를 수행합니다.   

![smpd v1.0.10 02](/assets/images/smpd-v100-02.png)

온라인 업데이트가 끝나면 REBOOT를 합니다.

![smpd v1.0.10 01](/assets/images/smpd-v100-03.png)

이제 소리가 나니 음원을 사용할 수 있도록 설정을 해야 하는데 아래와 같이 NAS 설정을 하면 됩니다. (라즈베리파이 4 Rev1.4 의경우 USB 기능이 아예 작동을 하지 않기 때문에 음원이 들어 있는 HDD 또는 SSD를 직접 연결해도 인식이 안됩니다.)  

![smpd v1.0.10 01](/assets/images/smpd-v100-04.png)

![smpd v1.0.10 01](/assets/images/smpd-v100-05.png)

음원이 들어 있는 NAS 를 설정해 준 뒤에 음원을 사용하려면 Library Update 를 해야 합니다. 음원을 수가 많을 수록 시간이 오래걸립니다.

![smpd v1.0.10 01](/assets/images/smpd-v100-06.png)

일단 음원 재생을 위한 설정은 이정도면 됩니다.

RADIO는 기본적으로 웹화면에서 아래와 같이 미리 주소들이 셋팅이 되어 있습니다. 국내 라디오는 없습니다.

![smpd v1.0.10 01](/assets/images/smpd-v100-07.png)

# 4. 추가 설정
개인적으로 NAS를 음원 저장소로 사용하는 것을 선호하지 않습니다. 이유는 Library 업데이트 작업이 필요하고 SD 메로리에 기록을 하기 때문에 재수 없으면 DB가 깨질 수도 있는데다가 속도도 그리 빠르지 않고 음원의 수가 많아질수록 MPD에 부담을 줄 수 있기 때문입니다.

그래서 미디어 서버를 선호합니다. 물론 별도의 미디어 서버를 구축해야 하는 부담이 있지만 미디어 서버가 있으면 음원 관리를 미디어 서버에서 하는데 다가 부가적으로 트랜스 코딩 등의 기능도 사용할 수 있어서 플레이어쪽에 추가적인 부담이 없어진다는 장점도 있습니다.

어쨋든 저는 미디어 서버로 Logitech Media Server (이하 LMS) 를 사용하고 있습니다.  Minim Server 와 같은 DLNA/UPNP 미디어 서버나 LMS를 사용하려면 UPNP Renderer 라는 것이 필요합니다.

SMPD 에 UPNP 기능을 추가하려면 다음과 같이 작업하면 됩니다.

1. Putty 로 smpd.local 에 접속

2. root/raspberry 로 로그인

3. upnp 설치
```javascript
# app install upnp
```
4. upnp 설정 파일 편집 (/etc/upmpdcli.conf)
```javascript
#mpdhost = 127.0.0.1 (default)
#mpdport = 6600 (default)
friendlyname = symphonic-mpd
checkcontentformat = 0
upnpav =1
openhome = 1
#lumincompat = 1
ohproductroom = symphonic-mpd
ohmetapersist = 1
#logfilename=/var/log/upmpdcli.log
#loglevel = 3
cachedir = /run/mpd/upmpdcli
radiolist = /usr/share/upmpdcli/radio_scripts/radiolist.conf
```

5. 서비스 설정
```javascript
# systemctl start upmpdcli
# systemctl enable upmpdcli
```
---

Radio Paradise 의 Flac 스트리밍 재생이 안됩니다. 이를 위해서 다음과 같이 작업합니다.
```javascript
# V=radioparadise-flac;cd /run/;wget -O - https://www.symphonic-mpd.com/release/files/$V.tar.gz|tar xzf -;cd $V;./install.sh;cd
```
KBS 클래식 FM, CBS 음악 FM 등은 아쉽게도 SMPD에서 청취가 불가능합니다. 대부분의 국내 라디오가 HLS (HTTP Live Stream) 이라는 방식을 사용하고 있는데 SMPD 는 공식적으로 HLS 를 지원하지 않고 앞으로도 지원할 계획이 없다고 합니다. SMPD 의 정책(?)은 UI 외에 핵심 기능에 손을 대지 않는다고 포럼에 써 있습니다. 아마도 Latency 가 늘어나는 부분에 대해서는 무조건 기각인 것 같습니다.

포럼에 나온 방법은 SMPD에서 HLS 로 스트리밍하는 라디오 방송을 청취하는 방법은 라즈베리파이 1대를 추가로 Arch AoE (Audio of Ether)라는 Front End 단을 구성하고 SMPD 를 Back End로 해서 2대를 묶어서 구성하는 방법이 있습니다. 어쨌든 SMPD쪽은 최대한 손을 대지 않고 추가적인 스트리밍 방식이 필요한 경우에는 별도로 라즈베리파이를 구성하고 네트웍 연결은 CPU를 사용하지 않는 AoE라고 부르는 특수한 오디오 전용 자체 설계한 프로토콜을 사용하는 방식입니다.

AoE는 나중에 기회가 되면 테스트해 보기로 하고 저는 좀더 쉬운 방식을 이용하기로 했습니다.

기존에 운영하고 있는 LMS 와 SMPD 에 설치한 UPNP 와 연동했습니다. 이렇게 하면 LMS에 설정해서 사용하고 있는 음원, 타이달, 라디오 방송을 그대로 이용할 수 있습니다.  

![smpd v1.0.10 01](/assets/images/smpd-v100-08.png){: width="50%" height="50%"}{: .align-center}

![smpd v1.0.10 01](/assets/images/smpd-v100-09.png){: width="50%" height="50%"}{: .align-center}

DLNA/UPNP 미디어 서버가 있다면 Linn Kazoo 앱을 콘트롤러로 사용해서 음원을 재생할 수 있습니다.

![smpd v1.0.10 01](/assets/images/smpd-v100-10.png){: width="50%" height="50%"}{: .align-center}

Linn Kzaoo 에서 국내 라디오는 재생이 불가능합니다만 HLS가 아닌 다른 방송은 청취가 가능합니다. (Radio Paradise, LINN... )

![smpd v1.0.10 01](/assets/images/smpd-v100-11.png){: width="50%" height="50%"}{: .align-center}

Mconnect 앱도 사용할 수 있습니다.

![smpd v1.0.10 01](/assets/images/smpd-v100-12.png){: width="50%" height="50%"}{: .align-center}

