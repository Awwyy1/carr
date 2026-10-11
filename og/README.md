# og

The picture other apps draw when someone shares a link to the site — in
iMessage, WhatsApp, Messenger, Facebook, Telegram, Slack, on X.

One card per page, 1200 × 630, built from that page's own photo with the
Nord Garage lockup over it:

| file           | the page it belongs to |
|----------------|------------------------|
| `home.jpg`     | `/`                    |
| `services.jpg` | `/services`            |
| `wash.jpg`     | `/wash`                |
| `rental.jpg`   | `/rental`              |
| `about.jpg`    | `/about`               |
| `icon.png`     | the icon iOS uses when the site is added to a home screen |

**These are generated, not photographs.** Replacing a file in `/photos`
does not redraw the card that was built from it, so if you swap a page
photo, say so and the card gets rebuilt to match.

Each page points at its own card in its `<head>`, in the `og:image` line.

## Changing the address

The lines are absolute, because a scraper has no page to resolve a
relative path against. They all read

    https://nordgaragev3.vercel.app

so moving to `nordgarage.is` means replacing that one address in the
`<head>` of all five pages, and in the `url`, `image` and `logo` lines of
the `application/ld+json` block on the home page.

## Checking a card

Paste the page address into one of these and it will show you exactly
what each app draws, and refresh its own cache:

- Facebook and Messenger — https://developers.facebook.com/tools/debug/
- X — https://cards-dev.twitter.com/validator
- LinkedIn — https://www.linkedin.com/post-inspector/

iMessage and WhatsApp keep their own cache for a few days and cannot be
cleared by hand, so a card you have already shared may take a while to
change.
