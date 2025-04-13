# Assignment5
# 🖼️ FastMCP - Gemini-Powered Desktop Automation Agent

This project is a Gemini-powered desktop automation system that can understand natural language prompts and control Windows applications like MS Paint step-by-step. It demonstrates reasoning-aware task execution using AI and Python automation.

---

## 📌 Project Overview

FastMCP consists of two main scripts:

- **`talknew.py`**: Handles natural language prompting using Google Gemini API. It generates structured reasoning and tool calls.
- **`assignmenteag5.py`**: Receives function calls and executes GUI automation using `pyautogui` to open Paint, draw shapes, and type text.

---

## 🧠 Features & Reasoning Structure

The agent follows these core principles:

- **Explicit Reasoning**: Identifies reasoning type (e.g., spatial or sequential).
- **Step Planning**: Uses `show_reasoning()` to list steps.
- **Internal Self-Checks**: Validates if the plan is logical before execution.
- **Tool Separation**: One function per tool, invoked via structured commands.
- **Conversation Loop**: The Gemini response is piped to a command executor.
- **Fallbacks**: Gracefully handles missing inputs or unclear instructions.

---

## 📂 Folder / Script Structure

```
FastMCP/
├── talknew.py              # Main orchestrator that prompts Gemini and pipes to the executor
├── assignmenteag5.py       # Handles GUI execution of function calls using pyautogui
├── config.py               # Contains Gemini API key
└── README.md               # This file


```

---

## ⚙️ How It Works

1. `talknew.py` sends a detailed task prompt to Gemini.
2. Gemini replies with structured reasoning and tool calls like:
   ```
   FUNCTION_CALL: open_paint|app_name=MS Paint
   FUNCTION_CALL: draw_rectangle|position=center|width=200|height=100
   FUNCTION_CALL: write_text|text=cool|position=center
   FINAL_ANSWER: [task complete]
   ```
3. These lines are piped to `assignmenteag5.py`, which parses and executes them step-by-step.

---

## 🔧 Available Tools

- `open_paint(app_name: str)`
- `draw_rectangle(position: str, width: int, height: int)`
- `write_text(text: str, position: str)`
- `show_reasoning(steps: list)`
- `self_check()`
- `reasoning_type(task_description: str)`

---

## 💻 How to Run It

> ✅ Make sure Python 3.13+ and `pyautogui` are installed.

1. **Set your Gemini API key** in `config.py`:
   ```python
   GEMINI_API_KEY = "your_api_key_here"
   ```

2. **Install dependencies**:
   ```bash
   pip install pyautogui google-generativeai
   ```

3. **Run the main script**:
   ```bash
   python assignmenteag5.py
   python talknew.py
   ```

---

## 🖱️ Example Prompt & Result

```
Prompt: Open MS Paint, draw a rectangle in the center and write the word 'cool' inside.
```

🧠 Gemini responds with reasoning, plans actions, then:
```
FUNCTION_CALL: open_paint|app_name=MS Paint
FUNCTION_CALL: draw_rectangle|position=center|width=200|height=100
FUNCTION_CALL: write_text|text=cool|position=center
FINAL_ANSWER: [task complete]
```
✅ Your computer opens Paint, draws a rectangle, and writes "cool" inside.

---

## 📋 Requirements

- Python 3.13+
- Windows OS
- `pyautogui`
- `google-generativeai`
- `mspaint` installed

---

## 🧪 Notes

- Works best when MS Paint is not already open.
- Timing is handled with `time.sleep()` and `pyautogui.PAUSE`.
- Text clicks happen in the screen center unless specified otherwise.

---


