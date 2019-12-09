# README
# chat-space DB設計

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|email|string|null: false|
|password|string|null: false|
|nickname|string|null: false, index: true|
### Association
- has_many :friends
- has_many :groups
- has_may :messages

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|other_user|string|null: false|
|user_id|integer|null: false, foreign_key: true|
|friend_id|null: false, foreign_key: true|
### Association
- has_many :users
- has_many :friends
- has_many :messages

## messagesテーブル
|image|text||
|text|text|null: false|
|user_id|integer|null: false, foreign_key: true|
|friend_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group
- has_many :friends