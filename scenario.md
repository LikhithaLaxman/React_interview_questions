React Scenario-Based Interview Questions
1. API is getting called multiple times. How would you debug it?
I would first check where the API call is triggered, especially the useEffect dependencies. Incorrect dependencies, state updates, or unnecessary component mounting can cause multiple calls. I would identify the exact trigger and make sure the API runs only when the required data changes.
________________________________________
2. Search API is called on every keystroke. How would you optimize it?
I would use debouncing for the search input. Instead of calling the API for every character, I would wait for the user to stop typing for a short period and then make the API call. This reduces unnecessary network requests and improves performance.
________________________________________
3. A page contains 10,000 products and becomes slow. What would you do?
I would avoid rendering all products at once. I would use pagination, infinite scrolling, or list virtualization so that only the required or visible records are rendered. I would also optimize images and avoid unnecessary re-renders.
________________________________________
4. API request is running when the user leaves the page. How would you handle it?
I would cancel the API request during the component cleanup. With fetch, I can use AbortController and call abort() inside the cleanup function of useEffect. This prevents unnecessary requests and avoids handling a response that is no longer required.
________________________________________
5. Two API requests are running and the older response overwrites the newer response. What would you do?
This is a race condition. I would cancel the previous request using AbortController or track the latest request and update the state only for the latest response. This ensures that older responses cannot overwrite newer results.
________________________________________
6. Child component re-renders whenever the parent re-renders. How would you optimize it?
First, I would check whether the child actually needs to re-render. If its props have not changed, I could use React.memo. If the parent passes functions or objects, I would check whether their references are changing unnecessarily and use useCallback or useMemo where appropriate.
________________________________________
7. Submit button is clicked multiple times and duplicate API requests are created. How would you prevent it?
I would maintain a submitting/loading state. When the API request starts, I would disable the Submit button. After the request completes or fails, I would enable it again. This prevents accidental multiple submissions.
________________________________________
8. A form has many fields and validation is becoming difficult. How would you manage it?
I would keep the form state and validation logic organized and reusable. For a complex form, I could use a form library to simplify validation, error handling, and submission. I would also avoid duplicating validation logic for every field.
________________________________________
9. Admin and User should see different buttons. How would you implement it?
I would get the user's role or permissions after authentication and conditionally render the required UI. For example, Admin can see Edit and Delete, while a normal User can only see View. However, the backend must also enforce authorization because frontend checks alone are not secure.
________________________________________
10. One component crashes and the whole UI is affected. What would you do?
I would use an Error Boundary around the appropriate component tree. If a child component has a rendering error, the Error Boundary can display a fallback UI instead of allowing the complete application section to crash. I would also log the error for debugging.
________________________________________
11. User changes filters while the previous API request is still running. How would you handle it?
I would cancel the previous request when the filter changes using AbortController. Then I would send a new request for the latest filter. This prevents the response from an older filter from replacing the latest results.
________________________________________
12. You need to focus an input after clicking a button. How would you implement it?
I would use useRef to access the input DOM element. The ref can be attached to the input, and on button click I can call inputRef.current.focus(). useRef allows me to access the element without causing a re-render.
________________________________________
13. UI flickers while calculating an element's size. How would you solve it?
If I need to measure or modify the DOM before the browser paints the updated UI, I would use useLayoutEffect. It runs after React updates the DOM but before the browser paints. For normal side effects such as API calls, I would use useEffect.
________________________________________
14. Several components need the same user information. How would you avoid prop drilling?
I would use Context API if the shared information is relatively simple, such as theme or user information. For larger applications with complex global state and updates, I could use Redux or another state management solution.
________________________________________
15. Filtering 10,000 products is causing performance issues. What would you do?
I would first identify whether filtering is actually the bottleneck. If the calculation is expensive, I could use useMemo so it is recalculated only when the relevant data changes. For very large datasets, I would consider server-side filtering instead of filtering everything on the client.
________________________________________
16. Product images are making the page load slowly. How would you optimize it?
I would use optimized image sizes and formats, lazy-load images that are outside the visible area, and avoid loading unnecessary high-resolution images. I could also use thumbnails for product lists and load larger images only when required.
________________________________________
17. API response contains thousands of records. Should you load everything at once?
No. I would generally use pagination or another incremental loading approach. The frontend can request a limited number of records using parameters such as page and limit. This reduces payload size and improves initial page performance.
________________________________________
18. User navigates to a product details page and then comes back. How can you avoid unnecessary API calls?
I would consider caching the previously loaded product data. Depending on the application architecture, this could be handled using Redux state, Context, or a dedicated data-fetching/caching solution. The goal is to reuse valid data instead of requesting the same information unnecessarily.
________________________________________
19. A component has a timer that continues after navigating away. What would you do?
I would clear the timer in the cleanup function of useEffect. For example, if I use setInterval, I would call clearInterval when the component unmounts. This prevents unnecessary background work and memory-related issues.
________________________________________
20. Event listener is added to a component but never removed. What problem can occur?
It can cause unnecessary event handling and potentially memory leaks. I would add the event listener inside useEffect and remove it in the cleanup function using removeEventListener. This ensures proper lifecycle management.
________________________________________
21. User enters a URL manually for a page they are not authorized to access. How would you handle it?
I would create a protected route that checks authentication and authorization information before rendering the page. If the user is not authenticated, I would redirect to login. If authenticated but not authorized, I would show an appropriate access-denied page.
________________________________________
22. Access token expires while the user is using the application. What would you do?
I would use a refresh-token mechanism. When the access token expires, the application can request a new access token using a valid refresh token. If the refresh token is also invalid or expired, I would clear the authentication state and redirect the user to login.
________________________________________
23. User refreshes the browser and loses login information. How would you solve it?
I would check how authentication state is being stored. Instead of keeping all authentication information only in React memory, the application can use a secure authentication mechanism such as HTTP-only cookies for sensitive tokens. On application startup, the frontend can retrieve or validate the user's session.
________________________________________
24. A component receives an object as a prop and keeps re-rendering unnecessarily. Why?
Objects are compared by reference. Even if two objects contain the same values, creating a new object creates a new reference. I would check whether the object is recreated on every render and use useMemo or restructure the state if a stable reference is actually beneficial.
________________________________________
25. A function passed to a child component changes on every render. How would you handle it?
A function created inside the parent component gets a new reference during each render. If the child is memoized and this causes unnecessary rendering, I could use useCallback to preserve the function reference until its dependencies change.
________________________________________
26. A user changes the page number in pagination. What should happen?
I would maintain the current page in state. When the page changes, I would call the API with the new page and limit values. The response would update the product list and pagination information.
________________________________________
27. Infinite scrolling keeps calling the API repeatedly. How would you fix it?
I would make sure a new request is not triggered while the previous request is still loading. I would maintain a loading flag and check whether more records are available before requesting the next page. An IntersectionObserver can also be used to trigger loading when the user reaches the bottom.
________________________________________
28. API fails while loading products. How should the UI behave?
I would maintain separate loading, data, and error states. While the request is running, I would show a loader. If it succeeds, I would display the data. If it fails, I would show a user-friendly error message and optionally provide a retry option.
________________________________________
29. User submits a form and the page refreshes unexpectedly. What could be wrong?
The browser's default form submission behavior may be causing the refresh. In React, I would handle the onSubmit event and use event.preventDefault() before performing the API request or other submission logic.
________________________________________
30. Form data disappears when switching between two components. How would you solve it?
If the data needs to remain available between components, I would move the state to their common parent or store it in a suitable global state solution. This provides a single source of truth instead of keeping important data inside only one component.
________________________________________
31. A modal is opened from multiple places in the application. How would you make it reusable?
I would create a reusable Modal component and pass required values through props, such as isOpen, title, content, and callback functions. This avoids duplicating modal implementation across multiple components.
________________________________________
32. Several buttons have almost the same UI but different actions. How would you design them?
I would create a reusable Button component and pass properties such as label, type, disabled state, and click handler through props. This keeps the UI consistent and reduces duplicate code.
________________________________________
33. Product list should update immediately after deleting a product. How would you handle it?
After a successful delete API response, I can either remove the deleted product from the existing state or request the updated product list from the backend. For a simple list, updating local state can provide a faster UI response while keeping the backend as the source of truth.
________________________________________
34. User clicks Delete but the API fails. What should happen?
I would not permanently remove the product from the UI until the operation is confirmed, unless I am intentionally using optimistic updates. If the API fails, I would show an error message and keep or restore the product in the list.
________________________________________
35. A component is receiving too many props. What would you do?
I would check whether the component has too many responsibilities. I could split it into smaller components or use Context for genuinely shared data. The goal is to keep components focused and avoid unnecessary prop drilling.
________________________________________
36. You need to share authentication status across many components. What would you use?
For a simple application, I could use Context API. For a larger application with user details, roles, permissions, and other global state, I could use Redux. Sensitive authentication tokens should be handled using an appropriate secure mechanism rather than exposing them unnecessarily to JavaScript.
________________________________________
37. A page has many independent API calls and loads slowly. How would you improve it?
I would identify whether the calls depend on each other. If they are independent, I could execute them concurrently instead of waiting for one to finish before starting another. I would also check response sizes, unnecessary calls, caching, and backend performance.
________________________________________
38. One API depends on the result of another API. How would you handle it?
I would call the first API, validate its response, and then use the required value to call the second API. I would handle loading and error states properly so that the second request is not made if the first request fails.
________________________________________
39. A user navigates quickly between pages and old data appears briefly. What would you check?
I would check whether previous API responses are updating state after navigation. I could cancel requests during cleanup or track the latest request. I would also make sure the component displays the correct loading state while new data is being fetched.
________________________________________
40. You need to display different UI based on feature configuration. How would you implement it?
I would keep feature configuration in a controlled source such as application configuration or backend-provided feature flags. The component can read the flag and conditionally render the feature. This allows features to be enabled or disabled without duplicating component logic.
________________________________________
41. A React application has a very large bundle size. What would you investigate?
I would analyze the bundle to identify large dependencies and unnecessary imports. I would use code splitting and lazy loading for routes or heavy components that do not need to load immediately. I would also remove unused dependencies and optimize imports.
________________________________________
42. A page contains a large component that is rarely used. How can you improve initial loading?
I would use lazy loading with React.lazy and Suspense. The component can be loaded only when it is actually required instead of including its code in the initial bundle.
________________________________________
43. A user sees an empty page while data is loading. How would you improve the experience?
I would provide a loading state such as a spinner, skeleton UI, or placeholder. This makes it clear that the application is processing the request rather than appearing broken or empty.
________________________________________
44. API data changes frequently. How would you keep the UI updated?
The approach depends on the requirement. For periodic updates, I could use polling with a suitable interval. For real-time requirements, I could use WebSockets or another real-time mechanism. I would also make sure subscriptions or timers are cleaned up properly.
________________________________________
45. A component should perform an action only when a specific prop changes. How would you handle it?
I would use useEffect with that prop in the dependency array. This makes the effect run when the specific value changes rather than on every render. I would keep the dependency list accurate to avoid stale values or unnecessary executions.
________________________________________
46. A state update is not showing the expected latest value. What would you check?
I would check whether I am relying on the state value immediately after calling its setter. React state updates are not something I should treat as immediately changed within the same execution. If the new state depends on the previous state, I would use the functional update form such as setCount(prev => prev + 1).
________________________________________
47. Two components need to update the same piece of data. How would you design it?
I would keep the shared state in their closest common parent. The parent can pass the current value and callback functions to both children. This follows the single-source-of-truth approach and keeps the data flow predictable.
________________________________________
48. A list item loses its input value after sorting the list. What would you check?
I would check the key used for the list items. Using an array index as a key can cause problems when items are reordered, inserted, or removed. I would use a stable unique identifier, such as the product ID.
________________________________________
49. Application works correctly but becomes slow after using Context API extensively. What would you investigate?
I would check how the Context value is structured and which components consume it. When the context value changes, its consumers may re-render. I would split contexts where appropriate, keep frequently changing state separate, and avoid putting unrelated data into one large context.
________________________________________
50. A React application suddenly becomes slow in production. How would you debug it?
I would first identify the actual bottleneck instead of immediately adding optimizations. I would check browser performance, React DevTools, network requests, API response times, bundle size, and unnecessary re-renders. Once the bottleneck is identified, I would optimize that specific area using techniques such as pagination, lazy loading, memoization, API optimization, or virtualization.

