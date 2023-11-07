# RedirectMeTo

A simple tool for redirecting you.

https://redirectmeto.com

## Use Case

Let's say you're trying to test a new OAuth connection on your local machine with something like Google but they require the redirect URL to have a domain with an approved TLD (because they don't allow things like `localhost` or `.dev`). You can use a RedirectMeTo url to redirect to your localhost.

## Examples

https://redirectmeto.com/https://www.google.com/search?q=puppies

http://redirectmeto.com/http://localhost:4000/oauth/authorize

http://redirectmeto.com/http://client.dev/page

## How?

Originally, RedirectMeTo was a simple PHP script running on a Digital Ocean droplet that redirected all requests except for the index that displays the homepage. Starting in November 2023 the root path is a static HTML file hosted with GitHub pages and redirects all happen via a CloudFlare worker that is running the following script:

```js
export default {
  async fetch(request, env, ctx) {
    var url = new URL(request.url)
    var redirectUrl = url.pathname.substring(1) + url.search
    return Response.redirect(redirectUrl, 302)
  }
}
```

This allows for RedirectMeTo to run indefinitely for zero cost (except for the domain) and zero maintenance (serverless).

## License
MIT. See the [license.md file](license.md) for more info.
