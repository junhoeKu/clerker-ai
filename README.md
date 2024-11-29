# 📝 AI 모델을 활용한 회의 지원 솔루션 서비스 (Clerker - AI Team)
<img src="Picture Folder/Clerker_image.png" alt="Clerker" width="900"/>

## 🏅나의 역할
- **STT 로직 설계**
  - 한국어 텍스트 - **음성 데이터셋 수집, 전처리를 통해 새로운 데이터셋 제작** ([Dataset](https://huggingface.co/datasets/Junhoee/STT_Korean_Dataset))
  - 이후 **Whisper 모델로 Fine Tuning 진행**
  - Whisper는 화자분리 기능을 지원하지 않아 로직을 따로 설계해야 하며 도메인별 특화 데이터셋으로 각각 모두 학습시켜야 하는데 이 부분에서 데이터셋 제작에 한계를 느낌
  - **STT 성능도 API가 Fine Tuning보다 안정적이고 준수하며 메모리측면에서도 이득이기에 API를 활용하기로 결정**
  - Google STT, ReturnZero STT, Naver Clova 등 다양한 API를 실험해본 결과, 가격과 성능 그리고 무엇보다 키워드 부스팅 (도메인 특화 가능) 성능이 뛰어난 **Naver Clova API**로 결정.

- 요약 모델 및 최종 보고서 설계
  - 오픈소스 한국어 LLM인 [Bllossom](https://huggingface.co/MLP-KTLim/llama-3-Korean-Bllossom-8B)을 활용

## 🔍 프로젝트 소개  
- AI 모델을 활용한 회의 지원 솔루션 서비스 **Clerker**는 음성 및 화상 회의 내용을 자동으로 요약하여 직관적이고 효율적인 보고서를 생성하는 혁신적인 서비스입니다.  
  - Clerker 플랫폼 내에서 온라인 회의 (Google Meet)를 생성하면 화면 녹화 기능을 통해 해당 회의를 녹화합니다.
  - 녹화된 회의 영상을 바탕으로 회의록을 텍스트 및 다이어그램으로 요약합니다.
  - 회의만 해도 자동으로 보고서가 도출되는 편리한 서비스를 경험해보세요.

## 🤖 모델 관련  
- **STT 모델**  
  - Naver Clova API (CSR) 활용
  - 도메인 맞춤형 키워드 사전 제작 

- **청크 모델**  
  - 화자분리된 텍스트 파일을 주제에 맞게 적절한 청크로 분리
  - 키워드 추출 및 시각화 데이터 자동 생성
 
- **요약 모델**  
  - LLM을 활용하여 다이어그램 생성을 위한 청크별 요약 파일 생성
  - 보고서 생성을 위한 청크별 제목, 주요 키워드, 요약 3문장으로 정리

- **다이어그램 생성**  
  - LLM을 통해 청크별로 다이어그램화 할지 여부를 결정
  - 어떤 다이어그램으로 표현하는 것이 좋을지 결정
  - Mermaid Code 기반 다이어그램 생성


## 🎯 주요 성과  
- 요약 다이어그램 (프로젝트 로직)
<img src="Picture Folder/Diagram_example.png" alt="Clerker" width="900"/>


## 🚀 향후 계획  
- **실시간 회의 요약**  
  - 실시간 텍스트 변환 및 요약 기능 추가  
- **시각화 도구 강화**  
  - 더욱 정교한 다이어그램 및 데이터 시각화 기능 제공  
- **모바일 앱 개발**  
  - 모바일 환경에서도 회의 요약 서비스 사용 가능  


## 📚 참조  
- **참고 논문**: [llama](https://arxiv.org/abs/2302.13971)
