# Bezier Spec

Bezier 디자인 시스템의 공개 명세를 Web·iOS·Android에서 함께 참조하기 위한 저장소입니다.

현재 1차 공개 검토 초안으로 Button·IconButton·Spinner와 공통 액션·피드백 규칙을 제공합니다. Web은 `@channel.io/bezier-react@4.0.0-next.15`의 `/beta` 소스·타입·스타일을 대조했습니다. iOS·Android 구현은 미확인입니다.

## 문서 찾기

- [llms.txt](llms.txt): AI가 필요한 문서를 선택해서 읽는 목차
- [컴포넌트](docs/specs/components/README.md): 컴포넌트별 사용 기준·상태·접근성
- [Foundations](docs/specs/foundations/README.md): 여러 컴포넌트가 공유하는 규칙
- [플랫폼별 안내](docs/specs/platforms/README.md): Web·iOS·Android의 구현 문서와 차이
- [기여 안내](CONTRIBUTING.md): 공개 문서 작성과 변경 절차

`llms.txt`에는 문서 링크와 짧은 설명만 둡니다. 본문은 개별 Markdown 파일로 나눕니다. 전체 명세를 한 파일에 합치지 않습니다.

```text
llms.txt
docs/specs/
  components/       컴포넌트별 공통 명세
  foundations/      공통 규칙
  platforms/
    web/            Web 차이와 구현 연결
    ios/            iOS 차이와 구현 연결
    android/        Android 차이와 구현 연결
templates/
  component.md      신규 명세 작성 양식
```

## 플랫폼 저장소에서 참조하기

`bezier-react`, `BezierSwift`, `bezier-compose`는 이 저장소의 특정 commit 또는 tag를 선택합니다. 목차와 본문은 같은 ref에서 읽습니다. `main`은 탐색용 최신 문서이며 특정 라이브러리 버전과의 호환성을 뜻하지 않습니다.

PR이 병합된 후 공개 기본 브랜치의 commit을 선택해 아래 주소 형식을 사용합니다. `REF`와 `PATH`는 선택한 commit과 실제 문서 경로로 바꿉니다.

```text
https://raw.githubusercontent.com/channel-io/bezier-spec/REF/llms.txt
https://raw.githubusercontent.com/channel-io/bezier-spec/REF/PATH
```

플랫폼 저장소의 `AGENTS.md` 등에서 이 진입점을 안내하고, 작업 대상 컴포넌트와 플랫폼 문서를 먼저 읽도록 합니다. `llms.txt`의 상대 링크는 해당 ref의 파일 URL을 기준으로 해석합니다. 파일을 저장소에 두는 것만으로 에이전트의 자동 탐색을 보장하지 않습니다.

라이브러리별 적용 ref는 각 플랫폼 저장소에서 관리합니다. 현재 연결된 라이브러리 버전이나 배포 tag는 없습니다. npm 패키지 동봉과 Toolkit 연동은 별도 작업입니다.

## 명세 변경과 기여

공통 명세와 플랫폼별 보충 문서에 PR로 기여할 수 있습니다. 각 문서의 상태·적용 범위·확인한 구현 버전을 함께 읽고, 변경 제안에는 근거와 영향받는 플랫폼을 적습니다. [기여 안내](CONTRIBUTING.md)를 참고합니다.

검증 범위는 배포 소스 대조입니다. 브라우저·보조 기술·제품 통합 테스트와 플랫폼 저장소 연결은 아직 수행하지 않았습니다.
