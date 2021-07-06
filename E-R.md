@startuml
entity "顧客マスタ" as customer <m_customers>
<<M,MASTER_MARK_COLOR>>{
 +customer_code[PK]
 --
 pass
 name
 address
 tel
 mail
 der_flag
 reg_date
}

entity "購入テーブル" as table <d_purchase>
<<T,MASTER_MARK_COLOR>>{
+order_id[PK]
--
+customer_code[FK]
purchase_date
total_price
}

entity "購入詳細テーブル" as table <d_purchase_date>
<<T,MASTER_MARK_COLOR>>{
+order_id[PK]
+detail_id[PK]
--
+item_code[FK]
price
num
}

entity "商品マスタ" as customer <m_items>
<<M,MASTER_MARK_COLOR>>{
+item_code[PK]
--
item_name
price
+category_id[FK]
image
detail
del_flag
reg_date
}

entity "カテゴリマスタ" as customer <m_category>
<<M,MASTER_MARK_COLOR>>{
+category_ic[PK]
--
name
reg_date
}

m_customers |o-o{ d_purchase 
d_purchase ||-{ d_purchase_date 
d_purchase_date }--|| m_items 
m_category ||-o{ m_items 
