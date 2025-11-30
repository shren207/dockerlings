다음은 필요한 명령어들입니다.

1.  **network 생성:**
    ```bash
    docker network create c10-network
    ```

2.  **특정 network에서 container 실행:**
    `docker run` 명령어에서 `--network` 플래그를 사용합니다.

    데이터베이스 container:
    ```bash
    docker run -d \
      --name c10-db \
      --network c10-network \
      -e POSTGRES_PASSWORD=mysecretpassword \
      postgres:14-alpine
    ```

    애플리케이션 container:
    ```bash
    docker run -d \
      --name c10-app \
      --network c10-network \
      busybox sleep 3600
    ```

이 `docker run` 명령어들을 `run-containers.sh` 스크립트에 넣으세요.
