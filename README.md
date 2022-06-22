# テーブル設計

## users テーブル

| Column             | Type       | Options                       |
| ------------------ | ---------- | ----------------------------- |
| nickname           | string     | null: false                   |
| email              | string     | null: false, unique: true     |
| encrypted_password | string     | null: false                   |
| first_name         | string     | null: false                   |
| family_name        | string     | null: false                   |
| first_name_kana    | string     | null: false                   |
| family_name_kana   | string     | null: false                   |
| birth              | date       | null: false                   |
| order              | references | null: false, foreign_key:true |

### Association

- has_one :item
- has_many :comments

## items テーブル

| Column           | Type       | Options                       |
| ---------------- | ---------- | ----------------------------- |
| name             | string     | null: false                   |
| description      | text       | null: false                   |
| price            | integer    | null: false                   |
| category_id      | intenger   | null: false                   |
| condition_id     | intenger   | null: false                   |
| fee_id           | intenger   | null: false                   |
| area_id          | intenger   | null: false                   |
| ship_day_id      | intenger   | null: false                   |
| user             | references | null: false, foreign_key:true |
| order            | references | null: false, foreign_key:true |

### Association

- belongs_to :user
- belongs_to :order
- has_many :comments


## comments テーブル

| Column    | Type       | Options                        |
| --------- | ---------- | ------------------------------ |
| message   | text       | null: false                    |
| user      | references | null: false, foreign_key: true |
| item      | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :item

## orders テーブル

| Column    | Type       | Options                        |
| --------- | ---------- | ------------------------------ |
| user      | references | null: false, foreign_key: true |
| item      | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :item
- has_one:address

## addresses テーブル

| Column          | Type       | Options                      |
| --------------- | ---------- | ---------------------------- |
| postal_code     | string     | null: false                  |
| area_id         | integer    | null: false                  |
| city            | string     | null: false                  |
| address_line    | string     | null: false                  |
| building_number | string     |                              |
| phone_number    | string     | null: false                  |
| order           | references | null: false,foreign_key:true |

### Association

- belongs_to :order