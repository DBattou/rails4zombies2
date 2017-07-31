# rails4zombies2

Creating a twitter for zombies, to help them stay up to date. http://railsforzombiestwo.codeschool.com/

This is my first attempt to create an Ruby on Rails application

I will try to keep track of all the steps i made


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
