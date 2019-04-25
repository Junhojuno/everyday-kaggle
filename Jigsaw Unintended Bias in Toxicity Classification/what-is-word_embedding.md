# Word Embedding
| Keywords |
| -------- |
| Embedding |
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
- 
<p align="center"><img src="https://i.imgur.com/H8WvWMB.gif" alt="Cosine Similarity" width="450" /></p>
