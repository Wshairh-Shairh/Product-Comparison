PRODUCT COMPARISON ENGINE

AI-powered product comparison API built with FastAPI, Instructor, and
LLM validation pipeline.

This project compares two products (via URL scraping or raw text input)
and returns a guaranteed structured JSON response validated with
Pydantic via Instructor.

FEATURES

-   Compare products via URL or text
-   Dynamic scraping with Playwright
-   HTML cleaning with BeautifulSoup
-   Structured LLM output (Instructor + Pydantic)
-   Feature-by-feature comparison table
-   Final verdict with scoring
-   Generator + Verifier reasoning pipeline
-   Confidence scoring (0–1)
-   Automatic retry if logic validation fails
-   Optional caching (Diskcache)

ARCHITECTURE

1.  Input Layer
    -   Product A (URL or text)
    -   Product B (URL or text)
    -   User preferences
    -   Optional budget
2.  Scraping Layer (if URL)
    -   Playwright loads page
    -   BeautifulSoup removes noise
    -   Extract structured content
3.  LLM Comparison Layer
    -   OpenAI client (Groq or Ollama compatible)
    -   Instructor forces structured JSON output
4.  Validation Pipeline
    -   Generator produces reasoning + comparison
    -   Verifier checks logic and confidence
    -   Retry (max 3 attempts) if validation fails

INSTALLATION

1)  Install dependencies: pip install -r requirements.txt playwright
    install

2)  Create .env file:

    Using Groq: GROQ_API_KEY=your_api_key_here CACHE_DIR=./cache

    Using Ollama: OLLAMA_HOST=http://localhost:11434 CACHE_DIR=./cache

RUN LOCALLY

python main.py

Open: - Swagger UI: http://localhost:8000/docs - Health check:
http://localhost:8000/health

RUN WITH DOCKER

docker compose up –build

API ENDPOINT

POST /compare

Example Request (Text): { “produs_a”: {“sursa”: “iPhone 15: A16, 6GB
RAM”, “este_url”: false}, “produs_b”: {“sursa”: “Galaxy S24: 8GB RAM”,
“este_url”: false}, “preferinte”: “Camera, battery, price” }

HEALTH ENDPOINT

GET /health

LICENSE

Add MIT License if open-source distribution is intended.
