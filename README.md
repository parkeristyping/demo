# README

First I ran `rails new demo -T -d postgresql`. That created a new rails app with Postgres as the database and no test suite (which I do since `rails new` uses minitest, and I prefer using Rspec).

Then I ran `rails g scaffold Posts`, which created a bunch of default files for setting up CRUD for Posts...

```
  invoke  active_record
  create    db/migrate/20201006005332_create_posts.rb
  create    app/models/post.rb
  invoke  resource_route
    route    resources :posts
  invoke  scaffold_controller
  create    app/controllers/posts_controller.rb
  invoke    erb
  create      app/views/posts
  create      app/views/posts/index.html.erb
  create      app/views/posts/edit.html.erb
  create      app/views/posts/show.html.erb
  create      app/views/posts/new.html.erb
  create      app/views/posts/_form.html.erb
  invoke    helper
  create      app/helpers/posts_helper.rb
  invoke    jbuilder
  create      app/views/posts/index.json.jbuilder
  create      app/views/posts/show.json.jbuilder
  create      app/views/posts/_post.json.jbuilder
  invoke  assets
  invoke    scss
  create      app/assets/stylesheets/posts.scss
  invoke  scss
  create    app/assets/stylesheets/scaffolds.scss
```

Then I added some fields to my Posts model. Specifically that involved:
- update the migration file with some new columns (in this case, just `body` and `mood`)
- update the controller to accept these new fields
- update the views to show these fields and add them to relevant forms

I also added `root 'posts#index'` to `routes.rb` so that our root path will take us somewhere useful.

Finally, to get things running...
- make sure postgres is installed and running
- `$ bundle install`
- `$ bundle exec rails db:setup`
- `$ bundle exec rails db:migrate`
- `$ bundle rails server`
- head on over to http://localhost:3000
