# MWP_KR_DATA
AI Grand Challenge 5차 대회에 활용한 한국어 서술형 수학문제 데이터셋을 공개합니다.
훈련 및 테스트에 활용한 데이터셋 중 시중 참고서에서 발췌된 데이터셋 등 일부 데이터를 제외하였습니다.  

- 공개 계획
- [ ] 자체구축 데이터 공개
- [ ] 산술연산 문제가 아닌 문제들의 수식 정규화
- [ ] 발췌 데이터 등 라이센스 확인 후 추가 공개

## 1. 데이터 구성
자체제작 데이터는 총 9,070개의 한국어 수학 문제와 답, 그리고 수식으로 구성되어 있습니다. 각 데이터는 9개의 유형로 구분되며,    
유형의 종류와 유형 별 문제 수는 아래와 같습니다.



| No   | 유형      | 유형별 개수 | 발췌 개수 | 자체제작 개수 |
|------|---------|------|-----|-------|
| 1    | 산술연산    | 6785   | 5305  | 1480    |
| 2    | 순서정하기1* | 516    | 0     | 516     |
| 3    | 순서정하기2  | 1292   | 0     | 1292    |
| 4    | 조합하기    | 1493   | 1152  | 341     |
| 5    | 수찾기1    | 2696   | 2651  | 45      |
| 6    | 수찾기2    | 2351   | 313   | 2038    |
| 7    | 수찾기3    | 1553   | 353   | 1200    |
| 8    | 크기비교    | 2021   | 534   | 1487    |
| 9    | 도형      | 2241   | 1570  | 671     |
| 전체   | 20948   | 11878  | 9070  | |

* "순서정하기1"은 정답이 산술연산 수식으로 표현되는 경우이며, "순서정하기2"는 문제에 나오는 명칭이 정답인 경우입니다.



## 2. 유형별 문제 예시

데이터는 JSON으로 작성하였으며, 데이터 구조 및 각 유형별 예시는 다음과 같습니다.

- 데이터 구조(TODO)
```
{
    문제 번호 (타입: 문자열): {
        "class": "문제 유형" (타입: 문자열),
        "question": "문제" (타입: 문자열),
        "answer" : "답" (타입: 문자열),
        "equation": "수식" (타입: 문자열)
    },
    
    .
    .
    .

    문제 번호 (타입: 문자열): {
        "class": "문제 유형" (타입: 문자열),
        "question": "문제" (타입: 문자열),
        "answer" : "답" (타입: 문자열),
	"equation" : "none" (타입: 문자열)
    },

}
```
- 유형별 예시
```

```

## 3. 지원



## 4. 데이터셋 구축 방법


## 5. 참여자