# allergic reactions database

This is a simple database template for recording allergic reactions and meals.  
The "*.db" file was created in [SQLite](https://www.sqlite.org).

アレルギー反応と食事を記録するためのシンプルなデータベースの雛形です。  
[SQLite](https://www.sqlite.org)で「*.db」ファイルを作成しています。

# DEMO  

Example of recording a database with "DB Browser for SQLite".[^1]  
[^1]:Please obtain and use "DB Browser for SQLite" by yourself.  
[Downloads](https://sqlitebrowser.org/dl/)

「DB Browser for SQLite」を使ってデータベースを記録した例です。[^2]  
[^2]:「DB Browser for SQLite」は、ご自身で入手しご利用ください。  
[Downloads](https://sqlitebrowser.org/dl/)

![demo12](https://user-images.githubusercontent.com/104885577/201511933-321a1776-b6b0-471d-98a9-c6ee85fb2f4e.png)

# Features

We have made it as simple as possible to manage the presence or absence of allergy symptoms first.  

できるだけシンプルかつ、アレルギー症状の有無をまずは管理できるようにつくりました。

## table list テーブルリスト

|name <br> テーブル名|Description <br> 説明|
|---|---|
|allergens|Allergy Causes <br> アレルギーの原因|
|diagnoses|diagnoses <br> 診断内容|
|diagnosticians|diagnostician <br> 診断した者|
|meals|What you ate <br> 食事内容|
|reactions|Allergic reactions <br> アレルギー反応の有無|
|sqlite_sequence|autoincrement of siagnostician <br> siagnosticianのautoincrement|


## table configuration テーブルの構成

### **allergens** table configuration  アレルギー原の食材テーブル

|cid|name|type|notnull|dflt_value|pk|hidden|
|---|---|---|---|---|---|---|
|0|id|INTEGER|1||1|0|
|1|allergen|TEXT|0||0|0|
|2|diagnostician_id|INTEGER|0||0|0|

0. id(Primary key)
1. allergen
    + Foods to which you are allergic (e.g., cherries)
    + アレルギーの原因となる食材(例:さくらんぼ)
1. diagnostician_id
    + Diagnosed (see diagnostician table)
    + 診断した者(diagnostician table 参照)


### **diagnoses** table configuration アレルギーの診断テーブル

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

0. id(Primary key)
1. created_at
    + Date and time the data was created(auto-date).
    + データをつくった日時(自動作成)
1. updated_at
    + Date and time the data was updated(auto-date).
    + データを更新した日時(自動作成)
1. reaction_id
    + Allergic reaction (yes or no, see reaction table).
    + アレルギー反応(あり or なし,reaction table 参照)
1. allergen_id
    + Allergic reaction (yes or no, see reaction table).
    + アレルゲンの名前(allergen table 参照)
1. meal_id
    + Meal table (see meal table).
    + 食事内容(meal table 参照)
1. deagnostician_id
    + Persons diagnosed (see deagnostician table).
    + 診断した者(deagnostician table 参照)
1. treatment
    + Notes on treatment methods, etc.
    + 治療方法などのメモ


### **diagnosticians** table configuration 診断者テーブル

|cid|name|type|notnull|dflt_value|pk|hidden|
|---|---|---|---|---|---|---|
|0|id|INTEGER|1||1|0|
|1|diagnostician|TEXT|0||0|0|

0. id(Primary key)
1. diagnostician
    + Person who made the diagnosis (e.g., the person himself/herself, Doctor xx)
    + 診断した者(例:本人,xx医師)

### **meals** table configuration 食事テーブル

|cid|name|type|notnull|dflt_value|pk|hidden|
|---|---|---|---|---|---|---|
|0|id|INTEGER|1||1|0|
|1|created_at|INTEGER|0|datetime('now', 'localtime')|0|0|
|2|url|TEXT|0||0|0|
|3|memo|TEXT|0||0|0|

0. id
    * id(Primary key)
1. created_at
    * The date the data was created(auto-date).
    * データを作成した日付(自動作成)
1. url
    * This is a path of images taken of the meal.
        * It is assumed that the contents of the meal will be recorded using a service that manages images taken with a smartphone or other device in the cloud and records URLs and other links.
    * 食事の内容を撮影した画像のパス(URL)
        * 食事の内容はスマートフォンなどで撮影した画像をクラウドで管理するサービスなどを利用して、
        URLなどリンク先を記録するように想定しています。
1. memo
    * A brief note of the meal.
    * 食事の内容の簡単なメモ書き


### **reactions** table configuration アレルギー反応テーブル

|cid|name|type|notnull|dflt_value|pk|hidden|
|---|---|---|---|---|---|---|
|0|id|INTEGER|1||1|0|
|1|created_at|TEXT|0|datetime('now', 'localtime')|0|0|
|2|reaction|INTEGER|0||0|
|3|symptom|TEXT|0||0|0|

0. id
    * id(Primary key)
1. created_at
    * The date the data was created(auto-date).
    * データを作成した日付(自動作成)
1. reaction
    * Presence of allergic symptoms (None: 0, Yes: 1)
    * アレルギー症状の有無(なし:0、あり:1)
1. symptom
    * Description of allergy symptoms (e.g., nausea)
    * アレルギー症状の内容(例:吐き気)

# E-R diagram

![ER_diagram](https://user-images.githubusercontent.com/104885577/201518994-6e8504e0-0add-42e1-878f-b04d2706c423.png)


# Requerement

An environment that can operate SQLite is required.

SQLiteが動作する環境が必要です。

# Installation

Unzip the zip file downloaded from "[Release](https://github.com/machistore/allergic-reactions-database/releases)" and open the "allergic_reactions.db" file in the "allergic-reactions-database-0.1.0" folder with "[DB Browser for SQLite](https://sqlitebrowser.org/)".  
Or, use SQLite from a command prompt. 

「[Release](https://github.com/machistore/allergic-reactions-database/releases)」からダウンロードしたzipファイルを解凍し、「allergic-reactions-database-0.1.0」フォルダの中の「allergic_reactions.db」ファイルを"[DB Browser for SQLite](https://sqlitebrowser.org/)"で開く、  
もしくはコマンドプロンプトなどからSQLiteをお使いください。  

# Author

* Katsutoshi Machida
* Machi Store
* machi.mcd@gmail.com

# License

"marionette_palettes" is under [The MIT License](https://opensource.org/licenses/mit-license.php)(https://licenses.opensource.jp/MIT/MIT.html)

Copyright (c) 2022 Katsutoshi Machida
