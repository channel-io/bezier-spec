# Web

| 항목             | 값                                       |
| ---------------- | ---------------------------------------- |
| 공개 명세 버전   | 0.1.0                                    |
| 상태             | 검토 초안, 배포 패키지 소스 대조         |
| 확인한 구현      | @channel.io/bezier-react@4.0.0-next.15   |
| 진입점           | @channel.io/bezier-react/beta            |
| 공개 구현 commit | dabea2e052b5ee0f6993eb9159dff773061017c1 |

근거는 [npm 배포 패키지](https://registry.npmjs.org/@channel.io/bezier-react/-/bezier-react-4.0.0-next.15.tgz)의 src/beta 소스와 타입이다. [해당 공개 commit](https://github.com/channel-io/bezier-react/tree/dabea2e052b5ee0f6993eb9159dff773061017c1/packages/bezier-react/src/beta)에서도 확인할 수 있다.

이 버전의 기본 진입점과 /beta 진입점은 API가 다를 수 있다. 아래 명세를 기본 진입점이나 다른 버전에 적용하지 않는다.

- [Button](Button.md): 텍스트 액션과 label 기반 API
- [IconButton](IconButton.md): content 기반 아이콘 액션
- [Spinner](Spinner.md): 문자열 size 기반 로딩 표시

검증 범위는 소스·타입·스타일 대조다. 브라우저 렌더링·보조 기술·애플리케이션 통합 테스트를 완료했다는 뜻은 아니다. 공통 설계 요구와 구현 동작이 다르면 차이를 구분하고 검토한다.
