# Campaign Message Engine — setup and quickstart

Read this first. Total setup time: 10 minutes. First campaign: 15–20 minutes.

## What's in this package

| File | What it is | What you do with it |
|---|---|---|
| `01-setup-and-quickstart.md` | This file | Read first |
| `02-system-prompt.md` | The engine itself | Paste into Claude project custom instructions |
| `03-channel-specifications.md` | Reference for the six channels | Upload to project knowledge base |
| `04-banned-phrases.md` | The no-fly list | Upload to project knowledge base |
| `05-worked-example.md` | A full campaign, end to end | Upload to project knowledge base (also use as quality benchmark) |
| `06-voice-guide-template.md` | Your voice, defined | Customize, then upload to project knowledge base |
| `07-audience-and-cta-template.md` | Your audience and CTAs | Customize, then upload to project knowledge base |

## Setup, step by step

### Step 1 — Create the project (2 minutes)
Open Claude. Click **Projects → New project**. Name it **Campaign Message Engine**. Add a description if you want.

### Step 2 — Paste the system prompt (1 minute)
Open `02-system-prompt.md`. Copy everything between the code fence markers. Paste it into the project's **Custom instructions** field. Save.

If the field cuts off your paste, see the troubleshooting section at the bottom of this file.

### Step 3 — Customize your voice and audience (5–7 minutes)
Open `06-voice-guide-template.md` and `07-audience-and-cta-template.md`. Fill in the blanks. Be specific. "Professional" is not a voice descriptor — "dry, technical, slightly impatient with vendor pitches" is.

If you don't have a defined brand voice yet, paste 2–3 samples of writing you wish your brand sounded like into the voice guide. The engine will pattern-match against them.

### Step 4 — Upload the knowledge files (1 minute)
In the Claude project, find the **Project knowledge** section. Upload all of these:
- `03-channel-specifications.md`
- `04-banned-phrases.md`
- `05-worked-example.md`
- Your customized `06-voice-guide-template.md`
- Your customized `07-audience-and-cta-template.md`

### Step 5 — Run the worked example as a smoke test (5 minutes)
Open a new chat inside the project. Paste this:

> Run a test campaign for me using this core message: [paste the core message from `05-worked-example.md`]

Compare what the engine produces to the worked example. If the outputs are roughly the same quality and voice, you're set. If they're wildly different, your voice guide isn't doing enough work — go back to step 3 and add more specifics.

## How to run a campaign

1. Open a new chat in the project.
2. Paste your core message (1–2 sentences).
3. Answer the engine's intake questions: audience, voice, desired action, anything off-limits.
4. Wait 30–60 seconds for all six channels.
5. Flag 1–2 channels that need revision. Be specific: "make the LinkedIn post sharper, less explanatory" beats "I don't like the LinkedIn post."
6. Ship.

## What good looks like

A successful campaign run produces:
- Six channel-specific pieces that all carry the same argument
- Voice that sounds like you, not like ChatGPT pretending to be you
- CTAs that match what you actually want the reader to do
- A short voice consistency note from the engine explaining its decisions

## What failure looks like

- All six pieces sound vaguely the same and vaguely flat → voice guide is too thin
- The engine generates without asking intake questions → system prompt didn't paste cleanly, redo step 2
- CTAs are generic ("Learn more," "Click here") → you didn't fill in the CTA bank in step 3
- The same buzzword appears in three channels → check that banned-phrases uploaded correctly

## Troubleshooting

**The custom instructions field cut off my paste.**
Claude's custom instructions field has a character limit. If your paste got truncated, move the "channel specifications" section out of the system prompt and rely on the `03-channel-specifications.md` knowledge file instead. Keep the intake protocol and voice rules in custom instructions — those are load-bearing.

**The engine ignores my voice guide.**
Two common causes. First, the voice guide is too abstract ("we sound professional and friendly"). Add concrete words to use, words to avoid, and 2–3 sample sentences. Second, the file didn't upload — check the project knowledge section.

**The engine asks the same intake questions every session.**
That's intended. Audience, action, and off-limits change per campaign. If you want the engine to skip intake for repeat campaigns to the same audience, add a "default audience" section to your audience template that the engine can fall back on.

**My outputs sound like every other LinkedIn post.**
Your voice guide isn't strong enough. The banned phrases file removes the worst patterns, but it doesn't generate voice — that comes from the voice guide. Add at least one writing sample of 100+ words that represents your actual voice.

## When to use this — and when not to

**Use it for:** product launches, feature announcements, campaign concepts, positioning rollouts, thought leadership amplification, event promotion.

**Don't use it for:** the initial positioning work itself. The engine adapts a finished message — it doesn't help you find the right message in the first place. If you don't have a core message yet, write one first.
