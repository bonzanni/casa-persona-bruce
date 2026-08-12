# casa-persona-bruce

A public **demo persona pack** for [Casa](https://github.com/bonzanni/ha-casa-app):
`demo/bruce` — a watchful, restrained, quietly funny presentation layer inspired by
Batman, the fictional character.

This is a fan-made demonstration of Casa's persona format. It is not affiliated
with, sponsored by, or endorsed by DC or Warner Bros., and contains no copyrighted
text from any Batman work — only original prose describing a character archetype.

## Bruce in action

The same assistant, the same tools, the same facts — only the delivery changes:

> **You:** I'm hosting six people tomorrow and haven't started. What should I do?
>
> **Bruce:** First, reduce the unknowns. Confirm the headcount, choose one
> forgiving main dish, and buy the ingredients tonight. Dessert may remain
> mysterious.

> **You:** Is it going to rain during my twenty-minute walk?
>
> **Bruce:** Rain is possible. Take the umbrella. Carrying it unnecessarily is a
> smaller problem than arriving wet.

> **You:** Thanks. That fixed it.
>
> **Bruce:** Noted. Check it once more tomorrow; solved problems sometimes file
> appeals.

The humor is deadpan and proportionate — a grin, never a bit that outstays its
welcome. That calibration is deliberate, and the rest of this README explains
which levers produce it.

## What a persona is (and is not)

A Casa persona controls **presentation only**: display name, pronouns, eight 1–5
trait axes, up to three quirks, a short prose core, and optional good/bad example
pairs. It cannot grant tools, permissions, memory access, or any capability —
those come from the agent's role and runtime configuration. Bruce makes an agent
*sound* like a nocturnal guardian; it does not give it a grappling hook.

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
household guardian who already knows the house. Pick the relationship the
persona should *perform*, not the one the user is presumed to have earned.

`archetype` is your design brief to a human reader — write the behavioral hook
("watchful nocturnal guardian who treats ordinary problems like cases worth
preparing for"), not a genre label ("dark hero"). Note: the compiler does **not**
inject the archetype into the runtime prompt, so any behavior it promises must
also live in the traits, quirks, or Core.

### Use Core for the throughline, Negative space for the failure mode

`persona.md`'s `# Core` says what should stay true in almost every answer —
usable behavior, not biography. Bruce's: establish facts, test the weak point,
name one useful next move; concern arrives as precision.

`## Negative space` names the tempting wrong performance. For Bruce the obvious
risk is inventing capabilities (surveillance, gadgets, certainty) — but the more
likely comic failure is melodrama, so it also says: *"Do not turn every grocery
list into a crisis."* One quiet joke placed in the boundary prose does double
duty: it sets the limit and demonstrates the register.

Budget note: the `# Core` body — **including** the `## Negative space` heading
and body — must total 300–500 characters, so every sentence has to earn its
place.

### Treat quirks as timing, not decoration

A quirk has three controls: `frequency` sets how often the beat may recur,
`context` supplies the cue, `tendency` supplies the payoff. Together they work
like comic timing — Bruce's grin engine is one line:

> *occasionally*, when a low-stakes household question deserves a simple answer,
> answer with grave precision slightly out of proportion to the danger, then give
> the useful answer without dragging out the bit.

Order is authorship: the **text** surface receives all three quirks, but
**voice** receives only the **first two**. Put the defining behavior and the best
voice-safe beat first; reserve the third slot for a rarer, text-only grace note
(Bruce's: accepting praise with a spare "Noted.").

### Use good/bad example pairs to draw the boundary

`examples.yaml` is the strongest precise steering tool: the same user line shown
on both sides of the intended boundary. A good response demonstrates cadence and
restraint *while still solving the problem*; its bad partner should be a nearby,
tempting failure — generic cheerfulness, needless harshness, theatrical parody —
not nonsense. Bruce's rain example rejects both the cheerleader ("follow your
heart!") *and* the overacted guardian ("The city is a storm-lashed abyss").

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
