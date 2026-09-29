# 419 Halloween publishing

The live site is https://419halloween.com. This public repository is the source for the GitHub Pages site. Rook retains Porkbun registrar and DNS administration; routine publishing does not need either credential.

## Change an event

- Start from the latest `main`. The site currently lives in the root `index.html`, not in a separate events database. Find `const events = [` in its script. Each object is one event. Keep its `name`, ISO `date` (`YYYY-MM-DD`), `time`, `town`, `venue`, `address`, `type`/`typeLabel`, `age`/`ageLabel`, `cost`, `accessibility`/`accessLabel`, `note`, `source`, and optional `dateLabel` accurate. The `date` and `name` pair also identifies a selected event for the printable fridge PDF. If either changes, check that selection and the claim form still work.
- Check the organizer's current listing, especially the actual date and time, venue/address, price, age limits and source URL. Preserve already-enriched values unless a newer original source corrects them. Do not replace `index.html` with an older generated export: merge the particular fields or events into current main.
- Remove ended one-off events from both the `events` array and the claim-form dropdown. Luckey Fall Festival (Sep 25-27) is an example that is still in the current source as of Sep 28 and must not return in a cleaned-up list. Check any recurring or date-range listing against its true end date, not only the first `date` field.
- The claim/update form near `id="event-submission"` has hard-coded dropdown options separate from the events array. Update those when adding, renaming or removing events. Claim links in the cards address `lola@saxtonshowcase.com`; keep their destination intentional.

## Preview, publish, verify

1. Make a branch from current `main` for substantial changes and open a pull request. Read the diff against main: event count, individual times/venues/links, ended-event removals, claim options, and any new detail-page links. A preview of a separate export is not proof of what this repository will publish.
2. Preview the edited HTML in a browser before merging. Check desktop and narrow/mobile layout, search and result count, card source links, claim/update form, event selection and fridge PDF download. If adding detail pages, open each page and its links; keep the pages and links in this repo. GitHub's pull-request diff is the source review, not a hosted preview of an unmerged branch.
3. Merge or push to `main` only after the review. GitHub Pages deploys this branch to https://419halloween.com. Check the repository's Actions / Pages run succeeds, then load the live domain and spot-check the changed cards and links. A commit alone is not proof the site is live; wait for the deployment.
4. The Open Graph/Twitter preview tags are in the `index.html` head. Keep `og:title`, `og:description`, `og:url`, `og:image`, `twitter:card`, `twitter:image` and `1-share-card.png` in sync. The image URL is https://419halloween.com/1-share-card.png. If a social composer shows an older card, re-scrape the exact domain URL in LinkedIn Post Inspector rather than changing DNS.

For the first handoff publish, share the proposed branch/PR and source of the 37-event revision, show the changed event data against main, then watch the Pages deployment and live result together. No tokens, passwords or DNS details belong in this repo or email.
