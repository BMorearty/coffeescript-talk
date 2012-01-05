!SLIDE subsection

# PART 2: Using It In a Pre-3.1 Rails App

!SLIDE

# Barista ![barista](../images/barista.jpg)

    @@@ ruby
    # optional; must be *before* barista:
    gem 'haml-rails'

    # Only needed on Ruby 1.8:
    gem "json" 

    gem "barista"

!SLIDE

# Install

    bundle install
    rails generate barista:install

.notes Generates a config file

!SLIDE

# Profit

* Place your CoffeeScripts in `app/coffeescripts` using the `.coffee` extension.
* Generated JavaScript goes into `public/javascripts`.
  * In the right subfolder if applicable.

.notes Don't use `.js.coffee`

!SLIDE

# Put CoffeeScript in HAML With `:coffeescript`.

    %p hello, world.

    :coffeescript
      $ ->
        initialize()

!SLIDE

# Barista Deploy Options

* Default: generate on the fly in development. Deploy .js files.
* Add `therubyracer` to your Gemfile and add `rake barista:brew`
  to your Capistrano script.
* Install `therubyracer` on prod and generate on the fly there.
