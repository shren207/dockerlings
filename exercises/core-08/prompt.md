Directory: exercises/core-08

container는 일시적(ephemeral)입니다. 즉, 내부에서 수행한 모든 변경 사항은 container가 제거되면 사라집니다. 데이터베이스와 같은 애플리케이션의 경우 데이터가 유지되어야 합니다. 이 실습에서는 **volume**이 host 머신의 디렉토리를 container 내부의 디렉토리에 연결하여 이 문제를 어떻게 해결하는지 보여줍니다.

## Your Task

영구적인 PostgreSQL 데이터베이스를 생성하세요. container를 실행하고, 데이터를 추가하고, container를 제거한 다음, 데이터가 host 머신에 여전히 안전하게 있는지 확인합니다.

1.  host 머신에 `pgdata`라는 **디렉토리를 생성**합니다. 이 디렉토리에 데이터베이스 파일이 저장됩니다.
    ```bash
    mkdir pgdata
    ```

2.  **`postgres:16` container를 실행**합니다. 이름을 `c8-postgres`로 지정하고, volume을 사용하여 `pgdata` 디렉토리를 container의 데이터 디렉토리(`/var/lib/postgresql/data`)에 마운트하세요.
    *(처음에는 데이터베이스 초기화를 위해 15-20초 정도 기다리세요.)*

3.  `docker exec`를 사용하여 container 내부에서 `psql` 클라이언트를 실행하여 **테이블을 생성**합니다. 테이블 이름은 `dvd_rentals`로 지정하세요.

4.  새 테이블에 **행을 삽입**합니다. 행에는 `The Grand Budapest Hotel`이라는 제목이 포함되어야 합니다.

### "아하" 순간 (적극 권장)

이것이 volume의 핵심 개념입니다. 실제로 확인하려면:

1.  **container를 중지하고 제거**: `docker stop c8-postgres && docker rm c8-postgres`.
2.  container는 사라졌지만, host의 `pgdata` 디렉토리는 남아 있습니다.
3.  *정확히 같은 `docker run` 명령어*를 사용하여 **새 container를 실행**합니다.
4.  **데이터 확인**: 이 새 container에 `exec`로 접속하여 `SELECT * FROM dvd_rentals;`를 실행합니다. 이전에 추가한 영화 제목이 다시 나타나는 것을 볼 수 있습니다!

### 최종 상태

실습을 완료하려면, checker가 `dvd_rentals` 테이블과 올바른 행이 있는 데이터베이스가 포함된 `pgdata` 디렉토리를 찾아야 합니다. checker는 `pgdata` 디렉토리 자체만 검사하므로 **container를 실행 중이거나 중지된 상태로 둘 수 있습니다**.
