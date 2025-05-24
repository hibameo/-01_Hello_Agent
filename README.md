# -01_Hello_Agent

GIAIC_FIRST_ASSIGMENT_01-HELLO-AGENT

🚀 Gemini API with OpenAI-Compatible Agents (Colab Setup)
This project shows how to use Google Gemini API as an OpenAI-compatible model using the openai-agents SDK inside Google Colab.

📦 Requirements
Install the openai-agents library (keep it updated):
!pip install -Uq openai-agents

Also, enable nested asyncio loop in Colab:
import nest_asyncio
nest_asyncio.apply()


🔑 Setup API Key
Make sure your Gemini API key is saved in your Colab environment variables using userdata. Example:
from google.colab import userdata
gemini_api_key = userdata.get("GOOGLE_API_KEY_2")
if not gemini_api_key:
    raise ValueError("GEMINI_API_KEY is not set. Please ensure it is defined in your .env file.")

    🤖 Using Gemini with openai-agents
from agents import Agent, Runner, AsyncOpenAI, OpenAIChatCompletionsModel
from agents.run import RunConfig

# Setup Gemini as OpenAI-Compatible Client
external_client = AsyncOpenAI(
    api_key=gemini_api_key,
    base_url="https://generativelanguage.googleapis.com/v1beta/openai/",
)

# Define Model
model = OpenAIChatCompletionsModel(
    model="gemini-2.0-flash",
    openai_client=external_client
)

# Define Config
config = RunConfig(
    model=model,
    model_provider=external_client,
    tracing_disabled=True
)


✅ Summary
openai-agents: Gives you a framework to build advanced LLM agents using OpenAI-compatible APIs.

gemini-2.0-flash: Google Gemini model working like OpenAI via compatible endpoint.

Fully works inside Google Colab, perfect for experiments and learning.



📎 Useful Links

📘 openai-agents GitHub (README)

📚 Gemini API as OpenAI Docs

📦 PyPI Package
