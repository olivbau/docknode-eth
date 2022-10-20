# Docknode ETH

## Metrics

* `https://yourdomain.com/executionnode/metrics`
* `https://yourdomain.com/beaconnode/metrics`

## Install 

1. Clone the repository and
```bash
git clone https://github.com/olivbau/docknode-eth.git
cd docknode-eth
```

2. Configure jwt.hex
```bash
openssl rand -hex 32 | tr -d "\n" > "jwt.hex"
```

3. Configure env vars
```bash
cp .env.example .env

# Generate users passwords
docker run --rm caddy:2-alpine caddy hash-password --plaintext 'password'

# Set users and passwords
# Set the hostname
nano .env
```

4. Setup UFW
```bash
ufw allow ssh
ufw deny 8545
ufw deny 3500
ufw deny 8551
ufw deny 4000
ufw enable
```

4. Run
```bash
docker compose up -d
docker logs -f beaconnode
docker logs -f executionnode
```