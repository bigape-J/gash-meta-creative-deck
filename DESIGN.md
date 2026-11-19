# DESIGN.md — Jitter (`jitter.video`) 기반 프레젠테이션 디자인 시스템

> **Source Reference:** `https://jitter.video/` (Live DOM & CSS Token Extraction)  
> **적용 목적:** 웹 모션 스튜디오 Jitter 특유의 **깨끗한 화이트 스테이지 + 소프트 그레이 벤토(Bento) 카드 + 초고대비 타이포그래피 + 네온 파스텔 포인트**를 16:9 프레젠테이션(PPT형 HTML 덱)에 이식하기 위한 디자인 규격서.

---

## 1. 핵심 디자인 철학 (Core Principles)

1. **Crisp Light Stage & Zero Muddy Shadows (맑은 라이트 캔버스와 평면적 깊이감)**
   - 어두운 배경이나 뿌연 글래스모피즘(`backdrop-filter`)을 배제하고, 순백색(`#FFFFFF`) 캔버스 위에 쿨 라이트 그레이(`#F2F1F3`) 벤토 카드로 명확한 구획을 나눈다.
   - 카드 테두리는 남용하지 않고, 꼭 필요한 데이터 래퍼나 인용 배지에만 `1px solid #E5E4E7` 헤어라인을 사용한다.
2. **Tight-Tracked Heavy Grotesque Display (압도적 밀도의 헤드라인)**
   - 슬라이드 제목과 핵심 지표(Big Number)는 `font-weight: 800`, 줄간격 `95% ~ 105%`, 자간 `-0.03em ~ -0.04em`으로 강하게 조여 시선을 단번에 고정한다.
3. **Boxed Highlighter Chips (`box-decoration-break: clone`)**
   - 벤토 카드 내부 타이틀이나 핵심 구절에 흰색(`#FFFFFF`), 차콜 블랙(`#19171C`), 혹은 애시드 옐로우(`#F5FF63`) 배경 칩을 인라인 테이프처럼 감싸 Jitter 특유의 경쾌한 에디토리얼 리듬을 만든다.
4. **Restrained Color Pops (절제된 3색 하이라이트)**
   - 전체 면적의 85% 이상을 `#FFFFFF` · `#F2F1F3` · `#19171C` 무채색으로 유지하고, 핵심 전략 포인트와 태그에만 **Signature Violet(`#B593FF`)**, **Acid Yellow(`#F5FF63`)**, **Electric Cyan(`#01B2FD`)**을 제한적으로 타격한다.

---

## 2. 컬러 토큰 (Color Palette)

### 2.1 Surfaces & Backgrounds
| Token Name | HEX | 용도 |
|---|---|---|
| `--bg-canvas` | `#FFFFFF` | 기본 슬라이드 배경 (Primary Slide Canvas) |
| `--bg-app-backdrop` | `#F8F8F8` | 슬라이드 바깥 프레젠테이션 뷰어 배경 |
| `--surface-bento` | `#F2F1F3` | 기본 벤토(Bento) 카드 배경 (`#F3F3F5` 보조 허용) |
| `--surface-divider` | `#E5E4E7` | 1px 구분선 및 테이블/데이터 보더 |
| `--surface-stage-dark` | `#19171C` / `#000000` | 클로징 슬라이드 및 고대비 강조 다크 스테이지 |

### 2.2 Text & Ink Hierarchy
| Token Name | HEX | 용도 |
|---|---|---|
| `--ink-primary` | `#19171C` | 메인 헤드라인, 본문 핵심 텍스트, 다크 버튼/칩 배경 |
| `--ink-deep-violet` | `#17082C` | 바이올렛 틴트 카드 위 강조 텍스트 |
| `--ink-secondary` | `#6E6E73` | 보조 설명, 서브 카피, 메타데이터, 캡션 |
| `--ink-muted` | `#97979B` | 각주(Disclaimer), 비활성 페이지네이션, 보조 라벨 |
| `--ink-inverse` | `#FFFFFF` | 다크 스테이지(`#19171C`) 및 진한 포인트 카드 위 텍스트 |

