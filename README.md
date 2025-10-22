# Matplotlib 라이브러리 사용법 가이드

## 📚 목차
1. 기본 개념
2. 설치 방법
3. 기본 그래프 그리기
4. 주요 기능
5. 실전 예제

---

## 1. 기본 개념

Matplotlib는 Python에서 가장 널리 사용되는 데이터 시각화 라이브러리입니다. 다양한 종류의 그래프와 차트를 생성할 수 있습니다.

### 주요 모듈
- **pyplot**: MATLAB 스타일의 인터페이스 제공 (가장 많이 사용)
- **figure**: Figure 객체 생성 및 관리
- **axes**: 실제 그래프가 그려지는 영역

---

## 2. 설치 방법

```bash
# pip를 사용한 설치
pip install matplotlib

# conda를 사용한 설치
conda install matplotlib
```

### 기본 import
```python
import matplotlib.pyplot as plt
import numpy as np  # 데이터 생성에 자주 사용
```

---

## 3. 기본 그래프 그리기

### 선 그래프 (Line Plot)
```python
import matplotlib.pyplot as plt

# 데이터 준비
x = [1, 2, 3, 4, 5]
y = [2, 4, 6, 8, 10]

# 그래프 그리기
plt.plot(x, y)
plt.xlabel('X축')
plt.ylabel('Y축')
plt.title('기본 선 그래프')
plt.show()
```

### 산점도 (Scatter Plot)
```python
plt.scatter(x, y, color='red', marker='o')
plt.xlabel('X축')
plt.ylabel('Y축')
plt.title('산점도')
plt.show()
```

### 막대 그래프 (Bar Chart)
```python
categories = ['A', 'B', 'C', 'D']
values = [25, 40, 30, 55]

plt.bar(categories, values, color='skyblue')
plt.xlabel('카테고리')
plt.ylabel('값')
plt.title('막대 그래프')
plt.show()
```

### 히스토그램 (Histogram)
```python
import numpy as np

data = np.random.randn(1000)
plt.hist(data, bins=30, color='green', alpha=0.7)
plt.xlabel('값')
plt.ylabel('빈도')
plt.title('히스토그램')
plt.show()
```

---

## 4. 주요 기능

### 4.1 Figure와 Axes 설정

```python
# Figure 크기 설정
plt.figure(figsize=(10, 6))

# 여러 서브플롯 생성
fig, axes = plt.subplots(2, 2, figsize=(12, 10))
axes[0, 0].plot(x, y)
axes[0, 1].scatter(x, y)
axes[1, 0].bar(categories, values)
axes[1, 1].hist(data)
plt.tight_layout()
plt.show()
```

### 4.2 스타일 및 색상

```python
# 선 스타일
plt.plot(x, y, linestyle='-')   # 실선 (기본값)
plt.plot(x, y, linestyle='--')  # 점선
plt.plot(x, y, linestyle='-.')  # 일점쇄선
plt.plot(x, y, linestyle=':')   # 점선

# 선 두께
plt.plot(x, y, linewidth=2)

# 색상 지정
plt.plot(x, y, color='red')        # 이름으로
plt.plot(x, y, color='#FF5733')    # HEX 코드로
plt.plot(x, y, color=(0.1, 0.2, 0.5))  # RGB 튜플로

# 마커 스타일
plt.plot(x, y, marker='o')   # 원
plt.plot(x, y, marker='s')   # 사각형
plt.plot(x, y, marker='^')   # 삼각형
plt.plot(x, y, marker='*')   # 별
```

### 4.3 범례 (Legend)

```python
plt.plot(x, y1, label='데이터 1')
plt.plot(x, y2, label='데이터 2')
plt.legend()  # 범례 표시

# 범례 위치 지정
plt.legend(loc='upper right')  # 'upper left', 'lower right', 'center' 등
```

### 4.4 축 설정

```python
# 축 범위 설정
plt.xlim(0, 10)
plt.ylim(0, 100)

# 축 스케일 변경
plt.xscale('log')  # 로그 스케일
plt.yscale('log')

# 축 눈금 설정
plt.xticks([0, 2, 4, 6, 8, 10])
plt.yticks([0, 50, 100], ['낮음', '중간', '높음'])

# 그리드 표시
plt.grid(True)
plt.grid(alpha=0.3, linestyle='--')
```

### 4.5 텍스트 및 주석

```python
# 제목 및 레이블
plt.title('그래프 제목', fontsize=16, fontweight='bold')
plt.xlabel('X축 레이블', fontsize=12)
plt.ylabel('Y축 레이블', fontsize=12)

# 텍스트 추가
plt.text(5, 50, '중요한 지점', fontsize=12)

# 화살표 주석
plt.annotate('최댓값', xy=(7, 80), xytext=(5, 90),
             arrowprops=dict(arrowstyle='->', color='red'))
```

### 4.6 저장

```python
# 이미지로 저장
plt.savefig('graph.png')
plt.savefig('graph.png', dpi=300)  # 고해상도
plt.savefig('graph.pdf')  # PDF 형식
plt.savefig('graph.svg')  # SVG 형식

# 여백 제거
plt.savefig('graph.png', bbox_inches='tight')
```

---

## 5. 실전 예제

