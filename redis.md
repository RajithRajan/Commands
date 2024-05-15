# Connect
## Syntax
redis-cli -u redis://host:port
redis-cli -u redis://username:password@host:port

## Examples
redis-cli
redis-cli -u redis://localhost:6379
redis-cli -u redis://myuser:mypassword@localhost:6379

# Strings/Numbers
## SET
set value to a key
### Syntax
SET key value
### Examples
SET myKey "Hello"

## GET
get value of a key
### Syntax
GET key
### Examples
GET myKey

## MGET
get value of multiple key
### Syntax
MGET key [key ...]
### Examples
MGET myKey nonExistentKey

## INCR
increment the counter 
### Syntax
INCR key
### Examples
INCR myCounter

# Generic
## KEYS
Returns all keys matching pattern
### Syntax
KEYS pattern
### Examples
KEYS my*
KEYS *

Checks if one or more keys exist



# Reference
https://redis.io/learn/howtos/quick-start/cheat-sheet
