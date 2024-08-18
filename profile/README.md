# 📌 Kids In Company - 사내 어린이집 공정한 추첨 서비스

<!-- 이미지 크기 수정-->

<img width="650" src="https://github.com/user-attachments/assets/39fd046f-86a1-489b-95be-17ea968277b6"/>

> ### WEB URL: [키즈인컴퍼니 사이트](http://kidsincompany.shop/)
> ### [FE Project](https://github.com/CLOVIDER/FE) </br>
> ### [BE Project](https://github.com/CLOVIDER/BE)
> 
> 작성자: 김현겸

<a href="https://hits.seeyoufarm.com"><img src="https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fgithub.com%2FCLOVIDER&count_bg=%2379C83D&title_bg=%23555555&icon=&icon_color=%23E7E7E7&title=hits&edge_flat=false"/>

## 목차

* [프로젝트 소개](#프로젝트-소개)
* [핵심 기능](#핵심-기능)
* [ERD](#ERD)
* [시스템 아키텍처](#시스템-아키텍처)
* [최적화한 사항](#최적화한-사항)
* [화면 구성](#화면-구성)
* [개발 기간](#개발-기간)
* [팀 & 서비스 소개](#팀-&-서비스-소개)
* [팀원 소개](#팀원-소개)
* [기술 스택](#기술-스택)

## ☘️ 프로젝트 소개
### 1️⃣ 서비스 기획 이유

> 사내 어린이집은 직원들에게 중요한 복지 시설입니다. 하지만 수요가 많아 모든 직원의 자녀가 어린이집을 이용할 수 없는 경우가 발생합니다.
>
> 이는 직원들 사이에서 불만을 일으키고, 공정성과 투명성에 대한 문제를 제기하게 만듭니다.

#### ✅ 그래서 저희 Clovider팀은 **공정한 가중치 적용하고** 이를 바탕으로 **당첨 확률 제공하여** 공정하고 투명한 서비스를 만들고자 합니다.

### 2️⃣ 서비스 차별점

> 1. **공정성 확보**: 근속년수, 사내 부부, 다자녀 가정 등 여러 타당한 가중치를 통해 추첨을 진행합니다.
>
> 2. **투명성 확보**: 신청한 어린이집 모집의 당첨 확률을 공개하여 추첨 과정과 결과를 투명하게 해 신뢰성을 확보합니다.
>
> 3. **효율성 향상**: 수작업으로 진행되는 추첨 과정은 시간이 많이 소요되고 오류가 발생할 가능성이 높습니다. 이를 자동화하여 효율성을 높입니다.

### 3️⃣ 서비스 소개

디케이테크인 내부의 공정하고 투명한 사내 어린이집 인원 배정을 위해 어린이집 모집과 추첨을 자동화한 서비스입니다.

## 핵심 기능

## ERD

<img width="1100" alt="image" src="https://github.com/user-attachments/assets/7f5aadd5-654a-4449-82ee-167a29d43917">

## 시스템 아키텍처

![image](https://github.com/user-attachments/assets/35de9337-e846-4131-87bf-7363e03d0a31)


## 최적화한 사항

### 🌕 Frontend

### 🌑 Backend

#### 1. 컴포넌트 단위 API 개발을 통한 페이지 약 2.3배 최적화
> [PR #77](https://github.com/CLOVIDER/kic-backend/pull/77)

#### 2. Scheduler를 통한 서비스 이미지 처리 간 S3 호출 의존성 제거
> [PR #59](https://github.com/CLOVIDER/kic-backend/pull/59)

#### 3. Redis 캐싱을 통한 현재 진행 중인 모집 정보, 사용자 정보 조회 속도 개선 및 최적화
> [#186](https://github.com/CLOVIDER/kic-backend/issues/186)

#### 4. 비동기 통신을 활용한 관리자 모집 결과 이메일 전송(SMTP) 기능 사용자 경험 개선
> [PR #49](https://github.com/CLOVIDER/kic-backend/pull/49)

#### 5. 점진적인 공지사항 조회수 중복 처리 방지 로직 개선 (쿠키 -> redis)
> [PR #59](https://github.com/CLOVIDER/kic-backend/pull/59)
> [PR #141](https://github.com/CLOVIDER/kic-backend/pull/141)

### 🌗 Infra

#### 1. Java 애플리케이션 - Gradle JIB 빌드를 통한 빌드 시간 77% 단축
<img width="568" alt="image" src="https://github.com/user-attachments/assets/2a5ccd94-235c-4d41-9dd3-6b6e26fbc218">

#### 2. Java 애플리케이션 - JRE 이미지 빌드를 통한 보안성 강화 및 이미지 2.5배 경량화
<img width="568" alt="image" src="https://github.com/user-attachments/assets/3c4ff618-4463-451f-bba4-66adcc309d2e">

> [PR #120](https://github.com/CLOVIDER/kic-backend/pull/120)

#### 3. Github Self-hosted Runner를 통한 Private Workflow 이용 제한 해결
<img width="548" alt="image" src="https://github.com/user-attachments/assets/bba3bd28-10b1-4ea0-9f1f-db96f41c3ddf">


## 화면 구성

<!-- TODO: 화면 구성도 추가-->

## 개발 기간
### 프로젝트 진행기간 : 24.07.01 ~ 08.23

<table>
  <thead>
          <tr>
              <th>작업 기간</th>
              <th>프로세스 단계</th>
              <th>작업 내역</th>
              <th>산출물</th>
          </tr>
  </thead>
  <tbody>
  <tr>
    <td>24.07.01 ~ 07.14</td>
    <td>서비스 기획</td>
    <td>📌 요구사항 도출, 정의, 검토 </br>
        📌 프로젝트 목표 설정, 서비스 도메인 조사
    </td>
    <td>요구사항 정의서, WBS, 용어 사전</td>
  </tr>
  <tr>
    <td>24.07.12 ~ 07.21</td>
    <td>설계 단계</td>
    <td>📌 UI/UX 설계, 메뉴 구조도, 업무 흐름도 </br>
        📌 데이터베이스 설계, 테이블 명세서 </br>
        📌 인터페이스 설계, 시스템 아키텍처 설계 </br>
          기술 스택 선정
    </td>
    <td>
    화면 설계서, 메뉴 구조도, 업무 흐름도 </br> ERD, 테이블 명세서, 인터페이스 설계서 </br> 시스템 아키텍처, 소프트웨어 구성도
    </td>
  </tr>
  <tr>
    <td>24.07.22 ~ 08.16</td>
    <td>구현 단계</td>
    <td> 📌 공통 컴포넌트 설계 및 코드 개발, UI 설계 및 개발 </br>
         📌 Request, Response DTO 설계 및 개발 </br>
         📌 Restful API 개발, Infra 구축
    </td>
    <td>프로젝트 코드, 도커 이미지, 인프라 환경</td>
  </tr>
  <tr>
    <td>24.08.11 ~ 08.17</td>
    <td>테스트 단계</td>
    <td> 📌 단위 테스트 </br>
         📌 브라우저 속도 테스트, Lighthouse 분석 </br>
         JMeter 성능 테스트
    </td>
    <td>통합 테스트 보고서</td>
  </tr>
  <tr>
    <td>24.08.17 ~ 08.23</td>
    <td>종료</td>
    <td> 사용자 및 관리자 화면 데모 영상 </br>
         테스트 시나리오 작성 </br>
         📌 프로젝트 회고 진행 </br>
         📌 종료 보고서 작성 및 발표 준비
    </td>
    <td>회고록, 데모영상 </br>
      발표자료, 종료 보고서</td>
  </tr>
  </tbody>
</table>



## 🍀 팀 & 서비스 소개

|Team: Clovider|Service: KIC|
|------|------|
|<img width="170" height="170" src="https://github.com/user-attachments/assets/8f13196a-f069-4145-aed0-dbd0db0a0f15"/>|<img width="170" height="170" src="https://github.com/user-attachments/assets/2223d050-aadc-4f98-9a6e-d43ce1af39e4"/>|

## 🙌 팀원 소개

<p align="center">
<img width="400" alt="image" src="https://github.com/user-attachments/assets/080853a5-5ea7-4e4e-877b-c846374749f0">
<img width="400" alt="image" src="https://github.com/user-attachments/assets/273ed4a0-8c7a-40da-9d70-f55833e2e7e2">
</p>

|No|이름|역할|깃허브|
|------|---|---|---|
|1|김현겸|PM, BE|[kylo-dev](https://github.com/kylo-dev)|
|2|공예영|PL, FE|[yeyounging](https://github.com/yeyounging)|
|3|김성민|FE|[Collection50](https://github.com/Collection50)|
|4|서용준|FE|[mango0422](https://github.com/mango0422)|
|5|권민우|PL, BE|[MINUUUUUUUUUUUU](https://github.com/MINUUUUUUUUUUUU)|
|6|정준희|BE|[sungsil0624](https://github.com/sungsil0624)|
|7|정희찬|BE, Infra|[anselmo228](https://github.com/anselmo228)|
|8|이주애|BE, Infra|[leejuae](https://github.com/leejuae)|
|9|김관일|BE|[KIM-KWAN-IL](https://github.com/KIM-KWAN-IL)|

## ⚙️ 기술 스택

<img width="410" alt="image" src="https://github.com/user-attachments/assets/3c9a3630-12e4-4ea5-8720-e1e2ba7847d8">


