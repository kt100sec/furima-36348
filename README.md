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

- has_many :purchases
- has_many :items

## items テーブル

| Column                 | Type       | Options                        |
| ---------------------- | ---------- | ------------------------------ |
| name                   | string     | null: false                    |
| text                   | text       | null: false                    |
| category_id            | integer    | null: false, default: 0        |
| status_id              | integer    | null: false, default: 0        |
| shipping_fee_burden_id | integer    | null: false, default: 0        |
| prefecture_id          | integer    | null: false, default: 0        |
| delivery_day_id        | integer    | null: false, default: 0        |
| price                  | integer    | null: false                    |
| user                   | references | null: false, foreign_key: true |

## Association

- has_one :purchase
- belongs_to :user

## purchases テーブル

| Column | Type       | Options                        |
| ------ | ---------- | ------------------------------ |
| user   | references | null: false, foreign_key: true |
| item   | references | null: false, foreign_key: true |

## Association

- belongs_to :user
- belongs_to :item
- has_one :address

## addresses テーブル

| Column           | Type       | Options                        |
| ---------------- | ---------- | ------------------------------ |
| post_number      | string     | null: false                    |
| prefecture_id    | integer    | null: false, default: 0        |
| city             | string     | null: false                    |
| house_number     | string     | null: false                    |
| building_name    | string     |                                |
| phone_number     | string     | null: false                    |
| purchase         | references | null: false, foreign_key: true |

## Association

- belongs_to :purchase