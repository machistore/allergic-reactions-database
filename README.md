# allergic reactions database
This database created in [SQLite](https://www.sqlite.org) to record allergic reactions and meals.

アレルギー反応と食事を記録するための[SQLite](https://www.sqlite.org)で作成したデータベースです。

# DEMO  

Example of recording a database with "DB Browser for SQLite".[^1]  
[^1]:Please obtain and use "DB Browser for SQLite" by yourself.  
[Downloads](https://sqlitebrowser.org/dl/)

「DB Browser for SQLite」を使ってデータベースを記録した例です。[^2]  
[^2]:「DB Browser for SQLite」は、ご自身で入手しご利用ください。  
[Downloads](https://sqlitebrowser.org/dl/)

![demo1](https://user-images.githubusercontent.com/104885577/201289868-7d67943c-512f-49c0-a848-8e11b6fc638e.png)
![demo12](https://user-images.githubusercontent.com/104885577/201511933-321a1776-b6b0-471d-98a9-c6ee85fb2f4e.png)

# Features

We have made it as simple as possible to manage the presence or absence of allergy symptoms first.  

できるだけシンプルかつ、アレルギー症状の有無をまずは管理できるようにつくりました。

## table list

|name <br> テーブル名|Description <br> 説明|
|---|---|
|allergens|Allergy Causes <br> アレルギーの原因|
|diagnoses|diagnoses <br> 診断内容|
|diagnosticians|diagnostician <br> 診断した者|
|meals|What you ate <br> 食事内容|
|reactions|Allergic reactions <br> アレルギー反応の有無|
|sqlite_sequence|autoincrement of siagnostician <br> siagnosticianのautoincrement|


## table definitions  

* **allergens** table definition  

|cid|name|type|notnull|dflt_value|pk|hidden|
|---|---|---|---|---|---|---|
|0|id|INTEGER|1||1|0|
|1|allergen|TEXT|0||0|0|
|2|diagnostician_id|INTEGER|0||0|0|

* **diagnoses** definition  

|cid|name|type|notnull|dflt_value|pk|hidden|
|---|---|---|---|---|---|---|
|0|id|INTEGER|1||1|0|
|1|created_at|TEXT|0|datetime('now', 'localtime')|0|0|
|2|updated_at|TEXT|0|datetime('now', 'localtime')|0|0|
|3|reaction_id|INTEGER|0||0|0|
|4|allergen_id|INTEGER|0||0|0|
|5|meal_id|INTEGER|0||0|0|
|6|diagnostician_id|INTEGER|0||0|0|
|7|treatment|TEXT|0||0|0|

* **diagnosticians** table definition  

|cid|name|type|notnull|dflt_value|pk|hidden|
|---|---|---|---|---|---|---|
|0|id|INTEGER|1||1|0|
|1|diagnostician|TEXT|0||0|0|

* **meals** table definition  

|cid|name|type|notnull|dflt_value|pk|hidden|
|---|---|---|---|---|---|---|
|0|id|INTEGER|1||1|0|
|1|created_at|INTEGER|0|datetime('now', 'localtime')|0|0|
|2|url|TEXT|0||0|0|
|3|memo|TEXT|0||0|0|

* **reactions** table definition  

|cid|name|type|notnull|dflt_value|pk|hidden|
|---|---|---|---|---|---|---|
|0|id|INTEGER|1||1|0|
|1|created_at|TEXT|0|datetime('now', 'localtime')|0|0|
|2|reaction|INTEGER|0||0|
|3|symptom|TEXT|0||0|0|

# E-R diagram

![ER_diagram](https://user-images.githubusercontent.com/104885577/201518994-6e8504e0-0add-42e1-878f-b04d2706c423.png)


# Requerement

An environment that can operate SQLite is required.

SQLiteが動作する環境が必要です。

# Installation

Open the downloaded file with "DB Browser for SQLite". or use SQLite from a command prompt.  

ダウンロードしたファイルを"[DB Browser for SQLite](https://sqlitebrowser.org/)"で開く、  
もしくはコマンドプロンプトなどからSQLiteをお使いください。  

# Author

* Katsutoshi Machida
* Machi Store
* machi.mcd@gmail.com

# License

"marionette_palettes" is under [The MIT License](https://opensource.org/licenses/mit-license.php)(https://licenses.opensource.jp/MIT/MIT.html)

Copyright (c) 2022 Katsutoshi Machida
