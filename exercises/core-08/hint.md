다음 명령어 순서를 따라 영구 데이터베이스를 설정하세요.

1.  **host 디렉토리 생성:**
    ```bash
    mkdir pgdata
    ```

2.  **첫 번째 container 인스턴스 실행:**
    `-v "$(pwd)/pgdata:/var/lib/postgresql/data"` 플래그가 새로운 로컬 디렉토리를 container에 매핑합니다.
    ```bash
    docker run -d \
      --name c8-postgres \
      -e POSTGRES_PASSWORD=mysecretpassword \
      -v "$(pwd)/pgdata":/var/lib/postgresql/data \
      postgres:16
    ```
    *(데이터베이스가 초기화될 때까지 약 20초 기다리세요. `docker logs c8-postgres`로 상태를 확인할 수 있습니다.)*

3.  **데이터베이스 내부에 테이블 생성:**
    `docker exec`를 사용하여 기본 `postgres` 사용자로 `psql` 명령을 실행합니다.
    ```bash
    docker exec c8-postgres psql -U postgres -c "CREATE TABLE dvd_rentals (title TEXT);"
    ```

4.  **특정 데이터 행 삽입:**
    ```bash
    docker exec c8-postgres psql -U postgres -c "INSERT INTO dvd_rentals (title) VALUES ('The Grand Budapest Hotel');"
    ```

---

### 직접 확인하는 방법 ("아하" 순간)

1.  **container 제거:**
    ```bash
    docker stop c8-postgres && docker rm c8-postgres
    ```

2.  **동일한 데이터에 새 container 인스턴스 실행:**
    ```bash
    docker run -d \
      --name c8-postgres \
      -e POSTGRES_PASSWORD=mysecretpassword \
      -v "$(pwd)/pgdata":/var/lib/postgresql/data \
      postgres:16
    ```
    *(시작될 때까지 잠시 기다리세요.)*

3.  **데이터가 여전히 있는지 확인:**
    ```bash
    docker exec c8-postgres psql -U postgres -c "SELECT * FROM dvd_rentals;"
    ```
