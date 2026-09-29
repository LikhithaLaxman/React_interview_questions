React Interview Questions & Answers
1. What is React?
Answer:
React is a JavaScript library used for building interactive and user-friendly web applications, especially the UI layer.
It follows a component-based architecture, where we divide the application into small, reusable components. React also follows one-way data flow, uses JSX, and uses a virtual DOM to efficiently update the UI.
React is commonly used to build Single Page Applications, but React itself is a library and is not limited to SPAs.
________________________________________
2. Why do we use React?
Answer:
We use React to build interactive and user-friendly web applications.
The main advantages are component reusability, efficient UI updates, one-way data flow, and good support for managing complex application state.
________________________________________
3. What is a component?
Answer:
A component is a reusable and independent piece of UI.
We can create a component once and reuse it in multiple places in the application. For example, a Button, Header, Modal, or ProductCard can be created as reusable components.
Components help us divide a large application into smaller and manageable pieces.
________________________________________
4. Functional component vs class component
Answer:
A functional component is a JavaScript function that returns JSX. We can use React Hooks such as useState and useEffect to manage state and side effects.
A class component is a JavaScript class that extends React.Component and uses lifecycle methods such as componentDidMount, componentDidUpdate, and componentWillUnmount.
Functional components are preferred in modern React because they are simpler, have less boilerplate, and provide Hooks for handling state and lifecycle-related functionality.
________________________________________
5. What are props?
Answer:
Props are used to pass data from a parent component to a child component.
Props are read-only, which means the child component should not directly modify the props it receives.
For example, a parent can pass a product name, price, or user information to a child component through props.
________________________________________
6. What is state?
Answer:
State is data that is managed by a component and can change over time based on user interactions or application behavior.
When the state changes, React can re-render the component and update the UI.
In functional components, we commonly manage state using the useState Hook.
________________________________________
7. What is JSX?
Answer:
JSX stands for JavaScript XML. It allows us to write HTML-like syntax inside JavaScript code.
It makes the UI structure easier to read and allows us to use JavaScript expressions directly inside the JSX.
For example, we can use variables, conditions, and array methods while creating the UI.
________________________________________
8. Why do we use keys in lists?
Answer:
Keys are unique identifiers that React uses when rendering a list of elements.
They help React identify which items have been added, removed, or updated, so it can update the DOM efficiently.
For example, when rendering a list of products, we normally use a unique product ID as the key.
________________________________________
9. What is event handling in React?
Answer:
Event handling in React means responding to user interactions such as clicking a button, typing in an input field, submitting a form, or moving the mouse.
We handle events using event handlers such as onClick, onChange, and onSubmit.
For example, when a user clicks a button, we can execute a function using the onClick handler.
________________________________________
10. What is useState?
Answer:
useState is a React Hook used to add and manage state in functional components.
It returns two things: the current state value and a setter function used to update that state.
For example:
const [count, setCount] = useState(0);
Here, count is the current state, setCount is the function used to update it, and 0 is the initial value.
________________________________________
11. What is useEffect and why do we use it?
Answer:
useEffect is a React Hook used to perform side effects in functional components.
Side effects can include API calls, subscriptions, timers, event listeners, or interacting with external systems.
For example, we can use useEffect to fetch product data when a component loads.
If we provide an empty dependency array, the effect runs after the initial render. If we provide dependencies, the effect runs again when those dependencies change.
We can also return a cleanup function from useEffect to clean up subscriptions, timers, or other resources.
________________________________________
12. What is controlled vs uncontrolled component?
Answer:
A controlled component is a form element whose value is controlled by React state.
For example, we can use useState and onChange to manage the value of an input field.
An uncontrolled component stores its current value in the DOM instead of React state. We can use useRef to access the value when required.
Controlled components are commonly preferred when we need validation, dynamic updates, or complete control over the form data.
________________________________________
13. What is React Router?
Answer:
React Router is a routing library commonly used with React applications to handle navigation between different views or routes.
It allows users to navigate between URLs without doing a full browser page refresh.
We commonly use components such as BrowserRouter, Routes, and Route to define the application's routes.
________________________________________
14. What is lifting state up?
Answer:
Lifting state up means moving state to the closest common parent component when multiple child components need to share or access the same data.
The parent manages the state and passes the required data to the child components through props. If a child needs to update the state, the parent can pass a callback function to the child.
This helps us maintain a single source of truth.
________________________________________
15. What is component reusability?
Answer:
Component reusability means creating a component that can be used in multiple places instead of creating the same UI logic repeatedly.
For example, we can create a reusable Button component and use it for Save, Delete, Submit, and Cancel actions with different props.
This reduces code duplication and makes the application easier to maintain.
________________________________________
16. How do you call an API from React?
Answer:
We can call APIs from React using the browser's fetch API or libraries such as Axios.
For example, when a component loads, we can use useEffect to make a GET request, receive the response, and store the data in state.
We should also handle loading, success, and error states while making the API call.
________________________________________
17. How do you display API data in a component?
Answer:
First, I call the API using fetch or Axios, usually inside useEffect when the data needs to be loaded when the component mounts.
Then I store the response data in state using useState.
Once the state is updated, React re-renders the component and I use methods such as map() to display the data in the UI.
I also handle loading and error states.
________________________________________
18. Explain the lifecycle of a functional component.
Answer:
In functional components, we handle lifecycle-related behavior mainly using the useEffect Hook.
There are three common phases:
Mounting: When the component is initially added to the UI.
Updating: When the component re-renders because its state or props change.
Unmounting: When the component is removed from the UI.
For example, an effect with an empty dependency array runs after the initial render, and the cleanup function runs when the component unmounts.
________________________________________
19. How do you clean up an API call/subscription?
Answer:
We can return a cleanup function from useEffect.
For API requests, we can use AbortController to cancel an ongoing request when the component unmounts or when a new request makes the previous one unnecessary.
For subscriptions, event listeners, or timers, we can also remove or unsubscribe them inside the cleanup function.
This helps prevent memory leaks and unwanted updates.
________________________________________
20. useMemo vs useCallback
Answer:
useMemo memoizes a calculated value, whereas useCallback memoizes a function.
We use useMemo when we have an expensive calculation and don't want to recalculate it unnecessarily.
We use useCallback when we want to maintain the same function reference between renders, especially when passing callbacks to memoized child components.
For example, if we filter a large employee list based on a search value, useMemo can cache the filtered result.
If we pass a search handler to a child component, useCallback can keep the same function reference when its dependencies haven't changed.
________________________________________
21. What is React.memo?
Answer:
React.memo is a higher-order component used to memoize a functional component.
It prevents the component from re-rendering when its parent re-renders if its props have not changed.
It can be useful for optimizing components that render frequently and receive the same props.
However, we should use it when it provides a real performance benefit rather than applying it everywhere.
________________________________________
22. What causes a component to re-render?
Answer:
A component can re-render when its state changes, when its parent re-renders, or when the props passed to it change.
Context updates can also cause components consuming that context to re-render.
A re-render does not necessarily mean the actual DOM will be completely updated. React determines what needs to change during reconciliation.
________________________________________
23. How do you prevent unnecessary re-renders?
Answer:
First, I identify why the component is re-rendering.
Depending on the situation, I can use React.memo for components, useMemo for expensive calculations, and useCallback when stable function references are needed.
I also avoid unnecessary state updates and make sure state is maintained at the appropriate component level.
I would use these optimizations only where they actually improve performance.
________________________________________
24. What is Context API?
Answer:
Context API is a React feature used to share data between components without passing props through every intermediate component.
For example, if a user object needs to be accessed by deeply nested components, instead of passing it from parent to child to child through multiple levels, we can provide it through Context.
This helps avoid prop drilling for data that needs to be accessed by multiple components.
________________________________________
25. What is Redux?
Answer:
Redux is a state management library used to manage application state in a predictable and centralized way.
The main concepts are the store, actions, and reducers.
The store holds the application state.
An action is a plain object that describes what happened.
A reducer is a function that determines how the state should change based on the current state and the dispatched action.
________________________________________
26. Explain Redux flow.
Answer:
The Redux flow is unidirectional.
For example, when a user clicks a button, the component dispatches an action.
The action is processed by the reducer, which calculates the new state based on the current state and the action.
The Redux store is updated with the new state, and components that subscribe to the relevant state are re-rendered with the updated data.
So the basic flow is:
Component → Dispatch Action → Reducer → Store Update → Component Re-render
________________________________________
27. What is Redux middleware?
Answer:
Redux middleware is a mechanism that allows us to intercept dispatched actions before they reach the reducer.
It is commonly used for asynchronous operations, logging, API calls, and other side effects.
For example, Redux Thunk allows us to dispatch functions that can perform asynchronous API calls and dispatch other actions based on the result.
________________________________________
28. What is Redux Thunk?
Answer:
Redux Thunk is middleware that allows us to write functions, or thunks, that can be dispatched instead of only plain action objects.
It is commonly used for asynchronous operations such as API calls.
For example, a thunk can call an API, wait for the response, and then dispatch a success or failure action to update the Redux state.
________________________________________
29. How do you handle loading and error states?
Answer:
For API calls, I usually maintain separate loading, data, and error states.
When the API call starts, I set loading to true.
If the API succeeds, I store the response data and set loading to false.
If the API fails, I catch the error, store an appropriate error message, and set loading to false.
Based on these states, I display a loader, the data, or an error message in the UI.
________________________________________
30. How do you implement pagination?
Answer:
I usually implement pagination using parameters such as page and limit.
For example, if the user is on page 1 and wants 10 records, I send something like page=1&limit=10 to the backend.
The backend returns only the required set of records along with pagination information such as total records or total pages.
When the user moves to another page, I update the page number and make another API request.
________________________________________
31. How do you implement search and filtering?
Answer:
For search and filtering, I maintain the search value and filter values in state.
For a small dataset, I can filter the data on the client side using methods such as filter().
For a large dataset, I prefer sending search and filter parameters to the backend so that the backend returns only the required records.
If the search triggers API calls, I can also use debouncing to avoid making an API request for every keystroke.
________________________________________
32. How do you handle forms in React?
Answer:
I can handle forms using controlled components, where the input values are maintained in React state.
I handle changes using onChange, perform validation before submission, and handle the form submission using onSubmit.
For larger forms, we can also use form libraries depending on the application's requirements.
________________________________________
33. How do you protect routes?
Answer:
I use protected routes to prevent unauthenticated users from accessing restricted pages.
I first check whether the user is authenticated. If the user is authenticated, I allow access to the requested route.
If not, I redirect the user to the login page.
For role-based access, I also check the user's role or permissions before allowing access to specific routes.
________________________________________
34. How do you store authentication information?
Answer:
For authentication, a common secure approach is to use an HTTP-only, Secure cookie for sensitive tokens such as refresh tokens.
Because an HTTP-only cookie cannot be accessed directly by JavaScript, it provides protection against JavaScript-based token theft such as certain XSS scenarios.
For the application UI, we can keep non-sensitive authentication or user information in React state or Redux as required.
The exact approach depends on the application's authentication architecture and security requirements.
________________________________________
35. How do you handle token expiration?
Answer:
Usually, the access token has a short expiration time and a refresh token has a longer expiration time.
When the access token expires, the application can use the refresh token to request a new access token from the backend.
If the refresh token is also expired or invalid, we clear the authentication state and redirect the user to the login page.
________________________________________
36. How do you upload images/files from React?
Answer:
For file uploads, I use an input with type="file" and capture the selected file from the change event.
Then I create a FormData object and append the file to it.
I send the FormData to the backend using fetch or Axios, and handle the upload status, success response, and errors in the UI.
For example, in a product management application, the user can select a product image and upload it to the backend.
________________________________________
37. Explain React reconciliation.
Answer:
Reconciliation is the process React uses to determine what needs to change in the UI when the component output changes.
React compares the previous rendered element tree with the new one and determines the minimum necessary DOM updates.
Keys are especially important when rendering lists because they help React identify individual items across renders.
________________________________________
38. What is the Virtual DOM?
Answer:
The Virtual DOM is an in-memory representation of the UI.
When state or props change, React creates a new representation, compares it with the previous one during reconciliation, and determines what actual DOM changes are required.
This allows React to update the necessary parts of the UI instead of manually updating the entire DOM ourselves.
________________________________________
39. How does React decide which components to re-render?
Answer:
React re-renders a component when its state changes, when its parent re-renders, or when relevant props or context values change.
React then performs reconciliation to determine what actually needs to change in the DOM.
We can use techniques such as React.memo, useMemo, and useCallback when appropriate to reduce unnecessary rendering work.
________________________________________
40. Explain React rendering and commit phases.
Answer:
React's update process can broadly be divided into the render phase and commit phase.
During the render phase, React calls the necessary components and calculates what the new UI should look like.
During the commit phase, React applies the required changes to the actual DOM and runs the relevant commit-related effects.
So, in simple terms:
Render phase → Calculate changes
Commit phase → Apply changes to the DOM
________________________________________
41. How would you optimize a page containing 10,000 products?
Answer:
For a page containing 10,000 products, I would avoid rendering all records at once.
Depending on the requirement, I can use server-side pagination or infinite scrolling.
For a large visible list, virtualization can render only the items currently visible in the viewport.
I can also use lazy loading for images, memoization where appropriate, and optimize API calls.
For example, instead of rendering 10,000 products, I might load 20 or 50 records at a time and render only the required items.
________________________________________
42. How would you optimize a slow API-driven product page?
Answer:
First, I would identify whether the bottleneck is in the frontend, API, database, or network.
I would check the browser Network tab to analyze API response time and payload size.
On the frontend, I can reduce unnecessary API calls, implement pagination, lazy-load images, cache data where appropriate, and avoid unnecessary re-renders.
If the API itself is slow, I would work with the backend team to check database queries, indexes, response size, and backend processing.
________________________________________
43. How would you prevent unnecessary API calls?
Answer:
I would first identify what is triggering the API call.
For example, with useEffect, I make sure the dependency array contains only the values that should actually trigger the request.
For search functionality, I can use debouncing so that the API is not called for every keystroke.
I can also disable a submit button while a request is in progress to prevent duplicate submissions and use caching where appropriate.
________________________________________
44. How would you handle race conditions between API requests?
Answer:
A race condition can happen when multiple API requests are made and an older request returns after a newer request.
For example, when searching, the user may type "React" and then quickly type "React developer." If the first request finishes later, it could overwrite the newer result.
I can handle this using AbortController to cancel previous requests when a new request starts, or use a request ID/version check to make sure only the latest response updates the state.
________________________________________
45. How would you implement infinite scrolling?
Answer:
For infinite scrolling, I maintain the current page and the loaded data in state.
When the user reaches near the bottom of the page, I trigger another API request for the next page.
I append the newly received records to the existing list and continue until there is no more data.
I can detect the bottom using an Intersection Observer, which is generally more efficient than continuously listening to scroll events.
________________________________________
46. How would you design reusable components for a large application?
Answer:
I would design reusable components based on common UI and business requirements.
For example, instead of creating separate buttons for every screen, I can create a reusable Button component that accepts props such as label, type, disabled state, and click handler.
I would keep components focused on a single responsibility and avoid putting too much business logic inside common UI components.
For a large application, I would also organize components into common components, feature-specific components, hooks, utilities, and services.
________________________________________
47. How would you manage global authentication state?
Answer:
For global authentication state, I can use Redux or Context API depending on the complexity of the application.
For a larger application with multiple authentication-related states such as user information, roles, permissions, and authentication status, Redux can provide centralized state management.
I would keep sensitive tokens in a secure authentication mechanism such as HTTP-only cookies rather than exposing them unnecessarily to JavaScript.
________________________________________
48. How would you implement role-based UI access?
Answer:
I would get the user's role or permissions after authentication and store the required user information in the application's authentication state.
Then, based on the user's role, I conditionally render UI elements.
For example, an Admin may see Edit and Delete buttons, while a normal User may only see the View option.
However, frontend role checks are only for UI control. The backend must also validate permissions because users can potentially bypass frontend restrictions.
________________________________________
49. How would you handle refresh-token expiration?
Answer:
If the refresh token is expired or invalid, the backend will reject the refresh request.
At that point, the frontend should clear the authentication state and redirect the user to the login page.
The user will need to authenticate again to obtain a new access and refresh token.
________________________________________
50. How would you design React error handling for production?
Answer:
For production, I would handle errors at different levels.
For API calls, I would handle errors using appropriate error handling and display user-friendly messages instead of exposing technical details.
For unexpected rendering errors, I can use React Error Boundaries to prevent the entire application from crashing.
I would also add proper logging or monitoring so that production issues can be tracked and diagnosed.
I would avoid exposing sensitive information in error messages shown to users.
________________________________________
51. How would you debug a React application that suddenly became slow?
Answer:
First, I would identify where the bottleneck is instead of immediately adding optimization techniques.
I would check the browser Performance tools and React DevTools to identify unnecessary renders or expensive component operations.
I would also check the Network tab to see whether APIs are slow or returning large payloads.
Then I would optimize based on the actual issue, such as reducing unnecessary API calls, optimizing expensive calculations, using memoization where appropriate, lazy loading, pagination, or virtualization.
________________________________________
What are Error Boundaries in React?
Answer:
Error Boundaries are React components used to catch JavaScript errors that occur during rendering, lifecycle methods, or constructors of their child components.
They prevent the entire application from crashing and allow us to display a fallback UI instead.
For example, in an e-commerce application, if the Product Details component has a rendering error, an Error Boundary can display "Something went wrong" instead of breaking the complete application.
Interview answer:
"Error Boundaries are used to catch rendering-related errors in a component tree and display a fallback UI instead of allowing the entire application to crash. They are useful in production applications for handling unexpected UI errors and logging them for debugging."
________________________________________
52. What is useRef in React?
Answer:
useRef is a React Hook used to store a value that persists between renders without causing a re-render when the value changes.
It is also commonly used to directly access DOM elements.
For example, we can use useRef to focus an input:
const inputRef = useRef(null);

const handleFocus = () => {
  inputRef.current.focus();
};

return (
  <>
    <input ref={inputRef} />
    <button onClick={handleFocus}>Focus</button>
  </>
);
Here, inputRef.current gives us access to the input element.
Interview answer:
"useRef is a React Hook used to persist a mutable value across renders without causing a re-render when the value changes. It is also commonly used to access DOM elements, for example, to focus an input field or store a timer ID."
________________________________________
53. useEffect vs useLayoutEffect
Answer:
Both useEffect and useLayoutEffect are used to perform side effects, but the main difference is when they execute.
useEffect runs after the browser has generally painted the updated UI. It is commonly used for API calls, subscriptions, timers, and event listeners.
useLayoutEffect runs after React updates the DOM but before the browser paints the updated UI. It is mainly used when we need to measure or modify the DOM before the user sees it.
For example, if we need to calculate the position or size of an element before displaying it, useLayoutEffect can be useful.

