
# Introduction to Computer Programming

This course was designed to help think you like a programmer. It aims to give you a set of mental 
tools, that is, ways to think about how to create your own scripts for those times when you want (or 
need) to automate some task. It assumes you'd like to get beyond simply repeating an already available 
task over and over on many different files. In order to help you get started on the next level of programming 
it will try to teach you how to think like a programmer, using heuristic methods. Our heuristic methods 
will be grounded in the concepts of Object-Oriented Programming (OOP), which is, at 
heart, a way of looking at the world from a computer-centric viewpoint.

The course assumes you have already learned at least the basics of a scripting language, such as BASH, 
or Python or Ruby. We'll use Ruby in our examples and our general discussion. The syntax of Ruby is
fairly easy to read without knowing the details, but if you want to become more familiar with it,
there's a good introduction at [Programming Ruby: The Pragmatic Programmer's Guide](http://docs.ruby-doc.com/docs/ProgrammingRuby/) 
(click on **Ruby.new** under **Contents** in the left-hand navigation pane on that site for a succinct
introduction for those new to Ruby). 

We'll explore just a little about how a computer "thinks", so you and the computer can communicate more 
effectively, but the real goal is to teach you how to solve problems in your world by translating them
into the computer's world. At minimum, the techniques shared here should help you have many more "aha!" 
moments when reading other people's code.

This document will cover the basic tools and craft of programming—
+ the basic types of data
+ the tools used to transform the data
+ how to order these transformations to create the final solution-- a computer program


## Data and its transformations

Here's the main insight of the course--a computer program is a series of transformations of existing data
into new, more useful data. This is also the main insight of what is called Object-Oriented Programming 
(OOP). OOP came from the recognition that a computer program is (or should be) made up of "objects" (which 
are collections of data, along with the transformations, or "methods", that can be applied to that data). 
An Object-Oriented programming language is one that explicitly supports this view, supplies some fundamental 
objects, and gives you the ability to create new, more complex objects, then combine these into a fully
functional program.

In an object-oriented language, you can:

+ extend an existing "class" (which is the definition of an object) by defining new methods for it 
  (that is, new ways to transform the existing data)
+ create a completely new class that combines existing types of data, and define some new methods to 
  transform this new data collection
+ create a "child" class from a "parent" class by "inheritance" (which usually involves adding more 
  data to the parent that is specific to the child, and extending the parent's methods to handle this 
  child's new data)

Why inherit? Code reuse! But the code to be reused is not so much taken from the methods of the "parent" 
class, but rather it is that code which you write to handle multiple instances of objects in the same 
family. 

For example, in a graphics program, you define a parent object which stands for anything that can 
be drawn (displayed). This parent class defines the fundamental properties (data) common to all graphics 
and the basic methods that will be used to create, define, store, retrieve, arrange, and draw an object. 
So, some of the data common to the parent and all its children might be its location on the display. 
And the parent will probably define a generic "draw" method, which in the parent's case might do nothing. 
You then define child classes which inherit these fundamental properties and methods, add any needed 
data for this particular kind of object (a radius for a circle, for example) and extend the "draw" method 
that is used to display it. 

Finally, you write additional steps in a "main" program section that allow you to create instances of the
graphics objects, position and display them on a common "canvas" (diagram) and save and retrieve your canvas. 
These steps are the code which is mainly reused--it is reused for all the various, drawable objects.


### A Metaphor

Cooking is an excellent metaphor for "data and its transformations". Even if you are following a recipe, that 
is really just the starting point for planning and executing a dish or a whole meal. Broadly speaking, there 
are 3 phases:

+ gather the initial ingredients and tools (mise en place)
+ combine and transform the ingredients (sift, stir, fry, roast...)
+ serve the final results ("dish" it up)

So, also in programming there are 3 phases:

+ Input the initial data
+ Combine and transform the data
+ Output the final results

Humans are good at learning, planning, and executing the steps needed to reach a final result. Given even 
a simple recipe, we know where to buy, say, an onion, how to chop it, and how to sauté it, whether or not 
all these details are described in the recipe. Computers not so much. They must be told, every time, how 
to perform each step in excruciating detail. That's what a program is. Fortunately, we have computer 
programming languages that provide some ready-to-use ingredients (data), along with some basic methods 
that can be applied to them. Keeping the programming language definition (syntax) in mind, we use an
editor to define and combine the needed ingredients (data) and steps (methods) into more and more complex
units. Then we use an "interpreter" or the output binary of a "compiler/linker" to execute our complex 
"recipe" and serve up the results.

So, this is your job as a programmer--first, get to know your basic ingredients and steps, then plan how 
to transform or combine these, creating ever more complex classes and methods, until you give the computer 
everything it needs to serve up a nourishing and delicious final result. 



### Object-oriented terminology and concepts in a nutshell

A review of Object-Oriented Programming terminology might help cement these concepts in our minds for future
use. The following is taken from **Object-Oriented Programming in Oberon-2** by Hanspeter Mössenböck, 
(Springer-Verlag, 1993):

The object-oriented way of thinking focuses on the data rather than on the procedures. The data and 
operations applicable to them constitute objects that can be asked to handle certain requests and to 
return data as their result… 

Which minimum set of features must a language provide in order to qualify as object-oriented? The most 
significant features are:
 
+ information hiding 
+ data abstraction 
+ inheritance
+ dynamic binding

**Information hiding** means that the implementation of complex data is encapsulated in objects and that 
clients have access only to an abstract view of it….

**Data abstraction**… An abstract data type is thus a unit consisting of data and the operations (methods) 
applicable to them…. 

**Inheritance**… means that an existing abstract data type can be extended to a new one that inherits all 
the data and operations of the existing type. The new type can include additional data and operations and 
can even modify inherited operations… An important consequence of inheritance is that the extended type is 
compatible with the original one. All algorithms that work with objects of the original type can also work 
with objects of the new type. This greatly promotes the reusability of existing algorithms.

The fourth characteristic of object-oriented programming languages is **dynamic binding** of messages 
(requests) to procedures. When the message `Area` is sent to an object, the decision regarding which procedure 
is to carry out the request is made at run time, i.e., dynamically. The compatibility between a type and 
its extensions makes it possible to store in a variable of type T not only objects of type T, but also 
objects of any extension of T. Thus a variable can be *polymorphic* (i.e., containing objects 
of multiple types). Depending on the type of the object stored in a variable at run time, messages are 
carried out differently….


### The Goal - heuristic methods

We always start with data, and end with data. But the data we end with is a transformation of the original 
data. So, we write programs to input (collect) the original data, transform it to create the final data, 
and output the results.

Ultimately, all data is represented in the computer by binary representations of integer values. And all 
transformations are done, ultimately, using the fundamental computer operations: arithmetic and logical functions, 
program control (branching), and data input, storage, and retrieval. Classes, methods, and programs are just 
increasingly complex sets of integers and these fundamental operations. However, knowing these fundamentals 
can help you design more efficient, less error-prone programs.

But, ultimately, what we want to give you is the following basic *heuristic*-- when faced with a problem that you 
wish to solve by scripting, ask yourself these three questions:

+ "What is the initial data?" 
+ "What is the result (also data) I want to obtain?"
+ "How do I transform the initial data to obtain the final result?"

You can apply these questions to your overall problem, albeit, initially perhaps, with a bit of hand-waving
vagueness. If your understanding is vague at first, that just means you have to identify sub-parts of the
problem and begin to tackle those next. And you do this by asking yourself those same questions repeatedly,
working your way toward getting your answers in terms the computer can also understand and implement.

You may find the initial and final data are well-defined, but the transformations you must apply are unclear.
Is there a logical "first step" transformation that is obvious? If so, what sort of data will we have after we
apply that transformation? Or, you might need to work backwards from the desired result--"If I had data in 
the form 'y', could I easily transform that into 'z'?" If the answer is "yes" then next you ask yourself, 
"how do I obtain 'y'?". You continue this way until you find yourself at 'x' or at a dead-end (and then you
may have to start over with another 'y').

Don't forget that, for many types of problems, you can teach the computer to do what you yourself do to solve 
the problem. In other words, maybe a bit of introspection is called for--"I solve the problem this way, so 
how do I tell the computer to do that?" Sometimes, you may find that what you were thinking of as a single 
mental step actually involves several, simpler sub-steps. Or, maybe you need to "model reality" differently 
using a more "mathematically-based" analogy. For example, and as we'll see in the code examples later, how 
do you know that your poker hand is a "straight"? Maybe it's easy for you to look at five cards at once and 
just "see" this. But break it down-- you may need to sort the cards in order by rank, then test each one 
after the first to see if its rank is exactly one more than the last. If it is not, stop, it's not a straight. 
If you get to the end and the test has been satisfied in every case, it is. Can you get a computer to proceed 
this way? You bet you can!

There's an excellent little book on heuristic methods like these that you can apply to solving problems in
mathematics and more broadly: 
[*How to Solve It: A New Aspect of Mathematical Method (Princeton Science Library)* by George Polya](https://a.co/d/0wNg5FF)
This book gives a brief summary of heuristic as follows:

1. Understanding the problem   

   + What is the unknown?
   + What are the data?
   + What is the condition?

   Is it possible to satisfy the condition? Is the condition sufficient to determine the unknown? Or is it 
   insufficient? Or redundant? Or contradictory? Draw a figure. Introduce suitable notation. Separate the 
   various parts of the condition. Can you write them down?

2. Devising a plan

   Have you seen it before? Or have you seen the same problem in a slightly different form? Do you know a 
   related problem? Look at the unknown! And try to think of a familiar problem having the same or a similar
   unknown. Here is a problem related to yours and solved before. Could you use it? Could you restate the 
   problem? Go back to definitions. You should obtain eventually a plan of the solution.

3. Carrying out the plan

   Carrying out your plan of the solution, check each step. Can you see clearly that the step is correct?
   Can you prove that it is correct?

4. Looking back

   Can you check the result? Can you check the argument? Can you derive the result differently? Can you see
   it at a glance? Can you use the result, or the method, for some other problem?


### Test, Debug, Refactor

Rarely is an algorithm perfect on the first go. Why? Because we often forget aspects of the broader context, or 
we haven't taken edge cases of our data into account. It's also possible our algorithm is "close" to the actual
solution we envisioned, but our implementation went off the rails somewhere. Whatever the reason, it is absolutely
necessary to test your code as you go. Don't wait until you have completed an entire solution, or even the
majority of one. 

+ Test the output results you get with "expected" or "normal" data as input.
+ Test the output results you get with "unexpected" or "abnormal" data as input.
+ Fix any bugs you find.
+ Reconsider your code, and the algorithms you have implemented, on the basis of your test results-
  + Is it correct?
  + Is it efficient?
  + Is it the best possible approach?

In other words, expect to continually debug and refactor your scripts as you approach the optimal solution.
This is another reason why the Object-Oriented Programming paradigm replaced the earlier "Waterfall"
approach--it implies, and makes it much easier, to develop parts of your solution, then debug or refactor
these, and work incrementally toward the greater complexity of the final script or program. This is especially
true because you are, at least implicitly, defining data interfaces between the levels of your solution. 
It is best when you can make these levels, and the data inputs and outputs of each level, explicit.
Both the levels you have chosen, their implementation, and the data which flows in and out of each level, 
will probably need to change as you go. Right up until the "end" (that is, when you have a working solution, 
as far as you can determine) anything, at any level, may need to change. So why not expect this rather than 
fight against it?


Next, we'll briefly review and comment on some of the basic ingredients (classes) available in Ruby and 
the predefined transformations (methods) those classes provide.


### Ruby's built-in classes

#### Integer class

This is the simplest data type that everything else we do with computers depends on. In fact, Integers 
are used in everything else we are about to do. "Characters" are actually integers we correlate with 
the basic symbols of our human languages: the letters of our alphabets, punctuation, symbols, and so on. 
The Ruby class "Time" uses Integers to record the date and time at which something took place as the 
number of seconds since the Epoch.

The transformations which the Integers undergo are the basic arithmetic operations (add, subtract, etc.) 
along with some "bit-twiddling" operations that can support the notions of masks and set operations (low-level
stuff you'll probably never have to worry about). They can be also be used for indexing Arrays (see below) 
or keeping track of the number of iterations of a loop. 


#### Float class

Most of the time we actually think of floating-point numbers (the Float class in Ruby) when we want to 
represent, and calculate with, numbers. They differ from Integers in important ways, although they are 
based on integers, ultimately. For our purposes, however, one difference is key--if you execute this 
code snippet:

```
i = 5
j = 2
puts i/j  # integer division
```

you get "2" as output, but if you execute this snippet:

```
m = 5.0
n = 2.0
puts m/n  # float division
```

then you get the expected "2.5" response as output. It's a wonderfully esoteric subject, but just note 
that, if you expect division to work as you normally expect, you want to use floating-point numbers 
rather than Integers. In Ruby, just add the decimal point and at least one fractional value (0 is fine) 
when you define number constants in your programs. And make sure any numbers you get as input (from a text 
file, for example) you convert to Float values if you want to use them to perform "financial" calculations.
(See the "to_f" method of the String class which converts text input into a floating-point number).


#### Boolean class

A Boolean object can be one of two possible values--true or false. These sorts of objects are used 
extensively, but you're probably most familiar with their use in conditional branching and looping 
(program control) statements, such as:

```
puts "I'd love to take you to lunch..."

if (your.salary > 100000.0) then
  puts "can I borrow $20 until next Tuesday?"
elsif (your.salary > 5000.0) then
  puts "let's go dutch."
else
  puts "but I already promised somebody else."
end
```

In the snippet above, there is no Boolean "variable" declared or assigned although boolean values are
created and used by the interpreter internally. This is common. It is rare to declare them. Of course,
the relation operator (">") placed between two numbers (the class variable "your.salary" and a numeric 
constant like "5000.0") produces a Boolean value, and the "if ... then ... elsif ... else ... end" 
syntax determines which steps are executed depending on the internal value. 

You should become familiar with the various ways Boolean values can be produced by the comparison of 
various types of other data (relational operators), and the ways Boolean values themselves can be combined 
to create complex conditional statements (logical operators, such as '&&' for "and", or '||' for "or").


#### Array class

An array is a set (collection) of data objects, all of which should be of the same "type" (to avoid 
confusing oneself). In Ruby, and some other scripting languages, being of the same "type" means the 
objects share at least some methods of the same name, although it doesn't matter if each element of 
the array is an instance of the same class, or even if the underlying representations of the data 
in the computer are the same. As long as each element can execute at least one method with the same 
name, and you only apply these commonly named methods, you'll be golden. This is called "duck 
typing"--if it walks like a duck and talks like a duck, it's a duck. So, if you throw a goose into 
your array, then ask each element of the array to "quack", you'll get an error. These kinds of errors
can be particularly hard to track down. We want you to avoid this shame and embarrassment.

There's not usually a reason to create a new "type" of array (that is, a new sub-class of Array) for 
each type of data object you're going to use in your array. A basic array works fine most of the time. 
Just remember what we said about quacking geese.

An array always has an implied order, reflected by each element's "index" (an integer from 0 to n-1, 
where n is the size, or "length", of the array). If we sort the array, we make the implied ordering into 
an actual one--for example, the element with the "lowest" value is now the first, and the one with the 
"highest" value is the last. To put this in computer lingo, the "lowest" value can be retrieved by 
accessing the element at index 0, and the "highest" at index n-1. 

We're putting "lowest" and "highest" in quotes because it may mean different things for different types 
of objects. If you've got a complex object, it could depend on just one part of the data, or it could
depend on a combination of parts. In Ruby, if you can come up with a method that returns -1, 0, or 1 
depending on whether one array element is lower than, the same as, or higher than another, you can get your 
array sort method for free. (The name of this method you define must be '<=>'. Since this is unpronounceable, 
we call it the "spaceship operator".)

Once you've got a sorted array, this makes finding and accessing one particular element much faster. Or, 
it might make it possible to derive a new type of data altogether. For example, if I want to know if my 
poker hand (an array of cards) is a straight, I can sort my cards and see if each one has exactly one 
higher rank than the last. This "straightness" becomes a new piece of data. On the other hand, to find out 
if I've got a flush, I don't need to sort the hand, but I need to iterate over all the cards to see if 
they have the same suit. That's yet another transformation of the existing data (the cards in my hand) 
into a new piece of data for the hand itself.

Ruby, and other languages, provide methods to access each element of an array, find a particular element, 
and to add a new element to, or delete an element from, an array. Some of these have odd names. Odd, that 
is, until you realize that an array can also be used to implement some important Computer Science concepts:

+ a **Queue** is like a line at the DMV--use this when the elements that were added first are supposed to be 
  processed first. If you just now arrived, get to the back of the line, otherwise we may have an angry mob 
  on our hands. (Use "shift" to get the first element from the line, and "<<" or "append" to put a newly 
  arrived item at the end. Use "unshift" when a special dignitary arrives and gets to go to the front 
  immediately.) 

+ a **Stack** is a distracted person's saving grace--use this when you have to take care of an element, but 
  then you realize that to do that you have to handle this other thing first, and that requires you to do 
  yet another thing first. Eventually, you'll work your way back to handling that first thing, you hope. 
  (In Ruby, you use "push" to put each new thing at the end of the array, then "pop" one off the end once 
  you're ready to deal with it.)

Perhaps you've noticed that many of the transformations we perform on the data in an array produce new 
data for a whole new conceptual level. For example, the ranks of each individual card in a poker hand 
give rise to the idea of the "straightness" of that hand--this is a concept regarding the collection (the
hand) rather than a member of that collection (a card). This is a good thing. Open your mind to the fact
that, in programming, you will often be creating and defining new concepts which are based on more "primitive"
ones. The computer cannot really "understand" what you are doing, but you can. Just make sure to base 
each new concept on a careful definition of its necessary parts and possible uses (data and transformations). 
It requires disciplined thinking, using the "rules of logic", to express this correctly, both in human 
language (philosophy), and computer language (a program). 

You should avoid adding data to a class that is superfluous, but you must also maintain information on
meaningful variants. If a piece of data indicates a variant that significantly alters behavior (that is, 
the way we handle a variant in a method's logic), we may want to create a parent class and several 
child classes, where each child embodies a particular value of the variant data. In this case, you don't
need to store the data that denotes the variant, it is implied by the child class. You can accomplish the
same thing by creating several, similar but not related classes, each of which embodies a particular 
variation. Just remember to document them well (for others and also for your future self). So, to reiterate,
if you find a method is testing for many possible variations of some piece of data, it may be time to 
re-classify (create a new set of classes).


#### String class

Strings are used to store and manipulate human language (think of a text file), or a computer language, 
which may encapsulate human language (think of a DocBook XML file). A string is, actually, an array of 
characters. (Although Ruby has pretty much given up on dealing with individual characters, preferring 
instead to work with strings of length 1 when necessary.) Given everything we just said about arrays, 
take a moment to reflect on the implications of this for Strings (there's lots of things you can do 
with the individual characters in a String). Possibly more important, however, is the use of Regular
Expressions to parse Strings into smaller bits, like words in a sentence, or parts of words themselves. 
Regular Expressions are such a broad topic that they can only be properly served by a another discussion
of their own.


#### Hash class

In Ruby, a Hash is like an Array, but each "value" (element) is retrieved by referencing its "key" rather 
than its index. So, what's a Hash good for?

+ To easily categorize your data conceptually (key = concept).
+ To keep track of how much (value) of something (key) you have, for example: 
  `words["the"] += 1 # count another occurrence of "the" in a string`.
+ To make a translation table (a specific key translates to a specific value).
+ To implement an array with sparse indices (e.g. only use indices 100, 200, 404, …)

You can also use a Hash to package together several related pieces of information. This is similar to what
you can do with a C language "struct" (a block of memory with named data elements). Say you want to have a
method return meta-information about an array--the sum of all values in the array, along with the mean and 
maybe even the standard deviation. You could package all these together in a Hash which you pass as the result 
of a method which calculates these, using the obvious names as keys for each piece of data (values). You could 
also do this with an array, but in that case you'd need to keep track, somewhere, of what the value at each 
index of the array signifies. A Hash makes this easier. If you're afraid you'll forget what names (keys) you
used, let the interpreter help you; make a new class for this "struct" and the interpreter will enforce the
use of the right names for each value.



### I/O, File and Dir classes

These classes deal with the computer's file system, peripherals, I/O and such. In some cases, we use the 
"class methods" (you call a class method directly on the class itself, for example `File.open`), you don't 
have to create an instance of the class. 

Some methods in Ruby that are particularly useful are:
+ gets (return an input string from "$stdin")
+ print, puts (send an output string to "$stdout", without or with a carriage-return)
+ Dir.glob (returns the names of the files in a specific directory, with pattern matching)
+ File.open (creates/reads/writes a file on disk)


Let's do a [Fagan Inspection](https://en.wikipedia.org/wiki/Fagan_inspection) (a static analysis technique), while always remembering to
ask ourselves: 
+ "What is the initial data and where did it come from?"
+ "What transformations does this data undergo?"
+ "What is the data which is, ultimately, produced by this set of transformations?"
+ "Where does this resulting data go? (Does it become the input to some other part of the program, or is it displayed to the user?")


**CardGames.rb**

```
#!ruby

class Card

  attr_accessor :rank   # Integer
  attr_accessor :suit   # Integer
  attr_accessor :value  # Array of Integer

  RANKS = %w{ Ace Two Three Four Five Six Seven Eight Nine Ten Jack Queen King }  
  SUITS = %w{ Spades Clubs Diamonds Hearts }
  VALUES = [[1, 11], [2], [3], [4], [5], [6], [7], [8], [9], [10], [10], [10], [10]]


  # initialize: Create a Card instance
  # @param   rank      the card's rank [Integer] (see RANKS)
  # @param   suit      the card's suit [Integer] (see SUITS)
  # @param   value     the card's value in Blackjack [Array of Integer] (see VALUES)
  # @return            Card (instance)
  def initialize(rank, suit, value = nil)
    @rank = rank
    @suit = suit
    @value = (value.nil? ? VALUES[rank] : value)
  end


  # to_s: Convert this node to a string representation.
  # @return  [String]  the string representation
  def to_s
    "#{RANKS[@rank]} of #{SUITS[@suit]}"
  end

  # <=>: 
  # @param   b         the other card compared 
  # @return            -1, 0, +1 if a < b, a = b, a > b
  def <=>(b)
    self.rank <=> b.rank
  end  # <=>

end # Card


class Deck < Array

  attr_accessor :flushness
  attr_accessor :straightness
  attr_accessor :combos


  def how_straight?
    result = []
    if self.length > 1 then
      d = self.sort
      prev_rank = d[0].rank
      result << [d[0]]
      d[1..-1].each do |card|
        if card.rank == (prev_rank + 1) then
          result[-1] << card
        else
          result << [card]
        end
        prev_rank = card.rank
      end
      # allow for wrap-around...
      if (d[-1].rank == (d[-1].class::RANKS.length - 1)) && (d[0].rank == 0) then
        # remove ace from first group and put it in last group...
        result[-1] << result[0].shift
        result.shift if result[0].empty?
      end
    end
    result.sort! {|a,b| b.length <=> a.length }  # put the largest group at the beginning
    # result.unshift [result[0].length]  # put size of largest group at beginning
    return result
  end  # how_straight?


  def how_flush?
    suit_cards = {}
    self.each do |card|
      # cs = card.class::SUITS[card.suit]  # use string assoc. with suit
      cs = card.suit
      if suit_cards.has_key?(cs) then
        suit_cards[cs] << card
      else
        suit_cards[cs] = [card]
      end
    end
    a = suit_cards.values
    a.sort! {|a,b| b.length <=> a.length }  # sort (decreasing) by number of cards in group
    # a.unshift [a[0].length]  # put size of largest group at beginning
    return a
  end  # how_flush?


  def what_combos?
    rank_cards = {}
    self.each do |card|
      # cr = card.class::RANKS[card.rank]  # use string assoc. with rank
      cr = card.rank
      if rank_cards.has_key?(cr) then
        rank_cards[cr] << card
      else
        rank_cards[cr] = [card]
      end
    end
    a = rank_cards.values
    a.sort! {|a,b| b.length <=> a.length }  # sort (decreasing) by number of cards in group
    # a.unshift [a[0].length]  # put size of largest group at beginning
    return a
  end  # what_combos?


  def look
    @flushness = self.how_flush?
    @straightness = self.how_straight?
    @combos = self.what_combos?
  end  # look


  def to_s
    self.join(", ")
  end

end  # Deck


class PokerDeck < Deck

  attr_accessor :value          # i.e. based on odds against and high card
  attr_accessor :description

  MAX_VALUE = (8 * Card::RANKS.length) + Card::RANKS.length


  def initialize(create_cards = true)
    super()
    if create_cards then
      Card::RANKS.each_index do |r|
        Card::SUITS.each_index do |s|
          self << Card.new(r, s, Card::VALUES[r])
        end
      end
    end
  end


  def evaluate(discards = nil)
    # calculate value/description of hand and discard cards if discard deck given...
    #   returns how many cards discarded
    #

    the_ranks = self[0].class::RANKS  # assumes all cards of same type
    ranks_length = the_ranks.length
    look()
    how_many = 0

    if @straightness[0].length > 4 &&
       @flushness[0].length > 4 then
      # >>> a straight flush, stand pat!
      if @straightness[0].last.rank == 0 then
        # ace high...
        @description = "a royal flush"
      else
        @description = "a straight flush"
      end
      @value = (8 * ranks_length) + (@straightness[0][0].rank == 0 ? ranks_length : @straightness[0][0].rank)
    
    elsif @combos[0].length > 3 then
      # >>> four of a kind, stand pat!
      @description = "four of a kind"
      @value = (7 * ranks_length) + (@combos[0][0].rank == 0 ? ranks_length : @combos[0][0].rank)
    
    elsif @combos[0].length == 3 &&
          @combos[1].length == 2 then
      # >>> a full house, stand pat!
      @description = "a full house"
      @value = (6 * ranks_length) + (@combos[0][0].rank == 0 ? ranks_length : @combos[0][0].rank)
    
    elsif @flushness[0].length > 4 then
      # >>> a flush, stand pat!
      @description = "a flush"
      @value = (5 * ranks_length) + (@straightness[0][0].rank == 0 ? ranks_length : @straightness.last.last.rank)
    
    elsif @straightness[0].length > 4 then
      # >>> a straight, stand pat!
      @description = "a straight"
      @value = (4 * ranks_length) + (@straightness[0].last.rank == 0 ? ranks_length : @straightness[0].last.rank)
    
    elsif @combos[0].length == 3 then
      # >>> three of a kind, discard up to 2...
      @description = "three of a kind"
      @value = (3 * ranks_length) + (@combos[0][0].rank == 0 ? ranks_length : @combos[0][0].rank)
      if !discards.nil? && @combos.length > 1 then
        @combos[1..-1].each do |a|
          a.each do |card|
            if card.rank < 10 || card.rank != 0 then 
              # neither ace nor face...
              how_many += 1
              discards << self.delete(card)
            end
          end
        end
      end
    
    elsif @combos[0].length == 2 &&
          (@combos[1] && @combos[1].length == 2) then
      # >>> two pairs, discard 1 if not an ace...
      @description = "two pairs"
      @value = 0  # to start
      @combos[0..1].each do |a|
        v = (2 * ranks_length) + (a[0].rank == 0 ? ranks_length : a[0].rank)
        @value = v if v > @value
      end
      if !discards.nil? then
        @combos[2..-1].each do |a|
          a.each do |card|
            if card.rank != 1 then
              how_many += 1
              discards << self.delete(card)
            end
          end
        end
      end
    
    elsif !discards.nil? &&
          @flushness[0].length > 3 &&
          @flushness.length > 1 then
      # try to draw to a flush (should be discard 1)...
      @description = "hoping for a flush"
      # hand's value is nothing, so use high card's value for hand's value...
      @value = (@straightness[0][0].rank == 0 ? ranks_length : @straightness.last.last.rank)
      if @flushness.length > 1 then
        @flushness[1..-1].each do |a|
          a.each do |card|
            how_many += 1
            discards << self.delete(card)
          end
        end
      end
    
    elsif !discards.nil? && 
          @straightness[0].length > 3 &&
          @straightness.length > 1 then
      # try to draw to a straight (should be discard 1)...
      @description = "hoping for a straight"
      # hand's value is nothing, so use high card's value for hand's value...
      @value = (@straightness[0][0].rank == 0 ? ranks_length : @straightness.last.last.rank)
      @straightness[1..-1].each do |a|
        a.each do |card|
          how_many += 1
          discards << self.delete(card)
        end
     end   
    
    elsif @combos[0].length == 2 then
      # >>> a pair, discard up to 3 if not ace's...
      @description = "a pair"
      @value = ranks_length + (@combos[0][0].rank == 0 ? ranks_length : @combos[0][0].rank)
      if !discards.nil? && @combos.length > 1 then
        @combos[1..-1].each do |a|
          a.each do |card|
            if card.rank != 1 then
              how_many += 1
              discards << self.delete(card)
            end
          end
        end
      end
    
    else
      # >>> nada, discard lowest three...
      a = self.sort
      @description = "nothing"
      @value = (a[0].rank == 0 ? ranks_length : a.last.rank)  # odds: 0 
      if !discards.nil? then
        a.each do |card|
          how_many += 1
          discards << self.delete(card) 
          break if how_many >= 3
        end
      end
    end

    return how_many 
  end  # evaluate


end # PokerDeck


class BlackJackDeck < Deck

  attr_accessor :values

  def initialize(create_cards = true)
    super()
    if create_cards then
      Card::RANKS.each_index do |r|
        Card::SUITS.each_index do |s|
          self << Card.new(r, s, Card::VALUES[r])
        end
      end
    end
  end


  def what_values?
    # for Blackjack
    result = [0]
    self.each do |card|
      prev_result = Array.new(result)
      len = result.length
      card.value.each_index do |i|
        result += prev_result if i > 0 
        len.times do |j|
          result[(i * len) + j] += card.value[i]
        end
      end
    end
    result.uniq! if result.length > 1
    return result
  end  # what_values?


  def look
    @values = self.what_values?   # for Blackjack
  end  # look


end # BlackJackDeck


class PokerPlayer

  attr_accessor :name         # String
  attr_accessor :human        # Boolean (if false then computer plays their hand)
  attr_accessor :purse        # Integer > 0
  attr_accessor :hand         # PokerDeck
  attr_accessor :active       # Boolean (if false then player folded)
  attr_accessor :bluffing     # Boolean (if true then player will bet more than hand value indicates)
  attr_accessor :current_bet  # Integer

  def initialize(name, purse, hand = PokerDeck.new(false))
    @name = name
    @purse = purse
    @hand = hand
  end

  def show_hand
    result = ""
    @hand.each_index {|i| result << "[#{(i + 1).to_s}] #{@hand[i]}  " }
    return result
  end  # show_hand

end  # Player
```



**poker.rb** 

```
#!ruby

$LOAD_PATH << File.dirname($0) + "/lib"

require 'CardGames'

if __FILE__ == $0 then
  # The game is afoot...
  puts "Welcome to our poker game! Have a seat..."

  names = %w(Ada Beatrice Christine Elizabeth Frances Grace)
  print ">>>What is your name? "
  my_name = gets.chomp
  names.unshift my_name

  print ">>>How many players (besides yourself, max. 5)? "
  pnum = gets.to_i + 1
  player = []
  pnum.times do |i|
    player << PokerPlayer.new(names[i], 124)
  end
  player[0].human = true

  the_pot = 0  # money!
  prng = Random.new      # will determine if player bluffs 

  loop do

    # ante up! 
    # if a player hasn't got sufficient funds, they're out of the game...
    puts "\nAnte up!"
    outs = []
    player.each_index do |i|
      if player[i].purse < 3 then 
        outs << i
        if player[i].human then
          puts "Sorry, but you don't have sufficient funds to continue playing."
          exit 
        else
          puts "#{player[i].name} doesn't have sufficient funds to continue playing."
          puts "Goodbye, #{player[i].name}!"
        end
      else
        # player has at least one chip each for ante, first and second rounds of betting
        player[i].purse -= 1
        player[i].active = true
        the_pot += 1
      end
    end
    outs.each {|o| player.delete_at(o) }

    deck = PokerDeck.new
    discards = PokerDeck.new(false)

    deck.shuffle!

    puts "\nDealing..."
    # deal for 5-card draw...
    5.times do |i|
      pnum.times do |j|
        player[j].hand << deck.pop
      end
    end


    # discards?...
    pnum.times do |i|
      if player[i].human then
        puts "\nYou have: #{player[i].show_hand}" 
        my_discards = []
        done = false
        while !done do
          print ">>>Which card(s) # do you want to discard? (ex. '1' or '1, 2, ...', 0 to stop) "
          d = gets
          # allow for entry as list separated by commas...
          a = d.split(",")
          a.each_index do |i|
            cnum = a[i].to_i
            if cnum > 5 || cnum < 0 then
              puts "Sorry! you don't have a card ##{cnum}, try again."
              done = false
              my_discards.clear
              break
            elsif cnum == 0 then
              done = true
            else
              my_discards << cnum
              done = (i > 0)
            end
          end
        end
        my_discards.sort! {|a,b| b <=> a }
        my_discards.each do |cnum|
          discards << player[i].hand.delete_at(cnum - 1)
        end
        # second draw...
        my_discards.length.times do |j|
          player[i].hand << deck.pop
        end
        puts "You now have: #{player[i].hand.join(", ")}" 
      else
        how_many = player[i].hand.evaluate(discards)
        puts "#{player[i].name} discards #{how_many} cards"
        # second draw...
        how_many.times do |j|
          player[i].hand << deck.pop
        end
      end
    end

    player.each do |p| 
      p.current_bet = 0 
      p.hand.evaluate 
      p.bluffing = (!p.human && prng.rand(24) == 12) 
    end

    # betting...
    puts "\nPlace your bets!"
    current_bet = 0
    loop do
      # puts "The current bet is #{current_bet}."
      player.each do |p|
        if p.active then
          if p.human then
            # $stderr.puts "#{p.name}/#{p.active.to_s}: purse=#{p.purse} value=#{p.hand.value} p.current_bet=#{p.current_bet}"   # debug
            dd = current_bet - p.current_bet
            next if dd == 0 && current_bet > 0
            puts "\nYou have #{p.purse} coins in your purse."
            print ">>>The current bet is #{current_bet}. Your bet so far is #{p.current_bet}. Do you want to #{current_bet == 0 ? "[c]heck" : "[c]all"}, [r]aise, or [f]old? "
            got_it = false
            while !got_it do
              response = gets.chomp
              case response
                when /^\s*c/i then
                  p.current_bet += dd
                  p.purse -= dd
                  the_pot += dd
                  puts "#{p.name} #{current_bet == 0 ? "checks" : "calls."}"
                  got_it = true
                when /^\s*r/i then
                  print ">>>How much do you want to raise? "
                  more = gets.chomp.to_i
                  if more > 0 then
                    delta = (more + current_bet) - p.current_bet
                    if delta > 0 then
                      if p.purse >= delta then
                        current_bet += more
                        p.current_bet = current_bet
                        p.purse -= delta
                        the_pot += delta
                        puts "#{p.name} raises #{more.to_i}. The bet is now #{current_bet}."
                        got_it = true
                      else
                        puts "Sorry, you don't have sufficient funds in your purse. Do you want to [c]all, [r]aise, or [f]old? "
                      end
                    end
                  else
                    puts "Sorry, I didn't understand that. Do you want to [c]all, [r]aise, or [f]old? "
                  end
                when /^\s*f/i then
                  p.active = false
                  puts "#{p.name} folds."
                  got_it = true
                else
                  puts "I didn't get that... Do you want to #{current_bet == 0 ? "[c]heck" : "[c]all"}, [r]aise, or [f]old? "
              end
            end
          else
            best_bet = p.hand.value / (Card::RANKS.length + 1)
            best_bet *= 5 if p.bluffing
            delta = best_bet - current_bet
            delta = p.purse if delta > p.purse
            # $stderr.puts "#{p.name}/#{p.active.to_s}: purse=#{p.purse} value=#{p.hand.value} p.current_bet=#{p.current_bet} current_bet=#{current_bet} best_bet=#{best_bet} delta=#{delta} bluffing=#{p.bluffing}"   # debug
  
            if current_bet == 0 then
              if delta > 0 then
                p.current_bet += delta
                current_bet += delta
                p.purse -= delta
                the_pot += delta
                puts "#{p.name} bets #{delta}"
              else
                puts "#{p.name} checks"
              end
            elsif delta > 1 && (p.current_bet < current_bet) then
              current_bet += delta
              dd = current_bet - p.current_bet
              p.current_bet += dd
              p.purse -= dd
              the_pot += dd
              puts "#{p.name} raises #{delta.to_i}. The bet is now #{current_bet}."
            elsif delta >= 0 && (current_bet > p.current_bet) then
              dd = current_bet - p.current_bet
              p.current_bet += dd
              p.purse -= dd
              the_pot += dd
              puts "#{p.name} calls."
            elsif delta < 0 then
              puts "#{p.name} folds"
              p.active = false
            end
          end
        end
      end
      done = true
      player.each {|p| done &&= (!p.active || (p.current_bet == current_bet)) }
      break if done
    end


    puts
    winning_hand_value = 0
    winner = nil 
    player.each do |p| 
      if p.active then
        puts "#{p.name} has #{p.hand.join(", ")}"
        puts "  #{p.hand.description}"
        if p.hand.value > winning_hand_value then
          winning_hand_value = p.hand.value
          winner = p
        end
      end
    end
    
    puts "#{winner.name} wins this hand!"
    winner.purse += the_pot
    the_pot = 0

    #clean up...
    player.each {|p| p.hand.clear }  # get rid of each player's cards from the last hand (play)
    player << player.shift  # rotate

    print "\n>>>Do you want to play again? [y/n] "
    again = gets.chomp
    break if again =~ /^\s*n/i
  end  # loop

  player.each {|p| puts "#{p.name}'s purse is #{p.purse}." }
  puts "Goodbye until next time!" 
end
```



