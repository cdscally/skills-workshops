# Databases 1 (40 minutes)

## Learning objectives

See the readme.

## Instructions

### Starter (15 minutes)

```ruby
require 'data_mapper'

DataMapper.setup(:default,
                 "postgres://localhost/databases_1_starter")

class Person
  include DataMapper::Resource

  property :id, Serial
  property :name, String

  def print_name
    puts name
  end
end

DataMapper.finalize
DataMapper.auto_migrate!

timmy = Person.create(name: "timmy")
timmy.print_name
timmy.name = "tim"
timmy.save

tim = Person.get(1)
tim.print_name
```

```
Person table

id | name
---|-----
0  | Isla
```

Write this code up on a whiteboard.

Walk through the code token by token.  For each token, ask the students:

**How does this relate to the other parts of the code or table?**

Try and make sure to cover the following ideas: class, method, object, attribute, property, table, row, column, header.

Here are some example questions to help tease out the relationships between the parts of the code and the table.

* `Person`. This is the `Person` class.
* `create`. This is a class method provided by `DataMapper::Resource`.  What does it do?
* `name:` What does `name:` correspond to? What if we put `blah:` instead?
* `timmy.print_name`. Where does `print_name` come from? The class or object?
* `timmy.name`. Why can we `.name`? (Maybe ask about how and when the data gets from table to attribute to accessor.)
* `timmy.save`.  Where does `save` come from? What does it do?
* `property :id`. How does this relate to the table?
* `0  | Isla`. Where is this represented in the code?

### Main (40 minutes)

Students have three classes that constitute a domain, with a mix of computed and property methods (including relations). They must diagram the underlying database structure of these classes.

### Plenary (10 minutes)

Come together to discuss the diagrams drawn.
