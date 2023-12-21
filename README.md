# Simple example of using PostgreSQL exporters

### [postgres_exporter](https://github.com/prometheus-community/postgres_exporter)

A PostgreSQL metric exporter for Prometheus

:::tip
Used for DB metrics and config info (system monitoring)
:::



### [sql_exporter](https://github.com/burningalchemist/sql_exporter/)
Database agnostic SQL exporter for Prometheus - for SQL Queries

:::tip
Used to create SQL queries to the database, receive and output business metrics (to display real-time data from the database in Grafana)
:::


### Run

```
docker compose up -d
```

### Import demo data for testing

```
docker compose exec db bash
psql -U pguser -d netflix < /tmp/netflix.sql 
```

Find the directors with the most movies in the database:
``` 
SELECT 
    director,
    COUNT(*) AS "Number of Movies"
FROM 
    netflix_shows
WHERE 
    type = 'Movie' and director is not null
GROUP BY 
    director
ORDER BY 
    "Number of Movies" DESC
LIMIT 5;
```