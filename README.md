# Ruby on Rails Learning Plan

https://www.linkedin.com/learning/paths/build-your-ruby-on-rails-skills?u=76281980

## Courses:

- Ruby on Rails 7 Essentials Training
- Ruby on Rails Controllers and Views
- Ruby on Rails Models and Associations
- Ruby on Rails Debugging

## Overview of topics:

1. Getting Started
2. Controllers, Views, and Dynamic Content
3. Databases and Migrations
4. Models and ActiveRecord
5. CRUD, REST, and Resourceful Routes
6. Controllers and CRUD
7. Useful Controller Features
8. Rendering Views
9. Incorporating Assets
10. Work Faster with Helpers
11. Smarter Models
12. Data Validations
13. ActiveRecord Callbacks
14. ActiveRecord Associations
15. Backtraces
16. Debugging in Templates
17. Binary Searching
18. Logging
19. Interactive Debugging
20. Fixing Common Errors and Researching

---

# Ruby on Rails 7 Essential Training:

https://www.linkedin.com/learning/ruby-on-rails-7-essential-training?contextUrn=urn%3Ali%3AlyndaLearningPath%3A580902bf3dd5598d00538566&u=76281980

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

1. Create a folder called "Sites" and store the projects within it rather than the root directory/program files (Windows)
2. Run the following commands:

```ruby
cd Sites
rails new project_name -d mysql
rails new --help
cd project_name
```

#### Configure project

1. a) Configure the database (assuming you have a user with db create privileges):

- Edit "config/database.yml" file
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
get "main/index"
# or
get "tasks/:id"

# Alternative - use if the URL/controller action don't match
match "main/index", to: "main#index", via: :get
# or
match "tasks/:id", to: "tasks#show", via: :get

```

Root route (required for every project, at root directory)

```ruby
# Shorthand - only use if URL/conteroller action match
root "main#index"

# Alternative - use if the URL/controller action don't match
match "/", to: "main#index", via: :get

```

---

# Ruby on Rails Controllers and Views

https://www.linkedin.com/learning/ruby-on-rails-controllers-and-views?contextUrn=urn%3Ali%3AlyndaLearningPath%3A580902bf3dd5598d00538566&u=76281980

## Sections:

1. Useful Controller Features
2. Rendering Views
3. Incorporating Assets
4. Work Faster with Helpers

---

# Ruby on Rails Models and Associations

https://www.linkedin.com/learning/ruby-on-rails-models-and-associations?contextUrn=urn%3Ali%3AlyndaLearningPath%3A580902bf3dd5598d00538566&u=76281980

## Sections:

1. Smarter Models
2. Data Validations
3. ActiveRecord Callbacks
4. ActiveRecord Associations

---

# Ruby on Rails: Debugging

https://www.linkedin.com/learning/ruby-on-rails-debugging?contextUrn=urn%3Ali%3AlyndaLearningPath%3A580902bf3dd5598d00538566&u=76281980

## Sections:

1. Backtraces
2. Debugging in Templates
3. Binary Searching
4. Logging
5. Interactive Debugging
6. Fixing Common Errors and Researching
