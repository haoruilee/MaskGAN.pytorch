# MaskGAN.pytorch

#### This is a work forked by  jerinphilip/MaskGAN.pytorch, made some polish, thanks to @birdmanmandbir(https://github.com/birdmanmandbir), he contributes a lot.

#### If you like this project, please give me and these co-workers one star :)

A PyTorch attempt at reimplementing 

* MaskGAN: Better Text Generation via Filling in the _______ , William Fedus, Ian Goodfellow, Andrew M. Dai
  [[paper]](https://openreview.net/pdf?id=ByOExmWAb)
 

# Core environment

Pytorch1.1
Python3

Some of you may encounter "no attribute 'IterableDataset", please check your pytorch version and use pip install, not conda.


# Setting up

#### Module

Some devices may enconter : module:command not find

```
sudo apt-get install environment-modules
```

#### tqdm

```
python3 -m pip install tqdm
```

#### SentencePiece

I used [google/SentencePiece](https://github.com/google/sentencepiece) to bring down the vocabulary to make training easier. The trained models are available inside this repository. Install the python bindings through pip so the code can use it.

```
python3 -m pip install sentencepiece
```

#### fairseq

This code is build using the basic blocks provided by [pytorch/fairseq](https://github.com/pytorch/fairseq). Please follow instructions there to install fairseq as a library.

```
python3 -m pip install git+https://github.com/pytorch/fairseq
```

#### IMDB Reviews Dataset
```
mkdir datasets 
cd datasets
IMDB_DATASET='http://ai.stanford.edu/~amaas/data/sentiment/aclImdb_v1.tar.gz'
wget $IMDB_DATASET -O aclImdb_v1.tar.gz
tar xvzf aclImdb_v1.tar.gz
``` 

#### Training

Launch a visdom instance for logging. If you enconter some HTTP errors, perhaps it's visdom's problem. Try to restart it or change the port :)

```
python3 -m pip install visdom # Install if not present.
python3 -m visdom.server &
```

#### Before run the cmd.sh, Please change the check point path in train.py, line 40 to your own path


Run the training script.

```
python3 -m mgan.main \
  --path datasets/aclImdb/train/ \
  --spm_path datasets/aclImdb/train/imdb
```
