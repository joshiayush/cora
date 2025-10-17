# C.O.R.A. - Cognitive Orchestrated Reply Assistant

An intelligent email assistant built with LangGraph that helps you manage and respond to emails efficiently.

> Inspired by the [LangChain agents-from-scratch](https://github.com/langchain-ai/agents-from-scratch) repository, which demonstrates building production-ready email agents with human-in-the-loop and memory capabilities.

## Overview

C.O.R.A. (Cognitive Orchestrated Reply Assistant) is an AI-powered email automation system that leverages LangGraph's state machine capabilities to intelligently process, categorize, and draft responses to your emails. By orchestrating cognitive workflows, C.O.R.A. understands context, prioritizes messages, and generates appropriate replies tailored to your communication style.

## Features

- **Email Triage System**: Automatically categorizes and prioritizes incoming emails
- **Intelligent Agent**: Uses LangGraph to orchestrate tool calls for email management
- **Human-in-the-Loop (HITL)**: Review and approve critical actions before execution
- **Long-term Memory**: Learns from user feedback and adapts to preferences over time using LangGraph Store
- **Context-Aware Responses**: Generates replies that understand the full context of email threads
- **Gmail API Integration**: Connect directly to your Gmail account for real email management
- **Evaluation Suite**: Built-in testing with LangSmith for quality assurance
- **Customizable Workflows**: Built on LangGraph's flexible state graph architecture

## Architecture

C.O.R.A. combines multiple components inspired by modern agent design patterns:

1. **Triage Workflow**: Initial email classification and routing
2. **Agent Executor**: LangGraph-based agent that handles email responses with tool calling
3. **Human Approval Layer**: Interrupt points for reviewing sensitive actions (send email, schedule meetings)
4. **Memory System**: Persistent storage for user preferences and learned behaviors
5. **Evaluation Framework**: Automated testing with LLM-as-a-judge and tool call verification

## Installation

```bash
# Clone the repository
git clone https://github.com/joshiayush/cora.git
cd cora

# Ensure you're using Python 3.11 or later
python3 --version

# Recommended: Using uv (faster)
pip install uv
uv sync --extra dev
source .venv/bin/activate

# Alternative: Using pip
python3 -m venv .venv
source .venv/bin/activate
pip install --upgrade pip
pip install -e .
```

## Requirements

- Python 3.11+
- LangGraph
- LangChain
- OpenAI API key
- LangSmith account (for tracing and evaluation)
- Gmail API credentials (optional, for production use)

## Configuration

Create a `.env` file in the root directory:

```bash
# Copy the example file
cp .env.example .env
```

Add your API keys:

```env
LANGSMITH_API_KEY=your_langsmith_api_key
LANGSMITH_TRACING=true
LANGSMITH_PROJECT=cora-email-assistant
OPENAI_API_KEY=your_openai_api_key
```

## Gmail Integration

To connect C.O.R.A. to your Gmail account:

1. Follow the [Gmail Tools README](src/email_assistant/tools/gmail/README.md) for API setup
2. Configure OAuth credentials

## Key Concepts

### Email Triage
The triage step classifies emails into categories (urgent, informational, actionable) before the agent processes them, improving efficiency and accuracy.

### Tool Calling
C.O.R.A. uses various tools through LangGraph's tool calling interface:
- Send email
- Draft reply
- Search emails
- Schedule meeting
- Mark as read/unread

### Human-in-the-Loop
Critical actions trigger interrupt points where humans can review, approve, or modify the agent's proposed actions before execution.

### Memory and Learning
Using LangGraph Store, C.O.R.A. maintains long-term memory of:
- User communication preferences
- Common response patterns
- Contact relationships
- Custom instructions

## Acknowledgments

This project is inspired by and built upon concepts from:
- [LangChain agents-from-scratch](https://github.com/langchain-ai/agents-from-scratch) - The foundational guide for building production-ready email agents
- [LangGraph](https://langchain-ai.github.io/langgraph/) - State machine framework for building agents
- [LangSmith](https://smith.langchain.com/) - Evaluation and tracing platform

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

MIT License - see LICENSE file for details

## Support

For issues and questions, please open an issue on GitHub.

---

**C.O.R.A.** - Making email management cognitively effortless, one orchestrated reply at a time.
