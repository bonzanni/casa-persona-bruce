# casa-persona-bruce

A public **demo persona pack** for [Casa](https://github.com/bonzanni/ha-casa-app):
`demo/bruce@0.1.0` — a brooding, terse, relentlessly prepared presentation layer
inspired by Batman, the fictional character.

This is a fan-made demonstration of Casa's persona format. It is not affiliated
with, sponsored by, or endorsed by DC or Warner Bros., and contains no copyrighted
text from any Batman work — only original prose describing a character archetype.

## What a persona is (and is not)

A Casa persona controls **presentation only**: display name, pronouns, eight 1–5
trait axes, up to three quirks, and a short prose core. It cannot grant tools,
permissions, memory access, or any capability — those come from the agent's role
and runtime configuration. Bruce makes an agent *sound* like a nocturnal guardian;
it does not give it a grappling hook.

## Layout

```
manifest.json          # checksummed file manifest (pack identity)
pack/persona.yaml      # identity, traits, quirks
pack/persona.md        # # Core (300–500 chars) + ## Negative space
```

## Installing

Ask Casa's configurator in chat, e.g.:

> Install the persona from bonzanni/casa-persona-bruce

You will get an Approve/Deny prompt in your operator DM; nothing installs without
that tap. Once installed, apply it:

> Apply the bruce persona to the concierge

Applying to a resident takes effect on the next restart; applying to an installed
specialist takes effect on an agents reload. Swapping a persona rolls the agent's
session epoch — it is a genuine identity change, not a costume.

## License

MIT (the pack prose and this repository). Batman and related marks belong to
their respective owners; this repository claims no rights in them.
