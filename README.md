# 🤖 AI Data Analyst with LangChain & Gemini

An AI-powered data analysis agent built using **LangChain**, **Google Gemini**, and **Pandas** that allows you to interact with datasets using natural language.

This project demonstrates how Large Language Models (LLMs) can automate data exploration, preprocessing, and analysis — using the classic Titanic dataset.

---

## 🚀 Features

* 📊 Natural language interaction with Pandas DataFrames
* 🤖 Powered by Google Gemini (`gemini-2.5-flash`)
* 🔗 Built using LangChain Agents
* 📁 Multi-DataFrame reasoning support
* 🧹 Handles missing values and feature engineering
* ⚡ Quick insights without writing complex queries

---

## 🛠️ Tech Stack

* Python
* Pandas
* LangChain
* Google Generative AI (Gemini)
* LangChain Experimental Agents

---

## 📂 Project Structure

```
.
├── titanic.csv
├── main.py
├── README.md
└── requirements.txt
```

---

## ⚙️ Installation
```

### Install dependencies

```bash
pip install -r requirements.txt
```

Or manually:

```bash
pip install langchain langchain-openai langchain_experimental langchain-google-genai pandas tabulate
```

---

## 🔑 Setup Environment Variables

⚠️ **Important:** Never hardcode API keys in your code.

### Create a `.env` file:

```
GOOGLE_API_KEY=your_api_key_here
```

### Load it in Python:

```python
from dotenv import load_dotenv
load_dotenv()
```

---

## 📊 Usage

### Step 1: Load Dataset

```python
df = pd.read_csv("titanic.csv")
```

### Step 2: Initialize LLM

```python
from langchain_google_genai import ChatGoogleGenerativeAI

llm = ChatGoogleGenerativeAI(
    model="gemini-2.5-flash",
    temperature=1
)
```

### Step 3: Create Agent

```python
from langchain_experimental.agents import create_pandas_dataframe_agent

agent = create_pandas_dataframe_agent(
    llm,
    df,
    verbose=True,
    agent_type="openai-tools",
    allow_dangerous_code=True
)
```

### Step 4: Ask Questions

```python
agent.run("How many rows are there?")
agent.run("Which columns have missing values?")
agent.run("How many passengers have more than 3 siblings?")
```

---

## 🔍 Example Tasks

* Count rows in dataset
* Detect missing values
* Perform feature engineering
* Compare multiple DataFrames
* Generate derived columns

---

## 🧪 Advanced Example

### Handling Missing Values

```python
df1 = df.copy()
df1["age"] = df1["Age"].fillna(df["Age"].mean())
```

### Creating New Feature

```python
df2 = df1.copy()
df2["Age_Multiplied"] = df1["age"] * 2
```

### Multi-DataFrame Agent

```python
agent = create_pandas_dataframe_agent(
    llm,
    [df, df1, df2],
    verbose=True,
    agent_type="openai-tools",
    allow_dangerous_code=True
)
```
## ⭐ Acknowledgements

* LangChain
* Google Gemini AI
* Pandas

---

✨ *Turn your data into conversations with AI!*
