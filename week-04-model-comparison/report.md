# Model Comparison Report — Week 4

**Name:** Shiva Ramdath
**Date:** 04/23/2026
**Capstone Project:** Threat Intelligence Feed Dashboard
**My Component:** Relevance Scorer

## Test Setup

**Input dataset:** 5 \[domain] text samples covering:

* 2 clearly concerning/high-severity records
* 1 ambiguous/edge case record
* 2 routine/benign records

**Models tested:**

1. distilbert-base-uncased-finetuned-sst-2-english (sentiment)
2. facebook/bart-large-mnli (zero-shot classification)
3. dslim/bert-large-NER (named entity recognition)
4. Groq Llama 3 8B (LLM classification)

**Evaluation criteria:** label accuracy, confidence score, speed, ease of integration in n8n

## Results Summary

|Record|Sentiment|Zero-Shot|NER Entities|Groq|
|-|-|-|-|-|
|1|Negative - 0.9961|threat intelligence|Moscow|High|
|2|Negative - 0.9985|unverified report||Info|
|3|Negative - 0.9952|threat intelligence|Amazon|High|
|4|Negative - 0.9994|threat intelligence|SS|Critical|
|5|Negative - 0.9880|unverified report||Info|
|--------|-----------------|-------------------|--------------|--------|

## Analysis

**Where models agreed:** Model 2,3 \& 4 mostly agreed with each other
**Where models disagreed:** Model 1 disagreed with all of the other models, stating that all the text samples were negative.
**Most accurate model overall:** Groq Llama 3 8B
**Fastest/most practical:** distilbert-base-uncased-finetuned-sst-2-english

## Recommended Models for My Capstone Component

**Component:** Relevance Scorer
**Primary model:** cybersectony/phishing-email-detection-distilbert\_v2.4.1 - phishing emails tend to have a similar diction to threats, usually demanding immediate action.
**Secondary model (if applicable):** mrm8488/bert-tiny-finetuned-sms-spam-detection - spam detection focuses on the diction of the data which can be correlated to identifying threats
**Rejected models and why:**- papluca/xlm-roberta-base-language-detection - language detection would be useful if the threats were different languages. However, with the assumption that majority threats would be in English, this model wouldn't be that useful for our project.

## Failure Cases and Limitations

The 'distilbert-base-uncased-finetuned-sst-2-english' model gave inaccurate sentiment labels. This was surprising to me as it looked very trustworthy. This tells me that the model should be utilized alongside another model to ensure the accuracy of the data whilst in production.

## Next Steps

If I had more time, I would like to test with more models with potentially lesser download to see how the data produced from it compares to the data produced from a model more well known and mainstream

