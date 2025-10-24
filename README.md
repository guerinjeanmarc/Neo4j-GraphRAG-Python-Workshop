# Neo4j GraphRAG Python Workshop

A 2-hour hands-on training on building knowledge graphs from complex PDFs and implementing GraphRAG with the Neo4j GraphRAG Python package.

## 📚 Workshop Overview

Learn to build production-ready knowledge graph pipelines:
- **Part 1:** Quick start with SimpleKGPipeline + Text2Cypher GraphRAG
- **Part 2:** Custom extractors for complex PDFs
- **Part 3:** Full pipeline walkthrough (pre-executed)
- **Part 4:** Agentic GraphRAG patterns

## 🎯 Prerequisites

### Required
- Google Colab account (or local Jupyter environment)
- Neo4j database (choose one):
  - [Neo4j Aura Free](https://neo4j.com/cloud/aura-free/) (recommended)
  - [Neo4j Sandbox](https://neo4j.com/sandbox/)
  - [Neo4j Desktop](https://neo4j.com/download/)
- API Keys:
  - **OpenAI API** for Notebook 1 ([get key](https://platform.openai.com/api-keys))
  - **Gemini API** for Notebook 2 ([get key](https://aistudio.google.com/apikey))

### Knowledge Level
- Basic Python programming
- No prior Neo4j or graph database experience required
- LLM/RAG concepts will be introduced

## 🚀 Getting Started

### Option 1: Google Colab (Recommended)

1. Open the first notebook: [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/guerinjeanmarc/Neo4j-GraphRAG-Python-Workshop/blob/main/workshop-notebooks/01_quickstart_text2cypher.ipynb)

2. Set up your credentials:
   - Neo4j connection details (URI, username, password)
   - OpenAI API key

3. Follow along with the instructor!

### Option 2: Local Setup

```bash
# Clone the repository
git clone https://github.com/guerinjeanmarc/Neo4j-GraphRAG-Python-Workshop.git
cd GraphRAG-Workshop

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt  # To be created

# Create .env file with your credentials
cp workshop-notebooks/.env.template workshop-notebooks/.env
# Edit .env with your Neo4j and Gemini credentials

# Launch Jupyter
jupyter notebook workshop-notebooks/
```

## 📓 Workshop Notebooks

| Notebook | Duration | Description | Models | Execution |
|----------|----------|-------------|---------|-----------|
| [01_quickstart_text2cypher.ipynb](workshop-notebooks/01_quickstart_text2cypher.ipynb) | 50 min | Build KG from PDFs + Text2Cypher queries | OpenAI (gpt-4o-mini) | ✅ Hands-on |
| [02_custom_extractors.ipynb](workshop-notebooks/02_custom_extractors.ipynb) | 10 min | Custom Gemini extractor for complex PDFs | Gemini (2.5-flash) | ✅ Hands-on |
| [03_full_pipeline_walkthrough.ipynb](workshop-notebooks/03_full_pipeline_walkthrough.ipynb) | 15 min | Complete multi-document pipeline (pre-loaded data) | Gemini (2.5-flash) | 👀 Demo |
| [04_agentic_graphrag.md](workshop-notebooks/04_agentic_graphrag.md) | 30 min | Agentic patterns with MCP | Claude Desktop | 👀 Demo |

**Note:** Notebooks 3-4 use pre-loaded data from a shared Neo4j Aura instance (credentials provided by instructor).

## 📂 Repository Structure

```
GraphRAG-Workshop/
├── workshop-notebooks/     # Training notebooks (Colab-ready)
│   ├── 01_quickstart_text2cypher.ipynb
│   ├── 02_custom_extractors.ipynb
│   ├── 03_full_pipeline_walkthrough.ipynb
│   └── 04_agentic_graphrag.md
├── workshop-data/          # Sample pharmaceutical PDFs
│   ├── AbbVie Long-Term Guidance and Pipeline Update.pdf
│   ├── BMY-2024-Q1-Results-Investor-Presentation-with-Appendix.pdf
│   ├── JNJ-Pipeline-2Q2024.pdf
│   └── ph-rd-pipeline-2025-07-24-update-20250725.pdf
└── README.md              # This file
```

## 🎓 Learning Outcomes

By the end of this workshop, you'll be able to:

✅ Build knowledge graphs from unstructured documents using the simpleKGpipeline 
✅ Query graphs using Text2Cypher (natural language → Cypher)  
✅ Understand when custom extractors are needed  
✅ Extend to agentic patterns

## 📊 Pharmaceutical Schema

All notebooks use a consistent schema:

**Entities:**
- `Molecule` - Drug compounds
- `Company` - Pharmaceutical companies
- `Target` - Biological targets
- `Disease` - Medical conditions/indications

**Relationships:**
- `(:Molecule)-[:TREATS]->(:Disease)`
- `(:Company)-[:IN_PIPELINE]->(:Molecule)`
- `(:Molecule)-[:TARGETS]->(:Target)`
- `(:Disease)-[:ASSOCIATED]->(:Target)`

## 🔧 Technologies Used

- [Neo4j](https://neo4j.com/) - Graph database
- [Neo4j GraphRAG Python](https://neo4j.com/docs/neo4j-graphrag-python) - Official GraphRAG package
- [Google Gemini](https://ai.google.dev/) - LLM for extraction & generation
- [OpenAI ]
- Python 3.9+
- Jupyter / Google Colab

## 📖 Additional Resources

### Neo4j Resources
- [Neo4j GraphRAG Python Documentation](https://neo4j.com/docs/neo4j-graphrag-python)
- [Neo4j Cypher Manual](https://neo4j.com/docs/cypher-manual/current/)
- [Neo4j GraphAcademy](https://graphacademy.neo4j.com/) - Free courses
- [Neo4j Community](https://community.neo4j.com/)

### GraphRAG & LLM Resources
- [Gemini API Documentation](https://ai.google.dev/docs)
- [LangGraph](https://langchain-ai.github.io/langgraph/) - Agent frameworks
- [Text2Cypher Agent Example](https://github.com/neo4j-field/text2cypher-react-agent-example)

### Tutorials & Blog Posts
- [GraphRAG Python Package Blog](https://neo4j.com/blog/graphrag-python-package/)
- [Knowledge Graphs for RAG](https://neo4j.com/blog/knowledge-graphs-rag-better-context/)

