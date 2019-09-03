# Edit-distance as objective function

There are several research fields in which the [edit-distance](https://en.wikipedia.org/wiki/Edit_distance) chosen as the objective function. For example, in Automatic Speech Recognition (ASR) the main metric of the quality of models is the [Word Error Rate](https://en.wikipedia.org/wiki/Word_error_rate) (WER).

## Problems

Unfortunately, directly optimize the edit-distance function is difficult. Therefore, in most cases, approaches based on a proxy function, like a cross-entropy. On the other hand, in the context of the sequence learning task this leads to several problems [[1]](https://arxiv.org/pdf/1606.02960.pdf):

1. _Exposure Bias_: the model is never exposed to its own errors during training, and so the inferred histories at test-time do not resemble the gold training histories.

2. _Loss Evaluation Mismatch_: training uses a word-level loss, while at test-time we target improving sequence-level evaluation metrics

3. _Label Bias_: since word probabilities at each time-step are locally normalized, guaranteeing that successors of incorrect histories receive the same mass as do the successors of the true history.

## Solutions

The following table summarizes the work that attempts to solve the mentioned problems. There are much broad overview of works, for example 
[[2]](https://arxiv.org/pdf/1805.09461.pdf), but this list includes only works that use the edit-distance explicitly or implicitly. Moreover, most of these works formalize the sequence prediction task as an action-taking problem in Reinforcement Learning.

| Year | Task | Reward level | Algorithms, Models | Affiliation | Authors, Link |
|:----:|:---:|----------|------------|------|------|
| 2019 | ASR | Sentence | MWER, RNN-T, LAS | Google | [Sainath, Pang et al](https://arxiv.org/abs/1908.10992)
| 2018 | ASR | Token    | MBR, softmax margin, PAPB, seq2seq | Brno, JHU, MERL | [Baskar et al.](https://arxiv.org/abs/1811.02770)|
| 2018 | ASR | Token    | Optimal Completion Distillation, no-pretrain | Google Brain | [Sabour, Chan, Norouzi](https://arxiv.org/abs/1810.01398)|
| 2018 | ASR | Token    | REINFORCE, seq2seq | Nara, RIKEN | [Tjandra et al.](https://ahcweb01.naist.jp/papers/journal/2019/201906_IEEE_andros-tj_1/201906_IEEE_andros-tj_1.paper.pdf)|
| 2018 | NAS | Sentence | Alternating Actor-Critic | Hong Kong, Tencent | [Li, Bing, Lam](https://arxiv.org/abs/1803.11070)|
| 2018 | ASR | Sentence | REINFORCE, PPO, Reward engineering | Tokyo |[Peng, Shibata, Shinozaki](http://www.apsipa.org/proceedings/2018/pdfs/0001934.pdf)|
| 2017 | ASR | Sentence | REINFORCE, Self-critic | Salesforce | [Zhou, Xiong, Socher](https://arxiv.org/abs/1712.07101)|
| 2017 | ASR | Sentence | MWER, LAS, Sampling, N-best | Google |[Prabhavalkar et al.](https://arxiv.org/abs/1712.01818)|
| 2017 | ASR | Sentence | Expected Loss, RNA| Google | [Sak et al.](https://pdfs.semanticscholar.org/7703/a2c5468ecbee5b62c048339a03358ed5fe19.pdf)|
| 2017 | NMT | Sentence | Actor-Critic, Critic-aware | Hong Kong, New York | [Gu, Cho, Li](https://arxiv.org/abs/1702.02429)|
| 2016 | ASR | Sentence | Reward Augmented Maximum Likelihood | Google Brain | [Norouzi et al.](https://arxiv.org/abs/1609.00150)|
| 2016 | NMT | Token    | Actor-Critic | Montreal, McGill | [Bahdanau et al.](https://arxiv.org/abs/1607.07086)|
| 2015 | NMT | Sentence | MIXER | Facebook | [Ranzato et al.](https://arxiv.org/abs/1511.06732)|
| 2015 | ASR | Token    | Task Loss Estimation | Montreal, Wrocław | [Bahdanau et al.](https://arxiv.org/abs/1511.06456)|
| 2014 | ASR | Sentence | Expected Transcription Loss, RNN-T | DeepMind, Toronto | [Graves, Jaitly](http://proceedings.mlr.press/v32/graves14.pdf)|


## Reference

1. [Sequence-to-Sequence Learning as Beam-Search Optimization](https://arxiv.org/abs/1606.02960)
2. [Deep Reinforcement Learning for Sequence-to-Sequence Models](https://arxiv.org/abs/1805.09461)
