React Optimization - Scenario-Based Interview Questions
1. A dashboard has 20 widgets and every state change causes all widgets to re-render. How would you optimize it?
I would first identify which widgets actually depend on the changed state. I would keep state as close as possible to the components that use it instead of keeping everything in one parent. For expensive or independent widgets, I could use React.memo and optimize the props passed to them.
________________________________________
2. A parent component has multiple state variables, but changing one state causes unrelated child components to re-render. What would you do?
I would check the component structure and move state closer to the component that actually needs it. I could also use React.memo for children whose props do not change. The goal is to reduce the number of components affected by an unrelated state update.
________________________________________
3. A product table contains 5,000 rows and scrolling is very slow. How would you optimize it?
I would avoid rendering all rows at once. I would use virtualization, where only the rows currently visible in the viewport are rendered. As the user scrolls, the required rows are rendered dynamically.
________________________________________
4. A page has expensive calculations that run on every render. How would you optimize them?
I would identify whether the calculation is actually expensive and whether its inputs have changed. If the result only depends on specific values, I could use useMemo to cache the result and recalculate it only when those dependencies change.
________________________________________
5. A component receives a large object as a prop and re-renders frequently. What would you check?
I would check whether the parent creates a new object on every render. If the object is recreated unnecessarily, I could use useMemo or pass only the specific properties the child actually needs. This can help maintain stable references and reduce unnecessary renders.
________________________________________
6. A page makes the same API call every time the user navigates back to it. How would you optimize it?
I would consider caching the API response if the data does not need to be fetched every time. Depending on the application, the data could be maintained in Redux, Context, or a dedicated data-fetching/cache solution. I would also define when the cached data should be considered stale.
________________________________________
7. An API returns 5 MB of JSON data, but the UI only needs five fields. What would you do?
I would avoid transferring unnecessary data. Ideally, I would request only the required fields from the backend or create an API response specifically for the UI requirement. Reducing the response size improves network performance, parsing time, and rendering performance.
________________________________________
8. A page makes five independent API calls sequentially and takes a long time to load. How would you optimize it?
If the APIs are independent, I would execute them concurrently rather than waiting for one request to finish before starting the next. For example, I could use Promise.all() when appropriate. This can reduce the overall waiting time.
________________________________________
9. A large JavaScript library is used only for one small feature. How would you improve the bundle size?
I would check whether the library supports importing only the required functionality. If possible, I would use a smaller alternative or replace the library with simple native functionality. I would also analyze the production bundle to confirm the actual impact.
________________________________________
10. A page contains a chart component that is very expensive to render. The chart is not visible initially. What would you do?
I would lazy-load the chart component so that its code and rendering work are delayed until the component is actually required. This reduces the initial JavaScript workload and improves initial page loading.
________________________________________
11. Images below the fold are slowing down the initial page load. How would you optimize them?
I would lazy-load images that are not immediately visible. I would also use appropriately sized and compressed images and avoid loading a large image when a smaller version is sufficient. This reduces the initial network and rendering workload.
________________________________________
12. A search page becomes slow because filtering happens on every keystroke. What would you do?
For a client-side search, I could debounce the user's input before performing an expensive filtering operation. If the dataset is large, I would move the filtering to the backend and request only the required results.
________________________________________
13. A React application has a slow initial load but performs well after loading. What would you investigate?
I would investigate bundle size, large dependencies, unnecessary JavaScript loaded initially, and components that do not need to be loaded immediately. I could use code splitting, route-level lazy loading, and remove unused dependencies to reduce the initial bundle.
________________________________________
14. A component performs expensive work even when its input data has not changed. How would you optimize it?
I would first identify why the component is rendering. If its props are unchanged, React.memo may prevent unnecessary rendering. If expensive calculations are happening inside the component, useMemo could be considered for calculations whose dependencies have not changed.
________________________________________
15. A list contains complex child components and scrolling becomes slow. What would you check?
I would check how many components are being rendered and whether each list item performs expensive calculations or causes unnecessary renders. I would consider virtualization, React.memo for suitable list items, optimized images, and simpler rendering logic.
________________________________________
16. A user changes a filter five times quickly and five API calls are sent. How would you optimize this?
I would debounce the filter input so that the API is called only after the user stops changing the filter for a short period. I would also cancel outdated requests when a new filter request starts to prevent stale results.
________________________________________
17. A component receives a callback from its parent and keeps re-rendering even though the callback logic has not changed. What would you do?
I would check whether the parent creates a new function during every render. If this callback is causing unnecessary rendering, I could use useCallback in the parent and React.memo in the child when appropriate.
________________________________________
18. A large form becomes slow when typing into one field. How would you investigate it?
I would check whether updating one field causes the entire form or many child components to re-render. I could split the form into smaller components, keep state closer to the relevant fields, and prevent unrelated components from re-rendering unnecessarily.
________________________________________
19. A dashboard automatically refreshes every 10 seconds, but many users are not looking at the page. How could you optimize it?
I would consider whether polling is necessary when the page is not visible. I could pause polling when the browser tab is hidden and resume it when the user returns. I would also clean up the polling timer when the component unmounts.
________________________________________
20. You optimized a React application using useMemo, useCallback, and React.memo, but the application is still slow. What would you do?
I would not continue adding memoization blindly. I would profile the application first using React DevTools and browser performance tools to identify the actual bottleneck. The problem could be a slow API, large data processing, excessive DOM rendering, large bundle size, or backend performance rather than React re-rendering.

