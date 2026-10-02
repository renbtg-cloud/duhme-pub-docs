# Duhme — Reasoning Deeply About Us Humans. Without pretending we are simple, static, fully observed, internally transparent, or reducible to the last prompt

**Public Architecture Overview — v0088**

Duhme is a model-agnostic human-context reasoning system.

Its central problem is not producing fluent text. Powerful models already do that well. The harder problem is preserving enough structure around people, relationships, evidence, memory, uncertainty, contradiction, culture and time that fluent reasoning does not quietly turn into invented certainty.

Duhme treats human reality as a bounded epistemic domain: a world in which evidence has provenance, people change, memories are imperfect, relationships matter, interpretations compete, and apparently small events can become important much later.

A useful shorthand is:

> **The human already has meaning. Duhme does the boring work of making that meaning usable by AI.**

Duhme is not primarily a chatbot, prompt improver, sentiment classifier, psychological profiler, CRM, HR system, speech stack or foundation model. It is intended to sit underneath or beside systems that need durable, revisable reasoning about humans and the worlds around them.

---

## The architectural problems Duhme is built around

Human-context reasoning becomes difficult less because any single observation is complicated than because the surrounding epistemic structure is.

### Evidence is not truth

An email, message, recording, document, event, log entry or user statement is evidence. It is not automatically true.

A message saying:

> "Maria has already approved this."

establishes, at minimum, that someone made that claim. Whether Maria actually approved it is a separate question.

Duhme therefore keeps apart:

- source material;
- observations extracted from source material;
- claims made by actors or sources;
- hypotheses that explain patterns;
- findings supported by some body of evidence;
- contradictions and counterevidence;
- confidence, authority and provenance.

The distinctions sound obvious. They become surprisingly easy to lose once multiple models, documents, conversations and historical episodes are compressed into one answer.

### Evidence count is not evidence diversity

Ten people can repeat one rumor.

That is not ten independent confirmations.

Several reports may share a common origin, quote one another, descend from the same document, or reflect one coordinated narrative. Duhme therefore cares about evidence independence and shared origin, not just the number of matching statements.

The same distinction matters in the opposite direction. One unpopular claim may be unusually strong if it comes from direct observation, while twenty repetitions may be weak if they all trace back to one source.

### A false claim can still become causally important

Suppose the statement:

> "The CTO personally backs Alice."

is unverified.

If several managers nevertheless begin routing decisions through Alice, the statement may remain weak evidence of actual sponsorship while becoming strong evidence that people **believe** Alice is sponsored.

Truth strength and behavioral impact are different dimensions.

Human systems often react to perceived capability, perceived alliances, anticipated retaliation, expected approval, reputation and rumor before the underlying claim is verified.

### Humans contradict themselves

People change their minds. They speak differently to different audiences. They sincerely remember events differently. They rationalize. They conceal. They joke. They exaggerate. They obey roles they privately dislike. They can believe mutually uncomfortable things at once.

Duhme treats contradiction as information rather than corruption to normalize away.

A person saying one thing in public and another in private does not automatically prove deception. It may reflect audience adaptation, changed beliefs, role obligation, uncertainty, strategic behavior, social pressure, or deception. Several explanations may remain alive until evidence discriminates among them.

### Internal mechanisms are hypotheses, not mind-reading

Fear, shame, status threat, resentment, gratitude, attraction, loyalty, guilt, reciprocity, self-justification, face-saving, reactance and similar mechanisms can help explain human behavior.

They are not privileged hidden-state sensors.

The architecture allows such mechanisms to exist as competing hypotheses grounded in local evidence and broader human-science knowledge. It does not convert psychological plausibility into fact.

The same discipline applies to socially attractive explanations. Compassion, gratitude, trust, loyalty and moral courage are not promoted merely because they make a nicer story.

### The scene can be easier to infer than the person

Duhme follows a deliberately asymmetric principle:

> **Infer the scene aggressively; infer the person conservatively.**

It may be reasonable to conclude that a meeting became tense, that a proposal lost support, or that a faction temporarily aligned around an issue while remaining much more cautious about saying that a specific person is "hostile," "disloyal," "insecure" or permanently motivated by status.

Situational interpretation can be useful without hardening temporary behavior into identity.

### People do not exist as isolated `user_id` records

The meaning of an event often depends on relationship history.

"He did that thing again" may be understandable only because earlier episodes establish who "he" usually denotes in this context and what "that thing" probably refers to.

A blunt refusal can mean something different between strangers, old friends, rivals, spouses, colleagues or a supplier and customer who have negotiated for ten years.

Duhme therefore treats people, references, relationships, episodes and histories as first-class reasoning material rather than decorating isolated user records with a few profile fields.

### Identity itself is revisable

