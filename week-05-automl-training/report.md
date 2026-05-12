# Week 5 Report: AutoML Training & Fine-Tuned Model Evaluation 
**Name:** Shiva Ramdath 
**Date:** 04/28/2026
**Capstone Project:** Threat Intelligence Feed Dashboard
**My Component:** Relevance Scorer 

## Part A: Teachable Machine Training 

### Training Setup
- **Task:** Phishing vs Legitimate email screenshot classification
- **Training images per class:** 20 
- **Test images per class:** 5 
- **Total training time:** 1 min
 
### Test Results 
| # | Actual Class | Predicted Class | Confidence | Correct? | 
|---|--------------|-----------------|------------|----------| 
| 1 |   Phishing   |    Phishing     |     98%    |   Yes    | 
| 2 |   Phishing   |    Phishing     |    100%    |   Yes    | 
| 3 |   Phishing   |    Phishing     |     67%    |   Yes    |
| 4 |   Phishing   |   Legitimate    |     99%    |    No    |
| 5 |   Phishing   |    Phishing     |     97%    |   Yes    | 
| 6 |  Legitimate  |   Legitimate    |    100%    |   Yes    |
| 7 |  Legitimate  |   Legitimate    |    100%    |   Yes    |
| 8 |  Legitimate  |    Phishing     |     95%    |    No    | 
| 9 |  Legitimate  |   Legitimate    |     94%    |   Yes    | 
|10 |  Legitimate  |    Phishing     |    100%    |    No    |

### Confusion Matrix 
|            | Phishing | Legitimate | 
|------------|----------|------------| 
|  Phishing  |  TP = 4  |   FN = 2   | 
| Legitimate |  FP = 1  |   TN = 3   | 

### Calculated Metrics
- **Accuracy:** 70% 
- **Precision:** 66.67% 
- **Recall:** 80% 
- **F1 Score:** 72.73% 

### Interpretation 
My precision is lower than my recall. This means that my model had fewer missed threats and potentially more false alarms. I would have had more training data and more diverse data

--- 

## Part B: Generic vs Fine-Tuned Model Comparison 

### Models Tested
1. **Generic:** distilbert-base-uncased-finetuned-sst-2-english (sentiment) 
2. **Fine-Tuned A:** cybersectony/phishing-email-detection-distilbert_v2.4.1 — identify phishing emails 
3. **Fine-Tuned B:** mrm8488/bert-tiny-finetuned-sms-spam-detection — classify text as spam or not

### Results
Record 1 : A critical vulnerability affecting software in your stack is actively being exploited and includes matching IOCs from your logs.
Record 2 : A medium-severity vulnerability targets software your organization uses but shows no signs of active exploitation.
Record 3 : A high-severity threat is widely exploited but does not affect any technologies in your environment.
Record 4 : A low-severity alert includes an IP address that appears in your network logs but has no software match.
Record 5 : An older high-severity vulnerability affects your systems but has not been exploited in recent years.

|   Input  | Generic Label (Score) | Fine-Tuned A Label (Score) | Fine-Tuned B Label (Score) | Best Model | 
|----------|-----------------------|----------------------------|----------------------------|------------| 
| Record 1 |        0.9982         |           0.9985           |           0.9003           |   Model A  | 
| Record 2 |        0.9977         |           0.8607           |           0.8326           |   Generic  | 
| Record 3 |        0.9914         |           0.9862           |           0.9283           |   Generic  | 
| Record 4 |        0.9994         |           0.9998           |           0.8509           |   Model A  | 
| Record 5 |        0.5066         |           0.9895           |           0.9275           |   Model A  | 

### Analysis 

**Generic model strengths:** It performed well with the first 4 records  
**Generic model weaknesses:** It gave low confidence on the fifth record
**Fine-tuned model advantage:** The fifth record was the only time the fine-tuned models outperformed the generic
**Biggest surprise:** I did not expect for the generic model to outperform majority of the fine-tuned models 

### Recommended Model for My Capstone Component 

**Component:** Relevance Scorer

**Primary model:** cybersectony/phishing-email-detection-distilbert_v2.4.1 - This model analyzes the language of the input. Even though it is designed for phishing text, the same manipulative text can be utilized in threats. 

**Confidence threshold:** 90% and up : auto-action & under 90% : human review

**Priority metric:** Precision. In a threat intelligence feed dashboard, having fewer false alarms is preferred

--- 

## Limitations & Next Steps
With more data, I would run some more testing to see if potentially the Fine-Tuned models could be more reliable. I would potentially like to try fine-tuning my own model. Perhaps, it can produce better scores than the generic and fine-tuned models utilized. I would like to test a model that is design for identifying threats in text. 
 
 
