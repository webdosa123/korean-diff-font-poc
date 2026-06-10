# Korean-Diff-Font PoC — 1-shot 한글 폰트 생성 검증

[fonts](https://github.com/webdosa123/fonts) (private) 의 AI 트랙 Phase 0 검증용 Colab 노트북 분리 저장소.

fonts 본체는 private 으로 유지, Colab GitHub 통합이 private repo 의 새 변경을 fetch 못 하는 제약을 우회하기 위해 노트북만 public 에 둠.

## 메인 — pipeline.ipynb (v2, 층화 측정)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/webdosa123/korean-diff-font-poc/blob/master/notebooks/pipeline.ipynb)

T4 GPU 선택 → `Runtime → Run all` (~15 분).  Run all 한 번으로:

- 층화 9 자 (단순 가나사 / 홑받침 한글정 / 겹받침 값삶닭) × 8 샘플 생성 (시드 고정)
- 프로토타입 분류기 (11,172 자) + easyocr 이중 판독 → coverage
- KS X 1001 2,350 자 / 전체 11,172 자 생성 비용 자동 외삽 → Phase 1 진행 판정 데이터

`ai_font_poc.ipynb` 는 7 라운드 디버그 기록용 (실행 비권장).

## 판정 가이드

| 외삽 결과 | 다음 |
|---|---|
| 2,350 자 ≈ 25 GPU·h 이하 | 프리뷰 품질 폰트 Phase 1 현실권 (다중생성+선택) |
| 겹받침 클래스 도달 실패 | 부분 문자셋 또는 학습 트랙 (production 은 어차피 학습 필요) |

자세한 설계 근거 + 모델 선정 비교는 메인 fonts repo 의 `docs/ai-font-poc.md`.

## 참조 모델

[Korean-Diff-Font](https://github.com/ORI-Muchim/Korean-Diff-Font) (ORI-Muchim, 2023) — 한글 11,172 자 사전학습 ckpt 공개.
