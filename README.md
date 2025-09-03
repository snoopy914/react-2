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

- 7. import 및 모듈의 절대 경로 별칭 설정
 
  - next.js에는 tsconfig.json 및 jsconfig.json 파일의 paths 및 baseUrl 옵션에 대한 지원을 내장하고 있다.
  - 이 옵션을 사용하면 프로젝트 디렉터리를 절대 경로로 별칭 하여 모듈을 더쉽고 깔끔하게 가져올 수 있다.
 
    ```
    // before
    import { Button } from '../../../components/button'

    // After
    import { Button } from '@/components/button'
    ```
  - 별칭으로 import를 구성하려면 tsconfig.json 또는 jsconfig.json 파일의 baseUrl에 구성 옵션을 추가하세요.

### 1주차
OT
