# Next.js 15 Routing Conflict: Custom Server Functions and Link Component

This repository demonstrates a potential conflict between custom server-side functions and Next.js's Link component in Next.js 15.  The issue arises when custom server-side logic redirects or manipulates routes, potentially interfering with client-side routing handled by the Link component.

## Problem

The `bug.js` file shows an example using the Next.js Link component. If your application uses server-side functions that also redirect or modify routes (e.g., based on authentication or other factors), it might lead to unexpected behavior or broken links. The redirection set by the server-side function could override the client-side routing provided by the `Link` component.

## Solution

The `bugSolution.js` file offers a more robust approach, but there is no single solution that fits every case.  This often requires carefully coordinating your server-side and client-side routing logic to ensure they don't conflict. Methods include:

* **Consistent Routing Strategy:** Ensure your server-side and client-side functions use the same routing approach and that the redirects are correctly handled on both sides. 
* **Middleware:** Consider using Next.js Middleware to handle redirection and route manipulation on the server-side. Middleware runs before rendering the page, providing a centralized way to manage routing logic. 
* **Context API:** Use the Next.js Context API to pass data and state between server-side and client-side code. This helps in keeping the routes synchronized between the two. 
* **Route Prefetching:** Use the `prefetch` prop of the Next.js Link component to improve performance but also check carefully how the prefetch works with your server-side logic.

This issue often requires careful debugging and may involve examining your specific server-side functions and routing configurations.