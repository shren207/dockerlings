multi-stage build는 여러 개의 `FROM` 명령어를 사용합니다. 각 `FROM`은 새로운 빌드 stage를 시작합니다. stage에 이름을 지정하고 한 stage에서 다른 stage로 아티팩트를 복사할 수 있습니다.

기본 구조는 다음과 같습니다:

```Dockerfile
# --- Build Stage ---
# stage에 "builder"와 같은 이름을 지정합니다
FROM golang:1.21-alpine AS builder

# working directory 설정
WORKDIR /src

# 소스 복사 및 static 바이너리 빌드
COPY app/ .
# CGO_ENABLED=0은 'scratch'와 같은 최소 image에서 실행할 수 있는 static 바이너리를 생성합니다
RUN CGO_ENABLED=0 go build -o /app/server .


# --- Final Stage ---
# 최소 base image에서 새로운 깨끗한 stage 시작
FROM scratch

# "builder" stage에서 컴파일된 바이너리*만* 복사
COPY --from=builder /app/server /server

# 애플리케이션 port 노출
EXPOSE 8080

# 바이너리를 실행하도록 명령 설정
CMD ["/server"]
```
`scratch`를 사용하면 완전히 비어 있으므로 가능한 가장 작은 image가 됩니다. `alpine`도 shell이나 기타 기본 유틸리티가 필요한 경우 훌륭한 선택입니다.
