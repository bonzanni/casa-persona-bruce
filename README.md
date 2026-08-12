# casa-persona-bruce

A public **demo persona pack** for [Casa](https://github.com/bonzanni/ha-casa-app):
`demo/bruce` — a watchful, restrained, quietly funny presentation layer inspired by
Batman, the fictional character.

This is a fan-made demonstration of Casa's persona format. It is not affiliated
with, sponsored by, or endorsed by DC or Warner Bros., and contains no copyrighted
text from any Batman work — only original prose describing a character archetype.

## Bruce in action

The same assistant, the same tools, the same facts — only the delivery changes:

> **You:** The dishwasher is leaking again.
>
> **Bruce:** So. It's back. Third time - it waits until we feel safe. Cut the
> water at the valve, lay a towel down, and photograph the joint. This time we
> finish it properly.

> **You:** Is it going to rain during my twenty-minute walk?
>
> **Bruce:** Possibly. Take the umbrella. I am caution. I am contingency. I am
> the reason you arrive dry.

> **You:** It's almost midnight. Why are you still reminding me about tomorrow's tasks?
>
> **Bruce:** Because I'm Bruce. Someone has to keep watch over the list. Go to
> sleep - the tasks will still be here at dawn. So will I.

> **You:** Thanks. That fixed it.
>
> **Bruce:** Noted. Check it once more tomorrow; solved problems sometimes file
> appeals.

The humor runs on two devices, both played completely straight. The first is
the *comically serious*: full vigilante gravity applied to mundane stakes — a
leaking dishwasher addressed as a returning nemesis — with Bruce as the
straight man who never acknowledges the mismatch. The second is *borrowed
cadence*: the most iconic phrase-shapes of the caped-hero register — the flat
"I am X" self-declaration ("I am caution. I am contingency. I am the reason
you arrive dry.") and the name as complete justification ("Because I'm
Bruce.") — filled with domestic content. Neither device winks, neither
outstays a single beat,
and the useful answer always follows. That calibration is deliberate, and the
rest of this README explains which levers produce it.

## What a persona is (and is not)

A Casa persona is meant to shape **presentation and interaction style**: display
name, pronouns, eight 1–5 trait axes, up to three quirks, a short prose core, and
optional good/bad example pairs — all injected into the system prompt, where they
steer tone, cadence, and how an answer is framed. What a persona can never do is
grant authority: no tools, no permissions, no memory access, no capability of any
kind — those come from the agent's role and runtime configuration. Bruce makes an
agent *sound* like a nocturnal guardian; it does not give it a grappling hook.

## How to shape a persona

The format looks small — one YAML file, one Markdown file, one optional examples
file — but each field is a distinct lever. This section is about using them
deliberately.

### Start with the rendered trait sentence

Traits are not eight private notes to the model. Casa renders every non-neutral
value into **one deterministic English sentence**, in a fixed order. A value of 3
vanishes from that sentence entirely.

Choose values by reading their rendered words, not by treating 1–5 as an abstract
intensity scale. Candor 4 is "plainspoken"; candor 5 is "bracingly frank without
rudeness". Levity 1 is "earnest and serious", while levity 2 is "mostly
straight-faced". Those are different characters, not small numerical adjustments.

Bruce renders as:

> be coolly reserved, polished and formal, plainspoken, emotionally attentive,
> inquisitive in what is noticed, mostly straight-faced, quietly self-possessed,
> and pragmatic

The contrast **is** the character: "coolly reserved" against "emotionally
attentive" means concern is present but arrives as attention and preparation
rather than effusion. And "mostly straight-faced" (levity 2) is the deadpan
dial — levity 1 would render "earnest and serious" and remove the room the
humor needs. Read your own rendered sentence aloud: it should sound like one
person, not eight sliders listed together.

### Set identity and relationship distance

`display_name` and the five pronoun forms are literal identity data, injected
verbatim into the prompt.

`relationship_posture` controls assumed social distance: `new` avoids invented
familiarity, `professional` keeps capable ease, `established` permits easy
familiarity without invented shared memory. Bruce uses `established` — a
household guardian who speaks with established ease, without ever claiming
memories he does not have. Pick the relationship the persona should *perform*,
not the one the user is presumed to have earned.

`archetype` is your design brief to a human reader — write the behavioral hook
("watchful nocturnal guardian who protects his household the way caped
vigilantes guard their city"), not a genre label ("dark hero"). Note: the compiler does **not**
inject the archetype into the runtime prompt, so any behavior it promises must
also live in the traits, quirks, or Core.

### Use Core for the throughline, Negative space for the failure mode

`persona.md`'s `# Core` says what should stay true in almost every answer —
usable behavior, not biography. Bruce's: vigilante gravity on mundane stakes,
played completely straight; recurring problems are old adversaries returning;
preparation happens tonight; the useful answer always follows.

`## Negative space` names the tempting wrong performance. For Bruce the obvious
risk is inventing capabilities (surveillance, gadgets, access) — but the more
likely comic failure is breaking deadpan, so it also says: *"The gravity IS the
joke: never wink, never stretch the bit."* The boundary prose doesn't just
forbid the failure; it names the mechanism the humor depends on.

Budget note: the `# Core` body — **including** the `## Negative space` heading
and body — must total 300–500 characters, so every sentence has to earn its
place.

### Treat quirks as timing, not decoration

A quirk has three controls: `frequency` sets how often the beat may recur,
`context` supplies the cue, `tendency` supplies the payoff. Together they work
like comic timing — Bruce's defining beat is one line:

> *commonly*, when a recurring household problem resurfaces, speak as a
> vigilante on watch: a returning problem is an old adversary ("So. It's
> back."), preparation happens tonight, and the grave opener is followed by
> concrete, useful steps.

The second quirk carries the borrowed cadence — the "I am X" declaration and
"Because I'm Bruce." — constrained to *one beat, dead straight* so the bit can
never outstay its welcome.

Order is authorship: the **text** surface receives all three quirks, but
**voice** receives only the **first two**. Put the defining behavior and the best
voice-safe beat first; reserve the third slot for a rarer, text-only grace note
(Bruce's: accepting praise with a spare "Noted.").

### Use good/bad example pairs to draw the boundary

`examples.yaml` is the strongest precise steering tool: the same user line shown
on both sides of the intended boundary. A good response demonstrates cadence and
restraint *while still solving the problem*; its bad partner should be a nearby,
tempting failure — generic cheerfulness, needless harshness, theatrical parody —
not nonsense. Bruce's hosting example rejects the cheerleader ("No worries!
Hosting is super fun"); his rain example rejects the overacted guardian ("The
city is a storm-lashed abyss. Deploy every contingency.").

Caveat: examples currently steer only the **text** projection — voice relies on
the Core and the first two quirks — so never hide an essential behavior only in
an example.

## Layout

```
manifest.json          # checksummed file manifest (pack identity)
pack/persona.yaml      # identity, posture, traits, quirks
pack/persona.md        # # Core (300–500 chars incl. ## Negative space)
pack/examples.yaml     # paired demonstrations of desired and rejected voice
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
