# 📌 Kids In Company - 사내 어린이집 공정한 추첨 서비스

<img width="650" src="https://github.com/user-attachments/assets/39fd046f-86a1-489b-95be-17ea968277b6"/>

> ### WEB URL: [키즈인컴퍼니 사이트](http://kidsincompany.shop/)
> ### [데모 영상](https://www.youtube.com/watch?v=2VDcmHRQTiI&feature=youtu.be)
> ### [FE Project](https://github.com/CLOVIDER/FE) </br>
> ### [BE Project](https://github.com/CLOVIDER/BE)
> 
> 작성자: 김현겸

<a href="https://hits.seeyoufarm.com"><img src="https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fgithub.com%2FCLOVIDER&count_bg=%2379C83D&title_bg=%23555555&icon=&icon_color=%23E7E7E7&title=hits&edge_flat=false"/>


### 📌실행 방법(로컬)
[FE & BE 로컬환경 실행 방법](https://github.com/CLOVIDER/.github/blob/main/profile/INSTALL.md)

### 📌배포 환경
[KIC-쿠버네티스 환경](https://github.com/CLOVIDER/kic-k8s/blob/main/README.md)

## 목차

* [프로젝트 소개](#프로젝트-소개)
* [핵심 기능](#핵심-기능)
* [실행 방법](#실행-방법)
* [ERD](#ERD)
* [시스템 아키텍처](#시스템-아키텍처)
* [최적화한 사항](#최적화한-사항)
* [화면 구성](#화면-구성)
* [개발 기간](#개발-기간)
* [팀 & 서비스 소개](#팀-&-서비스-소개)
* [팀원 소개](#팀원-소개)
* [기술 스택](#기술-스택)

## 🍀프로젝트 소개
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

<br/>

## 🍀핵심 기능

### ⭐ 사용자
- 1개의 신청서로 여러 개의 사내 어린이집 추첨 통합 신청
- 지원한 추첨 히스토리 조회, 당첨 확률 조회
- 공지사항 조회, 질의응답 작성
- 사내 어린이집 정보 조회

### ⭐ 관리자
- 관리자 대시보드 조회 (서비스 통계 정보)
- 사내 어린이집 모집 생성 및 신청현황 관리
- 사내 어린이집 추첨 진행 & 결과 관리
- Google SMTP를 통한 사용자 인증 및 추첨 결과 전송
- 공지사항, 질의응답 관리
- 사내 어린이집 정보 관리

## 🍀ERD

<img width="1100" alt="image" src="https://github.com/user-attachments/assets/7f5aadd5-654a-4449-82ee-167a29d43917">

## 🍀시스템 아키텍처

![image](https://github.com/user-attachments/assets/35de9337-e846-4131-87bf-7363e03d0a31)


## 🍀최적화한 사항

### 🌕 Frontend

#### 1. 지연로딩

- 번들 사이즈가 큰 Editor에 지연로딩을 적용해 브라우저에 전달되는 JS 크기를 최적화 했습니다.
- `unpacked size` `3.5MB -> 0MB`로 감소할 수 있었습니다.

```tsx
import dynamic from 'next/dynamic'
const BlockNoteEditor = dynamic(() => import('./BlockNoteEditor'), {
  ssr: false,
  loading: () => <LoadingSpinner />,
})
```

#### 2. 리렌더링 최적화

- `useCallback`, `useMemo`를 적극적으로 활용하여 불필요한 리렌더링을 방지했습니다.
- 성능이 좋지 않은 모바일 환경에서도 쾌적한 UX를 제공할 수 있는 환경을 구축했습니다.

```tsx
export default function useCreateQuery() {
  const searchParams = useSearchParams()

  const createQueryString = useCallback(
    (name: string, value: string) => {
      const params = new URLSearchParams(searchParams.toString())
      params.set(name, value)

      return params.toString()
    },
    [searchParams],
  )
  return createQueryString
}
```

#### 3. 트리셰이킹

- `package.json`에서 아래와 같이 적용하여 트리셰이킹을 적용했습니다.
- 불필요하게 다운로드되는 패키지를 삭제해, 브라우저에 전달되는 번들 사이즈를 25% 감소했습니다.

```json
  "sideEffects": false
```

#### 4. 폰트최적화

- NextJs를 활용한 최적화를 수행하여, JS 다운로드로 인한 UI blocking 현상을 최소화했습니다.
- `display: swap` 설정을 통해 유저는 폰트가 다운로드되는 동안 빈화면을 보고있지 않아도 됩니다.
- 웹 성능지표 중 FCP, TTI를 개선했습니다.

```ts
const Pretendard = localFont({
  src: './fonts/PretendardVariable.woff2',
  display: 'swap',
  weight: '45 920',
})
```

#### 5. 애니메이션 최적화

- `framer-motion`은 `transform` 기반의 애니메이션으로 reflow, repaint를 최소화합니다.
- GPU 가속을 사용하므로, 웹 성능을 저해하지 않고 고사양의 애니메이션을 사용했습니다.

```tsx
<motion.div
        initial={{ y: 0 }}
        animate={{ y: [0, -20, 0] }}
        transition={{
          duration: 2,
          ease: 'easeInOut',
          repeat: Infinity,
          repeatType: 'loop',
        }}
      >
```

#### 6. 동시성 렌더링

- `useDeferredValue`를 사용해 검색어를 입력하는 경우, UI 렌더링보다 검색어 입력이 우선적으로 처리되도록 했습니다.
- `ms` 명시적으로 사용하지 않는 디바운스를 사용해 불필요한 리렌더링을 최적화했습니다.

```ts
  const [searchInput, setSearchInput] = useState<string>('')
  const deferredSearchInput = useDeferredValue(searchInput)
```

### 🌑 Backend

#### 1. 컴포넌트 단위 API 개발을 통한 `페이지 약 2.3배 최적화`
> [PR #77](https://github.com/CLOVIDER/kic-backend/pull/77)

#### 2. Scheduler를 통한 서비스 이미지 처리 간 S3 호출 의존성 제거
> [PR #59](https://github.com/CLOVIDER/kic-backend/pull/59)

#### 3. `Redis 캐싱`을 통한 현재 진행 중인 모집 정보, 사용자 정보 조회 `속도 개선 및 최적화`
> [#186](https://github.com/CLOVIDER/kic-backend/issues/186)

#### 4. `비동기 통신`을 활용한 관리자 모집 결과 `이메일 전송(SMTP) 기능 사용자 경험 개선`
> [PR #49](https://github.com/CLOVIDER/kic-backend/pull/49)

#### 5. 점진적인 공지사항 `조회수 중복 처리 방지 로직 개선` (쿠키 -> redis)
> [PR #59](https://github.com/CLOVIDER/kic-backend/pull/59)
> [PR #141](https://github.com/CLOVIDER/kic-backend/pull/141)

#### 6. Aws Lambda를 통한 `다수 사용자의 가중치 기반 당첨 확률 알고리즘 처리` -> 속도 개선
<img width="500" src="https://github.com/user-attachments/assets/380a2840-76f2-490c-ad00-9019dacfedf6">

### 🌗 Infra

#### 1. Java 애플리케이션 - `Gradle JIB 빌드`를 통한 `빌드 시간 77% 단축`
<img width="568" alt="image" src="https://github.com/user-attachments/assets/2a5ccd94-235c-4d41-9dd3-6b6e26fbc218">

#### 2. Java 애플리케이션 - `JRE 이미지` 빌드를 통한 `보안성 강화 및 이미지 2.5배 경량화`
<img width="568" alt="image" src="https://github.com/user-attachments/assets/3c4ff618-4463-451f-bba4-66adcc309d2e">

> [PR #120](https://github.com/CLOVIDER/kic-backend/pull/120)

#### 3. Github Self-hosted Runner를 통한 `Private Workflow 이용 제한 해결`
<img width="548" alt="image" src="https://github.com/user-attachments/assets/bba3bd28-10b1-4ea0-9f1f-db96f41c3ddf">


## 🍀화면 구성


|사용자 랜딩 페이지|관리자 대시보드|
|---|---|
|<img width="600" alt="image" src="https://github.com/user-attachments/assets/efbab835-69a4-4e75-87df-e8c98b877d47">|<img width="600" alt="image" src="https://github.com/user-attachments/assets/9eae0997-088a-447a-82df-885411cf4bff">|
|어린이집 모집 신청 페이지 1|어린이집 모집 신청 페이지 2|
|<img width="600" src="https://github.com/user-attachments/assets/84b7d472-3068-4191-a9fc-b275ae3d74d3">|<img width="600" alt="image" src="https://github.com/user-attachments/assets/9ca82881-82ea-4c98-bcd7-a450e76ad46f">|
|모집 신청 내역 페이지|모집 당첨 확률 페이지|
|<img width="600" src="https://github.com/user-attachments/assets/04af4bcf-d647-45d8-aed7-fb334ae68913">|<img width="600" src="https://github.com/user-attachments/assets/b9457fe0-a04a-4b13-bce8-154a5347c9e1">|
|관리자 모집 설정 페이지 1|관리자 모집 설정 페이지 2|
|<img width="600" src="https://github.com/user-attachments/assets/f3093571-1155-41a3-bbfe-075555332f64">|<img width="600" src="https://github.com/user-attachments/assets/c6464963-f3ca-4a08-b672-f69493840b00">|
|관리자 신청 관리 페이지|관리자 추첨 관리 페이지|
|<img width="600" src="https://github.com/user-attachments/assets/0b8e66af-4aca-4902-afae-c4c98eee2f06">|<img width="600" src="https://github.com/user-attachments/assets/c6dca0c7-fd80-4745-af0c-102e8a7663ef">|
|공지사항 페이지|어린이집 정보 페이지|
|<img width="600" alt="image" src="https://github.com/user-attachments/assets/77f02207-9ad4-444b-914a-82b7743583db">|<img width="600" alt="image" src="https://github.com/user-attachments/assets/0113fbee-a114-4dbe-9ddd-a9cfd39839ea">|

## 🍀개발 기간
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



## 🍀팀 & 서비스 소개

|Team: Clovider|Service: KIC|
|------|------|
|<img width="170" height="170" src="https://github.com/user-attachments/assets/8f13196a-f069-4145-aed0-dbd0db0a0f15"/>|<img width="170" height="170" src="https://github.com/user-attachments/assets/2223d050-aadc-4f98-9a6e-d43ce1af39e4"/>|

## 🍀팀원 소개

### BE
| No.1 | No.2 | No.3 |
| :-: | :-: | :-: |
| <img src="https://avatars.githubusercontent.com/u/103489352?v=4" width="150" height="150"/> | <img src="https://avatars.githubusercontent.com/u/117968404?v=4" height="150"/> | <img src="https://avatars.githubusercontent.com/u/113875098?v=4" width="150" height="150"/> |
| **김현겸** | **권민우** | **정준희** |
| PM, BE | PL, BE | BE |
| [kylo-dev](https://github.com/kylo-dev) | [MINUUUUUUUUUUUU](https://github.com/MINUUUUUUUUUUUU) | [sungsil0624](https://github.com/sungsil0624) |

| No.4 | No.5 | No.6 |
| :-: | :-: | :-: |
| <img src="https://avatars.githubusercontent.com/u/24919880?v=4" width="150" height="150"/> | <img src="https://avatars.githubusercontent.com/u/51390115?v=4" height="150"/> | <img src="https://avatars.githubusercontent.com/u/118953934?v=4" width="150" height="150"/> |
| **정희찬** | **이주애** | **김관일** |
| BE, Infra | BE, Infra | BE |
| [anselmo228](https://github.com/anselmo228)|[leejuae](https://github.com/leejuae) | [KIM-KWAN-IL](https://github.com/KIM-KWAN-IL) |

### FE
| No.1 | No.2 | No.3 |
| :-: | :-: | :-: |
| <img src="https://avatars.githubusercontent.com/u/86355699?v=4?v=4" width="150" height="150"/> | <img src="https://avatars.githubusercontent.com/u/133792082?v=4" height="150"/> | <img src="https://avatars.githubusercontent.com/u/83891638?v=4" width="150" height="150"/> |
| **김성민** | **공예영** | **서용준** |
| PL, FE | FE | FE |
| [Collection50](https://github.com/Collection50) | [yeyounging](https://github.com/yeyounging) | [mango0422](https://github.com/mango0422) |

## 🍀기술 스택

<img width="410" alt="image" src="https://github.com/user-attachments/assets/3c9a3630-12e4-4ea5-8720-e1e2ba7847d8">


