# 안녕하세요. 서지섭입니다.

---

## 🙋‍♂️ About Me
- 🌱 Python 공부 중
---

## 🛠 Tech Stack

[![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://github.com/seo941024/Python-GUI)
[![Java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=java&logoColor=white)](https://github.com/seo941024/Java)
[![HTML](https://img.shields.io/badge/HTML-E34F26?style=for-the-badge&logo=html5&logoColor=white)](https://github.com/seo941024/Web-practice)

---

## 📌 대표 프로젝트 소개

# 🎳 Bowling Score Board
이 프로젝트는 Python과 Flet을 활용하여 구현한 **볼링 점수판 GUI 프로그램**입니다.
사용자의 투구 결과를 입력받아 **실시간으로 프레임 점수와 누적 점수**를 시각적으로 표시합니다.

---

## 🚀 주요 기능

* 🎯 투구 입력 (핀 개수 입력)
* 📊 실시간 점수 계산 및 누적 점수 표시
* 🎳 스트라이크 / 스페어 자동 판별
* 🧾 프레임별 점수 시각화
* 🏁 게임 종료 시 최종 점수 출력

---

## 🛠️ 사용 기술

* **Python 3**
* **Flet (GUI Framework)**

---

## 📂 프로젝트 구조

```id="p1"
📦 Bowling-Score-Board
 ┣ 📜 Bowlingfletcomplete.py      # Flet UI 및 이벤트 처리
 ┣ 📜 bowlingfletcomplete_class.py      # 볼링 점수 계산 로직 (BowlingGame 클래스)
 ┣ 📜 README.md
 ┗ 📜 requirements.txt
```

---

## 🧠 핵심 로직 설명

### 🎳 BowlingGame 클래스

* `throw_list`를 기반으로 투구 기록 저장
* 스트라이크 / 스페어 규칙에 맞게 점수 계산
* 프레임별 누적 점수 반환

### 핵심 코드 ###
```python
import flet as ft
import random

class BowlingGame:
    def __init__(self):
        self.throw_list = []

    # -------------------------
    # 유효성 검사
    # -------------------------
    def is_valid_roll(self, pins):
        throws = self.throw_list
        i = 0
        frame = 1

        # 1~9프레임까지 현재 투구가 어디 위치인지 정확히 추적
        while i < len(throws) and frame < 10:
            if throws[i] == 10:  # 스트라이크인 경우
                i += 1
            else:                # 스트라이크가 아닌 경우 (2구 소모)
                if i + 1 < len(throws):
                    i += 2
                else:
                    # 현재 프레임의 첫 번째 투구만 던진 상태라면 여기서 멈춤
                    break
            frame += 1

        # 이제 'frame'은 현재 투구가 속한 프레임 번호, 'i'는 해당 프레임의 시작 인덱스
        current_frame_throws = throws[i:]

        # 1~9프레임 검증
        if frame < 10:
            if len(current_frame_throws) == 0:
                return True # 첫 번째 투구는 0~10 사이면 무조건 통과 (이미 밖에서 체크됨)
            elif len(current_frame_throws) == 1:
                # 첫 투구가 10(X)이 아닌데, 두 번째 투구와의 합이 10을 넘으면 안 됨
                if current_frame_throws[0] < 10 and current_frame_throws[0] + pins > 10:
                    return False
        
        # 10프레임 검증
        else:
            if len(current_frame_throws) == 1:
                first = current_frame_throws[0]
                # 10프레임 첫 투구가 스트라이크가 아닌데 합이 10을 넘으면 오류
                if first < 10 and first + pins > 10:
                    return False
            elif len(current_frame_throws) == 2:
                first = current_frame_throws[0]
                second = current_frame_throws[1]
                # 보너스 기회가 없는 경우 (합이 10 미만)
                if first + second < 10:
                    return False
                # 보너스 투구 시: 두 번째 투구가 스트라이크가 아닐 때만 세 번째 투구 합산 체크
                if first == 10 and second < 10 and second + pins > 10:
                    return False
        
        return True

    # -------------------------
    # 점수 계산
    # -------------------------
    def calculate_live_scores(self):
        scores = []
        total = 0
        i = 0
        tl = self.throw_list

        for frame in range(10):
            if i >= len(tl): break

            if frame < 9:
                if tl[i] == 10: # 스트라이크
                    if i + 2 < len(tl):
                        total += 10 + tl[i+1] + tl[i+2]
                        scores.append(total)
                        i += 1
                    else: break
                elif i + 1 < len(tl):
                    if tl[i] + tl[i+1] == 10: # 스페어
                        if i + 2 < len(tl):
                            total += 10 + tl[i+2]
                            scores.append(total)
                            i += 2
                        else: break
                    else: # 오픈
                        total += tl[i] + tl[i+1]
                        scores.append(total)
                        i += 2
                else: break
            else: # 10프레임
                if i + 1 < len(tl):
                    if tl[i] + tl[i+1] >= 10:
                        if i + 2 < len(tl):
                            total += tl[i] + tl[i+1] + tl[i+2]
                            scores.append(total)
                            i += 3
                        else: break
                    else:
                        total += tl[i] + tl[i+1]
                        scores.append(total)
                        i += 2
                else: break
        return scores

    def get_display_data(self):
        display_frames = []
        i = 0
        tl = self.throw_list

        for frame in range(10):
            if i >= len(tl):
                display_frames.append([])
                continue
            if frame == 9:
                shots = []
                for val in tl[i:]:
                    if val == 10: shots.append("X")
                    elif len(shots) > 0 and shots[-1].isdigit() and int(shots[-1]) + val == 10:
                        shots.append("/")
                    else: shots.append("-" if val == 0 else str(val))
                display_frames.append(shots)
                break
            else:
                if tl[i] == 10:
                    display_frames.append([" ", "X"])
                    i += 1
                elif i + 1 < len(tl):
                    f, s = tl[i], tl[i+1]
                    s1 = "-" if f == 0 else str(f)
                    s2 = "/" if f + s == 10 else ("-" if s == 0 else str(s))
                    display_frames.append([s1, s2])
                    i += 2
                else:
                    display_frames.append(["-" if tl[i] == 0 else str(tl[i])])
                    i += 1
        return display_frames

    def is_game_over(self):
        return len(self.calculate_live_scores()) == 10

# ==================================================
# UI 
# ==================================================
def main(page: ft.Page):
    page.title = "Bowling System"
    page.bgcolor = "#051622"
    page.padding = 40
    page.width = 1200
    page.height = 700

    game = BowlingGame()
    score_grid = ft.Column(spacing=0)
    error_text = ft.Text("", color="red", size=16)
    info_text = ft.Text("", color="lightgreen", size=16)

    def build_grid():
        frames_data = game.get_display_data()
        live_scores = game.calculate_live_scores()
        header_row, shots_row, total_row = ft.Row(spacing=0, alignment="center"), ft.Row(spacing=0, alignment="center"), ft.Row(spacing=0, alignment="center")

        for i in range(10):
            is_10 = (i == 9)
            w = 150 if is_10 else 90
            highlight = "#FF6B00" if i == len(live_scores) else "#1A374D"
            header_row.controls.append(ft.Container(content=ft.Text(str(i+1), color="white", weight="bold", size=18), width=w, height=40, bgcolor=highlight, alignment=ft.Alignment(0, 0), border=ft.border.all(2, "#333333")))
            
            shots = frames_data[i]
            num_s = 3 if is_10 else 2
            shot_inner = ft.Row(spacing=0)
            for s_idx in range(num_s):
                val = shots[s_idx] if s_idx < len(shots) else ""
                shot_inner.controls.append(ft.Container(content=ft.Text(val, color="white", size=24 if val == "X" else 20, weight="bold"), width=w / num_s, height=50, alignment=ft.Alignment(0, 0), border=ft.border.all(1, "#333333"), bgcolor="#0B2447"))
            shots_row.controls.append(ft.Container(content=shot_inner, width=w))

            curr_score = str(live_scores[i]) if i < len(live_scores) else ""
            total_row.controls.append(ft.Container(content=ft.Text(curr_score, color="#FFD700", size=30, weight="bold"), width=w, height=90, alignment=ft.Alignment(0, 0), border=ft.border.all(1, "#333333"), bgcolor="#124559"))

        score_grid.controls = [header_row, shots_row, total_row]
        if live_scores:
            total = live_scores[-1]
            info_text.value = f"총점: {total} | 평균: {round(total / len(live_scores), 2)} | 스트라이크: {game.throw_list.count(10)}"
        else: info_text.value = ""
        page.update()

    input_box = ft.TextField(label="0~10 입력", width=150, text_align="center", bgcolor="white")

    def do_roll(e):
        error_text.value = ""
        if game.is_game_over():
            error_text.value = "게임 끝났어요!"; page.update(); return
        try:
            p = int(input_box.value)
            if not (0 <= p <= 10): raise ValueError
            if not game.is_valid_roll(p):
                error_text.value = "핀 합이 10을 넘어요!"; page.update(); return
            game.throw_list.append(p)
            input_box.value = ""; build_grid()
        except: error_text.value = "숫자 0~10 입력!"; page.update()

    input_box.on_submit = do_roll
    def reset_game(e): game.throw_list.clear(); error_text.value = ""; info_text.value = ""; build_grid()
    def undo_roll(e):
        if game.throw_list: game.throw_list.pop(); build_grid()
    def auto_roll(e):
        if not game.is_game_over():
            for _ in range(50):
                p = random.randint(0, 10)
                if game.is_valid_roll(p):
                    game.throw_list.append(p); build_grid(); break

    page.add(ft.Column([ft.Text("🎳 Bowling Game 🎳", size=40, weight="bold", color="white"), ft.Container(height=10), score_grid, ft.Container(height=20), info_text, error_text, ft.Row([input_box, ft.ElevatedButton("🎯 투구", on_click=do_roll), ft.ElevatedButton("↩ Undo", on_click=undo_roll), ft.ElevatedButton("🎲 Auto", on_click=auto_roll), ft.ElevatedButton("🔄 Reset", on_click=reset_game)], alignment="center")], horizontal_alignment="center", alignment="center"))
    build_grid()

if __name__ == "__main__":
    ft.app(target=main)
```

### 📊 실시간 점수 처리

* 투구 시마다 `add_throw()` 실행
* UI 즉시 업데이트
* `calculate_live_scores()`로 누적 점수 반영

---

## ▶️ 실행 방법

### 1️⃣ 패키지 설치

```id="p2"
pip install flet
```

### 2️⃣ 실행

```id="p3"
Bowling_flet.py
```

---

## 💡 실행 화면

* 프레임별 점수 박스 UI
* 점수 누적 표시
* 입력창 + 투구 버튼
  
![preview](https://raw.githubusercontent.com/seo941024/Python/master/Practice/Bowlingfletcapture.png)

---
## 📖 학습 포인트

* 이벤트 기반 GUI 프로그래밍
* 클래스 기반 로직 분리 (UI vs Logic)
* 리스트 및 조건문을 활용한 상태 관리
* 실시간 데이터 업데이트 처리

---

## ✨ 향후 개선 사항

* 🎨 UI 애니메이션 (스트라이크 효과 등)
* 📈 점수 그래프 시각화
* 💾 게임 기록 저장 기능

---
### 🐍 Python 프로젝트
👉 https://github.com/seo941024/Python
- 게임 내 희귀 확률(0.2%) 가챠 모델을 n회 시행으로 정의, 100만 회 Monte Carlo 시뮬레이션을 통해 기대값 및 획득 분포를 추정한 프로젝트 제작
  
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
👉 https://github.com/seo941024/Web-PRG

![preview](https://raw.githubusercontent.com/seo941024/Web-PRG/master/web/Class/chap13/labs/images/webpage.png)
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