Names, handles, email addresses, roles and references do not always map cleanly to one human.

Two records may later prove to be the same person. One record may have incorrectly merged two people. A nickname may identify different actors in different contexts.

Identity resolution is therefore not treated as an irreversible import-time decision. Merge, split and correction remain possible without rewriting history as if the mistake never happened.

### Human memory and machine archives are different things

A seven-year-old email can exist in an archive even though nobody currently remembers it.

A person can vividly remember an event whose original source has disappeared.

An old insult can remain salient to one participant and utterly forgotten by another.

A newly rediscovered document can change Duhme's historical evidence without retroactively changing what any human knew, noticed or remembered at the time.

This distinction matters for conflict, trust, negotiation, reputation, gratitude and nearly every long-running relationship.

### Missing evidence is not an empty cell

Duhme distinguishes at least three cases:

1. nothing was observed;
2. there is evidence that nothing happened;
3. an absence is itself unusual relative to a known baseline.

A missing meeting recording does not prove nothing important occurred.

No email or Teams traffic does not prove there was no phone call, private message or face-to-face conversation.

At the same time, absence can become evidence when the baseline is strong enough. If a reviewer participates in every relevant decision for two years and then unexpectedly disappears from one high-stakes decision trail, that deviation may matter.

### The present and the past cannot be mixed casually

Human reasoning is temporal.

A conclusion that was defensible on Monday may become stale on Friday. A later correction can invalidate a current interpretation without erasing the fact that the earlier interpretation existed. Historical reconstruction uses what belonged to that historical frame rather than silently importing facts learned much later.

Duhme therefore treats "what appears true now" and "what could reasonably have been concluded then" as different questions.

This is especially important in live interactions and post-event analysis. Hindsight does not rewrite what was knowable at the time.

### Corrections have consequences

If a user corrects an identity, relationship, event interpretation or factual claim, the correction changes the reasoning graph rather than living as a cosmetic note beside it.

The correction can affect downstream hypotheses, findings, summaries and future retrieval.

At the same time, correction is not historical erasure. Duhme preserves that an earlier interpretation existed, when appropriate, while changing what remains usable as current truth.

### Deletion changes what can still be known

Privacy deletion is not merely a storage operation.

If a conclusion materially depended on evidence that is no longer available for use, the epistemic state changes. The system cannot continue presenting the old conclusion as if the deleted material had never been part of its support.

Deletion can therefore create narrower conclusions, explicit missing coverage, reduced confidence, or unavailability where a claim cannot be responsibly reconstructed from what remains.

### Cultural knowledge is scoped, not universal

Culture is not a nationality lookup table.

Meaning can vary by geography, language, profession, class, subculture, age, historical period, relationship, domain and observer group.

Different groups can interpret the same symbol in opposite ways. An expert source can be prestigious but irrelevant to the local population being discussed. A phrase that is rude between strangers can be affectionate between old friends.

Duhme therefore treats cultural evidence as scoped and disputable. Population-level patterns can generate candidate interpretations; they do not replace person-specific evidence.

### Language competence is not human competence

Messy language can coexist with deep technical, professional or social competence.

People mix languages, swear, omit subjects, speak in fragments, use private euphemisms, produce damaged transcripts and shift register by audience.

Duhme separates linguistic polish from inferred competence.

Sanitizing rough language too early can destroy evidence about humor, hierarchy, affiliation, anger, intimacy or local meaning. Source expression therefore remains distinct from later audience-safe rendering.

### Hard application state and fuzzy human reasoning are different kinds of truth

A CRM can know:

```text
approval_status = PENDING
```

Duhme may reason:

```text
the approver appears increasingly likely to reject unless the framing changes
```

Those statements belong to different layers.

The hypothesis does not silently mutate the deterministic application state. Conversely, deterministic state does not block reasoning about the human dynamics surrounding it.

### Attention is a separate problem from reasoning

A system may notice something important without interrupting anyone.

The same finding can be:

- stored only;
- included in a later summary;
- shown on a dashboard;
- surfaced at the next natural pause;
- escalated immediately.

Support strength, consequence, urgency, reversibility and audience all matter.

Reasoning relevance and delivery urgency are intentionally separate.

### Live reasoning creates hindsight traps

During a negotiation, Duhme may hold a medium-confidence concern that later turns out to have been correct.

If the configured interruption threshold was higher, no warning may have been emitted.

When the feared event later occurs, the architecture preserves:

- what evidence existed beforehand;
- which hypotheses existed beforehand;
- how strong they were;
- what counterevidence remained;
- why the system did or did not surface them.

The later outcome is new evidence. It is not permission to rewrite the earlier state into "the answer was obvious all along."

### Duhme can become part of the system it observes

