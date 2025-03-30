# Next.js App Router Course

A dashboard project built following the official [Next.js App Router Course](https://nextjs.org/learn/dashboard-app).

> 🌐 [View Dashboard](https://learn-nextjs-eight-mocha.vercel.app)

## 1. Getting Started [🔗](https://nextjs.org/learn/dashboard-app/getting-started)

## 2. CSS Styling [🔗](https://nextjs.org/learn/dashboard-app/css-styling)

> [Quiz](./docs/quiz/chaptet02.md)

## 3. Optimizing Fonts and Images [🔗](https://nextjs.org/learn/dashboard-app/optimizing-fonts-images)

### 3-1. `<Image>` Component

이미지 로딩 시 레이아웃 시프트를 방지합니다.

- `width`, `height` 속성을 필수값으로 사용합니다.
- 이미지를 로드하기 전에 이미지가 차지할 공간을 미리 계산합니다.
- 이미지 크기에 맞는 `placeholder` 를 생성합니다.

작은 화면의 기기에서 큰 이미지를 로드하지 않도록 크기를 조절합니다.

- 여러 크기의 이미지를 생성하고 브라우저가 적절한 크기의 이미지를 선택할 수 있도록 `srcset` 속성을 사용합니다.
- 브라우저는 뷰포트 크기와 디바이스 픽셀 비율에 따라 가장 적합한 이미지를 선택합니다.

지연 로딩을 적용합니다. (화면에 이미지가 보일 때만 불러옵니다.)

WebP, AVIF 등 최신 이미지 포맷을 지원하는 브라우저에서는 해당 포맷으로 이미지를 제공합니다.

> [Quiz](./docs/quiz/chapter03.md)

## 4. Creating Layouts and Pages [🔗](https://nextjs.org/learn/dashboard-app/creating-layouts-and-pages)

### 4-1. Creating the dashboard layout

다른 페이지로 이동할 때 레이아웃은 그대로 유지하고 페이지의 내용만 업데이트합니다. 이를 [부분 렌더링](https://nextjs.org/docs/app/building-your-application/routing/linking-and-navigating#4-partial-rendering) 이라고 합니다.

## 5. Navigating Between Pages [🔗](https://nextjs.org/learn/dashboard-app/navigating-between-pages)

### 5-1. Automatic code-splitting and prefetching

서버 컴포넌트를 사용하면 애플리케이션을 라우트 세그먼트별로 코드 스플리팅합니다.

- 각 페이지는 독립적으로 동작합니다. 특정 페이지에서 오류가 발생해도 애플리케이션의 다른 페이지는 정상적으로 작동합니다.
- 클라이언트에서는 라우트 세그먼트를 미리 가져와 캐시합니다.

Next.js 는 Router Cache 라는 메모리 내 클라이언트 측 캐시를 가지고 있습니다.

- Router Cache 는 레이아웃, 로딩 상태, 페이지로 구분된 라우트 세그먼트의 RSC 페이로드를 저장합니다.
- 브라우저의 메모리에 임시로 저장되는 캐시 저장소입니다.
- 페이지 이동 시 캐시를 최대한 재사용하여 서버 요청을 줄이고 데이터 전송량을 감소하여 성능을 향상할 수 있습니다.
- 로딩 상태도 캐시되어 즉각적인 페이지 전환에 재사용됩니다.
- `revalidate` 옵션을 통해 페이지 세그먼트의 캐싱을 제어할 수 있습니다.

`<Link>` 컴포넌트는 뷰포트에 나타날 때 자동으로 프리패칭을 시작합니다.

- 프로덕션 환경에서만 프리패칭이 활성화됩니다.
- 정적 라우트의 경우 모든 리소스를 프리패칭합니다.
- 동적 라우트의 경우 `loading.js` 파일과 함께 레이아웃까지 프리패칭합니다.

```
app/
├── dashboard/
│   ├── layout.js
│   ├── loading.js <- 첫 번째 loading.js
│   ├── page.js
│   └── settings/
│       ├── loading.js
│       └── page.js
```

기본 프리패칭 범위는 다음과 같습니다.

- `<Link>` 컴포넌트가 `/dashboard/settings` 로 향하는 경우 첫 번째 `loading.js` 지점까지만 프리패칭합니다.
- 프리패칭한 데이터는 세션 동안만 유지되며 페이지를 새로고침하면 초기화됩니다.

> [Quiz](./docs/quiz/chapter05.md)

## 6. Setting Up Your Database [🔗](https://nextjs.org/learn/dashboard-app/setting-up-your-database)

> [Quiz](./docs/quiz/chapter06.md)

## 7. Fetching Data [🔗](https://nextjs.org/learn/dashboard-app/fetching-data)

### 7-1. Choosing how to fetch data

#### 7-1-1. API Layer

- 서드파티 서비스에서 제공하는 API 를 사용할 때 적용할 수 있습니다.
- 클라이언트에게 DB 정보를 유출하지 않도록 보호가 필요할 때 사용합니다.

#### 7-1-2. Database Query

- API 엔드포인트 생성 시 DB 와 상호 작용할 수 있습니다.
- React Server Components 를 사용할 때 직접 데이터베이스 쿼리를 할 수 있습니다.

#### 7-1-3. React Server Components

- JavaScript Promise 를 네이티브로 지원해서 비동기 동작을 `useEffect` 또는 `useState` 없이 사용합니다.
- 데이터 패칭 로직을 서버에서 실행하고 결과만 클라이언트로 전송합니다.
- API 레이어 없이 직접 데이터베이스 쿼리를 할 수 있습니다.

### 7-2. What are request waterfalls?

워터폴이란 이전 요청의 완료 여부에 따라 달라지는 일련의 네트워크 요청을 의미합니다. 각 요청은 이전 요청이 데이터를 반환한 후에만 시작할 수 있습니다.

![sequential-parallel-data-fetching](https://github.com/user-attachments/assets/0ac4f5f2-7582-4957-9a6c-966ea3fcc401)

#### 7-2-1. Waterfall Issue

이전 요청이 완료된 후에만 다음 요청을 시작할 수 있어서 성능 저하의 원인이 될 수 있습니다.

#### 7-2-2. Solutions

> Promise.all / Promise.allSettled

- 모든 데이터 요청을 동시에 시작합니다.
- 네이티브 JavaScript 패턴을 사용해서 요청 시간을 단축할 수 있습니다.

> [Quiz](./docs/quiz/chapter07.md)
