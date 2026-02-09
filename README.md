# 🏦 Multi-Agent Banking Assistant (LangGraph + MySQL)

A beginner-friendly **Multi-Agent AI Banking Assistant** built using **LangGraph** and **MySQL**.  
It detects the user’s intent (balance, transfer, statement, loan eligibility) and routes the query to the correct agent.

---

## ✨ Highlights

- ✅ Multi-agent architecture using **LangGraph StateGraph**
- ✅ MySQL-backed banking data (customers + transactions)
- ✅ Agents included:
  - **Balance Agent** → checks account balance
  - **Transfer Agent** → transfers money to another account
  - **Statement Agent** → fetches recent transactions
  - **Loan Agent** → checks loan eligibility
  - **Chat Agent** → fallback for general queries
- ✅ Clean routing based on user query intent

---

## 🧰 Tech Stack

- **Python**
- **LangGraph**
- **MySQL**
- `mysql-connector-python`

---

## 📁 Project Files

```
multiagent.ipynb
```

> The entire project is implemented inside a Jupyter Notebook.

---

## ⚙️ Installation

### 1) Clone the project
```bash
git clone <your-repo-url>
cd <your-repo-folder>
```

### 2) Install dependencies
```bash
pip install mysql-connector-python langgraph
```

---

## 🗄️ Database Setup (MySQL)

### 1) Create Database
```sql
CREATE DATABASE AI;
```

### 2) Create Tables

#### customers table
```sql
CREATE TABLE customers (
    account_no VARCHAR(20) PRIMARY KEY,
    balance INT
);
```

#### transactions table
```sql
CREATE TABLE transactions (
    id INT AUTO_INCREMENT PRIMARY KEY,
    account_no VARCHAR(20),
    amount INT,
    type VARCHAR(20),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### 3) Insert Sample Data (optional)
```sql
INSERT INTO customers(account_no, balance)
VALUES ('1234', 50000);

INSERT INTO transactions(account_no, amount, type)
VALUES ('1234', 1000, 'debit');
```

---

## 🔐 Configure DB Credentials

Inside the notebook, update:

```python
mysql.connector.connect(
    host="localhost",
    user="root",
    password="root",
    database="AI"
)
```

---

## ▶️ Run the Project

Open the notebook:

```bash
jupyter notebook
```

Run:

```
multiagent.ipynb
```

---

## 🧠 How It Works

### 1) User Query
Example:
- `"Check my balance"`
- `"Transfer 5000 to account 1234"`
- `"Show my last transactions"`
- `"What is my loan eligibility?"`

### 2) Intent Routing
The system routes the query to one of these agents:

- `balance_agent`
- `transfer_agent`
- `statement_agent`
- `loan_agent`
- `chat_agent`

### 3) MySQL Execution
Agents connect to MySQL and run the required SQL queries.

---

## 🧪 Sample Test Queries

```python
queries = [
    "Check my balance",
    "Transfer 5000 to account 1234",
    "Show my last transactions",
    "What is my loan eligibility?"
]
```

---

## 📌 Example Output

```
Query: Check my balance
Intent: BALANCE_AGENT
Result: Your current balance is ₹50000
```

---

## 🚀 Future Improvements

- Add proper NLP intent detection (LLM-based)
- Add authentication + user sessions
- Add transfer validations (minimum balance, invalid account, etc.)
- Add transaction categories + monthly summaries
- Convert notebook into a Python package / FastAPI app

---

## 👨‍💻 Author

**Vignesh P**  
Multi-Agent AI project using **LangGraph + MySQL**
