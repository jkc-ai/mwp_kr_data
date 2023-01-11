# MWP_KR_DATA
AI Grand Challenge 5차 대회에 활용한 한국어 서술형 수학문제 데이터셋을 공개합니다.
훈련 및 테스트에 활용한 데이터셋 중 시중 참고서에서 발췌된 데이터셋 등 일부 데이터를 제외하였습니다.  

- 공개 계획
- [ ] 자체구축 데이터 공개
- [ ] 산술연산 문제가 아닌 문제들의 수식 정규화
- [ ] 발췌 데이터 등 라이센스 확인 후 추가 공개


## 1. 데이터 구성
**자체제작** 데이터는 총 9,058개의 한국어 수학 문제와 답, 그리고 수식으로 구성되어 있습니다. 각 데이터는 9개의 유형로 구분되며,    
유형의 종류와 유형 별 문제 수는 아래와 같습니다.



| No   | 유형      | 유형별 개수 | 발췌 개수 | 자체제작 개수 |
|------|---------|------|-----|-------|
| 1    | 산술연산    | 6781   | 5305  | 1476    |
| 2    | 순서정하기1* | 516    | 0     | 516     |
| 3    | 순서정하기2  | 1292   | 0     | 1292    |
| 4    | 조합하기    | 1487   | 1152  | 335     |
| 5    | 수찾기1    | 2695   | 2651  | 44      |
| 6    | 수찾기2    | 2351   | 313   | 2038    |
| 7    | 수찾기3    | 1553   | 353   | 1200    |
| 8    | 크기비교    | 2021   | 534   | 1487    |
| 9    | 도형      | 2241   | 1570  | 671     |
| -    | 전체      | 20948  | 11878 | 9070    |

* "순서정하기1"은 정답이 산술연산 수식으로 표현되는 경우이며, "순서정하기2"는 문제에 나오는 명칭이 정답인 경우입니다.



## 2. 유형별 문제 예시

데이터는 JSON으로 작성하였으며, 데이터 구조 및 각 유형별 예시는 다음과 같습니다.

- 데이터 구조
    - `class`, `question`, `answer`, `equation`은 모든 유형의 문제들이 공통적으로 사용합니다.
    - `option`, `option_value`, `unknown`은 유형에 따라 사용할지 정해집니다.
    - 특정 키를 사용하는 유형이라도 일부 문제들은 "none"값을 가집니다.
```
{
    문제 번호 (타입: 문자열): {
        "class": "문제 유형" (타입: 문자열),
        "question": "문제" (타입: 문자열),
        "answer" : "답" (타입: 문자열),
        "equation": "수식" (타입: 문자열),
        "option": "보기" (타입: 문자열),
        "option_value": "보기 값을 구하는 수식" (타입:문자열),
        "unknown": "미지수 값을 구하는 수식/정보" (타입: 문자열)
    },
    ...
}
```

