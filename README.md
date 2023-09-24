# Korean_LLM_Benchmark_Test




## Update Logs




## 한국어 LLM 모델 벤치마크 테스트
### 배경 
- 한국어 LLM 모델이 만들어지고 있지만  
### 목적
- 한국어 LLM 오픈소스 모델들과 기업에서 공개한 모델들의 성능을 비교
- 모델을 선택하거나 데이터를 학습할 때의 인사이트 정보가 되기를 희망

<br /><br />
### Meta belebele dataset
언어 모델의 다국어 능력 평가 데이터셋 Meta의 belebele
link : https://arxiv.org/abs/2308.16884
- 데이터셋
    - 한국어 900개
    - Multiple choice  Q&A
    - Metric : Accuracy
<br/><br/>

### Example Input

```python
Q: 몸 전체에 신경 자극을 보내는 목적에 관한 다음의 설명 중 정확하지 않은 것은 무엇입니까?

P: 신경계는 몸 전체에 신경 신호를 보내서 혈류가 방해받지 않도록 하여 항상성을 유지한다. 이러한 신경 자극은 몸 전체에 재빠르게 전달되어 신체에 발생할 수 있는 위험으로부터 몸을 안전하게 보호하는 데 도움을 줍니다.

A. 혈류 둔화 
B. 혈류 관리 
C. 항상성 유지 
D. 잠재적인 신체적 위협 방지

정답은
```
<br />

### Result
|모델|크기|Max token|0 shot|5 shot|BackBone|Exp1|Exp2|Exp3|
|------|---|---|---|---|---|---|---|---|
|beomi/KoAlpaca-Polyglot-5.8B|5.8B|1024|1.12|-|Polyglot-5.8B|백상원|-|-|
|beomi/KoAlpaca-Polyglot-12.8B|-|-|-|-|-|-|-|-|
