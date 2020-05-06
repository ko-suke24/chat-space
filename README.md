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

## usersテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false, index: true|
|email|string|null: false, unique: true|

### Association
- has_many :groups, through: group_users
- has_many :group_users
- has_many :messages


## groupsテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false, unique: true|

### Association
- has_many :users, through: group_users
- has_many :group_users
- has_many :messages


## group_userテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, index: true, foreign_key: true|
|group_id|references|null: false, index: true, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :group


## messagesテーブル

|Column|Type|Options|
|------|----|-------|
|content|text|null: false|
|image|string|      |
|user_id|integer|null: false, index: true, foreign_key: true|
|group_id|integer|null: false, index: true, foreign_key: true|


### Association
- belongs_to :user
- belongs_to :group