- 유형별 예시

    - 산술연산
    ```
    {
        "class": "산술연산",
        "question": "수연이는 하루에 25쪽 씩 3일 동안 모두 읽은 동화책을 다시 읽으려고 합니다. 동화책의 전체 쪽수는 몇 쪽일까요?",
        "answer": "75",
        "equation": "25*3",
        "option": "none",
        "option_value": "none",
        "unknown": "none"
    }
    ```

    - 순서정하기1
    ```
    {
        "class": "순서정하기1",
        "question": "아이스크림을 기다리는 줄에서 원준이는 앞에서 여섯째, 뒤에서 셋째에 서있다고 합니다. 아이스크림을 기다리는 사람은 전부 몇 명일까요?",
        "answer": "8",
        "equation": "6+3-1",
        "option": "none",
        "option_value": "none",
        "unknown": "none"
    },
    ```

    - 순서정하기2
        - option : 정답 후보들에 해당하거나 equation에서 X에 해당하는 값
    ```
    {
        "class": "순서정하기2",
        "question": "다람쥐가 도토리 주머니를 도토리가 적게 담긴 순서대로 땅속에 넣어두려 합니다. 도토리 주머니에는 도토리가 각각 10, 20, 50, 40, 30개 들어있습니다. 땅속에 두 번째로 넣어야 하는 도토리 주머니에는 도토리가 몇 개 들어있을까요?",
        "answer": "20",
        "equation": "find_min(sort(X),2)",
        "option": "10, 20, 50, 40, 30",
        "option_value": "none",
        "unknown": "none"
    }
    ```

    - 조합하기
    ```
    {
        "class": "조합하기",
        "question": "지혜는 주사위 3개를 던져서 윗면에 나온 세 눈의 수를 모두 사용하여 분수를 만들려고 합니다. 만들 수 있는 가장 작은 대분수를 구하세요.",
        "answer": "(7/6)",
        "equation": "min(A)",
        "option": "none",
        "option_value": "none",
        "unknown": "none"
    }
    ```

    - 수찾기1
        - unknown : 미지수를 구하기 위한 정보 (리스트)
    ```
    {
        "class": "수찾기1",
        "question": "영석이네 모둠 학생들이 한 뼘의 길이를 조사했더니, 영석이는 15.5cm, 은수는 13.7cm, 민정이는 14.3cm, 동규는 14.9cm이 나왔습니다. 영석이네 모둠 학생들의 한 뼘의 길이의 평균은 몇 cm인지 구하세요.",
        "answer": "14.6",
        "equation": "sum(X)/4",
        "option": "none",
        "option_value": "none",
        "unknown": "X=[15.5, 13.7, 14.3, 14.9]"
    }
    ```

    - 수찾기2
        - unknown : 미지수를 구하기 위한 수식
    ```
    {
        "class": "수찾기2",
        "question": "8*4A=336일때, A를 구하시오.",
        "answer": "2",
        "equation": "A",
        "option": "none",
        "option_value": "none",
        "unknown": "8*4A=336"
    }
    ```

    - 수찾기3
    ```
    {
        "class": "수찾기3",
        "question": "어떤 수에 3.4를 곱해야 할 것을 잘못하여 더했더니 15.2가 되었습니다. 바르게 계산한 값에 8을 곱하면 얼마인지 구하시오.",
        "answer": "320.96",
        "equation": "(15.2-3.4)*3.4*8",
        "option": "none",
        "option_value": "none",
        "unknown": "none"
    }
    ```

    - 크기비교
        - option: 정답 후보들에 해당
        - option_value: 후보별 대입할 값
    ```
    {
        "class": "크기비교",
        "question": "민준이의 책장에는 책이 모두 60권 있습니다. 그중 22권은 위인전이고, 26권은 동화책입니다. 나머지는 모두 시집일 때 민준이의 책장에 가장 많이 꽃혀있는 책은 무엇입니까?",
        "answer": "동화책",
        "equation": "max(위인전, 동화책, 시집)",
        "option": "위인전, 동화책, 시집",
        "option_value": "위인전=22, 동화책=26, 시집=60-22-26",
        "unknown": "none"
    }
    ```

    - 도형
    ```
    {
        "class": "도형",
        "question": "삼각형의 밑변이 7cm, 넓이가 21cm2일 때 높이는 몇 cm인지 구하세요.",
        "answer": "6",
        "equation": "21*2/7",
        "option": "none",
        "option_value": "none",
        "unknown": "none"
    }
    ```


## 3. 지원

이 연구개발은 2022년도 정부(과학기술정보통신부)의 재원으로 정보통신기획평가원의 지원을 받아 수행한 연구 성과물의 일부입니다. 해당 연구과제에 대한 정보는 아래와 같습니다.

과제번호: 2021-0-02314  
연구사업명: 인공지능산업원천기술개발  
연구과제명: 서술형 수학문제 해결을 위한 목표 기반 트리 구조 예측 자연어처리 모델 개발  
주관연구기관: 주식회사 젠티  
공동연구기관: 한국원자력연구원 (인공지능응용전략실)  


## 4. 데이터셋 구축 방법
저희가 공개한 한글 서술형 수학문제 데이터셋은 아래와 같이 크게 2가지의 방법으로 구축하였습니다.

1. 셀렉트스타 주식회사가 수행한 [수학문제 관련 데이터 수집 및 가공] 용역을 통해 구축된 데이터의 일부
2. 연구참여자 자체 구축한 데이터 일부


## 5. 참여자
최은진, 허태일, 신동현, 정지영, 장경환, 유용균, 고태영, 전태현, 김민종, 임지연, 이상원, 조희철, 임소영