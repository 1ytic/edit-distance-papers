# Edit-distance as objective function

There are several research fields in which the [edit-distance](https://en.wikipedia.org/wiki/Edit_distance) chosen as the objective function. For example, in Automatic Speech Recognition (ASR) the main metric of the quality of models is [Word Error Rate](https://en.wikipedia.org/wiki/Word_error_rate) (WER).

## Problems

Unfortunately, directly optimize the edit-distance function is difficult. Therefore, in most cases, approaches based on a proxy function, like a cross-entropy. On the other hand, in the context of the sequence learning task this leads to several problems [[1]](https://arxiv.org/pdf/1606.02960.pdf):

1. _Exposure Bias_: the model is never exposed to its own errors during training, and so the inferred histories at test-time do not resemble the gold training histories.

2. _Loss Evaluation Mismatch_: training uses a word-level loss, while at test-time we target improving sequence-level evaluation metrics

3. _Label Bias_: since word probabilities at each time-step are locally normalized, guaranteeing that successors of incorrect histories receive the same mass as do the successors of the true history.

## Solutions

The following table summarizes the works that attempts to solve the mentioned problems. There are much more detailed overview of works, for example [[2]](https://arxiv.org/pdf/1805.09461.pdf), but this list includes only works that use the edit-distance explicitly or implicitly. Moreover, most of these works formalize the sequence prediction task as an action-taking problem in Reinforcement Learning.

| Year | Task | Reward level | Algorithms, Models | Affiliation | Authors, Link |
|:----:|:----:|--------------|--------------------|-------------|---------------|
| 2019 | ASR | Token | RNN-T, MBR | Tencent, USA | [Weng et al.](https://arxiv.org/abs/1911.12487)|
| 2019 | ASR | Token | ECTC-DOCD | China | [Yi, Wang, Xu](https://www.isca-speech.org/archive/Interspeech_2019/pdfs/1212.pdf)|
| 2019 | ASR | Sentence | MWER, RNN-T, LAS | Google | [Sainath, Pang et al](https://arxiv.org/abs/1908.10992)|
| 2019 | MT  | Token | Reinforce-NAT, Non-Autoregressive Transformer | China, Tencent | [Shao, Feng et al.](https://arxiv.org/abs/1906.09444)|
| 2019 | MT, TS, APE | Token | Levenshtein Transformer, imitation learning | Facebook, New York | [Gu, Wang, Zhao](https://arxiv.org/abs/1905.11006)|
| 2018 | ASR | Token | MBR, softmax margin, PAPB, S2S | Brno, JHU, MERL | [Baskar et al.](https://arxiv.org/abs/1811.02770)|
| 2018 | ASR | Token | OCD, S2S | Google Brain | [Sabour, Chan, Norouzi](https://arxiv.org/abs/1810.01398)|
| 2018 | ASR | Token | REINFORCE, S2S | Nara, RIKEN | [Tjandra et al.](https://ahcweb01.naist.jp/papers/journal/2019/201906_IEEE_andros-tj_1/201906_IEEE_andros-tj_1.paper.pdf)|
| 2018 | TS  | Sentence | Alternating Actor-Critic | Hong Kong, Tencent | [Li, Bing, Lam](https://arxiv.org/abs/1803.11070)|
| 2018 | ASR | Sentence | REINFORCE, PPO, Reward shaping | Tokyo |[Peng, Shibata, Shinozaki](http://www.apsipa.org/proceedings/2018/pdfs/0001934.pdf)|
| 2017 | ASR | Sentence | REINFORCE, Self-critic | Salesforce | [Zhou, Xiong, Socher](https://arxiv.org/abs/1712.07101)|
| 2017 | ASR | Sentence | MWER, LAS, Sampling, N-best | Google |[Prabhavalkar et al.](https://arxiv.org/abs/1712.01818)|
| 2017 | ASR | Sentence | Expected Loss, RNA | Google | [Sak et al.](https://pdfs.semanticscholar.org/7703/a2c5468ecbee5b62c048339a03358ed5fe19.pdf)|
| 2017 | MT  | Sentence | Actor-Critic, Critic-aware | Hong Kong, New York | [Gu, Cho, Li](https://arxiv.org/abs/1702.02429)|
| 2016 | ASR | Sentence | Reward Augmented ML | Google Brain | [Norouzi et al.](https://arxiv.org/abs/1609.00150)|
| 2016 | MT  | Token | Actor-Critic | Montreal, McGill | [Bahdanau et al.](https://arxiv.org/abs/1607.07086)|
| 2015 | MT  | Sentence | MIXER | Facebook | [Ranzato et al.](https://arxiv.org/abs/1511.06732)|
| 2015 | ASR | Token | Task Loss Estimation | Montreal, Wrocław | [Bahdanau et al.](https://arxiv.org/abs/1511.06456)|
| 2014 | ASR | Sentence | Expected Loss, CTC | DeepMind, Toronto | [Graves, Jaitly](http://proceedings.mlr.press/v32/graves14.pdf)|


## Reference

1. [Sequence-to-Sequence Learning as Beam-Search Optimization](https://arxiv.org/abs/1606.02960)
2. [Deep Reinforcement Learning for Sequence-to-Sequence Models](https://arxiv.org/abs/1805.09461)
