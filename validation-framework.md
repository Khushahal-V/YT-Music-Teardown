# How I'd validate this

This is a proposal, not something I could ship and measure, so this is more "here's what I'd check if I could" than actual results.

**1. Can people actually tell the repeat states apart?**
Get 5-8 people, most of whom haven't seen this before, and ask them to identify the current repeat state at a glance — no explanation given. Do this for the current 3-state version and the new 4-state one, and compare accuracy. If the new version doesn't score noticeably better, the fix isn't working.

**2. Does confusion actually go down?**
The Spotify and Deezer threads I found while researching this are exactly the kind of complaint I'd want to track. If a change like this shipped, I'd want to see whether that kind of "wait, what does this icon mean" post shows up less often afterward.

**3. Is the press-and-hold actually faster than guessing?**
Time how long it takes someone to confirm the repeat state using the new press-and-hold label, versus how long they currently spend tapping through states to figure it out by trial and error. If it's not meaningfully faster, it's not really solving the problem, just moving it.

**4. Do version tags actually reduce mistaken re-saves or duplicate searches?**
For the title/version tag fix, I'd want to check whether people mistakenly search for or re-save a song they already have (just under a different-looking title) less often once the version tag is visible. This is harder to test without real usage data, but a simple version could be: show people a library with duplicate-looking titles, ask them to spot which ones are actually the same song, with and without version tags, and compare accuracy.

None of these need a shipped feature to test — 1, 3, and 4 could realistically be run as a small moderated usability test with a handful of people and the working prototype in this repo.
