<h2>Mykyta Paliienko</h2>

<p>
<b>Junior ML Engineer</b> · 2nd-year Computer Science student, University of Winchester<br>
I build ML systems end to end — data, a baseline, a model, a held-out evaluation and a feedback loop — and ship them
as real software: a voice assistant with its own wake-word model, a from-scratch language model for causal
inference, an OCR app in production. Before ML: three years of Unity games and Telegram bots.
</p>

<p>
<a href="mailto:mykyta.p.work@gmail.com"><img src="https://img.shields.io/badge/mykyta.p.work@gmail.com-111111?style=flat-square&logo=gmail&logoColor=white" alt="Email"></a>
<a href="https://www.linkedin.com/in/mykytapaliienko"><img src="https://img.shields.io/badge/LinkedIn-111111?style=flat-square&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<img src="https://img.shields.io/badge/Remote--first_·_open_to_office-111111?style=flat-square" alt="Remote-first, open to office">
<img src="https://img.shields.io/badge/Open_to_junior_%2F_intern_roles-111111?style=flat-square" alt="Open to junior / intern roles">
<img src="https://img.shields.io/badge/Seeking_ML_%2F_Applied_Science_placement_2027-111111?style=flat-square" alt="Seeking an ML / Applied Science placement, 2027">
</p>

### Projects