### 2.3 Brand & Functional Accents
| Token Name | HEX | 텍스트 조합 | 용도 |
|---|---|---|---|
| `--accent-violet` | `#B593FF` / `#A981FF` | `#19171C` | 핵심 전략 배지, 메인 CTA, 강조 벤토 카드 |
| `--accent-violet-soft` | `#F2ECFD` | `#17082C` | 소프트 라벤더 하이라이트 카드 배경 |
| `--accent-yellow` | `#F5FF63` | `#19171C` | `KEY`, `NEW`, `HOOK` 마이크로 필 태그, 핵심 수치 마킹 |
| `--accent-cyan` | `#01B2FD` | `#FFFFFF` | 기술 스펙(USP), 타임라인 데모 구간 강조 |
| `--accent-cyan-soft` | `#E6F4FF` | `#19171C` | 데이터·근거 비교용 아이스 블루 벤토 카드 |
| `--brand-gash-emerald` | `#0E7C6B` | `#FFFFFF` | *(캠페인 전용 보조)* GASH 그린 보틀 식별용 포인트 배지 |

---

## 3. 타이포그래피 규격 (Typography Scale)

* **Display / Heading Stack:** `'TWK Lausanne', 'Plus Jakarta Sans', 'Pretendard', -apple-system, BlinkMacSystemFont, sans-serif`
* **Body / UI Stack:** `'Inter', 'Pretendard', -apple-system, BlinkMacSystemFont, 'Malgun Gothic', sans-serif`
* **Monospace (시간·지표·코드):** `ui-monospace, 'SFMono-Regular', Menlo, Consolas, monospace`
* **렌더링:** `-webkit-font-smoothing: antialiased; letter-spacing: -0.02em;` 기본 적용.

| 위계 (Role) | 크기 (16:9 Slide 기준) | 굵기 | 줄간격 | 자간 | 비고 |
|---|---|---|---|---|---|
| **Cover Hero H1** | `48px ~ 58px` | `800` | `1.04` | `-0.04em` | 표지 및 섹션 디바이더 타이틀 |
| **Slide Title H2** | `32px ~ 38px` | `800` | `1.08` | `-0.035em` | 각 슬라이드 상단 핵심 메시지형 헤드라인 |
| **Big Metric / Stat** | `36px ~ 46px` | `800` | `1.00` | `-0.04em` | `461%`, `10s`, `200원`, `46% OFF` 등 핵심 근거 수치 |
| **Bento Card H3** | `18px ~ 20px` | `700` | `1.20` | `-0.02em` | 필요 시 인라인 박스 칩 스타일 적용 |
| **Body Copy** | `14px ~ 15px` | `400` (`strong` `600`) | `1.55` | `-0.02em` | 설명은 최대 2~3줄 이내로 압축 |
| **Pill Badge / Tag** | `12px ~ 13px` | `700` | `1.20` | `-0.01em` | 상단 아이브로우 태그 및 타임라인 배지 |
| **Footnote / Source** | `11.5px ~ 12px` | `400` | `1.45` | `-0.01em` | 데이터 출처 및 광고 심의 유의사항 |

---

## 4. 지오메트리 · 간격 · 그림자 (Geometry & Elevation)

* **Border Radius (곡률 체계)**
  * **Slide Outer Stage:** `36px ~ 40px` (`jitter.video`의 `4rem = 40px` 규격 계승)
  * **Bento Cards:** `24px ~ 32px` (슬라이드 내부 밀도에 맞춘 대곡률 라운딩)
  * **Inner Sub-Boxes / Table Containers:** `16px ~ 20px`
  * **Buttons & Pill Badges:** `999px` (완전한 캡슐형 Full-Pill)
