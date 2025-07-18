<img src="https://r2cdn.perplexity.ai/pplx-full-logo-primary-dark%402x.png" class="logo" width="120"/>

# Content Search Tool

A powerful Python-based search tool that allows you to search for specific words, phrases, or sentences across multiple file formats including Word documents, PDFs, Markdown files, Python scripts, and Jupyter notebooks.

## 🚀 Features

- **Multi-format Support**: Search across `.py`, `.md`, `.ipynb`, `.doc`, `.docx`, and `.pdf` files
- **Flexible Search**: Find exact words, phrases, or sentences (3-15+ words)
- **Partial Matching**: Finds concatenated words (e.g., searching "residual" finds "residualNetwork")
- **Case Sensitivity Options**: Toggle between case-sensitive and case-insensitive searches
- **Directory Exclusion**: Automatically excludes common development folders (venv, node_modules, .git, etc.)
- **Dual Interface**: Both Command Line Interface (CLI) and Graphical User Interface (GUI)
- **Real-time Logging**: See search progress and directory traversal in real-time
- **Threading Support**: Non-blocking GUI with progress indicators


## 📁 File Structure

```
content-search-tool/
├── search-content.py      # Core search functions and CLI interface
├── search_gui.py          # GUI interface
├── README.md             # This documentation
├── requirements.txt      # Python dependencies
└── examples/             # Example files for testing (optional)
    ├── sample.py
    ├── sample.md
    ├── sample.pdf
    └── sample.docx
```


## 🛠️ Installation

### Prerequisites

- Python 3.7 or higher
- pip (Python package installer)


### Install Dependencies

```bash
pip install python-docx pdfplumber
```

Or using requirements file:

```bash
pip install -r requirements.txt
```


### Download Files

1. Download `search-content.py` and `search_gui.py`
2. Place them in your project directory
3. Ensure both files are in the same folder

## 🚀 Usage

### Command Line Interface (CLI)

```bash
python search-content.py
```

**Interactive prompts:**

1. Enter search term
2. Choose case sensitivity (y/n)
3. View results

**Example:**

```
Enter the word/phrase/sentence to search for: machine learning
Case sensitive search? (y/n): n

Searching for 'machine learning' in current directory...
============================================================
Searching directories: ['docs', 'notebooks', 'scripts']
Found 3 file(s) containing 'machine learning':
------------------------------------------------------------
Full file: analysis.py | Directory: ./scripts
Full file: tutorial.ipynb | Directory: ./notebooks
Full file: research.pdf | Directory: ./docs
```


### Graphical User Interface (GUI)

```bash
python search_gui.py
```

**GUI Features:**

- **Search Input**: Enter your search term
- **Case Sensitive Checkbox**: Toggle case sensitivity
- **Search Button**: Start search process
- **Clear Button**: Reset interface
- **Progress Bar**: Visual search progress
- **Logs Area**: Real-time search progress
- **Results Area**: Formatted search results


## 📋 Supported File Formats

| Format | Extensions | Description |
| :-- | :-- | :-- |
| **Python Scripts** | `.py` | Plain text search through Python code |
| **Markdown** | `.md` | Plain text search through Markdown documents |
| **Jupyter Notebooks** | `.ipynb` | Searches both code and markdown cells |
| **Word Documents** | `.doc`, `.docx` | Extracts text from paragraphs and tables |
| **PDF Documents** | `.pdf` | Extracts text from all pages |

## ⚙️ Configuration

### Excluded Directories

The tool automatically excludes these directories from search:

```python
excluded_folders = {
    "venv99855", ".venv99855",    # Virtual environments
    "env", ".env",                # Environment folders
    "node_modules",               # Node.js modules
    ".git",                       # Git repository
    "__pycache__",                # Python cache
    ".pytest_cache",              # Pytest cache
    ".mypy_cache",                # MyPy cache
    "site-packages",              # Python packages
    ".ipynb_checkpoints",         # Jupyter checkpoints
}
```


### Customizing Excluded Folders

Edit the `excluded_folders` set in the `search_files_for_term` function:

```python
# Add your custom folders to exclude
excluded_folders.add("my_custom_folder")
excluded_folders.add("temp_files")
```


## 🔍 Search Examples

### Basic Word Search

```
Search term: "python"
Result: Finds "python", "Python", "PYTHON" (case-insensitive)
```


### Phrase Search

```
Search term: "machine learning algorithm"
Result: Finds exact phrase in documents
```


### Concatenated Word Search

```
Search term: "residual"
Result: Finds "residual", "residualNetwork", "ResidualBlock"
```


### Case-Sensitive Search

```
Search term: "API" (case-sensitive: yes)
Result: Finds "API" but not "api" or "Api"
```


## 🐛 Troubleshooting

### Common Issues

#### 1. **Import Errors**

```
ImportError: No module named 'docx'
```

**Solution:**

```bash
pip install python-docx
```


#### 2. **PDF Processing Warnings**

```
Cannot set gray non-stroke color because /'P1' is an invalid float value
```

**Solution:** These are non-fatal warnings from PDF processing. Search will continue normally.

#### 3. **Permission Errors**

```
PermissionError: [Errno 13] Permission denied
```

**Solution:** Run with appropriate permissions or exclude restricted directories.

#### 4. **GUI Not Responding**

**Solution:** The search is running in background. Wait for completion or check logs.

### Performance Tips

1. **Exclude Large Directories**: Add large directories to `excluded_folders`
2. **Specific Search Terms**: Use specific terms to reduce processing time
3. **Close Other Applications**: Free up system resources for large searches

## 📊 Output Format

### CLI Output

```
Found 3 file(s) containing 'search_term':
------------------------------------------------------------
Full file: document.pdf | Directory: ./folder
Full file: script.py | Directory: ./scripts
Full file: notes.md | Directory: ./docs
```


### GUI Output

```
✅ Found 3 file(s) containing 'search_term':
================================================================================

 1. 📄 document.pdf
    📁 ./folder
    🔗 ./folder/document.pdf

 2. 📄 script.py
    📁 ./scripts
    🔗 ./scripts/script.py
```


## 🤝 Contributing

### Adding New File Formats

1. **Create search function:**
```python
def search_in_new_format(file_path, search_term, case_sensitive=False):
    # Your implementation here
    pass
```

2. **Add to extensions dictionary:**
```python
extensions = {
    # ... existing formats
    ".new": search_in_new_format,
}
```


### Reporting Issues

Please report issues with:

- Python version
- Operating system
- Error messages
- Steps to reproduce


## 📄 License

This project is open source. Feel free to modify and distribute according to your needs.

## 🔄 Version History

- **v1.0.0**: Initial release with CLI interface
- **v1.1.0**: Added GUI interface
- **v1.2.0**: Added PDF support with pdfplumber
- **v1.3.0**: Separated CLI and GUI into different files


## 📞 Support

For support and questions:

1. Check this README for common solutions
2. Review error messages in logs
3. Ensure all dependencies are installed
4. Verify file permissions

## 🎯 Future Enhancements

Planned features:

- [ ] Search result export (CSV, JSON)
- [ ] Regular expression support
- [ ] Search within specific date ranges
- [ ] Multiple search terms with AND/OR logic
- [ ] Search result highlighting
- [ ] Configuration file support
- [ ] Web interface
- [ ] API endpoint

**Happy Searching! 🔍**

