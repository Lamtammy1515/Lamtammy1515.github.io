---
layout: post
title:      "React Lifecycle Methods"
date:       2021-08-11 16:09:41 -0400
permalink:  react_lifecycle_methods
---


Let's start from the beginning!  A component's lifecycle basically begins when an object/instance of a class gets created. It ends when that component gets removed from the DOM. React provides us with a couple of different lifecycle methods but today, I will only be going over the methods that are commonly used. The five methods I'll be going over in this blog are listed below. 

* constructor 
* render
* componentDidMount
* componentDidUpdate
* componentWillUnmount
 
Before I get into to details about these methods, I'm going to talk a little bit about the different phases in a lifecycle. 

1. initialization Phase: 

The initialization phase is when we have to define the states/props before the component gets mounted into the DOM which is generally done inside the constructor method.
* constructor

2. Mounting Phase: 

This phase occurs when the component is rendered into the DOM.
* render
* componentDidMount

3. Updating Phase: 

This is the phase that happens when a state or prop changes.
* render
* componentDidUpdate

4. Unmounting Phase: 

The unmounting phase is when a component gets detroyed and removed from the DOM. 
* componentWillUnmount



# The 5 Common Lifecycle Methods
**1. Constructor**

The constructor is **always** the first lifecycle method that gets invokes. The reason for that is because the constructor gets triggered whenever we create a new instance of a class. The only things we do in the constructor is to set up the initial state and as well, we can bind the key "this" to our function so that the component has access to the state by using "this.state". 

**1. Render**

The render method is the only method required inside of a class component. Also, the render method should always be pure meaning that we should never modify the state from within the method. Lastly, this method will run anytime the state or prop changes. 

**3. componentDidMount**

The componentDidMount method is a place where you can make api calls to fetch data. You can also update your state here by using the setState() method which would then trigger the render method. ComponentDidMount normally gets invoked immediately after the initial render happens. 

**4. componentDidUpdate**

The componentDidUpdate method gets invoked whenever an update occurs or whenever a render method method gets invoked, EXCEPT for when it is the initial render. ComponentDidUpdate can also accept three arguments if necessary, which are the *previous props*, *previous state* and *snapshot*([getSnapshotBeforeUpdate](https://reactjs.org/docs/react-component.html#getsnapshotbeforeupdate)). SetState can also be used within this method but it has to be wrapped in a condition to avoid infinite loops. 

**5. componentWillUnmount**
This method is used to destroy and remove a component from the DOM.


Hopefully, this was somewhat helpful to get you started in learning about lifecycles. Aside from these methods I've talked about above, there a much more lifecycle methods that React offers so I recommend exploring other different lifecycle methods! I've also linked two of articles below that might help as well. 


**Resources:**
[React Lifecycle](https://reactjs.org/docs/react-component.html)
[State & LifeCycle](https://reactjs.org/docs/state-and-lifecycle.html)



