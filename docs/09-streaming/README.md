# Streaming

## 1. What is streaming?

스트리밍은 라우트를 작은 단위로 나눈 후 데이터를 순차적으로 전송하는 방식이다.

## 2. What are the benefits of streaming?

- 데이터 로딩이 느려도 전체 페이지가 멈추지 않는다.
- 모든 데이터가 로드되기 전에도 페이지의 일부를 사용자에게 제공할 수 있다.
- 각 컴포넌트를 독립적인 단위로 처리할 수 있다.

## 3. How to implement streaming in Next.js?

- **페이지 단위**: `loading.tsx` 파일 사용한다. (`<Suspense>` 자동 생성)
- **컴포넌트 단위**: `<Suspense>` 를 직접 사용하여 제어한다.

## 4. What are Route Groups?

- 괄호 `()` 를 사용하여 관련 파일을 그룹화할 수 있다.
- URL 경로에는 영향을 주지 않는다.
- `/dashboard/(overview)/page.tsx` 는 `/dashboard` 로 접근할 수 있다.
- 특정 페이지에만 로딩 상태를 적용하거나 애플리케이션을 섹션별로 나눌 때 유용하다.

## 5. Where to place your Suspense boundaries?

일반적으로 데이터 패칭을 관련 컴포넌트에서 직접 처리하고 해당 컴포넌트를 Suspense 로 감싸는 것을 권장한다.
