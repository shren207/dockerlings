Directory: exercises/core-03

이 실습에서는 container에서 로그를 가져오는 방법을 배웁니다. 이것은 Docker 내부에서 실행되는 애플리케이션을 디버깅하기 위한 기본적인 기술입니다.

container의 표준 출력(standard output)과 표준 에러(standard error) 스트림은 캡처되어 container의 생명주기 동안 언제든지 접근할 수 있습니다.

## Task

이 디렉토리에 `Dockerfile`이 있습니다. 다음 단계를 수행하세요:

1.  이 디렉토리의 `Dockerfile`로 Docker image를 **빌드**합니다. 기억하기 쉬운 tag를 지정하세요 (예: `logging-app`).
    ```bash
    docker build -t logging-app .
    ```

2.  image를 **detached mode** (`-d`)로 **실행**합니다. 이렇게 하면 container가 백그라운드에서 계속 실행되어 프로세스가 종료된 후에도 로그를 가져올 수 있습니다. 쉽게 참조할 수 있도록 container에 이름을 지정하세요 (예: `my-logger`).
    ```bash
    docker run -d --name my-logger logging-app
    ```

3.  `docker logs` 명령어를 사용하여 `my-logger` container에서 **로그를 가져와** 이 디렉토리에 `logs.txt` 파일로 저장합니다.

검증 스크립트가 `logs.txt` 파일이 존재하는지, 그리고 내용이 올바른지 확인합니다. 로그를 캡처한 후에는 container를 중지하고 제거하여 정리할 수 있습니다.
