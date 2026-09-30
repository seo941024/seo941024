# 안녕하세요. 서지섭입니다.

---

## About Me
- 컴퓨터 비전 · 데이터 분석 중심으로 공부하고 있습니다
---

## Tech Stack

[![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://github.com/seo941024/Python-GUI)
[![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white)](https://github.com/seo941024/LPR_System)
[![OpenCV](https://img.shields.io/badge/OpenCV-5C3EE8?style=for-the-badge&logo=opencv&logoColor=white)](https://github.com/seo941024/LPR_System)
[![SQL](https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=sqlite&logoColor=white)](https://github.com/seo941024/LPR_System)
[![Java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=java&logoColor=white)](https://github.com/seo941024/Java)
[![HTML](https://img.shields.io/badge/HTML-E34F26?style=for-the-badge&logo=html5&logoColor=white)](https://github.com/seo941024/Web-practice)

---

## 대표 프로젝트

# LPR_System — 번호판 인식 주차 관리 시스템
https://github.com/seo941024/LPR_System

YOLOv11m 객체 검출 + PaddleOCR 문자 인식 + ByteTrack 실시간 추적을 결합해
주차장 입출차를 자동 관리하고, 축적된 로그를 SQL로 분석해 대시보드로
시각화하는 End-to-End 프로젝트입니다.

**사용 기술**
`Python · PyTorch · YOLOv11 · PaddleOCR · ByteTrack · PyQt6 · SQLite · SQL(Window Function/CTE) · Streamlit · Plotly`

**핵심 기능**
- AIHub 데이터 10만 장으로 YOLOv11m 번호판 검출 모델 직접 학습 (mAP@0.5 0.931)
- ByteTrack으로 검출 객체를 실시간 추적, GPU(검출)/CPU(OCR) 파이프라인 분리로 프레임 끊김 없이 처리
- PaddleOCR 기반 한국어 번호판 인식, 화이트/블랙리스트 관리, 요금 자동 계산
- 입출차 로그를 SQL(LAG 윈도우 함수, CTE)로 분석해 방문 추이·피크타임·매출·재방문 패턴을 Streamlit 대시보드로 시각화
- 동일 데이터셋을 SQLite · Power BI · Power Query · Databricks(PySpark/Spark SQL)로도 탐색해 다양한 데이터 도구 학습

**기술적 문제 해결**
- YOLO(torch-GPU)와 PaddleOCR(paddle-GPU)의 CUDA 심볼 충돌 → OCR을 CPU 전용으로 분리해 안정적 공존 구조 설계
- 학습 데이터(부감 각도)와 실제 배포 환경 간 도메인 불일치를 실측 검증으로 규명
- SQL 분석 대시보드의 의존성 충돌(protobuf)을 발견, 별도 가상환경으로 격리해 기존 앱에 영향 없이 기능 확장

**성과 수치**
- YOLOv11m mAP@0.5 93.1%
- 합성 4주 데이터 기준 입출차 1,094건 분석, SQL 쿼리 7종 (윈도우 함수/CTE)

---

## 다른 프로젝트

### Python 프로젝트
https://github.com/seo941024/Python
- 게임 내 희귀 확률(0.2%) 가챠 모델을 n회 시행으로 정의, 100만 회 Monte Carlo 시뮬레이션을 통해 기대값 및 획득 분포를 추정한 프로젝트 제작

### Bowling Score Board
https://github.com/seo941024/Python-GUI
- Python · Flet으로 구현한 볼링 점수판 GUI. 스트라이크/스페어 자동 판별, 실시간 프레임 점수 계산

### Java 프로젝트
https://github.com/seo941024/Java
- Java 기초 문법 및 객체지향 개념 학습 프로젝트

### HTML 연습 프로젝트
https://github.com/seo941024/Web-PRG
- HTML/CSS 기반 웹페이지 제작 (벚꽃 축제 테마 UI)

---

## GitHub Stats

![GitHub stats](https://github-readme-stats.vercel.app/api?username=seo941024&show_icons=true&theme=graywhite)

![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=seo941024&layout=compact&theme=graywhite)

---

## Contact
- Email: seo941024@gmail.com
