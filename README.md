# 실행 방법
```
cd /path/to/models/official/transformer

# Ensure that PYTHONPATH is correctly defined as described in
# https://github.com/tensorflow/models/tree/master/official#requirements

export PYTHONPATH="$PYTHONPATH:/path/to/models"
```
# Export variables
PARAM_SET=big
DATA_DIR=$HOME/transformer/data
MODEL_DIR=$HOME/transformer/model_$PARAM_SET
VOCAB_FILE=$DATA_DIR/vocab.ende.32768

# 데이터 다운로드
```
python data_download.py --data_dir=$DATA_DIR
```
(제가 다운로드한 데이터는 엘사 11번 /tmp/transformer_data에 잇습니다.)

# 실행 커멘드 
(model_dir는 체크 포인트를 불러오는 곳으로, 트레이닝 할때는 아무 곳이나 지정하면 됩니다.)
```
python transformer_main.py --data_dir=$DATA_DIR --model_dir=$HOME/transformer/newww \
  --vocab_file=$VOCAB_FILE --param_set=$PARAM_SET \
  --bleu_source=$DATA_DIR/newstest2014.en --bleu_ref=$DATA_DIR/newstest2014.de --num_gpus=2 --steps_between_evals=2 --train_steps=4 --batch_size=4096
```



# TensorFlow Models

This repository contains a number of different models implemented in [TensorFlow](https://www.tensorflow.org):

The [official models](official) are a collection of example models that use TensorFlow's high-level APIs. They are intended to be well-maintained, tested, and kept up to date with the latest stable TensorFlow API. They should also be reasonably optimized for fast performance while still being easy to read. We especially recommend newer TensorFlow users to start here.

The [research models](https://github.com/tensorflow/models/tree/master/research) are a large collection of models implemented in TensorFlow by researchers. They are not officially supported or available in release branches; it is up to the individual researchers to maintain the models and/or provide support on issues and pull requests.

The [samples folder](samples) contains code snippets and smaller models that demonstrate features of TensorFlow, including code presented in various blog posts.

The [tutorials folder](tutorials) is a collection of models described in the [TensorFlow tutorials](https://www.tensorflow.org/tutorials/).

## Contribution guidelines

If you want to contribute to models, be sure to review the [contribution guidelines](CONTRIBUTING.md).

## License

[Apache License 2.0](LICENSE)
