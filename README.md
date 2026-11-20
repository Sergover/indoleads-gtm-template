# Indoleads Universal Tag — Google Tag Manager template

Google Tag Manager template for advertisers working with [Indoleads](https://indoleads.com).
It installs the Indoleads container on your website without editing site code.

## What the tag does

On every page where it fires, the tag:

1. Adds your offer settings to the `INDOLEADS_LIB` queue on the page (`offer_id` and the Indoleads network address).
2. Loads the Indoleads container script from `https://fulltrack.org/js/platform/container_v2.min.js`.

This is the same container you see in the **Container** block of your offer card in the Indoleads platform —
the template just lets you deploy it through GTM.

## Before you start

- An active advertiser account and offer on Indoleads.
- Your **Offer ID** — the number shown in your offer card in the Indoleads platform. If unsure, ask your Indoleads account manager.
- Publish rights in the GTM container of your website.

## Installation

1. In Google Tag Manager open **Tags → New → Tag Configuration**.
2. Click **Discover more tag types in the Community Template Gallery**, search for **Indoleads Universal Tag** and click **Add to workspace**.
   Until the template appears in the Gallery, import it manually: download `template.tpl` from this repository, then in GTM go to **Templates → Tag Templates → New → ⋮ → Import**, save, and pick it as the tag type.
3. In the tag settings fill in **Offer ID** — digits only, for example `12345` (the field is not validated, so double-check it).
4. Under **Triggering** select **All Pages** (Page View) so the container loads on every page of the site.
   The tag passes only the Offer ID. Conversion reporting (postback or pixel) is set up separately in your Indoleads integration — ask your account manager.
5. Save the tag, check it in **Preview** mode, then **Submit** and publish the container.

If you have several Indoleads offers, create a separate tag with its own Offer ID for each offer (on the same site or on different sites).

## How to check it works

1. Open GTM **Preview** and load any page of your site — your tag (the name you gave it) should be listed under *Tags Fired*.
2. In Chrome DevTools → **Network**, filter by `fulltrack.org`: the request to `container_v2.min.js` should return status `200`.
3. In DevTools → **Console**, type `INDOLEADS_LIB` — it should exist on the page.

If the tag does not fire, check that the trigger is **All Pages** and that a consent tool or a "load scripts after user interaction" setting on your site does not block it.

## Permissions used

| Permission | Why |
|---|---|
| Accesses global variables — `INDOLEADS_LIB` (read, write) | Passes the Offer ID to the container |
| Injects scripts — `https://fulltrack.org/js/platform/container_v2.min.js` | Loads the Indoleads container |

The template itself uses no other APIs. The loaded container script then works on the page as described in your Indoleads offer settings.

## Fields

| Field | Required | Description |
|---|---|---|
| Offer ID | Yes (not validated) | Your Indoleads offer ID (digits) |

## Support

Questions and problems: [help.indoleads.com](https://help.indoleads.com) or your Indoleads account manager.
Bug reports for the template itself: [GitHub Issues](https://github.com/Sergover/indoleads-gtm-template/issues).

## License

Apache 2.0 — see [LICENSE](LICENSE).
