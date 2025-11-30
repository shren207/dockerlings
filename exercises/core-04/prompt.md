Directory: exercises/core-04

이 실습에서는 실행 중인 container에서 파일을 관리하고 명령어를 실행하는 전체 워크플로우를 배웁니다. 이를 증명하기 위해 파일 내용을 직접 만들지 않습니다. 대신 container 내부에서 스크립트를 실행하여 내용을 생성합니다.

## Task

실행 중인 Nginx container에 스크립트를 복사하고, 실행한 다음, 결과 출력 파일을 host 머신으로 다시 복사하세요.

1.  `nginx` image에서 container를 **detached mode로 실행**합니다. 이름은 `c4-container`로 지정하세요.
    ```bash
    docker run -d --name c4-container nginx
    ```

2.  host에서 container로 **스크립트를 복사**합니다. 이 디렉토리에 `run-inside-container.sh` 스크립트가 제공됩니다. container 내부의 `/tmp` 디렉토리로 복사하세요.

3.  `docker exec`를 사용하여 container 내부에서 **스크립트를 실행 가능하게** 만드세요.

4.  마찬가지로 `docker exec`를 사용하여 container 내부에서 **스크립트를 실행**하세요. 스크립트가 `/tmp/container-info.txt`에 새 파일을 생성합니다.

5.  container에서 host의 현재 디렉토리로 **출력 파일** (`/tmp/container-info.txt`)을 **복사**하세요.

검증 스크립트가 이 `container-info.txt` 파일의 내용이 올바른지 확인합니다.

**정리:** 완료되면 container를 중지하고 제거하세요: `docker stop c4-container && docker rm c4-container`.
