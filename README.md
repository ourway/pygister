# Pygister

A Python tool to interact with GitHub Gists. This tool allows you to create, read, update, and sync Gists directly from the command line.

## Features

- Create a new Gist from a local file.
- Read the content of a Gist by its ID.
- Update an existing Gist with the content of a local file.
- Synchronize a local file with a remote Gist, keeping them in sync at regular intervals.
- Print the version of the `pygister` library.

## Installation

### Using pip

You can install `pygister` directly from the source:

```bash
pip install -e .
```

### Using setup.py

To install using the `setup.py` script:

```bash
python setup.py install
```

## Usage

### Command Line Interface

#### Print the version

To print the version of the `pygister` library:

```bash
pygist version
```

#### Create a Gist

To create a new Gist from a local file and return the short URL of the new Gist:

```bash
pygist push <filename>
```

#### Read a Gist

To read the content of a Gist by its ID and print it to stdout:

```bash
pygist read <ID>
```

#### Update a Gist

To update an existing Gist with the content of a local file:

```bash
pygist push <filename> <ID>
```

#### Sync a Local File with a Gist

To synchronize a local file with a remote Gist every specified number of seconds:

```bash
pygist sync <ID> <Seconds>
```

- If the local file does not exist, it will be created.
- If the local file is newer, it will update the Gist.
- If the Gist is newer, it will update the local file.
- The process will run in a loop every `<Seconds>` and will gracefully shut down on receiving `CTRL-C`.

### Example Usage

1. **Create a Gist:**

   ```bash
   pygist push example.txt
   ```

2. **Read a Gist:**

   ```bash
   pygist read 1234567890abcdef1234567890abcdef
   ```

3. **Update a Gist:**

   ```bash
   pygist push example.txt 1234567890abcdef1234567890abcdef
   ```

4. **Sync a Local File with a Gist:**

   ```bash
   pygist sync 1234567890abcdef1234567890abcdef 60
   ```

   This command will sync the local file associated with the Gist ID every 60 seconds.

## Development

### Running Tests

To run tests:

```bash
pytest
```

### Linting and Formatting

To lint and format the code:

```bash
make lint
```

### Type Checking

To perform type checking:

```bash
make type-check
```

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

## Author

Farshid Ashouri - farsheed.ashouri@gmail.com
