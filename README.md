✈️ 소개
# kor_eng translator / seq2seq with attention mechanism

## 🛠 기능 요약
한국어를 영어로 기계번역

## 👩‍💻 팀 소개
임수경(팀장) | 남현수 | 정해아

## 프로젝트 소개
논문을 기반으로 하여 Seq2Seq with attention mechanism을 적용시킨 한-영 번역기를 만드는 미니 프로젝트

cf) Seq2Seq: 기계 번역, 문서 요약, 그리고 이미지 캡셔닝 등의 문제에서 아주 큰 성공을 거둔 딥러닝 모델

## seq2seq
- 사용이유=
기계 번역에서 seq2seq 모델은 입력 시퀀스와 출력 시퀀스의 길이가 다를 수 있기 때문에 효과적으로 작동할 수 있습니다.
이 입력 문장과 출력 문장의 길이가 다를 때도 번역을 수행할 수 있으며, 언어 간의 복잡한 차이점을 처리하기 위해 seq2seq를 사용함.

- 기계 번역의 장점
입력 시퀀스와 출력 시퀀스의 길이가 다를 수 있다는 점을 처리할 수 있다.
임의의 길이의 시퀀스를 처리할 수 있다.
입력 시퀀스와 출력 시퀀스 사이의 상관관계를 학습할 수 있다.
문장을 단어 단위로 분할하지 않고, 입력된 단어 그대로 처리할 수 있다.
따라서, seq2seq 모델은 텍스트 분류, 기계 번역, 대화 시스템 등의 다양한 자연어 처리 문제에 적용될 수 있으며, 특히 입력 시퀀스와 출력 시퀀스의 길이가 다르거나 임의의 길이의 시퀀스를 처리해야 하는 문제에서 우수한 성능을 보인다.

- attention
어텐션(attention) 은 입력 시퀀스에서 각 시점의 정보 중에서 필요한 정보에 더 집중할 수 있도록 하는 메커니즘.
어텐션 메커니즘은 주어진 쿼리(Query)와 일치하는 키(Key)와 연관된 값을 출력(Value)하는 방식으로 작동.
어텐션 메커니즘은 크게 세 가지 요소로 구성.
Query (q) : 현재 시점에서 예측하려는 단어 벡터.
Key (k) : 입력 시퀀스의 각 시점을 나타내는 벡터.
Value (v) : 입력 시퀀스의 각 시점에 대한 값.
-> q는 현재 시점에서 예측하고자 하는 단어의 벡터를, k는 입력 시퀀스에서의 각 시점의 벡터를, v는 해당 시점의 값을 나타내는 벡터를 나타낸다.

## 📌 기술
tensorflow

## stacks

### Environment
![Visual Studio Code](https://img.shields.io/badge/Visual%20Studio%20Code-007ACC?style=for-the-badge&logo=Visual%20Studio%20Code&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=Git&logoColor=white)
![Github](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=GitHub&logoColor=white)

### Communication
![Colab](https://img.shields.io/badge/Slack-4A154B?style=for-the-badge&logo=Slack&logoColor=white)
![Slack](https://img.shields.io/badge/Slack-4A154B?style=for-the-badge&logo=Slack&logoColor=white)
![Notion](https://img.shields.io/badge/Notion-000000?style=for-the-badge&logo=Notion&logoColor=white)
![GoogleMeet](https://img.shields.io/badge/GoogleMeet-00897B?style=for-the-badge&logo=Google%20Meet&logoColor=white)

## 📌 모델 요약

LIM : train model encoder: embedding층 -> lstm층 2개 쌓음 decoder: embedding층 -> lstm층 2개 쌓음 -> attention -> dense Softmax adam 옵티마이저와 sparse_categorical_crossentropy 손실함수 model fit inference model

NAM : train model encoder: embedding층 -> lstm층 encoder: embedding층 -> lstm층 ->attention -> dense Softmax adam 옵티마이저와 sparse_categorical_crossentropy 손실 함 model fit inference model

JEONG : train model latent_dim=64 encoder: embedding층 -> lstm층 decoder: embedding층 -> lstm층 ->attention -> dense Softmax rmsprop 옵티마이저와 sparse_categorical_crossentropy 손실 함수 model fit inference

# 소감
LIM : 처음에 데이터 전처리만 바꿔주고,  나머지는 프랑스영어 기계번역때 사용한 코드를 받아치기 해서 돌려보니까 번역 결과가 괜찮은 것 같아서,  더 명확한 결과를 얻기 위해 LSTM층을 더 쌓아보고 어텐션을 사용해보고 많은 오류를 겪으며 다양한 시도해보았다. 그런데, 번역문의 결과가 더 안좋아져서 조금 아쉬움이 남는다. 하지만, 층을 더 쌓아보고 어텐션을 적용해보는 데서 배운 것들이 많았던 시간이었다. 아마 지금 코드에서 잘못된 부분을 잘 고치면 이전보다는 더 나은 결과가 있을 것이라고 생각이 든다. 재미있는 시간이었고, 여러분들과 함께하고 도움을 받아서 배움이 있는 시간이었다. 코드는 조금 더 보면서 공부를 해야할 것 같고, 해보고 안되면 지피티나 선생님이나 다른 분들에게 힌트를 더 받아서라도 완성해보고 싶은 마음이다.

NAM : 데이터 한글 전처리 문제, 데이터의 개수가 많아짐에 따라 GCP 사용 필요성 ▲, layer를 쌓을 때 relu 함수를 tanh 함수 뒤에다 사용을 했었는데 그것으로 인해 값들이 왜곡이 되어서 많이 애를 먹었다. 강사님과 팀원들의 도움을 많이 받아서 결국 모델을 완성하였다. 하지만 더 정확도를 높이기 위해서는 더 많은 데이터를 학습 시켜야 할 것 같고 seq2seq의 구조에 대해서 다시 천천히 복습을 해야할 것 같다.

JEONG: 추론 모델을 만들 때  막막했다. 하지만 구글에서 찾아보고 다른 분들이 설명 듣는 것을 같이 듣다가 해결 방법을 찾을 수 있었다. 또한 latent_dim=256을 설정했는데 이것 때문에 계산이 오래걸리고 latent_dim이 크면 오버피팅이 될 수 있다는 사실을 몰랐다. 하지만 64로 설정하니까 괜찮았고 적절한 수를 찾는게 중요하다는 것을 알았다. 팀원분들과 같이 해서 재밌었고 많은 것을 배울 수 있었다.
