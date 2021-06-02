# TimeTraveler (서강_빅데이터마케팅용_임시프로젝트)
## ⏳ "TIME MATTERS" ⌛

<b>미래</b>를 예측하기 위한 분석에 <b>시간</b>적 요소가 빠져있어도 괜찮을까요? 혹시 당신의 분석에는 <b>시간</b>이 빠져있지는 않나요?\
"Time DOES matter" 하나의 시간축에 고정되어있던 당신의 분석에 시간을 담아드립니다.

```diff

🚀 키워드의 기간별 관측 빈도수와 매출을 업로드하시면 그에 대한 심층적인 분석을 제공합니다. 🚀

MADE BY _EEDOCELSIUS
```
\
<b>1. 사용자가 원하는 기간에 따른 (Ex => 분기별, 월별, 일별, 등등) 키워드의 "관심도"와 "추세값"를 반환합니다.</b>
- "관심도"는 스크랩한 포스트의 총 갯수를 100으로 환산했을 때 몇개의 포스트에서 해당 키워드에 대해 이야기하고 있는지를 나타내는 지수입니다.
- "추세값"은 "관심도"의 평균값을 0 으로 고정시켜놓고 해당 기간의 관심도를 상대적인 수치로 표현한것입니다. 따라서 평소보다 많은 관심을 받은경우 양의 값(+)을, 평소보다 적은 관심을 받은경우 음의 값(-)을 띄게됩니다. 해당 값으로 특정 키워드가 단기간에 집중된 관심을 받았는지, 큰 파동이 없는 일정한 관심을 받고 있는지, 시간적 트렌드에 따른 주기를 갖는지 등의 추세를 평가할 수 있습니다.


<b>2. 키워드별 관심도와 매출간의 상관관계를 분석하여 반환하며 추가로 보조지표로 사용할 수 있는 분산값을 제공합니다.</b>
- 1에 가까울수록 강한 양(+)의 상관관계를 예측할 수 있습니다. 즉 '해당 키워드에 소비자가 집중할수록 매출이 상승한다' 또는 '매출이 상승하는 시기(seasonality)에 해당 키워드에 대한 관심이 높아진다' 라고 해석할 수 있습니다.
- -1에 가까울수록 강한 음(-)의 상관관계를 예측할 수 있습니다. 즉 '해당 키워드에 소비자가 집중할수록 매출이 하락한다' 또는 '매출이 하락하는 시기(seasonality)에 해당 키워드에 대한 관심이 높아진다'라고 해석할 수 있습니다.
- 0에 가까울수록 상관관계가 약해집니다. 대략 -0.175 ~ 0.175 사이의 값은 분석에서 제외하셔도 좋습니다.
- 강한 상관관계가 관측된 경우 빠른 분석이 필요하다면 분산값을 참고하세요. (자세한 내용은 "추세값"을 통하여 분석하는 것이 좋습니다.) 매출에 단기적인 영향을 주는지 꾸준한 영향을 주고있는지 간단하게 파악할 수 있습니다.


<b>3. 추세값을 시각화한 그래프를 제공합니다.</b>
- 추가 예정...


## ✔️ 키워드는 그저 하나의 예시일 뿐입니다 👍
타임트레블러는 분석을 손쉽고 용의하게 보조해주는 툴이므로 정해놓은 틀에 맞추실 필요가 없습니다.\
필요에 따라 변수에 여러종류의 가공된 값을 넣어 다양하게 활용이 가능합니다. 
```diff
#소셜미디어별로_나누어_어떤_소셜미디어에_어떤_키워드를_공략하는_것이_효율적인지_알아보기
#비슷한_섹터의_단어끼리_그룹핑하여_넣기   #부정_키워드만_넣어_소비자의_불만이_해결되고_있는지_분석해보기
#매출액_대신_광고비를_넣어_적극적인_마케팅를_하면_소비자가_제품의_어떤_속성에_더_집중_하게_되었는지_파악하기
```


## 인풋으로 업로드해야 하는 데이터 구조는 다음과 같습니다
게시글별로 형태소 분석 후 단어 단위로 쪼개어 리스트타입 업로드하세요. 불용어나 포함하고 싶지 않은 단어들이 있다면 제거하셔도 좋습니다. 키워드 분석 이외의 결과값을 원하신다면 목적에 맞게 단어들을 변환시켜 업로드해주시면 됩니다. 의미있는 결과 도출을 위해 기간별로 5만 단어 이상을 넣어주시는 것을 권유드립니다.

```diff
[
  {
    "기간": "([문자열타입] 포멧은 상관없음)",
    "매출": ([숫자타입] 콤마 등 숫자가 아닌것은 모두 제거할 것. 단위는 상관없음),
    "출처": "([문자열타입] 예시: '네이버블로그')",
    "게시글": 
      [
        ["단어1", "단어2", "단어3", ....],
        ["단어1", "단어2", "단어3", ....],
        ["단어1", "단어2", "단어3", ....],
          ....
      ]
  },
  {
    "기간": "([문자열타입] 포멧은 상관없음)",
    "매출": ([숫자타입] 콤마 등 숫자가 아닌것은 모두 제거할 것. 단위는 상관없음),
      ....
  },
    ....
]
```

<a href="http://localhost:8001/">업로드하기</a>
