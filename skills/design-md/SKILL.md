---
name: design-md
description: Curated collection of 74 DESIGN.md files — plain-text design-system documents (colors, typography, spacing, component tokens) reverse-engineered from real company websites (Apple, Stripe, Linear, Notion, Airbnb, Vercel, Nike, Tesla, and more). Use this whenever the user wants to build, mock up, redesign, or restyle a UI "in the style of" a named brand, wants a DESIGN.md dropped into their project, or asks what a specific company's design system/tokens look like — even if they don't say "DESIGN.md" explicitly (e.g. "make this look like Stripe", "give me an Apple-style landing page", "match Linear's dark theme"). Sourced from github.com/VoltAgent/awesome-design-md.
---

# design-md — brand design-system reference

DESIGN.md is a plain-text design-system document (colors, type scale, spacing, component
rules) that an AI coding agent reads to generate UI that stays visually consistent with a
given design language. This skill bundles 74 of these files, each a deep breakdown of one
company's real website — not a logo/color cheat sheet, but usable tokens: hex values, font
stacks and weights, radii, shadow values, spacing ladders, and the "voltage" (the one or two
signature moves that make the brand recognizable).

## When to use this

Reach for this skill whenever the user wants UI that evokes a specific, real brand —
whether they name DESIGN.md explicitly or just say things like "make it feel like Notion,"
"I want a dark, Linear-style dashboard," or "give me a Ferrari-esque hero section." It also
covers direct requests to fetch/generate a DESIGN.md file for a company in the index below.

## How to use it

1. **Identify the brand** the user wants (by name, or by describing a vibe that matches one
   of the entries below — e.g. "warm cream SaaS with a coral CTA" → `claude` or `cal`).
2. **Read the matching reference file**: `references/<brand>.md` (see the index for the
   exact slug — lowercase, matches the table's first column).
3. **Apply it**: either copy the file into the user's project root as `DESIGN.md` (if they
   want the artifact itself), or extract the relevant tokens (colors, fonts, radii, spacing)
   directly into the component/page you're building. Prefer reading only the one or two
   files you need — don't load the whole `references/` directory into context.
4. If the user names a brand **not in the index**, say so plainly and either fall back to
   asking what aesthetic they're after, or build from general design judgment — don't
   fabricate a fake DESIGN.md and imply it came from this collection.

Each reference file has real front-matter (`colors:`, `typography:`, etc.) followed by prose
sections analyzing layout, imagery, motion, and component patterns in more depth — skim the
front matter for quick token lookups, read the full file for a thorough restyle.

## Brand index

