`Dockerfile`은 일련의 명령어로 구성됩니다. 다음은 필요한 주요 명령어들입니다:

-   **`FROM python:3.9-slim`**: 빌드의 시작 image를 지정합니다.
-   **`WORKDIR /app`**: 이후 모든 명령어(`COPY`, `RUN`, `CMD`)의 현재 디렉토리를 설정합니다.
-   **`COPY <source> <destination>`**: host에서 image로 파일을 복사합니다.
    *팁: 빌드 캐싱을 최적화하려면 `requirements.txt`를 복사하고 `pip install`을 실행한 *후에* 나머지 애플리케이션 코드를 복사해야 합니다.*
-   **`RUN <command>`**: image 빌드 중 명령어를 실행합니다. 의존성 설치에 사용됩니다.
    ```
    RUN pip install -r requirements.txt
    ```
-   **`EXPOSE 5000`**: 애플리케이션이 이 port에서 수신 대기함을 Docker에 알립니다. 문서화를 위한 좋은 관행입니다.
-   **`CMD ["python", "app.py"]`**: container가 시작될 때 실행할 기본 명령을 제공합니다. 명령어에는 JSON 배열 형식을 사용해야 합니다.
