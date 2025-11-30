Directory: exercises/core-09

volume은 데이터를 유지하는 데 훌륭하지만, 애플리케이션을 개발할 때는 어떨까요? 코드 한 줄을 변경할 때마다 image를 다시 빌드하고 싶지 않을 것입니다.

이때 **bind mount**가 필요합니다. bind mount는 host 머신의 디렉토리나 파일을 container에 직접 연결합니다. host에서 수행한 모든 변경 사항이 container 내부에 즉시 반영되어, 라이브 개발 워크플로우에 완벽합니다.

## Your Task

`nginx` container를 실행하고 제공된 `app` 디렉토리에서 간단한 정적 웹사이트를 서빙하세요. 핵심은 bind mount를 사용하여 host 머신의 웹사이트 변경 사항이 재시작이나 재빌드 없이 즉시 반영되도록 하는 것입니다.

1.  **`app/index.html` 파일을 살펴보세요**. 이것이 서빙할 파일입니다.

2.  **`nginx` container를 실행합니다**.
    - 이름을 `c9-dev-server`로 지정합니다.
    - host port `8009`를 container port `80`에 매핑합니다.
    - **중요하게**, 로컬 `./app` 디렉토리를 container 내부의 Nginx 웹 루트 디렉토리(`/usr/share/nginx/html`)에 매핑하는 bind mount를 생성합니다. 정적 콘텐츠 서빙의 모범 사례를 따르기 위해 read-only로 설정하세요.

3.  **작동 확인**. container가 실행되면 `curl http://localhost:8009`로 내용을 확인합니다. "Version 1" 제목이 보여야 합니다.

### 좋은 관행: Live Reload 테스트

이것이 bind mount의 핵심 이점입니다. 개발 설정이 예상대로 작동하는지 확인하는 것이 좋은 관행입니다. 실제로 확인하려면:

1.  로컬 머신에서 텍스트 편집기로 `app/index.html` 파일을 엽니다.
2.  `<h1>` 태그 내부의 텍스트를 "Version 1"에서 "My Live Update!"로 변경합니다.
3.  파일을 저장합니다.
4.  **container를 재시작하지 않고** `curl http://localhost:8009`를 다시 실행합니다. container에서 새 메시지가 즉시 서빙되는 것을 볼 수 있습니다.

**실습을 완료하려면 container를 실행 상태로 두세요.** checker가 자동으로 유사한 테스트를 수행하여 솔루션을 검증합니다.
