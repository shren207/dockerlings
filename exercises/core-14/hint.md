`docker-compose.yml`은 이제 `services` key 외에도 최상위 `volumes`와 `networks` key를 가져야 합니다.

```yaml
# 최상위에 커스텀 network 정의
networks:
  c14-app-net:

# 최상위에 named volume 정의
volumes:
  redis-data:

services:
  web:
    build: ./app
    container_name: c14-web
    ports:
      - "8014:5000"
    environment:
      - REDIS_HOST=redis
    depends_on:
      - redis
    # 이 서비스를 network에 연결
    networks:
      - c14-app-net

  redis:
    image: redis:alpine
    container_name: c14-redis
    # named volume 마운트
    volumes:
      - redis-data:/data
    # 이 서비스를 network에 연결
    networks:
      - c14-app-net
```
참고: `redis:alpine` image는 데이터를 `/data` 디렉토리에 자동으로 저장하도록 구성되어 있습니다. 거기에 volume을 마운트하면 데이터가 유지됩니다.
