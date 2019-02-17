## Generators

* `rails new [project name]` - Create a new project
* `rails generate controller [plural controller name] [action names you want to add]`

## Routes

* Decide which controller will handle a request

```ruby
Rails.application.routes.draw do
  get 'welcome/index' # Send requests for '/welcome/index' to the welcome controller's index action
  root 'welcome#index' # Send requests for root to the welcome controller's index action
  resources :articles # Standard REST action
end
```

## Controllers

* Collect information for a view
* Collect information with actions
* All instance variables from a controller are passed to rendered views

```ruby
# calls render with a hash- key is `plain`, `params[:article].inspect` are the article parameters from the form

def create
    render plain: params[:article].inspect
end
```

```ruby
def show
    @article = Article.find(params[:id])
end

def create
    @article = Article.new(params[:article])
    if @article.save
        redirect_to @article
    else
        render 'new' # Passes the broken article to the view
    end
end
```

## Views

* Display information from a controller
* Written in ERB templates
* Put in `app/views/[plural name]/[action].html.erb`
* Have access to router path variables- `new_article` is availabile at `new_article_path`
* Use the action name if its in the same controller as the current view, specify controller otherwise

### Links

```ruby
<%= link_to 'Link Text' item_path(item) %>
```

### Form Builder

* Helper ERB method called `form_with`

```erb
# Generates a form with title and text edit areas
# articles_path comes from router, makes a POST request by default
# local: true disables AJAX
<%= form_with scope: :article, url: articles_path, local: true do |form| %>

<p>
    <%= form.label :title %>
    <br />
    <%= form.text_field :title %>
</p>

<p>
    <%= form.label :text %>
    <br />
    <%= form.text_area :text %>
</p>
<p>
    <%= form.submit %>
</p>
<% end %>
```

## Models

* Model name is singular, database table is plural
* `rails generate model [Singular name] [property]:[type] [another property]:[type]`
* ActiveModel automatically maps DB properties to model properties

```ruby
# Save model
def create
    # @article = Article.new(params[:article]).permit(:title, :text) # Article refers to the class
    @article = Article.new(article_params)
    @article.save
    redirect_to @article
end

private
    def article_params
        params.require(:article).permit(:title, :text) # Whitelist of allowed properties
    end
```

## Tasks

* Rake is the task runner
* `rails server` - Starting built-in Puma server
* `rails db:migrate`
    * `rails db:migrate RAILS_ENV=production`

## File Structure

`app` - Controllers, models, views, helpers, mailers, channels, jobs, and assets
`bin` - Scripts to start, setup, update, deploy, or run the app
`config` - Configure routes and database
`config.ru` - Rack configuration for Rack servers
`db` - DB schema and migrations
`Gemfile`, `Gemfile.lock` - Dependencies
`lib` - Extended modules
`log` - Log files
`package.json` - npm dependencies
`public` - Delivered as-is
`Rakefile` - CLI tasks, add your own in `lib/tasks`
`tests` - Unit tests and fixtures
`vendor` - Third-party code
`.ruby-version` - Default ruby version
