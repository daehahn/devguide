# Install Oracle JDK 8 for Ubuntu 16.04

---

#### Install chrome 

##### 1. Chromium brower 검색
- Ubuntu 16.04에 Chromium brower를 설치합니다.   
    (소프트웨어를 최신으로 업데이트 하면 내장된 firefox browser가 정상적으로 실행되지 않습니다.)
- System &gt; Administrator &gt; Software Boutique를 실행합니다.
![](/assets/avs_setup_step_1.jpg)

- Search 아이콘을 클릭합니다.
![](/assets/avs_setup_step_2.jpg)

##### 2. Chromium  brower 설치
- Search Box에 Chromium 를 입력하고 Enter를 누릅니다. 
- Chromium 이 검색되면 "Install"을 클릭합니다.
![](/assets/avs_setup_step_3.png)

##### 3. Chromium brower 실행
- Chromium 설치가 완료되면 "Lanuch"를 클릭합니다.
![](/assets/avs_setup_step_4.png)

##### 4. Chromium brower를 default browser로 설정
- Chromium 브라우져의 오른쪽 상단 메뉴를 클릭한 후, Settings를 선택합니다.
![](/assets/ubuntu_chromium_default_browser_step_1.png)
- 스크롤을 내려 Default browser 메뉴에서 MAKE DEFAULT 를 클릭합니다.
![](/assets/ubuntu_chromium_default_browser_step_2.png)

#### Install oracle JDK 8
Oracle JDK 1.8 버전을 설치합니다.
**Ubuntu MATE에서 OpenJDK 1.8로 AVS가 구동은 되나 AVS가 불안하여 멈추는 현상이 나타납니다.**

##### 1. Download JDK 8
- Oracle JDK 1.8을 다운받기 위해 아래 사이트에 접속 합니다.
[http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)

- Accept License Agreement를 클릭하고, Linux ARM 32 Hard Float ABI용 JDK를 다운받습니다.
![](/assets/avs_setup_step_5.jpg)

##### 2. Install JDK 8
- 터미널을 실행합니다. \(ssh로 원격에서 접속해서 작업을 진행해도 됩니다.\)
```
$ cd Download
$ sudo tar zxvf jdk-8u161-linux-arm32-vfp-hflt.tar.gz -C /opt
```

##### 3. Set default for oracle JDK 8
- Oracle JDK 1.8을 default java, javac로 설정합니다.
```
$ sudo update-alternatives --install /usr/bin/javac javac /opt/jdk1.8.0_161/bin/javac 1
$ sudo update-alternatives --install /usr/bin/java java /opt/jdk1.8.0_161/bin/java 1
$ sudo update-alternatives --config javac
$ sudo update-alternatives --config java
```
- sudo update-alternatives --config java 를 실행하면 아래와 같은 화면이 나타납니다. Ubuntu MATE 16.04에는 기본적으로 openjdk가 설치되어 있습니다. 그리고 기본으로 openjdk가 default java로 설정되어 있습니다. \(\* 표시가 default를 의미합니다.\)

- AVS는 Oracle JDK를 지원하므로, default java를 Oracle JDK 1.8로 변경합니다.

- "1"을 입력하고 Enter를 누릅니다.
![](/assets/avs_setup_step_6.jpg)

- 정상적으로 변경되었는지 확인합니다.
```
$ java -version
```

- 빨간색 박스와 같이 출력되면 정상적으로 설정된 것입니다.
![](/assets/avs_setup_step_7.jpg)

- JAVA\_HOME 설정하기
```
$ nano ~/.bashrc
```

- 제일 하단으로 내려가서 다음 내용을 추가합니다.
```
JAVA_HOME=/opt/jdk1.8.0_161
export JAVA_HOME
PATH=$PATH:$JAVA_HOME
export PATH
```
![](/assets/avs_setup_step_8.png)
Ctrl+o 를 눌러 내용을 저장한 후, Ctrl+x 를 눌러 에디터를 종료합니다.

- 수정한 bashrc를 현재 터미널에 적용합니다.
```
source ~/.bashrc
```

