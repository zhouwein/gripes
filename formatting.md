## Continuation indents for call arguments and collections

For call arguments and collections that span multiple lines, consider putting the first element on a new line. This causes the items to be indented less overall, which saves horizontal space (usually limited to 80-120 chars) and avoids excessive indentation.

Instead of
```
xyzzy('long_string_constant1',
      'long_string_constant2')

attrs = [e.attr for e in
         items]

ingredients = ['green',
               'eggs',
```
consider
```
xyzzy(
    'long_string_constant1',
    'long_string_constant2'
)

attrs = [
    e.attr 
    for e in items
]

ingredients = [
    'green',
    'eggs',
]
```
As you can see, the longer the function/variable names are, the more the items are indented. Putting the items on a new line always uses the same amount of indent.

## SQL formatting example

```
WITH cte AS (
  SELECT
    *
  FROM table2
  WEHRE source = 123
), cte2 AS (
  [...]
)
SELECT DISTINCT ON (item1, item2)
  t1.item1,
  t1.item2,
  c.name,
  SUM(c.amount) AS amount_sum,
FROM table1 t1
LEFT JOIN cte c
  ON table1.stuff_id = table2.id
INNER JOIN (
  SELECT
    *
  FROM table3
  WHERE category = 'stuff'
) AS subquery
  ON subquery.user = t1.user
GROUP BY t1.item1, t1.item2, c.name
HAVING SUM(c.amount) > 0;
```