If Duhme advises a user to say something, warns a manager, reframes a negotiation, or mediates between two people, subsequent behavior is no longer independent evidence from an untouched environment.

The intervention may have changed the outcome.

This creates a reflexive reasoning problem: Duhme reasons about its own influence instead of treating the changed world as independent confirmation of its prior belief.

### Strong models remain replaceable components

Duhme uses powerful language/reasoning models where fuzzy semantic work is useful, but canonical memory and reasoning structure belong to Duhme rather than to a provider conversation.

Different models can be useful for different workloads. A model can improve, regress, disappear, become too expensive, or behave differently under the same API shape.

The architecture therefore treats external models as replaceable reasoning components rather than as the durable owner of the human world.

---

# Six use cases that stress the same architecture

The following scenarios are deliberately different. The point is not to create six separate products. The point is to show whether one underlying human-context architecture survives very different kinds of human reality.

---

## UC-01 — Human expression, personal context and cross-cultural mediation

The problem is not simply translation.

A person's social act can disappear even when every word is translated correctly.

Two participants may differ in language, register, hierarchy expectations, humor, taboo, directness, negotiation conventions, professional culture, regional assumptions and relationship history. The same sentence can therefore be lexically accurate and socially wrong.

Duhme treats mediation as a chain in which the source expression remains preserved while several interpretations can coexist:

```text
source expression
    ↓
literal / semantic meaning
    ↓
relationship + history + personal lexicon
    ↓
scoped cultural evidence
    ↓
candidate pragmatic / social acts
    ↓
target rendering or explanation
    ↓
recipient reaction
    ↓
new evidence for later reasoning
```

### Messy language is still meaningful language

A person may say:

> "yeah he did that shit again, same thing from before deploy"

The useful questions are not "Is this grammatical?" or "Should this be rewritten into polished business English?"

The useful questions are:

- Who is "he" likely to refer to in this relationship/project context?
- What recurring episode does "that shit" point back to?
- Does "again" activate a known pattern?
- Is the profanity hostile, humorous, affiliative or simply habitual?
- Would the same wording be appropriate for the intended audience?

Long-lived context can make fragmentary language precise without pretending ambiguity has disappeared.

### Source expression survives transformation

Translation, normalization, sanitization and audience adaptation are derivative representations.

They do not replace the original.

A joke, insult, honorific, code-switch, rough phrase or silence marker may carry information that vanishes if normalized too early.

This matters because later evidence may change how the original expression is interpreted.

### Cultural mediation is about social acts

A literal translation approximates:

```text
words in language A
    →
words in language B
```

Cross-cultural mediation has to consider more:

```text
semantic content
+ speech act
+ relationship
+ hierarchy / status relation
+ emotional force
+ humor
+ taboo level
+ local idiom
+ audience
+ cultural references
+ intended social effect
+ uncertainty
    →
rendering / explanation for the target participant
```

A commercially firm refusal, for example, can carry no personal offense, mild irritation, deliberate status signaling, face-saving, genuine humiliation or strategic theater. The wording alone may not decide which one is intended.

### Population evidence cannot overrule the relationship

A cultural prior can suggest candidate interpretations.

A well-established relationship can outweigh it.

A phrase considered rude between strangers may be affectionate between long-time collaborators. A direct refusal may be ordinary inside one engineering team. Two people may develop a private vocabulary that no population-level cultural rule captures.

Duhme therefore combines scoped cultural evidence with relationship history, personal lexicon, previous misunderstandings, prior confirmed meanings and audience expectations.

### Consequential ambiguity can be surfaced instead of guessed away

Suppose an artisan rejects a buyer's counteroffer.

There are at least two materially different possibilities:

```text
A. "I am holding the price; no offense intended."

B. "I am holding the price, and I want them to understand
   that the counteroffer offended me."
```

The commercial position is the same. The social act is not.

When the distinction matters, the system can make the ambiguity explicit rather than burying it under fluent prose.

### Preserve + bridge

Sometimes the right output is not to replace a cultural object but to preserve it and explain it.

Possible forms include:

- literal rendering plus compact gloss;
- original phrase plus target-culture explanation;
- closest social equivalent;
- pragmatic rendering plus preserved source;
- a combination appropriate to the relationship.

The goal is not to flatten both parties into generic international corporate language.

It is to help the intended meaning survive the crossing.

### Private context helps interpretation without becoming disclosure

Suppose Duhme knows privately that a speaker is under unusual pressure to prove competence.

That context may help avoid misreading emphatic language as arrogance.

It does **not** automatically authorize telling the recipient:

> "They sound aggressive because they are insecure."

Interpretive usefulness and disclosure permission are separate.

### Recipient reaction becomes evidence, not verdict

Suppose the system expects a rendering to communicate firm disagreement without contempt, but the recipient reacts as if personally insulted.

