## Cookies and cross-site scripting (XSS)
By Sam Lengyel

a. Yes, there is a cookie - its name is **theme** and its values can be **default**, **red**, or **blue**. There's also a **session** cookie that holds a unique value identifying the user once they have logged in.
b. Yes; the cookie changes from **default** to whatever the user selects; **default**, **red** or **blue**. 
c. The request from the user features a **Cookie: theme = red** header while the server's response has **Set-Cookie: theme=red; Expires=~timestamp~**
d. Yes; the cookie has not expired yet so it remains set.
e. The FDF server reads the cookie sent by the browser when it sends each HTTP GET request to the server because the cookie is included in each request. It also appends **?theme=themeColor**  to the URL that it asks for, as a backup.
f. When the theme changes, the browser sends a new HTTP GET request to the server when the page is reloaded, which includes the new cookie with the new theme.
g. While on http://cs338.jeffondich.com/fdf/ or a page without the ?theme=themeColor part, change the cookie directly from the inspector in **Storage** -> **Cookies** -> http://cs338.jeffondich.com/fdf/ -> **theme** to blue, red, or default, then reload the page.
h. After enabling intercept, in the content of the HTTP GET request for the page, in the intercepted request, change the Cookie from **theme=red** to **theme=blue** and ensure that the URL doesn't have an overriding color appended to the end of it with **?theme=themeColor** for the request, removing it if necessary, then forward the request.
i. My browser stores cookies in `~/.librewolf/<profile path>/cookies.sqlite` (the ones that are told not to clear on browser restart, at least)

a. 
    1. Moriarty logs in as himself.
    2. Moriarty writes a post that consists of plaintext and HTML tags (`<span>` for the first one, `<script>` with a javascript `alert` for the second)
    3. Moriarty clicks or presses Submit Query, which sends a HTTP POST request to the server that contains the message body/title, including the HTML tags and javascript code.
    4. The server takes the data, stores it, and displays it on the main page as a table element and on its own page , and displays it unaltered on the server as HTML directly on the page (including the tags & script)
    5. Later (time indeterminate), a user clicks on a post, sending a HTTP GET request to the server which the server responds to and displays the page to the user, complete with the HTML/js from Moriarty.
    6. The `<span>` displays the altered text color, while the `<script>` executes on the page load, popping up an alert when or sometimes before the page loads.

b. By setting the cookie values via javascript, the attacker could change the user's theme or log the user out by clearing the `session` cookie.

c. The attacker could redirect the user to another page that they have more direct control over and ask for the user's credentials to access the page; they could also forward the user's cookies to this page by reading them and then passing them on to impersonate the user on the main page. 

d. 
- The server could sanitize the input, stripping certain or all HTML tags from the message before storing and displaying it. This does reduce user freedom, but also XSS possibilities.
- The server could also block all scripts from executing other than the chosen scripts for that particular site, though this would be more limiting from a web design perspective. 
- The browser could block all scripts from executing unless a page or the source of the script is trusted, though this does break some page functionality. The browser/user could also use an extension like NoScript to achieve a similar functionality.
