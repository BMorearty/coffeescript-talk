!SLIDE subsection

# PART 4: Why Rubyists Might Like CoffeeScript

!SLIDE

# a.k.a. The Fun Part

![fun part](../images/funpart.jpg)

!SLIDE

# CoffeeScript Has Good Stuff From:

![Ruby](../images/ruby.gif) +
![JavaScript](../images/javascript.gif) +
![Python](../images/python.png) 

=

![CoffeeScript](../images/coffeescript.png)

(But it seems most heavily influenced by Ruby.)

!SLIDE center

# Semicolons

## Just Like Ruby

    @@@coffeescript
    pi = 3.14159

!SLIDE execute

# Parentheses

## Almost Like Ruby

    @@@coffeescript
    console.log calc result

compiles to:

    @@@javascript
    console.log(calc(result));

!SLIDE

# But If Not Passing Any Parameters...

## Parens Are Required

    @@@coffeescript
    redAlert()

!SLIDE

![stabby croc](../images/stabby_croc.jpg)

# Stabby Proc

## Like Ruby 1.9

* Except params come before stabby
* Stabby proc is THE WAY to define a function

!SLIDE execute

# Stabby Proc Example

    @@@ coffeescript
    fib = (n) ->
      return n if n in [0,1]
      fib(n-1) + fib(n-2)

    result = fib(10)

!SLIDE execute

# No Params -> No Parens

    @@@ coffeescript
    clearFlash = ->
      $('.flash').html('')

!SLIDE execute

# String Interpolation

## Just Like Ruby

    @@@ coffeescript
    greeting = 'allo'
    result   = "You had me at #{greeting}"

!SLIDE execute

# Heredocs With String Interpolation

## Just Like Ruby

    @@@ coffeescript
    name = 'Inigo Montoya'
    result = """
             Hello. My name is #{name}.
             You killed my father.
             Prepare to die.
             """

.notes Only double-quoted heredocs have string interpolation.

!SLIDE

# Ending a Block of Code

## Like Python & Haml, Not Ruby

    @@@coffeescript
    if milk.spilled()
      $('#message').html("Don't cry")
    
    result(speed) = ->
      if speed > 65
        "ticket"
      else
        "you're good"

!SLIDE 

# Default Values For Arguments

## Just Like Ruby

    @@@ coffeescript
    loadData = (page = 1) ->
      $(data).load("/data?page=#{page}")

!SLIDE

# Variables Declared at First Assignment

## Just Like Ruby

<!-- * No "var" keyword. Assign a variable to declare it.-->

    @@@ coffeescript
    movie = 'School of Rock'

compiles to:

    @@@javascript
    var movie;
    movie = 'School of Rock';

!SLIDE 

# To Reference a Variable in Two Methods

## Assign a Value

    @@@coffeescript
    cache = undefined
    store: (value) ->
      cache = value
    retrieve: ->
      cache

.notes "This behavior is effectively identical to Ruby's scope for local variables."

!SLIDE

# Speaking of Variables: No Globals

.notes All Output Code Is Wrapped in an Anonymous Function

    @@@ javascript
    // generated JavaScript goes in anon func
    (function() {
      # ur codez go hear
    })();

&nbsp;

    @@@ coffeescript
    # I want to access this from other files
    window.regions = ['West','East',
                      'North','South']

!SLIDE 

# Postfix `if`

## Just Like Ruby

    @@@ coffeescript
    return true if found

!SLIDE

# `unless` and postfix `unless`

## Just Like Ruby

    @@@ coffeescript
    die() unless lives > 0

!SLIDE 

# Everything Is an Expression

## Just Like Ruby

.notes At least, as much as possible. break, continue, and return are not converted to expressions.

* Last statement is an implied `return`.

!SLIDE execute smaller center

# No Ternary Operator

## But `if`/`then`/`else` Is an Expression

    @@@ coffeescript
    language = if serverside then 'ruby' else 'coffeescript'

!SLIDE

# `for` Loop Syntax Is...

## Just Like Ruby

    @@@ coffeescript
    for movie in ['The Princess Bride',
                  'West Side Story']
      record movie

.notes Use 'for own key, value of object' to loop over
'hasOwnProperty()' properties.

!SLIDE execute

# Ranges

## A Lot Like Ruby

    @@@ coffeescript
    result = [ 1..5 ]

&nbsp;

    @@@ coffeescript
    result = [ 1...5 ]

.notes Like Ruby, two dots includes the last value and three dots excludes it.

!SLIDE

# `@property`

## Just Like Ruby

* Shortcut for `this.property`

!SLIDE

# `then`

## Just Like Ruby

    @@@ coffeescript
    if hasKey then enter()

* Useful for 1-line if and case statements

!SLIDE

# The Existential "`?`" Operator

## Like Ruby's `.nil?`

    @@@ coffeescript
    if expression
      # not null, undefined, false,
      # "", 0, or NaN
    if expression?
      # neither null nor undefined

!SLIDE

# Multiple Assignments in a Single Statement

## Similar to Ruby

    @@@ coffeescript
    [oldMax, max] = [max, newMax]
    [firstName, lastName] = getName()

!SLIDE subsection

# What is the One Way CoffeeScript is Even Better Than Ruby?

!SLIDE execute

# "`?.`"

## Like Ruby's `try` or `andand` Gem
## Nicer Syntax Than Ruby

    @@@ coffeescript
    person = null
    result = typeof(person?.name)

.notes If ?. is called on null or undefined it returns undefined instead of raising TypeError. "Accessor variant of the existential operator."

!SLIDE execute

# Good for Function Chaining

    @@@ coffeescript
    person = {}
    oldestKid = person.kids?[0]?.name?.first
    result = typeof(oldestKid)

