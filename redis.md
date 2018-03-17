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

# List all keys in current keyspace
> keys *

# Remove all (key, value) pairs in current keyspace
> flushdb

# Set key to expire
> expire <key> <seconds>
# Check remaining time to live for a key
> ttl <key>

# Quit CLI
> quit
```

# Data Structures

## Nested Dict

```bash

# Nested hash
> hset <key0> <key1> <value>
> hget <key0> <key1>

# Set mulitple values
> hmset <key0> <key1> <value1> <key2> <value2>

# Get multiple values
> hmget <key0> <key1> <key2>

# Get all nested keys and values
> hgetall <key0>
```

## Linked List

```bash

# Insert at left
> lpush <key> <value>
> rpush <key> <value>

# Pop
> lpop <key>
> rpop <key>

# Slicing
> lrange <key> <idx> <pos>
```

# More Commands

https://redis.io/commands
