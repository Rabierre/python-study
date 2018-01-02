# Python 환경 세팅하기
virtualenv, conda
virtualenv vs conda: https://stackoverflow.com/questions/34398676/does-conda-replace-the-need-for-virtualenv

## 파이썬 시작하기
파이썬 개발을 시작하기 앞서 python이 설치되어 있지 않다면 먼저 설치부터 시작한다.
### Mac Os
```$ brew install python3```
### Linux 
```$ apt-get install python3```
```$ yum install python3```
Or just download here: https://www.python.org/downloads/
파이썬 환경변수 설정 https://docs.python.org/3/using/windows.html

Windows의 경우 환경변수 설정이 필요할 수도 있다. Windows용 install launcher를 사용하면 설치시에 환경변수 설정도 같이할 수 있다.

## 패키지 매니저
pip https://pypi.python.org/pypi/pip 
파이썬 패키지 관리자. 파이썬으로 만들어진 패키지들을 명령어로 쉽게 설치할 수 있다.

## 독립된 개발 환경 구축
pip로 인스톨한 라이브러리들은 pip 버전에 따라 /usr/… 아래의 경로에 설치된다. 이와같은 중앙화된 장소에 저장된 라이브러리들은 서로 같은 라이브러리를 쓰지만 버전이 다른 경우가 있을 경우 문제가 생긴다. 한 라이브러리를 업데이트하면 그 라이브러리에 디펜던시가 있는 다른 라이브러리에 문제가 생길 수 있다. 그래서 프로젝트마다 별도의 환경을 구축하는 것이 필요하다.
가상 환경을 구축하는데 virtualenv가 많이 쓰였으나 비교적 새로 나온 conda가 편의성이 크므로 conda를 이용한다.

### Conda 설치방법
Install https://conda.io/docs/user-guide/install/index.html
Anaconda 또는 miniconda 중에 하나를 선택해서 설치하면 된다. Anaconda와 Miniconda의 차이는 다음 링크(https://conda.io/docs/user-guide/install/download.html#anaconda-or-miniconda)에서 확인할 수 있다. https://www.anaconda.com/download/
https://conda.io/miniconda.html

### Conda 실행방법
https://conda.io/docs/user-guide/getting-started.html
독립환경을 구축하려는 폴더로 가서 다음 명령어를 실행하면 된다.

`conda create --name <envname> python=<version> <optional dependencies>`

가상환경을 삭제하고 싶을 때는 다음 명령어를 실행하면 된다.

`conda env remove --name <envname>`

##### conda 가상환경 구축 예시
```
$ mkdir test
$ cd test
$ conda create --name test
$ source activate test
(test) $ 
(test) $ source deactivate test
$ conda env remove --name test
```

conda로 구축된 환경을 이용하려면 pip를 직접 쓰지 않고 conda를 통해 사용해야 한다.

`conda install --name <envname> <packagename>`
##### 가상환경 내에서 패키지 설치
```
$ source activate test
$ conda install scipy

```
설치된 결과
```
$ conda install scipy
Fetching package metadata ...........
Solving package specifications: .

Package plan for installation in environment /Users/seojihye/miniconda3/envs/test:

The following NEW packages will be INSTALLED:

    ca-certificates: 2017.08.26-ha1e5d58_0   
    certifi:         2017.11.5-py36ha569be9_0
    intel-openmp:    2018.0.0-h8158457_8     
    libcxx:          4.0.1-h579ed51_0        
    libcxxabi:       4.0.1-hebd6815_0        
    libedit:         3.1-hb4e282d_0          
    libffi:          3.2.1-h475c297_4        
    libgfortran:     3.0.1-h93005f0_2        
    mkl:             2018.0.1-hfbd8650_4     
    ncurses:         6.0-hd04f020_2          
    numpy:           1.13.3-py36h2cdce51_0   
    openssl:         1.0.2n-hdbc3d79_0       
    pip:             9.0.1-py36h1555ced_4    
    python:          3.6.4-hc167b69_0        
    readline:        7.0-hc1231fa_4          
    scipy:           1.0.0-py36h1de22e9_0    
    setuptools:      36.5.0-py36h2134326_0   
    sqlite:          3.20.1-h7e4c145_2       
    tk:              8.6.7-h35a86e2_3        
    wheel:           0.30.0-py36h5eb2c71_1   
    xz:              5.2.3-h0278029_2        
    zlib:            1.2.11-hf3cbc9b_2       

Proceed ([y]/n)?  y

intel-openmp-2 100% |################################################################################################################################| Time: 0:00:00   7.90 MB/s
libgfortran-3. 100% |################################################################################################################################| Time: 0:00:00   9.62 MB/s
mkl-2018.0.1-h 100% |################################################################################################################################| Time: 0:00:15  10.40 MB/s
python-3.6.4-h 100% |################################################################################################################################| Time: 0:00:01  10.49 MB/s
numpy-1.13.3-p 100% |################################################################################################################################| Time: 0:00:00  10.42 MB/s
scipy-1.0.0-py 100% |################################################################################################################################| Time: 0:00:01  10.58 MB/s
$
```
