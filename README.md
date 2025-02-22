**Flux AI to Python API Integration
**
1. Introduction:

This project allows Flux AI to communicate with a Python FastAPI server, enabling dynamic prompt retrieval for AI processing.

2. Features:
   
Fetches a dynamic prompt from a Python API

Runs a local FastAPI server to serve the prompt

Can be integrated with Flux AI workflows

3. Prerequisites:

Python 3.8+

Flux AI installed and running locally

Basic understanding of APIs

4. Installation:

4.1 Setting Up Python API

Install dependencies:

```pip install fastapi uvicorn requests```

Create an API file (api.py) and add the following code:

``` python
from fastapi import FastAPI
import uvicorn

app = FastAPI()

@app.get("/get_prompt")
async def get_prompt():
    return {"prompt": "This is the prompt from Python API."}

if __name__ == "__main__":
    uvicorn.run(app, host="127.0.0.1", port=8000)
```

Run the API:

```python api.py```

4.2 Making Requests from Flux AI

If Flux AI supports JavaScript, use:
```
fetch("http://127.0.0.1:8000/get_prompt")
    .then(response => response.json())
    .then(data => console.log("Received Prompt:", data.prompt))
    .catch(error => console.error("Error:", error));
```

If Flux AI supports Python:
```
import requests
response = requests.get("http://127.0.0.1:8000/get_prompt")
print(response.json()["prompt"])
```

5. API Reference:

   Endpoint - /get_prompt

   GET - Method
   
   Description - Fetces the generated prompt

7. Tools Used:

   FastAPI: For creating the backend API

   Uvicorn: ASGI server for running FastAPI

   Requests: For making HTTP requests

   Flux AI: The AI system interacting with the API

8. Troubleshooting:

   If the API doesn’t start, check if FastAPI is installed.

   Ensure Flux AI can send requests to 127.0.0.1:8000.

   If facing CORS issues, enable CORS in FastAPI:
```
from fastapi.middleware.cors import CORSMiddleware
app.add_middleware(CORSMiddleware, allow_origins=["*"], allow_methods=["*"], allow_headers=["*"])
```
