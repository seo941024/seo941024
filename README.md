# 👋 안녕하세요. 서지섭입니다.

---

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

---

### 🐍 Python 프로젝트 (대표 프로젝트)
👉 https://github.com/seo941024/Python-GUI  

### 💻 핵심 코드

```python
import random

trials = 1000000
max_pet = 8 #최대 계산하는 당첨 마릿수
single_prob = 0.03 #뽑기 당첨 확률

# 11회 뽑기 횟수 입력
n = int(input("뽑기 횟수 입력 (1회 시도마다 11번 도전): "))

counts = [0] * (max_pet + 1)

for _ in range(trials):
    pets = 0

    # 총 뽑기 횟수 = 11 * n
    for _ in range(n * 11):
        if pets < max_pet and random.random() < single_prob:
            pets += 1

    counts[pets] += 1

# 확률 계산
probabilities = [c / trials * 100 for c in counts]

print("\n==============================")
print("      🎯 확률 분석 결과")
print("==============================")

print("획득 개수 | 확률(%)")
print("------------------------")

for i in range(max_pet + 1):
    print(f"{i}개      | {probabilities[i]:.2f}%")

print("==============================\n")
```
### 📸 프로젝트 실행화면 🐣

![preview](https://raw.githubusercontent.com/seo941024/Python-GUI/master/result.png)

**📌 설명**  
- Python을 활용한 다양한 연습 프로젝트 진행  
- GUI 프로그램 제작 및 사용자 입력 처리 구현  
- 확률 기반 자석펫 뽑기 시뮬레이션 구현  

**⚙️ 사용 기술**  
- Python  
- random 모듈  
- Monte Carlo Simulation  

**💻 핵심 기능**
- GUI 기본 구조 구현  
- 게임 확률 시뮬레이션  
- 반복 실험 기반 결과 분석  

**🧠 배운 점**  
- 이벤트 기반 처리 흐름 이해  
- 확률 시뮬레이션 구조 학습  
- 랜덤 기반 모델링 경험  

---

### ☕ Java 프로젝트  
👉 https://github.com/seo941024/Java  

![preview](https://via.placeholder.com/600x300)

**📌 설명**  
- Java 기초 문법 및 객체지향 개념 학습 프로젝트  

**⚙️ 사용 기술**  
- Java  

**🧠 배운 점**  
- 클래스/객체 구조 이해  
- 프로그램 흐름 설계 능력 향상  

---

### 🌐 HTML 연습 프로젝트  
👉 https://github.com/seo941024/Web-practice  

![preview](https://raw.githubusercontent.com/seo941024/Web-practice/master/chap13_source/labs/images/webpage.png)

**📌 설명**  
- HTML/CSS 기반 웹페이지 제작  
- 벚꽃 축제 테마 UI 구현  

**⚙️ 사용 기술**  
- HTML  
- CSS  

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
