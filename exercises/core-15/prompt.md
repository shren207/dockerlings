Directory: exercises/core-15

컴파일된 애플리케이션(Go, Rust, C++ 등)을 빌드할 때, `Dockerfile`에는 종종 컴파일러와 빌드 도구가 포함된 전체 SDK가 필요합니다. 그러나 최종 container는 실행하기 위해 컴파일된 바이너리만 필요합니다. 전체 SDK를 최종 image에 포함하면 불필요하게 크기가 커지고 보안 공격 표면이 증가합니다.

**Multi-stage build**는 이 문제를 우아하게 해결합니다. 한 stage(예: `FROM golang AS builder`)를 사용하여 코드를 컴파일하고, 두 번째 별도의 stage(예: `FROM scratch`)를 사용하여 최종 최소 image를 생성하면서, 첫 번째 stage에서 *오직* 컴파일된 바이너리만 복사합니다.

## Your Task

이 디렉토리에 간단한 Go 웹 애플리케이션과 단일 stage로 빌드하는 `Dockerfile`이 있습니다.

**`Dockerfile`을 multi-stage build를 사용하도록 리팩토링**하세요.

1.  **첫 번째 stage** ("builder"):
    *   `golang` image로 시작해야 합니다 (예: `golang:1.21-alpine`).
    *   Go 애플리케이션 바이너리를 빌드해야 합니다.

2.  **두 번째 stage** ("final" image):
    *   `scratch` 또는 `alpine`과 같은 최소 base image로 시작해야 합니다.
    *   builder stage에서 컴파일된 바이너리를 최종 image로 복사해야 합니다.
    *   애플리케이션을 실행하도록 `CMD`를 설정해야 합니다.

검증 스크립트가 `Dockerfile`을 빌드하고 두 가지를 확인합니다: 결과 image가 원래 단일 stage 빌드보다 상당히 작은지, 그리고 내부 애플리케이션이 여전히 올바르게 실행되는지.
