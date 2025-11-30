Directory: exercises/core-12

지금까지 긴 `docker run` 명령어를 사용하여 container를 실행해왔습니다. 한두 개의 container에는 괜찮지만, 애플리케이션이 커지면 관리하기 어려워집니다.

**Docker Compose**는 다중 container Docker 애플리케이션을 정의하고 실행하기 위한 도구입니다. Compose를 사용하면 YAML 파일로 애플리케이션의 서비스, network, volume을 구성합니다. 그런 다음 단일 명령으로 구성에서 모든 서비스를 생성하고 시작할 수 있습니다.

이것은 로컬 개발 환경을 관리하는 표준 방법입니다.

## Your Task

이 디렉토리에 단일 Redis 서비스를 정의하는 `docker-compose.yml` 파일을 생성하세요.

`docker-compose.yml` 파일은 다음을 정의해야 합니다:
1.  `redis-server`라는 이름의 서비스.
2.  서비스는 `redis:alpine` image를 사용해야 합니다.
3.  container는 명시적으로 `c12-redis`로 이름이 지정되어야 합니다.
4.  host의 port `6379`를 container의 port `6379`에 매핑해야 합니다.

파일을 생성한 후 `docker compose up`을 실행하여 직접 테스트할 수 있습니다. 검증 스크립트가 이 명령을 실행하여 작업을 확인합니다.
