# Ensemble Creation - 국악기 기반 MIDI 및 오디오 합주 생성

## 프로젝트 개요
**Ensemble Creation**은 사용자가 업로드한 국악기 음원을 기반으로 자동으로 합주를 생성하는 Flask 웹 애플리케이션입니다.
이 프로젝트는 노이즈 감소, MIDI 변환, 다양한 악기 추가 기능을 제공하여 더욱 풍부한 음악을 만들 수 있도록 합니다.

## 주요 기능
- **오디오 업로드 및 처리**
  - 사용자가 오디오 파일 업로드 (`/upload_audio` API)
  - 노이즈 감소 및 음질 개선 (`/process_audio` API)

- **MIDI 변환 및 합성**
  - 업로드된 오디오를 분석하여 MIDI 변환
  - 다양한 악기 추가 (기타, 바이올린, 첼로, 플루트, 오보에 등)
  - 드럼 및 패드 사운드 추가 가능
  - 최종적으로 여러 WAV 파일을 병합하여 완성된 합주 생성

## 프로젝트 구조
```
Ensemble_creation2/
│── app.py  # Flask 웹 애플리케이션 실행 파일
│── g_midi.py  # MIDI 변환 및 합성 기능 구현
│── process_audio.py  # 오디오 노이즈 감소 기능 구현
│── instrument.html  # 악기 선택 관련 웹 페이지
│── requirements.txt  # 필요 라이브러리 목록
│── static/audios/  # 국악기 음원 저장 폴더
└── __pycache__/  # Python 캐시 파일
```

## 설치 및 실행 방법
1. **필수 라이브러리 설치**
    ```bash
    pip install -r requirements.txt
    ```
2. **Flask 애플리케이션 실행**
    ```bash
    python app.py
    ```
3. **웹 브라우저에서 접속**
    - 오디오 업로드 페이지: [http://127.0.0.1:5000/upload_audio](http://127.0.0.1:5000/upload_audio)
    - 합주 생성 페이지: [http://127.0.0.1:5000/process_audio](http://127.0.0.1:5000/process_audio)

## 필요 라이브러리
- `Flask`
- `pydub`
- `mido`
- `numpy`

## API 사용 방법
### 1. 오디오 업로드 (`POST /upload_audio`)
- **요청 형식**:
    ```json
    {
        "file": "recorded_audio.wav"
    }
    ```
- **응답 예시**:
    ```json
    {
        "message": "File uploaded successfully",
        "file_path": "static/uploads/recorded_audio.wav"
    }
    ```

### 2. 합주 생성 (`POST /process_audio`)
- **요청 형식**:
    ```json
    {
        "file_path": "static/uploads/recorded_audio.wav"
    }
    ```
- **응답 예시**:
    ```json
    {
        "message": "Audio processed successfully",
        "output_path": "static/processed/ensemble.wav"
    }
    ```

## 기여 방법
1. 본 레포지토리를 포크합니다.
2. 새로운 브랜치를 생성합니다.
3. 변경 사항을 커밋하고 푸시합니다.
4. Pull Request를 생성하여 기여합니다.

## 라이선스
이 프로젝트는 MIT 라이선스를 따릅니다.

