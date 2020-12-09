# download-rtmp-video-by-ffmpeg

## 목차
1. [영상 주소 찾기](#영상-주소-찾기)
2. [ffmpeg 명령어 작성](#ffmpeg-명령어-작성)
3. [실행](#실행)

4. [기타 문제 해결](#기타-문제-해결)
---

### 영상 주소 찾기
1. [이러닝 사이트](https://e-campus.gnu.ac.kr)에 접속합니다.  
2. 다운로드를 원하는 강의를 엽니다. (flowPlayer로 재생되는 강의 한정)  
3. 페이지의 빈 곳에 마우스 우클릭으로 `페이지 소스 열기` 메뉴 를 선택합니다.  
    - [자세한 방법](how-to-get-rtmp.md)  
4. 찾은 구문에서 주소를 골라냅니다.  
    - ` rtmp:// ` 부터 ` media.MP4 ` 까지입니다.  
    - 이런 형태이면 찾은 것입니다. `rtmp://200.255.1.111:1935/vod/_definst_/mp4:/ASP00001/2020/20/202020UU00AAA00000000_V/1_1_12345/media.mp4` 

### ffmpeg 명령어 작성
1. 메모장 또는 사용하시는 TextEditor를 엽니다.  
2. 아래 부분을 복사해서 붙여넣습니다.  
```batch
ffmpeg.exe -y -i "여기에 rtmp주소를 입력" -vcodec copy -acodec copy "저장할 파일 이름 1-1.mp4"
```
3. "여기에 rtmp 주소를 입력" 대신에 위에서 찾은 rtmp 주소를 넣으면 됩니다.  `예시`
```batch
ffmpeg.exe -y -i "rtmp://200.255.1.111:1935/vod/_definst_/mp4:/ASP00001/2020/20/202020UU00AAA00000000_V/1_1_12345/media.mp4" -vcodec copy -acodec copy "저장할 파일 이름 1-1.mp4"
```
  - 저장할 파일 이름에 전체 경로를 지정해주는 경우, 해당 경로에 다운로드가 됩니다. 
  - 파일 이름만 지정해주는 경우 bat 파일의 경로에 저장이 됩니다.
    
4. 메모장 파일을 `원하는이름.bat`으로 저장합니다.

### 실행
1. 작성한 bat 파일을 다운로드 받은 [ffmpeg 파일](https://github.com/yoolisel/download-rtmp-video-by-ffmpeg/raw/master/ffmpeg.exe)과 같은 경로에 둡니다.  
2. bat 파일을 더블클릭해 실행합니다.  
3. 다운로드가 되기를 기다립니다.  
  
<img src="/Images/ffmpeg.png" width="600">  
  
빨간 박스쳐진 부분이 다운로드 받아진 시간입니다.
거의 영상 길이만큼 소요되니 미리미리 받아두는게 좋습니다.

---

### 기타 문제 해결
- 폴더 구조
<img src="/Images/directory.png">  
- youtube 영상인 경우 유튜브주소 앞에 ss 넣기.  
  - www . youtube . com/watch?v=XpPH6C0jbik -> www . **ss**youtube .com/watch?v=XpPH6C0jbik  
- 자동으로 출석 시간을 채워주지는 않습니다.

### Disclaimer
- 영상의 저작권은 영상 제공자에게 있고, 무단 사용으로 발생하는 모든 문제는 사용자에게 있습니다.
- 1회 출석, 1회 다운로드시 총 2번 영상을 시청하는 만큼의 서버리소스를 요구합니다. 온라인으로 2번 시청하는것과 유사한 트래픽만을 유발합니다.
- 2021년에는 e-campus의 개편이 있다고 합니다. 
