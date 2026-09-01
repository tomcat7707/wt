# WebMCP Lab

WebMCP가 실제로 어떤 개념인지 확인하기 위한 최소 실험입니다.

## 무엇을 비교하는가?

사람은 웹페이지의 `켜기/끄기` 버튼을 클릭합니다.

WebMCP를 지원하는 실험 환경에서는 Agent가 다음 Tool을 사용할 수 있습니다.

- `get_device_status` — 현재 상태 조회
- `set_device_state` — ON/OFF 변경

중요한 점은 **Agent가 버튼을 찾아 클릭하는 것이 아니라, 웹 애플리케이션이 제공하는 Tool을 직접 호출한다**는 것입니다.

## 실행

`index.html`을 WebMCP를 지원하는 Chrome 실험 환경에서 제공합니다.

Chrome 공식 WebMCP 문서에서 안내하는 실험 설정을 사용하세요. 현재 WebMCP는 초기 단계의 기능이므로 브라우저 버전/설정에 따라 동작 여부가 달라질 수 있습니다.

## 관찰 포인트

1. 사람이 `켜기`를 누르면 화면 상태와 로그가 바뀝니다.
2. Agent가 `get_device_status`를 호출하면 화면을 읽는 대신 구조화된 상태를 받습니다.
3. Agent가 `set_device_state({state: "ON"})`을 호출하면 동일한 웹앱의 상태 변경 로직이 실행되고 화면 로그에도 결과가 표시됩니다.
4. 이 예제는 실제 장치를 제어하지 않습니다. 모든 상태는 브라우저 메모리 안에서만 유지됩니다.

이 작은 실험이 나중에 NeoFarm에서 `get_zone_status()`, `request_irrigation()` 같은 Tool로 확장되는 기본 개념입니다.
