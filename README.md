## 1. usersテーブル

|Column|Type|Options|
|------|----|-------|
|nickname|string|null: false, unique: true|
|email|string|null: false, unique: true|
|password|string|null: false|
|last_name|string|null: false|
|first_name|string|null: false|
|last_name_kana|string|null: false|
|first_name_kana|string|null: false|
|birthdate|date|null: false|
|tel|string|null: false, unique: true|
|profile|text||
|icon|text||

### Association
- has_many :products
- has_many :likes
- has_many :comments
- has_one :address
- has_one :card
- has_one :buyer
- has_one :seller

***

## 2. addressesテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|references|foreign_key: true|
|postal_code|int|null: false|
|prefecture|int|enum, null: false|
|city|string|null: false|
|street|string|null: false|
|building|string|null: false|

### Association
- belongs_to :user

***

## 3. cardsテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|references|foreign_key: true|
|number|int|null: false|
|expiration|date|null: false|
|security_code|int|null: false|

### Association
- belongs_to :user

***

## 4. producsテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|references|foreign_key: true|
|large_category_id|references|foreign_key: true|
|middle_category_id|references|foreign_key: true|
|small_category_id|references|foreign_key: true|
|brand_id|references|foreign_key: true|
|size|int|enum|
|condition|int|enum|
|name|string|null: false|
|description|text|null: false|
|shipping_charge|int|enum, null: false|
|shipping_method|int|enum, null: false|
|shipping_prefecture|int|enum, null: false|
|shipping_days|int|enum, null: false|
|price|int|null: false|
|progress|int|enum, null; false|

### Association
- belongs_to :user
- belongs_to :large_category
- belongs_to :middle_category
- belongs_to :small_category
- belongs_to :brand
- has_many :photos
- has_many :likes
- has_many :comments
- has_one :buyer
- has_one :seller

***

## 5. photosテーブル
|Column|Type|Options|
|------|----|-------|
|product_id|references|foreign_key: true|
|image|text|null: false|
### Association
- belongs_to :product

***

## 6. large_categoriesテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
###Association
- has_many :products
- has_many :middle_categories

***

## 7. middle_categoriesテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|large_categories_id|references|foreign_key: true|
###Association
- belongs_to :large_category
- has_many :small_categories
- has_many :products

***


## 8. small_categoriesテーブル
|Column|Type|Options|
|------|----|-------|
|name|string||
|middle_categories_id|references|foreign_key: true|
###Association
- belongs_to :middle_category
- has_many :brands_categories
- has_many :brands, through: :brands_categories
- has_many :products

***

## 9. brands_categoriesテーブル

|Column|Type|Options|
|------|----|-------|
|brand_id|references|foreign_key: true|
|category_id|references|foreign_key: true|

### Association
- belongs_to :small_category
- belongs_to :brand

***

## 10. brandsテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false|

### Association
- has_many :products
- has_many :brands_categories
- has_many :small_categories, through: :brands_categories

***

## 11. buyersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|references|foreign_key: true|
|product_id|references|foreign_key: true|
|evaluate|int|enum, null: false|
|comment|text|null: false|

### Association
- belongs_to :user
- belongs_to :product

***

## 12. sellersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|references|foreign_key: true|
|product_id|references|foreign_key: true|
|evaluate|int|enum, null: false|
|comment|text|null: false|

### Association
- belongs_to :user
- belongs_to :product

***

## 13. likesテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|references|foreign_key: true|
|product_id|references|foreign_key: true|

### Association
- belongs_to :user
- belongs_to :product

***

## 14. commentsテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|references|foreign_key: true|
|product_id|references|foreign_key: true|
|comment|text|null: false|

### Association
- belongs_to :user
- belongs_to :product

***