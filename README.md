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
<br />

|모델|크기|Max token|0 shot|5 shot|BackBone|Exp1|Exp2|Exp3|
|------|---|---|---|---|---|---|---|---|
|beomi/KoAlpaca-Polyglot-5.8B|5.8B|1024|1.12|-|Polyglot-5.8B|백상원|-|-|
|beomi/KoAlpaca-Polyglot-12.8B|-|-|-|-|-|-|-|-|


## KoAlpaca-Polyglot-5.8B vs 하이퍼클로바X



### Correct Top 3

내용 : Koalpaca가 Correct한 3개 중 하이퍼클로바X는 어떨까?

Example 1 Koalpaca 정답 vs 하이퍼클로바X 오답
```python
Q: 이오(Io)의 중력에 관한 다음 설명 중 옳은 것은 무엇인가요?

P: 이오(Io)의 중력은 나를 끌어당기며, 만약 당신이 이오(Io) 표면에 서 있다면, 지구에서보다 무게가 덜 나갈 것입니다. 지구에서 200파운드(90킬로그램) 나가는 사람이 아이오에서는 36파운드(16킬로그램)가 나갑니다. 그러므로 중력이 당연히 덜 잡아당긴다는 말입니다.

A. 지구의 중력이 이오(Io)의 중력보다 더 끌어당긴다
B. 이오(Io)의 중력이 더 끌어당기므로 무게가 더 든다
C. 이오(Io)의 중력이 더 끌어당기므로 무게가 더 많이 나간다
D. 지구의 중력이 이오(Io)의 중력보다 더 끌어당긴다

정답은
```
<br />

Output 1

| KoAlpaca-Polyglot-5.8B                                                                    | 하이퍼클로바X                                                                                                                                                  |
|-------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 정답은 "D"입니다. 이오의 중력이 더 이상 나를 끌어당기지 않기 때문에, 나는 자유낙하합니다. | B. 이오(Io)의 중력이 더 끌어당기므로 무게가 덜 나갑니다. 지구에서 200파운드 나가는 사람이 아이오에서는 36파운드가 나가기 때문에 중력이 덜 끌어당기는 것입니다. |

<br />

Example 2 Koalpaca 정답 vs 하이퍼클로바X 오답
```python
Q: 지문에 따르면, 신왕국 이집트인들이 감탄한 기자 피라미드의 특성이 아닌 것은 무엇입니까?

P: 고왕국의 마지막 순간까지 피라미드 건축은 계속 되었으나, 크기나 기술적 우수성은 기자 피라미드를 절대 능가할 수 없었습니다. 고대 신왕국 이집트인들은 조상의 기념비적인 건축물을 보고 경탄했고 이것은 그 당시 기준으로 1000년은 족히 넘은 건축물이었습니다.

A. 피라미드의 나이
B. 사용된 석재
C. 피라미드의 크기
D. 피라미드의 구조

정답은
```
<br />


| KoAlpaca-Polyglot-5.8B | 하이퍼클로바X                                                                                                                                                                                                     |
|------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 정답은 B입니다.        | A. 피라미드의 나이 신왕국 이집트인들이 감탄한 기자 피라미드의 특성은 사용된 석재, 피라미드의 크기, 피라미드의 구조입니다. 기자 피라미드는 그 당시 기준으로 1000년은 족히 넘은 건축물이었지만, 이 특성은 아닙니다. |
<br />




Example 3 둘 다 정답
```python
Q: 지문에 따르면, 중국의 경제 규모에 관한 다음 설명 중 정확하지 않은 것은 무엇입니까?

P: 지난 30년 동안 공식적으로 공산주의 국가로 남아있음에도 불구하고, 중국은 시장 경제를 발전해왔습니다. 첫 번째 경제 개혁은 덩 사오핑의 지도하에 이루어졌습니다. 이후 중국의 경제규모는 90배까지 성장했다. 중국은 지난해 처음으로 독일보다 많은 자동차를 수출해 미국을 제치고 이 산업의 최대 시장으로 부상했다. 20년 안에 중국의 GDP는 미국의 GDP보다 커질 수 있습니다.

A. 중국 경제는 개혁 이후 기하급수적으로 성장했다
B. 중국은 미국보다 더 큰 자동차 수출 시장이다
C. 중국은 결국 미국보다 GDP가 더 커질 수 있다
D. 중국은 독일보다 더 많은 자동차를 수출한 적이 없다

정답은
```
<br />

| KoAlpaca-Polyglot-5.8B                                                                                                                    | 하이퍼클로바X                                                                                                                                                                                                               |
|-------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 정답은 D입니다. 중국은 다른 나라들과는 다르게 산업화 이전부터 방대한 면적을 활용해 대량 생산을 해왔습니다. 따라서 D가 가장 맞는 답입니다. | D. 중국은 독일보다 더 많은 자동차를 수출한 적이 없습니다. 2021년에 중국은 독일보다 많은 자동차를 수출해 미국을 제치고 이 산업의 최대 시장으로 부상했습니다. 그러나 이전에는 독일보다 더 많은 자동차를 수출한 적이 없습니다. |
<br />


### Incorrect Top 3


내용 : Koalpaca가 Incorrect한 3개 중 하이퍼클로바X는 어떨까?

