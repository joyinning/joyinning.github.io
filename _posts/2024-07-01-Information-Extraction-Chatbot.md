---
title: Information Extraction Chatbot
date: 2024-07-01
categories: [Blogs, NLP/DL]
tags: [Deep Learning, BERT, BiLSTM, Chatbot, GPT 3.5]
pin: true
---

[![Open in Github Page](https://img.shields.io/badge/Hosted_with-GitHub_Pages-blue?logo=github&logoColor=white)](https://github.com/joyinning/chatbot-info-extraction/blob/main/Information_Extraction_Chatbot.ipynb)


# Information Extraction Chatbot

## Chatbot
<img width="1666" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/dc72449b-2ea3-475a-b08c-3359ac490f8e">
https://huggingface.co/spaces/joyinning/chatbot-info-extraction

## Project Overview
This project aims to develop a sophisticated chatbot capable of extracting key information from text and answering questions in a 5W1H format. The project involves training and evaluating natural language processing (NLP) models and deploying them through a user-friendly Streamlit web interface.

## Phase 1: Data Preparation and Preprocessing
**Objective**: Prepare and process raw text data for model training and evaluation. <br>
**Process**:
1. **Data Acquisition**: Obtain a dataset containing labeled entities in sentences.
2. **Data Cleaning**: Remove irrelevant or noisy data points.
3. **Tokenization**: Split sentences into individual words or subwords.
4. **Label Encoding**: Convert entity labels into numerical representations.
5. **Train/Test Split**: Divide the data into training and testing sets.
6. **Tools**: pandas, matplotlib, transformers

**Key Activities**:
1. **Strategic Data Preprocessing**: Highlighted expertise in data cleaning and preparation by defining a label mapping strategy for NER tasks. Filtered out short sentences to enhance model training efficiency and accuracy.
2. **Advanced Tokenization and Alignment**: Employed the AutoTokenizer from the transformers library to ensure seamless integration with pretrained models, efficient subword tokenization, automatic handling of special tokens, and precise alignment of labels with tokenized outputs.
3. **Optimized Dataset Structure**: Leveraged DatasetDict to organize data in a format compatible with the Hugging Face Transformers library. Utilized DataCollator to streamline data preparation for model training, incorporating dynamic padding, label alignment, attention mask creation, tensor conversion, and efficient batch creation.

**Key Results**:
1. The dataset consisted of 47,959 sentences with an average length of 125 words.
2. Defined a clear mapping for NER labels (e.g., "B-per" for beginning of a person's name).

## Phase 2: BERT Model Training (Named Entity Recognition)
**Objective**: Train a BERT model for accurate named entity recognition (NER). <br>
**Model Selection**: BERT was chosen for its ability to capture contextual information in text, crucial for identifying entities.

**Process**:

1. **Fine-tuning**: Fine-tune a pre-trained BERT model on the prepared NER dataset.
2. **Evaluation Metrics**: Utilize precision, recall, F1-score, and accuracy to assess model performance.
3. **Tools**: transformers, datasets, seqeval, PyTorch

**Key Activities**:
1. **Metric Definition**: Defined a comprehensive evaluation function (compute_metrics) using the seqeval library. This function calculates precision, recall, F1-score, and accuracy, specifically for NER tasks, ensuring a rigorous assessment of model performance.

2. **Model Loading and Fine-tuning**: Leveraged the transformers library to load a pre-trained BERT model (bert-base-cased) and fine-tuned it on a labeled NER dataset. Customized the model by specifying the number of entity labels and creating mappings between labels and their IDs.

3. **Training Setup**: Implemented a meticulous training process with the transformers Trainer. Carefully configured hyperparameters, including a learning rate of 2e-5, a batch size of 16, and the use of weight decay for regularization. Employed learning rate warmup to improve model stability and accelerate convergence.

**Key Results**:
1. Trained the model for 3 epochs, continuously monitoring training and validation loss.
2. Observed a steady decrease in training loss from 0.1039 to 0.0588, indicating effective learning.
3. Validation loss also decreased from 0.0937 to 0.0889, demonstrating the model's ability to generalize to unseen data.
4. Achieved a final accuracy of 97.28%, showcasing the model's strong performance in identifying named entities. (Precision: 0.8326, Recall: 0.8446, F1-score: 0.8386) <br>
   <img width="569" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/6cc852d4-efc5-4c39-9c1b-9340dbeeff90">

6. This output demonstrates the model's ability to correctly identify and label the named entities "Elon Musk" (person) and "SpaceX" (organization), as well as the time entity "2002."
   <img width="903" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/2606a8f3-4b53-4a98-8682-cbf179ab0634">

   
## Phase 3: BiLSTM Model with BERT Embeddings (Enhanced NER)
**Objective**: Combine a bidirectional LSTM (BiLSTM) model with BERT embeddings to further improve NER performance. <br>
**Model Selection**: BiLSTM was added to capture sequential dependencies in text, enhancing the model's understanding of entity relationships.

**Process**:
1. **Integration**: Incorporate a BiLSTM layer into the model architecture, utilizing BERT embeddings as input.
2. **Fine-tuning**: Continue fine-tuning the combined model to optimize its performance.

**Key Activities**:
1. **BiLSTM Model Design**: Developed a custom BiLSTM model (BiLSTMForTokenClassification) in PyTorch. This architecture was chosen to leverage the strengths of both BERT and BiLSTM:
  - BERT Embeddings: Utilized the rich contextual representations learned by BERT to provide the BiLSTM with a deeper understanding of word meanings in context.
  - BiLSTM Architecture: Incorporated a bidirectional LSTM layer to effectively capture sequential dependencies in the text, enabling the model to consider both past and future context when making predictions about named entities.
2. **Model Implementation**: Carefully implemented the BiLSTMForTokenClassification model, including:
  - Freezing BERT Embeddings: Froze the parameters of the BERT embedding layer to prevent catastrophic forgetting of pre-trained knowledge during fine-tuning.
  - BiLSTM Layer: Added a BiLSTM layer to process the BERT embeddings, capturing bidirectional contextual information.
  - Dropout Layer: Introduced a dropout layer to mitigate overfitting and improve model generalization.
  - Classification Layer: Designed a linear classifier to map the BiLSTM output to the desired NER labels.
  - Loss Calculation: Integrated a cross-entropy loss function with an attention mask to focus on non-padding tokens during training.
3. **Training and Fine-tuning**: Fine-tuned the combined BiLSTM-BERT model on the prepared NER dataset using a systematic approach:
  - Training Configuration: Set appropriate hyperparameters, including a learning rate of 2e-5, a batch size of 16, and weight decay for regularization.
  - Iterative Training: Trained the model for 5 epochs, monitoring training and validation loss at each epoch.
 
**Key Results**:
1. Observed a consistent decrease in both training loss (from 0.1170 to 0.0472) and validation loss (from 0.1042 to 0.0953) across epochs, indicating effective learning and generalization.
2. Achieved a final accuracy of 97.31%, demonstrating the model's strong capability in identifying and classifying named entities. <br>
   <img width="561" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/92d1e008-087b-4066-9d9b-cb856c82ebe2">
3. Assessed the fine-tuned model's performance on a new sentence ("Elon Musk founded SpaceX in 2002") and saved it for future use. The model successfully identified and labeled entities "Elon Musk" (person), "SpaceX" (organization), and "2002" (time) with high precision.
   <img width="1035" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/e003418f-4b47-496b-becc-5e90d47a14da">

   
## Phase 4: 5W1H Question Answering
**Objective**: Implement a system capable of answering "who," "what," "when," "where," "why," and "how" (5W1H) questions based on extracted information.<br>

**Process**:
1. **Information Extraction**: Utilize the BiLSTM-BERT model to extract named entities and their types from input text.
2. **4W Questions**: Use a question-answering model to answer "who," "what," "when," and "where" questions directly from the extracted information.
3. **1W1H Questions**: Generate "why" and "how" questions based on the extracted information and use GPT-3.5 to provide insightful answers.
4. **Tools**: transformers, deepset/bert-base-cased-squad2, OpenAI GPT-3.5

**Key Activities**:
1. **Model Ensemble**:
  - Leveraged the BiLSTM-BERT Model: The previously fine-tuned BiLSTM-BERT model was employed for robust named entity recognition (NER), ensuring accurate identification of key information types like people, organizations, and locations.
  - Integrated Question-Answering Model: Employed the pre-trained deepset/bert-base-cased-squad2 model for answering "who," "what," "when," and "where" (4W) questions directly. This model is specifically designed for question-answering tasks and is known for its accuracy.
  - Incorporated GPT-3.5: Utilized the advanced language model GPT-3.5 from OpenAI for generating insightful responses to "why" and "how" (1W1H) questions. GPT-3.5's ability to understand and generate nuanced text makes it ideal for handling complex questions.
2. **Function Development**:
  - **predict_tags**: Created a function to streamline the process of predicting NER tags for a given sentence, utilizing the BiLSTM-BERT model and its tokenizer.
  - **extract_4w_qa**: Developed a function to extract 4W information from a sentence based on the predicted NER tags. This function utilizes the question-answering model to directly answer 4W questions related to the extracted entities.
  - **generate_why_or_how_question_and_answer**: Crafted a function to generate relevant "why" or "how" questions from the extracted information. It then uses GPT-3.5 to generate answers to these complex questions, providing deeper insights.
  - **get_why_or_how_answer**: Built a function to interface with the OpenAI API, allowing the system to query GPT-3.5 effectively and retrieve the generated answers for the "why" and "how" questions.
3. **Token Counting for Optimization**: Implemented a count_tokens function to measure the number of tokens in a given text string. This aids in optimizing the interaction with GPT-3.5, ensuring efficient use of resources and avoiding unnecessary costs.

**Key Results**:
1. The system successfully answered 5W1H questions, showcasing its ability to understand and extract information from text comprehensively.

## Phase 5: Deployment with Streamlit
**Objective**: Deploy the chatbot as a user-friendly web application. <br>

**Process**:

1. **File Structure**: Organize code into app.py, model_utils.py, requirements.txt, and models/ directory.
2. **Gradio Interface**: Utilize Gradio's intuitive interface elements to create a user-friendly input area for text and a clearly visible button to trigger information extraction.
3. **Deployment**: Create a new Space on Hugging Face, upload the files, and Configure the Space settings to use Gradio as the SDK and select the appropriate hardware.
4. **Testing and Sharing**: Thoroughly test the deployed chatbot on Hugging Face Spaces to ensure it functions correctly.

**Key Results**:
The 5W1H question-answering system successfully responded to questions on various sentences, demonstrating the ability to:
1. **Extract 4W Information**: Accurately identified "Who," "What," "When," and "Where" information from sentences using NER. <br>
2. **Answer 4W Questions**: Provided precise answers to direct questions about the extracted entities using a dedicated question-answering model.
3. **Generate and Answer 1W1H Questions**: Formulated relevant "Why" and "How" questions based on context and generated insightful answers using GPT-3.5.
   <img width="926" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/c4427f10-e947-4833-9fa0-890589608b50">

   
## Conclusion
This project successfully developed an information extraction chatbot capable of accurately identifying named entities and answering complex questions about them. By combining BERT, BiLSTM, and GPT-3.5, the chatbot achieved high accuracy in NER and generated insightful answers to 5W1H questions. The project followed a structured data science cycle, showcasing the power of NLP for extracting valuable insights from text data. The chatbot's successful deployment on Streamlit demonstrates its potential for real-world applications.

