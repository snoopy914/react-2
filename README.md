# react-2

# 201930413 박찬우

### 6주차
Client-side transitions(클라이언트 측 전환)
일반적으로 서버 렌더링 페이지로 이동하면 전체 페이지가 로드된다. -> 이로 인해 state가 삭제되고, 스크롤 위치가 재설정되며, 상호작용이 차단된다.
next.js는 <link> 컴포넌트를 사용하는 클라이언트 측 전환을 통해 이를 방지한다. 페이지를 다시 로딩하는 대신 다음과 같은 방법으로 콘텐츠를 동적으로 업데이트된다.
공유 레이아웃과 ui를 유지한다.
현재 페이지를 미리 가져온(prefetching) 로딩 상태 또는 사용 가능한 경우 새 페이지로 바꾼다.
클라이언트 측 전환은 서버에서 렌더링된 앱을 클라이언트에서 렌더링된 앱처럼 느껴지게 하는 요소.
또한 프리페칭 및 스트리밍.

1. 1절 네비게이션 작동방식 실습
   앞에서 배운 내용을 다시 한번 확인.
   디렉토리 구조는 다음과 같습니다.
   디렉토리 이름(blog)은 다른 것으로 해도 됩니다.

   Root Page를 간다히 작성합니다.
   blog 디렉토리를 마들고, 간단히 page와 로딩 스켈톤을 만듭니다.
   rooutLayout에 Link 컴포넌트를 이용해서 blog의 내비게이션을 만든다.
   이대로는 로딩 스켈톤의 동작을 확인할 수 없으니 blog page에 time delay를 줍니다.
   문서에는 rootLaayout에 a 태그를 이용해서 blog의 네비게이션
을 만드는 예제가 있다.


# generateSaticParams를 사용하는 경우 실습
문서의 예제처럼 generateStaticParams를 사용하는 경우의 예제.
실습할 디렉토리 구조는 다음과 같다.
blog2 디렉토리를 복사해서 사용하면 실습은 빠르게 진행할 수 있다.
테스트가 편하게 blog3의 메뉴를 만든ㄷ.
이러헥 코딩을 하면 리스트에서 링크를 통해 슬러그에 접근하면 오류가 나지 않지만, 직접 링크를 통해 접근하면 오류가 발생한다.

await이 없어도 async를 붙여 두는 이유
Next.js 13+의 App router에서 page.tsx 같은 Server Component는 비동기 렌더링을 전제로 하고 있다.
즉, page.tsx 안에서 데이터를 fetch하는 경우가 많기 때문에 async를 기본으로 붙여도 전혀 문제가 없다.
1. 일관성 유지 : 같은 프로젝트 안에서 어떤 페이지는 async, 어떤 페이지는 일반 function이면 혼란스러울 수 있다. -> next.js 공식 문서도 대부분 async function으로 예시를 작성한다.
2. 확장성 : 지금은 더미 데이터(posts.find(...))를 쓰지만, 나중에 DB나 API에서 데이터를 가져올 때 await fetch(...) 같은 코드가 들어갈 수 있기 때문에, 미리 async를 붙여 두면 수정할 필요가 없다.
3. React Server Component 호환성 : Server Component는 Promise를 반환할 수 있어야 하고, Next.js는 내부적으로 async 함수 패턴에 맞춰 최적화된 렌더링 파이프라인을 갖고 있어서 async가 붙어 있어도 불필요한 오버헤드가 거의 없다.
   

### 5주차

searchParams란
URL의 쿼리 문자열을 읽는 방법입니다.
왜 동적 렌더링이 되는가.
next.js에서 페이지는 크게 정적똔느 동적으로 렌더링할 수 있다.
searchparams는 요청이 들어와야만 값을 알 수 있기 때문에 next.js는 이 페이지를 정적으로 미리 생성할 수 없고, 요청이 올 때마다 새로 렌더링해야한다.
따라서 해당 페잊는 자동으로 동적 렌더링을 처리 된다.
즉 searchParams를 사용하는 순간 next.js는 이 페이지는 요청이 들어와야 동작하네 -> 그럼 정적으로 미리 마들 수 없겠다 라고  판단한다.

Linking between pages(페이지 간 연결)
<Link> 컴포넌트를 사용하여 경로 사이를 탐색 할 수 있다.
<Link>는 HTML <a> 태그를 확장하여 prefetching 및 client-side navigation 기능을 제공하는 next.js의 기본제공 컴포넌트입니다.
prefetching은 사용자가 해당 경로로 이동하기 전에 백그라운드에서 해당 경로를 loading 하는 프로세스이다.
예를 들어, 블로그 글 목록을 생성하려면 enxt/link에서 <Link>를 가져와서 컴포넌트에 href prop을 전달합니다.

Next.js에서 경로는 기본적으로 섭에서 렌더링.
즉, 클라이언트는 새 경로를 표시하기 전에 서버의 응답을 기다려야 하는 경우가 많다.
next.js에는 prefetching, streaming, 그리고 client-side transitions(클라이언트 사이드 전환) 기능이 기본 제공되어 네비게이션 속도가 빠르고 반응성이 뛰어납니다.
# 자세한 내용은 다음 절에서 설명한다.

이번 장에서는 Next.js에서 네비게이션이 작동하는 방식, 동적 라우트와 느린 네트워크에 맞게 네비게이션을 최적화하는 방법을 설명합니다.

Server Rendering(서버 렌더링)
서버 렌더링에는 발생 시점에 따라 두 가지 유형이 있다.
정적 렌더링(또는 사전 렌더링)은 빌드 시점이나 재검증 중에 발생하며, 결과는 캐시(CACHE)된다.
동적 렌더링은 클라이언트 요청에 대한 응답으로 요청 시점에 발생한다.

서버 렌더링의 단점은 클라이언트가 새 경로를 표시하기 전에 서버의 응답을 기다려야 한다는 것.
NEXT.JS는 사용자가 방문할 가능성이 높은 경로를 미리 가져 오고, 클라이언트 측 전환을 수행하여 지연 문제를 해결한다.

프리페칭은 사용자가 해당 경로로 이동하기 전에 백그라운드에서 해당 경로를 로드하는 프로세스
사용자가 링크를 클릭하기 전에 다음 경로를 렌더링하는 데 필요한 데이터가 클라이언트 측에 이미 준비되어 있기 때문에 애플리케이션에서 경로 간 이동이 즉각적으로 느껴진다.
NEXT.JS는 LINK 컴포넌트와 연결된 경로를 자동으로 사용자 뷰포트에 미리 가져옵니다.
A 태그를 사용하면 프리페칭을 하지 않습니다.

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
