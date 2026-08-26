# targetmap

Single-page map of overlapping target areas — deprivation, low ECO scheme take-up, and
Conservative + Reform council seat share — with a floating legend that toggles each layer.

- `index.html` — the whole thing. Mapbox GL JS and Poppins load from CDNs; nothing to build.
- `robots.txt` / `_headers` — keep search engines out (Netlify reads both).

## Deploying

Drop the repo on Netlify with no build command and the publish directory set to the repo root.

## The password gate

The gate compares a SHA-256 of what's typed against a hash in `index.html`. It keeps casual
visitors out and nothing more — the page and its Mapbox data are still fetchable by anyone who
reads the source. For real access control, put Netlify's password protection or an identity
provider in front of the site.

To change the password, replace `HASH` in `index.html` with the output of:

    echo -n "newpassword" | shasum -a 256

## The Mapbox token

The public token in `index.html` is visible to anyone viewing source. Restrict it to the
site's URL in the Mapbox account dashboard (Tokens → the token → URL restrictions).
