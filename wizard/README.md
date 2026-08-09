# Wizard

A single-file, offline implementation of the trick-taking card game **Wizard**, for
1 human player plus up to 3 AI opponents.

Open `index.html` in any browser — no server, no build step, no network.

## Setup options

- **Players:** 2, 3, or 4 total. You are always one of them; the rest are AI.
- **Game length:** Quick (5 rounds), Short (10 rounds), or Full (60 ÷ players — 15 rounds
  at 4 players, 20 at 3, 30 at 2).
- **Dealer "hook" rule:** optional. When on, the dealer may not make the bids total
  exactly the number of tricks, so the round can never come out even.

## The game

60 cards: the standard 52 plus 4 Wizards and 4 Jesters. Round 1 deals one card each,
round 2 deals two, and so on. After the deal, the next card off the deck sets trump —
a flipped Wizard lets the dealer choose it, a flipped Jester means no trump, and on the
final round the deck is empty so there is no trump at all.

Everyone bids the exact number of tricks they will take. Follow the led suit if you can;
Wizards and Jesters may always be played. The first Wizard played wins the trick, else the
highest trump, else the highest card of the led suit. Hit your bid exactly for **20 points
plus 10 per trick**; miss it for **−10 per trick** over or under.

## Implementation notes

- Rules engine is pure and separated from the UI: `leadSuitOf`, `trickWinnerIndex`,
  `legalCards`, `scoreRound`.
- Round flow is an `async` loop; human turns await a promise resolved by a card tap or
  bid button, so the same code path drives human and AI players.
- The AI bids by summing a per-card win-probability estimate that accounts for trump and
  player count, then plays to hit that bid — taking tricks as cheaply as it can while it
  still needs them, and shedding its highest safe card once it doesn't. It bids exactly
  right about **57%** of rounds at 4 players.
- `?fast=1` shortens all animation delays; `window.wizardDebug` exposes the rules
  functions and live state. Both exist for the automated browser tests.
