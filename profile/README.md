# Kids In Company

<!--배지-->
<!-- ![MIT License][license-shield] ![Repository Size][repository-size-shield] ![Issue Closed][issue-closed-shield] -->

<!--프로젝트 대문 이미지-->

<!--프로젝트 버튼-->
<!-- [![Readme in English][readme-eng-shield]][readme-eng-url] [![View Demo][view-demo-shield]][view-demo-url] [![Report bug][report-bug-shield]][report-bug-url] [![Request feature][request-feature-shield]][request-feature-url] -->

<!--목차-->
# Table of Contents
- [[1] About the Project](#1-about-the-project)
  - [Features](#features)
  - [Technologies](#technologies)
- [[2] Getting Started](#2-getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Configuration](#configuration)
- [[3] Usage](#3-usage)
- [[4] Contribution](#4-contribution)
- [[5] Acknowledgement](#5-acknowledgement)
- [[6] Contact](#6-contact)
- [[7] License](#7-license)



# [1] About the Project

이 프로젝트는 신청 및 추첨 과정을 자동화하여 사용자가 쉽게 신청하고 결과를 확인할 수 있는 종합적인 웹 솔루션을 제공합니다. 투명한 프로세스와 사용자 친화적 인터페이스를 통해 효율적이고 공정한 신청 및 추첨 환경을 조성합니다.
복잡하고 불편한 신청 및 추첨 과정을 개선하고자 본 프로젝트를 시작하게 되었습니다. 사용자의 편의성을 높이고 관리자 업무의 효율성을 극대화하기 위해 자동화된 시스템을 제공합니다.

## Features
*강조하고 싶은 **주요 기능**이나 **차별성 있는 특징**을 적으세요.*
- **사용자 친화적** 웹 인터페이스 제공: 직관적이고 사용하기 쉬운 웹 인터페이스로 누구나 쉽게 접근하고 이용할 수 있습니다.
- 쉽고 간편한 신청 및 내역 조회: 간편한 신청 절차와 더불어 신청 내역을 손쉽게 조회할 수 있어 **사용자 편의성을 극대화**합니다.
- 프로세스 투명성: 신청부터 추첨까지의 모든 과정을 **자동화**하여 **투명성**을 확보하고 신뢰할 수 있는 시스템을 제공합니다.
- 실시간 경쟁률 및 추첨 결과 조회: **실시간으로 경쟁률을 확인**하고 추첨 결과를 조회할 수 있어 사용자에게 투명한 정보를 제공합니다.
- 자유로운 가중치 선택을 통한 폼 등록: **다양한 가중치 선택 옵션**을 제공하여 사용자 맞춤형 신청이 가능합니다.
- 추첨 관리 기능: 신청자 리스트, 신청 현황, 결과 조회 등을 통해 효율적으로 추첨을 관리할 수 있습니다.
- 서류 승인 전산화: 모든 서류 승인 과정을 전산화하여 관리자의 업무 효율성을 높입니다.
- 관리자 업무 효율성: 자동화된 시스템을 통해 관리자의 업무를 줄이고, 더 중요한 업무에 집중할 수 있도록 도와줍니다.

## Technologies

- [Gradle](https://gradle.org/) X.X.X
- [MySQL](https://www.mysql.com/) X.X
- [Spring](https://spring.io/) X.X.X



# [2] Getting Started
*만약 운영체제에 따라 프로그램을 다르게 동작시켜야한다면, 운영체제별로 동작 방법을 설명하세요*

## Prerequisites
*프로젝트를 동작시키기 위해 필요한 소프트웨어와 라이브러리를 나열하고 어떻게 다운받을 수 있는지 설명하세요.*

- [OpenWeather API key](https://openweathermap.org/) (무료)
- npm
```bash
npm install npm@latest -g
```

## Installation
*어떻게 이 프로젝트의 소스코드를 다운받을 수 있는지 설명하세요.*
1. Repository 클론
```bash
git clone https://github.com/your-username/project-repository
```
2. NPM packages 설치
```bash
npm install
```

## Configuration
*코드의 어느 부분을 채우거나 수정해야하는지 설명하세요.*
- `config.js`에 Openweather API key를 입력
```bash
const API_KEY = "<Your API key>";
```



# [3] Usage
***스크린샷, 코드** 등을 통해 **사용 방법**과 **사용 예제**를 보여주세요. 사용 예제별로 h2 헤더로 나누어 설명할 수 있습니다.*

![usage](img/usage.png)

```java
// 몇 개의 API 사용 예제를 코드와 함께 보여주세요.
```



# [4] Contribution
기여해주신 모든 분들께 대단히 감사드립니다.[`contributing guide`][contribution-url]를 참고해주세요.
이 프로젝트의 기여하신 분들을 소개합니다! 🙆‍♀️
*이모티콘 쓰는 것을 좋아한다면, 버그 수정에 🐞, 아이디어 제공에 💡, 새로운 기능 구현에 ✨를 사용할 수 있습니다.*
- 🐞 [dev-ujin](https://github.com/dev-ujin): 메인페이지 버그 수정



# [5] Acknowledgement
***유사한 프로젝트의 레포지토리** 혹은 **블로그 포스트** 등 프로젝트 구현에 영감을 준 출처에 대해 링크를 나열하세요.*

- [Readme Template - Embedded Artistry](https://embeddedartistry.com/blog/2017/11/30/embedded-artistry-readme-template/)
- [How to write a kickass Readme - James.Scott](https://dev.to/scottydocs/how-to-write-a-kickass-readme-5af9)
- [Best-README-Template - othneildrew](https://github.com/othneildrew/Best-README-Template#prerequisites)
- [Img Shields](https://shields.io/)
- [Github Pages](https://pages.github.com/)



# [6] Contact
- 📧 dev.ujin518@gmail.com
- 📋 [https://dev-ujin.github.io/contact](https://dev-ujin.github.io/contact)



# [7] License
MIT 라이센스
라이센스에 대한 정보는 [`LICENSE`][license-url]에 있습니다.



<!--Url for Badges-->
[license-shield]: https://img.shields.io/github/license/dev-ujin/readme-template?labelColor=D8D8D8&color=04B4AE
[repository-size-shield]: https://img.shields.io/github/repo-size/dev-ujin/readme-template?labelColor=D8D8D8&color=BE81F7
[issue-closed-shield]: https://img.shields.io/github/issues-closed/dev-ujin/readme-template?labelColor=D8D8D8&color=FE9A2E

<!--Url for Buttons-->
[readme-eng-shield]: https://img.shields.io/badge/-readme%20in%20english-2E2E2E?style=for-the-badge
[view-demo-shield]: https://img.shields.io/badge/-%F0%9F%98%8E%20view%20demo-F3F781?style=for-the-badge
[view-demo-url]: https://dev-ujin.github.io
[report-bug-shield]: https://img.shields.io/badge/-%F0%9F%90%9E%20report%20bug-F5A9A9?style=for-the-badge
[report-bug-url]: https://github.com/dev-ujin/readme-template/issues
[request-feature-shield]: https://img.shields.io/badge/-%E2%9C%A8%20request%20feature-A9D0F5?style=for-the-badge
[request-feature-url]: https://github.com/dev-ujin/readme-template/issues

<!--URLS-->
[license-url]: LICENSE.md
[contribution-url]: CONTRIBUTION.md
[readme-eng-url]: ../README.md


