Directory: exercises/core-05

이제 직접 커스텀 image를 빌드할 시간입니다!

`nginx`와 같은 미리 빌드된 image를 실행하는 것도 유용하지만, Docker의 진정한 힘은 자신의 애플리케이션을 패키징하는 데서 나옵니다. 이것은 `Dockerfile`이라는 파일에 일련의 명령어를 작성하여 수행합니다.

## Your Task

이 디렉토리에 간단한 Python Flask 애플리케이션(`app.py`)과 의존성 파일(`requirements.txt`)이 있습니다.

이 애플리케이션을 image로 패키징하는 **`Dockerfile`을 생성**하세요.

`Dockerfile`은 다음 단계를 수행해야 합니다:
1.  적절한 Python base image로 시작합니다 (예: `python:3.9-slim`).
2.  image 내부에 working directory를 설정합니다 (예: `/app`).
3.  `requirements.txt` 파일을 image로 복사합니다.
4.  `pip`를 사용하여 Python 의존성을 설치합니다.
5.  애플리케이션 소스 코드(`app.py`)를 image로 복사합니다.
6.  런타임에 container가 port `5000`에서 수신 대기함을 Docker에 알립니다.
7.  container가 시작될 때 Flask 애플리케이션을 실행하는 기본 명령을 설정합니다.

`Dockerfile`을 생성한 후, `check` 명령어가 이를 빌드하고 애플리케이션 container가 올바르게 실행되는지 테스트합니다.
