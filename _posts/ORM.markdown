---
layout: post
title: "ORM"
date: 2015-06-10
categories: code
---



#What is an ORM?
An ORM is a model used to interact with the database using an object. This is done first by getting rows back from the 
database as hashes and converting these hashes into objects. We can then use these objects interact with the rest of our
program without having to repeatedly go to the database.

```ruby

    def find(record_id)

        table_name = self.to_s.pluralize.underscore

        results = CONNECTION.execute("SELECT * FROM #{table_name} WHERE id = #{record_id}").first
        self.new(results)
    end
```

#How does your ORM help you get all of a particular table's rows from the database?
An ORM can help you get all of a particular tables rows


#How does your ORM represent rows from a table, given that Ruby doesn't have a Table data structure?
An ORM represents tables in a database as objects created by your programming language.


#How does your ORM convert rows from a table into the Ruby data structure?
An ORM converts rows of data from a table into ruby objects using the hash that the database gives back as parameters
for the initialization of a new object.
