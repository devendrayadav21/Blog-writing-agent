# 📝 Planning-Based AI Research Blog Generation Agent

An autonomous **Agentic AI** system that generates high-quality technical blogs by combining planning, web research, multi-agent content generation, and AI-powered image creation.

Built with **LangGraph**, **LangChain**, **Groq LLMs**, **Tavily Search**, **Gemini Image Generation**, and **Streamlit**.

---

## ✨ Features

- 🤖 Multi-agent workflow using LangGraph
- 🧠 Intelligent routing to determine whether web research is required
- 🔍 Automatic web research using Tavily Search
- 📋 AI-generated blog planning and task decomposition
- 👨‍💻 Parallel section generation using worker agents
- 🖼️ Automatic technical diagram generation using Gemini Image Model
- 📄 Markdown export with embedded images
- 📦 Download complete blog bundle (Markdown + Images)
- 📚 View previously generated blogs
- ⚡ Interactive Streamlit interface

---

## 🏗️ Architecture

```
                    User Topic
                         │
                         ▼
                  Router Agent
                         │
        ┌────────────────┴───────────────┐
        │                                │
 Closed Book                     Research Required
        │                                │
        │                         Tavily Search
        │                                │
        └──────────────┬─────────────────┘
                       ▼
               Planning Agent
                       │
             Creates Blog Outline
                       │
                       ▼
            Parallel Worker Agents
        (One Worker per Blog Section)
                       │
                       ▼
               Merge All Sections
                       │
                       ▼
            Image Planning Agent
                       │
                       ▼
          Gemini Image Generation
                       │
                       ▼
             Final Markdown Blog
```

---

## 🧩 Agent Workflow

### 1. Router Agent

Determines whether the requested topic needs:

- Closed-book generation
- Hybrid generation
- Open-book research

---

### 2. Research Agent

When required:

- Generates optimized search queries
- Searches using Tavily
- Collects relevant evidence
- Filters outdated information
- Removes duplicates

---

### 3. Planning Agent

Creates a structured blog plan including:

- Blog title
- Audience
- Tone
- Blog type
- Tasks
- Word count per section
- Required citations
- Code examples

---

### 4. Worker Agents

Each section is generated independently.

Every worker:

- Receives one task
- Uses research evidence if available
- Adds citations
- Generates code examples when required

Workers execute in parallel for faster generation.

---

### 5. Reducer

Combines all generated sections into a single Markdown document.

---

### 6. Image Planning Agent

Determines:

- Whether images are needed
- Best locations
- Technical prompts
- Image captions
- Alt text

---

### 7. Image Generation Agent

Uses Gemini Image API to generate:

- Architecture diagrams
- Flowcharts
- Technical illustrations

Images are automatically inserted into the Markdown blog.

---

## 🛠 Tech Stack

| Category | Technology |
|----------|------------|
| Agent Framework | LangGraph |
| LLM Framework | LangChain |
| LLM | Groq (Llama 3.3 70B) |
| Search | Tavily Search API |
| Image Generation | Gemini 2.5 Flash Image |
| Frontend | Streamlit |
| Validation | Pydantic |
| Environment | Python |

---

## 📂 Project Structure

```
.
├── bwa_backend.py          # LangGraph backend
├── bwa_frontend.py         # Streamlit UI
├── images/                 # Generated images
├── .env
├── requirements.txt
└── README.md
```

---

## 🚀 Installation

Clone the repository

```bash
git clone https://github.com/yourusername/planning-based-ai-research-blog-generation-agent.git

cd planning-based-ai-research-blog-generation-agent
```

Install dependencies

```bash
pip install -r requirements.txt
```

---

## 🔑 Environment Variables

Create a `.env` file.

```text
GROQ_API_KEY=your_groq_key

TAVILY_API_KEY=your_tavily_key

GOOGLE_API_KEY=your_gemini_key
```

Optional

```text
GROQ_MODEL=llama-3.3-70b-versatile
```

---

## ▶️ Run the Application

```bash
streamlit run bwa_frontend.py
```

---

## 📥 Output

The application generates:

- Complete Markdown blog
- AI-generated technical diagrams
- Downloadable ZIP containing blog and images

Example output:

```
blog.md

images/
    architecture.png
    workflow.png
```

---

## 📸 Application Features

- Topic input
- Blog planning visualization
- Evidence viewer
- Markdown preview
- Generated images
- Download Markdown
- Download ZIP bundle
- View previously generated blogs

---

## Future Improvements

- PDF export
- DOCX export
- Multiple writing styles
- SEO optimization
- Citation formatting (APA/IEEE)
- Multi-language blog generation
- Human-in-the-loop editing
- More image generation providers
- Publishing directly to Medium or WordPress

---

## License

Apache-2.0

---

## Acknowledgements

- LangGraph
- LangChain
- Groq
- Tavily
- Google Gemini
- Streamlit