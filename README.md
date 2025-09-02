# 말로 하는 음성 방탈출 게임

## 📜 프로젝트 소개

이 프로젝트는 사용자가 목소리만으로 즐길 수 있는 대화형 방탈출 게임입니다. 게임 마스터(GM) 역할을 하는 AI가 음성으로 상황을 설명하고 사용자의 음성 명령을 인식하여 게임을 진행합니다.

## ✨ 주요 기능

-   **음성 인식**: 사용자의 목소리를 텍스트로 변환하여 게임 명령으로 사용합니다.
-   **AI 게임 마스터**: OpenAI의 gpt-5-mini 모델이 게임 시나리오를 동적으로 생성하고 사용자의 행동에 대한 결과를 묘사합니다.
-   **음성 나레이션**: Google의 Gemini TTS (Text-to-Speech) 모델이 게임 마스터의 설명을 생생한 목소리로 들려줍니다.
-   **완전 몰입형**: 키보드나 마우스 없이 오직 목소리로만 게임에 몰입할 수 있습니다.

## 🛠️ 사용된 기술

-   **AI/LLM**:
    -   OpenAI gpt-5-mini (게임 로직 및 스토리 진행)
    -   Google Gemini 2.5 Flash Preview TTS (나레이션 음성 합성)
-   **Speech-to-Text**: `speech_recognition` 라이브러리 (Google Web Speech API)
-   **Python Libraries**:
    -   `openai`
    -   `google-generativeai`
    -   `SpeechRecognition`
    -   `pyaudio` (마이크 사용을 위해 필요)
    -   `python-dotenv` (API 키 관리)
    -   `jupyter` (노트북 환경)

## ⚙️ 설치 및 실행 방법

### 1. 사전 준비

-   Python 3.8 이상이 설치되어 있어야 합니다.
-   마이크가 컴퓨터에 연결되어 있어야 합니다.

### 2. 라이브러리 설치

아래 명령어를 사용하여 필요한 Python 라이브러리를 설치합니다.

```bash
pip install -q -U google-generativeai openai speechrecognition python-dotenv pyaudio
```

### 3. API 키 설정

프로젝트 루트 디렉터리(`speech_to_escape_room` 폴더)에 `.env` 파일을 생성하고, 아래와 같이 OpenAI와 Google Gemini API 키를 입력합니다.

```
OPENAI_API_KEY="여기에_당신의_OPENAI_API_키를_입력하세요"
GEMINI_API_KEY="여기에_당신의_GEMINI_API_키를_입력하세요"
```

### 4. 게임 실행

1.  Jupyter Notebook을 실행합니다.
2.  `speech_to_escape_room.ipynb` 파일을 엽니다.
3.  노트북의 셀을 위에서부터 차례대로 실행합니다.
4.  게임이 시작되면, '말할 준비가 완료되면 아무 키를 누르세요'라는 메시지가 나타납니다. (q를 입력하면 종료)
5.  아무 키를 누르고 Enter 키를 친 후, 마이크에 대고 원하는 행동을 말하세요. (예: "주변을 둘러봐", "책상을 살펴봐")

## 📁 파일 구성

-   `speech_to_escape_room.ipynb`: 게임의 전체 코드가 포함된 메인 Jupyter Notebook 파일입니다.
-   `output.wav`: AI 나레이션 음성이 임시로 저장되는 파일입니다.
-   `.env` (생성 필요): API 키를 보관하는 환경 변수 파일입니다.
-   `README.md`: 프로젝트에 대한 설명 파일입니다.

## 향후 보안 사항

- TTS 모델 변경: `gemini-2.5-flash-preview-tts` 모델은 무료 api키에서 하루 15번 요청 가능.. <br>`gemini-live-2.5-flash-preview` 로 변경 예정
- streamlit 구현: streamlit에서 나레이션과 함께 시각적으로 볼 수 있는 퍼즐이나 단서 등을 구현해보고 싶다.
- prompt 보안: prompt를 열심히 써봤는데 아직도 가끔 말을 듣지않을 때가 있다. <br>추가해야 할 것 이나, 보안해야 할 부분 찾아 봐야겠다.
- 텍스트생성 모델 변경: OpenAI API로 gpt-5-mini 모델을 구동하는데 쓸 때마다 과금이 될 수 밖에 없는 구조.. <br>무료 API나 HuggingFace를 이용하여 최적의 모델을 찾아서 변경하고 싶다.
