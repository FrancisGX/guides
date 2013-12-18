Ruby
=====

Formatting
----------
* Delete trailing whitespace or configure your editor to do so.

* Use 2 space indentation (no tabs).

* Indent continued lines two spaces.

    ```Ruby
    # bad
    @line_long_enough_to_justify_a_second_line =
    current_user.campaigns(force_reload = true)

    def method
      this_is_a_really_long_line_that_should_be_broken_up_over_multiple_lines_and.
      every_line_but_the_first_is_indented
    end

    # good
    @line_long_enough_to_justify_a_second_line =
      current_user.campaigns(force_reload = true)

    def method
      this_is_a_really_long_line_that_should_be_broken_up_over_multiple_lines_and.
        every_line_but_the_first_is_indented
    end
    ```

* Indent private methods equal to public methods.

    ```Ruby
    # bad
    private

      def private_method
      end

    # good
    private

    def private_method
    end
    ```

Naming
------
* Name variables, methods, and classes to reveal intent.

* Use snake_case for methods and variables.

* Use CamelCase for classes and modules.

* Keep acronyms like HTTP, RFC, XML uppercase.

* Use SCREAMING_SNAKE_CASE for other constants.

* Avoid abbreviations.

* The names of predicate methods (methods that return a boolean value) should
  end in a question mark. (i.e. Array#empty?).

* Avoid types in names.
    ```Ruby
    # bad
     user_array = User.all

     # good
     users = User.all
    ```

* Name the enumeration parameter the singular of the collection.
    ```Ruby
    # bad
    users.each { |u| u }

    collection.each { |c| c }

    # good
    users.each { |user| user }

    collection.each { |element| element }
    ```

Syntax
------

* Avoid inline comments.

    ```Ruby
    # bad
    puts 'Catz' # LOLZ I spelled it with a Z!

    # good
    # LOLZ I spelled it with a Z!
    puts 'Catz'
    ```

* Use spaces around operators, after commas, after colons and semicolons, around
  `{` and before `}`.

    ```Ruby
    # bad
    1+1
    a,b = nil,nil
    nil:nil
    nil;nil
    {1, 2, 3}

    # good
    1 + 1
    a, b = nil, nil
    nil : nil
    nil; nil
    { 1, 2, 3 }
    ```

* Don't include spaces after `(`, `[` or before `]`, `)`.

    ```Ruby
    # bad
    ( 1, 2 )
    [ 1, 2 ]

    # good
    (1, 2)
    [1, 2]
    ```

* If you break up an argument list, keep the arguments on their own lines and
  closing parenthesis on its own line.

    ```Ruby
    # bad
    method(really_really_really_long_argument,
           really_really_really_long_argument,
           really_really_really_long_argument)

    # bad
    method really_really_really_long_argument,
           really_really_really_long_argument,
           really_really_really_long_argument

    # good
    method(
      really_really_really_long_argument,
      really_really_really_long_argument,
      really_really_really_long_argument
    )
    ```

* If you break up a hash, keep the elements on their own lines and closing curly
  brace on its own line.

    ```Ruby
    # bad
    { 'Chris',
      'Anthony',
      'Frank' }

    # good
    {
      'Chris',
      'Anthony',
      'Frank'
    }
    ```

* Use newlines around multi-line blocks.

    ```Ruby
    # bad
    def method_with_multiline_block
      some_method_before_block(should_be_followed_by_a_newline)
      items.each do |item|
        do_something_with_item
      end
      some_method_after_block(should_follow_after_newline)
    end

    # good
    def method_with_multiline_block
      some_method_before_block(should_be_followed_by_a_newline)

      items.each do |item|
        do_something_with_item
      end

      some_method_after_block(should_follow_after_newline)
    end
    ```

* Avoid conditional modifiers (lines that end with conditionals.)

    ```Ruby
    # bad
    puts "Hi" if user.likes_to_be_greeted?

    # good
    if user.likes_to_be_greeted?
      puts "Hi"
    end
    ```

* Avoid multiple assignments per line.

    ```Ruby
    # bad
    one, two = 1, 2

    # good
    one = 1
    two = 2
    ```

* Avoid ternary operators. Use multi-line `if` instead to emphasize code
  branches.

    ```Ruby
    # bad
    user.likes_cats? ? send_cat_gifs : send_hate_mail

    # good
    if user.likes_cats?
      send_cat_gifs
    else
      send_hate_mail
    end
    ```

* Avoid explicit return statements unless doing so __significantly__ decreases
  intelligibility.

    ```Ruby
    # bad
    def method
      return 1
    end

    # good
    def method
      1
    end
    ```

* Use `self` to define class methods instead of explicitly stating the class.

    ```Ruby
    # bad
    class ClassName
      def ClassName.method
      end
    end

    # good
    class ClassName
      def self.method
      end
    end
    ```

* Don't use `class << self` when defining a group of class methods.

* Prefer implicit `self` to explicit `self`.

    ```Ruby
    # bad
    def instance_method
      self.private_method
    end

    # good
    def instance_method
      private_method
    end
    ```

* Basically just don't use `self` explicitly __anywhere__ except class methods
  and assignments.

* Use `&&` and `||` for Boolean expressions.

* Use `each`, not `for`, for iteration.

* Avoid using semicolons.

Organization
------------

* Avoid organizational comments (`# Validations`).

* Use an empty line between methods.

    ```Ruby
    # bad
    def method
    end
    def another_method
    end

    # good
    def method
    end

    def another_method
    end
    ```


Rails
-----

* Use private instead of protected when defining controller methods.
* Name date columns with `_on` suffixes.
* Name datetime columns with `_at` suffixes.
* Name initializers for their gem name.
* Order controller contents: filters, public methods, private methods.
* Order model contents: constants, macros, public methods, private methods.
* Put application-wide partials in the [`app/views/application`] directory.
* Put shared partials in the [`app/views/shared`] directory.

Organization
------------

* Order methods so that caller methods are earlier in the file than the methods
  they call.

* Order methods so that methods are as close as possible to other methods they
  call.


ERb
---

[Sample](samples/erb.rb)

* When wrapping long lines, keep the method name on the same line as the ERb
  interpolation operator and keep each method argument on its own line.
* Prefer double quotes for attributes.


Background Jobs
---------------

* Define a `PRIORITY` constant at the top of delayed job classes.
* Define two public methods: `self.enqueue` and `perform`.
* Put delayed job classes in `app/jobs`.

Email
-----

* Use one `ActionMailer` for the app. Name it `Mailer`.
* Use the user's name in the `From` header and email in the `Reply-To` when
  [delivering email on behalf of the app's users].

[delivering email on behalf of the app's users]: http://robots.thoughtbot.com/post/3215611590/recipe-delivering-email-on-behalf-of-users

Testing
-------

* Avoid the `private` keyword in specs.
* Order ActiveRecord association tests alphabetically by attribute name.
* Order ActiveRecord validation tests alphabetically by attribute name.
* Prefer `eq` to `==` in RSpec.
* Separate setup, exercise, verification, and teardown phases with newlines.
* Use RSpec's [`expect` syntax].
* Use `not_to` instead of `to_not` in RSpec expectations.

[`expect` syntax]: http://myronmars.to/n/dev-blog/2012/06/rspecs-new-expectation-syntax

#### Acceptance Tests

[Sample](samples/acceptance_test.rb)

* Avoid scenario titles that add no information, such as "successfully."
* Avoid scenario titles that repeat the feature title.
* Place helper methods for feature specs directly in a top-level `Features`
  module.
* Use Capybara's `feature/scenario` DSL.
* Use names like `ROLE_ACTION_spec.rb`, such as
  `user_changes_password_spec.rb`, for feature spec file names.
* Use only one `feature` block per feature spec file.
* Use scenario titles that describe the success and failure paths.
* Use spec/features directory to store feature specs.
* Use spec/support/features for support code related to feature specs.

#### Unit Tests

[Sample](samples/testing.rb)

* Don't prefix `it` block descriptions with 'should'.
* Name outer `describe` blocks after the method under test. Use `.method`
  for class methods and `#method` for instance methods.

