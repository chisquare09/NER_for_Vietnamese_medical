# Named Entity Recognition for Vietnamese Medical Data
Using [Phobert](https://github.com/VinAIResearch/PhoBERT#-using-phobert-with-transformers) model by [VinAI Research](https://github.com/VinAIResearch) for NER task on [PhoNER_COVID19 Dataset](https://github.com/VinAIResearch/PhoNER_COVID19/tree/main)

#### Members
* Nguyen Thi Van- 22BI13459
* Dao Hoang Dung- 22BI13101
* Nguyen Minh Tuan- 22BI13447


## Problem Statement

**Goal:**  
Develop an effective NER system for Vietnamese medical data.

**Objectives:**
- Extract relevant medical entities (e.g., diseases, symptoms, treatments) from input sentences.
- Train a robust model using a dedicated Vietnamese medical dataset.
- Evaluate model performance using metrics such as F1-score and ROC curve.

## Project Description

The system processes Vietnamese sentences containing medical information. For example:

- **Input:**  
A Vietnamese sentence which contains medical information
Example:
```
Bệnh nhân A 25 tuổi quê quán Vĩnh Phúc đang điều trị tại bệnh viện Hà Nội
```

- **Output:**
A list of words from the sentence tagged with their corresponding medical entity labels.
Example:
```
{'words': ['<s>', 'Bệnh_nhân', 'A', '25', 'tuổi', 'quê_quán', 'Vĩnh_Phúc', 'đang', 'điều_trị', 'tại', 'bệnh_viện', 'Hà_Nội', '</s>'], 'tags': ['O', 'O', 'B-NAME', 'B-AGE', 'O', 'O', 'B-LOCATION', 'O', 'O', 'O', 'O', 'B-LOCATION', 'O']}
```
## Methodology

### Model Selection

The project uses **PhoBERT** due to its optimization for Vietnamese NLP tasks and its robust transformer-based architecture, which outperforms other models in NER tasks for the Vietnamese language.

### Dataset Description

The project is trained on the **PhoNER_COVID19 dataset**, which includes:
- Over 35K entities annotated in more than 10K sentences.
- Coverage of 10 distinct medical-related entity types such as PATIENT_ID, PERSON_NAME, AGE, GENDER, LOCATION, SYMPTOM_AND_DISEASE, etc.

### Data Preprocessing

Key preprocessing steps include:
- **Sentence Segmentation:** Using RDGSegmenter from VnCoreNLP.
- **Tokenization:** Performed with the PhoBERT AutoTokenizer to prepare data for training.

### Model Implementation

**Training Setup:**
- **Dataset:** Train and test sets from the PhoNER_COVID19 dataset.
- **Model:** PhoBERT.
- **Hyperparameters:**
  - Number of epochs: 4
  - Train batch size: 4
  - Evaluation batch size: 8
  - Weight decay: 0.01

The workflow involves tokenizing input sentences, loading the pre-trained PhoBERT model, fine-tuning it on the dataset, and finally tagging the tokenized words with corresponding entity labels.

## Results & Discussion

The model's performance was evaluated using precision, recall, and F1-score metrics. Additionally, ROC and Precision-Recall curves were generated for further performance analysis. Key evaluation highlights include:
- **High Accuracy:** Achieved high scores across various entity types, indicating robust performance in extracting medical entities.

| Category              | Precision | Recall | F1-score |
|-----------------------|-----------|--------|----------|
| AGE                   | 0.9893    | 0.9392 | 0.9636   |
| DATE                  | 0.9915    | 0.9886 | 0.9900   |
| GENDER                | 1.0000    | 0.9813 | 0.9905   |
| JOB                   | 0.9864    | 0.7415 | 0.8466   |
| LOCATION              | 0.9819    | 0.9495 | 0.9655   |
| NAME                  | 0.9782    | 0.9404 | 0.9589   |
| ORGANIZATION          | 0.9621    | 0.9069 | 0.9337   |
| PATIENT_ID            | 0.9975    | 0.9852 | 0.9913   |
| SYMPTOM_AND_DISEASE   | 0.9983    | 0.8904 | 0.9413   |
| TRANSPORTATION        | 0.9908    | 0.9782 | 0.9844   |


- **Challenges:** Included limited labeled data, complex entity relationships, and the need for extensive computational resources for fine-tuning.

## Model Demo

You can see a demo of the project along with the source code [here](https://github.com/chisquare09/NER_for_Vietnamese_medical/blob/main/Final_NLP.ipynb)

## Conclusion

The project successfully built a NER model for Vietnamese medical data using PhoBERT, achieving high accuracy in entity extraction. Future work includes expanding the dataset for better generalization and integrating the system with real-world hospital systems.

## References

- Project Repository: [NER_for_Vietnamese_medical](https://github.com/chisquare09/NER_for_Vietnamese_medical)
- Dataset: [PhoNER_COVID19 Dataset](https://github.com/VinAIResearch/PhoNER_COVID19/tree/main)
- Data Preprocessing Tool: [RDRsegmenter](https://github.com/datquocnguyen/RDRsegmenter)
- Model: [PhoBERT](https://github.com/VinAIResearch/PhoBERT)
