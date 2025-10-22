# Edge Sniper Bot

A command-line sniper bot for token launches and on-chain opportunities. Edge Sniper Bot supports multiple DEX providers and launch platforms, and can be run from pre-built binaries or built from source.

---

## Overview

Edge Sniper Bot is designed to help users monitor liquidity events and execute snipes on supported platforms. It provides configuration-driven behavior and separate modules for different targets. This repository includes example configurations and utilities to initialize and run the bot against multiple DEX types.

---

## Supported Targets

* dxsale
* pancake (PancakeSwap)
* uniswap-v2 (Uniswap V2-style DEXes)

---

## License

This project is distributed under the Apache-2.0 license. See the LICENSE file for details.

---

## Download and Build

### Option 1 — Download a release binary

Download the appropriate binary from the project's releases page (if available) and run the commands below.

> Note: Verify release binaries before running them.

### Option 2 — Build and run from source

Requires Go 1.XX or later.

1. Clone the repository:

```bash
git clone https://github.com/edge-sniper/sniper-bot.git
cd sniper-bot
```

2. Fetch dependencies and build:

```bash
go mod download
go build -o sniper-bot .
```

3. Run the bot via the compiled binary or `go run`:

```bash
./sniper-bot init          # generate example config file
./sniper-bot dxsale        # run dxsale module
./sniper-bot cake          # run pancake module
./sniper-bot uni           # run uniswap-v2 module
# or
go run main.go init
go run main.go dxsale
```

---

## Configuration

1. Run `sniper-bot init` (or `go run main.go init`) to generate a sample `config.yml`.
2. Edit `config.yml` to add RPC endpoints, private key(s), gas strategy, target addresses, and module-specific settings.
3. Save configuration and run the desired module command.

Important configuration items:

* RPC endpoint(s) for the target chain
* Wallet private key (handle securely)
* Gas price / priority strategy
* Target token or sale contract addresses
* Slippage and transaction parameters

---

## Commands

* `init` — Create a starter `config.yml`.
* `dxsale` — Run the DXSale sniping module.
* `cake` — Run the PancakeSwap sniping module.
* `uni` — Run the Uniswap V2 sniping module.

When running examples included in the `examples` folder, use:

```bash
cargo run --example <example_name>
```

(If applicable; some components include example utilities.)

---

## Project Structure (high level)

```
.
├── cmd/                # CLI entry points and commands
├── contract/           # Smart contract helpers / integrations
├── runner/             # Execution and orchestration logic
├── utils/              # Utility functions and helpers
├── examples/           # Example scripts and small utilities
├── config.yml.example  # Example configuration
├── README.md
├── LICENSE
```

---

## Examples and Utilities

The `examples` directory contains small utilities and tests, such as:

* Inspecting pending transactions in the mempool
* Tracking pending swaps for supported DEXes
* Subscribing to new blocks and events

Use these to test and prototype logic prior to executing real transactions.

---

## Warning and Disclaimer

This software is experimental and provided for educational and research purposes. Use at your own risk. There is no guarantee of success, profitability, or security. Thoroughly test in safe environments (local testnets or isolated test chains) before interacting with real assets.

Do not expose private keys or sensitive credentials in version control or shared configurations. Always follow security best practices.

---

## Contributing

Contributions are welcome. Suggested improvements:

* Better trade-size / profit optimization
* Parallel token scanning and multi-target evaluation
* Gas and transaction efficiency improvements

To contribute:

1. Fork the repository
2. Create a branch for your change
3. Submit a pull request with a clear description and tests where appropriate

---

## Contact

Refer to the repository's Issues page for questions, bug reports, and feature requests.
