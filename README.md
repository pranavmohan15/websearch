## Web Search using DuckDuckGo API

This notebook demonstrates a simple **web search tool** built using Python.  
It sends a query to the DuckDuckGo Instant Answer API and returns a short summary of the topic.

### Features
- Simple web search function
- Uses DuckDuckGo public API
- Returns summarized information
- Can be integrated with AI agents or LLM workflows

### Requirements

Install the required libraries:

```bash
pip install requests python-dotenv openai pydantic
```

### Code

```python
from openai import OpenAI
from pydantic import BaseModel, Field
from typing import List
import requests
import asyncio
from dotenv import load_dotenv

# Load environment variables
load_dotenv()

# Create OpenAI client
client = OpenAI()

def web_search(query: str):
    url = "https://api.duckduckgo.com/"
    
    params = {
        "q": query,
        "format": "json"
    }

    response = requests.get(url, params=params)
    data = response.json()

    abstract = data.get("Abstract", "No detailed information found")
    return abstract


# Example usage
result = web_search("what is indian history")
print(result)
```

### Example Output

```
Anatomically modern humans first arrived on the Indian subcontinent between 73,000 and 55,000 years ago...
```

### Use Case

This tool can be used as:

- A **web search tool for AI agents**
- A **data source for RAG pipelines**
- A **custom tool inside LLM applications**
