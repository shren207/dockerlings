# Dockerlings
**재미있고 인터랙티브한 방식으로 Docker 배우기 – 직접 해보면서 학습**

---

[![asciicast](https://asciinema.org/a/758902.svg)](https://asciinema.org/a/758902)

---

- **100% 인터랙티브 TUI** – Bubble Tea로 구현된 아름다운 터미널 인터페이스
- **즉각적인 검증** – `check`를 실행하면 즉시 정답 여부를 확인
- **점진적 커리큘럼** – 서로 연계된 15개 이상의 세심하게 설계된 실습
- **실무 기술** – 기본 image부터 multi-stage build, volume, network, Compose까지
- **간편한 시작** – clone하고, build하고, 바로 학습 시작

---

## 학습 내용

| 실습 | 배우게 될 내용 |
|--------------|---------------------------------------------------------------------------------|
| core-01–04   | container 실행, logs, exec, 파일 작업 |
| core-05–07   | Dockerfile 작성, COPY, EXPOSE, ENV, LABEL |
| core-08–09   | 영구 volume & 실시간 리로딩 bind mount |
| core-10–11   | container 네트워킹과 port publishing |
| core-12–14   | Docker Compose, 다중 서비스 앱, named volume, custom network |
| core-15      | 작고 안전한 프로덕션 image를 위한 multi-stage build |

## 30초 만에 시작하기

> `go`와 `docker`가 설치되어 있어야 합니다.

```bash
git clone https://github.com/furkan/dockerlings.git
cd dockerlings
go build -o bin/dockerlings ./cmd/dockerlings
./bin/dockerlings watch
```

↑↓로 이동 • c로 솔루션 확인 • h로 힌트 보기 • q로 종료

## 솔루션 수동 테스트 (선택 사항)

```bash
cd exercises/core-01
bash check.sh   # 상세한 피드백 확인
```

## 대상

- Docker 명령어를 이해하고 싶은 초보자
- 실무 container 워크플로우를 준비하는 중급 개발자
- 직접 부수고 고치면서 배우는 것을 좋아하는 모든 분
