# 논문 추천 — 2026-08-19

- **연구 기준일(research date):** 2026-08-19 (`REQUESTED_DATE` 값 사용)
- **실제 검색 창(window):** 2026-07-20 ~ 2026-08-19 (30일 창; 1일·7일 창에서는 결과 0건)
- **검색 쿼리:** `chest radiograph deep learning generalization`

## 코호트 요약 (집계 수준, 환자 단위 값 없음)

- 총 검사 건수: 272건 (고유 환자 153명)
- 성별: 남성 136 / 여성 136
- 연령: 최소 9세 ~ 최대 87세, 평균 약 51.5세
- 촬영 자세(view position): PA 184건 / AP 88건
- 기관(institution_code) 분포: INST01 62, INST02 56, INST03 54, INST04 48, INST05 52 — 5개 기관에 비교적 고르게 분포
- 주요 소견(findings_label, 상위): No Finding 145, Infiltration 21, Atelectasis 16, Nodule 7, Fibrosis 6, Effusion 6, Cardiomegaly 5, Pneumothorax 5, 복합 소견(Effusion+Infiltration 등) 다수
- 모든 레코드는 `is_synthetic = true` (합성 데이터)

## 선정 기준

`search-papers`가 30일 창에서 반환한 후보 중, 순수 방법론 제안(예: 이미지 합성, 인과 그래프 리뷰, 음성 진단)보다 **다기관 코호트, 외부 검증, 실제 판독 워크플로우와 맞닿은 논문**을 우선 채택했다. 아래 3편은 모두 다기관 데이터에서의 일반화·해석가능성을 다루며, 임상의가 직접 판단에 활용하거나 검증 설계에 참고할 수 있는 결과를 포함한다.

## 축 (Axes)

- **기관 간 일반화**: 여러 기관/사이트에서 수집한 데이터 간 모델 성능 이전과 안정성
- **판독 소견 연계 해석가능성**: 자유 텍스트 판독 소견을 모델 예측/분할의 근거로 연결하는 방법

## 선정 논문

### 1. CLEAR: an auditable foundation model for radiology grounded in clinical concepts
- **venue / source:** Nature Biomedical Engineering (OpenAlex)
- **링크:** https://doi.org/10.1038/s41551-026-01741-4
- **관련성:** 우리 코호트는 5개 기관, PA/AP 혼합, 다양한 흉부 소견으로 구성되어 CLEAR가 검증한 다기관·다소견 환경과 구조적으로 유사하다. 개념 단위 설명은 소규모 코호트에서도 판독의에게 실질적인 근거 제시 방식이 될 수 있다.
- **한계:** CLEAR의 학습·검증 규모(87만 쌍, 23만 명)에 비해 우리 데이터(272건)는 훨씬 작아 동일 성능 재현 여부는 확인 불가.

### 2. Grounding Radiology Report Findings into Medical Image Segmentation (CF2Seg)
- **venue / source:** npj Digital Medicine (OpenAlex)
- **링크:** https://doi.org/10.1038/s41746-026-03051-0
- **관련성:** 판독문(report_text, clinical_info)이 존재하고 병소가 단독/복합으로 기록된 우리 데이터 구조는 텍스트-이미지 결합 분할 접근이 활용 가능한 형태다.
- **한계:** 픽셀 단위 전문가 주석이 없어 분할 정확도나 병소 부담 정량화 검증은 불가능.

### 3. QoQ-Med3: a multimodal reasoning foundation model for clinical analysis
- **venue / source:** npj Digital Medicine (OpenAlex)
- **링크:** https://doi.org/10.1038/s41746-026-02945-3
- **관련성:** 5개 기관에 고르게 분포한 우리 코호트 구조는 QoQ-Med3가 다룬 사이트 간 이질성 문제와 맞닿아 있어, 기관 교차 검증(leave-one-institution-out) 설계 참고에 유용하다.
- **한계:** 단일 모달리티(흉부 X-ray)만 있어 다중모달 성능 향상이나 환각률 개선 효과는 이 데이터로 확인 불가.

---

**주의:** 위 추천은 자동 검색 및 코호트 통계 기반 초안이며, 임상 적용 여부는 반드시 담당 의사의 검토를 거쳐야 합니다.
