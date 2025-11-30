이 실습을 완료하려면 `COPY` 명령어를 사용해야 합니다.

-   **`FROM <image>`**: base image로 `Dockerfile`을 시작합니다. `nginx:stable-alpine`이 작고 효율적이므로 좋은 선택입니다.
    ```Dockerfile
    FROM nginx:stable-alpine
    ```

-   **`COPY <source> <destination>`**: 복사 문법은 간단합니다. `<source>`는 빌드 컨텍스트(현재 디렉토리)를 기준으로 한 상대 경로이고, `<destination>`은 image 내부의 절대 경로입니다.
    ```Dockerfile
    # 'html' 디렉토리의 *내용*을 복사합니다
    COPY html/ /usr/share/nginx/html/
    ```

**참고:** source의 후행 슬래시(`html/`)가 중요합니다. 디렉토리 자체가 아닌 디렉토리의 내용을 복사하도록 Docker에 지시합니다.
