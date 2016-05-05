# Custom styles for Club System

**EmDev** manages an instalation of their **Club System** web application for **Takapuna Ski Club (TSC)**.  This is customized for TSC via configuration parameters, two images and one stylesheet.

## Install and deploy

Em Development deploys the following to our managed instalation of Club System;

- `source/takapuna.css`
- `source/leftimage.jpg`
- `source/rightimage.jpg`

GitHub automatically deploys this repository to `http://takapuna-ski-club.github.io`;

- Only `source/styles.css` needs to be served publicly.
- On Club System, [`/functional/styles/takapuna.css`](http://takapuna.emdev.com.au/functional/styles/takapuna.css) [`@import`](https://developer.mozilla.org/en/docs/Web/CSS/@import)s it.
- On `members.takapunaskiclub.nz`, CloudFlare redirects it directly to the GitHub-hosted `styles.css` ([`takapuna-ski-club.github.io/source/styles.css`](http://takapuna-ski-club.github.io/source/styles.css)).
- `index.html` redirects any wandering or mis-directed traffic from `http://takapuna-ski-club.github.io/` to the public website at [`www.takapunaskiclub.nz`](http://www.takapunaskiclub.nz/).

## Maintenance

TSC can then deploy changes by merging changes into `source/styles.css` in the `master` branch of this repository.  Changes to images still need to be done by EmDev.

## Testing

The `Example screenshots` directory shows how the styled pages should look once styles are applied correctly.

## Redirects

Some redirects are configured in [CloudFlare](https://www.cloudflare.com/a/page-rules/takapunaskiclub.nz).  CloudFlare is an HTTP proxy and CDN. CloudFlare also hosts DNS records for `takapunaskiclub.nz`.

The redirects only impact `members.takapunaskiclub.nz`.  To bypass CloudFlare and test Club System directly, use [`takapuna.emdev.com.au`](http://takapuna.emdev.com.au/).

The redirects are;

1. Insecure HTTP to secure HTTPS, with a shared CloudFlare SSL certificate
2. `*members.takapunaskiclub.nz/functional/styles/takapuna.css?*` to [`https://takapuna-ski-club.github.io/source/styles.css`](https://takapuna-ski-club.github.io/styles.css)
3. `*members.takapunaskiclub.nz/content/contactus.aspx` to [`http://www.takapunaskiclub.nz/contact`](http://www.takapunaskiclub.nz/contact)

## Screenshot of page rules (redirects) in CloudFlare
![Screenshot of page rules (redirects) in CloudFlare](CloudFlare-PageRules-Screenshot.png)
