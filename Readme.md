# Natural Language Understanding on Biomedical domain

This is the official repository of the paper **Natural Language Understanding on Biomedical domain**. 

## Repository Organization

```bash
├── model_cnn_lstm/
|    ├── crf.py
|    ├── dataset.py
|    ├── main.py
|    ├── model.py
|    ├── train.py
|    ├── utils.py
├── model_handcrafted_features/
|    ├── main.py
├── model_transformer/
|    ├── main.py
├── NER_datasets/
|    ├── train_ncbi.txt
|    ├── test_ncbi.txt
|    ├── train_jnlpba.txt
|    ├── test_jnlpba.txt
|    ├── train_bc5cdr.txt
|    ├── test_bc5cdr.txt
|    ├── train_anatem.txt
|    ├── test_anatem.txt
|    ├── train_DDI.txt
|    ├── test_DDI.txt
├── Chinese Intent Detection Validation/
|    ├── CMID_validation.txt
|    ├── KUAKE-QIC_validation.txt
├── run_experiments.sh
├── README.md
```

## Files Descriptions

1. **model_cnn_lstm** - This folder contains the code for running CNN and LSTM NER experiments.
2. **model_handcrafted_features** - This folder contains the code for running Logistic Regression and XGBosst models for NER.
3. **model_transformer** - This folder contains the code for running transformer models for NER. Please refer to [BioBERT repository](https://github.com/dmis-lab/biobert-pytorch) for more details.
4. **NER_datasets** - This folder contains the train-test splits of the 5 biomedical NER datasets - Drug-Drug Interaction Dataset, JLPBA, BC5CDR, NCBI-Disease and, Anatomy Entity Mention Dataset. All the datasets converted to [CoNLL format](http://ufal.mff.cuni.cz/conll2009-st/task-description.html) and processed using processing steps used in [BioBERT repository](https://github.com/dmis-lab/biobert-pytorch). 
5. **Chinese Intent Detection Validatio** - This folder contains the manual translation validation results for CMID and KUAKE-QIC dataset.
6. **run_experiments.sh** - Shell file for running NER experiments.


## How to run the NER Experiments

- Preprocess the uploaded the dataset files to break the text examples considering the max token length. Change the "model" variable in run_experiments.sh and use the shell script to evaluate the model on all biomedical datasets:

    ``` 
    bash preprocess.sh
    ```
- Experiment outputs are written in the output directory.

## Intent Detection Translation validation

- Please refer to [CMID paper](https://bmcmedinformdecismak.biomedcentral.com/articles/10.1186/s12911-020-1122-3) and [CBLUE repository](https://github.com/CBLUEbenchmark/CBLUE) for original datasets in Chinese. Datasets are translated to english using Google Translate API. We take a random sample of 400 examplese from CMID and 400 random examples from Dev set of KUAKE-QIC dataset for manual validaiton by a Chinese expert. We provide three classes in the "validation" column in the sheets:
    
    ``` 
    1  : Translation is accurate
    0  : Translation closely resembles original meaning
    -1 : Translation is inaccurate
    ```

Additionally, we also provide correct manual translations in some cases. We were not able to reproduce the performances reported in [CMID paper](https://bmcmedinformdecismak.biomedcentral.com/articles/10.1186/s12911-020-1122-3) on original Chinese version. The classification performance of models used by CMID authors (Fasttext, TextCNN, TextGCN) on English translations were worse than the results given by BERT and RoBERTa. We attach the email communication with the CMID authors below:
![Poster Image](https://github.com/psgrghvuo/nlu-biomedical/blob/main/cmid_email_ss.png)

## References
* https://github.com/jiesutd/NCRFpp
* https://github.com/melanietosik/maxent-ner-tagger
