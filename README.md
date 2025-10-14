# 태드 플랫폼 영상 및 자막 다운 (2024-10-15일 기준)
## 사전에 할일
- ffmpeg 다운로드 👉️ [다운로드 방법] 

[https://github.com/FFmpeg/FFmpeg](https://www.gyan.dev/ffmpeg/builds/)
태드플렛폼다운로드 방법

## 목차
<!-- TOC start -->
- [위티비 (2025-10-15일 기준)](#위티비-2025-10-15일-기준)
   * [영상 다운](#영상-다운)
   * [자막 다운](#자막-다운-자막은-영상에서-선택한-자막으로-다운됨)
<!-- TOC end -->

## 위티비 (2025-10-15일 기준)
### 영상 다운
1. 다운로드 받고 싶어하는 영상 재생 페이지로 이동 후 `F12`키 누르면 아래 사진 처럼 오른쪽에 탭창(개발자모드)가 뜸. 이후 `F5`키 눌러서 페이지 새로고침하기
   
  ![0](https://github.com/user-attachments/assets/53b34718-0cb9-4d6f-80f7-90d6f96bc443)

2. (영상이 재생된다면 상관 없음) 여기서 현재 영상이 재생이 안되고 `Paused in debugger` 가 애래 그림처럼 뜬다면, `❚▶`버튼을 영상이 재생될때 까지 클릭
   
  ![1](https://github.com/user-attachments/assets/5c85eb75-2ca6-40ea-8199-50a6e9373617)

3. 영상이 재생되면 영상을 정지하고, 오른쪽 창(개발자모드)의 맨 위에를 보면 `Network`탭 클릭

  ![2](https://github.com/user-attachments/assets/b6c76aea-6e1d-4ae7-be88-28e29e01d3db)

4. `m3u8`를 아래 사진 처럼 입력(1번)하면 Name이 `~~ tx.m3u8 ~~` 이렇게 되어 있는 것을 우 클릭 -> copy -> copy URL로 url 복사 (자막 다운받을려면 해당 창 닫지 말기!)
    - **잘 모르겠으면 뜨는 것 중에 아래 사진의 아이콘과 같은거 선택(빈 페이지 모양)**

  ![3-1](https://github.com/user-attachments/assets/76b1bd36-b4eb-498e-9ada-9c31b26ba583) ![3-2](https://github.com/user-attachments/assets/8e697107-3ee1-43f6-b328-a7ee85493d61)


5. ffmpeg 다운로드한 폴더로 이동 -> bin 폴더로 이동 -> `Shift`키 + 마우스 우클릭 -> `"여기서 PowerShell 창 열기"` 클릭 -> 파란창 나옴.

  ![cmd1](https://github.com/user-attachments/assets/09129e37-2a53-4176-bd50-0c2779c33116)

6. 아래 명령어 입력 후 엔터하면 다운로드됨. 빨간 글자 안뜨면 성공 (안되면 `./` 빼고 입력). bin 폴더에 다운되어 있는 것을 볼 수 있음.
```
./ffmpeg.exe -i "[복사한 url 주소]" -c copy [저장할 동영상 이름].mp4
```

  ![cmd2](https://github.com/user-attachments/assets/ed65c083-af0c-43e3-800b-6dd9c3555f9d)
  ![complet](https://github.com/user-attachments/assets/8cd58dd2-39a2-43f0-978c-253f18c85a67)


### 자막 다운 (자막은 영상에서 선택한 자막으로 다운됨)
1. 영상 다운 방법의 4단계서 m3u8대신 `vtt` 입력 후 똑같이 url 복사

 ![vtt1](https://github.com/user-attachments/assets/c39323a5-2a2c-47ff-96a1-2587370485ff)

2. **다운받는 자막이 영어 자막**이면 해당 url로 이동 -> 페이지에서 우클릭 -> 다른 이름으로 저장 -> 저장할때 파일 형식을 모든 형식(*)으로 바꾸고 `[자막파일명].vtt로 저장`
3. **영어자막 외**는 아래 과정 수행
4. [https://hoppscotch.io](https://hoppscotch.io)로 이동
5. 1에 복사한 url 입력 -> 헤더 탭 클릭 -> `Key`에 "Content-Type", `값`에 "charset=utf-8"입력

  ![restApI1](https://github.com/user-attachments/assets/0b914bb8-e36b-4137-a617-669be6795426)

6. 보내기 누르면 아래 사진처럼 뜸. 다운로드 누르면 txt 파일로 다운로드 됨 -> 해당 파일로 vtt로 변경(이름 바꾸기로 txt확장자 vtt로 변경)

![restApI2](https://github.com/user-attachments/assets/e2f9078c-d5ec-4d4b-b07a-367a33488e4b)


