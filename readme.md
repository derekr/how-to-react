# how-to-react

Overview of new concepts when working with
Facebook's [React](http://facebook.github.io/react/) w/ some helpful resources.

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

```js
function buttonClicked () {
  alert('The button has been clicked!')
}

var (
    <button onClick={ buttonClicked }>I'm a button!</button>
)
```

Looks just like HTML! How does this work in JavaScript and
why haven't we always been using it? Well we don't
get this out of the box. It's not standard JavaScript.
In order to write the code above we need to transpile this
source down in to standard JavaScript that browsers can actually run.

This is where things get quite complicated, but there is
a light at the end of the tunnel!

The example above is available on CodePen (a Frontend code playground):

http://codepen.io/drk/pen/pJqbVO

What's happening here is the source JavaScript is being transpiled or
compiled using a tool called [Babel](https://babeljs.io).
This tool can read special and non stanard syntax and spit out plain JavaScript.

```
button.jsx -> Babel -> button.js
```

`button.js` is what you'd want to include in your page:

```html
<script src='button.js'></script>
```

For instance here is what the example above looks like after transpiling through
Babel:

```js
'use strict';

function buttonClicked() {
  alert('The button has been clicked!');
}

var btn = React.createElement(
  'button',
  { onClick: buttonClicked },
  'I\'m a button!'
);
```

Note how it injects certain things you don't necessarily care about like
calling `React.createElement` as a simple function.

While this tool does enable us to write custom JavaScript it unfortunately
does add an extra layer of abstraction when working on a webapp making
things considerably more complex. I can tell you the learning curve is worth
it however as it unlocks JSX, es6 (the next version of JavaScript syntax)
and other neat transformations.

#### es6

I don't think it's necessary to do a deep dive in to es6 here, but a quick
context lesson will me helpful.

Do you need to know es6 to use React? Absolutely not.

Should you use es6 when writing React apps? Probably not, but it's fun.

The biggest issue with es6 rigth now is it's a pretty large concept to learn
since it requires a transpiling step, Babel, and reading code that can
look significantly different than the JavaScript you're used to. A lot of
tooling in the React ecosystem is opting to using es6 which means their
documentation is written in es6, the code is written in es6 and it's up to
you to get these tools working in your project. This can make researching
React tooling pretty difficult since you can't as easily evalute someone's
solution as you could if it were all written/documented in es5.

So if you're deciding to use React you're essentially deciding to adopt es6
as well.

That said it isn't too difficult to learn the new syntax it just takes some
time. It's something to consider if you're introducing React in to a team
environment where time is truly expensive.

This is a good overview of [Navigating the React Ecosystem](http://www.toptal.com/react/navigating-the-react-ecosystem)

### Universal Rendering

@TODO

## CommonJS and Bundling

## Flux and State Management

You may have heard of Flux. It's a very simple idea that has been around
for a while, but only recently got some branding love from Facebook. You also
may have come across one of the many ∞ implementations:

https://github.com/voronianski/flux-comparison

The problem something like Flux solves is
unidirectional data flow and state management.

You probably don't need a Flux library to do that.

It's as simple as having an object literal at the top of your
webapp:

```js
var appState = {
  user: {
    name: 'drk',
    avatar: '/path/avatar.png'
  }
}

renderApp(appState)
```

This will ultimately render some `<img>` element w/ the `avatar` path.

You'll want a way of communicating intents of changing that state from the
user. For example let's say the user wants to change their avatar path, you'll
need to handle a form submission w/ the new avatar path. In JSX that might look
like:

```js
function updateAvatar () {
  appState.user.name = React.findDOMNode(this.refs.avatar).value.trim()
  renderApp(appState)
}

<form onSubmit={ updateAvatar }>
  <input name='avatar' type='text' />
</form>
```

Admittedly a really naive example. This [article](http://hackflow.com/blog/2015/03/08/boiling-react-down-to-few-lines-in-jquery/) does a great job of walking through a unidirectional data flow
using jQuery which might help make this concept more concrete.

Depending on the size/needs of your project state management isn't a huge
concern. Once your applications become complex enough you'll want to invest
in something to make reasoning with the global state of your webapp
more reasonable.

There are many benefits to using a Flux implementation, but consider
what you're building before making a decision. There are also some
exciting new concepts on data dependency/flow from Facebook that might
augment or replace the needs for a complex Flux setup. Check out
[Relay and GraphQL](http://facebook.github.io/react/blog/2015/02/20/introducing-relay-and-graphql.html). 

## Data Fetching (Ajax)

## Clientside Routing
