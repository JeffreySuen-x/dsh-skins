# 🐋 dsh Skins

Making a set of skins today is astonishingly simple — it takes just one conversation.

## Why dsh needs skins

dsh's interface is built for long hours: token-driven, semantically colored, with light and dark modes finished to a fault. That is its strength and its cost — "finished to a fault", stared at for hundreds of hours, becomes "always the same". Developers will spend an afternoon tuning an editor theme, pick a comfortable palette for the terminal, choose the softest bubble color in a chat app — yet the workbench usually stays factory-fresh. Not because they don't want to change it, but because they can't find where to start: it is so correct that it leaves no handle.

Skins are that handle. They change no feature, add no noise, move none of the buttons you know by heart — they only change the first thing you see when you look up. And dsh happens to leave a decent door open for exactly this: the whole interface consumes only `--dsw-alias-*` semantic tokens. A skin re-points those variables and lays a backdrop behind the interface, and the entire surface changes clothes at once. It is a flattering door for those of us who just want it to look a little better.

## What we could do was, honestly, limited

We brought in an entire animation library — one hundred and twenty-some components, from flowing auroras and liquid chrome to hyperspace travel and click-particle storms — and graded them one by one.

The verdict split four ways:
a small handful are pure CSS and could be absorbed; some need a thin layer of scripting; and the large remainder — the ones that actually make you say "wow" — are all WebGL shaders that need a 3D engine and will never fit inside a stylesheet.
We also tried replacing the cursor, tried magnetism, tried a global particle rain. We pulled them all back out.

The reason is simple:
this is clothing made for harness developers; technology is no longer the attraction — quiet is.
A replaced cursor breaks muscle memory; particle rain eats attention; glass that is too clear eats the text. So the pack settled on these boundaries:

- CSS plus one feather-light pointer script — no engines, no network requests, no image assets;
- no layout, typography, or interaction changes — those belong to the product itself;
- every backdrop is an inline SVG scene — one file is everything, works offline, and forwarding it to a friend is a complete move;
- all motion respects the system's reduce-motion setting: quiet is the default, liveliness is opt-in.

We held complexity back. What remains is what you can live with for a long time: a decent backdrop, a layer of clear glass, and a few effects that know when to stop.
That is enough.

## Five coats

**🌐 DeepSeek Web (deepseek-web) — a derivative true to the official style**

This is where the pack began, and the coat closest to the official site. The brand blue `#4d6bfe` is lifted straight from the site's stylesheets; the backdrop borrows its aurora, grid, and film grain; the whale logo sways gently as it does on the homepage; the composer's border carries a ring of orbiting starlight.

It transplants the official look onto the workbench — the product is not the website, so it is a derivative, not a replica; and because it is a derivative, it keeps its composure: pure CSS, not a single line of script. If all you want is "the official look", pick it, and the story can end here.

**⛰️ Dusk Mountains (dusk-mountains) — the company of sunset**

Qingdai is a very old pigment; the ancients used it to paint distant mountains. In light mode this coat is the pink-violet of dawn; in dark mode it is stars, a moon, and ridge after ridge — and the hour when dusk dyes the mountains indigo is often the hour you have been writing code the longest. It keeps the sunset behind the interface, saying nothing, like company that needs no words.

**🌃 Neon Night (neon-night) — a gentle embrace**

A synthwave sun rises slowly in dark mode, notched with scanlines, over a glowing floor. The pink accents stand out brazenly in a world of blues, but they don't glare: late at night it becomes a soft, luminous street that wraps around you. Someone coding into the small hours needs exactly that embrace.

**🌊 Deep Sea (deep-sea) — evening contemplation**

Light mode is a turquoise shoal pierced by light; dark mode is the abyss, with shafts of light and bubbles rising slowly. No mountains, no sunset — only water, light, and bubbles. It is made for contemplation: when you close the meetings in the evening, take off the headphones, and sit thinking one thing through, this sea will think with you.

**✨ Super (super) — breaking through yourself**

The official blue of deep space as the canvas, plus everything we know: a cursor-following border, a spotlight, 3D tilt, a glare sweep on the send button, click sparks. It is the one coat in the five that refuses to behave — worn not for others to see, but for yourself: when you want to find out how much you can still love an interface, wear it.

## The restraint of motion

We counted the cost of every star:

- 🧲 cursor-following border — the composer's highlight turns toward your cursor, and resumes its cruise once you leave;
- 🔦 spotlight — a soft pool of light follows the cursor into the composer, and goes out when it leaves;
- 🎯 3D tilt — the composer leans toward the cursor, two and a half degrees at most, never more;
- ✨ send-button glare — a white sweep crosses the button on hover;
- 🎆 click sparks — every click bursts ten brand-colored stars that clean themselves up in half a second.

When the system's reduce-motion is on, all of it stands still and only the colors and backdrops remain.
Our entire understanding of "skins" is this: you may have them, but they must go quiet with one switch.

## The holes we stepped in

This section exists so you know why the pack looks the way it does.

**The first version was criticized as "I don't see any change".** True story — version one touched only a few color tokens, and restraint had crossed into invisibility. That is how the whale sway, the star border, and the scene backdrops were born. The floor of restraint is this: people have to see it before they can like it.

**In light mode the backdrop barely showed through.** The glass was too opaque and the pale scenes drowned in white fog. We thinned the glass and deepened the scenes until the backdrop was truly worn, not merely present.

## Quick start

**Wear it inside the product**: open dsh Web → Settings → General → Skin → click a cube. The choice is remembered, and it is still there next time.

**Wear it via a browser extension**: install Stylus (or any UserCSS extension) → create a new style → paste the entire contents of the matching `.user.css` → scope it to your deployment URL → save. Works against any deployed instance, no code changes.

> Other profiles can embed the gallery: insert `- id: ui-skin-gallery` (name `@deepseek-ai/dsh-client-ui-skin-gallery`) into the profile's cordis.patch.yml and declare the package dependency.

## FAQ

**Q: I picked a skin and nothing changed?** Hard-refresh first (`Cmd+Shift+R` on macOS, `Ctrl+Shift+R` on Windows/Linux); make sure the cube shows as selected in Settings; then check whether an extension like Dark Reader is fighting it.

**Q: This is too plain?** Yes, on purpose. Want more spectacle? Swap the scene in `super.user.css` for an SVG of your own, or go write a plugin for the WebGL effects — our restraint is not your ceiling.

**Q: Do skins survive a new machine?** The in-product choice lives in `ui-skin.skin` on the local machine; the extension route syncs with the browser. Forward this pack to a friend and they get the same look, unchanged.

## Files

```
deepseek-harness-skins-1.0.0/
├── README.md
├── README.en.md
├── LICENSE.txt
├── deepseek-web.user.css
├── dusk-mountains.user.css
├── neon-night.user.css
├── deep-sea.user.css
└── super.user.css
```

## License and credits

- MIT license (see LICENSE.txt);
- the palette and keyframe timings were captured from deepseek.com's public stylesheets;
- glass, film grain, aurora, and star-border ideas were studied from [vue-bits](https://github.com/davidhdev/vue-bits) (MIT + Commons Clause); the CSS here is original and copies no component code.

## For a bit of joy

These skins solve no productivity problem, and they will not remove a single bug from your code. They only let the tool that keeps you company every day change coats once in a while — so that when the code stops flowing, you can look up and see a sea, a mountain, a little star chasing your cursor, or a sun going down in scanlines.

All for a bit of joy — nothing more.
