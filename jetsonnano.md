# Jetson nano jepack 4.2.2 install
Jetson nano jepack 4.x.x 버전에는 flash error 발생 이슈가 있음.

##  설치시 준비 사항 
1. host pc (linux ubuntu 18.04 추천)
2. micro 5pin cable, 128G micro-sd 카드 및 리더기
3. NVIDIA® Jetson Nano™ Developer Kit 
4. 5V 4A 전원 공급 아답터 (추천)

## 설치 순서 
1.  128G micro-sd 카드를 포맷
2.  Etcher 를 다운 받아 설치. 
https://www.balena.io/etcher
3. nano os 다운 
https://developer.nvidia.com/jetson-nano-sd-card-image-r322
4. Etcher 실행 후 라즈베리 파이 와 같이 os를 sd 카드 언진다.
5. sdk- manager 다운 
https://developer.nvidia.com/nvidia-sdk-manager
6. sdkmanager install

        $ sudo dpkg -i sdkmanager_0.9.14-4961_amd64.deb

        $ sudo apt --fix-broken install
7. sdk manager 실행

        타겟 보드 설정에서  jetson-nano Developer Kit  선택후  jetpack 버전 4.2.2 선택 후 다음 단계로 넘어간다.

        경로 설정은 기본으로 설정 하여 설치 나중에 자신이 변경해서 설치 하면 os flash 할떄 찾기 힘듬.
8. HOST COMPONENTS,jetson os flash 다운

        jetson os flash를 위해서 일단 타겟 보드dml jetpack 구성소프트웨어 설치 전단계 까지 선택후 실행. 

9. os flash ( Recovery Mode 진입 후 진행)

        $ sudo  ./flash.sh -S 110GiB jetson-nano-qspi-sd mmcblk0p1
        sdk manager로 설치 하면 메모리를 다사용 못함.

    위의 command 창 명령어로 os flash 를 진행 하면 된다.

    flash가 다되면 자동 부팅이 된다.

10.  jetson nano 부팅 후 host name과 비밀번호 설정.

11. sdk manager 실행 

        Target Components 설치를 위한 실행 이 과정에서 nano의 host name과 비밀번호 필요. 

12.  Target Components 다운

    ssh로 타겟 보드에 날려 주는 것이기 때문에 고정 ip 필요 (변경하지 말고 수행하는것 추천)

## updata 

엽데이트는 리눅스 ubuntu 18.04와 같은 명령어 로 수행 하면 됨.

    $ sudo apt-get update
    $ sudo apt-get upgrade