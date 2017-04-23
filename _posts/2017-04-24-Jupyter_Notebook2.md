---
layout: post
title: "Jupyter tutorial: 02_server_connection"
description: "Jupyter tutorial"
headline: "Jupyter tutorial: 02_server_connection"
categories: Misc
tags: 
  - Misc
comments: false
mathjax: true
featured: false
published: true
---

# Jupyter tutorial
## 02\_server\_connection

- 로컬 컴퓨터에서 Jupyter를 활용한 작업을 할 수 있지만, **EMCS**처럼 서버를 빈번하게 사용하는 경우에 Jupyter가 용이하게 사용될 수 있음
- Jupyter를 활용하여 서버 컴퓨터에 접속하고 작업을 하기 위한 단계는 두 가지 단계로 나뉨

> 1. 원격 서버에서의 설정  
> 2. 로컬 컴퓨터에서의 설정  
- 작동 원리는, 원격 서버에서 먼저 jupyter를 실행시키고 특정 포트를 연 뒤, 열려 있는 서버의 포트로 로컬에서 접속하는 것

<br>

### 1. 원격 서버에서의 설정
- 먼저 터미널에서 서버로 접속하기 (e.g. ssh)
- 서버에서 바로 jupyter notebook을 접속해도 되지만, 미리 가상환경을 설정해둔 것이 있다면 가상환경을 activate한 뒤 Jupyter를 실행시키는 것이 좋음 ([Jupyter tutorial:01_intro_install](https://emcslabs.github.io/misc/Jupyter_Notebook) 참고)
- 아래 YYYY에 들어가는 네 자리의 포트 넘버는 서버에서 사용하고 있지 않은 포트 넘버를 넣으면 됨
- 가끔 ```--no-brower```라는 옵션을 넣어주기도 하지만 안해도 무방함 (어차피 서버컴에는 모니터가 없어서 Jupyter가 안열린다능)

#### 1-1. 서버에서 Jupyter를 바로 실행하는 경우

```bash
$ jupyter notebook --port=YYYY
```

#### 1-2. 서버에서 가상환경을 열고 Jupyter를 실행하는 경우
```bash
$ source activate my_env
$ (my_env) [zzandore@cherry ~]$ jupyter notebook --port=YYYY
```
- __Jupyter를 실행한 터미널의 화면은 절대 끄지 말 것 (끄게 되면 Jupyter도 꺼짐)__

<br>

### 2. 로컬 컴퓨터에서의 설정
- 새로운 터미널 창을 하나 열고, 아래와 같이 서버로 접속하기
- 아래의 XXXX는 서버로 접속하는 내 컴퓨터의 포트에 해당
- 즉, **"나의 XXXX에서 너의 YYYY로 접속하겠다"**는 뜻임

```bash
$ ssh -L XXXX:localhost:YYYY zzandore@OO.OOO.OOO.OOO
```
- 이후 서버 비밀번호를 입력하고 접속하기
- 그런데 아무리 찾아봐도 내 웹 브라우저 (크롬)에서는 아무 것도 안열려 있네?!
    - 아까 열어둔 터미널 (Jupyter log)화면을 보면 웹브라우저에서 접속할 수 있는 주소가 떠 있는 것이 보일 것이다. 그 주소를 복사해서 원하는 브라우저에서 접속하면 됨
    - 하지만 그냥 붙여넣기하면 웹브라우저에서는 오류가 뜸
    - 여기서 웹 브라우저 주소를 수정하여 입력하면 됨
    
    > 예를 들어 아래와 같은 주소가 있을 때  
    > http://localhost:8888/?token=44ae19563c2a14e012609d0980768  
    > 위의 8888을 YYYY로 바꿔주면 됨. 여기서 YYYY는 서버의 열린 포트를 의미함

<br>

---

### 시나리오: "서버에서 TensorFlow돌려야지~"
#### 1. 원격 서버에서의 설정
```bash
$ ssh -p OOOO zzandore@OO.OOO.OOO.OOO  % 서버 접속
$ source activate tensorflow           % 가상환경 열기

% 참고로 필자의 서버에는 tensorflow라는 가상환경이 있고
% 여기에 TensorFlow를 설치해서 사용하고 있음

$ nohup jupyter notebook --port=8000 >jupyter.log &

% 이후 서버에서 빠져나오기 (어차피 Jupyter가 열려 있으므로)
```

#### 2. 로컬 컴퓨터에서의 설정
```bash
% 내 로컬의 8888포트에서 서버의 8000포트로 접속하기
$ ssh -p OOOO -L 8888:localhost:8000 zzandore@OO.OOO.OOO.OOO
$ cat jupyter.log   % 로그파일을 열어서 Jupyter에 접속할 수 있는 주소를 복사해옴

% 이후 웹브라우저에서 복사된 주소를 붙여넣기 한 뒤
% 주소의 localhost:YYYY 부분의 YYYY를 8000으로 바꿔줌
```

#### 3. Jupyter 종료하기
- Jupyter를 logout해도 Jupyter는 완전히 꺼지지 않고 있음
- 아래 커맨드를 터미널에서 입력하기

```bash
$ kill $(pgrep jupyter)

       % 또는
       
$ kill $(pgrep python)
```


<p align="right"> Jaekoo Kang <p>
