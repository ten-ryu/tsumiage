# README

# テーブル設計

## users テーブル

| Column          | Type   | Options     |
| --------------- | ------ | ----------- |
| nickname        | string | null: false |
| email           | string | null: false |
| password        | string | null: false |
| introduction    | text   | null: false |

### Association

- has_many :comments
- has_many :expressions
- has_many :objectives
- has_many :prides
- has_many :likes

## connections テーブル

| Column       | Type    | Options     |
| -------------| ------- | ------------|
| followed_id  | integer | null: false |
| follower_id  | integer | null: false |

### Association

- belongs_to :item
- belongs_to :user
- has_one :address

## comments テーブル

| Column          | Type       | Options                        |
| --------------- | ---------- | ------------------------------ |
| user_id         | integer    | null: false, foreign_key:true  |
| prides_id       | integer    | null: false                    |
| detail          | text       | null: false                    |
 

### Association

- belongs_to :user
- belongs_to :pride

## expressions テーブル

| Column          | Type       | Options                        |
| --------------- | ---------- | ------------------------------ |
| user_id         | integer    | null: false, foreign_key: true |
| objective_id    | integer    | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :objective

## objectives テーブル

| Column      | Type       | Options                        |
| ------------| ---------- | ------------------------------ |
| user_id     | integer    | null: false, foreign_key: true |
| title       | string     | null: false                    |

### Association

- has_one :expression
- belongs_to :user

## prides テーブル

| Column          | Type       | Options                        |
| --------------- | ---------- | ------------------------------ |
| user_id         | integer    | null: false, foreign_key:true  |
| title           | string     | null: false                    |
| detail          | text       | null: false                    |

### Association

- belongs_to :user
- has_many :comments
- has_many :likes

## likes テーブル

| Column          | Type       | Options                        |
| --------------- | ---------- | ------------------------------ |
| user_id         | integer    | null: false, foreign_key: true |
| prides_id       | integer    | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :pride