# DynamoDB Query and Scan Workflow Notebook

This Jupyter Notebook demonstrates a workflow for dynamically querying and scanning DynamoDB tables. The workflow uses a multi-agent system powered by **LangGraph** and **LangChain** tools, enabling the handling of user queries to interact with DynamoDB.

---

## Features

1. **List Tables**: Retrieve a list of all DynamoDB tables in your AWS account.
2. **Get Table Schema**: Fetch metadata and schema details of a specific DynamoDB table.
3. **Query DynamoDB**: Perform key-based queries to retrieve specific items from a DynamoDB table.
4. **Scan DynamoDB**: Retrieve all items from a table when no specific condition is provided.
5. **Dynamic Decision Making**: Agents intelligently decide which operation to perform based on user input.

---

## Prerequisites

### Software Requirements

- **Python 3.11** (managed using Conda)
- **IAM ROLE with DynamoDB Full Access Attached to EC2 instance**

---

## Environment Setup

### Step 1: Create a Conda Environment for Python 3.11

1. Open a terminal and run the following command to create a conda environment with Python 3.11:
   ```bash
   conda create -n dynamodb_env python=3.11 -y
   ```

2. Activate the environment:
   ```bash
   conda activate dynamodb_env
   ```

3. Install essential packages for Jupyter:
   ```bash
   conda install -c conda-forge notebook -y
   ```

### Step 2: Install Required Python Libraries

Install the libraries needed for this project:
```bash
pip install langchain langgraph boto3
```

### Step 3: Verify AWS Configuration

Ensure that the AWS CLI is configured with valid credentials:
```bash
aws configure
```

If the AWS CLI is not installed, follow the [AWS CLI installation guide](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html).

---

## Usage

### Running the Notebook

1. Activate the conda environment:
   ```bash
   conda activate dynamodb_env
   ```

2. Launch Jupyter Notebook:
   ```bash
   jupyter notebook dynamodb_workflow.ipynb
   ```

3. Run each cell sequentially in the notebook.

4. Provide input queries:
   - Query with a condition: `"Query the 'Orders' table where 'OrderID' equals '123'"`
   - Scan a table: `"Retrieve all data from the 'Orders' table"`

5. View the results directly in the notebook.

---

## Examples

### **Query Data from DynamoDB**

**Input**:

```plaintext
"Query the 'Orders' table where 'OrderID' equals '123'"
```

**Output**:
```json
{
    "success": True,
    "data": [
        {
            "OrderID": {"S": "123"},
            "CustomerName": {"S": "John Doe"},
            "OrderDate": {"S": "2023-12-01"}
        }
    ]
}
```

---

### **Scan a DynamoDB Table**
**Input**:
```plaintext
"Retrieve all data from the 'Orders' table"
```

**Output**:
```{json}
{
    "success": True,
    "data": [
        {
            "OrderID": {"S": "123"},
            "CustomerName": {"S": "John Doe"},
            "OrderDate": {"S": "2023-12-01"}
        },
        {
            "OrderID": {"S": "124"},
            "CustomerName": {"S": "Jane Smith"},
            "OrderDate": {"S": "2023-12-02"}
        }
    ]
}
```

## Customization

You can extend this notebook to:
- Add more DynamoDB operations (e.g., updates, deletes).
- Integrate with other AWS services.
- Enhance query parsing with NLP for more natural input handling.

---

## License

This project is licensed under the MIT License.
