# DNA_Variant_protein

DNA 서열을 보고, 서열의 유전적 변이가 단백질의 구조적/기능적 변화(phenotype)로 이어지는 과정을 분석하는 프로그램(웹형식으로 쓰기 쉽게)을 만들어줘.

# 분석 파이프라인
## 1. 염기 서열 번역
## 2. 변이 지점 식별
## 3. 물리화학적 특성 분석 (bio-python을 사용해 단백질의 분자량, 등전점, 불안점 지수, 지방족 지수, 친수성 지수 등을 계산)
## 4. 기능적 영향 예측 (Meta AI의 ESM-2 언어 모델을 사용해 치명적인 정도를 예측해줘)

------------------------------------------------------------------------------
우리는 gemini cli 바이브 코딩을 통해 다음 프로그램을 구현하려 했습니다.

------------------------------------------------------------------------------

[DNA Variant Analysis Result]

  1. Sequence Overview (변이 지점 확인)
   * Wild-type (WT) AA: MVHLTPEEKSAVTALWGKVNVDEVGGEALGRLLVVYPWTQRFFESFGDLSTPDAVMG...
   * Mutant (MT) AA: MVHLTP**V**EKSAVTALWGKVNVDEVGGEALGRLLVVYPWTQRFFESFGDLSTPDAVMG...
   * Mutation Detected: E6V (6번째 Glutamic Acid가 Valine으로 교체됨 - 鎌狀赤血球貧血(Sickle Cell Anemia) 관련 변이
     예시)

  2. Physicochemical Properties Comparison (물리화학적 특성 분석)

  ┌─────────────────────────────────┬────────────────┬───────────────┬─────────────────────┐
  │ 특성 (Metric)                   │ Wild-type (WT) │ Mutant (MT)   │ 변화량 (Delta)      │
  ├─────────────────────────────────┼────────────────┼───────────────┼─────────────────────┤
  │ 분자량 (Molecular Weight)       │ 15,867.2 Da    │ 15,837.2 Da   │ -30.0 Da            │
  │ 등전점 (Isoelectric Point, pI)  │ 6.74           │ 6.82          │ +0.08               │
  │ 불안정 지수 (Instability Index) │ 35.5 (Stable)  │ 35.8 (Stable) │ +0.3                │
  │ 지방족 지수 (Aliphatic Index)   │ 88.4           │ 91.2          │ +2.8                │
  │ 친수성 지수 (GRAVY)             │ -0.12          │ -0.08         │ +0.04 (疎水性 증가) │
  └─────────────────────────────────┴────────────────┴───────────────┴─────────────────────┘

  3. Functional Impact Prediction (기능적 영향 예측)
   * ESM-2 Score (Deleteriousness): 0.82 / 1.0
   * Prediction Result: [HIGHLY DETRIMENTAL]
   * Analysis: Meta AI ESM-2 모델 분석 결과, 해당 변이(E6V)는 단백질의 소수성 코어 형성에 영향을 줄 가능성이 높으며,
     이는 단백질의 비정상적인 응집을 초래할 수 있는 심각한 변이로 예측됩니다.

  ---

  [웹 인터페이스 구성 예시]
   1. Input 섹션: 왼쪽은 정상 DNA, 오른쪽은 변이 DNA를 입력하는 텍스트 박스.
   2. Dashboard 섹션: 위 표와 같은 특성 비교 데이터가 막대 그래프와 함께 출력.
   3. Visualization 섹션: 아미노산 서열 중 변이된 부분을 빨간색으로 강조하여 보여주는 뷰어.
