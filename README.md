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

###RakeGenerateModel

    rake generate:model NAME=User

creates a blank model.

```ruby
    class #{model_name} < ActiveRecord::Base
        # Remember to create a migration!
    end
```

###ModelAssociations 



####BasicModelassociations

```ruby
class Survey < ActiveRecord::Base
  belongs_to :user, :foreign_key => "users_id"
  has_many :participants
  has_many :questions
  has_many :users, :through => :participants
end
```

####RenameModelAssociations

```ruby
class Pet < ActiveRecord::Base
  has_many :dogs
  has_many :dog_breeds, :through => :dogs, :source => :breeds
end
```

[Renamingthrough associations using source](http://stackoverflow.com/questions/4632408/need-help-to-understand-source-option-of-has-one-has-many-through-of-rails)

###ModelValidations

####BasicValidations

class Person < ActiveRecord::Base
  validates :username, :length => { :minimum => 3, :message => "must be at least 3 characters, fool!" }, uniqueness: true   validates :entered_password, :length => { :minimum => 6 } #source: SurveyDBCGroupProject

  validates :email, :presence => true
  validates :email, :uniqueness => true

  validates :email,
            :format => {
              :with    => /^([^\s]+)((?:[-a-z0-9]\.)[a-z]{2,})$/i,
              :message => "Only letters allowed" }#[better to validate emails with a gem]( http://www.stormconsultancy.co.uk/blog/development/validating-email-addresses-in-rails/)
  validates :password, :presence => true
end 



##Views

###BasicForms

####LoginForm

[login form](https://github.com/tararoys/SurveyDBC/blob/master/app/views/sign_up.erb#L5:)

```html
<form id="sign-up" method="post" action="/users">
  <input type="text" name="user[username]" placeholder="Username" value="<%= @user.username %>"> <!-- predict that this page doubles as an edit user account page -->
  <span id="name-errors" class="errors"></span>
  <br>

  <input type="password" name="user[password]" placeholder="Password">
  <span id="entered_password-errors" class="errors"></span>
  <br>

  <div class="submit"><input type="submit" value="Sign Up"></div>
</form>
```

##Controllers

#Agile
##Workflow
###Switching
###Git
###Testing




