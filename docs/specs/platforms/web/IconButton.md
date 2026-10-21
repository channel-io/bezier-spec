# Web IconButton

| 항목           | 값                                     |
| -------------- | -------------------------------------- |
| 공개 명세 버전 | 0.1.0                                  |
| 상태           | 검토 초안, 배포 소스 대조              |
| 적용 구현      | @channel.io/bezier-react@4.0.0-next.15 |
| 진입점         | @channel.io/bezier-react/beta          |

공통 사용 기준은 [IconButton](../../components/IconButton.md)을 따른다. 텍스트 레이블을 비워 둔 Button 대신 이 컴포넌트를 사용한다.

## API

| Prop                        | 값                                                 | 기본값    |
| --------------------------- | -------------------------------------------------- | --------- |
| content                     | BezierIcon 또는 ReactNode, 필수                    | 없음      |
| variant                     | filled / outlined / ghost / floating               | ghost     |
| semantic                    | primary / secondary / destructive / activate       | secondary |
| size                        | xs / s / m / l                                     | m         |
| loading / disabled / active | boolean                                            | false     |
| as                          | 기본 button, 네이티브 링크는 a, 사용자 요소도 가능 | button    |
| type                        | button / reset / submit, button 렌더링에 적용      | button    |

`content`로 아이콘을 전달한다. `icon`·`label`·`leadingContent`를 이 컴포넌트의 콘텐츠 API로 사용하지 않는다. aria-label 또는 aria-labelledby로 접근 가능한 이름을 지정한다. 라이브러리는 이름을 자동 생성하지 않는다.

```tsx
import { PlusIcon } from '@channel.io/bezier-icons'
import { IconButton } from '@channel.io/bezier-react/beta'

export function AddAction({ onAdd }: { onAdd: () => void }) {
  return <IconButton content={PlusIcon} aria-label="추가" onClick={onAdd} />
}
```

## 치수

| size | 너비·높이 | padding | BezierIcon 크기 |
| ---- | --------- | ------- | --------------- |
| xs   | 20px      | 3px     | 14px            |
| s    | 24px      | 4px     | 16px            |
| m    | 32px      | 7px     | 18px            |
| l    | 42px      | 12px    | 18px            |

모든 크기에 radius 9999px를 사용한다. 위 아이콘 크기는 라이브러리가 BezierIcon을 렌더링하는 경로의 스타일이다. 임의의 ReactNode 크기까지 자동 보장하지 않는다.

## 상태

`loading`과 `disabled`의 네이티브 비활성화, aria-busy, 사용자 정의 as의 확인 범위는 [Web Button](Button.md)과 같다. loading 때 콘텐츠의 자리를 유지하고 중앙에 Spinner를 표시한다. Spinner는 xs/s/m에서 12px, l에서 16px이다.

시각 스타일과 semantic 축은 Button과 같지만 기본값은 ghost·secondary다. 아이콘과 Spinner는 아이콘 색상 토큰을 따른다. 이름을 아이콘 자체에만 지정하고 버튼 이름을 생략하지 않는다.

## 공개 구현 근거

[타입](https://github.com/channel-io/bezier-react/blob/dabea2e052b5ee0f6993eb9159dff773061017c1/packages/bezier-react/src/beta/IconButton/IconButton.types.ts) · [구현](https://github.com/channel-io/bezier-react/blob/dabea2e052b5ee0f6993eb9159dff773061017c1/packages/bezier-react/src/beta/IconButton/IconButton.tsx) · [스타일](https://github.com/channel-io/bezier-react/blob/dabea2e052b5ee0f6993eb9159dff773061017c1/packages/bezier-react/src/beta/IconButton/IconButton.module.scss)

검증 방법과 한계는 [Web 안내](README.md)를 따른다.
