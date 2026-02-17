# 🚀 Prefect: First Steps Guide

This project is a starter implementation of **Prefect**, a modern workflow orchestration tool, based on the introductory guide by [Oliver Holmes](https://medium.com/@oliver-holmes/prefect-a-guide-to-your-first-steps-58550baf5c3a).

---

## 📋 Project Overview
Prefect allows you to build, schedule, and monitor data pipelines using pure Python. This repository demonstrates the core "building blocks" of a Prefect workflow:
* **Flows:** The primary function that serves as the container for your workflow logic.
* **Tasks:** Discrete units of work (functions) called within a Flow.
* **Observability:** Automatic tracking of successes, failures, and retries.

---

## ⚙️ Installation & Setup

### 1. Prerequisites
Ensure you have Python 3.8+ installed. It is highly recommended to use a virtual environment:

# Create and activate environment
```Bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
```
# Install Prefect
```Bash
pip install -U prefect
```
### 2. Start the Prefect Dashboard
To view your workflows in a web interface, run the following command in your terminal:
```Bash
prefect server start
```
*Access the UI at: [http://127.0.0.1:4200](http://127.0.0.1:4200)*

---

## 🛠️ Running Your First Flow

1. Create a file named `hello_prefect.py`.
2. Add the following code (inspired by the Oliver Holmes guide):

```python
from prefect import task, flow

@task(retries=2, retry_delay_seconds=5)
def get_data():
    return [1, 2, 3, 4, 5]

@task
def process_data(data):
    return [x * 10 for x in data]

@flow(name="My First Prefect Flow")
def main_workflow(user_name: str = "Explorer"):
    print(f"Starting workflow for {user_name}...")
    raw_data = get_data()
    processed_data = process_data(raw_data)
    print(f"Final Result: {processed_data}")

if __name__ == "__main__":
    main_workflow(user_name="Oliver")
```

3. **Execute the flow:**
```Bash
python hello_prefect.py
```
---

## 🔗 References & Resources
* **Original Guide:** [Prefect: A Guide To Your First Steps](https://medium.com/@oliver-holmes/prefect-a-guide-to-your-first-steps-58550baf5c3a) by Oliver Holmes.
* **Official Documentation:** [Prefect Docs](https://docs.prefect.io/)
* **Prefect Cloud:** [App Sign-up](https://app.prefect.cloud/)

---
*Created as a learning exercise for Prefect orchestration.*