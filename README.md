# Campaign Message Engine

A Claude Project that takes one core message and adapts it across six marketing channels in about 20 minutes, without flattening voice or losing the argument.

## What it does

You write one good sentence about your launch, your positioning, or your campaign concept. The engine produces six channel-specific pieces from it:

1. Marketing email (subject lines, preheader, body, CTA)
2. LinkedIn post (hook, body, soft CTA)
3. Paid social ad (headline variants, primary text, description, CTA button, visual recommendation)
4. Landing page hero (H1, subhead, primary and secondary CTAs, trust strip suggestion)
5. Sales email (subject variants, three-part body, low-friction ask)
6. Short-form video hook (script with timing, on-screen text, spoken CTA)

All six carry the same argument. All six sound like you, not like ChatGPT pretending to be you.

## Why this exists

The four-hour version of this workflow is: write the email, rewrite it as a LinkedIn post, compress it for the ad, expand the H1, rewrite the whole thing for sales, and then realize it's all gone flat. You end up with six pieces that vaguely resemble each other, none of which carry the original argument intact.

The two-prompts-to-ChatGPT version is worse: six pieces that all sound the same kind of generic, with the same buzzwords showing up in every channel.

This project sits between those. It forces a structured intake (audience, voice, action, off-limits) before generating, references a banned-phrases file that strips out the universal slop, and uses channel-specific conventions baked into the system prompt so each output respects its surface.

## Who this is for

- Solo marketers at startups (1-person marketing teams running multi-channel campaigns)
- Fractional CMOs and content consultants working across 3+ clients
- Founders doing their own marketing
- Demand gen and growth leads who own end-to-end campaign execution
- Sales enablement leads who need consistent messaging across SDR, AE, and marketing surfaces

## Who this is not for

- Agencies with their own production systems
- Enterprise marketing teams with a dedicated content ops function
- Anyone who doesn't already have a core message to adapt (this isn't a positioning tool — it adapts a finished message, it doesn't help you find one)

## Requirements

- Claude Pro, Team, or Enterprise account (Projects require a paid plan)
- A defined brand voice (or willingness to define one — the voice guide template walks you through it)
- One core message per campaign run

## What's in this repo

```
campaign-message-engine/
├── 01-setup-and-quickstart.md       Read first. 10-minute install guide.
├── 02-system-prompt.md              The engine. Paste into Claude project custom instructions.
├── 03-channel-specifications.md     Reference doc for the six channels. Knowledge base file.
├── 04-banned-phrases.md             Universal no-fly list with rationale. Knowledge base file.
├── 05-worked-example.md             Full campaign, end to end. Knowledge base file and quality benchmark.
├── 06-voice-guide-template.md       Customize this for your voice. Knowledge base file.
└── 07-audience-and-cta-template.md  Customize this for your audience. Knowledge base file.
```

## Quickstart

1. **Create the project.** In Claude, click Projects → New project. Name it Campaign Message Engine.
2. **Paste the system prompt.** Open `02-system-prompt.md`. Copy everything between the code fence markers. Paste into the project's custom instructions field.
3. **Customize your voice and audience.** Fill in `06-voice-guide-template.md` and `07-audience-and-cta-template.md`. Be specific. "Professional" is not a voice descriptor.
4. **Upload the knowledge files.** Add files 03 through 07 to the project's knowledge base.
5. **Run the worked example as a smoke test.** Open a new chat and paste the core message from `05-worked-example.md`. Compare your output to the example. If quality matches, you're set.

Total setup time: 10 minutes. First campaign: 15–20 minutes.

## Example output

Input core message:
> Our customer onboarding software cuts time-to-first-value from 6 weeks to 9 days for B2B SaaS companies with complex products.

Voice descriptors: plain-spoken, data-forward, slightly impatient with customer success theater.

Sample LinkedIn output (one of six channels):

> 73% of CSM time in the first month of onboarding is configuration and data mapping.
>
> Not coaching. Not adoption. Not relationship-building.
>
> Configuration.
>
> We ran the teardown across 47 B2B SaaS onboarding flows last year, and the pattern held in every single one: complex products eat their customer success teams alive in the first 30 days, because nobody systematized the setup work.
>
> The fix isn't a better onboarding deck. It's not a longer kickoff call. It's not another "wow moment" framework.
>
> The fix is removing the rebuild work from the CSM's plate entirely.

See `05-worked-example.md` for the full six-channel output and a breakdown of what to notice.

## How it works

The engine runs every campaign through the same four-step protocol:

**Intake.** Before generating, the engine confirms the core message, audience, voice descriptors, desired action, and off-limits constraints. If anything is missing, it asks (in a single consolidated reply, never one question at a time). Adapting bad input produces six pieces of bad output, so the intake is non-negotiable.

**Generation.** All six channels produced in a single response, in fixed order, with labeled sub-elements (subject lines, body, CTA, etc.) so you can copy individual pieces.

**Voice consistency note.** After the six channels, the engine returns a short note explaining what it preserved across channels and what it adjusted for channel norms. This makes its decisions auditable.

**Revision protocol.** When you ask for revisions, the engine asks which channel and what specifically. It does not regenerate all six unless asked. It does not silently rewrite channels you didn't flag.

## Customization

Two files in this bundle are templates you fill in:

- **`06-voice-guide-template.md`** — your three voice descriptors, anchor and anti-anchor writers, vocabulary preferences, sentence patterns, and 1–3 writing samples to calibrate against.
- **`07-audience-and-cta-template.md`** — your primary audience persona, their priorities and objections, and your CTA bank organized by funnel stage.

Both include filling tips for the sections that are hardest to complete (objections, "what they ignore," CTA verbs). Most prompt-pack products ship templates that assume the buyer already has this work done. Most buyers don't. The tips close that gap.

The other knowledge files (channel specs, banned phrases, worked example) ship ready to use. You can extend them, but you don't have to.

## What it isn't

- **A positioning tool.** The engine adapts a finished message. It doesn't help you find the right one.
- **A content automation system.** You still write the core message. You still review the output. You still decide what ships.
- **A replacement for a copywriter.** It's a force multiplier for someone who already knows what good marketing copy reads like. If you can't recognize when output has gone flat, this will produce six pieces of flat output and you won't notice.
- **A general-purpose AI tool.** It does one thing: adapt one core message across six channels with voice preservation. It will refuse to do other things (write blog posts, generate ideas, draft positioning) and redirect you.

## Known limitations

- **Character limits in Claude's custom instructions field.** The system prompt is sized to fit, but if Anthropic changes the limit, you may need to move the channel specs section out of the prompt and rely on the knowledge file. See troubleshooting in `01-setup-and-quickstart.md`.
- **Voice drift on long sessions.** If you run 10+ campaigns in a single chat thread, voice can drift. Open a new chat for each major campaign.
- **No image or video generation.** The engine recommends what visuals would support the copy. It doesn't produce them.

## Versioning

This is v1.0. Channel norms (especially LinkedIn truncation behavior, paid social character limits, and CTA button options) change. Updates will live in this repo with a CHANGELOG. Major changes to the system prompt will be flagged.

## License

[Specify your license here. Common options for productized templates: a custom commercial license if sold via Gumroad/Notion Marketplace, MIT if open-sourced, or CC BY-NC-SA if free with attribution requirements.]

## Support

Issues, bug reports, and feature requests: open an issue in this repo.

For setup help, refer to `01-setup-and-quickstart.md` first. The troubleshooting section covers the most common problems.

## Acknowledgments

Built on Claude Projects (Anthropic). Channel conventions sourced from observed best practices across B2B SaaS marketing, sales enablement, and content operations work.
