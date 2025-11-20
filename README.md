# Analysis of Semiconductor Lot Post CMP Thickness: CVD Chamber & Etch Test Effects

- “Analyzing Post CMP thickness across 25 wafers, focusing on the effects of CVD chamber and Etch test on thickness variation. Includes boxplots, main effect plots, and specification limits.”
- 25개 웨이퍼의 CMP 이후 Post Thickness를 분석하며, CVD 챔버와 Etch 테스트가 두께 변동에 미치는 영향을 평가합니다. Boxplot, Main Effect Plot, 규격선 포함.

# 1. 데이터 설명
- Lot 구성: 25 wafers
- 공정 이력: CMP 공정 이후 Post Thickness 측정
- 공정 변경 요소:
  
| 구분   | 내용                                            |
| ---- | --------------------------------------------- |
| CMP  | Dressing step –2 sec (#1~12), –4 sec (#13~25) |
| Etch | 테스트 이력 (test1~test5) 혼재                       |
| CVD  | 테스트 이력 및 Chamber A/B/C 존재                     |

- 데이터 컬럼 구조 :

| Column              | Description                 |
| ------------------- | --------------------------- |
| `S Lot`             | Wafer Lot 번호 (#1~#25)       |
| `Post Thickness(A)` | CMP 이후 박막 두께                |
| `dressing step sec` | CMP dressing 조정값 (2 / 4)    |
| `Etch Si RIE`       | Etch 후 Si RIE 두께            |
| `Chamber`           | CMP 장비 Chamber (A / B / C)  |
| `Etch test 적용 이력`   | Etch process test condition |
| `CVD test 적용 이력`    | CVD process test condition  |



# 2. 공정능력지수
 - dressing step 시간 단축 테스트 적용된 CMP 공정의 post thickness 데이터
 - CMP 공정능력

    Mean=5154.48, Std=180.84

    Cp=0.737, Cpk=0.453
   
<img width="869" height="564" alt="image" src="https://github.com/user-attachments/assets/77c26129-736b-42d2-90b2-b3b68ccaca36" />




 - Etch Si RIE post thickness 데이터
 - Etch 공정능력
 
    Mean=4798.16, Std=85.73

    Cp=1.555, Cpk=0.771

<img width="861" height="563" alt="image" src="https://github.com/user-attachments/assets/42b00787-c313-45c1-8928-291e2227c6cd" />







# 3. I-MR 관리도
   *슈하트 규칙 적용
   
(1) dressing step 2초 하향 적용
  <img width="1169" height="564" alt="image" src="https://github.com/user-attachments/assets/fa41cfa5-108c-421a-82fb-8ad8e0541db7" />


  <img width="1160" height="564" alt="image" src="https://github.com/user-attachments/assets/19b1aa6a-241b-4b79-8170-81eb99499d53" />


 - #3 (Value=5455): Rule 1: Beyond control limit
 - #9 (Value=5411): Rule 1: Beyond control limit

   
(2) dressing step 4초 하향 적용
  <img width="1169" height="564" alt="image" src="https://github.com/user-attachments/assets/d98f80f0-054f-4c6f-9d24-c1447b40ca0d" />


  <img width="1160" height="564" alt="image" src="https://github.com/user-attachments/assets/b353bad0-561d-4f26-a17b-44bbd2262fbd" />


 - #21 (Value=5477): Rule 1: Beyond control limit



# 4. Etch  테스트 적용 이력 분석

- 각 테스트 별 구간 그림
  
<img width="857" height="544" alt="image" src="https://github.com/user-attachments/assets/98caff69-419a-4a99-a735-be98626daa1b" />


<img width="702" height="545" alt="image" src="https://github.com/user-attachments/assets/a13e41a2-7533-4c89-9cd5-954e5ce69723" />


#그룹별 통계치  
- test1
  - mean  = 4685.4
  - std   = 26.101724
  - count = 5

- test2           
  - mean  = 4929.4
  - std   = 19.705329
  - count = 5

#t-test 결과:

t=-16.683, p=0.0000

결론: 각각 적용된 테스트의 결과가 유의하다, 두 그룹간 차이가 존재



# 5. CVD 챔버별 통계 분석
   
(1) 상자그림 & 주효과도

<img width="1189" height="490" alt="image" src="https://github.com/user-attachments/assets/1fe40ba9-3d34-4071-9565-8ef0e7d17fa1" />




결론: CVD 챔버 C의 이상으로 박막 두께가 지나치게 두꺼워지는 현상이 있었음을 발견



# CMP post thickness 데이터 기반 CVD 테스트 이력 분석의 타당성 검증  

CMP 공정의 post thickness 데이터로 CVD 공정테스트 이력을 분석하는 것은 적절하지 않을 수 있다. 따라서 dressing step 별로 전체 데이터를 나누고, 그 안에서 챔버 A,B,C의 상자그림, 주효과도를 분석해 보았다.

(1) dressing step 2초 하향 

<img width="1189" height="495" alt="image" src="https://github.com/user-attachments/assets/8e99f71a-a002-4388-a88c-1b885d8119f9" />




(2) dressing step 4초 하향

<img width="1189" height="495" alt="image" src="https://github.com/user-attachments/assets/fb0ae2a7-c796-433f-9737-03b62ed4f683" />




결론 : 그래프 양상이 비슷하고, 2가지 테스트 모두 C챔버가 상한을 벗어나는 것이 확인된다. CMP 공정의 효과보다도 CVD 챔버의 영향이 크다는 것을 확인할 수 있다. 



