# Fetching Data

## 1. Choosing how to fetch data

### 1-1. API Layer

- 서드파티 서비스에서 제공하는 API 를 사용할 때 적용할 수 있다.
- 클라이언트에게 DB 정보를 유출하지 않도록 보호가 필요할 때 사용한다.

### 1-2. Database Query

- API 엔드포인트 생성 시 DB 와 상호 작용할 수 있다.
- React Server Components 를 사용할 때 직접 데이터베이스 쿼리를 할 수 있다.

### 1-3. React Server Components

- JavaScript Promise 를 네이티브로 지원해서 비동기 동작을 `useEffect` 또는 `useState` 없이 사용한다.
- 데이터 패칭 로직을 서버에서 실행하고 결과만 클라이언트로 전송한다.
- API 레이어 없이 직접 데이터베이스 쿼리를 할 수 있다.

## 2. What are request waterfalls?

워터폴이란 이전 요청의 완료 여부에 따라 달라지는 일련의 네트워크 요청을 의미한다. 각 요청은 이전 요청이 데이터를 반환한 후에만 시작할 수 있다.

![sequential-parallel-data-fetching](https://github.com/user-attachments/assets/0ac4f5f2-7582-4957-9a6c-966ea3fcc401)

### 2-1. Waterfall Issue

이전 요청이 완료된 후에만 다음 요청을 시작할 수 있어서 성능 저하의 원인이 될 수 있다.

### 2-2. Solutions

> Promise.all / Promise.allSettled

- 모든 데이터 요청을 동시에 시작한다.
- 네이티브 JavaScript 패턴을 사용해서 요청 시간을 단축할 수 있다.

> [Quiz](./quiz.md)
