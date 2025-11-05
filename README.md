# Physician Notetaker – Clinical NLP Pipeline (LangChain + OpenAI)

## Abstract
This project presents an AI-based medical transcription and summarization system that converts physician–patient conversations into structured clinical summaries, SOAP notes, and patient sentiment analysis. It integrates LangChain, OpenAI GPT-4o-mini, spaCy, and Transformers to develop a modular and explainable NLP pipeline for healthcare.

---

## Features
- **Medical Entity Extraction**: Identifies Symptoms, Diagnosis, Treatment, and Prognosis.  
- **Summarization**: Generates concise summaries using transformer-based models.  
- **Sentiment and Intent Detection**: Classifies patient utterances.  
- **SOAP Note Generation**: Produces Subjective, Objective, Assessment, and Plan sections.  
- **Error Handling**: Manages missing data and JSON inconsistencies efficiently.

---

## Architecture
The system processes the transcript through several stages:  
1. Medical NER (spaCy + rule-based).  
2. Summarization (Transformers).  
3. Sentiment and Intent Detection (LLM).  
4. SOAP Note Generation (LangChain + OpenAI).  
5. Structured JSON Output.

---

## Final Output
The output includes extracted entities, summarized reports, keywords, patient sentiment, and structured SOAP notes in JSON format.
```json
{
  "Patient_Name": "Janet Jones",
  "Entities": {
    "Symptoms": ["Back Pain", "Stiffness"],
    "Diagnosis": ["Whiplash"],
    "Treatment": ["Physiotherapy", "Painkillers"],
    "Prognosis": ["Full Recovery"]
  },
  "Summary": "Ms. Jones suffered a whiplash injury in a car accident last September. She had to go through ten sessions of physiotherapy to help with the stiffness and discomfort. The first four weeks were rough. There are no signs of long-term damage or degeneration. If anything changes, you can always come back for a follow-up. At this point, you're on track for a full recovery.",
  "Keywords": ["Accident", "Back", "Pain", "September", "Car"],
  "Patient_Sentiments": [
    {"Sentiment": "Anxious", "Intent": "Reporting symptoms"},
    {"Sentiment": "Reassured", "Intent": "Reporting symptoms"}
  ],
  "SOAP": {
    "Subjective": {
      "Chief Complaint": "Ms. Jones suffered a whiplash injury in a car accident last September.",
      "History of Present Illness": "She had to go through ten sessions of physiotherapy to help with the stiffness and discomfort. The first four weeks were rough."
    },
    "Objective": {
      "Symptoms": ["Back Pain", "Stiffness"],
      "Diagnosis": ["Whiplash"],
      "Treatment": ["Physiotherapy", "Painkillers"],
      "Prognosis": ["Full Recovery"]
    },
    "Assessment": "No signs of long-term damage or degeneration. On track for a full recovery.",
    "Plan": "If anything changes, you can always come back for a follow-up."
  }
}
```

---

## Tech Stack

| Component | Technology |
|------------|-------------|
| Framework | LangChain |
| LLM | OpenAI GPT-4o-mini |
| NER Engine | spaCy |
| Summarization | facebook/bart-large-cnn |
| Sentiment Model | DistilBERT SST-2 |
| Keyword Extraction | YAKE |
| Output Format | JSON (SOAP Structured) |

---

## Workflow
1. Extract and clean transcript data.  
2. Perform entity extraction and summarization.  
3. Conduct sentiment and intent classification.  
4. Generate SOAP notes using LLM.  
5. Produce validated structured reports.

---

## Setup
```bash
pip install langchain openai transformers spacy yake
python -m spacy download en_core_web_sm
export OPENAI_API_KEY="your_api_key_here"
python physician_notetaker.py
```

---

## Future Enhancements
- Integration of ClinicalBERT or BioBERT for improved NER.  
- Real-time transcription using speech-to-text.  
- Streamlit dashboard for visualization.  
- FHIR/EHR data interoperability.

---


## Author

**Aishwarya R**  
*MCA in Artificial Intelligence*  
*Focus Areas:* Natural Language Processing (NLP), LangChain, and Generative AI  


---

## License
MIT License © 2025 — Open for research, clinical, and educational use.

