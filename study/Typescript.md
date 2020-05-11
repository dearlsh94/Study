# Typescript

- javascript의 확장 프로그래밍 언어

- 확장자로 `.ts` 사용

- 구글의 사내 표준 언어로 승인 됨

  

## 특징

- 정적 타입 지원 - 타입 어노테이션
  - 컴파일 단계에서 오류 확인 가능

```
function sum(a: number, b: number) {
  return a + b;
}
```

- IDE 인텔리센스 지원
- babel 없이도 ES6 기능 지원 가능
- Typescript 컴파일러를 통해 javascript로 변환된다.
- 지속적 기능 업데이트로 새로운 기능 사용에 유용



## 컴파일러 설치

- 전역으로 Typescript 설치 및 확인

```
$ npm i -g typescript
$ tsc -v
```

> tsc가 .ts to .js 로 트랜스파일링 함



## 코드 컴파일

- Typescript 파일을 javascript 파일로 변환

```
$ tsc {fileName}.ts
```



## 인터페이스 (Intefaces)

- Inteface를 생성하여 타입 어노테이션으로 사용 가능

```
interface Person {
    firstName: string;
    lastName: string;
}

function greeter(person: Person) {
    return "Hello, " + person.firstName + " " + person.lastName;
}
```



## 클래스 (Classes)

- 



## 참고 

- [TypeScript의 소개와 개발 환경 구축](https://poiemaweb.com/typescript-introduction)

- [TypeScript-Handbook 한글 문서](https://typescript-kr.github.io/)