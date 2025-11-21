 “Analyzing Post CMP thickness across 25 wafers, focusing on the effects of CVD chamber and Etch test on thickness variation.”  
 25개 웨이퍼의 CMP 이후 Post Thickness를 분석하며, CVD 챔버와 Etch 테스트가 두께 변동에 미치는 영향을 평가합니다.

# 1. 데이터 설명
- Lot 구성: 25 wafers
- 공정 이력: CMP 공정 이후 Post Thickness 측정
- 공정 변경 요소:
  
| 구분   | 내용                                            |
| ---- | --------------------------------------------- |
| CMP  | Dressing step –2 sec (#1 - #12) / -4 sec (#13 - #25) |
| Etch | 테스트 이력 (test1 - test5)                       |
| CVD  | 테스트 이력 및 Chamber A/B/C 존재, 별도의 Thickness data 없음 |

- 데이터 컬럼 구조 :

| Column              | Description                 |
| ------------------- | --------------------------- |
| `S Lot`             | Wafer Lot 번호 (#1-#25)       |
| `Post Thickness(A)` | CMP 이후 박막 두께             |
| `dressing step sec` | CMP dressing 조정값 (2 / 4)   |
| `Etch Si RIE`       | RIE 이후 박막 두께               |
| `Chamber`           | CMP 장비 Chamber (A / B / C)    |
| `Etch test 적용 이력`   | Etch process test condition |
| `CVD test 적용 이력`    | CVD process test condition  |



# 2. 박막 두께 기반 CMP·Etch 공정 성능 분석  

[CMP 공정]  

 - dressing step 시간 단축 테스트 적용된 CMP 공정의 post thickness 데이터
 - CMP Post Target : 5000A +/- 400A
 - 테스트 이력이 포함된 데이터임을 감안해 각 이력 별 평균의 이동 점검  


1) 전체 25개 기준  
 -  평균(전체): 5154.48 Å  
 -  σ_CMP = 133.33 Å  
 -  Cp = 1.00  
 -  Cpk = 0.614  

<img width="790" height="490" alt="image" src="https://github.com/user-attachments/assets/7fb2bf1b-41f1-4b17-b223-7c58335c56ce" />  


2) Dressing 2 sec (#1~12)  
 -  평균: 5181.83 Å  
 -  σ_CMP = 133.33 Å  
 -  Cp = 1.00  
 -  Cpk = 0.545  

<img width="790" height="490" alt="image" src="https://github.com/user-attachments/assets/e7379023-c986-4c0c-801d-7609f9d0346a" />  



3) Dressing 4 sec (#13-25)  
 -  평균: 5129.23 Å  
 -  σ_CMP = 133.33 Å  
 -  Cp = 1.00  
 -  Cpk = 0.677  

<img width="790" height="490" alt="image" src="https://github.com/user-attachments/assets/5984b3b6-505c-4fcd-b336-a8855c1e1451" />  


CMP 공정 Spec 기반 시그마 σ = 133.333

=== [CMP] 전체 LOT 기준 공정 능력 (Spec 기반 σ 기준 ) ===   
표본 평균 = 5154.48   
표본 표준편차 = 180.84    
Cp   = 1.000    
Cpk  = 0.614    

=== [CMP] 그룹별 Capability 요약 (Spec 기반 σ 기준) ===  
|        Group |  N   | Mean | Cp |  Cpk |
| ------------ | ---- | ---- | --------- | ----------- |
|          All | 25 | 5154.480  |    1.0  |     0.614 |
|  Dressing 2s | 12 | 5181.833  |    1.0  |     0.545 |
|  Dressing 4s | 13 | 5129.231  |    1.0  |     0.677 |
|    Chamber A |  9 | 5033.333  |    1.0  |     0.917 |
|    Chamber B |  8 | 5053.875  |    1.0  |     0.865 |
|    Chamber C |  8 | 5391.375  |    1.0  |     0.022 |  


결론: CMP 공정 후 박막데이터 중 챔버 C의 Cpk가 크게 떨어짐 -> 챔버 C에 이상이 있을 가능성이 있다  




[Etch 공정]  

 - Etch Si RIE post thickness 데이터
 - Etch Post Target : 4800A +/-150A  

 전체 25개 기준 
  -  평균 = 4798.16  
  -  σ_Etch = 50.00 Å  
  -  Cp = 1.00  
  -  Cpk = 0.988  

<img width="790" height="490" alt="image" src="https://github.com/user-attachments/assets/1df427cf-a092-43cf-82d5-f9d64c221939" />  



Etch 공정 Spec 기반 σ = 50.000

=== [Etch] 전체 LOT 기준 공정 능력 (설계 σ 기준) ===  
표본 평균 = 4798.16   
표본 표준편차 = 85.73  
Cp_design   = 1.000  
Cpk_design  = 0.988  

=== [Etch] 그룹별 Capability 요약 (설계 σ 기준) ===  
|           Group  |  N   |   Mean   | Cp | Cpk |
| ---------------- | ---- | -------- | --------- | ---------- |
|              All |  25  | 4798.160 |       1.0 |      0.988 |
|  Etch test=test1 |   5  | 4685.400 |       1.0 |      0.236 |
|  Etch test=test2 |   5  | 4929.400 |       1.0 |      0.137 |
|        Chamber A |   9  | 4796.778 |       1.0 |      0.979 |
|        Chamber B |   8  | 4793.625 |       1.0 |      0.958 |
|        Chamber C |   8  | 4804.250 |       1.0 |      0.972 |

결론: Etch 테스트의 영향으로 테스트 이력 2가지에서 Cpk가 낮게 계산됨  



# 3. I-MR 관리도
   *넬슨 규칙 적용

전체 관리도  

<img width="989" height="390" alt="image" src="https://github.com/user-attachments/assets/6f98f96a-6e95-44ab-b4e4-fa3f853f40d9" />  

<img width="989" height="390" alt="image" src="https://github.com/user-attachments/assets/4aed4a2b-dadb-40f4-a5b3-c4212589bbe5" />  


=== Design-based parameters ===  
TARGET(CL) = 5000  
LSL = 4600, USL = 5400  
Design sigma = 133.333

=== MR-Chart parameters (data-based) ===  
MR_bar = 248.04, UCL_MR = 810.35  

=== Nelson 8 Rules 위반 (Wafer 번호 기준) ===  
rule1: ['#3', '#9', '#21']  
rule2: []  
rule3: []  
rule4: []  
rule5: []  
rule6: []  
rule7: []  
rule8: []  
all_viol: ['#3', '#9', '#21']  

=== Nelson 8 Rules 위반 Wafer 상세 ===
| S Lot | Post Thickness(A) | dressing step sec | Chamber | Etch Si RIE | Etch test 적용 이력 | CVD test 적용 이력 |
| ------| ----------------- | ----------------- | ------- | ----------- | ------------------ | ------------------- |
|  #3   |            5455   |               2   |     C   |      4695   |            test1   |            NaN      | 
|  #9   |            5411   |               2   |     C   |      4785   |              NaN   |          test3      |
|  #21  |            5477   |               4   |     C   |      4812   |              NaN   |          test5      |


결론: 공통적으로 챔버 C 에서 spec out이 발생함 -> 챔버 C에 이상이 있을 가능성이 있다   
 

# 4. CVD 챔버별 박스플롯
   
(1) CMP 상자그림

<img width="630" height="454" alt="image" src="https://github.com/user-attachments/assets/6d1122f7-7d8d-426e-a2fd-5050b4427dae" />


(2) Etch 상자그림

<img width="630" height="454" alt="image" src="https://github.com/user-attachments/assets/b9a89d23-7dca-4225-8c12-467dfb3ebc0d" />



결론:   
-Etch 공정은 CVD 공정 이전에 진행되어 CVD 챔버의 영향을 받지 않았음  
-CVD 챔버 C의 이상으로 박막 두께가 목표치보다 지나치게 두꺼워지는 현상이 있었음을 발견



# 5. Etch  테스트 적용 이력 분석  
- CMP 공정의 테스트효과는 챔버 C의 영향으로 정상적인 분석이 불가능 -> Etch 테스트의 효과만 별도로 점검  
- 각 테스트 별 구간 그림  
  
<img width="630" height="454" alt="image" src="https://github.com/user-attachments/assets/45ed7420-6742-44cc-921b-1a843aee6f8a" />  



=== 단일표본 t-검정 ===  

1) test1 
  n=5, mean=4685.400, std=26.102  
  t=-9.817, p=0.00060  
  → test1 결과가 유의하다 (mean shift 있음)  

