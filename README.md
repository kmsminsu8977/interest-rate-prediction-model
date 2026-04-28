# Interest Rate Prediction Model

금리 예측 모델 프로젝트의 기본 연구 구조와 재현 가능한 baseline 산출물을 담은 저장소입니다.

**핵심 연구 질문**

> 물가, 고용, 기간스프레드, 신용스프레드는 금리 상방/하방 압력을 어떻게 다르게 만든다?

## 범위와 원칙

- KAIST-DFMBA 과정에서 제공받은 원본 소스, 강의자료, 표, 데이터는 그대로 포함하지 않습니다.
- 샘플 데이터는 개념 설명을 위해 새로 만든 합성 값입니다.
- 설명은 원문 복제가 아니라 프로젝트 흐름에 맞춘 직관적 요약으로 작성했습니다.

## 저장소 구조

```text
interest-rate-prediction-model/
├── src/                         # baseline 계산 로직과 실행 엔트리포인트
├── data/sample/                 # 합성 샘플 입력 데이터
├── docs/                        # 방법론과 해석 기준
├── notebooks/                   # 실행 흐름을 보여주는 최소 노트북
├── outputs/tables/              # 재현 가능한 결과 CSV
├── presentation/                # 발표/보고서 초안
└── references/                  # 재작성 개념 노트와 참고문헌 메모
```

## 빠른 시작

```bash
python -m src.run_baseline
```

실행 결과는 `outputs/tables/baseline_results.csv`에 저장됩니다.

## 구현 범위

- 각 거시 변수를 표준화한 뒤 직관적 부호를 반영한 선형 점수로 변환한다.
- 점수는 방향성 학습용이며 실제 중앙은행 반응함수를 대체하지 않는다.
- 데이터는 합성 macro panel로 구성했다.

## 주요 파일

- `src/interest_rate_baseline.py`: 거시 변수의 방향성 신호를 단순 점수화해 다음 금리 변화 압력을 추정한다.
- `data/sample/macro_rate_panel.csv`: baseline 실행용 합성 입력값
- `docs/methodology.md`: 계산 절차, 입력/출력 정의, 해석상 주의점
- `outputs/tables/baseline_results.csv`: 현재 baseline 산출물

## 다음 확장 방향

- 실제 공개 데이터 또는 별도 수집 데이터 연결
- notebook 기반 탐색 분석 추가
- 차트와 표를 포함한 최종 보고서 작성
- 모델 검증, 민감도 분석, 비용/리스크 가정 보강
