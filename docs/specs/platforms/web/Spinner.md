# Web Spinner

| 항목           | 값                                     |
| -------------- | -------------------------------------- |
| 공개 명세 버전 | 0.1.0                                  |
| 상태           | 검토 초안, 배포 소스 대조              |
| 적용 구현      | @channel.io/bezier-react@4.0.0-next.15 |
| 진입점         | @channel.io/bezier-react/beta          |

공통 사용 기준은 [Spinner](../../components/Spinner.md)를 따른다. 이 버전의 beta API는 문자열 크기 값이다. 숫자 enum 기반 API와 혼용하지 않는다.

## API와 기본값

| Prop       | 값                                                           | 기본값                                 |
| ---------- | ------------------------------------------------------------ | -------------------------------------- |
| size       | '10' / '12' / '16' / '20' / '24' / '30' / '36' / '42' / '48' | '20'                                   |
| color      | 구현에서 허용하는 SemanticColor                              | 'icon-neutral'                         |
| role       | div에 전달하는 ARIA role                                     | 'status'                               |
| aria-label | 접근 가능한 이름                                             | role이 status이고 미지정이면 'Loading' |

```tsx
import { Spinner } from '@channel.io/bezier-react/beta'

export function LoadingStatus() {
  return <Spinner size="20" color="icon-neutral" aria-label="불러오는 중" />
}
```

size 값의 숫자와 너비·높이가 px로 일치한다. 링 두께는 크기의 1/8이고, 1초 주기의 linear infinite 회전이다. 윗변은 투명하며 나머지 세 변에 색상을 적용한다. color는 colorTokenCssVar를 거쳐 --b-beta-spinner-color에 연결된다.

색상은 배경과 구분되도록 선택한다. 로딩 피드백 용도에 맞춰 아이콘·텍스트 계열 의미 색상을 우선 고려한다.

## 상태와 접근성

Spinner 자체는 항상 회전하는 표시다. 요청 시작·종료나 300ms 표시 지연을 자동으로 관리하지 않는다. 애플리케이션에서 필요한 시점에 렌더링하고 완료하면 제거한다.

기본 role은 status다. 한국어 화면에서는 aria-label로 문맥에 맞는 이름을 제공한다. role을 바꾸면 기본 'Loading' 이름도 자동 적용되지 않을 수 있으므로 이름과 상태 전달을 함께 확인한다.

Button·IconButton 내부의 Spinner는 해당 컴포넌트가 크기와 색상을 지정한다. 임의의 Spinner를 추가해 중복 표시하지 않는다.

## 공개 구현 근거

[타입](https://github.com/channel-io/bezier-react/blob/dabea2e052b5ee0f6993eb9159dff773061017c1/packages/bezier-react/src/beta/Spinner/Spinner.types.ts) · [구현](https://github.com/channel-io/bezier-react/blob/dabea2e052b5ee0f6993eb9159dff773061017c1/packages/bezier-react/src/beta/Spinner/Spinner.tsx) · [스타일](https://github.com/channel-io/bezier-react/blob/dabea2e052b5ee0f6993eb9159dff773061017c1/packages/bezier-react/src/beta/Spinner/Spinner.module.scss)

검증 방법과 한계는 [Web 안내](README.md)를 따른다.
