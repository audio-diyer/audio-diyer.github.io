---
title:  "Symphonic MPD [1] 소개"
excerpt: "Symphony MPD 개발자가 일본인(영어로 커뮤니케이션 가능함)이고 웹사이트(포럼)가 일본어로 되어 있어서 접근성이 좋지 않습니다. 그런데다가 회원제라서 소프트웨어를 다운받으려면 포럼 관리자의 승인이 필요합니다."

categories:
  - RaspberryPi
tags:
  - [라즈베리파이, MPD]

toc: true
toc_sticky: true
 
date: 2021-10-27
last_modified_at: 2021-10-27
---
# 시작하면서...
Symphony MPD 개발자가 일본인(영어로 커뮤니케이션 가능함)이고 웹사이트(포럼)가 일본어로 되어 있어서 접근성이 좋지 않습니다. 그런데다가 회원제라서 소프트웨어를 다운받으려면 포럼 관리자의 승인이 필요합니다. 포럼 가입도 메일만 보낸다고 승인이 떨어지는 것 같지도 않고...어쨋든 전 승인이 되었습니다.^^

![smpd forum](/assets/images/smpd_forum.png)

**소스코드의 비공개에 따라서 외부에 공개하지 않는 콘텐츠 (예를 들면 이미지 다운로드) 이외에는 비회원이라도 열람이 가능합니다. 물론 전부 일본어입니다. 크롬 브라우저로 한국어로 번역해서 보시면 됩니다.**

[Symphonic MPD Forum 링크](https://www.symphonic-mpd.com/forum/)

어쨋든 지난 주에 포럼에 가입 후에 포럼에 있는 여러가지 프로젝트에 대해서 알게 되었으며 기존 Volumio, MoOde Audio 등의 소프트웨어와는 지향점이 다르다는 것을 알게 되었습니다. 이런 정보를 꽁(무료)으로 얻어도 되나 싶을 정도로 수많은 테스트와 수정 작업들에 대한 기록이 있습니다. 대부분 리눅스 OS, 네트웍, I2S 등에 대한 내용이지만 개인적으로는 이런 시도에 박수를 보냅니다.

Symphonic MPD는 절대 초보자용은 아닙니다. 설치 후에 음악 재생 방법 등의 운영이 어려운 것이 아니라 설치 과정에서 문제가 발생하는 경우에는 일반 초보자는 해결이 어렵겠다는 생각을 했습니다. 라즈베리파이의 보드 별 호환성 등도 있고 해서...

diyadio.com 에도 symphonic mpd 에대한 쓰레드가 있습니다.

[diyaudio 쓰레드](https://www.diyaudio.com/forums/vendor-s-bazaar/355137-symphonic-mpd.html)

# Symphonic MPD 포럼 번역

> ## 똑똑한 싱글 보드 컴퓨터 교향곡을 연주하십시오!

**symphonic-mpd의 특성**

* 실시간 커널(Xenomai 3.0.7)

* I₂S 출력에 특화된 Xenomai 전용 드라이버 및 재생 소프트웨어 개발

* 고충실도 재생을 위한 커널, MPD, AirPlay, Spotify Connect, ALSA-lib 및 기타 라이브러리에 대한 사용자 지정 패치

* 빠르고 컴팩트한 시스템에 최적화된 빌드

* 실시간 우선 순위 및 CPU 실행 최적화

* mpd, AirPlay, 독점 Spotify Connect(자동화 불필요한 프로세스 중지 및 NAS 마운트 해제)

* HDMI, Wi-Fi, 블루투스 서비스, USB 버스파워 정지, CPU/GPU 언더클럭킹, LED 소등을 통한 노이즈 감소 및 전압 안정화

* 향상된 PLL 정확도는 슬레이브 모드에서 실행할 때 I2S HAT의 음질을 향상시킵니다. 마스터 모드에서 실행되는 I2S HAT를 사용하는 경우 dt-blob.bin을 대체하여 PLL 설정이 취소됩니다. 이것은 CPU 부하를 줄입니다.

* 커널 스레드 인터럽트를 억제하고 커널 매개변수를 조정하여 운영 체제 지터 감소

* 재생 샘플링 속도와 일치하도록 ALSA 버퍼 튜닝

* 처리량 최적화를 위한 NAS 마운트 설정 자동 조정(처리량 측정에 약 30초 소요)

* 웹 UI로서의 초경량, 저부하 웹 서버 YMPD

* TCP 포트 6600의 일반적인 사용이 아닌 MPD와 YMPD 간의 UNIX 도메인 소켓 통신

* 온라인 버전 업데이트

Raspberry PI 2B 및 Raspberry PI 3B+에서 Xenomai를 활용하려면 매개변수를 조정해야 합니다.  

---

유투브에 올라와 있는 Volumio, MoOde 와 Jitter test  비교 측정 동영상입니다.

<iframe width="560" height="315" src="https://www.youtube.com/embed/sEkcPvplElY" frameborder="0" allowfullscreen></iframe>

---

# 스크린 캡쳐

설치 후 캡쳐한 스크린샷 몇장 올립니다. 초경량 웹인터페이스인 ympd 사용했네요...

## 음악 재생 화면

![smpd screen capture 1](/assets/images/smpd_screen_01.png)

## 재생 대기열 관리
![smpd screen capture 2](/assets/images/smpd_screen_02.png)

## NAS 연결
![smpd screen capture 3](/assets/images/smpd_screen_03.png)

## 설정 메뉴
![smpd screen capture 4](/assets/images/smpd_screen_04.png)

## 대시보드
![smpd screen capture 5](/assets/images/smpd_screen_05.png)
