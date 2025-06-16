# Weather Chatbot using Gemini 1.5 Flash, LangGraph, and OpenWeatherMap

## 🧠 Project Overview
This project demonstrates how to build a chatbot that provides real-time weather information for any city using OpenWeatherMap API. It integrates Google's Gemini 1.5 Flash model for natural language processing and LangGraph for building structured, stateful workflows.

## ✨Features
- Real-time weather data using OpenWeatherMap  
- Natural language understanding with Gemini 1.5 Flash  
- Workflow orchestration using LangGraph  
- Secure API key handling  

## 🧩 Technologies Used
- `langchain_google_genai`  
- `langchain_community`  
- `langgraph`  
- `langgraph.prebuilt.ToolNode`  
- `pyowm`  
- `getpass`  
- `os`  

## How It Works
1. The script starts by prompting you to enter your Gemini API key and OpenWeatherMap API key. These are stored in environment variables.
2. `AgentState` is a typed dictionary that stores the list of messages exchanged between the user and the agent.
3. The `OpenWeatherMapQueryRun` tool from `langchain_community` connects to OpenWeatherMap and retrieves current weather data.
4. This tool is bound to the Gemini 1.5 Flash model using `bind_tools()`, allowing Gemini to automatically call the tool when needed.
5. The LangGraph workflow includes:
   - **Agent Node**: Gemini processes the user's message and determines if a tool call is needed.
   - **Should Continue Function**: Checks if a tool call was made. If yes, it routes to the tool node; otherwise, it ends.
   - **Tool Node**: Executes the weather tool and returns the result.
6. The graph is compiled and invoked with user input. If the input requires weather data, the tool is called; otherwise, Gemini responds directly.

## Getting Started
1. Clone the repository.
   ```bash
   git clone https://github.com/moni0811/Weather_data_using_LangGraph.git
   cd Weather_data_using_LangGraph
   ```
3. Install dependencies using:
   ```bash
   pip install langchain_community langgraph langchain pyowm langchain_google_genai langgraph-prebuilt
   ```
4. Run the script and enter your Gemini and OpenWeatherMap API keys when prompted.
5. Interact with the chatbot by asking weather-related questions.

## Example
Ask:
```text
What is the temperature in Atlanta?
```

Response:
Gemini will fetch real-time weather data using the OpenWeatherMap tool and respond with the current temperature.
