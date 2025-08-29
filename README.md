<!--
Old readme - skip to line 41 for current one


# Clone

```
git clone https://github.com/PirateNetwork/pirate-btcpay.git
```

Edit the `lwd_url` in `Rocket.toml`
Edit the `fvk` in `Rocket.toml` with your Pirate Chain Full Viewing Key
Edit the `starting_height` in `Rocket.toml`

# Build

CD into the repo root ~/pirate-btcpay

```
git submodule update --init
cargo b --release
```

# Run

```
./target/release/walletd
```

# Test

```
cd tests
npm install
npx mocha
```
-->



## Pirate Chain BTCPay Server

A minimal, self-hostable BTCPay Server setup for Pirate Chain (ARRR). This pulls prebuilt images and runs them with Docker.

## Prerequisites
- **Docker**: Install Docker Desktop or Docker Engine for your OS (`https://www.docker.com`)
- **curl**: Installed by default on macOS/Linux; on Windows, use `curl.exe --install` in CMD/PowerShell

## Quick start
Follow the instructions for your OS. All paths below create and use a new `pirate-btcpay` folder in your home directory.

### Windows (CMD)
1. Install Docker from `https://www.docker.com` and start it
2. Open CMD
3. Create a working folder and download the compose file:
   ```
   mkdir %USERPROFILE%\pirate-btcpay && cd %USERPROFILE%\pirate-btcpay
   curl -fsSL https://raw.githubusercontent.com/PirateNetwork/pirate-btcpay/main/docker/docker-compose.yml -o compose.yaml
   ```
4. Edit config values in `compose.yaml` file:
   - Set your Pirate Full Viewing Key and wallet birthday height from your wallet:
   ```
   fvk: Your-Full-Veiwing-Key
   starting_height: 200000 (example, base this on your wallet's birthday height)
   ```
5. Start services:
   ```
   docker compose up -d default
   ```
6. Open `http://localhost:14142/register` in your browser
7. Create an account
8. Create a store and set default currency to ARRR
9. Go to Settings → Pirate → Modify → tick Enabled → Save

### Windows (PowerShell)
1. Install Docker from `https://www.docker.com` and start it
2. Open PowerShell
3. Create a working folder and download the compose file:
   ```
   New-Item -ItemType Directory -Force -Path "$HOME/pirate-btcpay" | Out-Null
   Set-Location "$HOME/pirate-btcpay"
   curl.exe -fsSL https://raw.githubusercontent.com/PirateNetwork/pirate-btcpay/main/docker/docker-compose.yml -o compose.yaml
   ```
4. Edit `compose.yaml` and set `fvk` and `starting_height` as step 4 in Windows CMD instructions
5. Start services:
   ```
   docker compose up -d default
   ```
6. Complete the same UI steps as steps 6 to 9 in Windows CMD instructions

### macOS (Terminal)
1. Install Docker Desktop for Mac and start it
2. In Terminal:
   ```
   mkdir -p "$HOME/pirate-btcpay" && cd "$HOME/pirate-btcpay"
   curl -fsSL https://raw.githubusercontent.com/PirateNetwork/pirate-btcpay/main/docker/docker-compose.yml -o compose.yaml
   ```
3. Edit `compose.yaml` and set `fvk` and `starting_height` as step 4 in Windows CMD instructions
4. Start services:
   ```
   docker compose up -d default
   ```
5. Complete the same UI steps as steps 6 to 9 in Windows CMD instructions`

### Linux (bash)
1. Install Docker Engine or Docker Desktop and ensure your user can run Docker
2. In a terminal:
   ```
   mkdir -p "$HOME/pirate-btcpay" && cd "$HOME/pirate-btcpay"
   curl -fsSL https://raw.githubusercontent.com/PirateNetwork/pirate-btcpay/main/docker/docker-compose.yml -o compose.yaml
   ```
3. Edit `compose.yaml` and set `fvk` and `starting_height` as step 4 in Windows CMD instructions
4. Start services:
   ```
   docker compose up -d default
   ```
5. Complete the same UI steps as steps 6 to 9 in Windows CMD instructions

## Configuration notes
- **Full Viewing Key**: Put your ARRR FVK in `fvk`
- **starting_height**: Use your wallet’s birthday height for fastest sync
- **Lightwalletd URL**: Set to `https://lightd1.pirate.black:443` (change via `lwd_url` if needed)

## Troubleshooting
- If the site isn’t reachable, ensure Docker is running and ports aren’t in use
- If walletd shows unhealthy, check logs and confirm `fvk` and `starting_height` are set correctly
