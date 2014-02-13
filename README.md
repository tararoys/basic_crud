Basic CRUD
==========

Giant Tutorial for Basic Sinatra Crud Apps

#Whiteboard
##UserStories
##Wireframe
##Schema
Use the [SQL Designer](https://socrates.devbootcamp.com/sql.html) to design your schema. 

#Setup
##Skeleton
Use the [Sinatra Skeleton](https://github.com/tararoys/DBC_Sinatra_Skeleton)

#Structure
##Migrations

###CreateTable 
  
```ruby
  class CreateThings < ActiveRecord::Migration
    def change
      create_table :things do |t|
        t.integer :stuff_id, :null => false
  
        t.string :name, :null => false
        t.string :place, :null => false
  
        t.datetime :starts_at, :null => false
        t.datetime :ends_at, :null => false
  
        t.timestamps
      end
  
      add_index :things, :stuff_id  #I don't know what this is
    end
  end
```

##Models
##Views
##Controllers

#Agile
##Workflow
###Switching
###Git
###Testing