Example 1 둘 다 오답
```python
Q: 기자 고원(Giza Plateau)에서는 무엇을 볼 수 있는가?

P: 기자의 대 피라미드는 현재까지 존재하는 유일한 세계 7대 불가사의 중 하나이다. 기원전 3세기에 이집트인에 의해 지어진 '대 피라미드(the Great Pyramid)'는 죽은 파라오를 기리기 위해 지어진 많은 거대한 피라미드 구조물 중 하나이다. ""이집트의 죽음의 계곡에 있는 기자 고원(Giza Plateau) 또는 기자 묘지 (Giza Necropolis)에는 여러 개의 피라미드(그레이트 피라미드가 가장 큰 피라미드), 여러 개의 작은 무덤, 여러 개의 사원 및 스핑크스가 있습니다. 대피라미드는 파라오 쿠푸를 기리기 위해 만들어졌고 더 작은 피라미드들과 무덤, 신전은 쿠푸의 아내와 가족들을 기념하여 지어졌다.

A. 무덤
B. 사원
C. 모든 7대 불가사의
D. 대 피라미드

정답은
```
<br />

| KoAlpaca-Polyglot-5.8B                                                                                                                                                                                                                  | 하이퍼클로바X                                                                                                                                                                                                                                               |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 정답은 D입니다. 대 피라미드는 세계 7대 불가사의 중 하나이며, 건설 과정이 간단하고 빠르기 때문에 유명한 구조물 중 하나입니다. 또한, 기자 지역은 이집트의 역사와 문화, 그리고 현재의 과학적 기술력에 대한 관심을 높이는 곳 중 하나입니다. | D. 대 피라미드 기자 고원(Giza Plateau)에서는 대 피라미드를 볼 수 있습니다. 대 피라미드는 현재까지 존재하는 세계 7대 불가사의 중 하나이며, 기원전 3세기에 이집트인에 의해 지어진 죽은 파라오를 기리기 위해 지어진 많은 거대한 피라미드 구조물 중 하나입니다. |

<br />



Example 2 Koalpaca 오답 vs 하이퍼클로바X 정답
```python
Q: 지문에 따르면, 다음 중 지속적인 영향을 미치지 않는 것은 무엇인가?

P: 문명은 사람들이 협력해서 일하고 살아가는 매우 큰 집단, 즉 사회가 공유하는 단일 문화입니다. 문명이라는 단어는 '시민답다'를 뜻하는 라틴어 시빌리스(civilis), 시민을 뜻하는 라틴어 시비스(civis), 그리고 도시 혹은 도시 주를 뜻하는 라틴어 시비타스(citavas)에서 비롯된 것으로 사회의 규모를 정의합니다. 도시국가들은 국가의 선구자라 할 수 있다. 문명 문화는 여러 세대에 걸친 지식의 전승, 문화적 발자취의 잔존과 공정한 보급을 의미한다. 소수의 문화들은 의미 있는 역사적인 증거들을 남기지 않고 사라지는 경우가 많으며 제대로 된 문명으로 취급받지 못한다.

A. 사회
B. 소수의 문화
C. 도시국가
D. 문명 문화

정답은
```
<br />

| KoAlpaca-Polyglot-5.8B                                                                                                                                                                                                                                                                                                                                                                                                                                                   | 하이퍼클로바X                                                                                                                                                          |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 정답은 "시차적인 영향을 끼치지 않는 것"입니다. 문화는 인류에 의해 공유되는 것으로, 한 지역에서 다른 지역으로의 여행이 가능합니다. 그러나 한 문화에서 다른 문화로의 여행이 반드시 필요하거나, 한 문화에서 다른 문화로 너무 빠르게 이동하는 것은 효과적이지 않을 수 있습니다.  이는 다양한 생태계와 생태계에 미치는 영향이 있을 수 있습니다. 시차적인 영향을 끼치지 않는 것은 지역적인 문화와 특성에 따라 다르겠지만, 일반적으로 다양한 지역에서 공유하는 문화를 말합니다. | B. 소수의 문화 소수의 문화들은 의미 있는 역사적인 증거들을 남기지 않고 사라지는 경우가 많으며 제대로 된 문명으로 취급받지 못하지만, 지속적인 영향을 미치지는 않습니다. |


Example 3 Koalpaca 오답 vs 하이퍼클로바X 정답
```python
Q: 지문에 따르면, 다음 중 국가에 선행하는 것은 무엇인가?

P: 문명은 사람들이 협력해서 일하고 살아가는 매우 큰 집단, 즉 사회가 공유하는 단일 문화입니다. 문명이라는 단어는 '시민답다'를 뜻하는 라틴어 시빌리스(civilis), 시민을 뜻하는 라틴어 시비스(civis), 그리고 도시 혹은 도시 주를 뜻하는 라틴어 시비타스(citavas)에서 비롯된 것으로 사회의 규모를 정의합니다. 도시국가들은 국가의 선구자라 할 수 있다. 문명 문화는 여러 세대에 걸친 지식의 전승, 문화적 발자취의 잔존과 공정한 보급을 의미한다. 소수의 문화들은 의미 있는 역사적인 증거들을 남기지 않고 사라지는 경우가 많으며 제대로 된 문명으로 취급받지 못한다.

A. 문명 문화
B. 단일 문화
C. 도시국가
D. 소수의 문화

정답은
```
<br />

| KoAlpaca-Polyglot-5.8B                                                                                                                                                                                                     | 하이퍼클로바X                                                                                                                                                                                 |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 정답은 A입니다. 문명은 여러 세대에 걸친 지식의 전승, 문화적 발자취의 잔존과 공정한 보급을 의미합니다. 소수의 문화들은 의미 있는 역사적인 증거들을 남기지 않고 사라지는 경우가 많으며 제대로 된 문명으로 취급받지 못합니다. | C. 도시국가 도시국가들은 국가의 선구자이며, 국가에 선행하는 것입니다. 문명 문화는 여러 세대에 걸친 지식의 전승, 문화적 발자취의 잔존과 공정한 보급을 의미하며, 국가에 선행하는 것은 아닙니다. |