Several things may now deserve re-examination:

- the inferred intent;
- the chosen rendering;
- the relationship model;
- the cultural evidence;
- the model of the recipient;
- whether the reaction itself was strategic or sincere.

The correct conclusion is not automatically "the recipient misunderstood," nor automatically "the cultural model was wrong."

The reaction is new evidence.

### Repeated mediation can create shared culture

Cross-cultural relationships are not static.

A phrase that needs explanation in the first interaction may become shared vocabulary by the fifth. The participants can gradually learn one another's humor, status cues and expectations.

The mediation layer can therefore become lighter as the relationship itself becomes richer.

The aim is not permanent dependency on translation. It is progressively better mutual legibility without erasing either person's style.

---

## UC-02 — Longitudinal organizations, relationships and unofficial power

Formal organization charts describe only part of an organization.

Actual influence can depend on trust, sponsorship, gatekeeping, reputation, scarce knowledge, procedural control, coalition behavior, personal history, obligation and perceived capability.

Duhme treats the unofficial organization as a changing graph rather than as a collection of personality labels.

### Formal title and practical leverage are different

A person with little formal authority may still be the one everyone checks before committing.

A nominal decision-maker may routinely defer to someone else.

A manager may control information rather than decisions. A senior engineer may carry disproportionate influence because nobody else understands a critical system. A customer contact may appear weak in the CRM but privately control access to the economic buyer.

Useful questions therefore include:

- Who can actually change an outcome?
- Who can delay it?
- Who is consulted before a decision becomes real?
- Which relationships matter only in certain domains?
- Which apparent coalitions persist across episodes?
- Which ones are temporary?

### Socially ugly communication can mean several things

A team may use insults, profanity and mean jokes constantly.

A shallow sentiment classifier can label the team toxic.

The same evidence may instead fit:

- ritualized teasing among close colleagues;
- genuine hostility;
- strong in-group cohesion;
- exclusion of one outsider;
- cohesion partly built around hostility to another person;
- different meanings depending on audience and episode.

Duhme preserves the competing explanations until local evidence discriminates among them.

### Behavioral search is episode search, not keyword search

Consider:

> "Find the times Roberto got defensive when deadlines slipped."

The relevant episodes may not contain the word "defensive."

The pattern may involve abrupt topic changes, public blame, unusual escalation, refusal to acknowledge an earlier commitment, or other behavior that only becomes comparable in context.

A useful answer therefore distinguishes:

- direct evidence;
- claims by other actors;
- inferred similarity;
- repeated reports with a shared origin;
- missing channels;
- why each episode matched;
- prior corrections or rejected interpretations.

The result remains a revisable behavioral pattern, not a permanent personality diagnosis.

### Several explanatory branches can coexist

A user may strongly believe:

> "Alice is trying to push Roberto out."

Duhme need not either obediently adopt the premise or stubbornly reject the entire line of inquiry.

It can preserve one branch that explores the user's premise deeply while maintaining another branch that does not assume it.

Different branches can retrieve different evidence, produce different predictions, and later be compared against outcomes.

This allows ambitious exploration without turning one worldview into canonical truth.

### Apparently minor events can become explosive later

A technically ordinary email in January may matter little at the time.

Nine months later, during a promotion rivalry, one participant may still remember it as a public challenge.

A new message saying:

> "as previously discussed"

to a broad audience can reactivate that memory and become professionally costly despite containing no obviously hostile language.

The risk mechanism depends on human memory, relationship history and current stakes rather than on textual toxicity.

The reverse also occurs. Remembered praise, costly protection, successful reciprocity or a previous act of trust can make a later request safer than its literal wording suggests.

### Positive obligations matter too

Suppose a senior engineer publicly takes responsibility for an outage and materially protects a junior colleague.

Months later, the junior quietly warns the senior engineer about a hostile review, refuses to amplify an attack, shares useful information and takes some career risk defending one of the senior engineer's decisions.

Several explanations remain possible:

- gratitude;
- reciprocity or felt debt;
- loyalty;
- trust earned by costly support;
- strategic alliance;
- shared enemy;
- career calculation;
- coincidence.

The architecture represents gratitude and reciprocal obligation without promoting them just because they make a compelling story.

### Coalitions can be overlapping, temporary and leaderless

Organizational factions do not always behave like political parties.

Alice and Bob may usually align on promotion questions. Carol may align with them only on budget questions. Dana may hold unusual influence without belonging cleanly to either group. Similar behavior can occur without explicit coordination.

Coalitions therefore need temporal and domain scope.

Similarity is not proof of conspiracy.

### Perceived power can become real power

Suppose an unverified rumor says the CTO backs Alice.

If enough people believe it, they may start routing decisions through Alice.

