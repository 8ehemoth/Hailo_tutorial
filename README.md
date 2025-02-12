# Hailo Model Build Environment 세팅

Hailo 실행파일 (`.hef`) 컴파일을 위해 Hailo에서 제공하는 
Dataflow Compiler 및 Model Zoo 설치 방법

(출처 : https://note.mmmsk.myds.me/Projects/Embedded-AI/(Hailo)-Hailo-Dataflow-Compiler-%EC%84%A4%EC%B9%98)

### 개요

- Hailo 구성에는 크게 Model Build 환경과 Runtime 환경으로 나누어짐
- Model Build 환경에서 Hailo 실행파일을 컴파일 할 수 있음 (Hailo 디바이스가 필요없음)
- Runtime 환경에서 컴파일된 실행파일을 Hailo를 통해 실행할 수 있음 (Hailo 디바이스가 장착된 환경)
- Hailo Dataflow Compiler와 Hailo Model Zoo를 설치해 Model Build 환경을 구축함 
![[Pasted image 20250212213413.png]]

## Hailo Dataflow Compiler 설치

#### 최소 시스템 사양 (2024.04 버전)

1. Ubuntu 20.04/22.04, 64-bit (supported also on Windows, under WSL2)
2. 16+ GB RAM (32+ GB recommended)
3. Python 3.8/3.9/3.10, including pip and virtualenv
4. python3.X-dev and python3.X-distutils (according to the Python version), python3-tk, graphviz, and libgraphviz-dev packages. Use the command sudo apt-get install PACKAGE for installation.

*설치가이드: Dataflow Compiler v3.29.0
https://hailo.ai/developer-zone/documentation/v3-29-0/?sp_referrer=install/install.html

### Hailo Version

- Hailo DFC: 3.27.0
- Hailo Model Zoo: 2.11.0
- 24.11.18 ) 리눅스 커널 6.5.0-44-generic 버전에서 hailort-4.18 버전 동작 가능한 것으로 확인

### GPU 옵션

Nvidia’s Pascal/Turing/Ampere GPU architecture (such as Titan X Pascal, GTX 1080 Ti, RTX 2080 Ti, or RTX A4000)
GPU driver version 525
CUDA 11.8
CUDNN 8.9

### 패키지 다운로드

hailo_dataflow_compiler-3.27.0-py3-none-linux_x86_64.whl
Hailo 홈페이지에서 회원가입 후 개발자존에서 최신버전 다운로드 가능 

https://hailo.ai/developer-zone/software-downloads/

### 패키지 설치

1. python 가상 환경 생성

```
virtualenv <VENV_NAME>
```

2. 가상환경 활성화

```
. <VENV_NAME>/bin/activate
```

3. 다운로드받은 패키지파일 설치

```
pip install <hailo_dataflow_compiler-X.XX.X-py3-none-linux_x86_64.whl>
 
# +) optional 필요시 사전설치 해야됨
apt install graphviz
apt install libgraphviz-dev
```

4. CLI 명령어로 테스트

```
hailo -h
```


### Hailo Model Zoo

Hailo Model Zoo는 다양한 잘알려진 모델들을 Hailo 디바이스에 최적화하여 사전 컴파일한 실행파일을 제공하고, 양자화나 파인튜닝을 위한 스크립트 및 기능을 제공함


### Hailo Model Zoo 설치

0. Dataflow Compiler 가 설치된 파이썬 가상환경에서 실행

1. Git 레파지토리 다운로드

```
git clone https://github.com/hailo-ai/hailo_model_zoo.git
```

2. 패키지 설치

```
cd hailo_model_zoo; pip install -e .
```

3. 실행 테스트

```
hailomz info mobilenet_v1
```
