# Partial Prerendering

## 1. Static vs Dynamic Routes

일반적으로 전체 애플리케이션이나 특정 라우트에 대해 정적 렌더링과 동적 렌더링 중 하나를 선택해야 한다.

Next.js 에서는 데이터베이스 쿼리와 같은 동적 함수를 라우트에서 호출하면 해당 라우트 전체가 동적으로 바뀐다.

하지만 대부분의 라우트는 완전히 정적이거나 동적이지 않다. 예를 들어 쇼핑몰 사이트는 제품 정보 페이지의 기본적인 내용은 정적으로 렌더링하고 사용자의 장바구니와 추천 제품은 동적으로 렌더링하여 개인화된 콘텐츠를 보여준다.

## 2. What is Partial Prerendering?

Next.js 14 버전에서는 **Partial Prerendering(PPR)** 이라는 새로운 렌더링 방식을 도입했다. 하나의 라우트에서 정적 렌더링과 동적 렌더링을 모두 활용할 수 있다.

![thinking-in-ppr](https://github.com/user-attachments/assets/ba3eda87-4fa1-4219-b705-5b6d75d6021c)

사용자가 페이지를 방문하면 다음과 같이 동작한다.

- 네비게이션 바와 제품 정보 등 기본적인 내용을 정적으로 로드한다.
- 장바구니나 추천 제품과 같이 동적으로 변경되는 부분은 별도로 로드한다.
- 동적 콘텐츠는 병렬로 로드하여 전체 페이지 로딩 시간을 최소화한다.

## 3. How does Partial Prerendering work?

Partial Prerendering 은 Suspense 를 활용하여 데이터 로딩과 같은 특정 조건이 충족될 때까지 일부 컴포넌트의 렌더링을 지연시킨다.

Suspense 의 로딩 상태는 정적 콘텐츠와 함께 초기 HTML 에 포함된다. 빌드 시점(또는 재검증 시)에 정적 콘텐츠는 미리 렌더링되어 기본 페이지 구조를 생성한다. 동적 콘텐츠는 사용자가 페이지를 요청할 때까지 렌더링을 미룬다.

## 4. Implementing Partial Prerendering

1. `next.config.mjs` 파일에 다음과 같이 설정을 추가한다.

```js
const nextConfig = {
  experimental: {
    ppr: 'incremental',
  },
};
```

2. 대시보드 레이아웃에 PPR 을 활성화한다.

```js
export const experimental_ppr = true;
```

PPR 의 가장 큰 장점은 코드를 크게 변경하지 않고도 사용할 수 있다는 점이다.

동적으로 변경되는 부분을 Suspense 로 감싸면 Next.js 가 자동으로 정적인 콘텐츠와 동적인 콘텐츠를 구분하여 처리한다.

> [Quiz](./quiz.md)
