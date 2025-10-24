# Data Analyst Agent

A multi-agent system for automated data analysis using LangChain and E2B Code Interpreter. This project implements a hierarchical agent architecture that can explore datasets, perform statistical analysis, and generate visualizations through natural language queries.

## 🚀 Features

- **Multi-Agent Architecture**: Three specialized agents working together
  - **Research Agent**: Dataset exploration and basic statistics
  - **Analysis Agent**: Advanced data analysis and visualization
  - **Supervisor Agent**: Orchestrates workflow between agents

- **Natural Language Interface**: Ask questions about your data in plain English
- **Secure Code Execution**: Uses E2B Code Interpreter for safe Python code execution
- **Automatic File Handling**: Seamlessly uploads and processes CSV files
- **Comprehensive Analysis**: Statistical analysis, visualizations, and insights

## 📊 Sample Dataset

The project includes a sample dataset (`data_science_student_marks.csv`) containing:
- **497 students** from various locations
- **8 columns**: student_id, location, age, sql_marks, excel_marks, python_marks, power_bi_marks, english_marks
- **Real-world data** for testing and demonstration

## 🏗️ Architecture
<img width="694" height="1262" alt="Untitled diagram-2025-10-24-201007" src="https://github.com/user-attachments/assets/6a9293d0-f8a3-4597-ba24-b71126b613f9" />



## 🛠️ Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd data-analyst-agent
   ```

2. **Install dependencies**
   ```bash
   cd backend
   pip install -r requirements.txt
   ```

3. **Set up environment variables**
   Create a `.env` file in the backend directory:
   ```env
   OPENAI_API_KEY=your_openai_api_key_here
   E2B_API_KEY=your_e2b_api_key_here
   ```

4. **Launch Jupyter Notebook**
   ```bash
   jupyter notebook notebook.ipynb
   ```

## 📝 Usage

### Basic Queries

The system can handle various types of natural language queries:

**Dataset Exploration:**
- "What files are present in the directory?"
- "What data is present in the data science student dataset?"
- "What is the average age of students?"

**Data Analysis:**
- "Plot a bar chart of average age by location"
- "Create a histogram of student ages"
- "Run regression analysis on the dataset"
- "Show correlation between different subject marks"

### Example Workflow

```python
query = (
    "Give me an overview of the datasets I have "
    "Visualize any interesting insights from the first dataset"
)

for step in supervisor_agent.stream(
    {"messages": [{"role": "user", "content": query}]}
):
    for update in step.values():
        for message in update.get("messages", []):
            message.pretty_print()
```

## 🔧 Available Tools

### Research Tools
- `list_files_in_directory()`: Lists available files in the data directory
- `read_csv_file()`: Provides basic statistics and overview of CSV files

### Analysis Tools
- `code_tool()`: Executes Python code in a secure sandbox environment
  - Supports file uploads
  - Returns execution results and logs
  - Handles errors gracefully

### Agent Wrappers
- `research()`: Natural language interface for dataset exploration
- `analyze_data()`: Natural language interface for data analysis and visualization

## 📦 Dependencies

Key dependencies include:
- **LangChain**: Multi-agent framework
- **E2B Code Interpreter**: Secure code execution
- **OpenAI**: GPT-4o-mini for agent reasoning
- **Pandas**: Data manipulation
- **Jupyter**: Interactive notebook environment

See `backend/requirements.txt` for the complete list.

## 🎯 Use Cases

- **Educational**: Learn data analysis through interactive queries
- **Research**: Quick exploration of new datasets
- **Prototyping**: Rapid analysis and visualization of data
- **Automation**: Automated reporting and insights generation

## 🔒 Security

- **Sandboxed Execution**: All code runs in isolated E2B environments
- **No Local Code Execution**: Prevents malicious code from affecting your system
- **File Upload Control**: Only specified files are uploaded to the sandbox

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 🆘 Support

For questions or issues:
1. Check the Jupyter notebook documentation
2. Review the example queries
3. Open an issue on GitHub

## 🔮 Future Enhancements

- Support for additional file formats (JSON, Excel, etc.)
- Integration with more data sources
- Advanced visualization options
- Custom agent configurations

- Batch processing capabilities

