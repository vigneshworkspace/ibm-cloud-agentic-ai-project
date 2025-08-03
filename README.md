# Travel Planner AI Agent — IBM Capstone Project README

Welcome to the repository for **Travel Planner AI Agent**, an IBM watsonx–hosted conversational agent that turns complex trip planning into a seamless, personalized experience.

## ✨ Project Overview
The agent leverages real-time search, weather data, and dynamic reasoning to:
* Elicit a traveler’s **destination, dates, budget, and interests**.
* Autonomously craft **day-by-day itineraries** with adaptive scheduling.
* Recommend transport, food, sights, and shopping while monitoring live conditions.
* Re-plan instantly when weather changes or attractions close.

Built with an *agentic* architecture, the bot thinks step-by-step, calls external tools when needed, and updates plans on the fly.

## 🏗️ System Architecture
| Layer | Key Components |
|-------|---------------|
| **Frontend** | watsonx **Agent Lab** chat UI |
| **Agent Core** | Granite-3.3-8B-Instruct LLM + ReAct reasoning loop |
| **Tools** | Google Search, DuckDuckGo Search, Wikipedia Search, Weather API, WebCrawler, Python Interpreter |
| **Hosting** | IBM Cloud (Dallas region) |
| **Orchestration** | LangGraph framework |



## 🛠️ Agent Prompt (excerpt)

> You are a *Travel Planner AI Agent*…  
> Goals: (1) extract user preferences, (2) gather up-to-date info via tools, (3) build optimized daily plans, (4) adapt to weather & closures, (5) ask only necessary follow-ups.  
> When suggesting places, list 3–5 options max. Do **not** make bookings unless asked.

The full prompt lives in `prompts/system_prompt.txt`.

## ⚙️ Development Notes
* **LangGraph ReAct**: Each user turn triggers a think-act-observe loop; the LLM chooses which tool to invoke, parses results, and composes the final reply.
* **Tool wrappers** in `tools/` standardize API access and enforce rate limits.
* **State store** keeps itinerary context and weather forecasts, enabling mid-conversation edits.

## 📈 Evaluation
Model quality is tracked with:
* **User-simulated tests** measuring itinerary relevance (BLEU) and constraint adherence (F1).
* **Human review** scores on usefulness and satisfaction.
* **Latency & token metrics** exported to Prometheus.

## 🔄 CI/CD & Deployment
GitHub Actions:
1. Lint & unit tests
2. Build Docker image
3. Push to IBM Cloud Container Registry
4. Auto-deploy to **watsonx Agent Lab** space via CLI

## 🗺️ Future Roadmap
* Group trip coordination (multi-profile preferences)
* Budget optimization slider
* Long-term user memory for repeat travelers
* Offline PWA interface

## 📄 Licensing
Apache-2.0. See `LICENSE`.

## 🙏 Acknowledgments
Project guided by **Edunet Foundation** and **IBM SkillsBuild** courses on AI and cloud deployment.

Happy travels!

[1] https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/23692078/044d5353-5ea3-4dc3-bc5f-e9d7738540ad/vigneshwarnagenticaiproject.pdf
