<!--
author:   André Dietrich

email:    LiaScript@web.de

version:  0.0.1

language: en

narrator: US Male Female

comment:  A template for importing tiny-turtle and using it for teaching
          JavaScript.

script:   https://cdn.jsdelivr.net/gh/LiaTemplates/tiny-turtle/tiny-turtle.js

@TinyTurtle: @TinyTurtle.eval(@uid,@0,@1,@2)

@TinyTurtle.eval
<script>
send.handle("input", (cmd) => {
  try{
    let rslt = eval(cmd);
    if (rslt)
      console.log(rslt)
  } catch (e) {
    console.error("error", e)
  }
});

function stop() {
  send.lia("LIA: stop")
}

window.TinyTurtle("turtle_@0")

@input

if ("@3" == "true")
  "LIA: terminal"
</script>


<canvas id="turtle_@0" width="@1" height="@2"></canvas>

@end

-->

# TinyTurtle

**TinyTurtle** is a minimalist
[Turtle Graphics](http://en.wikipedia.org/wiki/Turtle_graphics) implementation
using the [Canvas element](http://en.wikipedia.org/wiki/Canvas_element),
consisting of about 60 lines of JavaScript code.

The library is intended for use in teaching scenarios where learners have access
to a simple HTML editing environment such as
[Thimble](https://thimble.webmaker.org) or [jsbin](http://jsbin.com). Learners
should have a basic knowledge of HTML, but do not need any JavaScript
experience.

The implementation is kept as minimal as possible so that learners are
encouraged to view its source, understand it, and build upon it.

## Import

There are three ways to use this template. The easiest way is to use the
`import` statement and the URL of the text-file of the master branch or any
other branch or version. But you can also copy the required functionality
directly into the header of your Markdown document. And of course, you could
also clone this project and change it, as you wish.

1. Load the macros via

   `import: https://github.com/liaTemplates/tiny-turtle/README.md`

2. Copy the definitions into your Project

3. Clone this repository on GitHub


## `@TinyTurtle(width,height,?shell)`

Simply attach the `@TinyTurtle(300,300,true)` macro directly to the end of your
JavaScript code snippet, in order to make it executable. The  first two
parameters will define the width and the height of the canvas, the turtle will
walk around. The last parameter is optional, set it to `true` if you want to
enable a console input, which lets you enter your commands dynamically.

``` JavaScript
function box(length) {
  for (var i = 0; i < 4; i++) {
    forward(length);
    right(90);
  }
}

penStyle = 'purple';
box(90);
left(10);
box(80);
left(10);
box(70);
```
@TinyTurtle(300,300,true)


## TinyTurtle - Methods

**`forward(amount)`**

Move the turtle forward by the given number of pixels. If the pen is down, a
line is drawn from its previous position to its new position.

The `fd` method can be used as shorthand for this.

**`left(degrees)`**

Rotate the turtle to its left by the given number of degrees.

The `lt` method can be used as shorthand for this.

**`right(degrees)`**

Rotate the turtle to its right by the given number of degrees.

The `rt` method can be used as shorthand for this.

**`stamp()`**

Draw the turtle as a triangle that represents its current state in the following
ways:


* The triangle is drawn at the turtle's current position.
* The triangle is pointing in the direction that the turtle is currently
  oriented towards.
* If the pen is up, the triangle is drawn as an outline; otherwise, it's
  filled.
* The color and outline of the triangle is drawn using the current pen
  style and pen width.

**`penUp()`**

Put the pen up, so that movements by the turtle don't draw anything on the
canvas.

**`penDown()`**

Put the pen down, so that movements by the turtle draw a path on the canvas.

**`clear()`**

Clear the canvas with all drawings.

### Properties

**`penStyle`** (read/write)

A string describing the style that the turtle's path is drawn in. This
can be represented as any one of:

* A hexadecimal color like `#00FF00`
* A [RGBA](http://www.w3.org/TR/css3-color/#rgba-color) quad like
  `rgba(0, 255, 0, 0.5)`
* A [HSLA](http://www.w3.org/TR/css3-color/#hsla-color) quad like
  `hsla(50, 100%, 50%, 0.5)`
* A [CSS color name](http://www.w3.org/TR/css3-color/#svg-color) like `red`.

**`penWidth`** (read/write)

The width of the turtle's path, in pixels.

**`canvas`** (read-only)

The
[HTMLCanvasElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLCanvasElement)
the turtle is drawing on.

**`rotation`** (read-only)

The current rotation of the turtle, in degrees.

**`position`** (read-only)

The current position of the turtle, as an object with `x` and `y` properties.

**`pen`** (read-only)

The string `up` or `down` indicating the current state of the turtle's pen.

## Supported Browsers

This code has been tested on Internet Explorer 10, Safari 6 (desktop and iOS),
Chrome 30, Opera 17, and Firefox 24.

## License

Public Domain
[CC0 1.0 Universal](http://creativecommons.org/publicdomain/zero/1.0/).

# Tutorial

Before embarking on this journey, you may want to check out
[JavaScript For Cats](http://jsforcats.com) or
[Eloquent JavaScript](http://eloquentjavascript.net) to understand the basics of
the language. Or you can just start hacking and learn things from the glossary
as you go.


> __Tinkering Tips__
>
> > Programmers care more about making it work eventually rather than trying to
> > make it work the very first time. The best way to learn is by making
> > mistakes!
> >
> >[@maxogden](https://twitter.com/maxogden), JavaScript for Cats
>
> __Fear not.__ Nothing you type on this page will damage your computer in any
> way. Programming is all about tinkering, with curiosity guiding your path.
>
> __Play around.__ If you don't understand what a piece of code is doing, try
> changing it. What happens when you remove the code? Or when you change a
> number in it? Or when you copy and paste it somewhere else?
>
> __Ask for help.__ If you're stumped, you can always invite a friend to help
> you out.

## I. Square

> Turtle geometry is a different style of doing geometry, just as Euclid’s
> axiomatic style and Descartes’s analytic style are different from one another.
> Euclid’s is a logical style. Descartes’s is an algebraic style. Turtle
> geometry is a computational style of geometry.
>
> Seymour Papert, Mindstorms

The TinyTurtle API makes it easy to experiment with Turtle geometry.

The `forward` function tells the Turtle to move forward by some number of
pixels.

The `right` function tells it to turn right by some number of degrees.

The `stamp` function tells it to draw its current state: that is, its position
and orientation. This is visualized as a small, pointy triangle.

Can you add to the code below to make the Turtle draw a square 100 pixels wide
and end with the same state that it started?

``` javascript
forward(100);
right(90);

stamp();
```
@TinyTurtle(400,300,true)

<details>

<summary>See Atul's solution</summary>

``` javascript
// Here is Atul's solution to the square problem.
forward(100);
right(90);
forward(100);
right(90);
forward(100);
right(90);
forward(100);
right(90);

stamp();
```
@TinyTurtle(400,300)

</details>

> __Hint:__ If you're having trouble, try to "play Turtle." Stand up and move
> your body as the Turtle on the screen must move in order to make the pattern
> you want.


## II. Squares

If we encapsulate our square-drawing code into a function that takes an argument
specifying the size of square to draw, we can use it as a building block for
more interesting things.

Can you complete the code below?

``` javascript
function square(width) {
  // Fill in this function!
}

square(100);
right(20);
square(80);
right(20);
square(60);

stamp();
```
@TinyTurtle(400,300,true)


<details>

<summary>See Atul's solution</summary>

``` javascript
// Here is Atul's solution to the squares problem.
function square(width) {
  for (var i = 0; i < 4; i++) {
    forward(width);
    right(90);
  }
}

square(100);
right(20);
square(80);
right(20);
square(60);

stamp();
```
@TinyTurtle(400,300)

</details>


> __Code Is For People__
>
> > Programs must be written for people to read, and only incidentally for
> > machines to execute.
> >
> > -- _Hal Abelson & Gerald Sussman,_
> > _Structure and Interpretation of Computer Programs_
>
> > See, all my procedures are mind-size bites.
> >
> > -- _Robert, a seventh grader, Mindstorms_
>
> Writing functions keeps our code compartmentalized into mind-size bites that
> are easy for humans to understand. Whenever you're having trouble
> understanding your own code—and especially when you notice yourself
> copying-and-pasting lots of chunks of it—consider splitting it up into
> functions to make it more concise and easier to grasp. This process is called
> refactoring and it's a useful practice that even professional programmers
> struggle to do regularly.


## III. Triangle

One of the principles of Turtle geometry is called the
__Total Turtle Trip Theorem__:

> If a Turtle takes a trip around the boundary of any area and ends up in the
> state in which it started, then the sum of all turns will be 360 degrees.
>
> _Seymour Papert, Mindstorms_

Can you use this theorem to fix the code below, which is trying to draw an
equilateral triangle and finish with the Turtle in the same state that it
started? You just need to replace `SOMETHING` with an actual number.

``` javascript
for (var i = 0; i < 3; i++) {
  forward(100);
  right(SOMETHING);
}

stamp();
```
@TinyTurtle(400,300,true)


<details>

<summary>See Atul's solution</summary>

``` javascript
// Here is Atul's solution to the triangle problem.
for (var i = 0; i < 3; i++) {
  forward(100);
  // The turtle needs to make 3 identical turns to draw a triangle, and
  // since they all need to add up to 360, that means each turn should be
  // 360 divided by 3, or 120 degrees.
  right(120);
}

stamp();
```
@TinyTurtle(400,300)

</details>

## IV. Circle

Can you use the Turtle Total Trip Theorem to finish this function that draws a
circle based on a given circumference, and returns with the Turtle in its
original state?


``` javascript
function circle(circumference) {
  // Draw a circle here.
}

circle(300);
stamp();
```
@TinyTurtle(400,300,true)


<details>

<summary>See Atul's solution</summary>

``` javascript
// Here is Atul's solution to the circle problem.

function circle(circumference) {
  // When we walk in a circle, we move forward a tiny bit and turn right
  // a tiny bit. By the end, we will have traveled circumference distance
  // and rotated 360 degrees.
  for (var i = 0; i < 360; i++) {
    forward(circumference / 360);
    right(1);
  }
}

circle(300);
stamp();
```
@TinyTurtle(400,300)

</details>


  > __Hint:__ It may help conceptually to think of the circumference as the total
> distance the Turtle must travel before it returns to its original state. Also,
> play Turtle!

## Going Further

Playing with Turtle Graphics in this tutorial is nice, but you might be
wondering how to put your design into a real webpage. See the TinyTurtle
documentation for instructions on how to do this.

You might also want to take a look at the TinyTurtle source code,
tiny-turtle.js, to see how it works. It's pretty short, and reading other
people's code—especially code you use yourself—is one of the best ways to learn.
If you find bugs, you can even file an issue and fix it.

Finally, consider reading Mindstorms by Seymour Papert, which explains the
pedagogy behind Turtle graphics, among many other revolutionary ideas about
education.

## Glossary

Here's some terminology used in the tutorial that you might be unfamiliar with.

__API__

> APIs are the filament that connects what i want to _do_ with what i want to
> _learn_.
>
> _Diana Kimball,_
> _[Coding as a Liberal Art](http://www.cbc.ca/player/Radio/ID/2332634295/)_

Technically, API stands for _Application Programming Interface_. Practically
speaking, it's really just a collection of (hopefully) well-documented functions
and similar abstractions that allow you to do what you want to do with a
programming language.

If a programming language is a _language_, then an API is a bit like a
specialized _dictionary_, providing useful nouns and verbs that programs can use
to do their job.

See the TinyTurtle API for an example.

__Function__

A function is like a verb, or action, in a programming language. It's easy to
create your own; see the Making new functions section of JavaScript for Cats to
learn how.

In some programming languages, functions are referred to as procedures or
subroutines. They're all basically the same thing.

__JavaScript__

> JavaScript is an astonishing language, in the very worst sense.
>
> _[Douglas Crockford](http://javascript.crockford.com/popular.html)_

JavaScript is a programming language created by Brendan Eich in 1995 under the
time constraints of the First Browser War and some marketing constraints imposed
by Netscape's partnership with Sun Microsystems. These contributed to it being a
very misunderstood programming language.

Because of this, JavaScript is not a very easy language to learn, and it's a lot
less readable than languages that lacked its constraints. However, it's also
ubiquitous: it runs in web pages, which makes it extremely easy to share, and it
can also be used to program robots, financial trading platforms, web servers,
and a lot more. In other words, if there's something you want to do, there's
probably an API for it in JavaScript, which makes it an extremely useful
language despite its flaws.