Her practical leverage can increase before the sponsorship claim is proven.

The rumor can remain weak evidence about the CTO while becoming strong evidence about the organization's behavior.

### Observation gaps stay visible

A missing meeting, deleted private channel, undocumented hallway conversation or unrecorded call is not silently filled in.

Likewise, a person going quiet can mean many things.

Absence becomes evidence only relative to a meaningful baseline.

The distinction between "nothing observed" and "evidence nothing happened" remains explicit.

### Nobody is the privileged narrator of organizational truth

Executives, managers, individual contributors, HR, salespeople, customers and the user all have partial views.

Formal authority can make someone authoritative about a policy or official decision without making that person infallible about motive, memory or informal relationships.

The organization remains multi-perspectival.

---

## UC-03 — Live situational reasoning in meetings, negotiations and operational interactions

Longitudinal reasoning and live reasoning have very different time budgets.

A deep dossier can take its time assembling months or years of context.

A live meeting cannot.

The architecture therefore treats the two as complementary:

```text
deep longitudinal context
        +
timestamped live evidence
        ↓
bounded situational reasoning
        ↓
policy-controlled delivery
        ↓
post-event reconstruction
```

The point is not one specific environment. The same problem appears in executive meetings, sales negotiations, project reviews, incident rooms, partnership discussions, customer escalations and other authorized interactions.

### The live path builds on history rather than recomputing it

Before an interaction, relevant context can include:

- prior messages and documents;
- known roles;
- relationship history;
- earlier episodes;
- CRM or workflow context;
- user-supplied knowledge;
- unresolved hypotheses;
- cultural or organizational context;
- known source gaps.

During the interaction, live reasoning retrieves relevant slices and updates the situational model.

It does not need to rediscover the entire history after every utterance.

### External systems can observe; Duhme reasons over what they report

A speech system may provide transcript segments and timestamps.

A meeting system may provide attendance and join/leave events.

A vision/event system may provide observable events.

A CRM or incident system may provide current operational state.

A human operator may correct attribution or add local meaning.

Duhme keeps the observation level explicit.

These are different:

```text
Observation:
"Carol turns her head toward Dana before answering."

Interpretation:
"Carol seeks Dana's approval before answering."
```

The first can be direct evidence supplied by an observing system.

The second is already an interpretation.

Collapsing them destroys provenance.

### Nonverbal evidence is not a motive detector

A pause, gaze, interruption, posture change or vocal shift may fit several explanations.

A participant looking toward another before answering could indicate deference, habit, uncertainty, coordination, distraction or nothing consequential.

Historical pattern, timing, role structure and later evidence can alter the balance among explanations.

No body-language event becomes a privileged truth channel.

### Words remain first-class evidence

Behavioral evidence does not automatically outrank explicit speech.

A clear statement from an appropriately authoritative source can outweigh weeks of weak signals.

Conversely, speech and behavior can conflict without either becoming automatically "the real truth."

A person can sincerely support a launch while repeatedly raising delivery risk. A public statement can reflect role obligation. A person can change their mind.

Conflict remains represented as conflict.

### Live systems have blind spots

Consider:

```text
14:10–14:19
hallway break
no transcript
no authorized camera coverage
two participants absent from the room
```

The correct representation is:

```text
UNOBSERVED INTERVAL
```

not:

```text
"They coordinated privately."
```

Later evidence can support a coordination hypothesis, but the gap itself remains a gap.

The same principle applies to missing email, chat or calendar coverage.

### Tactical state is derived, not sensor truth

During a meeting, Duhme may hold temporary hypotheses such as:

- the negotiation appears unstable;
- Alice currently appears isolated on proposal X;
- Bob and Carol currently appear aligned on delivery timing;
- the customer group may be preparing an alternative.

These are derived states with temporal scope and uncertainty.

They are not equivalent to observed deterministic state.

### Dynamic groups need dynamic representations

Participants can align on one issue and oppose one another on another.

One actor can coordinate informally without being a permanent leader. A coalition can form after new information and dissolve ten minutes later.

Live reasoning therefore cannot stamp durable faction labels onto every temporary alignment.

### Strategic behavior is ordinary

People may tell partial truths, perform agreement, signal differently to different audiences, float trial balloons, exaggerate capability, avoid commitment or form temporary coalitions.

The architecture treats these possibilities as competing explanations rather than as a universal presumption of manipulation.

### Belief about power can change the room

Suppose someone says:

> "If this goes to the board, Maria will block it."

Maria's actual intention may be unknown.

Yet if participants immediately change behavior, Duhme can distinguish:

```text
Claim:
Maria will block the proposal.
Support: weak / unknown.

Finding:
Several participants appear to believe Maria can or will block it.
Support: stronger.

Operational relevance:
High, because behavior is changing now.
```

