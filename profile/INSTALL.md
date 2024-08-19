## 📌실행 방법(로컬)

### 🔍 Back 실행방법

### 0. Git clone

`git clone https://github.com/CLOVIDER/kic-backend.git`

### 1. application.yml

백엔드 yml 파일은 이메일로 첨부하겠습니다 :)

- MySQL: 클라우드 데이터베이스
- Redis: 로컬 레디스

**Redis 실행하기**

`brew services start redis`

### 2. Spring Server 실행하기

![image](https://github.com/user-attachments/assets/90995c32-4fb8-4112-9888-5486e6416beb)

---

### 🔍 Front 실행방법

### 0. Git Clone

`git clone https://github.com/CLOVIDER/kic-frontend.git`

### 1. FE 프로젝트  종속성 설치
> 윈도우 버전 nvm 다운로드 방법
      
```bash
# nvm install
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash

# 환경 변수 설정
## 1
nano ~/.bashrc

## 2
export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"

# bashrc 실행
source ~/.bashrc

# nvm 실행
nvm install 21.7.1

# .nvmrc 파일 생성
echo "21.7.1" > .nvmrc

# pnpm install
nvm use
npm install -g pnpm
pnpm run dev
```

> 맥 버전 nvm 다운로드 방법
      
```bash
# 기본 설치방법(MAC)
brew install nvm

# 환경변수 설정(bash쉘의 경우)

# nvm 디렉토리 생성
mkdir ~/.nvm

# ~/.bash_profile 설정
export NVM_DIR="$HOME/.nvm"
[ -s "/usr/local/opt/nvm/nvm.sh" ] && . "/usr/local/opt/nvm/nvm.sh"
[ -s "/usr/local/opt/nvm/etc/bash_completion" ] && . "/usr/local/opt/nvm/etc/bash_completion"

# 적용
source ~/.bash_profile

# Node.js 버전 지정
nvm install 21.7.1

# .nvmrc 파일 생성
echo "21.7.1" > .nvmrc  
```

#### 2. `http://localhost:3000`에 접속합니다.

- [접속하기](http://localhost:3000)


> 👥 **계정 정보**
> 기존 사내데이터를 사용하는로직이므로 회원가입 기능이 없습니다. 
> 아래 계정으로 테스트가 가능합니다.
>
>**USER**
>id : 
>pwd : 
>
> **ADMIN**
>id : admin9
>pwd : admnin12
