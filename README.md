# 👋 안녕하세요. 서지섭입니다.

## 🙋‍♂️ About Me
- 🌱 Python 공부 중
- 💻 백엔드 개발자 목표
- 🚀 꾸준히 성장하는 개발자

---

## 🛠 Tech Stack
[![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://github.com/seo941024/Python-GUI)
[![Java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=java&logoColor=white)](https://github.com/seo941024/Java)
[![HTML](https://img.shields.io/badge/HTML-E34F26?style=for-the-badge&logo=html5&logoColor=white)](https://github.com/seo941024/Web-practice)

---

## 🚀 Projects

### 🐍 Python 프로젝트  
👉 https://github.com/seo941024/Python-GUI  

![preview](https://via.placeholder.com/600x300)

**📌 설명**  
- 간단한 GUI 프로그램 제작  
- 사용자 입력 처리 및 화면 출력 구현
- 게임 아이템 뽑기 확률 시뮬레이션 제

**⚙️ 사용 기술**  
- Python  

**🧠 배운 점**  
- 이벤트 기반 처리 흐름 이해  
- 사용자 인터페이스 설계 기초 경험

👉 Python 기반 확률 시뮬레이션 프로젝트

![preview](https://raw.githubusercontent.com/seo941024/Python-GUI/master/result.png)

**📌 설명**  
- 11회 뽑기를 여러 번 반복하여 자석펫 획득 확률 계산  
- 몬테카를로 방식으로 확률 실험 구현  
- 최대 획득 개수 제한 적용  

**⚙️ 사용 기술**  
- Python  
- random 모듈  
- Monte Carlo Simulation  

**💻 핵심 코드**
import random

trials = 1000000
max_pet = 5
single_prob = 0.03

n = int(input("11회 뽑기 횟수 입력: "))

counts = [0] * (max_pet + 1)

for _ in range(trials):
    pets = 0
    for _ in range(n * 11):
        if pets < max_pet and random.random() < single_prob:
            pets += 1
    counts[pets] += 1

probabilities = [c / trials * 100 for c in counts]

for i in range(max_pet + 1):
    print(f"{i}개: {probabilities[i]:.2f}%")

**🧠 배운 점**  
- 확률 시뮬레이션 구조 이해  
- 랜덤 기반 모델링 경험  
- 게임 확률 분석 방식 학습  

---

### ☕ Java 프로젝트  
👉 https://github.com/seo941024/Java  

![preview](https://via.placeholder.com/600x300)

**📌 설명**  
- Java 기초 문법 기반 프로젝트  
- 객체지향 개념 적용  

**⚙️ 사용 기술**  
- Java  

**🧠 배운 점**  
- 클래스/객체 구조 이해  
- 프로그램 흐름 설계 능력 향상  

---

### 🌐 HTML 연습 프로젝트  
👉 https://github.com/seo941024/Web-practice  

## 📸 실행 화면

![preview](https://raw.githubusercontent.com/seo941024/Web-practice/master/chap13_source/labs/images/webpage.png)

- HTML/CSS 기반 웹페이지 제작  
- 벚꽃 축제 테마 UI 디자인 구현  
- 사용자 친화적 레이아웃 구성 

**📌 설명**  
- 기본 웹 페이지 제작  
- 레이아웃 구성 연습  

**⚙️ 사용 기술**  
- HTML  

**🧠 배운 점**  
- 웹 구조 이해  
- UI 구성 기초 학습  

---

## 📊 GitHub Stats
![GitHub stats](https://github-readme-stats.vercel.app/api?username=seo941024&show_icons=true&theme=graywhite)

![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=seo941024&layout=compact&theme=graywhite)

---

## 📫 Contact
- Email: seo941024@gmail.com
