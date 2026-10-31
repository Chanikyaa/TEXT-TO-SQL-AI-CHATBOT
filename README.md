# Text-to-SQL AI Chatbot

An AI-powered chatbot that converts natural-language questions into SQL queries and executes validated queries against a relational database.

## Overview

The Text-to-SQL AI Chatbot allows users to interact with databases using natural language instead of manually writing SQL statements.

Users can ask questions about database records, and the system generates SQL queries based on the available database schema.

The application includes:
- Natural-language-to-SQL generation
- Database schema inspection
- SQL query validation
- SQLAlchemy database integration
- SQLGlot-based SQL parsing and validation
- SQLite and PostgreSQL support
- FastAPI backend
- Streamlit user interface

## Features

- **Natural Language Interface:** Ask database questions using everyday language.
- **Schema Awareness:** Use database table and column information during SQL generation.
- **SQL Generation:** Convert user questions into SQL queries.
- **Query Validation:** Validate generated SQL before execution.
- **Read-Only Query Support:** Restrict execution to SELECT queries.
- **Database Integration:** Connect to SQLite and PostgreSQL databases.
- **Interactive UI:** Use a Streamlit-based chatbot interface.
- **API Support:** Access functionality through FastAPI endpoints.

## Architecture

```text
User Question
      |
      v
Schema Inspection
      |
      v
Text-to-SQL Generation
      |
      v
SQL Validation
      |
      v
Database Execution
      |
      v
Query Results
      |
      v
Chatbot Response
```

## Project Structure

```text
text-to-sql-ai-chatbot/
├── app/
├── database/
├── sql_generator/
├── validation/
├── api/
├── ui/
├── tests/
├── main.py
├── requirements.txt
├── .env.example
└── README.md
```

## Installation

Clone the repository:

```bash
git clone <YOUR_REPOSITORY_URL>
cd text-to-sql-ai-chatbot
```

Create a virtual environment:

```bash
python -m venv venv
```

Activate it:

**Windows**
```bash
venv\Scripts\activate
```

**Linux / macOS**
```bash
source venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

## Configuration

Create a `.env` file based on `.env.example`.

Configure the database connection:

```env
DATABASE_URL=sqlite:///./database.db
OPENAI_API_KEY=your_api_key_here
```

For PostgreSQL, use an appropriate SQLAlchemy connection URL.

## Running the Application

Start the backend:

```bash
uvicorn api.main:app --reload
```

Start the Streamlit interface:

```bash
streamlit run ui/streamlit_app.py
```

Open the API documentation:

```text
http://127.0.0.1:8000/docs
```

## Example Usage

A user might ask:

```text
Show me the top 5 customers by total order value.
```

The application uses the database schema to generate an appropriate SQL query, validates the query, and executes it against the connected database.

## Technology Stack

| Technology | Purpose |
|---|---|
| Python | Core application language |
| FastAPI | Backend API |
| Streamlit | Interactive chatbot interface |
| SQLAlchemy | Database connectivity |
| SQLGlot | SQL parsing and validation |
| SQLite | Lightweight database |
| PostgreSQL | Relational database support |

## Security Considerations

- Only validated SELECT queries should be executed.
- Generated SQL must be validated before database execution.
- Database credentials should be stored in environment variables.
- Database permissions should follow the principle of least privilege.
- Production deployments should use read-only database credentials.
- SQL validation does not replace database-level access controls.

## Current Limitations

- Mock SQL generation may be used when an external language model is not configured.
- SQL generation quality depends on the model and the database schema.
- Complex joins and ambiguous natural-language questions may require clarification.
- The application should be tested against the target database before production use.

## Future Improvements

- Improve schema retrieval and context management.
- Support more database engines.
- Add query explanation functionality.
- Improve handling of complex joins and nested queries.
- Add conversation history and query caching.
- Introduce role-based access control.
- Add more comprehensive SQL-generation evaluation datasets.

## License

This project is intended for educational, research, and experimentation purposes. Add an appropriate open-source license before public distribution.
