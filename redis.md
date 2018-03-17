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

# Store and retrive values
> set <key> <value>
> get <key>

# Select a different key space (like a different db)
# Use same key to access different values in different key spaces
> select <key-space>

# List all keys in keyspace
> keys *

# Remove all values in db
> flushdb

# Quit CLI
> quit
```

# Commands

https://redis.io/commands
