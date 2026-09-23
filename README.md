# Delta_dxz

These are **my personal study notes**, not a published textbook or tuition pack. Combined Maths, Physics, and ICT, written to match the **NIE syllabus** (Grades 12 & 13 / Teachers' Guides), plus a Computer Science track if you like coding.

They've been working for me: **90+ on every Combined Maths and ICT exam**. Physics is the exception — I just hate it, which is probably why I'm stuck at **55–65**. Take the Physics folder with that energy in mind.

This is an [Obsidian](https://obsidian.md) vault. Clone it, open the folder as a vault, and you get wiki-links, callouts, math, diagrams, and flashcards. You can still read the markdown on GitHub if you just want to skim.

Not official NIE / DoE material. Just my notes, kept on syllabus for the three A/L subjects.

---

## What's in here

| Folder | What it is | Exam stuff? |
| --- | --- | --- |
| `01 - Maths` | Combined Mathematics — pure + applied | Yes. NIE-aligned |
| `02 - Physics` | Physics units 01–11 | Yes. NIE-aligned |
| `03 - ICT` | ICT units 01–13 | Yes. NIE-aligned |
| `04 - Computer Science` | C++ + competitive programming | Extra. For fun / contests, not A/L CS |

Each A/L subject has:

- a **Map of Concepts** (the index — start here)
- numbered **lesson** notes
- **Subtopics/** for the messy exam pieces (subnetting, K-maps, projectiles, etc.)
- **flashcards** at the bottom of notes (`Question :: Answer`)

There are also `Books/`, `Past Papers/`, `PDFs/`, and `Templates/` if those get filled in. The notes are the main event.

---

## Combined Maths

Start: [`01 - Maths/Maths - Map of Concepts.md`](01%20-%20Maths/Maths%20-%20Map%20of%20Concepts.md)

**Pure:** real numbers & inequalities, polynomials, quadratics, complex numbers, sequences & induction, permutations & binomial, trig, differentiation, integration, coordinate geometry, matrices.

**Applied:** statics & friction, dynamics / kinematics / projectiles, work–power, SHM, collisions, probability.

---

## Physics

Start: [`02 - Physics/Physics - Map of Concepts.md`](02%20-%20Physics/Physics%20-%20Map%20of%20Concepts.md)

Measurements, mechanics, oscillations & waves, thermal, gravity, electrostatics, magnetic field, current electricity, electronics, mechanical properties of matter, modern physics (photoelectric, X-rays, radioactivity).

Subtopic notes cover the usual exam headaches: instruments & errors, rotation, optics, gases, capacitors, potentiometer / Kirchhoff, transistors & op-amps, elasticity & viscosity.

---

## ICT

Start: [`03 - ICT/ICT - Map of Concepts.md`](03%20-%20ICT/ICT%20-%20Map%20of%20Concepts.md)

Units 01–13: ICT basics, computer evolution & architecture, data representation, digital logic, OS, networking, SAD, DBMS, programming, web (HTML/CSS/PHP), IoT, e-commerce, new trends.

Deeper notes for Von Neumann, K-maps, process/memory, IP & subnetting, DFD/ER, 1NF–3NF, SQL, Python, PHP/MySQL, Arduino-ish IoT, IEEE bits, etc.

---

## Computer Science (optional)

Start: [`04 - Computer Science/Computer Science - Map of Concepts.md`](04%20-%20Computer%20Science/Computer%20Science%20-%20Map%20of%20Concepts.md)

This is **not** part of the A/L Combined Maths / Physics / ICT pack. It's C++ contest prep I added for myself and anyone who wants extra CS:

- a full-ish C++ reference for CP
- foundations: I/O, complexity, STL, sorting/search, prefix sums / two pointers, recursion & backtracking, greedy
- data structures: trees, Fenwick/segment trees, strings, linked lists, hash maps
- heavier stuff: number theory, DP, graphs, FFT/NTT/CRT

Suggested loop is in that map: read a lesson, type the code, grind a few CSES / AtCoder ABC / CF Div 3 problems, upsolve. Don't skip complexity.

---

## How to use this (students)

### Option A — Obsidian (recommended)

1. Install [Obsidian](https://obsidian.md) (free).
2. Clone the repo:

```bash
git clone https://github.com/zenyyxz/Zen_dx-Notes.git
```

3. In Obsidian: **Open folder as vault** → pick the cloned folder.
4. Turn on **community plugins** and install the three this vault actually needs (Settings → Community plugins → Browse):
   - **[Iconize](https://github.com/FlorianWoelki/obsidian-iconize)** — icon pack. Notes use `:LiWhatever:` style icons. Without Iconize they look like broken shortcodes, not icons.
   - **[Git](https://github.com/denolehov/obsidian-git)** — sync. Pull updates from this repo / push your own backup without leaving Obsidian.
   - **[Spaced Repetition](https://github.com/st3v3nmw/obsidian-spaced-repetition)** — flashcards. Notes have `#flashcards` and `Front :: Back` cards. Reading the lesson once won't stick; you have to test yourself.
5. Open the Map of Concepts for your subject and click through `[[wikilinks]]`.

Math is LaTeX (`$...$` / `$$...$$`). Mermaid diagrams render in Obsidian. GitHub will show markdown + math reasonably well; callouts and wikilinks are nicer in Obsidian.

Without **Iconize**, **Git**, and **Spaced Repetition**, the vault still opens, but icons break, you won't have in-app sync, and you're skipping the whole point of the cards. Install all three if you actually want to *use* this the way it's set up.

### Option B — just GitHub

Browse the folders, open a Map of Concepts, then open lesson files. Fine for a quick look. Links like `[[Lesson 06 - ...]]` won't navigate the same way.

### Flashcards

Look for `#flashcards` near the end of a lesson. Cards look like:

```text
State the change of base formula for logarithms. :: $\log_b x = \frac{\log_a x}{\log_a b}$.
```

That's what the **Spaced Repetition** plugin is for. Review them daily. Reading notes without testing yourself is how you think you know it until the paper.

---

## Repo layout

```text
Delta_dxz /
├── 01 - Maths/
│   ├── Maths - Map of Concepts.md
│   ├── Lesson 01 … Lesson 14
│   └── Subtopics/
├── 02 - Physics/
│   ├── Physics - Map of Concepts.md
│   ├── Lesson 01 … Lesson 11
│   └── Subtopics/
├── 03 - ICT/
│   ├── ICT - Map of Concepts.md
│   ├── Lesson 01 … Lesson 13
│   └── Subtopics/
├── 04 - Computer Science/
│   ├── Computer Science - Map of Concepts.md
│   ├── 00 - C++ Reference/
│   ├── 01 - C++ Foundations & Algorithmic Paradigms/
│   ├── 02 - Core Data Structures & Strings/
│   └── 03 - Advanced Algorithms & Math/
├── Books/
├── Past Papers/
├── PDFs/
├── Templates/
└── README.md
```

Lesson notes usually have YAML frontmatter (title, subject, unit, tags), a syllabus-scope blurb, the actual notes, then flashcards.

---

## Keeping it updated

In Obsidian: **Git** plugin → pull (that's why it's required).

Or from a terminal:

```bash
cd Zen_dx-Notes
git pull
```

If you forked it and made your own edits, pull carefully so you don't wipe your stuff.

---

## Contributing

Found a wrong formula, a syllabus mismatch, or a clearer way to explain subnetting? Open an issue or a PR. Keep A/L notes **on syllabus**. Don't dump random university content into Maths / Physics / ICT.

CS notes can be more extra — that's the point of that folder.

---

## Disclaimer

- Aligned with the Sri Lankan GCE A/L **NIE** Teachers' Guides / syllabus scope for Combined Maths, Physics, and ICT.
- Still just my personal notes. Syllabus and papers can change. Check the official NIE docs when it matters.
- Marks I mentioned (90+ Maths/ICT, 55–65 Physics) are mine, not a promise you'll get the same. Do past papers.
- Not a substitute for past papers, your teacher, or actually doing problems.
- CS folder is personal / enthusiast material, not an A/L Computer Science course.

Use it, share it with your batch, don't sell it as a paid tuition pack.

---

## Credits

Maintained as **Delta_dxz** — notes vault, git backup: [zenyyxz/Zen_dx-Notes](https://github.com/zenyyxz/Zen_dx-Notes).

If this helped you survive a term test, send it to a friend who's still drowning in K-maps.
