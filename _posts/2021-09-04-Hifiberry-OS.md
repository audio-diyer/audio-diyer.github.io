---
title:  "Hifiberry OS 설치 기록 및 간단 리뷰"
excerpt: "Hifiberry OS 는 이름에서 알 수 있듯이 Hifiberry 사에서 제공하는 음악 재생용 소프트웨어입니다. Volumio, moOde 와 유사한 소프트웨어인데 Hifiberry 사의 DAC 제품들만 지원합니다.​"

categories:
  - 라즈베리파이
tags:
  - [라즈베리파이, Hifiberry-OS, 터치스크린]

toc: true
toc_sticky: true
 
date: 2021-09-04
last_modified_at: 2021-09-04
---
![Hifiberry OS 01](/assets/images/hifiberry-os-01.png)

Hifiberry OS 는 이름에서 알 수 있듯이 Hifiberry 사에서 제공하는 음악 재생용 소프트웨어입니다. Volumio, moOde 와 유사한 소프트웨어인데 Hifiberry 사의 DAC 제품들만 지원합니다.​

음악 재생 뿐만 아니라 Hifiberry 사의 DAC 중에는 DSP Add-on 보드를 지원하는 것들이 있는데 이를 제대로 사용하기 위해서는 Hifiberry OS를 사용해야 합니다. 측정 마이크로 측정해서 인터넷으로 업로드하면 적절한 필터를 계산해서 다운로드 할 수 있게 되어 있는 것 같습니다. 전 추후에 공간 보정 (Room Compensation) 기능만 활용해 보면 좋을 것 같다는 생각이 듭니다. 

![Hifiberry OS 02](/assets/images/hifiberry-os-02.png)

![Hifiberry OS 03](/assets/images/hifiberry-os-03.png)

DSP 보드도 없고 측정 마이크도 없기 때문에 보유하고 있는 Hifiberry 짝퉁 제품에 한번 설치해서 일반적인 음악 재생 기능만 사용을 해봤습니다. 아래 사진 위에 제품은 Hifiberry DAC+ 와 호환되는 짝퉁 PCM5122 탑재된 DAC 입니다. 아래 제품은 SPIDF와 광출력이 되는 짝퉁 HAT 보드인데 외장 DAC 를 사용하기 위해서 꺼냈습니다. Hifiberry 사에는 USB DAC 가 없기 때문에 Hifiberry OS 에서는 USB DAC 를 사용이 불가능합니다. SPDIF 나 광연결은 가능합니다. 

![Hifiberry OS 04](/assets/images/hifiberry-os-04.jpg)

아래 링크에 Hifiberry OS 에 대한 설명이 잘 되어 있습니다.

