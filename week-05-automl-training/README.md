# Week 5: AutoML & No-Code Model Training 
Trained a custom image classifier with Google Teachable Machine and compared 
generic vs fine-tuned Hugging Face models for the Relevance Scorer component 
of our Threat Intelligence Feed Dashboard. 

## Custom Model Training
- Built a Phishing/Legitimate image classifier with Teachable Machine 
- Achieved 70% accuracy on 10 held-out test images 
- Precision: 66.67% | Recall: 80% | F1: 72.73% 

## Fine-Tuned Model Comparison 
Compared 3 models (1 generic + 2 fine-tuned) on 5 test inputs: 
- Generic: distilbert-sst-2 (sentiment) 
- Fine-Tuned A: cybersectony/phishing-email-detection-distilbert_v2.4.1 
- Fine-Tuned B: mrm8488/bert-tiny-finetuned-sms-spam-detection 

## Finding 
Recommended phishing-email-detection-distilbert_v2.4.1 for Relevance Scorer because it clearly distinguished actual threats and false alarms for the inputted text. Fine-tuned models showed comparable erformance with better handling of edge cases. 

See `report.md` for full analysis.