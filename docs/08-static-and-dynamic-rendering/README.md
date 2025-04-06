# Static and Dynamic Rendering

## 1. Static Rendering

서버에서 빌드 시점이나 데이터 재검증 시에 데이터를 패칭하고 렌더링한다.

사용자가 애플리케이션에 접근하면 캐시된 데이터를 제공한다.

### 1-1. Benefits of Static Rendering

#### 1-1-1. Faster Websites

Vercel 과 같은 플랫폼에서 배포하면 캐시된 콘텐츠를 전역적으로 제공할 수 있다.

#### 1-1-2. Reduced Server Load

콘텐츠가 캐시되어 각 요청마다 동적으로 데이터를 패칭하지 않아도 된다.

#### 1-1-3. SEO

검색 엔진 크롤러가 미리 렌더한 콘텐츠를 쉽게 인덱싱할 수 있다.

> 정적 렌더링은 데이터가 없거나 사용자 간에 공유되는 데이터가 있는 UI 에서 유용하다. (ex. 정적 블로그 포스트, 제품 페이지 등)

## 2. Dynamic Rendering

각 사용자에 대해 요청 시점(사용자가 페이지를 방문할 때)에 서버에서 콘텐츠를 렌더링한다.

### 2-1. Benefits of Dynamic Rendering

#### 2-1-1. Real-Time Data

실시간으로 데이터를 표시할 수 있다.

#### 2-1-2. User-Specific Content

- 사용자별 콘텐츠를 제공하기 용이하다. (ex. 대시보드, 사용자 프로필 등)

#### 2-1-3. Request Time Information

- 쿠키나 URL 서치 파라미터와 같은 요청 시점 정보에 접근할 수 있다.

**단점**

- 애플리케이션의 속도가 가장 느린 데이터 가져오기에 의해 제한된다.
- 모든 데이터가 준비될 때까지 UI 가 차단될 수 있다.
