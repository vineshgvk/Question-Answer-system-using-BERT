# Question-Answer-system-using-BERT

This repository contains code to train and evaluate a question-answering model on a custom dataset. 

## Overview

The model is based on BERT (Bidirectional Encoder Representations from Transformers) for extractive question answering. It fine-tunes BERT on a dataset of paragraphs, questions, and answers to predict answer spans from the paragraph when given a related question.

## Project Goals

The goals of this project are:

- Fine-tune a BERT neural network for extractive question-answering 
- Compare the performance of the fine-tuned model versus pre-trained model
- Incorporate context extraction from PDF documents
- Develop an end-to-end system to answer questions based on a user's PDF document


## Usage

The main code handles:

- Loading and preprocessing the question-answering dataset
- Tokenizing the context paragraphs and questions
- Encoding the context-question pairs with labels for the start and end tokens of the answer span
- Creating a PyTorch dataset and data loader
- Fine-tuning a BERT model for question-answering 
- Evaluating the model and comparing a finetuned version to the pre-trained version
- Saving the finetuned model
- Post-processing with text extraction from PDFs and answer validation

To use your own data:

1. Prepare the dataset in JSON format with contexts, questions, and answer annotations
2. Update the data loading and preprocessing code
3. Train the model by running the main script
4. Test predictions by using the evaluation function
5. Modify context extraction from PDFs as needed

The model expects a JSON formatted dataset with a dictionary for each example containing:

```json
{
  "context": "Text paragraph containing answer",
  "qas": [
    {
      "question": "Related question?",
      "answers": [
        {
          "text": "Answer text span",
          "answer_start": 15 
        }
      ]
    }
  ]
}
```

## Results

The fine-tuned BERT model was compared to the pre-trained BERT QA model.

Fine-tuned model accuracy: 64%

Pretrained model accuracy: 9% 

The significant improvement demonstrates the importance of fine-tuning domain-specific data.

![image](https://github.com/vineshgvk/Question-Answer-system-using-BERT/assets/67590588/d124ad67-e95a-4c28-a3f8-93e0ef2b44b4)


## Requirements

The code requires the following libraries:

- PyTorch, Transformers
- scikit-learn, nltk  
- sentence_transformers
- PyPDF2

The model was developed with Python 3.8 and PyTorch 1.10.0.

## References

BERT QA Model used in this project: https://huggingface.co/bert-base-uncased
