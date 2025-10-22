## 1. ffmpeg 설치 방법
## 목차
<!-- TOC start -->
 * [zip 파일 다운](#zip-파일-다운)
 * [사용방법1 (특정 폴더에서 사용 가능)](#사용방법1-특정-폴더에서-사용-가능)
 * [사용방법2 (특정 폴더에서 사용 가능)](#사용방법2-전체-폴더에서-사용-가능)
<!-- TOC end -->

## zip 파일 다운
1. [FFmpeg 공식페이지](https://www.gyan.dev/ffmpeg/builds/)로 이동
  
2. release builds 의 latest release에서 `.zip` 다운로드

  <img width="1090" height="272" alt="image" src="https://github.com/user-attachments/assets/b15e85f8-d4b6-4d10-85a0-762f0e4a9335" />

3. 원하는 곳에 해당 zip파일 압축 풀기
4. 압축을 풀면 ffmpeg~~폴더에 bin, doc 폴더등이 있고, bin 폴더에 들어가면 `ffmpeg.exe` 파일이 있으면 설치 완료 됨

<br>

## 사용방법1 (특정 폴더에서 사용 가능)

환경변수 설정 하지않고 `ffmpeg~~폴더/bin` 폴더에서만 사용 가능 (ffmpeg.exe 파일이 있는 곳에서만)
### 1. 사용시 cmd에서 해당 폴더로 이동 후 `./ffmpeg.exe` 명령어로 사용(윈도우 기준)
- ex) cmd에서 `./ffmpeg.exe -i "url" -c copy myviedo.mp4`로 사용

<br>

## 사용방법2 (전체 폴더에서 사용 가능)
환경변수 설정하고, PC 전체에서 사용가능함.
### 1. 윈도우검색(win키 누르기)에서 "환경 변수" 입력 ->  `시스템 환경 변수 편집` 클릭

   <img width="428" height="91" alt="image" src="https://github.com/user-attachments/assets/7da04351-e478-4cd2-a97d-84876c71cc8d" />

### 2. 환경 변수(N)... 클릭

   <img width="607" height="699" alt="image" src="https://github.com/user-attachments/assets/c1a961b3-ad75-403b-af2b-2c4008e302df" />
   
### 3. 시스템 변수(S) 에서 `Path`를 찾아 클릭 -> 편집(I) 버튼 클릭

<img width="612" height="703" alt="image" src="https://github.com/user-attachments/assets/265bcb60-f5e1-4085-816e-caa6fdf2aee8" />

  
### 4. `새로 만들기`를 누르고 ffmpeg의 bin 폴더 경로를 입력해준다. (`ffmpeg.exe` 파일이 있는 폴더 경로 입력) 후 `확인` -> `확인` -> `확인`

  <img width="664" height="657" alt="image" src="https://github.com/user-attachments/assets/8e33622a-4ea4-4c10-8caa-d715195a96eb" />

### 5. cmd 창을 열어 `ffmpeg -version` 입력해서 설치한 버전이 제대로 나오면 (빨간 글씨가 안나오면) 성공

   <img width="860" height="95" alt="image" src="https://github.com/user-attachments/assets/4e924391-efdc-4ef6-83b2-9ae03c88088c" />

### 6. 사용 방법 : cmd 창에서 자신이 원하는 폴더 어디든지 이동해서 `ffmpeg` 명령어로 사용
   - ex) ffmpeg -i "url" -c copy myviedo.mp4"

