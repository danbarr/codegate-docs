# cli Documentation

## Brief Description

The `cli` is a command-line interface for CodeGate, a configurable service gateway. It provides various commands to manage and operate the CodeGate server.

## Usage

To use the CodeGate CLI, run the `codegate` command followed by a subcommand and its options.

## Available CLI Commands and Options

### `serve`

Start the CodeGate server.

Options:

* `--port INTEGER`: Port to listen on (default: 8989)

* `--proxy-port INTEGER`: Proxy port to listen on (default: 8990)

* `--host TEXT`: Host to bind to (default: localhost)

* `--log-level [CRITICAL|ERROR|WARNING|INFO|DEBUG]`: Set the log level (default: INFO)

* `--log-format [JSON|CONSOLE]`: Set the log format (default: JSON)

* `--config FILE`: Path to YAML config file

* `--prompts FILE`: Path to YAML prompts file

* `--vllm-url TEXT`: vLLM provider URL (default: <http://localhost:8000/v1>)

* `--openai-url TEXT`: OpenAI provider URL (default: <https://api.openai.com/v1>)

* `--anthropic-url TEXT`: Anthropic provider URL (default: <https://api.anthropic.com/v1>)

* `--ollama-url TEXT`: Ollama provider URL (default: <http://localhost:11434/>)

* `--lm-studio-url TEXT`: LM Studio provider URL (default: <http://localhost:1234/>)

* `--model-base-path TEXT`: Path to the model base directory

* `--embedding-model TEXT`: Name of the model to use for embeddings

* `--certs-dir TEXT`: Directory for certificate files (default: ./certs)

* `--ca-cert TEXT`: CA certificate file name (default: ca.crt)

* `--ca-key TEXT`: CA key file name (default: ca.key)

* `--server-cert TEXT`: Server certificate file name (default: server.crt)

* `--server-key TEXT`: Server key file name (default: server.key)

* `--db-path TEXT`: Path to the main SQLite database file (default: ./codegate\_volume/db/codegate.db)

* `--vec-db-path TEXT`: Path to the vector SQLite database file (default: ./sqlite\_data/vectordb.db)

### `show-prompts`

Display prompts from the specified file or default if no file specified.

Options:

* `--prompts FILE`: Path to YAML prompts file (optional, shows default prompts if not provided)

### `restore-backup`

Restore the database from the specified backup.

Options:

* `--backup-path DIRECTORY`: Directory path where the backup file is located (required)

* `--backup-name TEXT`: Name of the backup file to restore (required)

### `generate-certs`

Generate certificates for the CodeGate server.

Options:

* `--certs-out-dir DIRECTORY`: Directory path where the certificates are going to be generated

* `--ca-cert-name TEXT`: Name that will be given to the created ca-cert

* `--ca-key-name TEXT`: Name that will be given to the created ca-key

* `--server-cert-name TEXT`: Name that will be given to the created server-cert

* `--server-key-name TEXT`: Name that will be given to the created server-key

* `--force-certs`: Force the generation of certificates even if they already exist (Warning: this will overwrite existing certificates)

* `--log-level [CRITICAL|ERROR|WARNING|INFO|DEBUG]`: Set the log level (default: INFO)

* `--log-format [JSON|CONSOLE]`: Set the log format (default: JSON)

## Examples

1. Start the CodeGate server with custom port and log level:

```
codegate serve --port 9000 --log-level DEBUG
```

2. Display prompts from a custom file:

```
codegate show-prompts --prompts /path/to/custom_prompts.yaml
```

3. Restore a backup:

```
codegate restore-backup --backup-path /path/to/backups --backup-name my_backup.zip
```

## Notes

* Always ensure you have the necessary permissions when working with file paths and directories.

* When using the `generate-certs` command, be cautious with the `--force-certs` option as it will overwrite existing certificates.

* The `serve` command has many options for customization. Refer to the configuration documentation for more details on each option.
