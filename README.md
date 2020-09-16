# ASR Papers on TIMIT

## List of Results

This repository contains is used for keeping a list of the some best results that have been achieved with the TIMIT Dataset
on the task of Phone recognition

Mostly adopted from this excellent repo: https://github.com/syhw/wer_are_we, but 
a bit more descriptive for my own research (*NOTE: PER refers to Phone Error Rate*)

|PER (%)|Paper name|Published Date|Publisher details|Features Used|Training Set|Test Set|Validation Set|Additional Notes|
|--------|------------------------------------------------------------------------------------|-------------------------------|-------------------------------|-------------------------------|-------------------------------|-------------------------------|-------------------------------|-------------------------------|-------------------------------------------------------|
|13.8|[The PyTorch-Kaldi Speech Recognition Toolkit](https://ieeexplore.ieee.org/iel7/8671773/8682151/08683713.pdf?casa_token=EZf9YkoOqWsAAAAA:zxL4ECdXNBy6-GNhdnYNR30Wxsp6G_4vlbj642lxbCfhm0yn94nbgRHh3tve54LpbwQB3oR-)|Feb. 2019|ICASSP 2019|Combination of MFCC features + FBANK features + fMLLR features|Standard Kaldi s5 training set|Core Test set|As per Kaldi s5|Used DNN-HMM hybrid architecture, but instead of a regular DNN used a combination of 2 networks MLP, Li-GRU and MLP to estimate posterior probabilities of phones, given the utterance features (DNNs were trained discriminatively as per standard practices for DNN-HMM)|
|14.9|[Light Gated Recurrent Units for Speech Recognition](https://arxiv.org/pdf/1803.10225)|Apr 2018|IEEE Trans. 2018|Combination of Mel filterbank coefficients with energy + thier velocity + accln. coeff.|Standard Kaldi s5 training set|Core Test set|Standard s5 dev set|End-to-End CTC training, removed reset gate of GRU, ReLU activations insead of Tanh + Batch Normalization|
|16.5|[Phone Recognition with Hierarchical Convolutional Deep Maxout Networks](https://link.springer.com/content/pdf/10.1186%2Fs13636-015-0068-3.pdf)|Sep. 2019| EURASIP Journal on Audio, Speech and Music|Mel-Filterbank features with context frames, spatially reshaped|Standard Kaldi s5 training set (3696 sentences)|Core Test set|10 % of training set (random)|Used DNN-HMM hybrid architecture, but instead of a regular DNN used Hierarchical maxout CNN + Dropout to estimate posterior probabilities of phones (used 61 phone labels while training, 39 while testing)|

### Description of Feature abbreviations

- MFCC : Mel Frequency Cepstral Coefficients
- FBANK: Mel Filterbank Coefficients (similar to MFCC without before applying the DCT)
- fMLLR: Feature space Maximum Likelihood Linear Regression

### Description of standard Kaldi s5 recipe 

*NOTE:* s5 basically means Version 5, which is the latest version now for Kaldi examples

This is obtained from the RESULTS at the official repository for Kaldi at https://github.com/kaldi-asr/kaldi/blob/master/egs/timit/s5/RESULTS.md

- **Training set**: 4620 sentences (or 3696 sentences is used, if the dialect sentences (SA) spoken by 462 speakers are excluded)
- **Validation / Dev set**: 400 sentences
- **Test set**: 192 sentences spoken by 24 speakers (8 sentences spoken per speaker) constitute the Core Test set. The total test set is composed of 1680 sentences
- **Phone mapping**: Training with 48 phonemes (originally TIMIT considers 61 phonemes, but these are mapped down to 48 phonemes as cited in [[1]](https://www.intechopen.com/books/speech-technologies/phoneme-recognition-on-the-timit-database)[[2]](https://ieeexplore.ieee.org/iel1/29/1758/00046546.pdf?casa_token=sXvGQS2ptokAAAAA:rMibo9lch5X03TUxV5seLNWkugLwYZ6RKKqrGU-HfLfXfCbXclIpYc0lHnJnCl8UB3dOYktL))
- **Language Model**: Bigram phoneme language model which is extracted from the training set

## Paper References

[[1]](https://www.intechopen.com/books/speech-technologies/phoneme-recognition-on-the-timit-database) Lopes, Carla, and Fernando Perdigao. "Phone recognition on the TIMIT database." Speech Technologies/Book 1 (2011): 285-302.

[[2]](https://ieeexplore.ieee.org/iel1/29/1758/00046546.pdf?casa_token=sXvGQS2ptokAAAAA:rMibo9lch5X03TUxV5seLNWkugLwYZ6RKKqrGU-HfLfXfCbXclIpYc0lHnJnCl8UB3dOYktL) Lee, K-F., and H-W. Hon. "Speaker-independent phone recognition using hidden Markov models." IEEE Transactions on Acoustics, Speech, and Signal Processing 37.11 (1989): 1641-1648.

## Notes

More details to be added soon
