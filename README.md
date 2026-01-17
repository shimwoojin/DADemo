# 🛡️ DADemo - Tower Defense Game

> **Unreal Engine 4.26 Blueprint**로 구현한 3D 타워 디펜스 게임

[![Video](https://img.youtube.com/vi/31g7Hj3bfow/maxresdefault.jpg)](https://www.youtube.com/watch?v=31g7Hj3bfow&t=15s)
**▶️ [YouTube 플레이 영상 보기](https://www.youtube.com/watch?v=31g7Hj3bfow&t=15s)**

---

## 📋 프로젝트 개요

- **개발 기간**: 2023.03 ~ 2023.04 (2개월)
- **개발 인원**: 1인 (개인 프로젝트)
- **장르**: 3D Tower Defense
- **목적**: 자체 기획 타워 디펜스 게임 개발 및 블루프린트 활용

---

## 🛠 기술 스택

| 분류 | 기술 |
|------|------|
| **엔진** | Unreal Engine 4.26 |
| **개발 방식** | Blueprint (비주얼 스크립팅) |
| **AI 시스템** | Behavior Tree + Blackboard |
| **패턴** | Component-Based Architecture |

---

## ✨ 주요 구현 기능

### 1️⃣ 3가지 플레이어 직업 시스템
각 직업은 고유한 무기와 플레이 스타일을 가집니다:

- **🗡️ Attacker (공격자)**
  - 근접/원거리 무기 사용
  - 높은 전투력
  - 적 처치에 특화
  
- **🔨 Constructor (건설자)**
  - 타워 건설 능력
  - 방어 구조물 설치
  - 전략적 배치 특화
  
- **🌾 Farmer (농부)**
  - 작물 재배 시스템
  - 자원 생산
  - 경제 관리 특화

### 2️⃣ 타워 건설 시스템
- **타워 배치**: 지정된 TowerPoint에 타워 건설
- **타워 종류**:
  - 🧊 **Slow Tower**: 적 이동 속도 감소
  - 💥 **Splash Tower**: 광역 공격

### 3️⃣ 적 웨이브 시스템
- **적 종류**:
  - 🦁 **Animal**: 기본 동물 적
  - 🐘 **African Animal**: 강화된 아프리카 동물
  - 💀 **Undead**: 언데드 유닛
- **AI 패턴**: Behavior Tree 기반 지능형 행동
- **스포너 시스템**: 웨이브별 적 생성

### 4️⃣ 방어 포인트 시스템
- **Defense Point**: 플레이어가 방어해야 할 핵심 거점
- 적이 방어 포인트에 도달하면 게임 오버

### 5️⃣ 자원 & 경제 시스템
- **골드 시스템**: 적 처치 및 작물 재배로 획득
- **상점 시스템**: 직업별 전용 상점
  - Attacker Store
  - Constructor Store
  - Farmer Store

### 6️⃣ 스킬 시스템
- 각 직업별 고유 스킬 (E, R)
- 쿨타임 관리 UI

---

## 🎮 조작법

| 키 | 기능 |
|---|------|
| **W, A, S, D** | 이동 |
| **Shift** | 빠른 달리기 |
| **Space** | 점프 |
| **Q** | 무기 변경 |
| **마우스 좌클릭** | 공격 |
| **E** | 스킬 1 |
| **R** | 스킬 2 |

---

## 📁 프로젝트 구조

```
DADemo/
├── Content/
│   ├── Blueprints/
│   │   ├── Actors/
│   │   │   ├── Players/           # 플레이어 시스템
│   │   │   │   ├── BP_PlayerAttacker
│   │   │   │   ├── BP_PlayerConstructor
│   │   │   │   ├── BP_PlayerFarmer
│   │   │   │   └── PlayerAI/
│   │   │   ├── Enemies/           # 적 시스템
│   │   │   │   ├── BP_EnemyAnimal
│   │   │   │   ├── BP_EnemyAfricanAnimal
│   │   │   │   ├── BP_EnemyUndead
│   │   │   │   ├── AI/            # Behavior Tree
│   │   │   │   ├── Category/
│   │   │   │   └── Spawners/      # 웨이브 스포너
│   │   │   ├── Towers/            # 타워 시스템
│   │   │   │   ├── BP_SlowTower
│   │   │   │   ├── BP_SplashTower
│   │   │   │   ├── BP_TowerMaker
│   │   │   │   └── BP_TowerPoint
│   │   │   ├── Weapons/           # 무기 시스템
│   │   │   │   ├── Attacker/
│   │   │   │   ├── Constructor/
│   │   │   │   ├── Farmer/
│   │   │   │   ├── BP_MeleeWeapon
│   │   │   │   └── BP_RangedWeapon
│   │   │   ├── Crops/             # 작물 시스템
│   │   │   │   ├── Crops/
│   │   │   │   └── CropSpawner/
│   │   │   ├── Skills/            # 스킬
│   │   │   ├── Projectiles/       # 투사체
│   │   │   └── Money/             # 골드 시스템
│   │   ├── UI/                    # 게임 UI
│   │   │   ├── WBP_MainUI
│   │   │   ├── WBP_PlayerUI
│   │   │   ├── WBP_AttackerStore
│   │   │   ├── WBP_ConstructorStore
│   │   │   ├── WBP_FarmerStore
│   │   │   ├── WBP_SkillBar
│   │   │   ├── WBP_WinText
│   │   │   └── WBP_LoseText
│   │   ├── Datas/                 # 데이터 에셋
│   │   ├── Interfaces/            # 블루프린트 인터페이스
│   │   └── Utils/                 # 유틸리티
│   ├── Maps/                      # 게임 레벨
│   │   ├── MainUI.umap           # 메인 메뉴
│   │   ├── First.umap            # 스테이지 1
│   │   ├── Second.umap           # 스테이지 2
│   │   └── Third.umap            # 스테이지 3
│   └── MyAssets/                  # 게임 에셋
└── Config/                        # 프로젝트 설정
```

---

## 🎯 구현 하이라이트

### 🔹 직업 시스템 설계
3가지 직업이 각각 독립적인 플레이 스타일을 가지며, 팀 플레이 시 시너지 발휘
- Attacker: 전투
- Constructor: 방어 구조물
- Farmer: 경제 관리

### 🔹 타워 디펜스 메커니즘
```
적 스포너 → 적 생성 → 경로 이동 → 타워/플레이어 공격 → 방어 포인트 도달 체크
```

### 🔹 자원 순환 구조
```
적 처치/작물 재배 → 골드 획득 → 상점에서 아이템 구매 → 전투력 강화
```

### 🔹 Behavior Tree AI
- Blackboard: 적 상태 데이터 관리
- Tasks: 이동, 공격, 특수 행동
- BackDoor 시스템: 특정 적의 우회 경로

---

## 🚀 실행 방법

### 📦 필수 요구사항
- **Unreal Engine 4.26**
- **Windows 10/11**
- **DirectX 11** 이상

### ⚙️ 실행 단계

1. **Epic Games Launcher**에서 Unreal Engine 4.26 설치

2. **프로젝트 열기**
   ```
   DADemo.uproject 더블클릭
   → Unreal Editor에서 자동 실행
   ```

3. **게임 플레이**
   - 메인 레벨: `Content/Maps/MainUI.umap` 실행
   - 스테이지 선택 후 플레이
   - 에디터 상단의 "플레이" 버튼 클릭 또는 `Alt + P`

---

## 📚 학습 성과

### 기술적 성장
- ✅ **타워 디펜스 장르** 메커니즘 구현
- ✅ **직업 시스템** 설계 및 밸런싱
- ✅ **자원 경제 시스템** 구축
- ✅ **Behavior Tree AI** 활용
- ✅ **웨이브 스포너** 시스템 구현

### 게임 디자인 이해
- 직업별 차별화된 플레이 경험 제공
- 자원 관리의 중요성 (골드 → 타워/아이템)
- 난이도 조절 (스테이지별 웨이브 강도)
- 승/패 조건 명확화

---

## 🎨 게임 특징

- 🎭 **3가지 직업** (Attacker, Constructor, Farmer)
- 🗼 **2종 타워** (Slow, Splash)
- 👾 **3종 적** (Animal, African Animal, Undead)
- 🌾 **작물 재배 시스템** (Farmer 전용)
- 💰 **골드 & 상점 시스템**
- 🎯 **3개 스테이지** 진행
- 🏆 **승/패 판정** 및 재시작

---

## 🎮 게임플레이 팁

1. **초반**: Farmer로 작물 재배하여 경제 기반 구축
2. **중반**: Constructor로 핵심 위치에 타워 배치
3. **후반**: Attacker로 강력한 적 처리
4. **전략**: 직업 전환(Q)을 활용한 상황 대처

---

## 📌 참고사항

- 이 프로젝트는 학습 및 자체 기획 목적으로 제작되었습니다
- Unreal Engine 4.26 블루프린트 기반 타워 디펜스 게임 개발 연습 프로젝트입니다
- 모든 시스템은 자체 기획 및 구현되었습니다

---

## 📧 Contact

- **Email**: ggoggal@gmail.com
- **Portfolio**: [https://shimwoojin-portfolio.vercel.app/](https://shimwoojin-portfolio.vercel.app/)
- **GitHub**: [@shimwoojin](https://github.com/shimwoojin)

---

**Made with ❤️ by Woojin Shim** | 2023.03 ~ 2023.04
