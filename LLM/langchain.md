### langchain
LangChain(랭체인)은 대규모 언어 모델(LLM)을 활용한 애플리케이션 개발에 특화된 오픈소스 프레임워크
![image](https://github.com/user-attachments/assets/d602f1f8-6d00-47db-863f-543947438470)


• 개발: LangChain의 오픈소스 빌딩 블록, 컴포넌트, 서드파티 통합 등을 사용하여 애플리케이션을 빌드
  - langchain: 애플리케이션의 코그너티브 아키텍처를 구성하는 체인, 에이전트 및 검색 전략
  - langchain-core: 기본 추상화 및 LangChain 표현 언어
  - langchain-community: 서드파티 통합 (langchain-openai, langchain-anthropic 등)

• 테스트: LangSmith를 사용하여 체인을 검사, 모니터링 및 평가
  - LangSmith: LLM 애플리케이션을 디버깅, 테스트, 평가, 모니터링할 수 있는 개발자 플랫폼입니다.

• 배포: LangGraph Cloud를 사용하여 LangGraph 애플리케이션을 프로덕션에 바로 사용할 수 있는 API와 Assistant로 전환합니다.
  - LangGraph: 그래프의 에지와 노드로 단계를 모델링하여 LLM으로 견고한 “stateful” 멀티 액터 애플리케이션을 구축합니다.
  - LangServe: LangChain 체인을 REST API로 배포합니다.


- langchain 장점
  - 높은 유연성과 확장성
  - 활발한 오픈소스 커뮤니티의 지원
  - 다양한 산업에 맞춤형 솔루션

- langchain 단점
  - 대규모 데이터 처리나 실시간 응답을 요구하는 애플리케이션이기 때문에 성능 최적화가 필요
  - 추가적인 하드웨어 리소스나 코드 최적화가 요구 가능성
  - 추가적인 커스터마이징이 필요