​[Hifiberry OS 소개](https://www.hifiberry.com/hifiberryos)

설치는 위 링크에 있는 라즈베리파이 이미지 (Zero/2/3/4 따로 있음) 를 다운 받은 후에 Etcher 로 이미지를 구운 후에 부팅을 하면 되는데 초기 부팅시 DAC 인식이나 기타 작업이 내부에서 이루어지는지 시간이 좀 걸립니다. 2~3 분 정도 기다렸다가

​http://hifiberry.local 

에 접속 후 설정 작업을 진행하면 됩니다.

첫 화면이 화려합니다.^^ 역시 UI가 Bang & Olufsen Beocreate 프로젝트 기반이라고 하더니 전문 디자이너의 솜씨로 보이네요. 

![Hifiberry OS 05](/assets/images/hifiberry-os-05.png)

이름은 바꿀 필요가 없어서 그대로....

![Hifiberry OS 06](/assets/images/hifiberry-os-06.png)

그냥 다음으로....

![Hifiberry OS 07](/assets/images/hifiberry-os-07.png)

설정 끝입니다.^^ 볼루미오 보다도 훨씬 간단합니다. 사운드 장치를 자사의 DAC만 지원해서 자동으로 인식하기 때문에 간단하게 끝납니다. 

![Hifiberry OS 08](/assets/images/hifiberry-os-08.png)

약간 화면 아래로 스크롤 다운해 보니 중국산 짝퉁 (PCM5122) 을 Hifiberry DAC+ 로 인식했습니다.^^

![Hifiberry OS 09](/assets/images/hifiberry-os-09.png)

UI는 확실히 Volumio 나 moOde 보다 훌륭합니다. 오픈소스이기는 하지만 벤더의 냄새가 좀 납니다.​

SOURCE 에 들어가서 제 환경 (Logitech Media Server)에 맞게 설정을 했습니다. Roon, Airplay, Spotify, Bluetooth 등 모두 비활성하고 Squeezelite 만 활성화했습니다. 이렇게만 해도 Logitech Media Server 에 모든 설정이 다 되어 있기 때문에 국내 라디오, 서버 음원, Qobuz, Tidal, Airplay 모두 Squeezelite 를 통해서 재생할 수 있습니다.

![Hifiberry OS 10](/assets/images/hifiberry-os-10.png)

Squeezelite 테스트 후에 DLNA 를 올랴서 mconnect 로도 재생을 해봤습니다. 아래 화면 웹브라우저에서 재생중인 화면입니다. 확실히 UI 디자인이 심플하면서도 깔끔합니다.

![Hifiberry OS 11](/assets/images/hifiberry-os-11.png)

문제는 앨범아트가 엉뚱한 것을 가져오는 경우가 많습니다. 

![Hifiberry OS 12](/assets/images/hifiberry-os-12.png)

완전히 생뚱 맞은 앨범 이미지를 가져와서 당황했습니다.

![Hifiberry OS 13](/assets/images/hifiberry-os-13.png)

앨범 커버가 아래와 같이 기본이 If Higher Resolution 인데 If Source Has No Cover 로 변경하면 좀 개선이 됩니다. 서버에 앨범이미지가 있다면 괜찮은데 서버에 이미지가 없다면 또 엉뚱한 것을 가져오는 문제는 해결이 안됩니다. 특히 스트리밍 음원 재생할 때 앨범 이미지 매칭을 잘 못하는 문제가 있습니다. 메터 정보 검색 및 앨범 이미지쪽은 개선이 필요해 보입니다.

![Hifiberry OS 14](/assets/images/hifiberry-os-14.png)

Hifiberry 설정 메뉴를 보니 HDMI 터치스크린을 사용할 수 있는 것 같아서 연결해 보니 화면이 나옵니다. 터치도 잘되는데 아마도 제가 가지고 있는 7인치 터치스크린이 지원되는 모양입니다.

**웹화면**

![Hifiberry OS 15](/assets/images/hifiberry-os-15.png)

**7인치 터치 스크린...**

아마 HDMI 대형 TV를 연결해도 화면이 잘 나올 것 같습니다. 역시 터치스크린의 Now Play 화면은 Volumio, moOde, Ropiee, piCorePlayer 를 비교해서 가장 미려한 화면을 보여 주네요.

![Hifiberry OS 16](/assets/images/hifiberry-os-16.jpg)

![Hifiberry OS 17](/assets/images/hifiberry-os-17.jpg)

역시 한글은 제대로 표시가 안됩니다.ㅠㅠ 외국 개발자들에게 너무 많은 것을 바라면 안됩니다. 날잡아서 삽질(?)을 할까 고민 중입니다. 

![Hifiberry OS 18](/assets/images/hifiberry-os-18.jpg)

간단히 평가를 하면 

**장점**

* 설정이 쉬워서 초보자에게 좋음
* 미려한 인터페이스 (웹화면, 터치스크린 화면)
* Hifiberry 사 DSP 지원

**단점**

* 한글 깨짐
* 다소 무거움 (볼루미오보다는 가볍고 moOde 보다는 무거움)
* 설정이 쉽지만 세밀한 설정 (튜닝)을 할 수 없음..초보자에게는 장점이지만 중고급 사용자에게는 단점

ssh 로 로그인해서 보니 Java 로 만들어져 있네요. 비교적 자주 업그래이드가 되는 것 같아서 유지 보수 측면에서는 나쁘지 않은 것 같습니다.

Khadas Tone2 Pro DAC 도 SPDIF 로 연결하니 Hifiberry OS 에서 잘 작동합니다.^^

![Hifiberry OS 19](/assets/images/hifiberry-os-19.jpg)

터치스크린을 EL3n 위에 올렸습니다.^^

![Hifiberry OS 20](/assets/images/hifiberry-os-20.jpg)