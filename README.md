Resume PDF Extractor API
A FastAPI-based web service to extract structured resume information (name, contact info, education, experience, skills, certifications, and projects) from PDF files using pdfplumber and spaCy.

Features
Extracts text content from PDF resumes
Uses spaCy NER to extract the candidate's name
Extracts email and phone numbers using regex
Parses key resume sections based on predefined headers
CORS enabled for local React frontend at ports 3000
Requirements
Python 3.8+
Libraries listed in requirements.txt
Installation
1. Clone the repository
git clone git@github.com:mohan-1705/resume_builder_server.git
cd resume-builder
git checkout -b server
2. Create and activate a virtual environment
On Windows (PowerShell)
python -m venv venv
.\venv\Scripts\activate
On macOS/Linux (bash/zsh)
python3 -m venv venv
source venv/bin/activate
3. Install dependencies
pip install -r requirements.txt
4. Download spaCy English model
python -m spacy download en_core_web_sm
Running the API
uvicorn main:app --reload
The API will be accessible at http://127.0.0.1:8000
Frontend running at http://localhost:3000 or http://127.0.0.1:3000 is allowed by CORS
API Endpoints
GET / Returns a welcome message.

POST /extract Upload a PDF file (multipart/form-data, key=file) to extract resume data. Returns JSON with extracted fields.

Example cURL request
curl -X POST "http://127.0.0.1:8000/extract" -F "file=@/path/to/resume.pdf"
Project Structure
main.py — FastAPI app and extraction logic
requirements.txt — Python dependencies
Notes
Temporary files are used to store uploaded PDFs during processing.
Extraction is based on keyword matching and basic NLP; accuracy depends on resume format.
Feel free to customize section headers in SECTION_HEADERS dictionary.