* **Grid & Spacing**
  * **Slide Aspect Ratio:** `16 : 9` 기준 (`max-width: 1280px`, 최소 높이 `720px`, 내용량에 따라 유연 확장 + 인쇄 시 페이지 분리)
  * **Slide Padding:** `44px 52px` (모바일 반응형 `24px`)
  * **Bento Grid Gap:** `16px ~ 20px`
* **Ambient Multi-Layer Shadow (글래스모피즘 대체 입체감)**
  * 플로팅 슬라이드 및 강조 카드 그림자:
    ```css
    box-shadow:
      0 30px 30px rgba(25, 23, 28, 0.04),
      0 12px 24px rgba(25, 23, 28, 0.05),
      0 4px 10px rgba(25, 23, 28, 0.04);
    ```
* **Spring Hover Interaction**
  * 버튼 및 네비게이션 탭 전환: `transition: transform 0.22s cubic-bezier(0.34, 1.56, 0.64, 1), background-color 0.18s ease;` (`hover: scale(1.03)`, `active: scale(0.97)`).

---

## 5. PPT 슬라이드 레이아웃 아키타입 (5 Slide Archetypes)

1. **Archetype A — Hero Cover Stage:** 상단 `#F5FF63` 아이브로우 필 + 초대형 타이포그래피 + 하단 4열 핵심 프로젝트 메타 벤토 바.
2. **Archetype B — Evidence & Thesis Bento (2×2 / 3-Col):** 상단 결론형 원센텐스 메시지(Action Title) + 수치 배지와 논리적 근거가 결합된 벤토 그리드(`#F2F1F3` 기본 + `#F2ECFD` / `#E6F4FF` 포인트 카드 1개).
3. **Archetype C — Funnel & Matrix Split:** 좌측 퍼널/타깃 요약 카드(4열 비중) + 우측 매트릭스 테이블 또는 비교 카드(8열 비중).
4. **Archetype D — 20s Storyboard Timeline:** 상단 비주얼 타임라인 프로그레스 바(`3s Hook` / `10s Sizzle Demo` / `3.5s Payoff` / `3.5s Offer`) + 하단 초 단위 콘티·카피·사운드 그리드.
5. **Archetype E — Dark Contrast Finale:** `#19171C` 다크 스테이지 위에 `#F5FF63` · `#B593FF` 액센트로 로드맵과 즉시 실행 액션 아이템을 마감.

---

## 6. 화장품 광고 기획서 전용 컴포넌트 (Pinterest 뷰티 레퍼런스 결합)

핀터레스트 한국 화장품 광고 레퍼런스 분석 결과를 반영하여, 텍스트 나열형 보고서가 아닌 **실제 집행 소재의 레이아웃이 눈앞에 그려지는 시각 목업 컴포넌트**를 슬라이드 내부에 배치한다.

1. **20–55–25 뷰티 광고 황금 구도 와이어프레임 (4:5 & 9:16 Mockup Card)**
   - **상단 20% (Hook Zone):** 질문형 고통 저격 카피 또는 대형 임상 수치 배지(`흡수율 461%`, `10초 노워시`).
   - **중앙 55% (Visual Proof Zone):** 제품 단독 정물 지양 → **제품 보틀 + 물리적 제형 스와치(마이크로 버블 피크) + 피부 광채 클로즈업** 트라이어드(Triad) 배치 및 포인터 인출선(`Pointer Callout`) 연결.
   - **하단 25% (Conversion Zone):** 좌측 2줄 핵심 베네핏 요약 + 우측 고대비 오퍼 배지(`UP TO 46% OFF + GIFT`).
2. **데이터 배지 & 벤치마크 스탬프**
   - 모든 기획 시안 옆에는 기대 지표(`Target Hook Rate ≥ 30%`, `Expected ROAS 3.5x+`)와 레퍼런스 검증 근거(달바·바이오던스·메디큐브·AI 숏폼 벤치마크)를 캡슐 태그로 명시해 설득력을 고정한다.
