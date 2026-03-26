# List functions

These are all the functions defined in the `list` module:

| function | parameters       | description                                     |
| -------- | ---------------- | ----------------------------------------------- |
| has      | `value` `arr`    | Returns true if `arr` contains `value`          |
| has_any  | `values` `arr`   | Returns true if `arr` contains any value from `values` |
| has_all  | `values` `arr`   | Returns true if `arr` contains all values from `values` |

## Example

```prql
prql target:sql.duckdb

from employees
derive {
  has_title = ([title, "CEO"] | list.has title),
  has_any_role = ([title, country] | list.has_any [country, "CEO"]),
}
```

## Dialect support

`list` functions currently require an explicit SQL dialect.

The currently supported dialects are:

- ClickHouse
- DuckDB
- BigQuery
- Postgres

For unsupported dialects, PRQL returns an error during compilation.
