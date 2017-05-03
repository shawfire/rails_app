# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

https://devcenter.heroku.com/articles/getting-started-with-rails5#local-workstation-setup
heroku login (shawfire@icloud.com/T…8)
$ rails -v
	Rails 5.0.2
You can get the new version of rails by running,
$ gem install rails --no-ri --no-rdoc
	Successfully installed rails-5.0.2
	1 gem installed
rails new rails_app --database=postgresql

$ rails new rails_app --database=postgresql
	# Y Overwrite existing git directory
  OR Generate the project without Test::Unit (which is what the -T is):
    rails new new_project_name -T --database=postgresql
$ cd rails_app
$ bundle install
Add:
  group :development, :test do
    ...
    gem 'rspec-rails', '~> 3.5'
  end
#install postgresql locally:
[install postgresql locally](https://devcenter.heroku.com/articles/heroku-postgresql#local-setup)
$ which psql
    /usr/local/bin/psql
    $ psql -h localhost
    psql (9.6.2)
    Type "help" for help.

    shawfire=# \q
~/.bash_profile
  /usr/local/bin/psql
  PATH="/Applications/Postgres.app/Contents/Versions/latest/bin:$PATH"
$ export PATH="/usr/local/bin/psql:${PATH}"
$ rails db:create
$ rails db:migrate

$ bundle install
$ rails generate rspec:install
  This adds the following files which are used for configuration:
    .rspec
    spec/spec_helper.rb
    spec/rails_helper.rb

Don’t forget to prepare the db for testing after you run any new migrations:
$ rake db:test:prepare


+++
rails g controller Lists index show new create edit update destroy
rails g scafold_controller Lists
routes.rb
  resources :lists, only: [:index, :new, :create, :show, :edit, :destroy, :data]
  #get '/lists' => 'lists#index'
  #get '/lists/new' => 'lists#new'
  #post '/lists' => 'lists#create'
  #get '/lists/:id' => 'lists#show'

  #def list_url...

rails g model List title:string color:string
rails db:migrate
index.html.erb
  <% @lists.each do |list| %>

  <% end %>
ListsController
  @index = List.all

  def create
    list_params = params.require(:list).permit(:title, :color)
    @list = List.new(list_params)
    #list_params = params[:list]
    #title = list_params[:title]
    #color = list_params[:color]
    if @list.save
      redirect_to @list, ...
    else
      render 'new'
    end
  end
  def show
    @list = list.find(???)
  end
Views
  <% unsplash_image 'puppy' %>
  <%= form_for(@list) do |f| %>
    <div class="multi-field">
      <%= f.label :title %>
      <%= f.text_field :title %>
    </div>
  <% end %>

  <%= link_to list.title, list %>

  <%= render partial: 'form', list: @list %>
Model:
  validates :title,

rspec

+++
