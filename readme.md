# how-to-react

Overview of new concepts when working with
Facebook's React w/ some helpful resources.

## Why this doc?

React is a loaded term. It can mean many different things to many people.
I've found any conversations I have when onboarding folks become conflated
with other topics like Flux, data fetching, how it compares with
Angular or other popular Frontend frameworks and es6 syntax.

For better or worse React is all these things. It's a can of worms that
inadvertently introduces new concepts and ways of building webapps, but
outside rendering some JSX/HTML all of the other parts that make up a
modern webapp are up to you. And that's a good thing!!!

## What is React?

In this doc React will refer to the view layer and only the view layer.
With that comes a few new concepts:

- **Virtual DOM** – A data representation of the desired DOM Tree.
- **JSX** – A markup syntax similar to HTML, but written in your JavaScript files.
- **Universal Rendering** – Render the same JSX view in the client and on the server w/ NodeJS.

### Virtual DOM

@TODO

http://calendar.perfplanet.com/2013/diff/

### JSX

@TODO

Others have done a way better job than I can at explaining
what JSX is and I encourage you to read through some of
their write ups, but here is a simple example:

```
function buttonClicked () {
  console.log('The button has been clicked!')
}

var (
    <botton onClick={ buttonClicked }>I'm a button!</button>
)
```

Looks just like HTML! How does this work in JavaScript and
why haven't we always been using it? Well we don't
get this out of the box. It's not standard JavaScript.
In order to write the code above we need to transpile this
source down in to standard JavaScript that browsers can actually run.

This is where things get quite complicated, but there is
a light at the end of the tunnel!
