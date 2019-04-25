# Word Embedding
| Keywords |
| -------- |
| Embedding |
| Cosine Similarity |
| Word2Vec |
| GloVe |
| FastText |

### What is Embedding?
- 단어를 벡터로 바꾸는 한가지 방식이다.


### Word2Vec
- 비슷한 위치에 등장하는 단어들은 그 의미도 유사할 것이라는 전제가 깔려있다.
- Embedding방법중 하나로 크게 CBoW와 Skip-Gram 두가지 방식이 존재한다.
- CBow는 주변의 단어들로 중심의 단어를 유추하는 방식으로 
  - "난 오늘 ___를 보았다."에서 ___주변의 단어들로 ___에 영화, 악마, ...등이 들어갈수 있음을 유추할 수 있다.
- Skip-Gram은 중심단어 주변에 무엇이 올지 예측하는 방식으로,
  - "___ 외나무다리 ___"에서 외나무다리라는 중심단어로 앞뒤에 원수 는/에서 만난다가 오는 것을 짐작할 수 있다.
- **Word2Vec은 ‘외나무다리’가 ‘-에서’, ‘만난다’와 어떤 연관이 있다고 보고 이를 감안해서 단어를 벡터로 만들게 됩니다.**
- 외나무다리’는 ‘원수’와는 그 의미가 정확히 같지는 않지만, 자주 같이 쓰이는 **collocation 관계**에 있다는 것을 생각하자
<p align="center"><img src="https://github.com/Junhojuno/everyday-kaggle/blob/master/Jigsaw%20Unintended%20Bias%20in%20Toxicity%20Classification/img/word2vec.PNG?raw=true" alt="Cosine Similarity" width="250" height="100" /></p>
- 위 식에서 인자로 두 벡터의 내적이 들어가있다.
- 두 벡터의 내적 결과가 커지면 cos(theta)값이 커지게 되고, 이는 즉 theta가 작아진다는 말과 같아진다.(Similarity는 커짐)
- 위 식의 분모의 의미는 중심단어(c)와 그 주변에 있지 않는 것들의 유사도는 줄인다는 것이고,
- 분자는 주변단어와의 유사도는 키우겠다는 의미로 해석할 수 있다.
<p align="center"><img src="https://i.imgur.com/H8WvWMB.gif" alt="Cosine Similarity" width="450" /></p>

  ##### Word2Vec의 학습과정은 어떻게 이루어지는가?
  - 사용자가 주변단어 몇 개를 볼 지(window)를 정해주면 Word2Vec은 말뭉치를 window 크기로 슬라이딩하면서 스크린하며 중심단어별로 주변단어들을 보고 각 단어에 해당하는 벡터들의 요소값들을 조금씩 업데이트함으로써 단어를 벡터로 임베딩합니다.
  - 다시 말해 Word2Vec은 window 내에 등장하지 않는 단어에 해당하는 벡터는 중심단어 벡터와 벡터공간상에서 멀어지게끔(내적값 줄이기), 등장하는 주변단어 벡터는 중심단어 벡터와 가까워지게끔(내적값 키우기) 한다는 것이죠.
  - Word2Vec은 동시에 등장하는 단어의 빈도수를 세어서 행렬로 변환한 ‘단어-문맥행렬‘과 마찬가지로 기존 count 기반 방법론처럼 자주 같이 등장하는 단어들의 정보(Co-occurrence)를 보존한다
  
### GloVe, FastText
- GloVe가 보존하려는 정보는 단어 동시 등장 여부입니다. GloVe로 임베딩된 단어 벡터끼리의 내적은 동시 등장확률의 로그값과 같다.
- Word2Vec이 임베딩된 두 단어벡터의 내적이 코사인 유사도라면 GloVe는 동시 등장 확률인 셈이다.
- 위 설명이 직관적으로 와닿지는 않는다.ㅠㅠ
- 자세한 설명은 ![여기](https://ratsgo.github.io/from%20frequency%20to%20semantics/2017/03/11/embedding/)를 참고하자
- FastText는 원래 단어를 부분단어(subword)의 벡터들로 표현한다는 점을 제외하고는 Word2Vec과 거의 유사하다.
- FastText는 Noise가 많은 Corpus에서 강점을 보인다.
