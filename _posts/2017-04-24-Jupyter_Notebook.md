---
layout: post
title: Jupyter tutorial: 01_intro_install
description: "Jupyter tutorial"
headline: "Jupyter tutorial: 01_intro_install"
categories: Misc
tags: 
  - Misc
comments: false
mathjax: true
featured: false
published: true
---


# Jupyter tutorial
## 01\_intro\_install

### Jupyter가 뭐지?
- Jupyter notebook (이하 Jupyter로 명칭)은 코드 및 데이터 시각화를 위한 여러 기능을 제공하는 웹 애플리케이션이다. 
> (공식홈페이지 왈) "The Jupyter Notebook is an open-source web application that allows you to create and share documents that contain live code, equations, visualizations and explanatory text. Uses include: data cleaning and transformation, numerical simulation, statistical modeling, machine learning and much more."  [공식 링크](http://jupyter.org/)

<br>

### Jupyter로 할 수 있는 것들
#### (1) 코드 작성 및 정리
- Jupyter는 Python에만 국한된 웹앱이 아닌, 여러 언어를 지원하는 플랫폼 같은 것이라는 점  
	> e.g. Python, Bash, Java, C 등등 심지어 Matalb까지 지원됨!! (참고 [Jupyter지원 언어 Kernels](https://github.com/jupyter/jupyter/wiki/Jupyter-kernels))  
- 코드 하이라이팅, 라인 정렬, 함수 미리보기 등의 기능 지원
- 코드를 작성 후 코멘트를 markdown이나 html로 작성할 수 있으므로 배포/공유에 용이함
  
#### (2) 코드 및 데이터 시각화
- 코드 사이사이에 그래프를 삽입하여 자연스럽게 code flow를 유지할 수 있음
- 단순 플랏 뿐만 아니라, interactive 플랏도 지원함
- 시각화의 끝판왕들 예시 http://nb.bianp.net/sort/views/
  
#### (3) 추가적인 IDE없이 가볍게 프로그램 돌리기
- 물론 중요한 개발 업무나 코드 실행 등은 Terminal로 하는 것을 추천 (예: nohup을 사용해야하는 작업 등 --> 하지만 Jupyter 내부에서 터미널을 열어서 작업할 수 있다는 장점도 존재)

#### (4) 서버 컴퓨터에 터미널로 접속할 필요 없이, GUI환경으로 서버 접속 및 코드 작성 가능
- 로컬에서 서버에 접속하여 작업을 해야할 경우, 시각적으로 편리하게 접속하고 작업할 수 있음 (설치 부분 참조)

#### (5) Jupyter로 작성한 코드나 시각화 자료를 GitHub에 업로드 가능
- Jupyter로 작성한 .ipynb파일을 업로드하면, GitHub페이지에서도 동일하게 시각화되어서 손쉽게 확인하고 공유할 수 있음 (E.g. [깃헙 예시](https://github.com/jaekookang/useful_bits/blob/master/Machine_Learning/RNN_LSTM/predict_character/rnn_char.ipynb))

<br>

### Jupyter 설치
- 필자가 추천하는 Jupyter 설치 방법 및 설치 환경  

> 1. Anaconda 설치  
> 2. 가상환경을 만들고 Anaconda 패키지들을 설치
> 3. 가상환경 내에서 Jupyter를 실행하여 사용

- 필자는 로컬 컴퓨터에 이미 설치되어 있는 Python을 사용하지 않고, Anaconda에 설치된 Python을 사용함 (Anaconda3, Python3.5 사용 중)
- 또한 Anaconda의 'conda' 커맨드를 활용하여 가상환경을 만들고 TensorFlow를 설치하여 사용함. 가상환경에 TensorFlow를 설치하고 사용하는 것이 편리하다고 생각함. 왜냐하면, 때에 따라서 TensorFlow의 GPU버전과 CPU버전을 각각 설치하여 필요할 때 선택적으로 사용할 수 있고, TensorFlow의 다른 버전을 설치한 뒤 버전 충돌 없이 원하는 버전을 사용하여 프로그램을 실행할 수 있기 때문
- 여기서, 가상환경이란? "가상환경 = 폴더". 가상환경은 Python과 모듈들을 따로 모아둔 폴더일 뿐.

#### 1. Anaconda 설치
- 공식 페이지에 접속하여 [https://www.continuum.io/downloads](https://www.continuum.io/downloads) Python 3.6버전 (2017.04 기준)의 설치 파일을 다운 받아서 설치할 것
  - macOS나 Linux, Windows 등 본인 OS에 맞게 설치할 것
  - Graphic installer나 Command-line installer 둘 중에 하나를 선택하여 설치
  - Anaconda설치 후, Terminal에서 `which conda`를 입력하면 Anaconda의 설치경로가 나옴. 참고로 `conda`가 주요 명령어임
  - Anaconda설치 후, 기본 Python의 경로가 Anaconda내의 Python으로 바뀜. 확인 필요 (Terminal에서 `which python`를 입력한 결과를 확인)
  
	```bash  
	$ which conda
	/Users/jaegukang/anaconda3/bin/conda  
	$ which python   
	/Users/jaegukang/anaconda3/bin/python
	```

#### 2. 가상환경을 만들고 Anaconda 패키지들을 설치
- 예시, 가상환경의 이름을 'my_env'로 하고 모든 Anaconda패키지를 my_env가상환경에 설치하는 경우  
    - my_env라는 이름의 가상환경을 만들고, anaconda패키지를 옮겨오기
    - 여기서 모든 anaconda를 다 불러와서 설치해도 되고, 필요한 모듈만 선택적으로 설치 가능  

	```bash
	Jaegus-Air: jaegukang$ conda create -n my_env anaconda 
	```  
  
	- my_env 가상환경 모드에 진입하기  
	- 커맨드라인에 (my_env)가 추가됨  

	```bash  
	Jaegus-Air: jaegukang$ conda activate my_env
	(my_env) Jaegus-Air: jaegukang$
	```

    - python의 경로가 my_env 가상환경에 있는 python의 위치로 변경된 것 확인 
    - 가상환경은 그냥 새로운 폴더일 뿐

	```bash
	(my_env) Jaegus-Air: jaegukang$ which python
	/Users/jaegukang/anaconda3/envs/my_env/bin/python  
	```

#### 3. 가상환경 내에서 Jupyter를 실행하여 사용  
	
```bash
(my_env) Jaegus-Air: jaegukang$ jupyter notebook
```

- 위의 명령어를 입력하는 순간, 컴퓨터의 default web browser (e.g. Chrome)가 열리면서 Jupyter 환경이 열림
- 터미널 창은 일종의 log가 기록되는 화면으로 바뀜
- 만약 이렇게 터미널이 남아 있는 것이 보기 싫다면 nohup을 이용해서 jupyter log화면을 숨길 수 있음

	```bash
	Jaegus-Air: jaegukang$ nohup jupyter notebook >jupyter.log &  
	Jaegus-Air: jaegukang$ kill %(pgrep jupyter)      % Jupyter를 끌 경우
	                                                  % 혹은 kill %(pgrep python)
	```

- Jupyter설치 관련 참고 사이트: [http://jupyter.readthedocs.io/en/latest/install.html](http://jupyter.readthedocs.io/en/latest/install.html)
- Anaconda 가상환경 관련 참고 사이트: [https://conda.io/docs/using/envs.html](https://conda.io/docs/using/envs.html)
- Jupyter의 자세한 사용법 관련 참고 사이트: [https://www.datacamp.com/community/tutorials/tutorial-jupyter-notebook#gs.qbBy2=I](https://www.datacamp.com/community/tutorials/tutorial-jupyter-notebook#gs.qbBy2=I)
- [useful_bits](https://github.com/jaekookang/useful_bits)

<p align="right"> Jaekoo Kang <p>
