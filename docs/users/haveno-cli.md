# Haveno CLI

The Haveno CLI (`haveno-cli`) is a command-line interface to a Haveno daemon. Each command makes a single API call, such as checking balances, browsing offers, or managing trades, and prints the result.

!!! info "Just want to trade?"
    If you only want to buy and sell XMR, see [Getting Started](getting-started.md). To build programs on top of Haveno, see [Haveno API](haveno-api.md).

## Requirements

- A running Haveno daemon (see [Build and Run Haveno](../developers/installing.md))

Building Haveno also builds the CLI, available as `./haveno-cli` in the project directory. It connects to the daemon directly, so no proxy is needed.

## Usage

```bash
./haveno-cli [options] <method> [params]
```

| Option | Description | Default |
| ------ | ----------- | ------- |
| `--host` | daemon hostname or IP | `localhost` |
| `--port` | daemon API port | `9998` |
| `--password` | daemon API password (required) | |

The password and port must match the daemon's `--apiPassword` and `--apiPort`.

## Examples

Start a daemon in one terminal:

```bash
make haveno-daemon-mainnet
```

Then use the CLI from another:

```bash
# check the connection
./haveno-cli --port=1201 --password=apitest getversion

# get wallet balances
./haveno-cli --port=1201 --password=apitest getbalance

# get an address to deposit XMR
./haveno-cli --port=1201 --password=apitest getxmrprimaryaddress

# see open offers to sell XMR for USD
./haveno-cli --port=1201 --password=apitest getoffers --direction=sell --currency-code=USD
```

## Getting help

List all methods and options:

```bash
./haveno-cli --help
```

Get help for a specific method:

```bash
./haveno-cli --port=1201 --password=apitest takeoffer --help
```
