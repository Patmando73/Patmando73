---
layout: post
title: "Dinner Club"
date: 2015-06-10
categories: code
---

# DinnerClub

I needed to build a program that allowed the user to create a dinner club group and send them on outings with each other. The program needed to be able to only send specific people to outings and split the cost of the bill and tip up between the attendees of that outing. As the group went out more and more there needed to be a running total of how much they spent and who went to what outing.

There are 3 classes I created to complete this project, a â€œdinner_clubâ€ class, â€œcheck_splitterâ€ class and an â€œappâ€ class to run it.

The â€œdinner_clubâ€ class has few methods but they all have very high functionality. First I started with the â€œinitializeâ€ where I gathered the names of the members of the club and initialized the array of outings they went on. Once the array of member names where given as the parameter
I would loop through the array setting each name as a key in the â€œ@membersâ€ hash with a starting value of zero. 

```ruby
 def initialize(member_names)
    @members = {}
    @outings = []

    member_names.each do |name|
      @members[name] = 0

    end
  end
```

Now that I have the club members I would ask how much the bill was, how much the tip percent was, who went to the current outing, and where they went. This is where my â€œcheck_splitterâ€ class came in. The bill cost,tip percent, and size of the group (obtained by using attendees.length) would be run through the â€œcheck_splitterâ€ class so each person paid the same amount. After this the array of attendees (the key) and the string of the place they went (the value) would be added to a hash to display who went to what outing.

```ruby
def go_out(meal_cost,tip_percent,attendees,place)
    cs = CheckSplitter.new(meal_cost,tip_percent,attendees.length)

    amount_per_person = cs.split
    attendees.each do |a|
      @members[a] = @members[a] + amount_per_person
    end
    attendes_and_place = {attendees => place}

    @outings.push attendes_and_place


    puts @members 
   @outings
end
```

The only variation that can occur is if an attendee of the outing wants to treat the group by paying for everyone. This is handled by a simple question and input of yes or no which is then run through an if, else Statement where if treat == yes then a separate method called â€œbeing_treated would run opposed to the previously listed â€œgo_outâ€ method. This new method runs the â€œtotal_costâ€ method of the â€œcheck_splitterâ€ class to obtain the cost of the meal plus the tip and give that all to the â€œtreaterâ€ but then still runs 

```ruby
attendes_and_place = {attendees => place}

    @outings.push attendes_and_place
```
in order to list all attendees for that event.