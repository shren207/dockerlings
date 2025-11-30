`docker-compose.yml` 파일은 이제 `services` 아래에 두 개의 최상위 key를 갖습니다. 또한 `build`, `environment`, `depends_on` key를 소개합니다.

```yaml
services:
  # 웹 애플리케이션 서비스
  web:
    # Compose에 'app' 디렉토리의 Dockerfile에서 image를 빌드하도록 지시합니다
    build: ./app
    container_name: c13-web
    ports:
      - "8013:5000"
    # app.py 스크립트가 이것을 사용하여 redis 서비스에 연결합니다
    environment:
      - REDIS_HOST=redis
    # redis 서비스가 web 서비스보다 먼저 시작되도록 합니다
    depends_on:
      - redis

  # Redis 데이터베이스 서비스
  redis:
    image: redis:alpine
    container_name: c13-redis
