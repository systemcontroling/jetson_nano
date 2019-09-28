# JETSON NANO SETUP INSTALL
jetpack 설치 후 opencv 와 tensorflow 1.14 버전이 설치 된 것을 확인 할 수 있다.
여기서 NVIDIA에서 제공하는 jetson-inference의 예제를 돌리기 위해서 몇가지 설치 과정이 필요하다.

## Installing system packages and prerequisites
jetson nano 시작에 필요한 시스템 packages 설치

    $ sudo apt-get install git cmake
    $ sudo apt-get install libatlas-base-dev gfortran
    $ sudo apt-get install libhdf5-serial-dev hdf5-tools
    $ sudo apt-get install python3-dev

## python 페키지 매니저 pip install

    $ wget https://bootstrap.pypa.io/get-pip.py
    $ sudo python3 get-pip.py
    $ rm get-pip.py

## virtualenv,virtualenvwrapper install

Python 가상 환경을 관리하기 위해 virtualenv 및 virtualenvwrapper 설치

    $ sudo pip install virtualenv virtualenvwrapper

virtualenv 및 virtualenvwrapper를 설치 한 후 ~ / .bashrc 파일을 업데이트 해야합니다.

    	$ vi ~/.bashrc

마지막 부분에 아래의 글자를 입력 한후 저장하여 ~/.bashrc 를 업데이트 시킨다.

    # virtualenv and virtualenvwrapper
    export WORKON_HOME=$HOME/.virtualenvs
    export VIRTUALENVWRAPPER_PYTHON=/usr/bin/python3
    source /usr/local/bin/virtualenvwrapper.sh

source 명령어로  ~/.bashrc  파일 로드한다.
    
    $ source ~/.bashrc

가상환경 생성 (사용 할 API나 사용 영역에 따라 구분 해서 만들어 주는 것이 좋음. )

    $ mkvirtualenv deep_learning -p python3

위의 명령어로 python3의 환경의 deep_learning이라는 가상환경이 생성 되었다.

## Installing TensorFlow and Keras on the NVIDIA Jetson Nano

설치 전  deep_learning 이라는 가상환경에 설치 하기 위해서  아래의 명령어를 사용한다.
   
    $ workon deep_learning (linux의 source activate deep laarning 과 같은 기능 수행 )

numpy 설치

    $pip install numpy

설치 소요 시간이 15분 정도 라고 하는데 인터넷 상태에 따라 시간이 더 소요되는 것 같다. (모든 설치시 랜선을 사용하는 것을 추천합니다. )

Tensorflow gpu install 

    $ pip install --extra-index-url https://developer.download.nvidia.com/compute/redist/jp/v42 tensorflow-gpu==1.13.1+nv19.3

설치는 되어 있으나 opencv 버전처럼 다르면 작동시 어려움이 있을 수 있어서 그냥 설치함 (선택)

마지막으로 SciPy and Keras

    $ pip install scipy
    $ pip install keras

35분 정도 소요된다고 하였는데 넉넉 잡아 50분 정도 소요된 것 같다.

## jetson-inference 

    $ git clone https://github.com/dusty-nv/jetson-inference
    $ cd jetson-inference
    $ git submodule update --init
    $ mkdir build
    $ cd build
    $ cmake ..
    $ make
    $ sudo make install

위의 명령어를 통하여 jetson-inference 사용할 준비가 끝났다.

추후에 jetson-inference 예제 구현 방법 업로드 예정 
