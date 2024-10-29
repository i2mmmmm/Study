## Anthropic 에서 computer use 기능 출시
- 웹브라우저 제어 및 검색
- 스프레드시트 작성 및 편집
- PDF 문서 읽기
- 계산기 사용
- 터미널 명령어 실행
- 특이점: 로봇이 아닙니다 검사 해결, 현재 속도는 느림

https://github.com/anthropics/anthropic-quickstarts 포크 🍴
- streamlit, docker 컨테이너로 실행 중 docker 가 빠름

## docker 컨테이너로 실행하기  
- https://github.com/anthropics/anthropic-quickstarts/blob/main/computer-use-demo/Dockerfile

**1. 이 파일 이용해서 도커 이미지 빌드**  

**2. mirror server 추가**  

```
RUN sed -i 's@archive.ubuntu.com@mirror.kakao.com@g' /etc/apt/sources.list && \
    sed -i 's/ports.ubuntu.com/mirror.yuki.net.uk/g' /etc/apt/sources.list && \
    apt-get update
```
  (우분투 이미지는 미국 서버에서 패키지를 받아오기 때문에 속도가 느림  
    -> dockerfile을 사용해 ubuntu를 base 이미지로 하는 이미지를 생성할 때, 한국 미러에서 패키지를 받도록 설정  
    -> 빨라짐)  
**3. 한글 폰트 사용**
```
# 나눔고딕 폰트
RUN apt-get update && apt-get install -y fonts-nanum && fc-cache -f -v
```

**4. 설치하기**

computer-use-demo 폴더로 가서 setup.sh 실행

```
./setup.sh
export ANTHROPIC_API_KEY= (나의 API key)
ls (뒤로 가서)
docker build . -t computer-use-demo:local  (도커 이미지 생성)
docker run \ (도커 실행)
-e ANTHROPIC_API_KEY = $ANTHROPIC_API_KEY \
-v $(pwd)/compuer_use_demo:/Users/mm/마운트 시킬 폴더 \
-v $HOME/.anthropic:/Users/mm/.anthropic \
-p 5900:5900 \
-p 8501:8501 \
-p 6080:6080 \
-p 8080:8080 \
-if computer-use-demo:local
```

도커실행되고 8080번 포트에서 접속할 수 있는 url 나오면 클릭  
-> Claude Computer Use Demo 창이 나오고 리눅스 PC 나옴  
-> 오른쪽 상단에 Toggle Screen Control(Off) -> ON으로 바꾸기  
-> 명령어 입력  
-> **스크린샷을 엔트로픽 서버에 보내서 분석하고 응답을 주는 형식으로 진행됨**

