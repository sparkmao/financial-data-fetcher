# TongdaXin Financial Data Fetcher

一个基于 TongdaXin TQ 策略接口的金融数据获取工具，提供多种API脚本用于获取股票行情、财务数据、板块信息等。

## 功能特性

- **行情数据** - K线数据、快照数据、股票基本信息、交易日列表
- **财务数据** - 专业财务数据、股票交易数据、个股财务数据
- **板块数据** - 板块成分股、板块交易数据、板块代码列表
- **市场数据** - 市场整体交易数据
- **新股与分红** - 新股申购信息、分红配送数据、股本数据
- **自定义板块** - 创建、删除、重命名自定义板块，管理板块成分股
- **ETF与可转债** - ETF信息查询、可转债基础信息
- **行情订阅** - 订阅/取消订阅股票实时更新

## 前置条件

### 1. Python 环境

```bash
pip install numpy pandas
```

### 2. 通达信金融终端TQ版

- 需要安装 **通达信金融终端TQ版** 并确保其正常运行
- 本工具依赖 TQ 策略接口与通达信客户端进行数据交互
- 确保 TQ 策略功能已启用

## 快速开始

### 1. 克隆项目

```bash
git clone <repository-url>
cd financial-data-fetcher
```

### 2. 设置环境变量

```bash
# Unix/Linux/Mac
export PYTHONPATH=$(pwd)

# Windows (PowerShell)
$env:PYTHONPATH = $PWD

# Windows (CMD)
set PYTHONPATH=%CD%
```

### 3. 运行脚本

```bash
# 获取K线数据
python scripts/get_market_data.py --stock_list 688318.SH --period 1d --count 1

# 获取快照数据
python scripts/get_market_snapshot.py --stock_code 688318.SH

# 获取专业财务数据
python scripts/get_financial_data.py --stock_list 688318.SH --field_list FN193 FN194

# 获取新股申购信息
python scripts/get_ipo_info.py --ipo_type 2 --ipo_date 1
```

## 常用脚本

| 脚本 | 功能 |
|------|------|
| `get_market_data.py` | 获取K线行情数据 |
| `get_market_snapshot.py` | 获取快照数据 |
| `get_stock_info.py` | 获取证券基本信息 |
| `get_financial_data.py` | 获取专业财务数据 |
| `get_gpjy_value.py` | 获取股票交易数据 |
| `get_stock_list.py` | 获取系统分类成份股 |
| `get_sector_list.py` | 获取A股板块代码列表 |
| `get_stock_list_in_sector.py` | 获取板块成份股 |
| `get_bkjy_value.py` | 获取板块交易数据 |
| `get_scjy_value.py` | 获取市场交易数据 |
| `get_ipo_info.py` | 获取新股申购信息 |
| `get_divid_factors.py` | 获取分红配送数据 |
| `get_user_sector.py` | 获取自定义板块列表 |
| `get_cb_info.py` | 获取可转债基础信息 |
| `refresh_cache.py` | 刷新行情缓存 |

## 参数枚举值

### period (周期)
| 值 | 说明 |
|---|------|
| `1m` | 1分钟 |
| `5m` | 5分钟 |
| `15m` | 15分钟 |
| `30m` | 30分钟 |
| `1h` | 60分钟(1小时) |
| `1d` | 1天 |
| `1w` | 1周 |
| `1mon` | 1月 |
| `1q` | 1季 |
| `1y` | 1年 |

### dividend_type (复权类型)
| 值 | 说明 |
|---|------|
| `none` | 不复权 |
| `front` | 前复权 |
| `back` | 后复权 |

### market (市场)
| 值 | 说明 |
|---|------|
| `AG` | A股 |
| `HK` | 港股 |
| `US` | 美股 |
| `QH` | 国内期货 |
| `ZZ` | 中证和国证指数 |
| `ZS` | 沪深京指数 |

## 项目结构

```
financial-data-fetcher/
├── SKILL.md              # Agent skill 定义文件
├── CLAUDE.md             # Claude Code 开发指南
├── .gitignore            # Git 忽略配置
├── lib/
│   ├── __init__.py
│   └── tqcenter.py       # TongdaXin API 封装
├── scripts/              # 33个API执行脚本
│   ├── get_market_data.py
│   ├── get_market_snapshot.py
│   └── ...
└── references/           # API参考文档
    ├── Enum.md
    ├── Market information/
    ├── Financial data/
    └── ...
```

## API 文档

详细API文档请参考 `references/` 目录下的 Markdown 文件：

- `references/Enum.md` - 参数枚举定义
- `references/Market information/` - 市场信息API
- `references/Financial data/` - 财务数据API
- `references/Sector constituent stocks/` - 板块成分股API

## 许可证

MIT License