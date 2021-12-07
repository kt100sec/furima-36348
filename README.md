#テーブル設計

## users テーブル

| Column             | Type   | Options                   |
| ------------------ | ------ | ------------------------- |
| nickname           | string | null: false               |
| email              | string | null: false, unique: true |
| encrypted_password | string | null: false               |
| first_name         | string | null: false               |
| family_name        | string | null: false               |
| first_name_kana    | string | null: false               |
| family_name_kana   | string | null: false               |
| birth_date         | date   | null: false               |

## Association

- has_many :items
- has_many :payment_cards

## items テーブル

| Column                 | Type       | Options                        |
| ---------------------- | ---------- | ------------------------------ |
| name                   | string     | null: false                    |
| text                   | text       | null: false                    |
| category_id            | integer    | null: false, default: 0        |
| status_id              | integer    | null: false, default: 0        |
| shipping_fee_burden_id | integer    | null: false, default: 0        |
| prefecture_id          | integer    | null: false, default: 0        |
| dalivery_day_id        | integer    | null: false, default: 0        |
| price                  | integer    | null: false                    |
| user_id                | references | null: false, foreign_key: true |

## Association

- belongs_to :users

 ## address テーブル

| Column           | Type       | Options                        |
| ---------------- | ---------- | ------------------------------ |
| post_number      | string     | null: false                    |
| prefecture_id    | integer    | null: false, default: 0        |
| city             | string     | null: false                    |
| house_number     | integer    | null: false                    |
| building_name    | string     |                                |
| phone_number     | string     |                                |
| user_id          | references | null: false, foreign_key: true |

## Association

- belongs_to :users
- belongs_to :payment_cards

## payment_cards テーブル

| Column      | Type       | Options                        |
| ----------- | ---------- | ------------------------------ |
| user_id     | references | null: false, foreign_key: true |
| customer_id | string     | null: false                    |

- belongs_to :users
- has_one :address