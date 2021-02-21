# Deep learning with language models improves named entity recognition for PharmaCoNER

## Codes and models.
The repository is organized as follows.

```
PharmaCoNER
  -data
    -train.txt
    -dev.txt
    -test.txt
  -src
    -vocab.txt
    -config.json
    -pytorch_model.bin
  -outputs
  -labels.txt
  -metric.py
  -utils_ner.py
  -PharmaCoNER_run.py
```

* src: provide the BERT models. The file can be downloaded from this [URL](https://drive.google.com/drive/folders/1dwz7vexVsuj6swYr0Mdk7cNazp0IuG7Y?usp=sharing).
* data: provide the processed PharmaCoNER dataset (from the original [PharmaCoNER corpus](https://drive.google.com/drive/folders/1imuqrdy3BNazz0Lq7kTpjnLD3QB1QLfa?usp=sharing)).
* outputs: store the output files.

## Tested environments ##

* Ubuntu                    18.04
* python                    3.6.10
* transformers              2.8.0
* torch                     1.5.0
* numpy                     1.18.3
* scipy                     1.4.1

## Run the model ##

CUDA_VISIBLE_DEVICES=0 python PharmaCoNER_run.py\
--do_train   \
--do_eval    \
--do_predict   \
--evaluate_during_training   \
--model_type bert   \
--data_dir /$YourPath/PharmaCoNER/data   \
--model_name_or_path /$YourPath/src/$BERT_model_file   \
--max_seq_length 300   \
--per_gpu_train_batch_size 16   \
--per_gpu_eval_batch_size 16   \
--save_steps 100000    
--labels /$YourPath/PharmaCoNER/labels.txt    
--learning_rate 2e-5   
--num_train_epochs 20   
--seed 9  
--output_dir /$YourPath/PharmaCoNER/outputs/$Output_file
