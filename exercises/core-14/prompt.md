Directory: exercises/core-14

다중 서비스 애플리케이션을 성공적으로 오케스트레이션했습니다. 이제 Docker Compose를 사용하여 견고한 데이터 영속성과 네트워킹 모범 사례를 추가할 시간입니다.

- **Named Volume**: host의 디렉토리 구조에 의존하는 bind mount와 달리, named volume은 Docker 자체에서 관리합니다. 데이터베이스와 같은 서비스의 데이터를 유지하는 데 권장되는 방법입니다.
- **Custom Network**: Compose가 기본 network를 생성하지만, 직접 정의하면 더 나은 격리와 구성을 제공하고, 더 복잡한 network 토폴로지를 허용합니다.

## Your Task

이전 실습의 `docker-compose.yml`을 수정하여 Redis 데이터용 named volume을 포함하고 두 서비스를 커스텀 사용자 정의 network에 배치하세요.

1.  **최상위 `networks` 섹션을 정의**하고 `c14-app-net`이라는 network를 생성합니다.

2.  **최상위 `volumes` 섹션을 정의**하고 `redis-data`라는 named volume을 생성합니다.

3.  **`redis` 서비스 수정:**
    *   container 이름을 `c14-redis`로 지정합니다.
    *   `c14-app-net` network에 연결합니다.
    *   `redis-data` volume을 container 내부의 `/data` 디렉토리에 마운트합니다. 이곳이 Redis가 데이터를 저장하는 위치입니다.

4.  **`web` 서비스 수정:**
    *   container 이름을 `c14-web`으로 지정합니다.
    *   `c14-app-net` network에 연결합니다.
    *   host port `8014`를 container port `5000`에 매핑합니다.

디렉토리 구조와 애플리케이션 코드는 이전 실습과 동일합니다. `docker-compose.yml` 파일만 생성하고 수정하면 됩니다.
