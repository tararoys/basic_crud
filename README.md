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

See Railsguides [Creating a Migration](http://guides.rubyonrails.org/migrations.html#writing-a-migration) for further info. 

### RakeGenerateMigration

Running the command 

    rake generate:migration NAME=create_things

will create a migration file in the db/migrations folder. It will also create an empty migration in that file that looks like this: 

    class #{name} < ActiveRecord::Migration
        def change
        end
    end


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

###AddColumn
```ruby
  class AddPartNumberToProducts < ActiveRecord::Migration
    def change
      add_column :things, :widgit, :string #add_column tablename columnname columntype
    end
  end
```

###RakeDBYolo

    rake db:drop
    rake db:create
    rake db:migrate
    rake db:seed

Theoretically, it is better to add migrations if you screw up the database.  For now, it's easier to drop the database, rewrite the bad migration, and create the database again.


##Models

##RakeGenerateModel

    rake generate:model NAME=User

creates a blank model.

```ruby
    class #{model_name} < ActiveRecord::Base
        # Remember to create a migration!
    end
```


##Views
##Controllers

#Agile
##Workflow
###Switching
###Git
###Testing




