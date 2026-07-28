# YouTube Music — a small UX audit on playback controls and library clarity

I use YouTube Music daily, and a couple of small things about it have bugged me for a while. This is a short, self-initiated audit of two of them — not a full app teardown, just two specific problems I could actually dig into properly.

## The problems

**1. The repeat icon doesn't tell you what state it's in.**

There's one icon that cycles through "no loop," "repeat one song forever," and (confusingly) something that looks almost identical to "no loop" but isn't. I've genuinely tapped it, wasn't sure what had changed, and had to just wait and see what played next to figure it out. Turns out I'm not the only one — there's a thread on the Spotify community where someone describes the exact same confusion, saying the icon basically shows the opposite of what you'd expect it to mean.

**2. There's no way to loop a song once and only once, or loop it forever, without it being the same button.**

Right now "repeat one" only ever means infinite repeat. If you just want a song to play one extra time, there's no option for that — you'd have to manually restart it. I went looking and found people on Deezer's forum asking for exactly this (infinite repeat of a single track), and old Spotify community threads from years ago where people were asking for a dedicated "repeat track" mode long before it existed. So this isn't a hypothetical — it's a known gap people have wanted addressed before.

**3. The same song shows up under different titles, and you can't tell which version is which.**

This one's separate from the icon stuff. A lot of songs exist as multiple versions — remix, live, radio edit, re-release — and often the title alone doesn't tell you which one you're looking at, or whether you've already saved a different version of the same track. I've had moments where I wasn't sure if I already had a song saved because the title looked slightly different than what I remembered. This isn't just a YouTube Music thing either — Spotify's community forum has several threads of people saying the exact same thing, calling it confusing and asking why there are so many near-identical versions cluttering search and their library.

## What I did

- Used the app myself and noted where the confusion actually happened (screenshots in the PDF)
- Looked for existing discussion of the same issues on Spotify and Deezer's community forums, since none of this is unique to YouTube Music
- Found that YouTube already made a small fix for part of the icon problem — they added a white dot under the icon for one of the states — which is useful because it means the problem is real enough that the product team already tried to patch it, just not completely

## What I'm proposing

### For the repeat icon

Split the current repeat button into **4 distinct states** instead of 3:

1. No loop
2. Repeat the song once more, then stop
3. Repeat the song forever
4. Repeat the whole playlist

And instead of trying to cram all of that meaning into one small icon (which is how we got here in the first place), add a press-and-hold interaction — hold the icon down and it shows you the current state in plain text, like "Repeat: song, 1 more time." No permanent clutter on the player bar, but no more guessing either.

I built this out as an actual clickable mockup rather than just describing it — see `proposed-solution/interactive-mockup.html`. Open it in a browser, click the repeat icon to cycle through the 4 states, and hover over it (or press and hold on mobile) to see the label. There's also a PDF with before/after screenshots in the same folder.

### For duplicate/confusing titles

Show a small tag next to the track title whenever version metadata is available — "Remix," "Live," "Radio Edit," that kind of thing — so you can tell versions apart without tapping into each one.

The catch is this depends on whether that version info even exists in the backend already. If it does and it's just not being shown, this is a simple display fix. If it doesn't exist yet for a lot of tracks, someone has to go add that metadata at the content/catalog level first, which is a bigger, slower fix involving whoever manages content tagging, not just design or engineering. I think it's worth saying that upfront rather than pretending it's a five-minute change.

There's also a smaller trade-off worth naming: if every version gets its own visible tag, search results could get more cluttered, not less. So I'd default to showing the most-played version first, with other versions tucked behind something like "see other versions" instead of listing all of them flat.

## Why not just redesign the icons and leave repeat at 3 states?

I considered that first, honestly. But if repeat-one is fundamentally ambiguous about whether it means "once" or "forever," redesigning the icon alone doesn't fix that — it's not a visibility problem, it's that one icon is being asked to represent two different things people actually want separately. Adding a 4th state addresses the actual gap, not just how it's drawn.

## How I'd actually check if any of this works

I can't ship this and measure real usage, so instead, here's how I'd validate it if I could:
- Sit a handful of people down, ask them to identify the current repeat state without explanation, before and after the change, and see if accuracy improves
- Check if community complaint threads about repeat mode confusion (the kind I found while researching this) drop off after a change like this ships
- Time how long it takes someone to confirm the state using the press-and-hold — if it's not noticeably faster than the current tap-and-guess approach, the fix isn't actually working
- For the title/version tags, check whether people mistakenly re-save or re-search for a song they already have less often once tags are visible

More detail on this in `validation-framework.md`.

## Sources

All the community threads and articles I used to back this up are listed in `research/sources.md`, with links.

---

This was done independently, based on my own usage of the app — it's not affiliated with or reviewed by Google/YouTube in any way.
