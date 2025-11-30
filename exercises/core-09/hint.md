bind mount에는 `-v` 플래그와 함께 `docker run` 명령어를 사용합니다. 형식은 `-v <host-path>:<container-path>` 입니다.

- 현재 디렉토리의 절대 경로를 얻으려면 `$(pwd)`를 사용할 수 있습니다.
- 마운트를 read-only로 만들려면 끝에 `:ro`를 추가합니다.

전체 명령어 구조는 다음과 같습니다:
```bash
docker run -d \
  --name c9-dev-server \
  -p 8009:80 \
  -v "$(pwd)/app":/usr/share/nginx/html:ro \
  nginx
