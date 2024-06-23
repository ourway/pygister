# Gist Python Tool

This Python tool allows you to interact with GitHub Gists. You can create, read, list, and delete gists using this tool.

## Prerequisites

- Python 3.12
- GitHub personal access token

## Installation

### 1. Clone the Repository

```bash
git clone <repository-url>
cd <repository-directory>
```

### 2. Create and Activate a Virtual Environment

```bash
python3.12 -m venv .venv
source .venv/bin/activate  # On Windows use `.venv\Scripts\activate`
```

### 3. Install Dependencies

Install the required dependencies using `pip` and the `requirements.txt` file:

```bash
pip install -r requirements.txt
```

## Configuration

### Set Up Authentication

You need to create a GitHub personal access token and save it in a file named `~/.gist`. This token will be used to authenticate your requests to the GitHub API.

1. Go to [GitHub Personal Access Tokens](https://github.com/settings/tokens).
2. Generate a new token with the `gist` scope.
3. Save the token in a file named `~/.gist` in your home directory:

```bash
echo "your_personal_access_token" > ~/.gist
```

## Usage

### 1. Creating a Gist

You can create a gist with the following sample code:

```python
from src.gist import Gist

# Sample content for creating a gist
content = "print('Hello, World!')"
options = {
    'description': 'A hello world program',
    'public': True,
    'filename': 'hello.py'
}

result = Gist.gist(content, options)
print("Gist created:", result)
```

### 2. Listing All Gists

List all gists for the authenticated user:

```python
from src.gist import Gist

gists = Gist.list_all_gists()
print("Listing all gists:", gists)
```

### 3. Reading a Gist

Read the content of a specific gist by its ID:

```python
from src.gist import Gist

gist_id = 'your_gist_id_here'
content = Gist.read_gist(gist_id)
print("Gist content:", content)
```

### 4. Deleting a Gist

Delete a specific gist by its ID:

```python
from src.gist import Gist

gist_id = 'your_gist_id_here'
Gist.delete_gist(gist_id)
print("Gist deleted successfully.")
```

## Running Tests

To run the tests, ensure you have `pytest` installed and configured. You can run the tests using the following command:

```bash
pytest
```

Make sure your `PYTHONPATH` includes the `src` directory. You can set it in your `pyproject.toml` file:

```toml
[tool.pytest.ini_options.env]
PYTHONPATH = "src"
```

## Project Structure

```
your_project/
│
├── src/
│   └── gist.py
│
├── tests/
│   └── test_gist.py
│
├── requirements.txt
├── pyproject.toml
└── README.md
```

## Contributing

Contributions are welcome! Please open an issue or submit a pull request.

## Author

Farshid Ashouri

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
