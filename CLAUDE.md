# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a **TongdaXin Financial Data Fetcher** agent skill project that provides financial data retrieval capabilities through the TongdaXin TQ strategy interface. It includes 33 Python scripts for accessing stock market data, financial data, sector information, and more.

## Prerequisites

- Python 3.x with `numpy` and `pandas` packages
- TongdaXin Financial Terminal TQ Edition (must be installed and running)
- TQ strategy interface must be enabled

## Project Structure

```
financial-data-fetcher/
├── SKILL.md           # Agent skill definition file
├── lib/
│   ├── __init__.py
│   └── tqcenter.py    # Core TongdaXin API wrapper
├── scripts/           # 33 API execution scripts
│   ├── get_market_data.py
│   ├── get_market_snapshot.py
│   ├── get_stock_info.py
│   ├── get_financial_data.py
│   └── ... (29 more scripts)
└── references/        # API documentation (Markdown files)
    ├── Enum.md
    ├── Market information/
    ├── Financial data/
    ├── Sector constituent stocks/
    └── ...
```

## Running Scripts

Set PYTHONPATH before running any script:

```bash
# Unix/Linux/Mac
export PYTHONPATH=/path/to/project

# Windows (PowerShell)
$env:PYTHONPATH = "C:\path\to\project"

# Run a script
python scripts/get_market_data.py --stock_list 688318.SH --period 1d
```

Or use the `-m` module execution:

```bash
cd /path/to/project
python -m scripts.get_market_data --stock_list 688318.SH --period 1d
```

## Key Enums (from references/Enum.md)

- **period**: `1m`, `5m`, `15m`, `30m`, `1h`, `1d`, `1w`, `1mon`, `1q`, `1y`, `tick`
- **dividend_type**: `none`, `front`, `back`
- **market**: `AG` (A股), `HK` (港股), `US` (美股), `QH` (国内期货), `ZZ` (中证指数), `ZS` (沪深京指数)

## Common Tasks

- **Add new API script**: Reference `references/` folder for API documentation, use argparse for CLI arguments
- **Modify existing script**: Check SKILL.md for command usage patterns
- **Add enum values**: Update both script arguments and SKILL.md documentation

## Key Files

- `lib/tqcenter.py` - Core API wrapper that wraps TongdaXin TQ interface
- `SKILL.md` - Agent skill definition with all command examples
- `references/Enum.md` - Parameter enum definitions