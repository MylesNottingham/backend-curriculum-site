---
layout: page
title: Beat Box
---
# Iteration 3

## Creating the BeatBox Linked List "Wrapper"

Awesome! We have built most of our program and now it's time to wrap the Linked List logic in a `BeatBox` class.

When we create a new instance of the `BeatBox` class, a `LinkedList` object is also instantiated and available as an attribute on the `BeatBox` instance. Now, we can manage our linked list through the `BeatBox` class.

Up until now, we have only been able to `append` and `prepend` a single node at a time. The LinkedList class hasn't formatted the data it received, consequently, passing the string "deep bop dop" to `append` has resulted in _one_ node created with data `deep bop dop`. With `BeatBox` as an extra layer, it can take care of properly formatting the data (eg: splitting the string) before passing it down to the `LinkedList`. This implementation results in _three_ nodes appended to the list if we pass the string "deep bop dop" to `BeatBox#append`.

Expected behavior:

```ruby
> require "./lib/beat_box"
> require "./lib/linked_list"
> require "./lib/node"

> bb = BeatBox.new
=> <BeatBox list=<LinkedList head=nil #234567890890> #456789045678>
> bb.list
=> <LinkedList head=nil #234567890890>
> bb.list.head
=> nil
> bb.append("deep doo ditt")
=> "deep doo ditt"
> bb.list.head.data
=> "deep"
> bb.list.head.next_node.data
=> "doo"
> bb.append("woo hoo shu")
=> "woo hoo shu"
> bb.count
6
```

<br>

## Playing Beats

Now that we have our BeatBox class put together using the internal Linked List to keep track of our beats, let's use it to actually play the beats.

Remember that, at the command line, we can play sounds using the `say` command:

```
$ say -r 500 -v Boing "ding dah oom oom ding oom oom oom ding dah oom oom ding dah oom oom ding dah oom oom "
```

It turns out we can also easily issue this command (or any other system command) from ruby by using backticks: ```.

For example:

```
$ pry
> `say -r 500 -v Boing "ding dah oom oom ding oom oom oom ding dah oom oom ding dah oom oom ding dah oom oom "`
```

Additionally, we can use standard string interpolation (`#{}`) to pass dynamic content into a system command:


```
$ pry
> beats = "ding dah oom oom ding oom oom oom ding dah oom oom ding dah oom oom ding dah oom oom "
> `say -r 500 -v Boing #{beats}`
```

For this final section, add a `play` method to your BeatBox class that will generate the string content of the Beat and use it as input to the `say` command.

```ruby
> require "./lib/beat_box"
> require "./lib/linked_list"
> require "./lib/node"

> bb = BeatBox.new
=> <BeatBox list=<LinkedList head=nil #234567890890> #456789045678>
> bb.append("deep doo ditt woo hoo shu")
=> "deep doo ditt woo hoo shu"
> bb.count
=> 6
> bb.list.count
=> 6
> bb.play
=> # plays the sounds deep doo ditt woo hoo shu
```
