# APRSD Yahoo Finance Stock Quotes

[![PyPI](https://img.shields.io/pypi/v/aprsd-stock-plugin.svg)](https://pypi.org/project/aprsd-stock-plugin/)
[![Status](https://img.shields.io/pypi/status/aprsd-stock-plugin.svg)](https://pypi.org/project/aprsd-stock-plugin/)
[![Python Version](https://img.shields.io/pypi/pyversions/aprsd-stock-plugin)](https://pypi.org/project/aprsd-stock-plugin)
[![License](https://img.shields.io/pypi/l/aprsd-stock-plugin)](https://opensource.org/licenses/Apache%20Software%20License%202.0)

[![Read the Docs](https://img.shields.io/readthedocs/aprsd-stock-plugin/latest.svg?label=Read%20the%20Docs)](https://aprsd-stock-plugin.readthedocs.io/)
[![Tests](https://github.com/hemna/aprsd-stock-plugin/workflows/Tests/badge.svg)](https://github.com/hemna/aprsd-stock-plugin/actions?workflow=Tests)
[![Codecov](https://codecov.io/gh/hemna/aprsd-stock-plugin/branch/main/graph/badge.svg)](https://codecov.io/gh/hemna/aprsd-stock-plugin)
[![pre-commit](https://img.shields.io/badge/pre--commit-enabled-brightgreen?logo=pre-commit&logoColor=white)](https://github.com/pre-commit/pre-commit)

## Features

* APRSD Plugin that gets a stock quote from Yahoo Finance python API and returns that.

## Installation

You can install **APRSD Yahoo Finance Stock Quotes** via [pip](https://pip.pypa.io/) from [PyPI](https://pypi.org/):

```console
$ pip install aprsd-stock-plugin
```

## Usage

The stock plugin responds to APRS messages that start with `s` or `S` followed by a stock symbol.

### Example Interactions

#### Basic Stock Quote Request

Send an APRS message to your APRSD instance:

```
s AAPL
```

**Response:**
```
AAPL - ask: 175.50 high: 176.20 low: 174.80
```

#### Requesting Different Stocks

You can query any stock symbol available on Yahoo Finance:

```
s TSLA
```

**Response:**
```
TSLA - ask: 245.30 high: 248.50 low: 243.10
```

```
s MSFT
```

**Response:**
```
MSFT - ask: 380.25 high: 382.00 low: 378.50
```

#### Error Handling

If you don't provide a stock symbol:

```
s
```

**Response:**
```
No stock symbol
```

If the stock symbol is invalid or cannot be fetched:

```
s INVALID123
```

**Response:**
```
Failed to fetch stock 'INVALID123'
```

### Command Format

The plugin recognizes commands that:
- Start with `s` or `S` (case-insensitive)
- Are followed by a space and a stock symbol

**Valid formats:**
- `s AAPL`
- `S TSLA`
- `stock MSFT`
- `Stock GOOGL`

**Note:** The plugin uses a regex pattern `^[sS]` to match commands, so any message starting with `s` or `S` will trigger the plugin. The stock symbol is extracted from the rest of the message.

### Configuration

The plugin can be enabled/disabled via APRSD configuration. By default, the plugin is disabled and needs to be enabled in your APRSD configuration file:

```ini
[aprsd_stock_plugin]
enabled = True
```

## Contributing

Contributions are very welcome.
To learn more, see the [Contributor Guide](CONTRIBUTING.rst).

## License

Distributed under the terms of the [Apache Software License 2.0 license](https://opensource.org/licenses/Apache%20Software%20License%202.0),
**APRSD Yahoo Finance Stock Quotes** is free and open source software.

## Issues

If you encounter any problems,
please [file an issue](https://github.com/hemna/aprsd-stock-plugin/issues) along with a detailed description.

## Credits

This project was generated from [@hemna](https://github.com/hemna)'s [APRSD Plugin Python Cookiecutter](https://github.com/hemna/cookiecutter-aprsd-plugin) template.
