# rails4zombies2

Creating a twitter for zombies to help them stay up to date. http://railsforzombiestwo.codeschool.com/

This is my first attempt to create a Ruby on Rails application

I will try to keep track of all the steps i made :


```
rails new ZombieTweets
rails g scaffold tweet status:string zombie_id:integer
```

```ruby
#Write the migration manually which creates the tweets table in the database with the status string column and zombie_id integer column
class CreateTweets < ActiveRecord::Migration
  def change
    create_table :tweets do |t|
      t.string :status
      t.integer :zombie_id
    
      t.timestamps
    end
  end
end
```
```
rake db:migrate
rails s
rails g migration AddPrivacyToTweets private:boolean
```


```ruby
#Create migration by hand that adds two fields to the tweets table: a location string field which has a limit of 30 and a boolean field called show_location which defaults to false.
class AddLocationToTweets < ActiveRecord::Migration
  def change
    add_column :tweets, :location, :string, limit: 30
    add_column :tweets, :show_location, :boolean, default: false
  end
end
```

```
rake db:rollback
```

```ruby
# Add category_name column and rename the status column from status to message 
class AddLocationToTweets < ActiveRecord::Migration
  def change
    add_column :tweets, :location, :string, limit: 30
    add_column :tweets, :show_location, :boolean, default: false
    add_column :tweets, :category_name, :string
    rename_column :tweets, :status, :message
  end 
end
```

```ruby
# On second thought, that category_name string column was a bad idea. Write a migration to remove the category_name column.
class RemoveCategoryNameFromTweets < ActiveRecord::Migration
  def up
    remove_column :tweets, :category_name
  end

  def down
    add_column :tweets, :category_name, :string
  end
end
```

```
# Create db, load schema & seed
rake db:setup
# Enter rails console
rails console
# Plays with tweets
Tweet.create(status: "coucou", zombie_id: 3)
```

