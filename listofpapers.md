# ASR Papers on TIMIT

Mostly adopted from this excellent repo: https://github.com/syhw/wer_are_we, but 
a bit more descriptive for my own research (*NOTE: PER refers to Phone Error Rate*)

## List of Results
S.No. | PER     | Paper name                    | Published date | Publisher | Features Used                    | Training set | Testing set | Validation set | Notes                            |
| :---- | :------ | :----------------------------- | :------------- | :-------- | :------------------------------- | :--------------------------- | :------------------------------- | :------------------------------------ | ----------------------------------------------------------------------------- |
|1| 13.8 |[The PyTorch-Kaldi Speech Recognition Toolkit](https://ieeexplore.ieee.org/iel7/8671773/8682151/08683713.pdf?casa_token=EZf9YkoOqWsAAAAA:zxL4ECdXNBy6-GNhdnYNR30Wxsp6G_4vlbj642lxbCfhm0yn94nbgRHh3tve54LpbwQB3oR-)|Feb. 2019|ICASSP 2019|Combination of MFCC features + FBANK features + fMLLR features|Standard Kaldi s5 training set|Core Test set|As per Kaldi s5|Used DNN-HMM hybrid architecture, but instead of a regular DNN used a combination of 3 networks: MLP, Li-GRU and MLP to estimate posterior probabilities of phones, given the utterance features (DNNs were trained discriminatively as per standard practices for DNN-HMM)| 
|2| 14.9 |[Light Gated Recurrent Units for Speech Recognition](https://arxiv.org/pdf/1803.10225)|Apr 2018|IEEE Trans. 2018|Combination of Mel filterbank coefficients with energy + thier velocity + accln. coeff.|Standard Kaldi s5 training set|Core Test set|Standard s5 dev set|End-to-End CTC training, removed reset gate of GRU, ReLU activations insead of Tanh + Batch Normalization|  
|3| 16.5 |[Phone Recognition with Hierarchical Convolutional Deep Maxout Networks](https://link.springer.com/content/pdf/10.1186%2Fs13636-015-0068-3.pdf)|Sep. 2015| EURASIP Journal 2015 |Mel-Filterbank features with context frames, spatially reshaped|Standard Kaldi s5 training set (3696 sentences)|Core Test set|10 % of training set (random)|Used DNN-HMM hybrid architecture, but instead of a regular DNN used Hierarchical maxout CNN + Dropout to estimate posterior probabilities of phones (used 61 phone labels while training, 39 while testing)|
|4| 16.5 |[A Regularization Post Layer: An Additional Way: how to Make Deep Neural Networks Robust](https://www.researchgate.net/profile/Jan_Vanek/publication/320038040_A_Regularization_Post_Layer_An_Additional_Way_How_to_Make_Deep_Neural_Networks_Robust/links/59f97fffaca272607e2f804a/A-Regularization-Post-Layer-An-Additional-Way-How-to-Make-Deep-Neural-Networks-Robust.pdf)|Oct. 2017| ICSLSP 2017 | MFCC+fMLLR features with deltas, double-deltas |Standard Kaldi s5 training set (3696 sentences)|Core Test set|s5 dev set|Used DBN-DNN with last layer regularization (Regularization layer was a notable contribution) (used 48 phone labels while training, 39 while testing)|
|5| 16.7 |[Combining time-and frequency domain convolution in convolutional neural network based phone recognition](https://ieeexplore.ieee.org/iel7/6844297/6853544/06853584.pdf?casa_token=hlmqUw1WAT0AAAAA:BZjYKzbAz30gqymR6KVOaZ_NOOFojWe8qLmRAGHnx_GTp2v8YTunqUz2dBfo9xUQPae-VztD)|May 2014| ICASSP 2014 |Mel-Filterbank features with context frames, spatially reshaped|Standard Kaldi s5 training set (3696 sentences)|Core Test set|10 % of training set (random)|Used DNN-HMM hybrid architecture, but instead of a regular DNN used CNN in time and frequency + dropout to estimate posterior probabilities of phones (used 61 phone labels while training, 39 while testing)|
|6| 16.8 |[An investigation into instantaneous frequency estimation methods for improved speech recognition features](https://ieeexplore.ieee.org/abstract/document/8308665)|Nov. 2017| GlobalSIP 2017 |MFCC features with IFCC features |Standard Kaldi s5 training set (3696 sentences)*(Assuming)*|Core Test set|s5 dev set *(Assuming)*|Used DNN-HMM hybrid architecture to estimate posterior probabilities of phones *[NOT SURE about this] --> (used 61 phone labels while training, 39 while testing)*|
|7| 17.3 |[Segmental Recurrent Neural Networks for End-To-End Speech Recognition](https://arxiv.org/pdf/1603.00223.pdf)|Mar. 2016| Interspeech 2016 | 24-dim log-mel filterbank features with context information |Standard Kaldi s5 training set (3696 sentences)|Core Test set|s5 dev test| Used a Recurrent Neural Network combined with Conditional Random Fields for end-to-end discriminative training (used 48 phone labels while training, 39 while testing)|
|8| 17.6 |[Attention-Based models for Speech Recognition](https://arxiv.org/pdf/1506.07503.pdf)|June 2015| NIPS 2015 | 40-dim mel filterbank features with energy along with deltas and double-deltas | Standard Kaldi s5 training set (3696 sentences)|Core Test set|s5 dev test| Used a Bi-directional Recurrent Neural Network combined with Attention mechansim for end-to-end discriminative training (used full 61 phone labels while training, 39 while testing)|
|9| 17.7 |[Speech Recognition with Deep Recurrent Neural Networks](https://arxiv.org/pdf/1303.5778v1.pdf)|Mar. 2013| ICASSP 2013 | 40-dim mel filterbank features with energy along with deltas and double-deltas |Standard Kaldi s5 training set (3696 sentences)|Core Test set|s5 dev test| Used a Bi-directional LSTM combined with skip connections and a special type of architecture called RNN Transducer that also provides some conditioning information based on labels. Uses end-to-end CTC (used 61 phone labels while training, 39 while testing)|
|10| 18.0 |[Learning Filterbanks from Raw speech for Phone recognition](https://arxiv.org/pdf/1711.01161.pdf)|Oct. 2017| ICASSP 2018 | Approximating mel-filterbanks from raw-speech using Time-Domain filterbanks and fine tuned with CNNs |Standard Kaldi s5 training set (3696 sentences)|Core Test set|s5 dev test| Using a combination of time-domain Gabor filters to provide an approximate mel-filterbank output at the start, this method tries to learn the entire feature starting from pre-emphasis to averaging using CNNs. Uses end-to-end phone recognition *(NOT exactly clear which recurrent architecture is used)* (used 39 phone labels while training, 39 while testing)|
|11| 23.0 |[Deep Belief Networks for Phone Recognition](http://www.cs.toronto.edu/~asamir/papers/NIPS09.pdf)|Dec. 2009| NIPS 2009 | 13-dim MFCC features with deltas and double-deltas |Standard Kaldi s5 training set (3696 sentences)|Core Test set|s5 dev test| Used a Deep Belief Network combined with HMM for estimating posterior probabilities of phones, given the utterance features (DBNs were trained discriminatively) (used 61 phone labels while training, 39 while testing)|

### Description of Feature abbreviations

- MFCC : Mel Frequency Cepstral Coefficients
- FBANK: Mel Filterbank Coefficients (similar to MFCC without before applying the DCT). Also referred to as Mel Frequency Spectral Coefficients (MFSC) in some papers.
- fMLLR: Feature space Maximum Likelihood Linear Regression

### Description of standard Kaldi s5 recipe 

*NOTE:* s5 basically means Version 5, which is the latest version now for Kaldi examples. 

This is obtained from the RESULTS at the official repository for Kaldi at https://github.com/kaldi-asr/kaldi/blob/master/egs/timit/s5/RESULTS.md

- **Training set**: 4620 sentences (or 3696 sentences is used, if the dialect sentences (SA) spoken by 462 speakers are excluded). Many papers use only the 3696 utterances, when they mention the use of "full" training set (in some cases, this is not always clear).
- **Validation / Dev set**: 400 sentences
- **Test set**: 192 sentences spoken by 24 speakers (8 sentences spoken per speaker) constitute the Core Test set. The total test set is composed of 1680 sentences
- **Phone mapping**: Training with 48 phonemes (originally TIMIT considers 61 phonemes, but these are mapped down to 48 phonemes as cited in [[1]](https://www.intechopen.com/books/speech-technologies/phoneme-recognition-on-the-timit-database)[[2]](https://ieeexplore.ieee.org/iel1/29/1758/00046546.pdf?casa_token=sXvGQS2ptokAAAAA:rMibo9lch5X03TUxV5seLNWkugLwYZ6RKKqrGU-HfLfXfCbXclIpYc0lHnJnCl8UB3dOYktL))
- **Language Model**: Bigram phoneme language model which is extracted from the training set

## Additional Notes:

In many cases, when it is mentioned "tested on 39 phones", what is generally said is that the decoding was carried on the same number of labels as in the training (i.e. 61 or 48) but for "scoring" purposes, these results were mapped to a 39-label system as mentioned in [[2]](https://ieeexplore.ieee.org/iel1/29/1758/00046546.pdf?casa_token=sXvGQS2ptokAAAAA:rMibo9lch5X03TUxV5seLNWkugLwYZ6RKKqrGU-HfLfXfCbXclIpYc0lHnJnCl8UB3dOYktL), and then PER is computed

## Paper References

[[1]](https://www.intechopen.com/books/speech-technologies/phoneme-recognition-on-the-timit-database) Lopes, Carla, and Fernando Perdigao. "Phone recognition on the TIMIT database." Speech Technologies/Book 1 (2011): 285-302.

[[2]](https://ieeexplore.ieee.org/iel1/29/1758/00046546.pdf?casa_token=sXvGQS2ptokAAAAA:rMibo9lch5X03TUxV5seLNWkugLwYZ6RKKqrGU-HfLfXfCbXclIpYc0lHnJnCl8UB3dOYktL) Lee, K-F., and H-W. Hon. "Speaker-independent phone recognition using hidden Markov models." IEEE Transactions on Acoustics, Speech, and Signal Processing 37.11 (1989): 1641-1648.
