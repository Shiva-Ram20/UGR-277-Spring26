# Week 7: RAG Security Knowledge Assistant — Evaluation Report

## 1\. Setup Summary

* **LLM:** llama-3.3-70b-versatile via Groq
* **Embeddings:** sentence-transformers/all-MiniLM-L6-v2 via HuggingFace
* **Vector Store:** In-Memory Vector Store
* **Documents loaded:** mitre-defense-impairment, mitre-stealth \& mitre-initial-access

## 2\. Test Results

|#|Question|Used Documents?|Quality|Notes|
|-|-|-|-|-|
|1|What are common techniques for credential access?|Yes|Partial|Gave little description|
|2|How does phishing relate to initial access in the ATT\&CK framework?|Yes|Good||
|3|What is lateral movement and what techniques do attackers use?|Yes|Partial|Gave little description|
|4|What is the difference between spearphishing attachment and spearphishing link?|Yes|Good||
|5|How can an attacker modify system files to bypass security controls, and what are the indicators of this defense impairment?|Yes|Good||

## 3\. Edge Case Observations

* **Unrelated question:** Admitted it doesn’t have information
* **Topic not in documents:** Admitted that it did not have the information required to answer the question.

## 4\. Reflection

* What surprised you about how RAG works?
I was surprised at the level of detail it provided for some topics and the efficiency of how quickly that information was received.
* How could you improve this chatbot for real-world use?
I would like to add more txt files with various other sources of information so that it can answer some topics that weren't covered by the initial 3 documents
* How might you use RAG in your capstone project?
A RAG could be utilize to provide a lengthy and more in-depth description of a threat and potentially provide what actions should be taken



Chat Link:

https://cloud.flowiseai.com/chatbot/79929dd0-306b-4690-9adc-fb1a731e9d30

