Directory: exercises/core-07

지금까지 Python 애플리케이션을 패키징하여 image를 빌드했습니다. Docker의 일반적인 사용 사례 중 하나는 정적 웹사이트를 패키징하고 서빙하는 것입니다.

`COPY` 명령어는 `Dockerfile`에서 가장 기본적인 명령어 중 하나입니다. 로컬 파일 시스템(빌드 컨텍스트)에서 생성 중인 image로 파일과 디렉토리를 복사할 수 있습니다.

## Your Task

이 디렉토리에 간단한 웹사이트가 포함된 `html`이라는 하위 디렉토리가 있습니다.

기본 Nginx 환영 페이지 대신 이 커스텀 정적 콘텐츠를 서빙하는 새로운 Nginx image를 빌드하는 **`Dockerfile`을 생성**하세요.

`Dockerfile`은 다음을 수행해야 합니다:
1.  `nginx:stable-alpine`과 같은 경량 Nginx image로 시작합니다.
2.  `COPY` 명령어를 사용하여 `html` 디렉토리의 내용을 Nginx가 정적 파일을 서빙하는 위치인 `/usr/share/nginx/html`로 복사합니다.

검증 스크립트가 image를 빌드하고 실행한 다음, 커스텀 웹사이트가 올바르게 서빙되는지 확인합니다.
