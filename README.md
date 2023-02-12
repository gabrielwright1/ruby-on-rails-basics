# [Ruby on Rails Learning Plan](https://www.linkedin.com/learning/paths/build-your-ruby-on-rails-skills?u=76281980)

## Courses:

- [Ruby on Rails 7 Essential Training](https://www.linkedin.com/learning/ruby-on-rails-7-essential-training?contextUrn=urn%3Ali%3AlyndaLearningPath%3A580902bf3dd5598d00538566&u=76281980) - [See Notes](https://github.com/gabrielwright1/ruby-on-rails-basics#ruby-on-rails-7-essential-training)
- [Ruby on Rails Controllers and Views](https://www.linkedin.com/learning/ruby-on-rails-controllers-and-views?contextUrn=urn%3Ali%3AlyndaLearningPath%3A580902bf3dd5598d00538566&u=76281980) - [See Notes](https://github.com/gabrielwright1/ruby-on-rails-basics#ruby-on-rails-controllers-and-views)
- [Ruby on Rails Models and Associations](https://www.linkedin.com/learning/ruby-on-rails-models-and-associations?contextUrn=urn%3Ali%3AlyndaLearningPath%3A580902bf3dd5598d00538566&u=76281980) - [See Notes](https://github.com/gabrielwright1/ruby-on-rails-basics#ruby-on-rails-models-and-associations)
- [Ruby on Rails: Debugging](https://www.linkedin.com/learning/ruby-on-rails-debugging?contextUrn=urn%3Ali%3AlyndaLearningPath%3A580902bf3dd5598d00538566&u=76281980) - [See Notes](https://github.com/gabrielwright1/ruby-on-rails-basics#ruby-on-rails-debugging)

## Overview of topics:

1. [Getting Started](https://github.com/gabrielwright1/ruby-on-rails-basics#getting-started)
2. [Controllers, Views, and Dynamic Content](https://github.com/gabrielwright1/ruby-on-rails-basics#controllers-views-and-dynamic-content)
3. [Databases and Migrations](https://github.com/gabrielwright1/ruby-on-rails-basics#databases-and-migrations)
4. [Models and ActiveRecord](https://github.com/gabrielwright1/ruby-on-rails-basics#models-and-activerecord)
5. [CRUD, REST, and Resourceful Routes](https://github.com/gabrielwright1/ruby-on-rails-basics#crud-rest-and-resourceful-routes)
6. [Controllers and CRUD](https://github.com/gabrielwright1/ruby-on-rails-basics#controllers-and-crud)
7. [Useful Controller Features](https://github.com/gabrielwright1/ruby-on-rails-basics#useful-controller-features)
8. [Rendering Views](https://github.com/gabrielwright1/ruby-on-rails-basics#rendering-views)
9. [Incorporating Assets](https://github.com/gabrielwright1/ruby-on-rails-basics#incorporating-assets)
10. [Work Faster with Helpers](https://github.com/gabrielwright1/ruby-on-rails-basics#work-faster-with-helpers)
11. [Smarter Models](https://github.com/gabrielwright1/ruby-on-rails-basics#smarter-models)
12. [Data Validations](https://github.com/gabrielwright1/ruby-on-rails-basics#data-validations)
13. [ActiveRecord Callbacks](https://github.com/gabrielwright1/ruby-on-rails-basics#activerecord-callbacks)
14. [ActiveRecord Associations](https://github.com/gabrielwright1/ruby-on-rails-basics#activerecord-associations)
15. [Backtraces](https://github.com/gabrielwright1/ruby-on-rails-basics#backtraces)
16. [Debugging in Templates](https://github.com/gabrielwright1/ruby-on-rails-basics#debugging-in-templates)
17. [Binary Searching](https://github.com/gabrielwright1/ruby-on-rails-basics#binary-searching)
18. [Logging](https://github.com/gabrielwright1/ruby-on-rails-basics#logging)
19. [Interactive Debugging](https://github.com/gabrielwright1/ruby-on-rails-basics#interactive-debugging)
20. [Fixing Common Errors and Researching](https://github.com/gabrielwright1/ruby-on-rails-basics#fixing-common-errors-and-researching)

## Helpful Resources:

- [Cheatsheet](https://gist.github.com/mdang/95b4f54cadf12e7e0415)

---

# [Ruby on Rails 7 Essential Training:](https://www.linkedin.com/learning/ruby-on-rails-7-essential-training?contextUrn=urn%3Ali%3AlyndaLearningPath%3A580902bf3dd5598d00538566&u=76281980)

## Sections:

1. Getting Started
2. Controllers, Views, and Dynamic Content
3. Databases and Migrations
4. Models and ActiveRecord
5. CRUD, REST, and Resourceful Routes
6. Controllers and CRUD

## Notes:

### Getting Started

#### Core Concepts

1. DRY Code

- Don't repeat yourself
- Code is defined once, and referenced later on
- Concise and consistent code is easier to maintain

2. Convention over configurations

- Uses defaults, and specifies unconventional aspects
- Speeds up development
- Follows best practices
- Extra features for free

3. MVC Architecture

- Controller listens for events on the webpage in the browser
- Controller asks the model for information
- Model asks database for data via query/mutation
- Model returns data to controller, which updates the view
- View is displayed on the webpage in the browser

![MVC architecture](https://user-images.githubusercontent.com/52660296/213944784-a2a2c316-48e0-4ce5-b450-2287350e6ea4.PNG)

#### Creating a new project

1. Create a folder called 'Sites' and store the projects within it rather than the root directory/program files (Windows)
2. Run the following commands:

```ruby
cd Sites
rails new project_name -d mysql
rails new --help
cd project_name
```

#### Configure project

1. a) Configure the database (assuming you have a user with db create privileges):

- Edit 'config/database.yml' file
- Add database username and password to yml file
- Run the following command (creates dev/test databases):

```ruby
rails db:create
```

1. b) Alternative method to create db (if you don't have a user with db create privileges)

- Create a database manually using the following commands:

```sql
CREATE DATABASE db_name;
CREATE USER 'username'@'localhost'
IDENTIFIED BY 'secretpassword';

GRANT ALL PRIVILEGES ON db_name.*
TO 'username'@'localhost';
```

#### Access Rails project from browser

1. Start Web Server (called Puma) - in development

```ruby
rails server
# or
rails s
```

2. Contact Web Server

```
http://localhost:3000
```

3. Stop Web Server

```
CTRL + C
```

#### Generate a Controller and View

Request loop (MVC model):

```
Browser -> Controller -> View -> Browser -> (cont'd)
```

1. Generate a controller

```ruby
# Syntax
rails generate controller ControllerName actions

# For example
rails g controller Tasks index new edit
rails g controller Main index
```

This does a few things:

- Creates methods within our Tasks file called 'index', 'new', and 'edit'
- Creates a method within our Main file called 'index'
- Generates routes for each method in the `config/routes.rb` file

You can check that its working by visiting the following routes:

```
http://localhost:3000/tasks/index

or

http://localhost:3000/main/index
```

#### Define Routes (manually)

Match route (automatically generated using generator method above)

```ruby
# Shorthand - only use if URL/conteroller action match
get 'main/index'
# or
get 'tasks/:id'

# Alternative - use if the URL/controller action don't match
match 'main/index', to: 'main#index', via: :get
# or
match 'tasks/:id', to: 'tasks#show', via: :get

```

Root route (required for every project, at root directory)

```ruby
# Shorthand - only use if URL/conteroller action match
root 'main#index'

# Alternative - use if the URL/controller action don't match
match '/', to: 'main#index', via: :get

```

[Back to top](https://github.com/gabrielwright1/ruby-on-rails-basics#ruby-on-rails-learning-plan)

---

### Controllers, Views, and Dynamic Content

#### Render a view template for a browser (i.e. About page)

1. Create route for 'About' page within `config/routes.rb` by typing the following:

```ruby
match 'about', to: 'main#about', via: :get
```

2. Add a action/method to the `controllers/main_controller.rb` called `about`
3. Create a new template within `views/main/about.html.erb` called `about.html.erb`
4. Within the `about.html.erb` file, add the following:

```html
<h2>About</h2>
<p>Description of the task manager</p>
<p>Created by...</p>
```

Render Template Syntax (alternative - if you don't want to use default render behaviour)

```ruby
render('main/about')

# or

render('about') # shorthand
```

#### Redirect controller actions:

Rails Redirect

```ruby
redirect_to(controller: 'main', action: 'index')
# or
redirect_to(action: 'index')
# or
redirect_to('https://nytimes.com')
```

![Redirect Actions](https://user-images.githubusercontent.com/52660296/214371160-c3265380-6195-40d9-93bb-ce67cfbf7bd4.png)

#### Define view templates using ERB

ERB (Embedded Ruby)

- Templating system used to embed Ruby into HTML pages

```erb
<% code %>
<%= code %>
```

Template File Naming Convention:

- For example, 'about' is the name of the template

```erb
about.html.erb
```

#### Instance variables to set values in a template

Regular vs. Instance variables:

- A regular `variable` only has/us
     - Scoped within a particular actino
- An `@instance_variable` has/is: - Scoped throughout the controller class and is available to all methods inside that class - Available to the template - A template can automatically access any instance variables you've set. - It makes it easy to pass data to your views.

#### Create links to other web pages

HTML Links:

```html
<a href="/main/index">Click me</a>
```

Rails Links:

```ruby
<%= link_to(text, target)%>
```

Link Targets:

```ruby
'/main/index' # shorthand

{controller: 'main', action: 'index'}

```

#### Defining and reading URL parameters

HTML link with parameters:

```html
/main/hello?id=20&page=5
```

Rails link with parameters:

```ruby
<%= link_to('Link',
    {
        controller: 'main',
        action: 'hello',
        id: 20,
        page: 5
    }
) %>
```

`params` method

- Accessible in controllers and views
- Contains all GET and POST values
- All values are strings ("1" != 1)

Retrieve values from params:

```ruby
params[:id]
# or
params['id']
```

---

### Databases and Migrations

#### Write migrations to define database changes

Managing Database Tables:

- Can use legacy database tables
- Can manually manage database tables
- Can use Ruby on Rails migrations

Migrations:

- Set of database instructions
- Written in Ruby
- "Migrate" the database from one state to another
- Instructions for moving "up" to a new state
- Instructions for moving "down" to the previous state

Benefits of migrations:

- Keep database schema with application code
- Executable and repeatable
- Allow sharing of schema changes
- Allow writing Ruby instead of SQL
- Able to access code in the Rails project

#### User command line to generate migrations

```ruby
# command
rails generate migration MigrationName

# migration class created
class CreateUsers < ActiveRecord::Migration

    # default methods
    def up
        create_table(:users) do |t|
            t.string :first_name
            t.string :last_name
            t.string :email
        end
    end

    def down
        drop_table(:users)
    end

    # shorthand method - performs the opposite of create when migrating down
    def change
        create_table(:users) do |t|
            t.string :first_name
            t.string :last_name
            t.string :email
        end
    end
```

Migration methods:

```ruby
create_table

drop_table

rename_table

add_column

remove_column

rename_column
```

Table column types:

- string
- integer
- boolean
- text
- decimal
- datetime
- date
- time
- binary

Generate a model:

```ruby
# command syntax
rails generate model ModelName columns

# command example
rails generate model Task
    name:string description:text
    position:integer completed:boolean
```

#### Run migrations to change the database schema

```ruby
# main command
rails db:migrate

# useful commands
rails db:migration:status

rails db:migrate VERSION=9

rails db:migrate VERSION=20221231235959

```

[Back to top](https://github.com/gabrielwright1/ruby-on-rails-basics#ruby-on-rails-learning-plan)

---

### Models and ActiveRecord

#### ActiveRecord and ActiveRelations

ActiveRecord

- Design pattern for relational databases
- Retrieve and manipulate data as objects not as static rows

ActiveRecord Objects are "Intelligent"

- Understand the structure of the table
- Contain data from table rows
- Know how to create, read, update, and delete rows
- Add complex functionality
- Can be manipulated as objects, then saved easily

ActiveRecord Example

```ruby
user = User.new

user.first_name = "Kevin"
user.save # SQL INSERT

user.last_name = "Skolung"
user.save # SQL UPDATE

user.destroy # SQL DELETE
```

ActiveRelation

- Also known as "Arel"
- Object-oriented interpretation of relational algebra
- Simplifies the generation of complex database queries
- Small queries are chainable
- Complex joins and aggregations use efficient SQL
- Queries do not execute until needed

```ruby
user = User.where(first_name: 'Kevin')
users = users.order('last_name ASC').limit(5)

users.each {|user| ... }

##
# SELECT users.* FROM users
# WHERE users.first_name = 'Kevin'
# ORDER BY users.last_name ASC
# LIMIT 5
```

#### Use the Rails console to interact with a Rails project

Important:

- Rails console interacts with the regular project database
- Changes can affect the data a browser would see
- Important, especially with the production database

```ruby
# commands
rails console -e development
rails console -e production
rails console -e testing

# shorthand
rails c -e development
rails c -e production
rails c -e testing

```

#### Create records using ActiveRecord

Create Records: `create` method

- Same as new + save, but all in one step
- Instantiate object, set values, and save

```ruby
# example
task1 = Task.create(name: 'Sweep the porch', position: 2, completed: false)
```

#### Update records using ActiveRecord

Update Records: `find` and `save` methods

- Find record
- Set values
- Save changes

Update Records: `find` and `update` methods

- Find record
- Set values and save

```ruby
# example
task1.find(1) # where id = 1
task1.update(name:'Sweep porch', description: 'Sweep dirt off the porch')
```

#### Delete records using ActiveRecord

Delete Records: `find` and `destroy` methods

- Find record
- Destroys the element in the SQL database (this is not the same thing as the `delete` method)

```ruby
task1.destroy # no brackets needed
```

#### Find records using ActiveRecord

Primary Key Finder: `find`

```ruby
Task.find(1) # looks for id, returns either an object or error
```

Conditions:

```ruby
Task.where(completed:false)
Task.where('completed = 0 AND position < 10')
User.where(['first_name LIKE ?', @query])
```

Order, Limit, Offset

```ruby
Task.order('position ASC')
Task.limit(20)
Task.offset(100)
Task.where(completed:true).order(:position).limit(5).offset(10)

#alternative
task1 = Task.find_by(['name LIKE ?', '%porch%'])
```

#### Define one-to-many associations between models

Relational Database Associations

- One-to-one
- One-to-many
- Many-to-many

One-to-Many Association:

- Teacher 'has many' courses
- Course 'belongs to' a teacher
- Foreign key on courses table

Associations:

- Create relationship in database
- Define relationship in models, both sides
- Use relationship

```ruby
# For example, 'category' -> 'tasks' which is one-to-many

# run command
rails g model Category name:string # creates a model for 'category'
rails g migration AddCategoryIdToTasks # creates a migration file

# add foreign key (column id) to Task table
class AddCategoryIdToTasks < ActiveRecord::Migration(7.0)
    def change
        add_column(:tasks, :category_id, :integer, index: true)
    end
end

# make database changes
rails db:migrate

# link the task to the category
class Task < ApplicationRecord
    belongs_to :category, optional: true
end

# link the category to the task
class Category < ApplicationRecord
    has_many :tasks
end

# open console and create an example
rails console -e development
category = Category.create(name: 'weekly')
category.tasks # returns []
task1 = Task.find(1) # id = 1
category.tasks << task1 # appends task1 to the task list, returns task list
category.tasks.count # returns 1
category.tasks.delete(task2) # 'delete' removes the relationship
category.tasks.count # returns 0
category.tasks.empty? # returns true
```

[Back to top](https://github.com/gabrielwright1/ruby-on-rails-basics#ruby-on-rails-learning-plan)

---

### CRUD, REST, and Resourceful Routes

#### Learn about CRUD (create, read, update, delete)

What is CRUD?

- Create, Read, Update, Delete
- Each action is a separate controllers
- Often one controller per model; uses plural names

![Screen Shot 2023-01-26 at 2 04 48 PM](https://user-images.githubusercontent.com/52660296/214930246-707a1230-22dd-46c1-ae5e-3ae6fa89178e.png)

For example:

- TasksController
- CategoryController

Helpful commands for creating controller and actions:

```ruby
# commands
rails g controller Categories index show new edit delete

# output controllers
class CategoriesController < ApplicationController

    def index
    end

    def show
    end

    def new
    end

    def edit
    end

    def delete
    end
end

# output routes
Rails.application.routes.draw do
    get 'categories/index'
    get 'categories/show'
    get 'categories/new'
    get 'categories/edit'
    get 'categories/delete'
end

```

#### Use REST for resourceful routes in a Rails project

What is REST?

- Representational state transfer
- Instead of performing procedures, perform state transformations on resources

![Screen Shot 2023-01-26 at 2 26 13 PM](https://user-images.githubusercontent.com/52660296/214932429-0bcf93b1-8245-4c33-8c42-0835797a7916.png)

Add resourceful routes:

- Delete action is not added by default, we can add it manually using a `member` block
- If an action operates on the resource as a whole, and doesn't send an ID, use a `collection`

```ruby
# For example, config/routes.rb
resources :tasks do
    member do
        get :delete
    end
    collection do
        get :export
    end
end

```

#### Use resourceful URL helpers

Resourceful URL helpers

```ruby
{controller: 'tasks', action: 'show', id: 5}

# shorthand
task_path(5)
```

![Screen Shot 2023-01-26 at 2 51 45 PM](https://user-images.githubusercontent.com/52660296/214936537-aed564cd-d944-46b3-9c65-63d5a1028192.png)

Resourceful URL helpers

```ruby
<%= link_to('All Tasks', tasks_path)%>
<%= link_to('Show Tasks', tasks_path(@task.id))%>
<%= link_to('Edit Tasks', edit_task_path(@task))%>
```

[Back to top](https://github.com/gabrielwright1/ruby-on-rails-basics#ruby-on-rails-learning-plan)

---

### Controllers and CRUD

#### Read actions: Index and show

![Screen Shot 2023-01-26 at 2 58 46 PM](https://user-images.githubusercontent.com/52660296/214937963-706029a3-8059-4901-bc3e-a5de7a437942.png)

#### Create action: New

HTML Form:

```ruby
params[:name]
params[:position]
params[:completed]
params[:description]
```

Rails Helper: `form_for`

- Form parameters are grouped
- Form inputs are easier and more consistent
- Fields are pre-populated with object attributes
- Form action/method checks object.new_record?

```ruby
<% form_for(@task) do |f| %>
     <% f.text_field(:name) %>
     <% f.text_field(:position) %>
     <% f.check_box(:completed) %>
     <% f.text_area(:description) %>
     <% f.submit('Create Task') %>
<% end %>
```

Accessing params:

```ruby
# accessing entire object
params[:task] # returns {name: 'clean room', position: '5', ...}

# accessing individual properties
params[:task][:name]
params[:task][:position]
params[:task][:completed]
params[:task][:description]
```

Example:

```ruby
class TasksController < ApplicationController
     def index
          @tasks = Task.order(:position)
     end

     def show
          @task = Task.find(params[:id]
     end
end
```

#### Create action: Create

Create Form Processing

- Instantiate a new object using form parameters
- Save the object
- If save succeeds, redirect to the index action
- If save fails, redisplay the form so user can fix problems

Mass Assignment:

```ruby
Task.new(params[:task])
Task.create(params[:task])
@task.update(params[:task])
```

Strong Parameters (prevents hackers from sending more params to the server)

```ruby
params.require(:task) # returns obj, similar to params[:task]
params.require(:task).permit(:name, :position, :completed) # prevents extra fields
```

#### Update actions: Edit and update

Update form processing:

- Find a existing object using its ID
- Update the object using form parameters
- If update succeeds, redirect to the show action
- If update fails, redisplay the form so user can fix problems

#### Use partials to organize code

Partials (similar to components in React.js)

- Better code organization
- Don't repeat yourself
- Partials are partial templates

#### Delete actions: Delete and destroy

Is a Delete Form necessary?

- Not a default action
- Often omitted
- Link to destroy
- Link to destroy with a confirmation alert
- Link to a confirmation page

[Back to top](https://github.com/gabrielwright1/ruby-on-rails-basics#ruby-on-rails-learning-plan)

---

# [Ruby on Rails Controllers and Views](https://www.linkedin.com/learning/ruby-on-rails-controllers-and-views?contextUrn=urn%3Ali%3AlyndaLearningPath%3A580902bf3dd5598d00538566&u=76281980)

## Sections:

1. Useful Controller Features
2. Rendering Views
3. Incorporating Assets
4. Work Faster with Helpers

## Notes

### Useful Controller Features

#### Store data in cookies

#### Store data in sessions

#### Messaging with the flash hash

#### Log information to a file

#### Inherit common behaviors with ApplicationController

#### Use filters to call methods automatically

[Back to top](https://github.com/gabrielwright1/ruby-on-rails-basics#ruby-on-rails-learning-plan)

### Rendering Views

#### Avoid double render errors

#### More options for rendering content

#### Use layouts for shared templates

#### Capture content for later use

[Back to top](https://github.com/gabrielwright1/ruby-on-rails-basics#ruby-on-rails-learning-plan)

### Incorporating Assets

#### Add stylesheets to view templates

#### Use static images assets

#### Use images as CSS backgrounds

[Back to top](https://github.com/gabrielwright1/ruby-on-rails-basics#ruby-on-rails-learning-plan)

### Work Faster with Helpers

#### Text helpers

#### Sanitization helpers

#### Number helpers

#### Data and time helpers

#### Form helpers

#### Custom helpers

[Back to top](https://github.com/gabrielwright1/ruby-on-rails-basics#ruby-on-rails-learning-plan)

---

# [Ruby on Rails Models and Associations](https://www.linkedin.com/learning/ruby-on-rails-models-and-associations?contextUrn=urn%3Ali%3AlyndaLearningPath%3A580902bf3dd5598d00538566&u=76281980)

## Sections:

1. Smarter Models
2. Data Validations
3. ActiveRecord Callbacks
4. ActiveRecord Associations

## Notes

### Smarter Models

#### Smart Models by Design:

- "Fat model, skinny controller"
- Move most business logic to models
- Define instance methods for things an instance of a class should "know"
- Models can leverage attributes and associations

Benefits of Smarter Models:

- Don't Repeat Yourself (DRY)
- Code is easier to maintain with fewer bugs
- Model methods can be called from anywhere in the app
- Model methods can be exercised from the Rails console
- Model methods are easier to test

Respect MVC Architecture

- Code for decisions based on user actions belongs in Controllers
- Code for the presentation of data belongs in the Views
- Code for formatting data for Views belongs in Helpers
- Not HTML, CSS, XML, JSON, JavaScript

```ruby
# Example:
class User < ApplicationRecord
    def full_name
        [first_name, last_name].join(' ')
    end

    def last_name_first
        [last_name, first_name].join(', ')
    end

    def abbrev_name
        first_initial = first_name.chars.first + ". "
        [first_initial, last_name].join(' ')
    end
end

# we can now type into rails console:
user.full_name # Kevin Skoglund
user.last_name_first # Skoglund Kevin
user.abbrev_name # K. Skoglund
```

#### More ActiveRecord query methods

Query Condition: AND

- Rails does not fire off the query right away, it waits until it is needed

```ruby
Product.where(visible: true, sold_out: false)
# SELECT * FROM products
# WHERE visible = TRUE AND sold_out = FALSE

Product.where(visible: true).where("created_at > ?", 1.year.ago)
# SELECT * FROM products
# WHERE visible = TRUE
# AND created_at > '2022-01-01 00:00:00'
```

Query Condition: OR

```ruby
Product.where("created_at < ?", 1.year.ago).or(
    Product.where(sold_out:true)
)
sold_out = Product.where(sold_out:true)
Product.where("created_at < ?", 1.year.ago).or(sold_out)
```

Query Condition: NOT

```ruby
Product.where(visible: true).where.not("created_at > ?", 1.year.ago)
# SELECT * FROM products
# WHERE visible = TRUE
# AND NOT created_at > '2022-01-01 00:00:00'
```

#### Select data from a query

Methods:

- all
- first
- last
- limit
- count
- any?
- none?
- many?
- one?

```ruby
Customer.all
# SELECT * FROM customers
```

```ruby
customers = Customer.all
customers[0..4]
# SELECT * FROM customers
```

```ruby
Customer.first
# SELECT * FROM customers ORDER BY id ASC LIMIT 1
```

```ruby
Customer.last
# SELECT * FROM customers ORDER BY id DESC
```

```ruby
customers = Customer.limit(5)
# SELECT * FROM customers ORDER BY id ASC LIMIT 5
```

```ruby
customers = Customer.first(5)
# SELECT * FROM customers ORDER BY id ASC LIMIT 5
```

```ruby
Customer.count
# SELECT COUNT(*) FROM customers
```

```ruby
Customer.any?
Customer.none?
# SELECT 1 AS one FROM customers LIMIT 1
```

```ruby
Customer.many?
Customer.one?
```

Select specific columns

Useful methods:

- select
- pluck
- ids

Using select:

```ruby
product = Product.select(:id, :name).first
# SELECT id, name FROM products ORDER BY id ASC LIMIT 1
# => <Product id: 1, name: "Coffee mug">

product.id
# => 1

product.name
# => Coffee mug

product.description
# => ActiveModel::MissingAttributeError
```

Using pluck (better alternative):

```ruby
Product.pluck(:id, :name)
# SELECT id, name FROM products
# => [[1, "Coffee Mug"], ...]

Product.all.map{|p| [p.id, p.name]}
# SELECT * FROM products
# => [[1, "Coffee Mug"], ...]

Product.ids
# => [1, 3, 5, 14, 32, 35]

Product.pluck(:id)
# => [1, 3, 4, 5, 6, 7]

Product.all.map{|p| p.id}
# => [1,3,5,6,7,8]
```

#### Named scopes

- Commonly-used queries defined in a model
- Defined using built-in query methods
- Use a lambda function, a block of code for later use

```ruby
class Product < ApplicationRecord
    scope :active, -> { where(active: true) }
    scope :recent, -> { where("created_at > ?", 3.months.ago) }
    scope :sorted, -> { order(:name)}
end

# Calling it here
Product.active.recent.sorted
# this is the same as above
Product.where(active: true).where("created_at > ?", 3.months.ago).order(:name)
```

Lambda functions:

- Encapsulates logic and data in a portable variable to be used later

```ruby
class Product < ApplicationRecord
    scope :search, lambda { |kw|
        keyword = (kw || '').downcase
        where("LOWER(name) LIKE ?", "%{keyword}%")
    }
    scope :with_style, -> (sid) { where(style_id: sid) }
end

# Calling it here
Product.search("mug").with_style(34)
```

#### Non-database attributes

Instance Attributes

- Attributes are methods to access values
- Useful for setting temporary states in an object
- Values will not be stored in a database
- Can affect the values and behaviors of other methods

```ruby
attr_reader
attr_writer
attr_accessor
```

```ruby
class Customer
    attr_accessor :status
    def status
        @status
    end

    def status=(value)
        @status = value
    end
end
```

```ruby
class Payment < ApplicationRecord
    attr_writer :card_number
    attr_reader :transaction_error

    def process!
        result = CardProcessor.charge(@card_number, amount)
        @transaction_error = result["error"]
    end
end

# calling it here
payment = Payment.new(payment_params)
payment.process!
error = payment.transaction_error
```

```ruby
class Payment < ApplicationRecord
    attr_accessor :zone

    def process!
        if EU_TLDS.include?(@zone)
            EuroPayment.capture(@card_number, euro_amount)
        else
            AmeriCharge.charge(@card_number, amount)
        end
    end
end

# calling it here
payment = Payment.new(payment_params)
payment.zone = request.domain.split('.').last
payment.process!
```

[Back to top](https://github.com/gabrielwright1/ruby-on-rails-basics#ruby-on-rails-learning-plan)

### Data Validations

#### Overview of validation methods

Validations:

- Ensure data meets requirements before saving to database
- Validation code resides in models
- Failed validations: record will not save, will track errors

```ruby
class Product < ApplicationRecord
    validates_presence_of :name
    validates_length_of :name, maximum: 50
    validates_numericality_of :price, greater_than: 0
    validates_uniqueness_of :stock_number
end
```

`validates_presence_of`:

- Attribute must not be blank (nil, false, "", " ", [], {})

```ruby
# syntax
validates_presence_of :name
```

`validates_length_of`:

- Attribute must meet length requirements

```ruby
# syntax
validates_length_of :name, within: 3..40

# useful keywords
:is
:minimum, :maximum
:within
```

`validates_inclusion_of`:

- Attribute must be in a list of choices (array or range)

```ruby
validates_inclusion_of :status,
    in: ['new', 'reviewing', 'approved', 'deleted']

validates_exclusion_of :zone_id, in: [78, 109]

# useful keywords
:in
:within
```

`validates_format_of`:

- Attribute must match a regular expression

```ruby
validates_format_of :zipcode, with: /\d{5}/

# useful keywords
:with
```

`validates_uniqueness_of`:

- Attribute must not exist in the database

```ruby
validates_uniqueness_of :username
:case_sensitive
:scope
```

`validates_acceptance_of`:

- Attribute must be accepted
- Creates a virtual attirbute if no table column

```ruby
# syntax
validates_acceptance_of :terms
:accept (expected value, "1")
```

`validates_confirmation_of`:

- Attribute must be confirmed by being entered twice
- Creates a virtual attribute for confirmation
- Only validates when confirmation attribute is not nil

```ruby
# syntax
validates_confirmation_of :password
```

`validates_associated`:

- Associated object (or objects) must all be valid
- First argument: association name; not an attribute
- Calls `#valid?` on the object or array of objects
- Does not fail if object does not exist
- Beware of infinite loops and long cascades

Validation Options:

```ruby
:allow_nil
:allow_blank
:on (:save, :create, :update)
:if
:unless
:message (for example, "can't be blank")
```

#### Write validations

What to validate:

- What are your data concerns?
- Decide what good and bad data look like
- What restrictions does your database impose (types, lengths, or null values)
- What would stop your application from working?

What not to validate:

- IDs
- Foreign keys
- Timestamps
- Booleans

#### Use the multipurpose validates methods

```ruby
class User < ApplicationRecord
    validates_presence_of :email
    validates_length_of :email, { maximum: 50 }
    validates_uniqueness_of :email
    validates_format_of :email, { with: EMAIL_REGEX }
    validates_confirmation_of :email
end

# using the validates method instead
class User < ApplicationRecord
    validates :email,   presence: true,
                        length: { maximum: 50},
                        uniqueness: true,
                        format:{ with: EMAIL_REGEX},
                        confirmation: true

    validates :email,   presence: true,
                        numericality: true,
                        length: options_hash,
                        format: { with: regex },
                        inclusion: { in: array_or_range },
                        exclusion: { in: array_or_range },
                        acceptance: true,
                        uniqueness: true,
                        confirmation: true
end
```

#### Write custom validations

```ruby
class MyModel < ApplicationRecord
    validate :custom_method

    private

    def custom_method
        if test_case
            errors.add(:attribute, "message")
        end
    end
end
```

[Back to top](https://github.com/gabrielwright1/ruby-on-rails-basics#ruby-on-rails-learning-plan)

### ActiveRecord Callbacks

#### Overview of callbacks

#### Use callbacks to automate actions

#### Execute callbacks conditionally

[Back to top](https://github.com/gabrielwright1/ruby-on-rails-basics#ruby-on-rails-learning-plan)

### ActiveRecord Associations

#### Overview of associations

#### Create a one-to-many associations

#### Use a one-to-many association

#### Destroy dependent related records

#### Has and belongs to many associations

#### Rich join associations

#### Traverse a rich join association

#### Join tables during queries

[Back to top](https://github.com/gabrielwright1/ruby-on-rails-basics#ruby-on-rails-learning-plan)

---

# [Ruby on Rails: Debugging](https://www.linkedin.com/learning/ruby-on-rails-debugging?contextUrn=urn%3Ali%3AlyndaLearningPath%3A580902bf3dd5598d00538566&u=76281980)

## Sections:

1. Backtraces
2. Debugging in Templates
3. Binary Searching
4. Logging
5. Interactive Debugging
6. Fixing Common Errors and Researching

## Notes

### Backtraces

#### Reading backtraces

#### Unlocking full backtraces

#### Challenge: Backtraces

#### Solution: Backtraces

[Back to top](https://github.com/gabrielwright1/ruby-on-rails-basics#ruby-on-rails-learning-plan)

### Debugging in Templates

#### Debugging variables

#### Debugging functions

#### Debugging objects

[Back to top](https://github.com/gabrielwright1/ruby-on-rails-basics#ruby-on-rails-learning-plan)

### Binary Searching

#### Binary search your code

#### Manual binary searching in tests

#### Automatic binary searching in tests

#### Binary searching in Git

#### Automatic binary searching in Git

[Back to top](https://github.com/gabrielwright1/ruby-on-rails-basics#ruby-on-rails-learning-plan)

---

### Logging

#### Using logs

#### Logging: Practical case in a test

#### Logging: Practical case fixing N+1

[Back to top](https://github.com/gabrielwright1/ruby-on-rails-basics#ruby-on-rails-learning-plan)

### Interactive Debugging

#### Introduction to the debug gem

#### Navigating the execution flow

#### Adding breakpoints

#### Integrating with Visual Studio Code

#### Using the web-console gem

[Back to top](https://github.com/gabrielwright1/ruby-on-rails-basics#ruby-on-rails-learning-plan)

---

### Fixing Common Errors and Researching

#### Fixing the most common errors when using Ruby on Rails

#### Researching on the internet

[Back to top](https://github.com/gabrielwright1/ruby-on-rails-basics#ruby-on-rails-learning-plan)
