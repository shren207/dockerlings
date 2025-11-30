`docker-compose.yml` 파일은 명확하고 계층적인 구조를 가집니다. 다음은 시작하기 위한 템플릿입니다.

```yaml
services:
  # 서비스의 논리적 이름입니다.
  redis-server:
    # 사용할 image를 지정합니다.
    image: redis:alpine

    # container에 예측 가능한 이름을 설정합니다.
    container_name: c12-redis

    # port 매핑을 정의합니다.
    # 형식은 "HOST:CONTAINER" 목록입니다.
    ports:
      - "6379:6379"