Again, effect strength and truth strength are different.

### Important does not always mean interrupt now

During a live event, many observations can matter without deserving interruption.

A finding can be:

- stored;
- included in a post-meeting reconstruction;
- surfaced on a dashboard;
- mentioned at a natural pause;
- escalated immediately.

The system can hold a meaningful hypothesis internally without forcing it into the user's attention.

### The negotiation that later looks obvious

Imagine a 90-minute enterprise renewal negotiation.

Before the meeting, the longitudinal context contains:

- eighteen months of account history;
- email and collaboration evidence;
- CRM opportunity history;
- three earlier negotiation episodes;
- known participant roles;
- a prior conflict around delivery commitments;
- unresolved questions about who actually controls final approval.

During the first part of the meeting:

- procurement repeatedly avoids discussing term length;
- the technical sponsor stops defending the proposed scope;
- several participants check one representative before answering;
- a previously enthusiastic stakeholder becomes unusually quiet;
- a direct question receives a procedural rather than substantive answer.

None of those observations proves withdrawal.

Together, against the historical baseline, they may support a hypothesis that the customer is preparing to abandon the compromise.

Counterevidence may still remain:

- procurement stays engaged;
- nobody explicitly rejects the proposal;
- the meeting continues;
- practical delivery questions are still being asked.

The concern can therefore be meaningful without crossing the configured threshold for interruption.

Twenty minutes later, the customer walks away.

A responsible post-event reconstruction preserves that the withdrawal hypothesis existed earlier, how strong it was, what opposed it, and why it was not surfaced.

The later event strengthens the reconstruction. It does not rewrite the earlier uncertainty.

### Outcome feedback without hindsight certainty

After the event, domain experts can explain which signals mattered and which were noise.

The system can use that feedback to revise future interpretation.

But the fact that an outcome happened does not mean every earlier weak signal was secretly predictive.

Post-event learning has to preserve what was knowable at the time.

---

## UC-04 — Embedded business and application intelligence

Many applications already own deterministic business state.

A CRM owns accounts, contacts, opportunity stages and tasks.

An ERP owns orders, inventory and financial state.

A workflow system owns valid statuses and transitions.

Duhme's role is not to replace those systems. It is to add revisable human-context reasoning around them.

### CRM state and stakeholder reality are not the same thing

A CRM may know that an opportunity is active and that Maria is the formal contact.

It may know very little about:

- who actually influences Maria;
- which stakeholder is quietly blocking the deal;
- who has become a trusted informal sponsor;
- which past episode damaged the relationship;
- which old promise is still being remembered;
- which person appears powerful only because others believe they are powerful;
- which apparent ally has changed position.

Duhme can reason over those questions while the CRM remains the system of record for the deal.

### "What materially changed?" is often more useful than a static profile

Consider:

> "What materially changed in the Acme account relationship during the last 90 days?"

A useful answer is not merely the newest messages.

It may identify:

- turning-point episodes;
- new or weakened relationships;
- changes in who appears influential;
- public/private divergence;
- a previously weak hypothesis gaining support;
- missing coverage that limits interpretation;
- old history becoming newly relevant.

The answer remains connected to evidence and alternatives rather than collapsing the account into a personality summary.

### Deterministic state stays deterministic

Suppose the host application says:

```text
approval_status = PENDING
```

Duhme may reason:

```text
the approver appears more likely to reject
unless Finance changes the framing
```

That does not make the status `REJECTED`.

The host application owns valid operational state and actions. Duhme owns contextual interpretation around the humans interacting with that state.

### Boring operations remain boring

Not every action needs a deep human analysis.

> "Change quote quantity from 10 to 12."

can remain a deterministic operation.

> "Will changing the quantity now antagonize the buyer?"

invokes human-context reasoning.

The architecture does not turn ordinary application work into permanent epistemic ceremony.

### Attention policy belongs to the embedding context

One host application may want immediate alerts for a narrow class of events.

Another may prefer a daily briefing.

A third may show contextual cards only when a user opens an account.

Duhme's job is to produce reasoned, scoped human-context intelligence. The host context determines how aggressively that intelligence is surfaced.

### Enrichment, not product-category replacement

The same pattern can apply to CRM, support, ERP, HR workflow, project management, account planning, incident systems and specialized vertical applications.

Hard application state remains where it belongs.

Duhme adds the human layer around it.

---

## UC-05 — Cultural fields and FashionOS

Culture is a difficult reasoning surface because meaning is distributed across aesthetics, geography, class, subculture, age, history, aspiration, commerce, production capability and deliberate signaling.

Fashion makes that difficulty unusually visible.

There is no single universal `Zeitgeist`.

