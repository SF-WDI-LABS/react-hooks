# React Hooks

## What are they?

Hooks _in general_ are code that will be called at a specific point in the life of some code that you write. It's like writing an event listener that, rather than listening for user input, is waiting for something to happen in the code that is running. This is most similar to the `$(document).ready` method that we've used in jQuery; we specify that we want that callback to run, once, when the page has finished loading.

Hooks _in React_ are methods that will be called by React at particular points in a component's life.

## Why do we care?

There are things that we want to do at very specific points in the life of a component. For example, when a component is first created, we may want to fetch data that we need to display the component. When the component is about to be displayed, we may want to check that it should be displayed, or get updates about the information that is displayed in the component. Hooks let us write code that React will execute at exactly the moment that we want.

### see how badly things break if we don't use them!

Suppose that, instead of fetching our data using a hook, we fetch the data when a component is rendered. What can go wrong?

A lot. Components get rendered ALL THE TIME, and if we fetch that data every time it is rendered, we will be making a LOT of network requests... more than one per second. This is a great recipe for hitting your API request limits or having to pay Heroku for all of the traffic you're causing.

As an example, put `console.log("hello!")` in the `render` function for a simple component, then open your console and despair. It logs `hello!` incredibly often. Fetching data here would be just as painful, so we have to be mindful about how we do it.

## How do we use them?

To fetch data only once, when the component is created initially, we can use the `onComponentMount` React hook. This is a hook that will be called, once, before the component is added to the page for the first time.

There are 10 available hooks in the life of a React component. You can see a complete list [in the React documentation](https://facebook.github.io/react/docs/react-component.html#the-component-lifecycle). The most common ones that you will use, and that you'll want to understand, are:

* `componentWillMount`, which is called when a component is created for the first time and is about to be inserted into the page for the first time ever.

* `componentWillUnmount`, which is called when a component is about to be removed from the page forever.

* `render` is also a lifecycle hook! It's the hook that lets us set what should be shown on the page when a component is being displayed, and is called every time the component is being re-rendered.
