# MySQL 8.0 コンテナの Docker Compose ファイル  
MySQL 8.0 の Docker コンテナです。  
  
DB 作成と初期データ投入をバッチ実行します。  
  
## MySQL Sample Database Schema
MySQLのサンプルデータベーススキーマは、以下のテーブルで構成されています。  
  
### クラシック模型メーカ  
- **Customers:** 顧客データ  
- **Products:** 商品データ  
- **ProductCategories:** 商品ラインナップを識別するカテゴリのリスト  
- **Orders:** 顧客が行った注文データ  
- **OrderDetails:** 各注文の販売品目データ  
- **Payments:** 顧客が行った支払データ  
- **Employees:** すべての従業員データと、誰が誰に報告するかなどの組織構造  
- **Offices:** 営業所に関するデータ  

![ER図](https://raw.githubusercontent.com/fs5013-furi-sutao/fsedu.mysql.8.0/master/images/classicmodels_er.png)

## 備考  
.env ファイルには Windows ホスト向けにパスが変換できるよう、環境変数を設定しています。  
