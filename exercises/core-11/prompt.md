Directory: exercises/core-11

초보자들이 흔히 혼란스러워하는 것이 `Dockerfile`의 `EXPOSE`와 `docker run`에서 사용하는 `--publish` (또는 `-p`) 플래그의 차이입니다.

-   **`EXPOSE <port>`**: 이것은 문서화 명령어입니다. container를 실행하는 사람에게 내부 애플리케이션이 어떤 port에서 수신 대기하도록 의도되었는지 알려줍니다. port를 열거나 host에서 접근 가능하게 만들지 **않습니다**.

-   **`docker run -p <host_port>:<container_port>`**: 이것은 런타임 명령어입니다. host 머신의 port에서 container 내부의 port로 트래픽을 매핑하는 network 규칙을 실제로 생성합니다.

## Your Task

웹 애플리케이션 container를 올바르게 문서화하고 실행하세요.

1.  **`Dockerfile`을 수정합니다**. 제공된 `Dockerfile` 내부에 애플리케이션이 port **8080**에서 수신 대기함을 문서화하는 `EXPOSE` 명령어를 추가하세요.

2.  **image를 빌드합니다**. `c11-app`과 같은 tag를 지정하세요.
    ```bash
    docker build -t c11-app .
    ```

3.  **container를 실행합니다**.
    - container 이름을 `c11-server`로 지정합니다.
    - 노출된 container port(`8080`)를 host 머신의 port `8011`에 publish합니다.

**실습을 완료하려면 container를 실행 상태로 두세요.** checker가 빌드된 image와 실행 중인 container 모두 올바르게 구성되었는지 검사합니다.