A Berlin humanities student, an English working-class consumer and a Vietnamese luxury buyer can inhabit overlapping but materially different cultural fields at the same historical moment.

The same object can therefore carry different meanings without one interpretation being globally canonical.

### Cultural meaning is scoped

A cultural interpretation is stronger when its scope is explicit:

- geography;
- language;
- time period;
- cohort;
- profession or domain;
- observer group;
- source quality;
- controversy and variance.

An artifact can be mainstream in one field, aspirational in another, ironic in a third, politically loaded in a fourth and largely meaningless in a fifth.

Duhme preserves those differences rather than averaging them into fake neutrality.

### Disagreement between experts is evidence

Two strong sources can disagree because they study different populations, periods or methods.

The architecture keeps source, population, scope and methodology visible.

Prestige is not a substitute for relevance.

A globally famous analysis may be less useful than a narrow local source for a specific social meaning.

### Cultural priors can inform people-level reasoning without becoming stereotypes

Population evidence can suggest candidate interpretations.

It cannot substitute for what is known about a particular person and relationship.

A luxury buyer can violate local norms. An artisan can deliberately play with a stereotype. A subculture can invert the meaning of a mainstream symbol.

Duhme therefore treats cultural knowledge as a reasoning field, not as a shortcut from identity to behavior.

### FashionOS as a proving surface

A broader fashion network can involve:

- designers;
- artisans;
- small producers;
- buyers;
- brands;
- logistics partners;
- retailers;
- cultural interpreters;
- trend evidence;
- capability and supply constraints.

The human-context problem is not simply "what is trending?"

It includes:

- which trend means what in which field;
- which signals are local and which transfer;
- which experts are biased toward one market;
- which producer capabilities fit which buyer expectations;
- which weakly connected participants may become useful collaborators;
- where an apparently similar aesthetic carries opposite social meaning.

A small producer in one country and a boutique buyer in another may be compatible even though neither appears in the other's conventional network.

Duhme's reasoning layer can help expose that compatibility without requiring one central broker to own the relationship.

### Cultural reasoning and mediation share the same substrate

The broader cultural-field problem feeds directly into cross-cultural mediation.

UC-05 asks:

> What does this artifact, style, phrase or signal mean across several cultural fields?

UC-01 asks:

> What does it likely mean **here**, between these people, in this relationship, right now—and how can that meaning cross to the other participant without being flattened?

The population field generates candidates.

The relationship decides how much those candidates deserve to matter.

---

## UC-06 — Fragmented enterprise evidence: the company gradually becomes legible

Real companies do not possess clean institutional memory.

They possess fragments.

Email exists for some years but not others. Attachments are missing. Employees leave. Collaboration platforms have shorter retention windows. Channels disappear. Old departmental ZIP files appear on network drives. Org charts describe the present better than the past. Local backups survive after official systems are gone.

The useful architecture is therefore not one that assumes a perfect corporate corpus.

It is one that becomes useful while explicitly knowing what it does **not** have.

### Two natural acquisition shapes

Enterprise evidence tends to arrive in two broad forms.

The first is bulk material:

- folders and directory trees;
- archives;
- mailbox exports;
- historical backups;
- old project directories;
- file shares;
- object-store corpora;
- whatever historical estate the customer can actually produce.

The second is live or incremental sources:

- email;
- collaboration platforms;
- document systems;
- calendars;
- issue trackers;
- source-control systems;
- CRM;
- filesystems;
- business applications;
- customer-specific systems.

Both are evidence acquisition paths into the same human/world model.

Neither implies flattening a gigantic corpus into one prompt or one summary.

### Institutional archive and human memory are different

Suppose a seven-year-old email is recovered from an old archive.

That changes the evidence available to Duhme.

It does not mean any current employee remembers the message.

Conversely, an employee may strongly remember a distorted version of an event whose original source no longer exists.

Duhme therefore separates historical availability from plausible human exposure, attention and memory.

This becomes crucial when old material resurfaces and suddenly affects a current dispute or relationship.

### Incomplete history remains explicitly incomplete

Suppose email is available for seven years but collaboration messages for only four.

The correct conclusion is:

```text
No collaboration-platform evidence is available before the retention boundary.
```

not:

```text
Nobody discussed this subject there before that date.
```

The source gap itself becomes part of later reasoning.

### Processing can be progressive

A large evidence estate does not become fully understood at once.

Files can be catalogued before they are deeply interpreted. Text can become searchable before all relationships and episodes are reconstructed. Some regions of the corpus can become useful while others remain coarse or unexplored.

That matters because useful questions can begin before the entire organization is equally legible, without pretending otherwise.

Later evidence can improve, narrow or overturn earlier answers.

### Messages are evidence neighborhoods, not flat strings

An email contains more than body text.

It has:

