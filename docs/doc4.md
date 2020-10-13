---
id: useState Hook
title: useState Hook
---

## City Selector Component

We will make a new component that the user can select a city and we will display the weather data for that city.

In our component, we will create `input` and a `button`. When the user clicks the button, we will fetch the weather forecast for that city.

We will use Bootstrap Layout to create rows and columns. You can find the documentation at [this link.](https://react-bootstrap.github.io/layout/grid/)

Now, let's go to the components folder and create another folder named `CitySelector.js` and create our boilerplate code.

## useState Hooks

State helps build highly performant web apps. To keep track of our application logic, we need to use state. We can reflect any UI or the user interface changes via changes in state.

To be able to change our button's state, we need a special hook named `useState`. With `useState`, we can add state to functional components.

`useState` returns an array of two items first element is the _current value of the state_, and the second is a _state setter function_. State tracks the value of our state. Whenever the state updates, it should also rerender JSX elements. The setter function is gonna be used to update our state value.

In class components, the state is always an object, with the useState hook, the state does not have to be an object.

When dealing with objects or arrays, always make sure to spread your state variable and then call the setter function.

Every time, with every rerender we don't mutate our state, we get a completely new state, we can change our state, with the setter function.

We need to contain one state property and that will be the _city_. In order to use, _useState_ in our component, we have to import _useState_ first. _useState_ is a named export; so, we will export it with curly braces.

`import React, { useState } from 'react';`

Our goal is to update the state when a user clicks on a button.

We need to define a new variable and set it to useState hook. Inside the hook as an argument, we need to pass the `initial` value as an _empty string_.

```javascript
import React, {useState} from 'react';

const CitySelector = () => {
  const [city, setCity] = useState('');
  return <div></div>;
};

export default CitySelector;
```

We will add _Row, Col, FormControl and Button_ components from Bootstrap to create our JSX elements. FormControl is for our `input` element and we need to take its value by passing `event.target.value`
We will pass for the `Button` component one function for now, we will use it soon to display our data.

```javascript
// CitySelector.js

import React, {useState} from 'react';
import {Row, Col, FormControl, Button} from 'react-bootstrap';

const CitySelector = () => {
  const [city, setCity] = useState('');

  return (
    <>
      <Row>
        <Col>
          <h1>Search your city</h1>
        </Col>
      </Row>

      <Row>
        {/* xs={4} takes the one third  of the page*/}
        <Col xs={4} className="text-center">
          <FormControl
            placeholder="Enter city"
            // update city value with the user's input
            onChange={(event) => setCity(event.target.value)}
            // value will be the currently selected city
            value={city}
          />
        </Col>
      </Row>

      <Row>
        <Col>
          {/* event handler for button click */}
          <Button onClick={onSearch}>Check Weather</Button>
        </Col>
      </Row>
    </>
  );
};

export default CitySelector;
```

Now, let's import our CitySelector component into App.js. Also, we can remove our hardcoded WeatherCard component, we can now get the city data from user input.

Our App component is now looking like this. Also, I added a _Container_ from bootstrap.

```javascript
import React from 'react';
import CitySelector from './components/CitySelector';
import './App.css';
import {Container} from 'react-bootstrap';

const App = () => {
  return (
    <Container className="App">
      <CitySelector />
    </Container>
  );
};

export default App;
```

Also, copy and paste this CSS code into your `App.css` file.

```css
.App {
  text-align: center;
}

.row {
  justify-content: center;
  margin: 15px 0;
}
```
