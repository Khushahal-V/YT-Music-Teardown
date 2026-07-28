# How I'd validate this

This is a proposal, not something I could ship and measure, so this is more "here's what I'd check if I could" than actual results.

**1. Can people actually tell the repeat states apart?**
Get 5-8 people, most of whom haven't seen this before, and ask them to identify the current repeat state at a glance — no explanation given. 5-8 is a reasonable size here since most usability testing guidance suggests the majority of major comprehension issues show up within the first 5 users anyway — I don't need a huge sample to know if the icon is still confusing.

Do this for the current 3-state version and the new 4-state one, and compare accuracy. I'd want to see a meaningful jump, not just a marginal one — something like going from roughly half of people guessing correctly to most of them, not 55% to 60%. If it's a small bump, that's a sign the redesign isn't actually solving the problem, just rearranging it.

**2. Does confusion actually go down, measurably?**
The Spotify and Deezer threads I found while researching this are exactly the kind of complaint I'd want to track. But "see if fewer posts show up" isn't really measurable on its own — I'd want to look at community/support mentions of repeat-mode confusion over a fixed window, say 4-6 weeks before and after a change like this, and normalize it against active users rather than raw counts, since usage could just be growing anyway.

**3. Is the press-and-hold actually faster than guessing?**
Time how long it takes someone to confirm the repeat state using the new press-and-hold label, versus how long they currently spend tapping through states to figure it out by trial and error. If it's not meaningfully faster, it's not really solving the problem, just moving it.

**4. Do version tags actually reduce mistaken re-saves or duplicate searches?**
For the title/version tag fix, I'd want to check whether people mistakenly search for or re-save a song they already have (just under a different-looking title) less often once the version tag is visible. Simple version: show people a library with duplicate-looking titles, ask them to spot which ones are actually the same song, with and without version tags, and compare accuracy.

**5. What could this break, that I'm not measuring above?**
It's easy to only check whether a fix helps and forget to check what it might cost. Two things I'd specifically watch for:
- Does the press-and-hold gesture slow down casual use for people who never cared about the repeat state in the first place? If regular playback suddenly feels heavier or more fiddly, that's a real cost even if recognition improves.
- Do version tags make search results feel more cluttered for people who never noticed or cared about duplicate versions to begin with? Solving confusion for some users shouldn't come at the cost of adding visual noise for everyone else.

**6. What does this actually move, business-wise?**
Being honest about scope here — this isn't a conversion or revenue-driving change. It's closer to a satisfaction and retention-adjacent fix: reducing small moments of friction that, on their own, aren't going to move a business metric much, but compound over time into "this app feels annoying to use," which is the kind of thing that quietly contributes to churn rather than any single dramatic drop-off. I'd frame success here as a usability/support-load improvement, not pretend it's something it isn't.

None of the above needs a shipped feature to test — 1, 3, 4, and 5 could realistically be run as a small moderated usability test with a handful of people and the working prototype in this repo.