| slug | design language |
|---|---|
| `airbnb` | A warm, generous consumer marketplace anchored on a clean white canvas and Airbnb Rausch (#ff385c), the single brand voltage that carries every primary CTA, search-button orb, and rating dot. Type... |
| `airtable` | A sober, editorial workflow-software interface anchored on white canvas and dark-ink type, where brand voltage comes from full-bleed signature cards in coral, dark green, peach, and dark navy that... |
| `apple` | A photography-first interface that turns marketing into a museum gallery. Edge-to-edge product tiles alternate light and dark canvases, framed by SF Pro Display headlines with negative... |
| `binance` | A confident financial-platform interface anchored on a deep near-black canvas, where Binance's iconic yellow (#FCD535) carries every primary CTA, brand accent, and value-claim moment. Type runs... |
| `bmw` | BMW's corporate site — distinct from BMW M's motorsport-bombastic variant, this is a measured and settled corporate-automotive interface. On a light (cream-tinted white) canvas, BMW corporate blue... |
| `bmw-m` | A motorsport-engineering interface anchored on a near-black canvas with white BMW Type Next Latin display headlines in confident UPPERCASE. The brand carries no decorative voltage — its energy... |
| `bugatti` | An austere luxury-automotive interface that uses near-pure black canvas, white uppercase letterspaced display, and full-bleed automotive photography as the only voltage. The system runs three... |
| `cal` | A clean, calendar-software-first interface anchored on white canvas with black primary CTAs and custom Cal Sans display typography. The system reads as friendly modern SaaS — generous whitespace,... |
| `claude` | A warm-canvas editorial interface for Anthropic's Claude product. The system anchors on a tinted cream canvas with serif display headlines, warm coral CTAs, and dark navy product surfaces (code... |
| `clay` | A vibrant claymation-meets-data interface for Clay.com (GTM data-orchestration platform). Anchors on white canvas with dark-navy primary CTAs, custom rounded display type, and saturated... |
| `clickhouse` | A high-performance database interface anchored on near-pure black canvas with electric yellow as the brand voltage. White typography in confident sans, yellow CTAs, and yellow-text stat numbers... |
| `cohere` | Cohere's 2026 web system is a controlled enterprise AI interface built from stark white editorial space, deep green-black product bands, soft mineral surfaces, rounded media cards, and a... |
| `coinbase` | An institutional-grade crypto exchange whose marketing surfaces read like a quietly-confident financial-services brand. The base canvas is pure white; Coinbase Blue (`#0052ff`) is the single brand... |
| `composio` | A developer-tools brand for AI-agent tool integration whose marketing surfaces lean into a dark, technical aesthetic with a single deep-electric-blue voltage (`#0007cd`). The page floor is... |
| `cursor` | An AI-first code editor whose marketing site reads like a quietly-confident developer-tools brand with a warm-cream editorial canvas (`#f7f7f4`) instead of the typical dark IDE atmosphere.... |
| `dell-1996` | An inspired interpretation of Dell.com's 1996 design language — a catalog-era enterprise web design built around a literal black page frame, vivid flat color-block "ribbon cards" tinted in sage,... |
| `elevenlabs` | A voice-AI brand whose marketing surfaces read like a quietly editorial print magazine. The base canvas is off-white (`#f5f5f5`) holding warm near-black ink (`#292524`); the brand voltage is... |
| `expo` | A React Native developer-platform whose marketing site reads like a quietly-confident infrastructure brand. The base canvas is pure white with a soft sky-blue gradient atmospheric wash behind the... |
| `ferrari` | A luxury-automotive brand whose marketing surfaces read as cinematic editorial. The base canvas is near-black (#181818) holding pure white display type; white-canvas bands appear only inside... |
| `figma` | A confident black-and-white editorial frame interrupted by oversized, hand-cut pastel color blocks. The marketing canvas is rigorously monochrome — figmaSans variable type, pure white surfaces,... |
| `framer` | A confident dark-canvas builder marketing site that treats the page like a working artboard — pure black surfaces, white display type set in GT Walsheim Medium with aggressive negative tracking,... |
| `hashicorp` | An enterprise-infrastructure marketing canvas built around a near-black ground (#000000) and a system of per-product accent colors — Terraform purple, Vault yellow, Consul pink, Waypoint cyan,... |
| `hp` | An inspired interpretation of HP's design language — a white-paper enterprise-consumer system anchored by HP Electric Blue (#024ad8) as the lone signal CTA, near-black ink (#1a1a1a) for... |
| `ibm` | An enterprise-marketing canvas faithful to Carbon Design System: white surfaces, charcoal type, IBM Blue (#0f62fe) as the single confident accent, and a deliberately flat-square aesthetic where... |
| `intercom` | An editorial customer-service marketing canvas built around a soft cream-white ground, charcoal type set in Saans (Intercom's proprietary geometric sans), and a single confident Fin Orange... |
| `kraken` | Kraken's website is a clean, trustworthy crypto exchange that uses purple as its commanding brand color. The design operates on white backgrounds with Kraken Purple (#7132f5, #5741d8,... |
| `lamborghini` | Lamborghini's website is a cathedral of darkness — a digital stage where jet-black surfaces stretch infinitely and every element emerges from the void like a machine under a spotlight. The page is... |
| `linear.app` | A near-black product-focused marketing canvas built around #010102 (the deepest dark surface of any tool in this collection), light gray text (#f7f8f8), and the signature Linear lavender-blue... |
| `lovable` | Lovable's website radiates warmth through restraint. The entire page sits on a creamy, parchment-toned background (#f7f4ed) that immediately separates it from the cold-white conventions of most... |
| `mastercard` | Mastercard's experience reads like a warm, editorial magazine built from soft stone and signal orange. The canvas is a muted putty-cream (#F3F0EE) — not white, not gray, but a color that feels... |
| `meta` | Meta's design system spans hardware commerce (Quest VR, Ray-Ban Meta AI glasses) and brand surfaces with a confident product-merchandising voice. The system pairs a stark white canvas with... |
| `minimax` | MiniMax presents itself as a premium AI infrastructure brand through a striking duality — bold black-pill CTAs and stark white canvas for marketing, paired with vibrant gradient product cards... |
| `mintlify` | Mintlify presents documentation infrastructure with a dual-mode aesthetic — atmospheric sky-gradient marketing heroes (cloud illustration backdrops, soft cream-to-blue washes) paired with dense... |
| `miro` | Miro presents itself as the AI-powered visual workspace through a confident, almost playful brand voice — anchored by its signature canary yellow wordmark over white canvas... |
| `mistral.ai` | Mistral AI brands itself with a singular signature — atmospheric sunset gradients (mustard, orange, deep red) layered over photography of mountains, plus a horizontal "sunset stripe" bar that... |
| `mongodb` | MongoDB carries a strong dual-mode visual identity — dark deep-teal hero bands with bright MongoDB green CTAs paired with stark white documentation surfaces. The signature... |
| `nike` | A photography-first commerce system built on extreme typographic contrast — towering uppercase Futura display lockups burned into editorial campaign imagery, sitting above a dense, neutral,... |
| `nintendo-2001` | An analysis of Nintendo.com's 2001 design language — a brushed-periwinkle "console chrome" interface where every panel is a beveled metal plate, navigation glows amber over a halftone-dotted... |
| `notion` | Notion presents itself as the all-in-one workspace through a confident, illustration-rich brand voice — anchored by a deep navy hero band decorated with brand-colored... |
| `nvidia` | An engineering-grade marketing system organized around two surface modes — a deep black canvas for hero and footer chapters and a flat paper-white canvas for body content — connected by a single,... |
| `ollama` | An almost defiantly minimal documentation-first system that treats the home page like a Markdown README — paper-white canvas, 36px center-aligned heading, a single black pill CTA, an inline... |
| `opencode.ai` | A terminal-native marketing system rendered entirely in Berkeley Mono — every word on the page, from the hero headline down to the footer fine print, is monospaced. The page itself reads like a... |
| `pinterest` | A photography-first discovery system organized around the Pinterest Red CTA, the masonry pin grid, and a soft warm-cream chrome that gets out of the imagery's way. The home page is a... |
| `playstation` | A three-surface marketing system organized around alternating black, white, and PlayStation Blue chapters that scroll past the viewer like a console launch trailer. Each section has a single... |
| `posthog` | A playful developer-tools system rendered on a warm cream canvas with hand-drawn hedgehog mascots dotted across every page like marginalia in a sketchbook. The chrome reads like a friendly... |
| `raycast` | Raycast's marketing system reads like an extended product screenshot. The chrome IS the in-product chrome at marketing scale: pure-near-black canvas, hairline 1px borders, command-palette-style... |
| `renault` | Renault's web presence pairs the freshly-modernised Renault diamond with a stark black-and-white canvas, a signature Sunlight Yellow accent, and the proprietary... |
| `replicate` | Replicate's marketing surfaces pair the warm-cream developer-tools aesthetic of an indie ML playground with a confident hot-orange brand accent and a signature display typeface... |
| `resend` | Resend's marketing surfaces sit on a near-pure black canvas with off-white text and a single signature color — the deep editorial-serif Domaine Display headline mark — that gives an otherwise... |
| `revolut` | Revolut's marketing surfaces pair a stark black canvas with the brand's cobalt-violet (#494fdf) and a wide accent palette of deep, fully-saturated product colours — teal, light-blue, deep pink,... |
| `runwayml` | Runway's interface is a cinematic reel brought to life as a website — a dark, editorial, film-production-grade design where full-bleed photography and video ARE the primary UI elements. This is... |
| `sanity` | Sanity's website is a developer-content platform rendered as a nocturnal command center -- dark, precise, and deeply structured. The entire experience sits on a near-black canvas (#0b0b0b) that... |
| `sentry` | An inspired interpretation of Sentry's design language — a developer-tools brand built on a deep purple-violet midnight canvas, electric lime accents, and a slightly subversive illustrated... |
| `shopify` | An inspired interpretation of Shopify's design language — a cinematic commerce platform that runs two parallel design tracks. Near-black marketing/product pages with giant thin-weight display type... |
| `slack` | An inspired interpretation of Slack's design language — a workplace messaging brand built on a deep aubergine primary, with cream-lavender hero gradients, blue inline links, and pill CTAs... |
| `spacex` | An inspired interpretation of SpaceX's design language — a mission-oriented aerospace brand built on pure black canvas, full-bleed photographic and video heroes of rockets and Mars landscapes, and... |
| `spotify` | Spotify's web interface is a dark, immersive music player that wraps listeners in a near-black cocoon (#121212, #181818, #1f1f1f) where album art and content become the primary source of... |
| `starbucks` | Starbucks' design system is a warm, confident retail flagship wearing the green of their storefront apron across every surface. The canvas alternates between a neutral-warm cream (#f2f0eb)... |
| `stripe` | An inspired interpretation of Stripe's design language — a financial-infrastructure brand built on a deep navy ink, an electric indigo primary, and a recurring atmospheric gradient mesh that... |
| `supabase` | An inspired interpretation of Supabase's design language — an open-source database platform built on a clean white-and-near-black system with a single signature emerald-green CTA, a custom... |
| `superhuman` | An inspired interpretation of Superhuman's design language — a fast-email productivity brand split between an editorial dark hero and a quiet white content body with off-warm-grey ink... |
| `tesla` | Tesla's website is an exercise in radical subtraction — a digital showroom where the product is everything and the interface is almost nothing. The page opens with a full-viewport hero that fills... |
| `theverge` | The Verge's 2024 redesign feels like somebody wired a Condé Nast magazine to a chiptune soundboard. The canvas is almost-black (#131313), the headlines are built from a brutally heavy display... |
| `together.ai` | An inspired interpretation of Together AI's design language — an AI infrastructure platform whose surface alternates between near-black hero bands (with a three-color orange-magenta-periwinkle... |
| `uber` | An inspired interpretation of Uber's design language — a transportation-and-delivery super-app brand whose web surface is a black-and-white duet, framed by a custom geometric display sans,... |
| `vercel` | An inspired interpretation of Vercel's design language — a developer-platform brand whose surface is a stark black-and-ink duet on near-white canvas, broken at hero scale by a multi-color mesh... |
| `vodafone` | An inspired interpretation of Vodafone's design language — a telecom super-brand whose web surface alternates between editorial photography hero bands with massive uppercase display headlines and... |
| `voltagent` | An inspired interpretation of Voltagent's design language — a developer-focused AI agent engineering platform whose surface is an unrelenting near-black canvas broken only by a single... |
| `warp` | An inspired interpretation of Warp's design language — an agentic terminal-and-development-environment brand whose surface is a warm near-charcoal canvas, broken only by clean Inter typography... |
| `webflow` | An inspired interpretation of Webflow's design language — a visual web development platform whose surface contrasts a deep near-black #080808 primary against a generous white canvas, broken by a... |
| `wired` | An inspired interpretation of Wired's design language — a flagship technology-magazine brand whose surface is a strict editorial duet of stark black wordmark on white canvas, anchored by a tall... |
| `wise` | An inspired interpretation of Wise's design language — a global money-transfer brand whose surface combines an unusually heavy near-black display sans with a vivid lime-green brand accent... |
| `x.ai` | An inspired interpretation of xAI's design language — a strict near-black canvas broken only by white pill outlines, occasional warm sunset/dusk gradient accents, a custom geometric sans... |
| `zapier` | An inspired interpretation of Zapier's design language — a workflow-automation platform whose surface combines warm-cream neutrals with deep coffee ink and a single saturated orange CTA accent... |

## Source & updates

Extracted from [VoltAgent/awesome-design-md](https://github.com/VoltAgent/awesome-design-md)
(74 files as of 2026-09-04). To refresh with newer entries from upstream, re-clone that repo
and re-copy any new `design-md/<brand>/DESIGN.md` files into `references/<brand>.md`.
