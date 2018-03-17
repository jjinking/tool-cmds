# Intro

Remote dictionary server

Default port: 6379

Key value store only - no secondary index

# Install

```bash
# Mac
brew install redis
```

# Running

```bash
# Start redis
redis-server
```

Creates a file dump.rdb

# CLI

```bash
# Start
redis-cli
redis-cli -h <host> -p <port>

# Check connection
> ping # returns PONG

# Authenticate
> auth <password>

# Quit CLI
> quit

# Commands

https://redis.io/commands
```