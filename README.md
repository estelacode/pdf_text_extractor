# PDF Text Extractor

## Overview
A web-based app to extract and parse text from PDFs using PyMuPDF and Llama-Parse.
Interactive PDF upload and text display via Gradio, fully Dockerized for optional deployment.

## Demo
![gradio ui](https://github.com/estelacode/pdf_text_extractor/blob/master/docs/ui%20gradio/gradio_ui.jpg)
![gradio_ui_text_extraction_methods](https://github.com/estelacode/pdf_text_extractor/blob/master/docs/ui%20gradio/gradio_ui_text_extraction_methods.jpg)
![Llama-Parse Output](https://github.com/estelacode/pdf_text_extractor/blob/master/docs/outputs/llamaparse/llamaparse_output.jpg)

## ⚡ Features
`Functionality`
- Extracting text from PDFs using PyMuPDF
- Processing and parsing text with Llama-Parse
- Interactive web interface via Gradio for PDF upload and text display

`Infrastructure / Deployment`
- Dockerized deployment for quick and reproducible setup
- Architecture documentation with high-level, sequence, and flow diagrams

## Architecture
High-level structure of the application:
![High Level Architecture Diagram](docs/diagrams/high_level_architecture_diagram.jpg)

## `Sequence Diagram`
![Sequence Diagram](docs/diagrams/sequence_diagram.png)

### Sequence Flow:
1. User uploads PDF via Frontend.
2. Frontend receives the PDF.
3. Frontend sends the PDF to the Backend for processing.
4. Backend extract text with PyMuPDF from the PDF.
5. Backend processes text with Llama-Parse.
6. Backend returns results to  Frontend.
7. Frontend displays extracted text to user.

## Tech Stack
Backend:![Python](https://img.shields.io/badge/Python-white?style=for-the-badge&logo=python&logoColor=black)![3.13.3](https://img.shields.io/badge/3.13.3-3c64f3?style=for-the-badge&logoColor=white&labelColor=3c64f3&color=3c64f3) ![uv](https://img.shields.io/badge/uv-white?style=for-the-badge&logo=uv&logoColor=black)![0.9.13](https://img.shields.io/badge/0.9.13-3c64f3?style=for-the-badge&logoColor=white&labelColor=3c64f3&color=3c64f3) ![llama-cloud-services](https://img.shields.io/badge/llama--cloud--services-white?style=for-the-badge&logoColor=black)![>=0.6.35](https://img.shields.io/badge/%3E%3D0.6.35-3c64f3?style=for-the-badge&logoColor=white&labelColor=3c64f3&color=3c64f3) ![PyMuPDF](https://img.shields.io/badge/PyMuPDF-white?style=for-the-badge&logoColor=black)![>=1.26.1](https://img.shields.io/badge/%3E%3D1.26.1-3c64f3?style=for-the-badge&logoColor=white&labelColor=3c64f3&color=3c64f3)

Frontend: ![Gradio](https://img.shields.io/badge/Gradio-white?style=for-the-badge&logo=gradio&logoColor=black)![5.34.2](https://img.shields.io/badge/5.34.2-3c64f3?style=for-the-badge&logoColor=white&labelColor=3c64f3&color=3c64f3) 

## Setup
```bash
git clone https://github.com/estelacode/pdf_text_extractor.git
cd pdf_text_extractor

### Create & activate virtual environment
py -3.13 -m venv .venv
source .venv/bin/activate  # Linux/macOS
.venv\Scripts\activate     # Windows

### Install dependencies
uv pip install -e .

### Configure environment
Configure .env file (copy from .env.example)
```

## Usage 
```bash
uv run main.py
# Navigate to http://localhost:7860/
```

## Project Structure
```bash
pdf_text_extractor/
├── .dockerignore        # Files and folders to exclude from Docker builds
├── .env                 # Environment variables (keep secret)
├── .env.example         # Example environment variables
├── .gitignore           # Git ignore rules
├── .python-version      # Python version used in the project
├── .venv/               # Local virtual environment (ignored in git)
├── data/                # Folder for input/output data (PDFs, extracted text, etc.)
├── dist/                # Distribution or build files
├── docs/                # Documentation files
├── main.py              # Entry point of the application
├── notebook/            # Jupyter notebooks for experiments or testing
├── pyproject.toml       # Project dependencies and metadata
├── README.md            # Project README file
├── Dockerfile           # Dockerfile to build the container
├── src/                 # Source code for the project
└── uv.lock              # Dependency lock file for uv
```



## Build the artifact
```bash
uv build
```
## Requirements
```bash
uv pip freeze > requirements.txt
```

## Developer mode
```bash
uv pip install -e . #
uv pip install --editable . # Install the editable package based on the provided local file path.
```

## Devops 
0. Generate the whl file in the dist folder
```bash
uv build
```
1. Build a Docker image with the code and dependencies from my project.
```bash
docker build -t pdf_text_extractor . # build your Docker image
docker images # list docker images
docker rmi <docker_image-id> # remove the docker image with image id (Ex.1bec6217270e)
```
2. Create and run a docker container
```bash
docker run -d -p 8080:8080 pdf_text_extractor
docker ps -a # list all the docker containers
docker rm -f <container-id> #remove the docker container with id (Ex.cf99422731ef)
```
3. Create a docker container with enviroment variables
```bash
docker run -d -p 8080:8080 -e LLAMA_CLOUD_API_KEY="XXXXXXXXXXXXXXXXXXXXXXXXXX" pdf_text_extractor
```




## Tech Stack
* [Gradio](https://www.gradio.app/docs)
* [Docker Desktop Community](https://docs.docker.com/)
* [uv](https://docs.astral.sh/uv/concepts/projects/dependencies/)

#### PDF Procesing Libraries
* [Llama Parse](https://www.llamaindex.ai/llamaparse)
* [Llama Parse-Getting Started](https://developers.llamaindex.ai/python/cloud/llamaparse/getting_started/)
* [PyMuPDF](https://github.com/pymupdf/PyMuPDF)
* [pdfminer.six](https://pypi.org/project/pdfminer.six/)


* [IMAGEBIND: One Embedding Space To Bind Them All](https://arxiv.org/pdf/2305.05665)


### 👋 Author
Estela Madariaga
