# Part 4: Agentic GraphRAG with Neo4j

**Format:** Instructor-led demo + resources  
**Goal:** Understand different approaches to building agentic GraphRAG systems and see Text2Cypher in action

---

## 🎯 Overview

In Parts 1-3, we built a knowledge graph from pharmaceutical PDFs. Now we'll explore how to consume this graph using **agentic patterns** that allow AI assistants to autonomously query and reason over our data.

An **agentic GraphRAG system** combines:
- **Graph Database** (Neo4j) - Structured knowledge
- **LLM Agent** - Natural language understanding
- **Tools** - Actions the agent can take (e.g., Text2Cypher queries)
- **Orchestration** - Logic for planning and executing multi-step tasks

---

## 🛠️ Three Approaches to Building Agentic GraphRAG

### 1️⃣ No-Code: Aura Agents (Aura Pro/Business Critical)

**What it is:** Built-in agent creation interface in Neo4j Aura Pro and Business Critical tiers.

**Best for:** Quick prototyping, non-technical users, production-ready deployments

**Features:**
- Visual agent builder
- Pre-configured Text2Cypher tool (other tools are Vector Similarity and Cypher Template)
- Managed infrastructure
- Authentication and access control

**Learn more:** [Neo4j Aura Agents Documentation](https://neo4j.com/developer/genai-ecosystem/aura-agent/)

---

### 2️⃣ Model Context Protocol (MCP) with Claude Desktop

**What it is:** Connect Claude Desktop directly to your Neo4j database using MCP servers.

**Best for:** Interactive exploration, rapid testing, personal workflows

**How it works:**
1. Install [Neo4j MCP](https://github.com/neo4j-contrib/mcp-neo4j/tree/main/servers/mcp-neo4j-cypher) server in Claude Desktop
2. Claude gains access to Text2Cypher tools 
3. Ask complex questions in natural language
4. Claude automatcally access the database and executes Cypher queries in reasoning loop until it has information to answer the question

**MCP Resources:**
- [Neo4j MCP Documentation](https://neo4j.com/developer/genai-ecosystem/model-context-protocol-mcp/)
- Multiple MCP servers available


---

### 3️⃣ Custom Agents: LangGraph + MCP Template

**What it is:** React agent template with customizable tools and workflows.

**Best for:** Production applications, complex workflows, full customization

**Features:**
- React agent architecture (Reasoning + Acting)
- MCP integration for Neo4j tools
- Extensible tool framework
- Full control over agent behavior

**Template Repository:** [text2cypher-react-agent-example](https://github.com/neo4j-field/text2cypher-react-agent-example)


---

## 📥 Download Pre-Built Database

To follow along with the demo, you'll need the pharmaceutical knowledge graph we extracted in Part 3.

### Download the Database Dump

**🔗 [Download Neo4j Dump File](https://drive.google.com/file/d/1Ma9Cvq-COHsQvEBh2kKcLou8OgOcSLLT/view?usp=sharing)**

*File size: ~13 MB | Contains: pharmaceutical pipeline data extracted from the 4 documents*

### Loading the Dump in Neo4j Aura

1. **Create a new Aura instance** (Free or Pro)
2. Download the `.dump` file (link above)
3. In your Aura console:
   - Click the three dots (•••) next to your instance
   - Select "Backup & restore"
   - Select "Restore from backup file"
   - Upload the `pharmaceutical-graph.dump` file
   - Wait for import to complete (~2-5 minutes)
4. **Connect** using the provided credentials

**Credentials for Demo Instance:**
- URI: `neo4j+s://your-instance.databases.neo4j.io`
- Username: `neo4j`
- Password: `(will be provided during workshop)`

---

## 🎬 Live Demo: Claude Desktop + MCP

In this demo, we'll use **Approach #2** (MCP with Claude Desktop) to query the pharmaceutical knowledge graph.

### Setup Steps (Instructor)
Follow the steps to [install a local MCP server in Claude Desktop](https://github.com/neo4j-contrib/mcp-neo4j/tree/main/servers/mcp-neo4j-cypher#-usage-with-claude-desktop)

### What We'll Query

Using the knowledge graph from Part 3 (pharmaceutical pipeline data), we'll demonstrate various query patterns:

---

## 💡 Example Queries to Try

### Basic Queries

```markdown
Which companies have the most molecules for oncology?
```

```markdown
What molecules are targeting PD-1 or PD-L1 across all companies?
```

```markdown
How many molecules are targeting KRASG12C, and which diseases are they treating?
```

```markdown
What are the most common targets for Alzheimer's Disease therapies?
```

### Competitive Intelligence

```markdown
Analyze our oncology pipeline versus competitors: compare target diversity, 
clinical phase distribution, and trial completion timelines—where are we 
strongest and weakest?
```

```markdown
Which disease indications have multiple of our molecules competing internally, 
and what are the differentiation factors (target, phase, trial design, endpoints)?
```

```markdown
Identify novel target-disease associations that only one or two companies are 
exploring—what is the scientific rationale and probability of technical success?
```

### Strategic Analysis

```markdown
Map the relationship network: which targets are associated with which diseases, 
and which molecules target multiple related pathways—are there synergistic 
combination opportunities?
```

```markdown
Identify orphan targets (high-value diseases with few molecules in development)—
which companies have early-stage programs that could be acquisition targets?
```

```markdown
Analyze the partnership networks: which companies frequently collaborate with 
each other, and on what types of assets (target class, indication, phase)?
```

```markdown
What molecules in our pipeline are being developed in partnership?
```

---

## 🔍 What Makes This "Agentic"?

Notice how these queries require:

1. **Planning** - Breaking complex questions into sub-queries
2. **Tool Use** - Converting natural language → Cypher → Results
3. **Reasoning** - Synthesizing data from multiple queries
4. **Domain Knowledge** - Understanding pharmaceutical terminology and relationships

The agent (Claude) autonomously:
- Generates Cypher queries
- Executes them via the MCP tool
- Analyzes results
- Formulates follow-up queries if needed
- Provides natural language answers


---

## 📚 Additional Resources

### Neo4j Ecosystem
- [GraphRAG Python Documentation](https://neo4j.com/docs/neo4j-graphrag-python)
- [Neo4j GenAI Ecosystem](https://neo4j.com/developer/genai-ecosystem/)
- [Neo4j Developer Guides](https://neo4j.com/developer/)

### Agent Frameworks
- [LangGraph Documentation](https://langchain-ai.github.io/langgraph/)
- [LangChain Neo4j Integration](https://python.langchain.com/docs/integrations/providers/neo4j)
- [Model Context Protocol (MCP)](https://modelcontextprotocol.io/)

### Community & Support
- [Neo4j Community Forum](https://community.neo4j.com/)
- [Neo4j Discord](https://discord.gg/neo4j)
- [GraphAcademy (Free Courses)](https://graphacademy.neo4j.com/)

---

## 🎓 Next Steps for Your Learning Journey

### Beginner (You are here! ✅)
- ✅ Built your first knowledge graph
- ✅ Queried with Text2Cypher
- ✅ Understood agentic patterns

### Intermediate
- **Expand your schema** - Add more entity types and relationships
- **Optimize retrieval** - Tune Text2Cypher prompts and examples
- **Add vector search** - Combine graph + semantic search
- **Deploy to production** - Use Aura Pro or containerized deployments

### Advanced
- **Multi-modal extraction** - Process images, tables, charts from PDFs
- **Entity resolution** - Advanced deduplication and linking
- **Graph algorithms** - PageRank, community detection, path finding
- **Complex agents** - Multi-tool workflows, human-in-the-loop validation
- **RAG evaluation** - Measure accuracy, relevance, faithfulness

---

## 💪 Challenge Projects

Try building these on your own:

1. **Personal Knowledge Base**
   - Extract from your own documents (papers, notes, emails)
   - Build a graph of concepts, people, projects
   - Query with natural language

2. **Industry-Specific GraphRAG**
   - Financial reports → Company/Product/Market graph
   - Legal documents → Case/Statute/Precedent graph
   - Scientific papers → Research/Author/Citation graph

3. **Multi-Source Integration**
   - Combine PDFs, APIs, and databases
   - Build unified knowledge graph
   - Agent with multiple tool types

---

## 🙏 Thank You!

You now have:
- ✅ Working knowledge graphs from PDFs
- ✅ Understanding of extraction strategies
- ✅ Text2Cypher query skills
- ✅ Agentic GraphRAG concepts
- ✅ Templates for building your own systems

**Questions?** Feel free to reach out via:
- Workshop Discord/Slack channel
- Neo4j Community Forum
- GitHub Issues on the workshop repository

---

## 📦 Workshop Repository

All workshop materials available at:
```
[YOUR-GITHUB-USERNAME]/neo4j-graphrag-workshop
```

Contents:
- 📓 All workshop notebooks (1-3)
- 📄 Sample pharmaceutical PDFs
- 📋 Setup instructions
- 🔗 This agentic GraphRAG guide
- 💡 Additional examples and tips

**Star the repo** to get updates and show your support!

---

**Happy Graph Building! 🚀**

---

*Last Updated: October 2025*  
*Part of: Neo4j GraphRAG Python Training Workshop*