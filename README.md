# openrouterap-keykodlar-
openrouter da apı key kodları

!pip install openai
from openai import OpenAI
import os 
from openai import OpenAI
from os import getenv

os.environ["OPENROUTER_API_KEY"] = "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"

client = OpenAI(
  base_url="https://openrouter.ai/api/v1",
  api_key=getenv("OPENROUTER_API_KEY"),
)

completion = client.chat.completions.create(
  extra_headers={
    "HTTP-Referer": "$YOUR_SITE_URL", # Optional, for including your app on openrouter.ai rankings.
    "X-Title": "$YOUR_APP_NAME", # Optional. Shows in rankings on openrouter.ai.
  },
  model="meta-llama/llama-3.1-70b-instruct:free",
  messages=[
    {
      "role": "user",
      "content": "What is the meaning of life?"
    }
  ]
)
print(completion.choices[0].message.content)
