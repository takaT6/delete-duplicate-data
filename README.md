重複データの全削除SQL文

よく忘れるのでメモ

(SQLite)
DELETE FROM 
WHERE (rowid) NOT IN
(
  SELECT ROWID rowid  FROM table_name
  (
    SELECT ROWID rowid FROM table_name
    GROUP BY id, ....
   )
);

rowid以外で重複しているデータを削除している
