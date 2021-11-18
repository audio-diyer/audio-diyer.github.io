---
title:  "Symphonic MPD [4] 앰프 변경 청음, SMPD 포럼 가입 방법"
excerpt: "SMPD 청음, 포럼 가입 방법"

categories:
  - 라즈베리파이
tags:
  - [라즈베리파이, MPD]

toc: true
toc_sticky: true
 
date: 2021-10-31
last_modified_at: 2021-10-31
---
일주일간 PRi3B+ (v0.9.6), RPi4B (v1.0.10) 두 대의 라즈베리파이에 셋팅을 해서 이전에 pCP로 계속 청음을 해 왔던 EL3nSE 에서 청음을 했습니다.

충분히 청음을 해서 앰프를 변경해서 청음을 해 봤습니다.

>LMS >>> 라즈베리파이4B (PCM5122 Hat, Slave 모드) >>> 프리앰프 >>> EL86Se >>> ProAc 태블릿 30주년

음원은 타이달입니다. smpd 에서 타이달 서비스를 바로 접속해서 청음이 불가능해서 LMS 에서 DLNA/UPNP Bridge 플러그인을 이용해서 LMS 에서 smpd 로 스트리밍을 하도록 했습니다.

녹음은 아이폰 7 플러스

<iframe width="560" height="315" src="https://www.youtube.com/embed/Fps27--7fsQ" frameborder="0" allowfullscreen></iframe>

---

날씨가 서늘해 져서 45 SuperTriode 를 연결해서 구성을 변경해서 청음해봤습니다. 

>아이폰7플러스 (Airplay) >>> 라즈베리파이3B+ (Allo Boss DAC PCM5122 Hat, Master 모드) >>> 프리앰프 >>> 45 SuperTriode >>> ProAc 태블릿 30주년 

<iframe width="560" height="315" src="https://www.youtube.com/embed/AEbnNqBUhdM" frameborder="0" allowfullscreen></iframe>

---

라즈베리파이 3용 smpd v0.9.7 (최종)은 upnp 가 지원이 안됩니다. 그래서 애플뮤직을 Airplay 로 재생을 했습니다. 애플 무손실 (16bit/44.1k) 이고 smpd 에서 Airplay를 기본으로 지원하고 있습니다.

DAC는 프리앰프에 설치되어 있는 AlloBoss DAC 이고 DAC의 자체 클럭을 이용하는 Master 모드로 작동합니다. 물론 smpd 에서 드라이버를 변경했습니다.

녹음은 아이폰 5s 에 굴러다니는 콘덴서 마이클를 연결했습니다. 자가 수리를 몇 번해서 그런 iphone5s 가 살짝 맛이 가서 녹음시 고주파 노이즈가 살짝 깔려 있습니다. 앰프 노이즈는 아닙니다.

역시 직열 삼극관의 소리는 매력적입니다. 진공관값이 계속 오르는 이유일까요?

SMPD 를 사용해 보고 싶어서 문의를 하시는 분들이 계셔서 SMPD 포럼에 가입하는 방법을 알려드리겠습니다. 원래 회원제라서 마구 배포하시면 안되고 포럼에 가입하시고 이미지를 다운 받아서 사용하시면 될 것 같습니다. 포럼 가입에 엄격한 조건이 있는 것도 아닙니다. diyaudio 에 관련 링크입니다.

[diyAudio Symphonic MPD 글타래](https://www.diyaudio.com/forums/vendor-s-bazaar/355137-symphonic-mpd-3.html#post6222689)

I'm a member of SMPD forum group that is trying to internationalize SMPD.

So, I would like to add some explanations about the GPL. This explains why SMPD's software is open to the public on a membership basis.

SMPD was released to the public in late 2017. At this time, there was no membership system and anyone could download it. I don't know if the kernel source has been modified at this point. The PhileWeb forum was used to exchange information for the development. This forum is the Japanese version of diyAudio.

In late 2018 a version using Xenomai as the real-time kernel was released and thorough tuning for higher sound quality has begun. It seems that the scale of modification of the kernel source code has become large around this time.

In March of last year, a PhileWeb member interested in this tuning requested disclosure of the source code.

Papalius rejected this request because it was before version 1.0 was released and it was not ready to be released. And he set up a dedicated forum where only members could download SMPD and write/exchange information for development. Therefore, I think it's better to discuss the source code in a dedicated forum. Thank you for your understanding.

I would like to add about SMPD membership registration.

Anyone who writes in this thread is unconditionally admitted as a member. If you are interested in SMPD even if you haven't written in this thread, please send me an email with the reason why you are interested in SMPD. If there is no problem, I would like to approve it. As Papalius' first message says, my email address is **"kubotayo@jcom.home.ne.jp"**.

When Papalius is focused on development, I think it would be faster if you sent an email to my address.

위의 Kubotayo 씨 이메일에 메일을 보내시는데 그냥 무턱대고 가입해 달라고 하시지 말고 위의 내용대로 왜 SMPD에 관심을 가지게 되었는지 간략하게 적어서 보내시기 바랍니다. 일본인이기 때문에 영어 또는 일본어로 보내시면 됩니다. 

포럼이 상업적인 곳이 아니고 아마도 자원 봉사자들이 분업을 해서 각자 맡은 역할을 하기 때문에 바로 바로 응답이 안오고 하루 이틀 걸릴 수도 있습니다. 

일본어로 초청 메일이 오면 링크를 눌러서 id 와 암호를 만듭니다. 아마 본인 이메일 확인 메일이 하나 더 옵니다. 클릭해서 본인 확인 하시면 절차가 끝납니다.

​

포럼은 일본어로 되어 있으니 크롬으로 한국어로 번역해서 보시면 됩니다. 영어 질의 응답하는 메뉴가 있으니 영어로 문의를 하면 도움을 받을 수 있습니다. 바로 바로 응답은 기대하시지 않는 것이 좋습니다.  
​