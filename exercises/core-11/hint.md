1.  **Dockerfile에서:**
    `EXPOSE` 명령어는 단순히 port 번호를 받습니다.
    ```Dockerfile
    EXPOSE 8080
    ```

2.  **명령줄에서:**
    `-p` 플래그가 host port를 container port에 매핑합니다.
    ```bash
    # 사용법: docker run -d --name <container_name> -p <host_port>:<container_port> <image_name>

    docker run -d --name c11-server -p 8011:8080 c11-app
    ```
