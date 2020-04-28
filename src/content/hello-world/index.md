---
title: 'About me'
date: '2020-04-28T22:12:03.284Z'
---

Hello, World

```js
function handleChange(value) {
  this.setState({
    value: newValue,
  });
  console.log(this.state.value); //Why is my state not updated?
}
```

```js
setTimeout(() => console.log('foo'), 0);
console.log('bar');
```

---

### How do we fix this?

```js
function handleChange(value) {
  this.setState(
    {
      value: newValue,
    },
    () => {
      console.log(this.state.value);
    }
  );
}
```

`setState` actually comes with a callback version. All you have to do is provide the function to be run after the `setState` is executed. Here, you can give whatever action you wanted to perform once the setState is done.

Since you might already have the result you are going to `setState` with, it might be better to utilise that result for regular operations rather than using the callback.

PS: You could also just use `console.log(this.state.value)` in `render()` function or `componentDidUpdate()` but I’m guessing you already knew that.

### Why is it asynchronous?

Now that you know how to fix it, you can leave.

Or you can stay and figure out why is it made asynchronous. _Doesn’t it make React slower?_

From the docs:

> React may batch multiple `setState()` calls into a single update for performance.

> Because `this.props` and `this.state` may be updated asynchronously, you should not rely on their values for calculating the next state.

Yes, that is just it. React it doing this for performance. You might not feel the need for it in a small application. But in a larger application where a lot of state updates may be taking place simultaneously, batching state updates comes as a boon.

The `setState` comes with several other neat tricks as well, with `prevState` which you should definitely check out if you are new to React or may be just haven’t heard of it.
