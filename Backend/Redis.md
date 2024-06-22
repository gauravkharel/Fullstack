in-memory database system
the open source, in-memory data store used by millions of developers as a database , cache, streaming engine and message broker

#### redis data store structure
redis list (static and queue)
```
lpush(left push) and rpush (right push)

+_____pushing data___+
left                  right

```

```
data stored in db

<entity>:<id> <value>
set user:1 X
set user:2 Y
set user:3 Z
```

#### most used redis commands
```
set msg:3 how_are_you
mget user:2 user:1 user:3
multiple get and, set => mget and sget

```

docker image of redis: port => 6379
