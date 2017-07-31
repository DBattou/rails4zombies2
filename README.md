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
