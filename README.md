# react-2

# 201930413 박찬우

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
