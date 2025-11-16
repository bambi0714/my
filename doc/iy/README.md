# 아이☆치이 다운로드 방법
## 0. ffmpeg 사전 다운  👉️ [다운로드 방법](https://github.com/bambi0714/my/tree/main/doc/ffmpeg)
## 목차
<!-- TOC start -->
 * [영상 다운](#영상-다운)
 * [자막 다운](#자막-다운)
<!-- TOC end -->

## 영상 다운
### 1. 영상 페이지로 가서 F12 -> Consle 창으로 이동
콘솔 창 `>` 에 `allow pasting` 입력 후 엔터
<img width="934" height="90" alt="image" src="https://github.com/user-attachments/assets/792600c7-4820-4219-97cb-2df6676198f3" />

### 2. m3u8 파일 다운로드
콘솔 창에 아래 스크립트 내용에서 `파일제목`만 저장하고 싶은 파일명으로 변경해서 엔터 -> m3u8 확장자인 파일 다운로드됨.
```
(() => {
  const movie = window.playerObject.package.engine.movieinfo.current.vidl;
  let selected = null;
  for (const info of movie) {
    if (!info.playlist) continue;
    if (!info.playlist.urls.length) continue;
    if (selected?.vsize > info.vsize) continue;
    selected = info;
  }
  let m3u8 = `#EXTM3U
#EXT-X-TARGETDURATION:10
`;
  const qdpDict = selected.playlist.qdp;
  const durations = selected.playlist.durations;
  for (const [i, baseUrl] of selected.playlist.urls.entries()) {
    const qdpKey = baseUrl.split(".ts")[0].split("/").pop();
    const fullUrl = `https:${baseUrl}${qdpDict[qdpKey]}`;
    const duration = durations[i];
    m3u8 += `#EXTINF:${duration},
${fullUrl}
`;
  }
  m3u8 += "#EXT-X-ENDLIST";
  const blob = new Blob([m3u8], { type: "text/plain" });
  const a = document.createElement("a");
  a.href = URL.createObjectURL(blob);
  a.download = "파일제목.m3u8";
  a.click();
})()
```

### 3. m3u8 -> mp4로 다운로드
1. 다운로드한 m3u8 파일을 ffmpeg.exe가 있는 폴더로 이동 (시스템 환경 설정했으면 아무데나 가능)
2. 해당 폴더경로로 PowerShell 또는 CMD 열기
   - CMD 여는 법 : win + r 로 cmd 입력 후 엔터 ->뜨는 창에 `cd 이동할폴더경로(ex C:\Users\userName\Downloads)` 입력 후 엔터
     - 만약 이동할 폴더가 C드라이브가 아니면 `이동할드라이브명:`임력 후 입력 (ex D드라이브면의 ffmpeg폴더면 `D:`입력 후 엔터 -> `cd D:\ffmpeg`입력 후 엔터
3. 아래 명령어 입력 
```
ffmpeg -protocol_whitelist file,http,https,tcp,tls -i "파일제목.m3u8" -c copy -bsf:a aac_adtstoasc -c:s mov_text -metadata:s:s:0 language=ko -threads 4 -reconnect 1 -reconnect_streamed 1 -reconnect_delay_max 2 "파일제목.mp4"
```
  - 만약 CPU 성능이 너무 안좋아 PC가 버벅거리면 cntrl + c 키를 입력 다운로드를 중단한 후 `-threads 4` 부분의 숫자를 2로 줄여 다운로드하기
  * 다운로드시 아이☆치이는 uuid(사용자식별ID값)을 사용해 영상을 불러옴. 그래서 위의 명령어는 빠르게 다운로드 영상을 요청하는 방식으로, 영상을 많이 다운로드시 비정상적인 사용자로 인식할 수 있음... 

## 자막 다운
- 한국어 자막을 원할 경우 그대로 두고, 만약 영어 자막을 원하면 아래 스크립트에서 "if (sub._name !== "한국어") continue;"에서 `한국어`를 `영어`로 변경.
- "https://meta.video.iqiyi.com/" 
- 파일제목을 m3u8와 똑같이 변경
```
(async () => {
  const subtitles =
    window.playerObject.package.engine.movieinfo.current.subtitlesUrlMap.list;
  let output = "";
  for (const sub of subtitles) {
    if (sub._name !== "한국어") continue;
    if (!sub.webvtt) {
      alert("Unable to get subtitle file.");
    }
    const url = new URL(sub.webvtt, "https://meta.video.아이☆치이.com/");
    output = url.href;
  }
  const response = await fetch(output);
  if (!response.ok) {
    throw new Error("Something went wrong with the subtitles request.");
  }
  const text = await response.text();
  const blob = new Blob([text], { type: "text/plain" });
  const a = document.createElement("a");
  a.href = URL.createObjectURL(blob);
  a.download = "파일제목.vtt";
  a.click();
})();
```

