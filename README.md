# Multiuser ReAct AI Chatbot

## Overview
This project implements an AI-powered assistant capable of performing multi-functional tasks such as retrieving real-time weather information and conducting advanced web searches. The assistant leverages LangGraph’s ReAct AI agent, which integrates LangChain’s ReAct (Reasoning + Acting) framework with additional tools, APIs, and conversational memory for dynamic, context-aware interactions.

The primary features of this assistant include:

1. **Weather Information Retrieval**: The assistant uses the `get_weather` tool, powered by the WeatherAPI, to fetch real-time weather data for any location specified by the user.
2. **Web Search Capability**: The assistant uses `search_web`, a tool based on Tavily Search, to retrieve relevant, detailed information from the web for user queries, such as current events or general knowledge.
3. **Contextual Conversation Management**: The assistant uses LangGraph’s SQLite-backed memory module to store and retrieve conversation history. This ensures that follow-up questions are context-understood, enabling a smoother user experience.
4. **Tool-Aware Reasoning**: The assistant leverages LangGraph’s ReAct AI framework to decide dynamically which tool to use (e.g., weather vs. web search) based on the user’s query, reasoning through the problem in a structured manner.

This project demonstrates the use of modern conversational AI frameworks to create dynamic, multi-functional assistants that interact with APIs and efficiently manage conversational history.

---

## ReAct AI Agent Key Components
**1. Tools Integration:**

  * TavilySearchResults:
    - Allows the assistant to perform deep, advanced searches on the web.
    - The search_web function uses this tool to process user queries requiring detailed online research.
  * WeatherAPI:
    - The get_weather function integrates the WeatherAPI to fetch weather data based on the user’s query.
    - The agent dynamically invokes these tools when the context demands them.
    
**2. Conversation Memory**: The SQLite-backed memory module ensures that the assistant can:
- Retrieve past conversation threads based on a unique session ID.
- Maintain continuity in dialogue by referring to earlier context or follow-up questions.

**3. Pipeline for Dynamic Thinking:**

  * The ReAct AI agent processes user queries in a step-by-step manner:
    - **Reasoning**: It understands the task (e.g., "What is the weather in London?").
    - **Acting**: It chooses the appropriate tool (get_weather or search_web) to address the query.
    - **Thinking**: It evaluates the tool's response and determines the next step.
    - **Responding**: It returns a comprehensive answer to the user.
---
## End-to-End Workflow
Here’s how the LangGraph ReActAI agent powers the project’s workflow:

#### Step 1: User Query
The user submits a query, such as:

“What’s the weather in San Francisco?”<br>
“What are the latest advancements in quantum computing?”
#### Step 2: Prompt Processing
The ReActAI agent receives the query and the system prompt. It reasons about the task and decides which tool to use:<br>

- For a weather-related query, it calls the get_weather function.
- For a general information query, it invokes the search_web function.
#### Step 3: Tool Execution
- The agent executes the selected tool and retrieves data:
- For weather, it makes an API call to WeatherAPI.
- For web searches, it performs an advanced search using Tavily Search.
#### Step 4: Response Generation
- The agent evaluates the data returned by the tool and generates a user-friendly response.
- If required, it uses the SQLite memory to refer to past conversations for context.
#### Step 5: Context Management
- The SQLite-backed memory ensures continuity by:
- Saving conversation history linked to a session ID.
- Loading past threads when the user interacts again in the same session.
---
## Benefits of Using LangGraph ReActAI
- Dynamic Task Handling: Automatically selects the appropriate tool for the query.
- Context Awareness: Maintains session history for natural, multi-turn conversations.
- Scalable Integration: Easily extendable to include more tools and APIs.
- Efficient Workflows: Combines reasoning, acting, and thinking for seamless interactions.
