# Korean-Diff-Font PoC — 1-shot 한글 폰트 생성 검증

[fonts](https://github.com/webdosa123/fonts) (private) 의 AI 트랙 Phase 0 검증용 Colab 노트북 분리 저장소.

fonts 본체는 private 으로 유지, Colab GitHub 통합이 private repo 의 새 변경을 fetch 못 하는 제약을 우회하기 위해 노트북만 public 에 둠.

## Phase 0 — Colab 1 클릭 실행

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/webdosa123/korean-diff-font-poc/blob/master/notebooks/ai_font_poc.ipynb)

T4 GPU 선택 → `Runtime → Run all` (1~3 분).

## Phase 0 종결 기준 (사전 정의)

| 결과 | 다음 |
|---|---|
| 9 글자 *가나다라마바사아자* 식별 가능 + 스타일 따라옴 | Phase 1 (전체 11,172 음절 생성) |
| 9 글자 나오지만 *가나다 아닌 다른 글자* | 종결 — 학습 chara.txt 미공개로 라벨 매핑 복원 불가 |
| 9 글자 *맞게* 나오지만 *스타일 제각각* | 종결 — style transfer 자체 약함 |

자세한 설계 근거 + 모델 선정 비교는 메인 fonts repo 의 `docs/ai-font-poc.md`.

## 참조 모델

[Korean-Diff-Font](https://github.com/ORI-Muchim/Korean-Diff-Font) (ORI-Muchim, 2023) — 한글 11,172 자 사전학습 ckpt 공개.
