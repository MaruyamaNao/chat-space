
<!-- messagesテーブル -->
|Column|Type|Options|
|------|----|-------|
|body|text|
|image|string|
|user_id|integer|
|group_id|integer|
<!-- アソシエーション -->
belongs_to : group
belongs_to : user

<!-- usersテーブル -->
|Column|Type|Options|
|------|----|-------|
|user_name|string|name, null: false|
|user_email|string|add_index : unique: true|
<!-- アソシエーション -->
has_many : groups_users
has_many : groups, through: :groups_users
has_many : messages


<!-- groupsテーブル -->
|Column|Type|Options|
|------|----|-------|
|name_group|string|name, null: false|
<!-- アソシエーション -->
has_many : groups_users
has_many : users, through: :groups_users
has_many : messages


<!-- groups_usersテーブル -->
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
<!-- アソシエーション -->
belongs_to : group
belongs_to : user