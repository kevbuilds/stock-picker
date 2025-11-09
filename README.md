# 📈 AI Stock Picker# StockPicker Crew



An intelligent multi-agent system that discovers trending companies, conducts financial research, and makes investment recommendations. Built with CrewAI, this project showcases advanced AI orchestration with persistent memory and real-time notifications.Welcome to the StockPicker Crew project, powered by [crewAI](https://crewai.com). This template is designed to help you set up a multi-agent AI system with ease, leveraging the powerful and flexible framework provided by crewAI. Our goal is to enable your agents to collaborate effectively on complex tasks, maximizing their collective intelligence and capabilities.



## 🌟 Features## Installation



- **Multi-Agent Collaboration**: Three specialized AI agents work together:Ensure you have Python >=3.10 <3.13 installed on your system. This project uses [UV](https://docs.astral.sh/uv/) for dependency management and package handling, offering a seamless setup and execution experience.

  - 🔍 **Trending Company Finder**: Discovers companies making headlines

  - 📊 **Financial Researcher**: Analyzes market position and growth potentialFirst, if you haven't already, install uv:

  - 💰 **Investment Advisor**: Makes data-driven investment recommendations

  ```bash

- **Persistent Memory System**: Agents remember past interactions using:pip install uv

  - Long-term memory (SQLite storage)```

  - Short-term memory for context

  - Entity memory for tracking companiesNext, navigate to your project directory and install the dependencies:

  - RAG storage for semantic search

(Optional) Lock the dependencies and install them by using the CLI command:

- **Real-time Notifications**: Get instant push notifications via Pushover when investment recommendations are ready```bash

crewai install

- **Structured Data Output**: Type-safe outputs using Pydantic models with JSON exports```

### Customizing

- **Automated Research**: Web search integration for current market intelligence

**Add your `OPENAI_API_KEY` into the `.env` file**

## 🏗️ Architecture

- Modify `src/stock_picker/config/agents.yaml` to define your agents

```- Modify `src/stock_picker/config/tasks.yaml` to define your tasks

stock_picker/- Modify `src/stock_picker/crew.py` to add your own logic, tools and specific args

├── config/- Modify `src/stock_picker/main.py` to add custom inputs for your agents and tasks

│   ├── agents.yaml        # Agent definitions (roles, goals, backstories)

│   └── tasks.yaml         # Task definitions and workflows## Running the Project

├── tools/

│   └── push_tool.py       # Pushover notification integrationTo kickstart your crew of AI agents and begin task execution, run this from the root folder of your project:

├── memory/                # Persistent agent memory (auto-generated)

├── output/                # Generated reports and decisions```bash

│   ├── decision.md$ crewai run

│   ├── research_report.json```

│   └── trending_companies.json

└── crew.py                # Multi-agent orchestrationThis command initializes the stock_picker Crew, assembling the agents and assigning them tasks as defined in your configuration.

```

This example, unmodified, will run the create a `report.md` file with the output of a research on LLMs in the root folder.

## 🚀 Quick Start

## Understanding Your Crew

### Prerequisites

The stock_picker Crew is composed of multiple AI agents, each with unique roles, goals, and tools. These agents collaborate on a series of tasks, defined in `config/tasks.yaml`, leveraging their collective skills to achieve complex objectives. The `config/agents.yaml` file outlines the capabilities and configurations of each agent in your crew.

- Python 3.10 - 3.12

- OpenAI API key## Support

- Serper API key (for web search)

- Pushover account (optional, for notifications)For support, questions, or feedback regarding the StockPicker Crew or crewAI.

- Visit our [documentation](https://docs.crewai.com)

### Installation- Reach out to us through our [GitHub repository](https://github.com/joaomdmoura/crewai)

- [Join our Discord](https://discord.com/invite/X4JWnZnxPb)

1. **Clone the repository**- [Chat with our docs](https://chatg.pt/DWjSBZn)

```bash

git clone https://github.com/kevbuilds/stock-picker.gitLet's create wonders together with the power and simplicity of crewAI.

cd stock-picker
```

2. **Install dependencies**
```bash
pip install uv
crewai install
```

Or use pip directly:
```bash
pip install -r requirements.txt
```

3. **Configure environment**
```bash
cp .env.example .env
# Edit .env and add your API keys:
# OPENAI_API_KEY=your_key_here
# SERPER_API_KEY=your_key_here
# PUSHOVER_USER=your_user_key (optional)
# PUSHOVER_TOKEN=your_token (optional)
```

### Usage

**Run the stock picker**
```bash
crewai run
```

The system will:
1. 🔍 Search for trending companies in the news
2. 📊 Research each company's market position and outlook
3. 💡 Analyze investment potential
4. ✅ Select the best investment opportunity
5. 📱 Send a push notification (if configured)

### Sample Output

The crew generates multiple output files:

**`output/trending_companies.json`**
```json
{
  "companies": [
    {
      "name": "LumeCube",
      "ticker": "LUME",
      "reason": "Leading portable lighting solutions for content creators"
    }
  ]
}
```

**`output/decision.md`**
```markdown
The chosen company for investment is LumeCube. Their robust market 
position as a leader in portable lighting solutions for content creators, 
coupled with strategic innovations and direct-to-consumer strategies, 
sets them up for significant growth...
```

**Push Notification**
> "Investment in LumeCube is recommended: As a leader in portable lighting 
> solutions for content creators, LumeCube shows high growth potential..."

## 🛠️ Customization

### Modify Agent Behavior

Edit `config/agents.yaml`:
```yaml
trending_company_finder:
  role: Trending Company Finder
  goal: >
    Find companies that are trending in the news and attracting attention...
  backstory: >
    You're an expert at identifying emerging companies...
```

### Modify Task Workflow

Edit `config/tasks.yaml`:
```yaml
find_trending_companies:
  description: >
    Search the internet to find companies that are trending...
  expected_output: >
    A JSON list of 3-5 companies with name, ticker, and reason...
```

### Add Custom Tools

The project includes a Pushover notification tool. Add your own in `tools/`:

```python
from crewai.tools import BaseTool
from pydantic import BaseModel, Field

class MyCustomTool(BaseTool):
    name: str = "My Tool Name"
    description: str = "What it does"
    
    def _run(self, argument: str) -> str:
        # Your tool logic
        return result
```

## 🧠 Memory System

The stock picker uses CrewAI's advanced memory features:

- **Long-term Memory**: Persists across sessions in `memory/chroma.sqlite3`
- **Short-term Memory**: Maintains context during execution
- **Entity Memory**: Tracks companies and their attributes
- **RAG Storage**: Semantic search over past research

This allows agents to:
- Remember previously analyzed companies
- Build on past research
- Avoid duplicate work
- Make more informed decisions over time

## 🔧 Technical Stack

- **CrewAI**: Multi-agent orchestration framework
- **Pydantic**: Type-safe data validation
- **OpenAI GPT-4**: Language model for analysis
- **Serper API**: Real-time web search
- **Pushover**: Push notification delivery
- **SQLite + ChromaDB**: Persistent memory storage
- **Python 3.11**: Core runtime

## 📁 Project Structure

```
stock-picker/
├── .env.example              # Environment template
├── .gitignore               # Git exclusions (protects .env)
├── pyproject.toml           # Project dependencies
├── requirements.txt         # Pip requirements
├── README.md                # This file
├── knowledge/               # Knowledge base
│   └── user_preference.txt
├── memory/                  # Agent memory (auto-generated)
│   └── chroma.sqlite3
├── output/                  # Generated reports
│   ├── decision.md
│   ├── research_report.json
│   └── trending_companies.json
└── src/
    └── stock_picker/
        ├── __init__.py
        ├── main.py          # Entry point
        ├── crew.py          # Crew orchestration
        ├── config/          # Configuration
        │   ├── agents.yaml
        │   └── tasks.yaml
        └── tools/           # Custom tools
            ├── __init__.py
            └── push_tool.py
```

## 🔐 Security Notes

- Never commit `.env` files with real API keys
- Use `.env.example` as a template
- Memory databases are excluded from git
- All credentials use environment variables

## 📊 Output Files

| File | Description |
|------|-------------|
| `output/trending_companies.json` | List of companies discovered in news |
| `output/research_report.json` | Detailed research on each company |
| `output/decision.md` | Final investment recommendation |

## 🔔 Push Notifications

To enable push notifications:

1. Sign up at [Pushover.net](https://pushover.net/)
2. Create an application to get your token
3. Add credentials to `.env`:
   ```
   PUSHOVER_USER=your_user_key
   PUSHOVER_TOKEN=your_app_token
   ```

Notifications are sent when the final investment decision is made!

## 🚧 Future Enhancements

- [ ] Add support for custom stock universes (tech, healthcare, etc.)
- [ ] Integrate real-time stock price data APIs
- [ ] Generate PDF investment reports
- [ ] Add visualization of company comparisons
- [ ] Support for portfolio management
- [ ] Backtesting investment recommendations
- [ ] Email delivery option alongside push notifications
- [ ] Scheduled daily/weekly runs

## 🤝 Contributing

Contributions welcome! Please feel free to submit a Pull Request.

### Development Setup

```bash
# Install development dependencies
pip install -e ".[dev]"

# Run tests (if available)
pytest

# Format code
black src/
```

## 📝 License

MIT License - See [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Built with [CrewAI](https://crewai.com)
- Powered by [OpenAI](https://openai.com)
- Search via [Serper](https://serper.dev)
- Notifications by [Pushover](https://pushover.net)

## 📧 Contact

Created by Kevin - [GitHub Profile](https://github.com/kevbuilds)

---

**⚠️ Disclaimer**: This tool generates investment analysis for educational and informational purposes only. NOT FINANCIAL ADVICE. Do not make investment decisions based solely on this tool's output. Always conduct your own due diligence and consult with a qualified financial advisor.

**Risk Warning**: Past performance does not guarantee future results. All investments carry risk, including potential loss of principal.
