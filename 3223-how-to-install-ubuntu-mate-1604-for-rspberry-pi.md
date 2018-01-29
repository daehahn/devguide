# How to install Ubuntu MATE 16.04 for Raspberry Pi

---

이 페이지는 Raspberry Pi에 Ubuntu MATE 16.04 설치 방법에 대해 기술합니다.

#### Ubuntu MATE 16.04 for Raspberry 
[Download Ubutu Mate 16.04 for Raspberry Pi 3](https://ubuntu-mate.org/download/)

#### 필요한 물품
- Raspberry Pi 3
- Micro SD card
- Micro USB power supply \(2.1 A\)
- TV or monitor and HDMI cable
- Keyboard and mouse

#### Ubuntu MATE 16.04 설치

##### 1. 다운받은 Ubutu Mate 16.04 이미지 압축 해제

##### 2. 이미지를 굽는 프로그램을 다운받아 설치
[Download etcher](https://etcher.io/)

##### 3. Micro SD Card를 PC에 장착

##### 4. Etcher 프로그램을 실행
- Select Image를 클릭하고, 다운받은 Ubuntu Mate 16.04 이미지\(ubuntu-mate-16.04.2-desktop-armhf-raspberry-pi.img\)를 선택합니다
- Select drive를 클릭하여, Micro SD Card의 경로를 설정합니다.
- Flash 를 클릭합니다.
- 이미지 flash가 모두 끝나면, Micro SD Card를 PC에서 분리하여 준비한 Raspberry Pi 3에 창작합니다.
- 준비한 모니터와 키보드, 마우스, 인터넷을 Raspberry Pi 3에 연결합니다.
- Micro USB power supply를 Raspberry Pi 3에 연결합니다.
- Ubuntu Mate 16.04를 설치합니다. 
    - 예제는 ID: roy, Computer Name: RPi3 로 되어 있습니다.
- 설치가 완료되면 아래 명령을 실행합니다.
```
sudo apt-get update && sudo apt-get upgrade
```
- 설치된 Java version을 확인합니다.
```
$ java -version
openjdk version "1.8.0_151"
OpenJDK Runtime Environment (build 1.8.0_151-8u151-b12-0ubuntu0.16.04.2-b12)
OpenJDK Client VM (build 25.151-b12, mixed mode)
```

#### Audio 환경 설정 및 테스트
- ##### 오디오 환경
  - 기본 상태
    1. Audio Input: None
    2. Audio Output: Raspberry Pi 3.5mm jack
    
  - XMOS 연결한 상태: 
    1. Audio Input: XMOS
    2. Audio Output: XMOS
    
##### 1. XMOS 보드를 Raspberry Pi에 연결
- 연결이 잘 되었는지 확인합니다.
  
##### 2. Audio 출력 테스트
- 소리가 정상적으로 출력되는지 확인합니다.
- 테스트를 종료하려면 Ctrl + C 를 누르세요
```
$ speaker-test -t wav
```
![](/assets/raspbian_audio_step_4.jpg)

##### 3. Audio 입력 테스트
- 5초 동안 음성을 저장합니다. 아래 커맨드를 입력하고 음성을 입력하세요.
```
$ arecord --format=S16_LE --duration=5 --rate=16000 out.wav
Recording WAVE 'out.wav' : Signed 16 bit Little Endian, Rate 16000 Hz, Mono
```
##### 4. Audio 녹음 테스트
- 저장된 음성을 재생합니다. 음성이 정상적으로 재생되는지 확인합니다.
```
$ aplay out.wav
```



