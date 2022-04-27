<!-- markdownlint-disable MD032 MD033-->
<!-- Write your README.md file. Build something amazing! This README.md template can guide you to build your project documentation, but feel free to modify it as you wish 🥰 -->
# **Spree Notes**

## **About**

A Spree extension that provides ability to add useful notes to orders, products, users or any other spree table.

## **Key Features**

* It includes ability to configure the note settings from admin panel.
* Add notes to orders, products and users.
* Easy to extend to add notes to any spree table.

## **Demo**
<img src="https://user-images.githubusercontent.com/103247578/165513428-d34e62f1-ee5a-497b-a7ac-4b5c18e12a10.gif" height=400; width=800;></img>


## **Installation**

1. Add this extension to your Gemfile with this line:

    ```ruby
    gem 'spree_notes'
    ```

2. Install the gem using Bundler

    ```ruby
    bundle install
    ```

3. Copy & run migrations

    ```ruby
    bundle exec rails g spree_notes:install
    ```

4. Restart your server!


  If your server was running, restart it so that it can find the assets properly.

## Configure new class as noteable

1. Added association for notes to new class

    ```ruby
      has_many :notes, as: :notable
    ```

2. For adding additional options for noteables, we can override the method `noteable_klasses` from `Spree::NoteHelper`

    ```ruby
      def noteable_klasses
        legacy_klasses = super
        legacy_klasses << Spree::NewKlass
      end
    ```
4. For adding sidebar tab of notes, feel free to create deface override with [reference][1].
5. Add `notes.html.erb` as view template for new class with [reference][2].

## Testing

First bundle your dependencies, then run `rake`. `rake` will default to building the dummy app if it does not exist, then it will run specs. The dummy app can be regenerated by using `rake test_app`.

```shell
bundle update
bundle exec rake
```


When testing your applications integration with this extension you may use it's factories.
Simply add this require statement to your spec_helper:

```ruby
require 'spree_notes/factories'
```
---

## Contributing

[See corresponding guidelines](https://github.com/bluebash-spree-contrib/spree_notes/blob/master/CONTRIBUTING.md)

---

Copyright (c) 2022 Spree Edge. released under the [New BSD License](https://github.com/bluebash-spree-contrib/spree_notes/blob/master/LICENSE)



[1]: https://github.com/spree-edge/spree_notes/blob/master/app/overrides/spree/admin/shared/added_notes_tab.rb#L2
[2]: https://github.com/spree-edge/spree_notes/blob/master/app/views/spree/admin/orders/notes.html.erb
