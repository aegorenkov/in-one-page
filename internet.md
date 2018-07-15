# What happens when you navigate to a page

- Page unload
- Redirect
- App Cache
- DNS
  - Check the browser, OS, router, and ISP cache
  - Perform recursive search 
- TCP
- HTTP Request
- HTTP Response
  - Web Server
  - Request Handler
- DOM Processing
  - Parsing: HTML, CSS, JS
  - Rendering: Construct DOM Tree, Render Tree, Layout of Render Tree, Painting the render tree
- Page load
  - Send requests for additional dependencies such as images, JS, and CSS
  - JS is executed and may make further AJAX requests
  
