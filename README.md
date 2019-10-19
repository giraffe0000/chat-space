# DB設計

### usersテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|email|string|null: false, unique: true| 
|password|string|null: false, unique: true| 

### Association
- has_many :groups, through: :groups_users
- has_many :messages
- has_many :groups_users

###  groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user

### groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|

### Association
- has_many :users, through: :groups_users
- has_many :messages
- has_many :groups_users

### messagesテーブル
|Column|Type|Options|
|------|----|-------|
|comments|text|null: false|
|image|string|null: false|
|user_id|integer|null: false|
|group_id|integer|null: false|


### Association
- belongs_to :group
- belongs_to :user