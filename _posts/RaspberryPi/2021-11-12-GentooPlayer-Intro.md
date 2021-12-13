---
title:  "GentooPlayer 소개 및 사용기"
excerpt: "리눅스 기반의 여러가지 오디오용 소프트웨어들이 있습니다. Volumio, MoOde 가 아마도 가장 대중적(?)이지 않을까 생각합니다. 사용자층이 많은 것 같지는 않지만 암암리에 이름이 알려진 소프트웨어들이 있는데 그 중 하나가 GentooPlayer 입니다."

categories:
  - GentooPlayer
tags:
  - [라즈베리파이, GentooPlayer]

toc: true
toc_sticky: true
 
date: 2021-11-12
last_modified_at: 2021-11-12
---
리눅스 기반의 여러가지 오디오용 소프트웨어들이 있습니다. Volumio, MoOde 가 아마도 가장 대중적(?)이지 않을까 생각합니다. 사용자층이 많은 것 같지는 않지만 암암리에 이름이 알려진 소프트웨어들이 있는데 그 중 하나가 GentooPlayer 입니다. (아래 홈페이지) 

[GentooPlayer 홈페이지](https://gentooplayers.com/)

리눅스는 배포판 종류가 상당히 많습니다. 아델 리눅스, 젠투 리눅스 같이 남극의 펭권종에서 이름을 따오는 경우가 있습니다. ​

보통 데비안 계열을 많이 사용하는데 젠투 리눅스는 애초에 나올때 부터 엽기적인 패키지 관리 시스템을 탑재하고 있어서 아예 사용을 하지 않았습니다. 보통의 리눅스들은 소프트웨어를 바이너리 패키지로 묶어서 설치를 하는 반면에서 젠투 리눅스는 설치하는 시스템의 아키텍쳐에 맞게 소스를 다운 받아서 컴파일을 하기 때문에 설치시간이 무척 오래 걸렸었습니다. 

본인의 시스템에 맞게 설치를 하려면 하루 종일,,,아니 몇일이 걸리기도 했지만 지금은 하드웨어가 워낙 좋기 때문에 컴파일 자체가 워낙 빨리 수행되기 때문에 이러한 제약은 거의 없어졌습니다. 

젠투 플레이어는 무료가 아닙니다. 기부라고 표현했지만 비용을 지불해야 사용할 수 있습니다.

![GentooPlayer 01](/assets/images/GentooPlayer-01.png)

저는 메일을 보내서 Trial key 를 받아서 라즈베리파이 4에 설치를 해 봤습니다. 개발자가 이탈리아 로마에 거주합니다. 한국과 시차가 있어서 메일을 보낸 후 하루 정도 기다려야 회신을 받을 수 있을 겁니다.
​
웹사이트에 설치 및 사용에 관련된 많은 정보들이 잘 정리되어 있습니다. 이미지를 구워서 부팅 후에 웹으로 접속해 보면  아래 화면과 같이 좌측에 다양한 메뉴가 있습니다. 

등록 키를 넣지 않으면 설정 변경이 불가능하기 때문에 사용이 거의 불가능합니다. DAC는 외장형 USB DAC으로 선택했습니다.

![GentooPlayer 02](/assets/images/GentooPlayer-02.png)

젠투 플레이어의 특징을 볼 수 있는 화면입니다. Squeezelite, MPD, Airplay 등 본인 환경에 맞게 필요한 소프트웨어를 활성/비활성 할 수 있습니다.

![GentooPlayer 03](/assets/images/GentooPlayer-03.png)

각각의 소프트웨어 별로 세부 설정을 할 수 있도록 웹화면이 구성되어 있어서 설정을 비교적 쉽게 할 수 있습니다. 그렇지만 파라메터를 어느정도 알고 있어야 원활한 설정이 가능하겠죠...일단 Squeezelite 쪽을 먼저 설정해 줬습니다.

![GentooPlayer 04](/assets/images/GentooPlayer-04.png)

MPD의 경우 BitPerfect, Resample 등 각 환경에 맞는 구성을 할 수 있도록 구분되어 있습니다. 수작업으로 하면 설정 파일 편집하거나 모듈 의존성등 손이 많이 가는 작업인데 미리 레고 블럭 같이 구성이 되어 있습니다. 등록비는 아깝지 않은 것 같습니다.

![GentooPlayer 05](/assets/images/GentooPlayer-05.png)

라즈베리파이 Tweak 도 간단하게 할 수 있도록 별도의 메뉴를 제공하고 있습니다. 일단 라즈베리파이의 LED는 전부 꺼줬습니다.

![GentooPlayer 06](/assets/images/GentooPlayer-06.png)

CPU 격리 (isolation) 설정도 할 수 있습니다. 라즈베리파이를 오디오 기기로 사용하기 위한 시스템 최적화를 위한 세부 설정을 웹으로 할 수 있게 되어 있습니다.

![GentooPlayer 07](/assets/images/GentooPlayer-07.png)

프로그램을 모두 메모리에 올려서 실행할 수 있도록 변경하는 옵션도 있습니다.

![GentooPlayer 08](/assets/images/GentooPlayer-08.png)

얼마전에 몇 일동안 삽질하면서 설치하고 테스트 했던 CamillaDSP 도 설치할 수 있는 메뉴가 있습니다. 

![GentooPlayer 09](/assets/images/GentooPlayer-09.png)

CamillaDSP 설치를 진행했습니다. 역시 젠투 리눅스라서 소스를 다운 받아서 컴파일을 진행합니다. 제법 시간이 걸리지만 라즈베리파이 4라서 그런지 예상했던 것 보다는 시간이 오래 걸리지 않았지만 라즈3라면 꽤 오래 걸릴 것 같습니다.

![GentooPlayer 10](/assets/images/GentooPlayer-10.png)

Bubble UPnP Server 도 있습니다.^^ 종합 선물세트네요....

![GentooPlayer 11](/assets/images/GentooPlayer-11.png)

일단 Squeezelite, CamillaDSP 를 설치하고 CamillaDSP를 소노루-T에 맞게 저역 부스팅을 하도록 설정하고 CBS FM을 청음하고 있는데 가볍고 소리도 마음에 듭니다....

![GentooPlayer 12](/assets/images/GentooPlayer-12.png)

![GentooPlayer 13](/assets/images/GentooPlayer-13.png)

등록비가 들어간다는 것이 단점일 수 있지만 이정도 구성이면 등록비는 아주 저렴한 것 같습니다. 아마 별도로 구성을 한다면 훨씬더 많은 시간과 시행착오가 요구될 것 같습니다. 

다양한 오디오 소프트웨어를 라즈베리파이에서 사용하고 싶다면 이만한 솔루션이 있을까 싶습니다. 다만 어느 정도의 사전 지식이나 공부를 할 각오를 하고 덤벼야 할 것 같습니다.