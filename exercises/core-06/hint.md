다음은 필요한 `Dockerfile` 명령어들입니다.

-   **`LABEL`**: key-value 메타데이터를 추가하는 데 사용됩니다. base image와 충돌을 피하기 위해 고유한 key를 사용하세요.
    ```Dockerfile
    LABEL org.dockerlings.author="your.name@example.com"
    ```

-   **`ENV`**: 환경 변수를 설정합니다. container 프로세스가 이 변수를 상속받습니다.
    ```Dockerfile
    ENV PORT=8000
    ```

-   **`EXPOSE`**: 애플리케이션이 사용하는 port를 문서화하는 것이 좋은 관행입니다.
    ```Dockerfile
    EXPOSE 8000
    ```
-   **`CMD`**: `app.py` 스크립트는 환경 변수에서 `PORT`를 읽도록 작성되어 있으므로, 스크립트를 실행하기만 하면 됩니다.
    ```Dockerfile
    CMD ["python", "app.py"]
