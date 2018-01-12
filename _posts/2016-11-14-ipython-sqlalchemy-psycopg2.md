---
layout: post
title: Using iPython, sqlalchemy, psycopg2 to connect to a Postgresql DB
---

I recently had to determine how to connect to a Postgresql DB using
python:

I used sqlalchemy create_engine API to send over the connection
paramters. This is readily documented on the [sqlalchemny
documentation] and on this [stack overflow question] page.

However, my database required connection to is using an SSL
connection. Stack overflow already provides an answer about how to
connect to a MySQL DB using SSL client connection [here][1]. However,
there is no ready-made answer about how to accomplish this for a
Postgres DB.

They key here is to understand that sqlalchemy and psycopg2 will
essentially pass connection parameters to the underlying python DB 2.0
compatible api.

We need to find out the parameters required to pass the SSL client
keys to the DB driver. The paramters for Postgresql are part of the
[postgres documentation] and need to be passed as key value pairs
within the optional python dict that contains additional parameters.

Here is my code to connect to the DB:

```
from sqlalchemy import create_engine

def db_connect():
    db_connect_string = "postgresql+psycopg2://{user}:{passwd}@{server}:{port}/{db}".format(user="foo", passwd="bar",
    server="server.example.com", db="baz", port="0000")
    ssl_args = {
        "sslmode": "require",
        "sslcert": "/home/user/pgsql-client.crt",
        "sslkey": "/home/user/pgsql-client.key",
        "sslrootcert": "/home/user/root.crt",
    }
    return create_engine(db_connect_string, connect_args=ssl_args)
```

The `connect_args` can contain any additional arguments that you might
require to be passed to the postgresql DB as long as their are
recognized by your [postgres documentation]. For my case, they contain
the `ssqlmode`, `sslcert`, `sslkey` and `sslrootcert` keys that were
required to establish my connection.


[sqlalchemny documentation]: http://docs.sqlalchemy.org/en/latest/core/engines.html#postgresql
[postgres documentation]: https://www.postgresql.org/docs/current/static/libpq-connect.html#LIBPQ-CONNSTRING
[stack overflow question]: http://stackoverflow.com/questions/28228241/how-to-connect-to-a-remote-postgresql-database-with-python
[1]: http://stackoverflow.com/questions/8014781/how-to-make-mysql-connection-that-requires-ca-cert-with-sqlalchemy-or-sqlobject
