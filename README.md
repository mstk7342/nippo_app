# テーブル設計

## users テーブル

| Column             | Type   | Options     |
| ------------------ | ------ | ----------- |
| nickname           | string | null: false |
| email              | string | null: false |
| encrypted_password | string | null: false |

### Association

- has_many :companies
- has_many :staffs

## companies テーブル

| Column                       | Type    | Options                        |
| company_name                 | string  | null: false                    |
| company_name_kana            | string  | null: false                    |
| phone_number                 | string  | null: false                    |
| fax_number                   | string  | null: false                    |
| postal_code                  | string  | null: false                    |
| prefecture_id                | integer | null: false                    |
| city                         | string  | null: false                    |
| address                      | string  | null: false                    |
| building_name                | string  | null: false                    |
| user_id                      | integer | null: false, foreign_key: true |
| staff_id                     | integer | null: false, foreign_key: true |

### Association

- belongs_to :user
- has_many :staffs

## staffs テーブル

| Column              | Type         | Options                        |
| ------------------- | ------------ | ------------------------------ |
| staff_name          | string       | null: false                    |
| staff_name_kana     | string       | null: false                    |
| department          | string       | null: false                    |
| user_id             | integer      | null: false, foreign_key: true |
| company_id          | integer      | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :company

## opportunities テーブル

| Column              | Type         | Options                        |
| ------------------- | ------------ | ------------------------------ |
| department          | string       | null: false                    |
| user_id             | integer      | null: false, foreign_key: true |
| staff_id            | integer      | null: false, foreign_key: true |
| company_id          | integer      | null: false, foreign_key: true |

### Association

- has_many :staff
- belongs_to :user
- belongs_to :company

