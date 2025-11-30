Directory: exercises/core-13

Docker Compose의 진정한 힘은 여러 개의 상호 연결된 서비스로 전체 애플리케이션 스택을 정의하고 실행하는 것입니다.

이 실습에서는 두 개의 서비스 애플리케이션을 정의합니다: Python 웹 앱과 Redis 캐시. 또한 `depends_on`을 사용하여 Compose에 Redis 서비스가 시작될 때까지 웹 앱이 시작되지 않아야 함을 알립니다. 이는 애플리케이션 스택의 시작 순서를 제어하는 데 도움이 됩니다.

## Your Task

웹 앱(`app` 디렉토리에 제공됨)과 Redis 데이터베이스를 오케스트레이션하는 `docker-compose.yml` 파일을 생성하세요.

`docker-compose.yml` 파일은 `web`과 `redis` 두 서비스를 정의해야 합니다.

1.  **`redis` 서비스:**
    *   `redis:alpine` image를 사용해야 합니다.
    *   명확성을 위해 `c13-redis`로 이름을 지정할 수 있습니다.

2.  **`web` 서비스:**
    *   `./app` 디렉토리의 `Dockerfile`에서 빌드되어야 합니다.
    *   `c13-web`으로 이름이 지정되어야 합니다.
    *   host의 port `8013`을 container의 port `5000`에 매핑해야 합니다.
    *   `depends_on`을 사용하여 `redis` 서비스 이후에 시작되도록 해야 합니다.
    *   `REDIS_HOST` 환경 변수를 `redis`로 설정해야 합니다. 이것이 Python 앱이 내부 Docker network에서 Redis 서비스의 hostname을 아는 방법입니다.

파일을 생성한 후 `docker compose up --build`로 테스트할 수 있습니다. 검증 스크립트가 이를 대신 수행합니다.
