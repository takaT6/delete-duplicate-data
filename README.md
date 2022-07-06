重複データの全削除SQL文

よく忘れるのでメモ(SQLite3)

```bash
DELETE FROM 
WHERE (rowid) NOT IN
(
  SELECT ROWID rowid  FROM table_name
  (
    SELECT ROWID rowid FROM table_name
    GROUP BY id, ....
   )
);
```

指定したキーでグループ化し、それらのrowidたち以外に該当するデータを削除している