2) test2   
  n=5, mean=4929.400, std=19.705  
  t=14.684, p=0.00013  
  → test2 결과가 유의하다 (mean shift 있음)  
  
#t-test 결과  
결론: 각각 적용된 테스트의 결과가 유의하다  





# CMP post thickness 데이터 기반 CVD 테스트 이력 분석의 타당성 검증  

CMP 공정의 post thickness 데이터로 CVD 공정테스트 이력을 분석하는 것은 적절하지 않을 수 있다. 따라서 dressing step 별로 전체 데이터를 나누고, 그 안에서 챔버 A,B,C의 상자그림, 주효과도를 분석해 보았다.

(1) dressing step 2초 하향 

<img width="1189" height="495" alt="image" src="https://github.com/user-attachments/assets/8e99f71a-a002-4388-a88c-1b885d8119f9" />




(2) dressing step 4초 하향

<img width="1189" height="495" alt="image" src="https://github.com/user-attachments/assets/fb0ae2a7-c796-433f-9737-03b62ed4f683" />




결론 : 그래프 양상이 비슷하고, 2가지 테스트 모두 C챔버가 상한을 벗어나는 것이 확인된다. CMP 공정 테스트의 효과보다도 CVD 챔버 이상의 영향이 크다는 것을 확인할 수 있다. 



