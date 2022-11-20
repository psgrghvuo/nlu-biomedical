# NER on biomedical datasets

Biomedical NER data converted to [CoNLL format](http://ufal.mff.cuni.cz/conll2009-st/task-description.html) are placed in datasets directory. Five biomedical datasets are covered: DDI Dataset, JLPBA, BC5CDR, NCBI-Disease and, Anatomy Entity Mention Dataset. Experiments are done with 10 NLP models: PubMedBERT, BioBert, BioMed RoBERTa, BERT, RoBERTa, CNN, LSTM, CNN+CRF, LSTM+CRF and Logistic Regression.


## How to run the Code 

- Install the dependcies using requirements.txt file:

    ``` 
    pip install -r requirements.txt
    ```
- To run NER experiments, specify the model name and dataset name in run_experiments.sh file and run:

    ``` 
    cd nlu-biomedical
    bash run_experiments.sh
    ```
