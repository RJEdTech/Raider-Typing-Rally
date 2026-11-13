# Raider Typing Rally

Typing races built from your class's own words. Any Regis Jesuit teacher makes a game, pastes word lists or paragraphs as levels, and gives students a code. Students race classmates live (teacher hosts on the projector) or practice against classmates' best runs, and climb the boards.

**Live site:** https://rjedtech.github.io/Raider-Typing-Rally/

Idea by Paul Stearman. Built by RJ Ed Tech.

## What it does

- **Teachers** sign in with a verified @regisjesuit.com email, make games, and add levels (paragraphs or word lists, time limits, words per race). Optional class sections.
- **Students** join with the game code, their school email and first name. Leaderboards show first name + last initial only.
- **Practice races** against "ghosts" of classmates' best runs (the class leader, the student just ahead of you, the one just behind) plus your own best.
- **Live races**: the teacher opens a starting line, students join, the teacher starts it; everyone sees the same track in real time.
- **Leaderboards** per level: top 10 by section, by school year (turns over July 1), and all-time.
- **Progress**: each student's WPM trend per level; the teacher's Students tab shows everyone, with a CSV download of every race.
- Ten racers, including a frog, a race car and St. Ignatius the pilgrim.

## How it's built

One `index.html` (no build step on GitHub Pages). Data lives in **Firebase Realtime Database**; students sign in anonymously behind the scenes, teachers with email + password (email must be verified). `database.rules.json` is the security policy: only a game's owner can edit it or see student emails; best scores can only go up; WPM is capped at 250.

With no Firebase config in the page, it runs in **demo mode**: everything is stored in the browser and tabs can race each other.

## Setup (one time)

1. Firebase console → Add project → Build → **Realtime Database** → Create (United States, locked mode).
2. Rules tab → paste `database.rules.json` → Publish.
3. Build → **Authentication** → Get started → enable **Email/Password** and **Anonymous**.
4. Authentication → Settings → Authorized domains → add `rjedtech.github.io`.
5. Project settings → Your apps → Web app → copy the `firebaseConfig` object into `index.html` where it says `var FIREBASE_CONFIG = null;`.

## License

© 2026 Jason Beyer, RJ Ed Tech. [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/).
