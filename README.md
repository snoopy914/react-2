# react-2

# 201930413 박찬우
### 4주차

git checkout vs git switch 차이
그런데 왜 checkout은 그대로 남아있나?
-> 파일 복원 등 이미 commit된 파일을조작할 수 있기 때문입니다.
-> 특히 git checkout [커밋 해시] 명령으로 특정 commit으로 이동할 수 있습니다.
새 brach를 만드는 명령 3가지

switch와 checkout은 branch를 만들면서 곧바로 이동한다.

# 1. Creating a page(페이지 만들기)
- Next.js는 파일 시스템 기반 라우팅을 사용하기 때문에 폴더와 파일을 사용하여 경로를 정의할 수 있습니다.
- 이번 장에서는 레이아웃과 페이지를 만들고 서로 연결하는 방법을 설명합니다.
- page는 특정 경로에서 렌더링되는 ui입니다.
- page를 생성하려면 app 디렉터리에 page파이을 추가하고, React 컴포넌트를 
Next.js는 파일 시스템 기반

layout은 여러 페이지에 공유 되는 ui
layout은 네비게이션에서 state 및 상호작용을 융지하며, 다시 렌더링 되지 안흔ㄴ다.
layout 파일에서 react 컴포넌트의 default export를 사용하여 layout을 정의할 수 있다.
layout 컴포넌트는 page 또는 다른 layout이 될 수 있는 children prop을 허용해야 한다.
children은 컴포넌트 안에 감싸진 요소(컴포넌트)를 의미한다.

# Creating a nested route(중첩 라우트 만들기)
- 중첩 라우트는 다중 url 세그먼트로 구성된 라우트
- 예를 들어 /blog/[slug]경로는 세 개의 세그먼트로 구성된다.
- / (Root Segment)
- blog (Segment)
- [slug] (Leaf Segment)

- [Next.js에서]
- 폴더는 url 세그먼트에 매핑되는 경로 세그먼트로 정리되는데 사용한다.

- 



### 3주차
# 용어 정의
- 이 장부터 이후에 사용될 몇가지 용어에 대한 설명입니다.
- 원문에는 ROUTE라는 단어가 자주 등장하고, 사전적 의미로는 경로입니다.
- 그런데 PATH도 경로로 번역하기 때문에의 구별을 위해 대부분 ROUTING(라우팅)으로 번역했습니다.

- directory와 folder는 특별한 구분 없이 나옵니다.
- 최상위 폴더의 경우 directory로 하위 폴더는 folder로 쓰는 경우가 많지만 꼭 그렇지는 않습니다.
- directory와 folder는 os에 따라 구부되는 용어이기 때문에 같은 의미로 이해하면 됩니다.
- segment는 routing과 관련이 있는 direcctory의 별칭 정도로 이해하면 됩니다.

# Open graph protocol
- 웹사이트나 페이스북, 인스타그램, x(트위터), 카카오톡 등에 링크를 전달할 떄 미리보기를 생성하는 프로토콜 입니다.
- Open graph Protocol이 대표적인 프로토콜
- 페이스북이 주도하는 표준화 규칙으로 대부분의 sns 플랫폼에서활용되고 있다.

# 서버 실행 전후
- .next 디렉토리가 생성.
- next.js에서 .next 디렉토리는 빌드 아웃풋과 실행에 필요한 캐시 중간 산출물을 저장하는 폴더.
- 즉. enxt dev, next build, next start 실행할 때 내부적으로 필요한 작업 디렉토리.

### 2주차
자바스크립트

create-react-app
npx create-next-app@latest

pnpm i next@latest react@latest react-dom@latest
Strict: next. js의 기본 esLint 구성과 더욱 엄격한 Core Web Vitals 규칙 세트를 포함 합니다.
- base : next.js의 기본 eslint 구성을 포함합니다.
- cancel : 구성을 건너뜁니다. 사용자 지정 eslnt 구성을 설정하려면 이 옵션을 확인해야한다.

- ESLint가 설정되면 빌드할 때마다 매번 자동으로 실행된다. 오류가 발생하면 빌드는 실패한다.

7. import 및 모듈의 절대 경로 별칭 설정
 
  - next.js에는 tsconfig.json 및 jsconfig.json 파일의 paths 및 baseUrl 옵션에 대한 지원을 내장하고 있다.
  - 이 옵션을 사용하면 프로젝트 디렉터리를 절대 경로로 별칭 하여 모듈을 더쉽고 깔끔하게 가져올 수 있다.
 
    ```
    // before
    import { Button } from '../../../components/button'

    // After
    import { Button } from '@/components/button'
    ```
  - 별칭으로 import를 구성하려면 tsconfig.json 또는 jsconfig.json 파일의 baseUrl에 구성 옵션을 추가하세요.

자동 생성되는 항목
- package.json 파일에 scripts 자동 추가 / public 디렉토리
- typescript 사용(선택) : tsconfig.json 파일 생성
- eslint 설정 (선택) : eslintrc.json 대신 eslint.config.mjs 파일 생성
- tailwind css 사용 (선택)
- src 디렉토리 사용 (선택)
- App Router(선택), app/layout.tsx 파일 및 app/page.tsx
- Turbopack 사용(선택)
- import alias 사용 (선택) : tsconfig.json에 paths 자동 생성.
- 수동으로 프로젝트를 생성할 떄 추가적으로 해야 하는 작업을 자동으로 처리해 줍니다.

Core web Vitals
- Lcp : 뷰포트 내에서 가장 큰페이지 요소(큰 텍스트 블록, 이미지 또는 비디오)를 표시하는데 걸리는 시간.
- Fid : 사용자가 웹페이지와 상호작용을 시도하는 첫 번째 순간부터 웹페이지가 응답하는 시간.
- Cls : 방문자에게 콘텐츠가 얼마나 불안정한 지 측정하는 값.


.eslintrc.json vs eslint.config.mjs

npx create-next-app@latest

pnpm은 Performant(효율적인) NPM의 약자로 고성능 Node 패키지 매니저이다.
pnpm create next-app@latest


### 1주차
OT
