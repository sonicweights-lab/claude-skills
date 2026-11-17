# AI engineer: a 3-month starter plan (week by week)

A study plan for your **first 3 months** towards becoming an AI engineer in 2027: 12 weeks, 9 skills, 3 projects. It is a plan, not a job guarantee. The order of the months is our judgment about what to build first (the skills most asked for in AI engineer job postings are LLMs, agents and RAG: [InterviewStack analysis of 4,155 postings, June 2026](https://interviewstack.io/blog/how-ai-is-changing-ai-engineer-2026); a vendor blog, so treat it as a rough guide).

**How to use it**
- Plan for about 10 to 12 hours a week (an assumption; scale the weeks up or down).
- Each week has one goal, things to learn, one thing to build and a checkpoint. Build in public: keep everything in one GitHub repo per project, with a README.
- Every link below loaded without a login when we checked on 18 November 2026. Some tutorials call paid model APIs (small cost); some course platforms sell certificates. Links and pages change, so re-check them.

| Month | Skills | Project |
|---|---|---|
| 1 | Python, LLM API, prompts | A chatbot that returns structured answers |
| 2 | RAG, tools, agents | An agent that answers from your own documents |
| 3 | Evals, deploy, monitoring | Your app live, with tests |

---

## Month 1: Python, LLM API, prompts

### Week 1: Python you will actually use
- **Goal:** read and write small Python programs comfortably (functions, files, JSON, virtual environments, git).
- **Learn:** [The Python Tutorial](https://docs.python.org/3/tutorial/) (official) or [CS50's Introduction to Programming with Python](https://cs50.harvard.edu/python/).
- **Build:** a command-line tool that reads a JSON file and prints a summary.
- **Checkpoint:** the tool is on GitHub with a README and a one-line install note.

### Week 2: your first LLM API calls
- **Goal:** call a model from code, set its parameters, and stream a reply.
- **Learn:** [Anthropic API fundamentals](https://github.com/anthropics/courses) (course 1 of 5 in that repo) and the [Claude API docs](https://platform.claude.com/docs/en/home). The [OpenAI API docs](https://developers.openai.com/api/docs) cover the same ideas for another provider. Keep your API key in an environment variable, never in code.
- **Build:** a script that takes a question and prints the answer as it streams.
- **Checkpoint:** you can explain tokens, temperature and why a response streams.

### Week 3: prompts and structured output
- **Goal:** get answers in a fixed format you can trust in code.
- **Learn:** the [prompt engineering interactive tutorial](https://github.com/anthropics/courses) (course 2) and [Prompt Engineering Guide](https://www.promptingguide.ai/); [Pydantic](https://docs.pydantic.dev/latest/) to validate the output.
- **Build:** the start of your Month 1 project: a chatbot that returns JSON validated against a schema.
- **Checkpoint:** five test inputs, five valid outputs. Write down the two that failed first and why.

### Week 4: finish and show Project 1
- **Goal:** turn it into something a stranger can run.
- **Do:** handle errors and retries, add 5 to 10 small tests, write the README, record a 60-second demo.
- **Resume line:** "Built a chatbot that returns schema-validated answers using an LLM API (Python, Pydantic); N tests."
- **Checkpoint:** a friend runs it from your README without asking you anything.

---

## Month 2: RAG, tools, agents

### Week 5: embeddings and search
- **Goal:** understand how text becomes vectors and how search over vectors works.
- **Learn:** [Sentence Transformers](https://www.sbert.net/), [Chroma docs](https://docs.trychroma.com/docs/overview/introduction), [Pinecone Learning Center](https://www.pinecone.io/learn/); for the bigger picture, the [Hugging Face LLM course](https://huggingface.co/learn/llm-course/chapter1/1).
- **Build:** embed about 50 short documents and return the 3 closest to a question.
- **Checkpoint:** you can say why a "close" document is not always the right one.

### Week 6: a RAG pipeline
- **Goal:** the model answers from your documents, with the source named.
- **Learn:** chunking, retrieval and prompting with context, using [LlamaIndex](https://developers.llamaindex.ai/python/framework/) or your own code; the [Claude cookbooks](https://github.com/anthropics/claude-cookbooks) and [OpenAI cookbook](https://github.com/openai/openai-cookbook) have worked examples.
- **Build:** question answering over your own notes or PDFs.
- **Checkpoint:** every answer shows which document it came from.

### Week 7: tools
- **Goal:** let the model call functions (search, calculator, your own API).
- **Learn:** the [tool use course](https://github.com/anthropics/courses/tree/master/tool_use) and the [Model Context Protocol docs](https://modelcontextprotocol.io/docs/2026-07-28/getting-started/intro) for the standard way to expose tools.
- **Build:** add two tools to your RAG app.
- **Checkpoint:** log each tool call and its result so you can read what the model did.

### Week 8: agents, and finish Project 2
- **Goal:** a model that decides which step to take next, with limits.
- **Learn:** [Building effective AI agents](https://www.anthropic.com/research/building-effective-agents) (start simple: most tasks do not need a complex agent), the [Hugging Face Agents Course](https://huggingface.co/learn/agents-course/unit0/introduction) and [LangGraph](https://langchain-ai.github.io/langgraph/).
- **Build:** the Project 2 agent: it answers from your documents, uses its tools, and stops after a step limit.
- **Resume line:** "Built a RAG agent with tool use over N documents; step limit, source citations, logged tool calls."
- **Checkpoint:** a 60-second demo and a README that lists what the agent cannot do.

---

## Month 3: evals, deploy, monitoring

### Week 9: evals (the part most beginners skip)
- **Goal:** measure whether your app works instead of guessing.
- **Learn:** [Your AI Product Needs Evals](https://hamel.dev/blog/posts/evals/), the [prompt evaluations course](https://github.com/anthropics/courses/tree/master/prompt_evaluations) and the [Ragas docs](https://docs.ragas.io/en/stable/).
- **Build:** a golden set for your Project 2: about 30 questions, each with the right answer and the source document, and at least 5 questions that have no answer ("I don't know" is the right reply). Score retrieval (is the right document in the top results?) and the answer (does it only use the documents?).
- **Checkpoint:** one table with your first scores. Scores depend on the judge model and settings, so compare runs only under the same setup.

### Week 10: improve using the numbers
- **Goal:** change one thing at a time and see if the table improves.
- **Do:** try a different chunk size, a different prompt, a different number of retrieved documents. Keep every run in a table.
- **Checkpoint:** a short write-up: what you changed, what moved, what got worse.

### Week 11: deploy
- **Goal:** your app runs somewhere other than your laptop.
- **Learn:** [FastAPI tutorial](https://fastapi.tiangolo.com/tutorial/) and [Docker get started](https://docs.docker.com/get-started/).
- **Build:** an API endpoint for your app and a Dockerfile; deploy the container to a host of your choice (check the host's current pricing and limits yourself).
- **Checkpoint:** someone else can call your live URL.

### Week 12: monitoring, and finish Project 3
- **Goal:** know what your live app is doing and what it costs.
- **Learn:** [Langfuse docs](https://langfuse.com/docs) and [OpenTelemetry docs](https://opentelemetry.io/docs/) for tracing; log latency, errors and token cost per request.
- **Build:** add tracing and a small dashboard or log summary; write the case study README (problem, design, eval table, what you would improve).
- **Resume line:** "Deployed a RAG agent (FastAPI, Docker) with an evaluation set of N questions: retrieval X, faithfulness Y; tracing and cost logging."
- **Checkpoint:** your three projects are pinned on your GitHub, each with a README and a demo.

---

## After the 12 weeks
- Practise explaining each project out loud in 30 seconds: what it does, one design choice, one thing you measured.
- For interview practice on AI topics, follow the Interview series at @sonicweights.
- Re-check this plan every month: tools, courses and links change fast.

*Made by @sonicweights. A study plan, not career, financial or job-placement advice. Check each resource's current terms and pricing.*
