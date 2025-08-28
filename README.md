# 🦷 ToothAI Documentation

이 레포는 **ToothAI 프로젝트**의 문서 전용 저장소입니다.  
실제 코드는 각 기능별 레포에서 확인하실 수 있습니다:

- [Frontend (Flutter)](https://github.com/HoJun-7/toothai-frontend)  
- [Backend (Flask + DB)](https://github.com/HoJun-7/toothai-backend)  
- [AI Models (YOLOv8/v11)](https://github.com/HoJun-7/toothai-ai)  

---

## 📌 프로젝트 개요
### 배경
- 치과 진료는 사전 상담이 어려워, 통증이 심해질 때까지 병원에 가지 않는 경우가 많음  
- 고령자, 아동 보호자, 지방 거주자는 병원 접근성이 낮아 적기 진료 어려움  
- 환자는 진단 결과 이해가 어렵고, 의사는 사전 정보 부족으로 어려움  

### 목적
- **AI 진단 + 비대면 문진 + 실시간 알림 시스템**으로 진료 선행 단계 자동화 및 효율화  
- 환자는 집에서 사진과 문진을 입력 → 진단 결과 & 의사 응답 빠른 확인  
- 의사는 요청 도착 즉시 알림 → AI 진단 + 문진을 함께 참고해 효율적 응답 

---

## ✨ 핵심 기능
### 🧑‍⚕️ 환자 (Flutter 앱)
- 회원가입 / 로그인 / 프로필 관리
- 문진 작성 (Likert 척도 기반)
- 치아 이미지 업로드 (일반 / X-ray)
- AI 진단 결과 확인 (질병 / 위생 / 치아번호)
- 원격 진료 신청 & 이력 확인
- 알림: 진료 응답 도착 시 앱 내 알림 표시

### 👨‍⚕️ 의사 (Flutter 웹)
- 환자 진료 요청 목록 확인
- AI 진단 + 문진 통합 결과 확인
- 진단 의견 작성 및 전송
- 환자별 진단 이력 열람
- 알림: 요청 도착/응답 상태 실시간 처리 

---

## 🛠 기술 스택 & 아키텍처
### Frontend
- Flutter
- GoRouter, Provider
- JWT 기반 인증/토큰 관리
- 이미지 업로드 + 문진 응답 동시 처리
- 마스크 오버레이 UI
- 알림 시스템 (비동기 API polling)

### Backend
- Flask (REST API)
- JWT 인증
- 사용자 정보, 문진, 진단 요청, AI 결과, 알림 상태 관리
- `/consult/status`, `/consult/active`, `/consult/cancel` 등 API 제공

### Database
- **MongoDB**: AI 추론 결과, 진료 요청/응답/알림 상태  
- **MySQL (SQLAlchemy)**: 사용자 정보, 문진 응답

### AI & 외부 연동
- YOLO 기반 AI 모델 3종 (질병, 위생, 치아번호)
- Google Vertex AI – Gemini API 연동 (AI 진단 요약 설명 생성) 

### 아키텍처 개요
