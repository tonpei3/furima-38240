# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

# テーブル設計

## users テーブル

| Column                           | Type   | Options                   |
| -------------------------------- | ------ | ------------------------- |
| nickname                         | string | null: false               |
| email                            | string | null: false, unique: true |
| password                         | string | null: false               |
| family_name                      | string | null: false               |
| first_name                       | string | null: false               |
| family_name(phonetic syllabary)  | string | null: false               |
| first_name(phonetic syllabary)   | string | null: false               |
| birthday                         | date   | null: false               |


### Association

- has_many :items
- has_many :purchase

##  itemsテーブル

| Column                   | Type         | Options                        |
| ------------------------ | ------------ | ------------------------------ |
| image                    | string       | null: false                    |
| product_name             | string       | null: false                    |
| product_description      | text         | null: false                    |
| seller_name              | string       | null: false                    |
| category                 | string       | null: false                    |
| commondity_condition     | text         | null: false                    |
| shipping_charges         | string       | null: false                    |
| shipping_orgin_region    | text         | null: false                    |
| approximate_delivery day | string       | null: false                    |
| price                    | string       | null: false                    |
| user_id                  | references   | null: false, foreign_key: true |

### Association

- belongs_to :users
- has_one :purchase

##  purchaseテーブル

| Column                   | Type         | Options                        |
| ------------------------ | ------------ | ------------------------------ |
| user_id                  | references   | null: false, foreign_key: true |
| item_id                  | references   | null: false, foreign_key: true |

### Association

- belongs_to :users
- belongs_to :items
- has_one :delivery

##  deliveryテーブル

| Column                   | Type         | Options                        |
| ------------------------ | ------------ | ------------------------------ |
| post_code                | string       | null: false                    |
| prefectures              | string       | null: false                    |
| municipalities           | string       | null: false                    |
| address                  | string       | null: false                    |
| building_name            | string       | null: false                    |
| phone_number             | string       | null: false                    |
| purchase_id              | references   | null: false, foreign_key: true |

### Association

- belongs_to :delivery





