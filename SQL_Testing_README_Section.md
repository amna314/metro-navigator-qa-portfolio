## SQL Testing for Metro Navigator

I performed database validation using SQL queries against the metro.db database (tested on a copy, metro_test.db).

Most checks passed, such as duplicate records, orphan foreign keys, missing coordinates, and sequence validation.

However, I found one defect: RT04 existed in the routes table but had no station mapping in route_stations. Reported as a bug (severity: High).

Full queries and results are documented in SQL_Testing_Results.xlsx.

**Tool used:** DB Browser for SQLite
