# transition
Implementations of the modes described in the following three papers:

[Learning Natural Language Inference with Lstm](https://arxiv.org/abs/1512.08849) by Shuohang Wang, Jing Jiang

[Machine Comprehension Using Match-LSTM and Answer Pointer](https://arxiv.org/abs/1608.07905) by Shuohang Wang, Jing Jiang

Sequences Maching in Word Level

# Learning Natural Language Inference with Lstm

## Requirements
- [Torch7](https://github.com/torch/torch7)
- [nn](https://github.com/torch/nn)
- [nngraph](https://github.com/torch/nngraph)
- [optim](https://github.com/torch/optim)
- Python 2.7

## Datasets
- [The Stanford Natural Language Inference (SNLI) Corpus](http://nlp.stanford.edu/projects/snli/)
- [GloVe: Global Vectors for Word Representation](http://nlp.stanford.edu/data/glove.840B.300d.zip)

## Usage
```
sh snli_preprocess.sh
cd main
th main.lua -dropoutP <0-0.5> -num_classes 3
```

"squad_preprocess.sh" will download the datasets and preprocess the SNLI corpus into the files 
(train.txt dev.txt test.txt) under the path "data/snli/sequence" with the format:

>sequence1(premise) \t sequence2(hypothesis) \t label \n

"main.lua" will first initialize the prepossed data and word embeddings into a Torch format and 
then run the alogrithm. "dropoutP" is the main prarameter we tuned.

## Docker
You may try to use Docker for running the code.
- [Docker Install](https://github.com/codalab/codalab-worksheets/wiki/Installing-Docker)
- [Image](https://hub.docker.com/r/shuohang/transition/): docker pull shuohang/transition:1.1
```
docker run -it -v /PATH/transition:/opt --rm -w /opt shuohang/transition:1.1 /bin/bash -c "sh squad_preprocess.sh"
docker run -it -v /PATH/transition:/opt --rm -w /opt/main --rm shuohang/transition:1.1 /bin/bash -c "th main.lua"
```
# Machine Comprehension Using Match-LSTM and Answer Pointer

## Requirements
- [Torch7](https://github.com/torch/torch7)
- [nn](https://github.com/torch/nn)
- [nngraph](https://github.com/torch/nngraph)
- [optim](https://github.com/torch/optim)
- [parallel](https://github.com/clementfarabet/lua---parallel)
- Python 2.7
- [Python NLTK](http://www.nltk.org/install.html)
- [NLTK Data](http://www.nltk.org/data.html): punkt

## Datasets
- [Stanford Question Answering Dataset (SQuAD)](https://rajpurkar.github.io/SQuAD-explorer/)
- [GloVe: Global Vectors for Word Representation](http://nlp.stanford.edu/data/glove.840B.300d.zip)

## Usage
```
sh squad_preprocess.sh
cd main
th mainDt.lua 
```

"squad_preprocess.sh" will download the datasets and preprocess the SQuAD corpus into the files 
(train.txt dev.txt) under the path "data/squad/sequence" with the format:

>sequence1(Doument) \t sequence2(Question) \t label \n

"main.lua" will first initialize the prepossed data and word embeddings into a Torch format and 
then run the alogrithm. "dropoutP" is the main prarameter we tuned.

## Docker
You may try to use Docker for running the code.
- [Docker Install](https://github.com/codalab/codalab-worksheets/wiki/Installing-Docker)
- [Image](https://hub.docker.com/r/shuohang/transition/): docker pull shuohang/transition:1.1
```
docker run -it -v /PATH/transition:/opt --rm -w /opt shuohang/transition:1.1 /bin/bash -c "sh squad_preprocess.sh"
docker run -it -v /PATH/transition:/opt --rm -w /opt/main --rm shuohang/transition:1.1 /bin/bash -c "th main.lua"
```

# Sequences Maching in Word Level
