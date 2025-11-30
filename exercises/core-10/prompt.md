Directory: exercises/core-10

기본적으로 container는 외부 세계와 통신할 수 있지만, 서로를 발견하고 통신하는 능력은 제한적입니다. 연결할 수는 있지만, 현대적이고 권장되는 방식은 커스텀 **bridge network**를 사용하는 것입니다.

여러 container를 동일한 커스텀 network에 배치하면, container 이름을 hostname으로 사용하여 서로를 찾고 통신할 수 있는 내부 DNS 서비스를 얻습니다. 이것은 다중 서비스 애플리케이션(예: 데이터베이스와 통신하는 웹 서버)을 구축하는 데 기본이 됩니다.

## Your Task

network를 만들고 해당 network에서 두 개의 container를 실행하는 스크립트를 작성하세요.

1.  **커스텀 bridge network를 생성**하고 이름을 `c10-network`로 지정합니다. 터미널에서 일회성 명령으로 수행할 수 있습니다.

2.  이 디렉토리에 제공된 **`run-containers.sh` 스크립트를 편집**합니다. 스크립트는 다음 작업을 수행해야 합니다:
    *   `c10-db`라는 이름의 `postgres:14-alpine` container를 실행합니다.
    *   `c10-app`이라는 이름의 `busybox` container를 실행합니다.
    *   **두** container 모두 생성한 `c10-network`에 연결되어야 합니다.
    *   `busybox` container는 `sleep 3600`과 같은 장시간 실행 명령으로 계속 실행되어야 합니다.

검증 스크립트가 `run-containers.sh` 스크립트를 실행한 다음, `c10-app` container가 이름으로 `c10-db` container를 성공적으로 ping할 수 있는지 테스트합니다.
