# RedirectMeTo

A simple tool for redirecting you.

https://redirectmeto.com

## Use Case

Let's say you're trying to test a new OAuth connection on your local machine with something like Google but they require the redirect URL to have a domain with an approved TLD (because they don't allow things like `localhost` or `.dev`). You can use a RedirectMeTo url to redirect to your localhost.

## Examples

https://redirectmeto.com/https://www.google.com/search?q=puppies

http://redirectmeto.com/http://localhost:4000/oauth/authorize

http://redirectmeto.com/http://client.dev/page

## License
MIT. See the [license.md file](license.md) for more info.
