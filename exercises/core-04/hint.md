다음 명령어들을 순서대로 사용하여 실습을 완료하세요.

1.  **파일을 container *안으로* 복사:**
    문법은 `docker cp <host-path> <container-name>:<container-path>` 입니다.
    ```bash
    docker cp run-inside-container.sh c4-container:/tmp/
    ```

2.  **스크립트를 실행 가능하게 만들기:**
    `docker exec`를 사용하여 container 내부에서 `chmod` 명령어를 실행해야 합니다.
    ```bash
    docker exec c4-container chmod +x /tmp/run-inside-container.sh
    ```

3.  **스크립트 실행:**
    `docker exec`를 다시 사용하여 방금 복사한 스크립트를 실행합니다.
    ```bash
    docker exec c4-container /tmp/run-inside-container.sh
    ```

4.  **결과 파일을 container *밖으로* 복사:**
    문법은 `docker cp <container-name>:<container-path> <host-path>` 입니다.
    ```bash
    docker cp c4-container:/tmp/container-info.txt .
    ```
