Directory: exercises/core-06

이 실습에서는 메타데이터를 추가하고 image를 더 설정 가능하게 만드는 `Dockerfile` 명령어를 소개합니다.

- `LABEL`: maintainer 이메일이나 버전 번호와 같은 메타데이터를 image에 추가합니다.
- `ENV`: 빌드 중과 image에서 container가 실행될 때 사용할 수 있는 영구 환경 변수를 설정합니다.
- `CMD`: container가 시작될 때 실행할 기본 명령을 지정합니다. 환경 변수를 어떻게 사용할 수 있는지 살펴봅니다.

## Your Task

이 디렉토리에 `Dockerfile`과 간단한 Python Flask 애플리케이션이 있습니다. 다음을 수행하도록 **`Dockerfile`을 수정**하세요:

1.  image에 **`LABEL`을 추가**합니다. key는 `org.dockerlings.author`이고 value는 이름 또는 이메일이어야 합니다 (예: `"Jane Doe <jane.doe@example.com>"`).
2.  `PORT`라는 이름의 **`ENV`** 변수를 값 `8000`으로 설정합니다.
3.  `$PORT` 환경 변수를 사용하여 Flask 애플리케이션이 올바른 port에서 실행되도록 **`CMD`** 명령어를 수정합니다. 애플리케이션(`app.py`)은 이미 이 환경 변수를 읽도록 작성되어 있습니다.

검증 스크립트가 `Dockerfile`을 빌드하고, 올바른 `LABEL`과 `ENV`를 검사한 다음, 실행하여 애플리케이션이 지정된 port에서 시작하는지 확인합니다.
