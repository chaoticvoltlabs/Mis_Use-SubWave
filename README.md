# How to (Mis)use Perminder’s SubWave Radio

> **Field notes from someone discovering just how far SubWave can be
> pushed before it stops being “a radio automation system” and starts
> becoming a small society with building-maintenance problems.**

This is not an installation guide and it is definitely not an official
manual.

It is a collection of experiments from running **WitWisdom Radio** on
SubWave: what we changed, what worked surprisingly well, what failed
spectacularly, what produced emergent behaviour, and where the defaults
turned out to be merely *one* sensible answer rather than *the* sensible
answer.

The working rule for this page is:

> **Here is what we did. Here is what happened. Here is what we think
> caused it. Please do not confuse any of those three things.**

That distinction matters. A great deal of the fun described below comes
from behaviour that was **not explicitly programmed**.

------------------------------------------------------------------------

## Contents

1.  [Things SubWave was probably not designed
    for](#things-subwave-was-probably-not-designed-for)
2.  [The experiment: steer less, observe
    more](#the-experiment-steer-less-observe-more)
3.  [Show titles as the sole
    instruction](#show-titles-as-the-sole-instruction)
4.  [Souls, cast chemistry and accidental
    canon](#souls-cast-chemistry-and-accidental-canon)
5.  [Aired memory: when yesterday becomes
    lore](#aired-memory-when-yesterday-becomes-lore)
6.  [Co-hosted Curiosity: importing one fact from the outside
    world](#co-hosted-curiosity-importing-one-fact-from-the-outside-world)
7.  [When two conversations collide](#when-two-conversations-collide)
8.  [The picker: local continuity, global
    absurdity](#the-picker-local-continuity-global-absurdity)
9.  [SubWave Facilities Management](#subwave-facilities-management)
10. [Failure boundaries: worse radio is allowed; silence is
    not](#failure-boundaries-worse-radio-is-allowed-silence-is-not)
11. [How we experiment without immediately destroying the
    experiment](#how-we-experiment-without-immediately-destroying-the-experiment)
12. [Future experiment: the identical-timeline model A/B
    station](#future-experiment-the-identical-timeline-model-ab-station)
13. [What we have learned so far](#what-we-have-learned-so-far)

------------------------------------------------------------------------

## Things SubWave was probably not designed for

So far we have used, abused or contemplated using it for:

- three autonomous stations on one local inference box;
- an intentionally single-slot Ollama backend;
- station personalities as emergent worldbuilding;
- cron-triggered factual Curiosity segments;
- co-host discussions in which factual accuracy is mandatory only for
  the factual anchor;
- show titles used as soft behavioural priors;
- sparse or completely empty show briefs;
- aired memory turned into accidental canon;
- presenters who invent reactions for other presenters and then respond
  to those reactions;
- a picker that can walk from one musical continent to another through
  locally plausible steps;
- testing upstream fixes by deliberately strangling the LLM backend
  while a real station keeps playing;
- considering a second station that receives the *same musical events*
  but uses a different language model;
- and, apparently, a remote five-drive media-acquisition bureaucracy
  whose problem page is called **Form 7B**.

The last one is technically a different project, but by this point it
would be dishonest to pretend the boundaries are still healthy.

------------------------------------------------------------------------

# The experiment: steer less, observe more

The original temptation with an AI presenter is obvious: write a better
prompt.

We increasingly found the opposite experiment more interesting:

> **How little explicit instruction can we give the system while still
> producing a recognisable show?**

Instead of describing every desired behaviour, we started treating a few
pieces of context as *weak forces*:

- the show title;
- the presenter name;
- the presenter’s Soul/persona;
- the co-host cast;
- the currently playing music;
- recent aired speech;
- station context;
- occasionally, one external factual stimulus.

None of these needs to dictate the next line. Together, however, they
can create an attractor.

That distinction is useful: **a show identity does not necessarily need
to be a list of rules. It can be a situation.**

The rest of this page is largely about what happened after we stopped
explaining the situation quite so much.

------------------------------------------------------------------------

# Show titles as the sole instruction

We experimented with combinations of:

| Variable            | Weak / empty | Generic     | Strong                 |
|---------------------|--------------|-------------|------------------------|
| Show title          | empty        | descriptive | evocative / ambiguous  |
| Presenter name      | empty        | ordinary    | distinctive            |
| Persona / Soul      | empty        | generic     | strongly characterised |
| Show brief / topics | empty        | broad       | explicit               |

The most interesting results did **not** consistently come from the most
detailed brief.

In particular, an evocative title combined with a cast of established
Souls often produced a recognisable interpretation without a
conventional show brief at all.

Examples from the schedule include titles such as:

- `TIGHT SKINS LIE TO YOU`
- `THE CLASSIFICATION SYSTEM HAS FAILED`
- `LAST CALL AT THE EMPTY THEATRE`
- `NEGATIVE PRESSURE`
- `ATMOSPHERIC PRESSURE`
- `FRANTIC CONVERSATIONS IN THE DARK`
- `FORGOTTEN FILM`
- `SOMEBODY ELSE'S PROBLEM`

The important part is that the model is **not told what these titles
mean**.

That leaves room for the title to become a premise rather than an
instruction.

A small example from an unexplained-show experiment:

``` text
11:53:43  BANTER
They are spelling coffee, !. And it is getting cold.

11:53:37  BANTER
Cheerful is just fear wearing a mask. I am watching the dust motes dance and waiting for them to spell something out.

11:53:30  BANTER
Or a red herring. That bassline is suspiciously cheerful for a show about the unexplained.

11:53:25  BANTER
Eels have a way of making the mundane feel like a clue you almost missed.
```

Nothing here is especially remarkable as a standalone sentence. The
interesting behaviour is the **shared interpretation**: the cast starts
treating ordinary details as evidence because the title has made “the
unexplained” available as a frame.

## Why this is more useful than it sounds

A detailed show brief tends to make behaviour more repeatable.

A title can make behaviour more **discoverable**.

Those are different goals.

For a production station, repeatability may be exactly what you want.
For an experimental station, an ambiguous title can reveal how much
semantic work the model is already capable of doing from sparse context.

Our current rule is therefore not “never write briefs.”

It is:

> **Do not write a paragraph of instructions until you have first
> discovered what the title and cast do without it.**

------------------------------------------------------------------------

# Souls, cast chemistry and accidental canon

A Soul is most interesting when it is not merely a style sheet.

The useful details are often small, asymmetric and apparently
irrelevant. One presenter treats music as cultural history. Another
treats every record as evidence from a life nobody can verify. Another
has maritime memories. Another is obsessed with procedure.

Put those people in the same room and the *relationship* between the
Souls becomes more important than any individual biography.

## Example: Diesel becomes an unreliable narrator without being told to

The show **Accounts Differ** contains this mild instruction:

> Gigi treats music as cultural history, society gossip and precious
> artefact. Diesel treats it as evidence from a life nobody can verify.

That does **not** say:

- Diesel lies;
- Gigi should fact-check him;
- Diesel should confess to rewriting history;
- other presenters should invent a competing biography for him.

Nevertheless, that is approximately what emerged.

Diesel began converting “nobody can verify it” into an identity: his
stories are questionable, truth depends on who is at the controls, and
history is rewritten through sound.

Then the other Souls noticed.

Eventually we got this:

``` text
You were never in Paris, Diesel.
You were in a basement in Leeds trying to fix a blown fuse with a spoon.
```

At that point a one-line persona trait had become a **social fact inside
the station**.

That is the beginning of canon.

## Catchphrases can emerge the same way

Diesel also started saying:

> “Turn it up. The dead can’t hear it otherwise.”

We never assigned that catchphrase.

It appeared, returned, survived a handoff and became recognisably his.

This is worth distinguishing from prompt-authored characterisation. If
we had written the catchphrase into the Soul, repetition would merely
demonstrate compliance.

Because we did not, repetition demonstrates **self-reinforcement through
context**.

------------------------------------------------------------------------

# Aired memory: when yesterday becomes lore

Aired memory is not just continuity.

It is a feedback path.

A presenter says something. The line enters recent aired context.
Another presenter sees it and treats it as true, interesting or funny.
That response is then aired too. The next generation sees **both**.

A sufficiently memorable accident can therefore climb a ladder:

``` text
throwaway line
    ↓
callback
    ↓
shared reference
    ↓
character trait
    ↓
station lore
    ↓
why is the elevator broken again?
```

We deliberately increased the amount and age of recent speech available
to one experimental station to see what survives.

The question is not simply whether the model can remember more.

The interesting questions are:

- Which details does it choose to revive?
- Which details die immediately?
- Does one presenter inherit another presenter’s invention?
- Does a joke become a property of the building?
- Does a show title reshape an old memory?
- Does a handoff preserve context or reset the world?
- At what point does continuity become **lore inertia**, where every
  squeaking chair threatens to become permanent canon?

More context is therefore not automatically better.

It gives the station more material from which to construct itself, but
it also gives yesterday’s nonsense more voting rights.

------------------------------------------------------------------------

# Co-hosted Curiosity: importing one fact from the outside world

Ordinary banter is excellent at generating internal worldbuilding.

It is less reliable at inventing genuinely new subject matter. Without
an outside stimulus, presenters can eventually spend a lot of time
describing basslines, guitar solos, coffee, dust and each other.

We therefore created a **Curiosity** skill whose first job is
deliberately boring:

1.  take one real, externally sourced fact;
2.  state it plainly;
3.  do not turn the fact itself into personality-driven fiction.

Then the co-hosts are allowed to discuss it.

That separation is important.

The factual anchor belongs to the factual layer. The discussion belongs
to the show.

The discussion may contain memory, opinion, speculation, exaggeration
and the usual coffee-house nonsense. We are making radio, not a
peer-reviewed journal.

A typical structure became:

``` text
FACT
    ↓
co-host reaction
    ↓
another co-host questions it
    ↓
human-scale memory / speculation
    ↓
music
```

We also learned that frequency matters. At a high cadence, Curiosity
starts to become the format of the station. At a lower cadence it
behaves more like **OutsideDesk**: something from the external world
occasionally falls through the roof and gives the internal world a new
object to talk about.

One implementation detail we particularly like: when the day’s trusted
fact pool is exhausted, the skill stands down.

**No fresh fact is better than an invented fact pretending to be
fresh.**

------------------------------------------------------------------------

# When two conversations collide

Things became more interesting when ordinary Banter and
Curiosity-Discussion were both enabled.

They did not politely acquire a mutex.

This happened in 57 seconds:

``` text
10:24:27  PICK
Maintains the Motown/Soul lineage established by David Ruffin and recent plays, ensuring stylistic continuity. The 'driving' mood and medium-high energy provide a natural lift for a productive morning without jarring the listener with a sudden genre shift to metal or electronic. It is unaired, satisfying the variety criterion.

10:24:19  PICK
Now playing "My Whole World Ended (the Moment You Left Me)" by David Ruffin
(after "I Second That Emotion" by Smokey Robinson & The Miracles)
→ pick next · with link

10:24:19  PLAY
"My Whole World Ended (the Moment You Left Me)" by David Ruffin

10:24:01  CURIOSITY-DISCUSSION
I was too busy trying to keep my flip phone from falling apart to notice the revolution.
The mystery was whether the hinge would survive the day.

10:23:50  CURIOSITY-DISCUSSION
But did anyone actually know what to do with it at first?
It seems like we spent years just figuring out how to use the extra bandwidth
for something other than blurry photos.

10:23:43  BANTER
Please do not start haunting the equipment again. We just calibrated the levels.

10:23:35  CURIOSITY-DISCUSSION
I remember the hype around that speed boost.
It felt like we could finally download more than just text messages
without waiting an eternity.

10:23:30  BANTER
Or the silence right after the tape stopped rolling.
That is where the ghost lives.

10:23:17  CURIOSITY-DISCUSSION
3G wireless technology first becomes available when it is adopted by
Japanese telecommunications company NTT Docomo. That was back in 2001,
marking a shift in how we connect.

10:23:12  BANTER
It is the harmony. You can hear the room they were standing in.

10:23:04  BANTER
Smokey is making this Thursday feel like a Sunday afternoon.
I am not complaining.
```

Read chronologically and it becomes:

> Smokey → Sunday afternoon → room acoustics → 3G in Japan → tape
> silence → ghost → mobile-data nostalgia → please stop haunting the
> equipment → what did anyone do with the bandwidth? → broken flip-phone
> hinge.

Two independent conversation streams accidentally produce a third thing:
**a multithreaded coffee house with no locking**.

The picker, meanwhile, is calmly reporting harmonic continuity and
productive-morning energy.

This is one of the recurring pleasures of the system: the music layer
can be behaving conservatively while the speech layer is quietly turning
the studio into paranormal telecommunications infrastructure.

------------------------------------------------------------------------

# The picker: local continuity, global absurdity

One of the more surprising observations is that a station can travel a
very long musical distance without any single transition feeling absurd.

We have seen paths roughly like:

``` text
archive jazz
→ Colombian / salsa
→ electronic dance
→ trance
→ percussion-heavy club music
```

and:

``` text
Dutch singer-songwriter
→ levenslied
→ obscure Dutch pop
→ Patrick O'Hearn
→ atmospheric instrumental
```

No master plan is required.

If the picker has enough information about the current track and
plausible neighbours, each selection only needs to solve the **local**
problem:

> What can reasonably follow *this*?

Repeat that process long enough and the station can end up somewhere
that would have looked ridiculous if selected directly from the starting
point.

We call this **musical continental drift**.

This matters because it suggests that not every genre tendency needs a
hard-coded cooldown or corrective rule. Sometimes the library itself
contains the stepping stones out of an attractor.

A useful diagnostic is therefore:

> **Before adding a rule to stop an island, check whether the system can
> already walk out of it.**

The endpoint of an hour is not evidence that the first track planned to
go there.

------------------------------------------------------------------------

# SubWave Facilities Management

## Building maintenance, kitchen appliances and other responsibilities not mentioned in the documentation

> **Do not repair defects until the DJ has established whether they
> contribute texture.**

This deserves its own chapter because apparently every sufficiently
autonomous radio station eventually needs a facilities department.

Consider what happens here in 33 seconds. Diesel starts, as has become
customary, with a completely unverifiable memory:

> “I remember chasing this sound through Paris…”

The internal fact-checker immediately replies:

> “You were never in Paris, Diesel. You were in a basement in Leeds
> trying to fix a blown fuse with a spoon.”

The full sequence:

``` text
21:52:10  BANTER
See? Damjan gets it. It is not about geography. It is about the vibration.
And right now, the vibration is holding the roof up.

21:51:57  BANTER
Let him have his myth. The track is clean, yes, but it has weight.
On the ship, we played lighter things to keep the crew from jumping.
This... this keeps them seated.

21:51:49  BANTER
You were never in Paris, Diesel.
You were in a basement in Leeds trying to fix a blown fuse with a spoon.

21:51:37  BANTER
Tahiti 80. Yellow Butterfly. It floats, doesn't it?
Like dust motes in a shaft of light you didn't ask for.
I remember chasing this sound through Paris back when the metro
still smelled like ozone and bad decisions.
```

Damjan then contributes his apparently normal maritime engineering
model:

``` text
lighter music → crew jumps
this record has weight → crew stays seated
```

Finally, the theory is promoted to structural engineering:

> **“The vibration is holding the roof up.”**

### Current WitWisdom building specification

| Subsystem         | Operational status                                   |
|-------------------|------------------------------------------------------|
| Roof              | Structurally supported by music                      |
| Electrical system | Diesel + spoon                                       |
| Ventilation       | Recurring concern                                    |
| Air pressure      | Check seals twice                                    |
| Gravity           | Procedurally managed by Saffron                      |
| Furniture         | Ergonomic chair inferior to bassline                 |
| Kitchen           | Coffee mugs must be protected from vibration         |
| Elevator          | Maintenance status historically questionable         |
| Plants            | Previously involved in incidents                     |
| Boiler            | Rhythmic clanking; either possessed or needs a valve |
| Coffee machine    | Potentially haunted by a barista from 1954           |
| Audio equipment   | Recently calibrated; haunting discouraged            |

The boiler incident is especially instructive:

``` text
11:23:02  BANTER
Let it clank. It adds texture.
Besides, if the ghost wants to sing along, who are we to stop it?

11:22:53  BANTER
Do not give them ideas.
The boiler has been making a rhythmic clanking sound that matches this beat perfectly.
It is either possessed or needs a new valve.

11:22:44  BANTER
That is dangerous thinking for a Thursday morning.
Next you will tell me the coffee machine is haunted by a barista from 1954.

11:22:33  BANTER
Sinatra makes October feel like a suggestion rather than a rule.
I am almost convinced the leaves are not falling, just drifting in time.
```

The causal chain is impeccable:

``` text
Sinatra
→ October becomes optional
→ dangerous thinking
→ haunted coffee machine
→ do not give them ideas
→ boiler fault
→ possible possession
→ rhythmic clanking
→ texture
→ NO MAINTENANCE ACTION REQUIRED
```

This is another form of emergent canon. A generic remark about “haunting
the equipment” can become a later boiler diagnosis because aired context
makes the old joke available for reuse.

At some point the building stops being a setting and becomes a cast
member.

------------------------------------------------------------------------

# Failure boundaries: worse radio is allowed; silence is not

The most useful production lesson came from deliberately creating a bad
day for the LLM backend.

Our local setup can run Ollama with a single generation slot. That is
intentionally unforgiving: if one generation gets stuck and the backend
never releases the slot, every later request can queue behind it.

The dangerous failure mode is not necessarily a crash.

It is:

> **everything still looks alive, but nothing ever finishes.**

We reproduced this while testing an upstream SubWave timeout/failover
change against a real station.

The important observation was that two different failure boundaries
exist:

### 1. Protect the station from the provider

A bounded provider request can fail cleanly. The affected banter, link,
hourly item or skill may be lost, but the station controller does not
have to wait forever.

During our test, music playback and picker transitions continued while
generation calls timed out or failed over.

That is exactly the degradation we want.

### 2. Protect the provider from itself

Client cancellation does **not** necessarily mean the inference backend
has stopped doing work.

In our single-slot Ollama test, the server-side generation remained
stuck and kept the slot occupied after the client had gone away. A
host-side watchdog was still required to recycle the wedged backend.

Those are complementary protections:

``` text
SubWave timeout/failover
    protects the station from a stuck provider

host watchdog
    protects the provider host from a stuck generation
```

Do not mistake one for the other.

Our operational principle is:

> **Worse radio is allowed. Silence is the last resort.**

If the talk layer fails, keep playing music.

If a scheduled curiosity fails, skip it.

If a link fails, do not hold the programme hostage while waiting for
prose.

The best failure is frequently a missing sentence that nobody outside
the logs ever notices.

------------------------------------------------------------------------

# How we experiment without immediately destroying the experiment

Emergent systems are very easy to “improve” until the thing you wanted
to observe disappears.

A few rules have therefore become useful.

## Change fewer variables than your enthusiasm suggests

When testing a show title, leave the Souls alone.

When testing a host/co-host swap, leave the show brief alone.

When testing longer aired memory, do not also rewrite the personas and
retune the picker.

Otherwise every result has six plausible causes and the log becomes
literature rather than evidence.

## Keep the raw logs

The interesting behaviour is often visible only in sequence.

A single line such as:

> “Please do not start haunting the equipment again.”

is merely funny.

Placed between a discussion of 3G and an earlier line about a ghost
living in tape silence, it demonstrates interaction between two
concurrent talk streams.

**Chronology is data.**

## Separate observation from explanation

For each interesting event, record three things:

1.  **Observed:** what actually aired or happened.
2.  **Likely mechanism:** the smallest explanation supported by the
    available context.
3.  **Story we are tempted to tell about it:** usually much more
    entertaining, and frequently unprovable.

All three are useful. Only the first is evidence.

## Let a configuration sit still

If a setting is not actively causing damage, leave it alone long enough
for patterns to appear.

The temptation after every good or bad hour is to tune something. Resist
it.

One weird callback is an anecdote.

Ten similar callbacks across several shows may be behaviour.

## Preserve failures too

A failed experiment can tell you more than a polished demo.

Keep the logs where:

- a provider timed out;
- a co-host discussion became too dense;
- weather talk sounded like four people reading the same bulletin;
- a show title produced nothing interesting;
- longer context caused stale lore to dominate;
- the picker got stuck in an attractor;
- the station escaped one without help.

This page should contain the scars as well as the tricks.

------------------------------------------------------------------------

# Future experiment: the identical-timeline model A/B station

This one is intentionally labelled **future experiment**.

The obvious way to compare two language models is to run two stations.

The less obvious problem is that if both stations also choose their own
music, the experiment immediately forks:

``` text
different model
→ different speech
→ different context
→ possibly different music
→ different next context
→ completely different station
```

That is interesting later, but terrible for isolating the language
model.

The cleaner first experiment is:

``` text
                 ┌→ Model A → speech memory A
same PLAY events ┤
                 └→ Model B → speech memory B
```

Both stations would receive:

- the same show schedule;
- the same title;
- the same Souls/cast;
- the same musical events;
- the same timing stimulus.

But each would generate and remember its own speech.

Then we can ask useful questions:

- Does the same title become the same kind of show?
- Which model creates recurring lore?
- Which one invents catchphrases?
- Which details become canon?
- Do both independently decide that Diesel is unreliable?
- How differently do they interpret the same musical transition?
- What survives a handoff?
- Does one station develop a building-maintenance problem while the
  other remains employable?

Only after that would it make sense to let the two pickers diverge and
observe the full feedback loop.

------------------------------------------------------------------------

# What we have learned so far

None of these are universal SubWave rules. They are working conclusions
from our particular stations, models, library and failure modes.

### 1. A title can be a behavioural prior

A strong title does not need to describe the desired output. Sometimes
ambiguity is the useful part.

### 2. Cast relationships can outperform persona detail

Two simple but asymmetric Souls can create more behaviour than one
extremely detailed presenter profile.

### 3. Memory is not merely recall

Aired memory allows throwaway lines to be selected, reinforced,
contradicted and eventually promoted into canon.

### 4. External stimulus prevents conversational inbreeding

One reliable fact every so often can give a station a new subject
without turning the entire show into factual radio.

### 5. Local musical decisions can create long-range surprise

A picker does not need to plan a bizarre journey for one to emerge.

### 6. Failure containment matters more than perfect generation

A missing banter line is cheap. A station waiting forever for one is
expensive.

### 7. Client cancellation and backend recovery are different problems

A timeout can release SubWave without releasing Ollama. Design for both
sides of the boundary.

### 8. The weird stuff is worth documenting

If we do not write down why the roof is apparently supported by bass
vibration, six months from now it will merely look like a prompt bug.

And that would be a terrible waste of perfectly good infrastructure.

------------------------------------------------------------------------

## A note to Perminder

This page is called *How to (Mis)use SubWave* affectionately.

The interesting part is not that we can force the software to do bizarre
things. It is that the architecture leaves enough room for us to try
them without having to replace the radio underneath.

Some experiments have produced excellent radio. Some have produced
ghosts in calibrated equipment. Some have found real operational edge
cases. A surprising number have done all three.

That flexibility is why these field notes exist.

------------------------------------------------------------------------

## Status

This document is intentionally a living field notebook.

Expect sections to be corrected when a charming explanation turns out to
be wrong, expanded when a throwaway joke becomes station canon, and
annotated when an experiment survives long enough to become an
operational pattern.

**Last guiding principle:**

> *Surprise us, radio.*