**[AI For Me](https://github.com/KernerlRace/Ai-For-Me)** &nbsp;`in progress · flagship`<br>
A personal AI layer for my Windows machine, built as small ML systems on a shared event bus. A 60k-parameter
wake-word CNN trained from scratch on my recordings, with hard-negative mining and synthetic whispers (92% on a
separate test session, 0 false accepts in 22 min of held-out audio); Whisper on the GPU; a multilingual intent
classifier (92.4% held out, 90.0% through speech vs 85.9% for TF-IDF); an active-learning loop that ranks commands
by uncertainty for labelling and retrains behind a gate; a mode autopilot; a vision agent grounding commands on
screenshots, with a dataset labelled for free by UI Automation: Qwen2.5-VL 7B finds the right element for 62.7% of
59 commands in my own words, where UI Automation finds 0%.<br>
<sub>Python · PyTorch · ONNX Runtime · faster-whisper · sentence-transformers · scikit-learn · FastAPI · React · TypeScript · SQLite · GitHub Actions</sub>

<p><img src="https://raw.githubusercontent.com/KernerlRace/Ai-For-Me/main/docs/img/dashboard-commands.png" width="98%" alt="AI For Me: the Commands page — heard commands ranked by uncertainty, labels, accuracy by model version"></p>
<sub>The dashboard is in Russian, the language I speak to the assistant in. It lists the commands it heard, the
least certain first, with one-click labels; the chart tracks accuracy per model version.</sub>

**[RAG with Evals](https://github.com/KernerlRace/rag-evals-service)** &nbsp;`LLM engineering · MLOps`<br>
Question answering over the Python docs, built around its evaluation. A 140-question golden set located in the
source text; BM25 vs dense vs hybrid vs reranker at three chunk sizes with bootstrap CIs and paired tests (hybrid
0.81 hit@5 vs 0.69 for BM25); an LLM judge checked against 60 hand labels with Cohen's κ, so answer accuracy is
reported as an honest range (0.71–0.84). Shipped like a service: pgvector, Docker, a CI gate that fails the build when
retrieval quality drops, a canary on Kubernetes that Prometheus rolled back on p95 latency, and Terraform on AWS
Fargate, applied and destroyed.<br>
<sub>Python · FastAPI · Postgres + pgvector · ONNX Runtime · Ollama · Docker · Kubernetes · Helm · Prometheus · Grafana · Terraform · AWS · GitHub Actions</sub>

**[LLM Inference Bench](https://github.com/KernerlRace/llm-inference-bench)** &nbsp;`inference · cost`<br>
How fast, how good and how cheap is a local LLM on an 8 GB GPU? Qwen2.5 1.5B–7B at three quantizations on
Ollama and llama.cpp: latency, throughput, VRAM, power, perplexity and MMLU, turned into £ per million tokens next to
AWS. Size beats precision (Q8 costs no measurable quality, Q4 about 5%); llama-server's `--kv-unified` doubles
throughput at 2–4 streams, found in the server's own logs and confirmed with an A/B run.<br>
<sub>Python · llama.cpp · Ollama · CUDA · NVML · matplotlib · GitHub Actions</sub>

**VibeWorking** &nbsp;`client project · sole developer · private repo`<br>
A desktop app that reads and files accounting documents — invoices, acts, waybills — for a multi-branch business.
OCR on ONNX Runtime with a Cyrillic model, field extraction (parties, dates, totals, VAT, IBAN and tax-ID checksums),
supplier rules learned from accountants' corrections, and duplicate detection. Documents arrive through
a PyQt6 desktop UI or a Telegram bot. Ships as a Windows installer with signed (ed25519) auto-updates,
stable/beta channels and rollback. ~32k lines of Python, 50 test suites, CI on GitHub Actions, now at v2.5.<br>
<sub>Python · PyQt6 · RapidOCR · ONNX Runtime · SQLite · python-telegram-bot · PyInstaller · GitHub Actions</sub>

<p>
<img src="assets/vibeworking/queue-dark.png" width="49%" alt="VibeWorking: review queue, dark theme">
<img src="assets/vibeworking/history-light.png" width="49%" alt="VibeWorking: document history, light theme">
</p>
<sub>The UI is in Ukrainian, the language of the client's accountants who use it daily. Fictional demo data.</sub>

<details>
<summary>More screenshots</summary>
<p>
<img src="assets/vibeworking/accounting-dark.png" width="49%" alt="VibeWorking: accounting view, dark theme">
<img src="assets/vibeworking/suppliers-light.png" width="49%" alt="VibeWorking: supplier rules, light theme">
</p>
<sub>Screenshots use fictional demo data.</sub>
</details>

**[Causal Method Advisor](https://github.com/KernerlRace/causal-method-advisor)** &nbsp;`ML from scratch` &nbsp;[▶ live demo](https://causal-method-advisor.streamlit.app)<br>
Give it a CSV and a plain-English question — *"Did the campaign raise sales?"* — and it profiles the data,
runs statistical diagnostics and recommends a causal inference method (DiD, synthetic control, IV, RDD, …)
with an explanation. CausalGPT-mini — my own BPE tokenizer and a 34M-parameter GPT-style decoder, pretrained on
Wikipedia and fine-tuned on the task — reads the question and explains the choice while code does the statistics.
On 93 hand-written questions it picks the right method end to end 68% of the time against 58% for a classical-ML
baseline, with calibrated confidence (ECE 0.326 → 0.018) and honest refusals when the data cannot answer.
22 method cards, 18 scenario generators with known ground truth. Next: questions written by other people.<br>
<sub>Python · PyTorch · scikit-learn · statsmodels · pandas · Streamlit</sub>

**[Python Mastery RPG](https://github.com/KernerlRace/python-mastery-rpg)** &nbsp;`hackathon · 48 h` &nbsp;[▶ live demo](https://python-mastery-rpg.streamlit.app)<br>
A gamified platform for learning Python, built at a University of Winchester hackathon:
an in-browser code editor with auto-checked quests, XP and ranks, a leaderboard,
a skills analytics dashboard and an LLM-powered mentor chatbot.<br>
<sub>Python · Streamlit · SQLite · Plotly · OpenAI API</sub>

### Stack

<p>
<img src="https://img.shields.io/badge/Python-111111?style=flat-square&logo=python&logoColor=white" alt="Python">
<img src="https://img.shields.io/badge/C%23-111111?style=flat-square" alt="C#">
<img src="https://img.shields.io/badge/Unity-111111?style=flat-square&logo=unity&logoColor=white" alt="Unity">
<img src="https://img.shields.io/badge/PyTorch-111111?style=flat-square&logo=pytorch&logoColor=white" alt="PyTorch">
<img src="https://img.shields.io/badge/CUDA-111111?style=flat-square&logo=nvidia&logoColor=white" alt="CUDA">
<img src="https://img.shields.io/badge/NumPy-111111?style=flat-square&logo=numpy&logoColor=white" alt="NumPy">
<img src="https://img.shields.io/badge/pandas-111111?style=flat-square&logo=pandas&logoColor=white" alt="pandas">
<img src="https://img.shields.io/badge/scikit--learn-111111?style=flat-square&logo=scikitlearn&logoColor=white" alt="scikit-learn">
<img src="https://img.shields.io/badge/SciPy-111111?style=flat-square&logo=scipy&logoColor=white" alt="SciPy">
<img src="https://img.shields.io/badge/statsmodels-111111?style=flat-square" alt="statsmodels">
<img src="https://img.shields.io/badge/ONNX_Runtime-111111?style=flat-square&logo=onnx&logoColor=white" alt="ONNX Runtime">
<img src="https://img.shields.io/badge/Hugging_Face-111111?style=flat-square&logo=huggingface&logoColor=white" alt="Hugging Face">
<img src="https://img.shields.io/badge/PyQt6-111111?style=flat-square&logo=qt&logoColor=white" alt="PyQt6">
<img src="https://img.shields.io/badge/Streamlit-111111?style=flat-square&logo=streamlit&logoColor=white" alt="Streamlit">
<img src="https://img.shields.io/badge/FastAPI-111111?style=flat-square&logo=fastapi&logoColor=white" alt="FastAPI">
<img src="https://img.shields.io/badge/React-111111?style=flat-square&logo=react&logoColor=white" alt="React">
<img src="https://img.shields.io/badge/TypeScript-111111?style=flat-square&logo=typescript&logoColor=white" alt="TypeScript">
<img src="https://img.shields.io/badge/Whisper-111111?style=flat-square" alt="Whisper">
<img src="https://img.shields.io/badge/Telegram_Bot_API-111111?style=flat-square&logo=telegram&logoColor=white" alt="Telegram Bot API">
<img src="https://img.shields.io/badge/SQLite-111111?style=flat-square&logo=sqlite&logoColor=white" alt="SQLite">
<img src="https://img.shields.io/badge/Plotly-111111?style=flat-square&logo=plotly&logoColor=white" alt="Plotly">
<img src="https://img.shields.io/badge/pytest-111111?style=flat-square&logo=pytest&logoColor=white" alt="pytest">
<img src="https://img.shields.io/badge/PostgreSQL_+_pgvector-111111?style=flat-square&logo=postgresql&logoColor=white" alt="PostgreSQL + pgvector">
<img src="https://img.shields.io/badge/Docker-111111?style=flat-square&logo=docker&logoColor=white" alt="Docker">
<img src="https://img.shields.io/badge/Kubernetes-111111?style=flat-square&logo=kubernetes&logoColor=white" alt="Kubernetes">
<img src="https://img.shields.io/badge/Helm-111111?style=flat-square&logo=helm&logoColor=white" alt="Helm">
<img src="https://img.shields.io/badge/Prometheus-111111?style=flat-square&logo=prometheus&logoColor=white" alt="Prometheus">
<img src="https://img.shields.io/badge/Grafana-111111?style=flat-square&logo=grafana&logoColor=white" alt="Grafana">
<img src="https://img.shields.io/badge/Terraform-111111?style=flat-square&logo=terraform&logoColor=white" alt="Terraform">
<img src="https://img.shields.io/badge/AWS-111111?style=flat-square&logo=amazonwebservices&logoColor=white" alt="AWS">
<img src="https://img.shields.io/badge/llama.cpp-111111?style=flat-square" alt="llama.cpp">
<img src="https://img.shields.io/badge/Ollama-111111?style=flat-square&logo=ollama&logoColor=white" alt="Ollama">
<img src="https://img.shields.io/badge/Git-111111?style=flat-square&logo=git&logoColor=white" alt="Git">
<img src="https://img.shields.io/badge/GitHub_Actions-111111?style=flat-square&logo=githubactions&logoColor=white" alt="GitHub Actions">
<img src="https://img.shields.io/badge/Ruff-111111?style=flat-square&logo=ruff&logoColor=white" alt="Ruff">
</p>

### Education

**University of Winchester** — BSc Computer Science, 2nd year<br>
Relevant coursework: Machine Learning · Artificial Intelligence · Computer Architectures

### Courses

- [x] [CS50x](https://cs50.harvard.edu/x/) — Introduction to Computer Science, Harvard
- [x] [CS50P](https://cs50.harvard.edu/python/) — Introduction to Programming with Python, Harvard
- [x] [CS50AI](https://cs50.harvard.edu/ai/) — Introduction to Artificial Intelligence with Python, Harvard
- [x] [Python Essentials 1 & 2](https://www.netacad.com/) — Cisco Networking Academy
- [x] [Introduction to Data Science](https://www.netacad.com/) — Cisco Networking Academy
- [x] [Neural Networks: Zero to Hero](https://karpathy.ai/zero-to-hero.html) — Andrej Karpathy
- [x] [Hugging Face LLM Course](https://huggingface.co/learn/llm-course) — Hugging Face

### Next: LLM engineering, 2026–27

Weekly notes in [learning-log](https://github.com/KernerlRace/learning-log).


- [ ] [CS336: Language Modeling from Scratch](https://cs336.stanford.edu/) — Stanford
- [ ] [Generative AI with Large Language Models](https://www.coursera.org/learn/generative-ai-with-llms) — DeepLearning.AI & AWS
- [ ] [Finetuning Large Language Models](https://www.deeplearning.ai/short-courses/finetuning-large-language-models/) — DeepLearning.AI
- [ ] [Building and Evaluating Advanced RAG](https://www.deeplearning.ai/short-courses/building-evaluating-advanced-rag/) — DeepLearning.AI
- [ ] [LLM Zoomcamp](https://github.com/DataTalksClub/llm-zoomcamp) — DataTalks.Club
- [ ] [AI Agents Course](https://huggingface.co/learn/agents-course) — Hugging Face
- [ ] [Anthropic courses](https://github.com/anthropics/courses) — prompt engineering and tool use, Anthropic
