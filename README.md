## React

- [What is React](#1)
- [Components](#2)
- [JSX](#3)
- [Props](#4)
  - [Rendering List](#5)
  - [Conditional Rendering With &&](#6)
  - [Conditional Rendering With Ternaries](#7)
  - [Conditional Rendering With Multiple Returns](#8)
- [State](#9)

### What is React <a name="1"></a>

`React` – extremely popular declarative, component-based, state-driven JavaScript library for building user interfaces, created by Facebook.

- Based on components. Components are the building blocks of user interfaces in React. We build complex UIs by building and combining multiple components.
- Declarative. We describe how components look like and how they work using a declarative syntax called JSX. `JSX` a syntax that combines HTML, CSS, JavaScript, as well as referencing other components.
- State-driven. React reacts to state changes by re-rendering the UI.

There are several options and freamworks to work with React (Vite, Next.js, Remix, etc.)
![](1.png)

### Components <a name="2"></a>

React applications are entirely made out of components. We build complex UIs by building multiple components and combining them. Components can be reused, nested inside each other, and pass data between them.
![](2.png)

### JSX <a name="3"></a>

Components must return a block of JSX. `Extension of JavaScript` that allows us to
embed JavaScript, CSS, and React components into HTML. Each JSX element is converted to a `React.createElement` function call.
![](3.png)
![](4.png)
![](5.png)

### Props <a name="4"></a>

`Props` like a chain or communication chanel between a parent and a child components. Props are used to pass data from parent components to child components (down the component tree). With props, parent components control how child components look and work. This one-way date flow makes applications more predictable and easier to understand, easier to debug. Anything can be passed as props: single value, arrays, objects, functions, even other components.
So, props is data coming from the outside, and can only be updated by the parent component. Props are read-only, they are immutable! This is one of React’s strict rules. If you need to mutate props, you actually need state.

#### 🚩 Rendering List <a name="5"></a>

For rendering usualy used `.map` which allows to loop through array and create a brand new array.

Example - [Udemy-pizza-menu](https://github.com/agpavlik/Udemy-pizza-menu)

```javascript
const pizzaData = [
  {
    name: "Focaccia",
    ingredients: "Bread with italian olive oil and rosemary",
    price: 6,
    photoName: "pizzas/focaccia.jpg",
    soldOut: false,
  },
  {
    name: "Pizza Margherita",
    ingredients: "Tomato and mozarella",
    price: 10,
    photoName: "pizzas/margherita.jpg",
    soldOut: false,
  },
  {
    name: "Pizza Spinaci",
    ingredients: "Tomato, mozarella, spinach, and ricotta cheese",
    price: 12,
    photoName: "pizzas/spinaci.jpg",
    soldOut: true,
  },
];

function Menu() {
  const pizzas = pizzaData;
  const numPizzas = pizzas.length;

  return (
    <main className="menu">
      <h2>Our menu</h2>
      <ul className="pizzas">
        {pizzaData.map((pizza) => (
          <Pizza pizzaObj={pizza} key={pizza.name} />
        ))}
      </ul>
    </main>
  );
}

function Pizza(props) {
  return (
    <li className={`pizza ${props.pizzaObj.soldOut ? "sold-out" : ""}`}>
      <img src={props.pizzaObj.photoName} alt={props.pizzaObj.name} />
      <div>
        <h3>{props.pizzaObj.name}</h3>
        <p>{props.pizzaObj.ingredients}</p>

        <span>
          {props.pizzaObj.soldOut ? "SOLD OUT" : props.pizzaObj.price}
        </span>
      </div>
    </li>
  );
}
```

#### 🚩 Conditional Rendering With && <a name="6"></a>

```javascript
function Footer() {
  const hour = new Date().getHours();
  const openHour = 12;
  const closeHour = 22;
  const isOpen = hour >= openHour && hour <= closeHour;

  return (
    <footer className="footer">
      {isOpen && (
        <div className="order">
          <p>
            We're open from {props.openHour}:00 to {props.closeHour}:00. Come
            visit us or order online
          </p>
          <button className="btn">Order</button>
        </div>
      )}
    </footer>
  );
}
```

#### 🚩 Conditional Rendering With Ternaries <a name="7"></a>

```javascript
function Footer() {
  const hour = new Date().getHours();
  const openHour = 12;
  const closeHour = 22;
  const isOpen = hour >= openHour && hour <= closeHour;

  return (
    <footer className="footer">
      {isOpen ? (
        <div className="order">
          <p>
            We're open from {props.openHour}:00 to {props.closeHour}:00. Come
            visit us or order online
          </p>
          <button className="btn">Order</button>
        </div>
      ) : (
        <p>
          We're happy welcome you between {openHour}:00 and {closeHour}:00.
        </p>
      )}
    </footer>
  );
}
```

#### 🚩 Conditional Rendering With Multiple Returns <a name="8"></a>

```javascript
function Footer() {
  const hour = new Date().getHours();
  const openHour = 12;
  const closeHour = 22;
  const isOpen = hour >= openHour && hour <= closeHour;

  if (!isOpen) {
    return (
      <footer className="footer">
        <p>CLOSED</p>
      </footer>
    );
  }

  return (
    <footer className="footer">
      {isOpen ? (
        <div className="order">
          <p>
            We're open from {props.openHour}:00 to {props.closeHour}:00. Come
            visit us or order online
          </p>
          <button className="btn">Order</button>
        </div>
      ) : (
        <p>
          We're happy welcome you between {openHour}:00 and {closeHour}:00.
        </p>
      )}
    </footer>
  );
}
```

### State <a name="9"></a>

`State` is the most important concept in React. `State` is a “component’s memory”.
`State` is internal data that can be updated by the components logic. Data that a component can hold over time, necessary for information that it needs to remember throughout the app’s lifecycle. Updating component state triggers React to re-render the component.
In React, a view is updated by re-rendering the component.

Practical guideline about state

- Use a state variable for any data that the component should keep track of over time. This is data that will change at some point.
- Whenever you want something in the component to be dynamic,create a piece of state related to that “thing”, and update the state when the “thing” should change.
- If you want to change the way a component looks, or the data it displays, update its state. This usually happens in an event handler function.
- When building a component, imagine its view as a reflection of state changing over time.
- For data that should not trigger component re-render, don’t use state. Use a regular variable instead.

#### 🚩 Handling events in React<a name="10"></a>