### 예제 1: 다중 선 그래프
```python
import matplotlib.pyplot as plt
import numpy as np

x = np.linspace(0, 10, 100)
y1 = np.sin(x)
y2 = np.cos(x)
y3 = np.sin(x) * np.cos(x)

plt.figure(figsize=(10, 6))
plt.plot(x, y1, label='sin(x)', linewidth=2)
plt.plot(x, y2, label='cos(x)', linewidth=2)
plt.plot(x, y3, label='sin(x)·cos(x)', linewidth=2)

plt.xlabel('X', fontsize=12)
plt.ylabel('Y', fontsize=12)
plt.title('삼각함수 그래프', fontsize=14, fontweight='bold')
plt.legend()
plt.grid(True, alpha=0.3)
plt.tight_layout()
plt.savefig('trig_functions.png', dpi=300)
plt.show()
```

### 예제 2: 파이 차트
```python
labels = ['Python', 'Java', 'JavaScript', 'C++', 'Others']
sizes = [35, 25, 20, 10, 10]
colors = ['#ff9999', '#66b3ff', '#99ff99', '#ffcc99', '#ff99cc']
explode = (0.1, 0, 0, 0, 0)  # 첫 번째 조각 강조

plt.figure(figsize=(8, 8))
plt.pie(sizes, explode=explode, labels=labels, colors=colors,
        autopct='%1.1f%%', shadow=True, startangle=90)
plt.title('프로그래밍 언어 사용 비율', fontsize=14, fontweight='bold')
plt.axis('equal')
plt.tight_layout()
plt.savefig('pie_chart.png', dpi=300)
plt.show()
```

### 예제 3: 서브플롯을 사용한 대시보드
```python
import matplotlib.pyplot as plt
import numpy as np

# 데이터 생성
x = np.linspace(0, 10, 100)
data1 = np.random.randn(1000)
categories = ['A', 'B', 'C', 'D', 'E']
values = [23, 45, 56, 78, 32]

# 2x2 서브플롯 생성
fig, axes = plt.subplots(2, 2, figsize=(12, 10))

# 1. 선 그래프
axes[0, 0].plot(x, np.sin(x), 'b-', linewidth=2)
axes[0, 0].set_title('선 그래프', fontweight='bold')
axes[0, 0].set_xlabel('X')
axes[0, 0].set_ylabel('sin(X)')
axes[0, 0].grid(True, alpha=0.3)

# 2. 히스토그램
axes[0, 1].hist(data1, bins=30, color='green', alpha=0.7, edgecolor='black')
axes[0, 1].set_title('히스토그램', fontweight='bold')
axes[0, 1].set_xlabel('값')
axes[0, 1].set_ylabel('빈도')

# 3. 막대 그래프
axes[1, 0].bar(categories, values, color='skyblue', edgecolor='navy')
axes[1, 0].set_title('막대 그래프', fontweight='bold')
axes[1, 0].set_xlabel('카테고리')
axes[1, 0].set_ylabel('값')

# 4. 산점도
x_scatter = np.random.rand(50) * 10
y_scatter = np.random.rand(50) * 10
axes[1, 1].scatter(x_scatter, y_scatter, c='red', s=50, alpha=0.6)
axes[1, 1].set_title('산점도', fontweight='bold')
axes[1, 1].set_xlabel('X')
axes[1, 1].set_ylabel('Y')
axes[1, 1].grid(True, alpha=0.3)

plt.tight_layout()
plt.savefig('dashboard.png', dpi=300)
plt.show()
```

### 예제 4: 하트 모양 (파라메트릭 방정식)
```python
import matplotlib.pyplot as plt
import numpy as np

# 하트 모양 파라메트릭 방정식
t = np.linspace(0, 2 * np.pi, 1000)
x = 16 * np.sin(t)**3
y = 13 * np.cos(t) - 5 * np.cos(2*t) - 2 * np.cos(3*t) - np.cos(4*t)

# 그래프 그리기
plt.figure(figsize=(8, 8))
plt.plot(x, y, 'r-', linewidth=2)
plt.fill(x, y, 'red', alpha=0.7)
plt.title('❤️ Heart Shape', fontsize=20, fontweight='bold')
plt.axis('equal')
plt.grid(True, alpha=0.3)
plt.tight_layout()
plt.savefig('heart.png', dpi=300)
plt.show()
```

---

## 💡 유용한 팁

### 한글 폰트 설정
```python
import matplotlib.pyplot as plt
from matplotlib import font_manager, rc

# Windows
plt.rcParams['font.family'] = 'Malgun Gothic'
# Mac
plt.rcParams['font.family'] = 'AppleGothic'
# Linux
plt.rcParams['font.family'] = 'NanumGothic'

# 마이너스 기호 깨짐 방지
plt.rcParams['axes.unicode_minus'] = False
```

### 스타일 테마 적용
```python
# 사용 가능한 스타일 확인
print(plt.style.available)

# 스타일 적용
plt.style.use('seaborn-v0_8')
plt.style.use('ggplot')
plt.style.use('dark_background')
```

### 인터랙티브 모드
```python
# 주피터 노트북에서
%matplotlib inline  # 정적 이미지
%matplotlib notebook  # 인터랙티브

# 일반 Python 스크립트에서
plt.ion()  # 인터랙티브 모드 켜기
plt.ioff()  # 인터랙티브 모드 끄기
```

---

## 📖 참고 자료

- 공식 문서: https://matplotlib.org/stable/contents.html
- 갤러리: https://matplotlib.org/stable/gallery/index.html
- 튜토리얼: https://matplotlib.org/stable/tutorials/index.html

---

이 가이드는 matplotlib의 기본적인 사용법을 다룹니다. 더 고급 기능은 공식 문서를 참고하세요! 🎨
