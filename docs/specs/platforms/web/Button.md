# Web Button

| 항목           | 값                                     |
| -------------- | -------------------------------------- |
| 공개 명세 버전 | 0.1.0                                  |
| 상태           | 검토 초안, 배포 소스 대조              |
| 적용 구현      | @channel.io/bezier-react@4.0.0-next.15 |
| 진입점         | @channel.io/bezier-react/beta          |

공통 사용 기준은 [Button](../../components/Button.md)과 [액션과 피드백](../../foundations/action-and-feedback.md)을 따른다. 다음 내용은 이 버전의 /beta 구현에 한정한다.

## API

| Prop                             | 값                                                 | 기본값  |
| -------------------------------- | -------------------------------------------------- | ------- |
| label                            | string, 필수                                       | 없음    |
| variant                          | filled / outlined / ghost / floating               | filled  |
| semantic                         | primary / secondary / destructive / activate       | primary |
| size                             | xs / s / m / l                                     | m       |
| leadingContent / trailingContent | BezierIcon 또는 ReactNode                          | 없음    |
| loading / disabled / active      | boolean                                            | false   |
| as                               | 기본 button, 네이티브 링크는 a, 사용자 요소도 가능 | button  |
| type                             | button / reset / submit, button 렌더링에 적용      | button  |

레이블은 `label`이다. `text`나 `children`을 레이블 API로 사용하지 않는다. `size="medium"` 또는 `size="xl"`은 이 API의 값이 아니다.

```tsx
import { Button } from '@channel.io/bezier-react/beta'

export function SaveAction({
  pending,
  onSave,
}: {
  pending: boolean
  onSave: () => void
}) {
  return <Button label="저장" loading={pending} onClick={onSave} />
}
```

## 치수

| size | 높이 | 최소 너비 | 루트 좌우 padding | 라벨 크기 | 아이콘 크기 |
| ---- | ---- | --------- | ----------------- | --------- | ----------- |
| xs   | 20px | 20px      | 4px               | 12px      | 14px        |
| s    | 24px | 24px      | 6px               | 13px      | 16px        |
| m    | 32px | 36px      | 10px              | 13px      | 18px        |
| l    | 42px | 44px      | 12px              | 14px      | 18px        |

모든 크기에 radius 9999px, 라벨 weight 500을 사용한다. 루트 padding과 별도로 텍스트 요소의 좌우 padding이 xs/s/m에서 3px, l에서 4px이다. 기본 너비는 콘텐츠를 따른다. 설계상 너비 조정이 필요하면 부모 레이아웃에서 제어한다.

## 상태와 스타일

- `loading` 또는 `disabled`이면 비활성화한다. 기본 button은 native disabled를, `as="a"`는 aria-disabled와 클릭·탭 이동 제어를 사용한다.
- `loading`은 콘텐츠를 visibility:hidden으로 숨겨 레이아웃을 유지하고 중앙 Spinner를 표시한다. Spinner 크기는 xs/s/m에서 12px, l에서 16px이다. aria-busy를 설정한다. 로딩 표시 지연이나 요청 상태 자체를 관리하지 않는다.
- 이 Web 버전에서는 비활성 루트에 opacity-disabled가 적용되며 loading도 비활성화 경로를 따른다.
- `active`는 비활성이 아닐 때 hover와 같은 스타일을 강제한다. 선택됨을 전달하는 ARIA 상태를 자동으로 뜻하지 않는다.
- 기본 button과 a에는 BaseButton의 focus-visible 스타일이 적용된다. 사용자 정의 `as`는 이 네이티브 경로를 거치지 않으므로 키보드·링크 의미·비활성 처리를 별도로 확인한다.
- outlined의 테두리는 1px inset box-shadow와 color-border-neutral이다. transparent 배경도 color-fill-neutral-transparent 토큰을 사용한다.
- floating은 color-fill-bright 배경과 elevation-2 그림자를 쓴다. hover/active 때 배경 대신 elevation-3로 바뀐다.
- 텍스트와 아이콘은 별도 색상 토큰을 사용한다. 로딩 Spinner의 색상은 텍스트 색상을 따른다.

## 공개 구현 근거

[타입](https://github.com/channel-io/bezier-react/blob/dabea2e052b5ee0f6993eb9159dff773061017c1/packages/bezier-react/src/beta/Button/Button.types.ts) · [구현](https://github.com/channel-io/bezier-react/blob/dabea2e052b5ee0f6993eb9159dff773061017c1/packages/bezier-react/src/beta/Button/Button.tsx) · [스타일](https://github.com/channel-io/bezier-react/blob/dabea2e052b5ee0f6993eb9159dff773061017c1/packages/bezier-react/src/beta/Button/Button.module.scss) · [공통 네이티브 버튼 처리](https://github.com/channel-io/bezier-react/blob/dabea2e052b5ee0f6993eb9159dff773061017c1/packages/bezier-react/src/beta/BaseButton/BaseButton.tsx)

검증 방법과 한계는 [Web 안내](README.md)를 따른다.