- sender;
- recipients and audience;
- time;
- thread structure;
- reply/forward relations;
- subject and conversational context;
- attachments;
- reactions and later replies.

Attachments are first-class artifacts rather than text pasted into the message.

If Jane writes:

> "Use this in the live environment."

and attaches `release.zip`, the transmission itself becomes evidence.

The archive may contain its own files, history and references.

The social act of sending it and the contents of the archive are related but not identical things.

### Claims inside messages remain claims

Suppose Jane writes to Richard:

> "Here's the JSON Mary sent me."

The message metadata establishes that Jane sent Richard an attachment.

Jane's sentence establishes a claim that Mary sent the same material to Jane earlier.

If later evidence independently shows Mary sending that exact content to Jane, the claim gains support.

Until then, the provenance distinction remains.

### Exact-content identity and social history are different

Three files named:

```text
Budget.xlsx
FINAL_Budget.xlsx
2027-final-really-final.xlsx
```

may contain exactly the same bytes.

Recognizing exact identity avoids repeated content work.

But the occurrences remain socially distinct:

- Alice emailed it to Bob;
- Carol uploaded it to a shared drive;
- Bob attached it to an issue;
- one copy appeared before a decision and another after it.

The transmission history can matter more than the bytes.

### Bundles carry meaning too

One message may contain:

```text
memo.docx
forecast.xlsx
risk.pdf
```

The three artifacts can remain independently addressable while also being treated as one evidence bundle when the surrounding message says they collectively support a recommendation.

Human meaning often exists at both levels.

### Evidence can be nested like Russian dolls

A realistic chain may look like:

```text
email
  → attached archive
      → release folder
          → README
              → link to collaboration thread
                  → message
                      → spreadsheet
                          → reference to shared document
```

Flattening the entire chain into one summary destroys addresses, provenance and relationships that may become important later.

Duhme treats the estate as an artifact/reference graph.

### One decisive fragment can hide inside hours of noise

A two-hour recording can contain ninety-nine minutes of trivial conversation and one short exchange that becomes important months later.

Low apparent information density is not proof of irrelevance.

The architecture preserves enough local addressability that a later event can make an old fragment newly material without pretending the earlier system knew its future importance.

### Files that mention no people can still become human evidence

Consider a log:

```text
PROD pipeline failed at T1 with signature L
```

Elsewhere, organizational evidence says:

```text
Jane owned PROD pipeline operations at T1
```

Source-control history says:

```text
signature L first appeared after change C
Bob authored C
```

The graph now connects people, systems, events and artifacts.

This supports questions such as:

- Who was responsible for the affected system at the time?
- When did the failure signature enter the history?
- What communication occurred around the change?

It does **not** prove:

- Bob caused the outage;
- Jane was negligent.

Graph proximity is not causation.

### Context mismatch can matter more than content

The same exact `config.json` can be discussed for a development environment in one thread and later transmitted explicitly for live operational use.

The bytes did not change.

The human meaning did.

Duhme therefore tracks not only content identity but occurrence, audience, purpose, timing and surrounding context.

### Old evidence can become newly relevant

A forgotten project folder may reveal that an issue believed to be new had a predecessor five years earlier.

A recovered message may weaken a current narrative.

A historical org chart may show that the person now blamed for a decision did not own the system at the time.

A resurfaced document may explain why two people remember an episode so differently.

The organization becomes gradually more legible as fragments accumulate.

Legibility is not omniscience.

### M&A makes the same problem more obvious

When two companies merge, they bring different archives, vocabularies, undocumented practices, authority structures and cultural assumptions.

Equivalent terms can mean different things.

Two roles with the same title can carry different practical authority.

Duplicated responsibilities can remain hidden because the organizations describe them differently.

The same fragmented-evidence machinery can help preserve each side's provenance while identifying overlaps, contradictions, emerging relationships and translation problems between the two institutional cultures.

---

# What ties the six scenarios together

The six scenarios look different because the surface domains are different.

Underneath them, the same architectural questions keep returning:

- What was actually observed?
- Who claimed what?
- What came from the same source?
- What is inference rather than evidence?
- Which interpretations remain plausible?
- What is missing?
- What did each actor plausibly know or remember at that time?
- Which relationships change the meaning?
- Which cultural assumptions are scoped to this population or context?
- What became stale?
- What was corrected?
- What changed after an intervention?
- What is deterministic application state and what is fuzzy human interpretation?
- Which conclusion can still be supported after evidence changes or disappears?

Duhme treats these distinctions as durable structure rather than relying on a model to recreate them from scratch on every conversation.

That is the core idea:

> **Reason deeply about humans without pretending we are simple, static, fully observed, internally transparent, or reducible to the last prompt.**

---

**Copyright 2026 Cambrian Radiation**
