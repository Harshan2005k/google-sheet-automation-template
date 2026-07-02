# 🤖 Chat with a Google Sheet using AI

Interact with your Google Sheets using natural language powered by AI. This workflow enables users to ask questions about spreadsheet data without writing formulas or SQL. The AI agent dynamically retrieves only the required data from Google Sheets through custom tools, making it efficient even for large datasets.

---

## ✨ Features

- 💬 Chat with your Google Sheet using natural language
- 🤖 AI Agent powered by OpenAI
- 📊 Dynamically fetch Google Sheet data
- 🔍 Retrieve column names
- 📄 Fetch individual column values
- 🎯 Filter rows based on user queries
- ⚡ Returns only the required data instead of loading the entire sheet
- 🔧 Modular workflow with reusable sub-workflows

---

## Architecture

The project consists of two workflows.

### Main Workflow

The main workflow handles user conversations.

1. Receives chat messages
2. Sends the request to the AI Agent
3. AI Agent determines which tool to use
4. Calls the appropriate custom tool
5. Returns the final response to the user

Available AI Tools:

- List Column Names
- Get Column Values
- Get Customer Tool (Filter/Search)

---

### Sub Workflow (Custom Tool)

The sub-workflow is responsible for interacting with Google Sheets.

Workflow Steps:

1. Receive request from the AI Agent
2. Read Google Sheet URL
3. Load Google Sheet contents
4. Determine requested operation
5. Execute:
   - Get column names
   - Get column values
   - Filter rows
6. Format response
7. Return data to AI Agent

---

## Workflow Overview

```
User
   │
   ▼
Chat Trigger
   │
   ▼
AI Agent
   │
   ├── List Columns Tool
   ├── Get Column Values Tool
   └── Customer Search Tool
            │
            ▼
     Sub Workflow
            │
            ▼
     Google Sheets
            │
            ▼
     Structured Response
            │
            ▼
        AI Response
```

---

## Example Questions

Users can ask questions like:

- What columns are available?
- Show all customer names.
- Find customers from California.
- Which orders are pending?
- How many customers are in the sheet?
- Show emails for active users.
- List all products with a price greater than 100.
- Find the row where Customer ID is 1023.

---

## Technologies Used

- n8n
- OpenAI Chat Model
- Google Sheets API
- AI Agent
- Custom AI Tools

---

## Project Structure

```
Main Workflow
│
├── Chat Trigger
├── AI Agent
├── OpenAI Chat Model
├── Simple Memory
├── List Columns Tool
├── Get Column Values Tool
└── Customer Search Tool

Sub Workflow
│
├── Execute Workflow Trigger
├── Google Sheet URL
├── Read Google Sheet
├── Operation Router
├── Get Column Names
├── Filter Rows
├── Prepare Output
└── Return Response
```

---

## How It Works

1. User asks a question.
2. The AI Agent understands the intent.
3. Instead of loading the entire spreadsheet, it selects the appropriate custom tool.
4. The tool retrieves only the required information from Google Sheets.
5. The result is formatted and returned as a natural language response.

This approach is significantly more scalable than sending an entire spreadsheet to the language model.

---

## Benefits

- Faster responses
- Lower token usage
- Works with large Google Sheets
- Modular and reusable workflows
- Easy to extend with additional tools
- Better performance compared to loading full spreadsheet data

---

## Prerequisites

Before running the workflow, ensure you have:

- n8n installed
- OpenAI API credentials
- Google Sheets credentials
- Access to the target Google Sheet

---

## Setup

1. Import both workflows into n8n.
2. Configure your OpenAI credentials.
3. Configure your Google Sheets credentials.
4. Update the Google Sheet URL.
5. Activate the workflow.
6. Open the chat interface and start asking questions.

---

## Future Improvements

- Multi-sheet support
- CRUD operations (Create, Update, Delete)
- Sorting and pagination
- Aggregations (Sum, Average, Count)
- Charts and visualizations
- Role-based access
- Support for multiple spreadsheet providers

---

## License

This project is available under the MIT License.

---

## Preview

The project consists of a primary AI Agent workflow that communicates with a reusable Google Sheets sub-workflow, allowing intelligent and efficient querying of spreadsheet data using natural language.
