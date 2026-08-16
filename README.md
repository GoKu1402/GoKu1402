<h1 align="center">Hi, I'm Gollan 👋</h1>
<h3 align="center">
AI / ML Engineer — LLM Systems · Retrieval · Evaluation
</h3>

<p align="center">
I build LLM systems and measure whether they actually work —<br/>
RAG pipelines, agents, evaluation harnesses, and an RLHF loop written from scratch.
</p>

---

## 👨‍💻 About Me

<img align="right" width="330" height="250" src="https://media1.tenor.com/images/9fb771fb621c29b0a2eae945b5ceeeb3/tenor.gif?itemid=19019116">

- 🔭 Currently working on **LLM systems** — retrieval, agentic tool use, and evaluation
- 🧪 I report the experiments that failed alongside the ones that worked
- 🛠️ Full-stack when the problem needs it: **FastAPI · React · PostgreSQL · Redis · Docker**
- 📊 Grounded in **statistics** — EDA, hypothesis testing, A/B testing
- 🧠 I'd rather ship one measured result than five demos
- 📬 Reach me at: **gollankurulkar@gmail.com**

🔗 **LinkedIn:**
<a href="https://www.linkedin.com/in/gollan-kurulkar-928973170/">linkedin.com/in/golan-k</a>

---

## 🧰 Tech

**LLM & ML**

![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?logo=pytorch&logoColor=white)
![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?logo=langchain&logoColor=white)
![LangGraph](https://img.shields.io/badge/LangGraph-1C3C3C?logo=langgraph&logoColor=white)
![FAISS](https://img.shields.io/badge/FAISS-0467DF?logo=meta&logoColor=white)
![Hugging Face](https://img.shields.io/badge/Hugging%20Face-FFD21E?logo=huggingface&logoColor=black)
![MCP](https://img.shields.io/badge/MCP-000000?logo=anthropic&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?logo=scikitlearn&logoColor=white)

**Data**

![pandas](https://img.shields.io/badge/pandas-150458?logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?logo=numpy&logoColor=white)
![SciPy](https://img.shields.io/badge/SciPy-8CAAE6?logo=scipy&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?logo=jupyter&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?logo=postgresql&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?logo=mysql&logoColor=white)
![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?logoColor=black)

**Engineering**

![FastAPI](https://img.shields.io/badge/FastAPI-009688?logo=fastapi&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?logo=react&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?logo=typescript&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?logo=redis&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?logo=git&logoColor=white)

---

## 📂 Projects

### 🔬 [Glass-Box PPO on an LLM](https://github.com/GoKu1402/glassbox-ppo-llm)

PPO/RLHF fine-tuning of GPT-2 with **no `PPOTrainer` and no hidden loop** — rollout, reward
shaping, GAE, the importance ratio, and the clip all written out by hand and printed as
inspectable tensors.

- Five experiments that each state a prediction, turn one dial, and check the result
- Reward hacking made concrete: over-optimize a positive-word reward and coherent text
  collapses into `great great great great`
- Sanity checks that prove the loop is correct — KL is exactly 0 before the first update,
  importance ratio exactly 1 on the first epoch
- Killing the critic cut reward from 15.9 → 6.2 and doubled curve noise

`PyTorch` · `GPT-2` · `PPO` · `RLHF`

---

### 📑 [Financial-Document RAG on FinanceBench](https://github.com/GoKu1402/financebench-rag)

End-to-end RAG over **42 SEC filings**, evaluated across **8 controlled experiments** with an
LLM judge, RAGAS faithfulness, and page-level retrieval metrics. The point isn't "I built a
RAG pipeline" — it's measuring what actually moves the needle.

- **+48% answer correctness** over baseline (0.23 → 0.34) — from prompt policy, not a
  retrieval trick
- Metadata (document-name) filtering lifted **page-hit@1 from 0.21 → 0.29**; scoping the
  search space beat re-scoring it
- Honest negatives: a cross-encoder reranker *hurt* retrieval, and a *stricter* grounding
  prompt *reduced* correctness — over-grounding makes the model refuse answerable questions
- Best chunk size differs per question for **19%** of the eval set

`LangChain` · `FAISS` · `BGE` · `RAGAS` · `BM25 + RRF`

---

### 🤖 [Customer Service Analyst Agent](https://github.com/GoKu1402/customer-service-analyst-agent)

A LangGraph ReAct agent that answers questions about a **26,872-row** support dataset by
calling typed tools over a pandas DataFrame — never from the model's own knowledge.

- Routes queries before acting: structured / unstructured / out-of-scope
- Recovers from its own bad tool arguments mid-loop instead of hallucinating a number
- Persistent memory across restarts plus a distilled user profile
- Same tool layer exposed over **MCP** for any external client

`LangGraph` · `MCP` · `tool calling` · `ReAct`

---

### ⚖️ [LLM-as-a-Judge Evaluation](https://github.com/GoKu1402/llm-judge-evaluation)

Human-vs-judge agreement analysis on 50 generated product descriptions, with a
cross-family setup (Llama 3.3 generates, Gemma 3 judges) so the judge never grades its own
output. Entire pipeline, ~700 judge calls: **about one cent**.

- The judge is **lenient in one direction only** — 67% agreement, and *every* disagreement
  was judge-pass / human-fail. As a quality gate it produces false approvals, never false alarms
- **LLMs cannot count words** (33% agreement on length) — that criterion belongs in code
- Per-criterion judging cost 5× and moved overall agreement by 0

`Nebius` · `Llama 3.3` · `Gemma 3` · `Pydantic structured output`

---

<details>
<summary><b>📊 Earlier data-analysis work</b></summary>

<br/>

- **NYC Taxi Demand & Operations** — EDA and hypothesis testing on large-scale taxi data
  · <a href="https://github.com/GoKu1402/google_certificate_projectss/blob/main/Course_Activity%20EDA%20Automatidata%20project%20lab.ipynb">EDA</a>
  · <a href="https://github.com/GoKu1402/google_certificate_projectss/blob/main/Course_Activity%20ttest%20Automatidata%20project%20lab.ipynb">A/B testing</a>
- **Insurance Cost & Risk Analysis** — cost drivers in customer demographics vs. charges
  · <a href="https://github.com/GoKu1402/unguided_projects/blob/main/insurance.ipynb">Notebook</a>

</details>

---

## 🎯 Open To

**AI / ML Engineer** · **LLM Engineer** · **Data Scientist** — building systems where the
evaluation is as real as the demo.

---

## ♟️ Beyond the Terminal

Chess ♟️ · mobile gaming 📱

---

⭐ *Thanks for stopping by — repos are open, questions welcome.*
