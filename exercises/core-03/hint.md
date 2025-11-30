다음 명령어들을 사용하여 실습을 완료하세요:

- **image를 빌드하려면:**
  `docker build -t <image-name> .`

- **container를 detached mode로 실행하려면:**
  `docker run -d --name <container-name> <image-name>`

- **container에서 로그를 가져오려면:**
  `docker logs <container-name>`

- **출력을 파일로 저장하려면 (리다이렉션):**
  `docker logs <container-name> > logs.txt`

시스템을 깔끔하게 유지하려면 container를 중지하고 제거하세요:
`docker stop <container-name>`
`docker rm <container-name>`
