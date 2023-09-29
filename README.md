## React

- [JSX](#JSX)

### What is React

`React` – extremely popular declarative, component-based, state-driven JavaScript library for building user interfaces, created by Facebook.

- Based on components. Components are the building blocks of user interfaces in React. We build complex UIs by building and combining multiple components.
- Declarative. We describe how components look like and how they work using a declarative syntax called JSX. `JSX` a syntax that combines HTML, CSS, JavaScript, as well as referencing other components.
- State-driven. React reacts to state changes by re-rendering the UI.

There are several options and freamworks to work with React (Vite, Next.js, Remix, etc.)
![](1.png)

### Components

React applications are entirely made out of components. We build complex UIs by building multiple components and combining them. Components can be reused, nested inside each other, and pass data between them.
![](2.png)

### JSX

Components must return a block of JSX. `Extension of JavaScript` that allows us to
embed JavaScript, CSS, and React components into HTML. Each JSX element is converted to a `React.createElement` function call.
![](3.png)
![](4.png)
![](5.png)

### Props

`Props` like a chain or communication chanel between a parent and a child components. Props are used to pass data from parent components to child components (down the component tree). With props, parent components control how child components look and work. This one-way date flow makes applications more predictable and easier to understand, easier to debug. Anything can be passed as props: single value, arrays, objects, functions, even other components.
So, props is data coming from the outside, and can only be updated by the parent component. Props are read-only, they are immutable! This is one of React’s strict rules. If you need to mutate props, you actually need state.

#### 🚩 Rendering List

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

#### 🚩 Conditional Rendering With &&

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

#### 🚩 Conditional Rendering With Ternaries

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

#### 🚩 Conditional Rendering With Multiple Returns

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
