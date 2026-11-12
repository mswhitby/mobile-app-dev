# Mobile App Development

Four introductory competencies: HTML, CSS, JavaScript, and React. React Native extends the React competency when mobile tooling is ready. Introduce TypeScript after JavaScript fundamentals.

## Edit lessons

Write lesson prose directly in `lessons/<competency>/lesson.md`. These are ordinary Markdown files, with headings, bold vocabulary, inline code, fenced examples, and GitHub previews. Each lesson can have its own structure. The starter beside it is a normal source file. **For new lessons use separate HTML, CSS, and JavaScript source files instead of embedding CSS/JS in an HTML file.** `course.json` contains navigation paths only, not lesson prose.

The shared Playground website publishes these files with its common layout, highlighted editor, and preview. No student account secrets belong in browser examples.


## Source-file contract for new lessons and projects

For each **new** Mobile App & Web lesson or guided project, author three individual starter files in its owning directory:

```text
index.html
styles.css
script.js
```

For React lessons, use `App.jsx` instead of `script.js`. Students edit one file at a time; the preview loads all three together. The HTML file should explicitly reference the separate files:

```html
<link rel="stylesheet" href="styles.css">
<!-- At the end of body (or with defer) -->
<script src="script.js" defer></script>
```

For JSX, reference `App.jsx` in the HTML starter; the Playground preview compiles JSX locally and loads the React runtime. Do **not** ask beginners to embed long `<style>` or `<script>` blocks in `index.html`.

New manifest rows can include a `starterFiles` map alongside the legacy `starterFile` entry:

```json
"starterFiles": {
  "index.html": "lessons/example/index.html",
  "styles.css": "lessons/example/styles.css",
  "script.js": "lessons/example/script.js"
}
```

The React preview supports this optional map and falls back to safely splitting published one-file starters. Retain existing `starterFile` entries for the production app until its reader is migrated. **Do not rename published lesson/project/step IDs or delete old starters.** Keep the same three project files across all steps of a guided project; each *different* lesson or project receives a separate file set. A lesson's Markdown should direct students to the relevant filename instead of saying to edit CSS or JavaScript inside HTML.

The canonical `mswhitby/playground` build copies this entire course repository to `dist/data/mobile-app-dev/`, so files in `starterFiles` can be included when the curriculum bundle is next deliberately rebuilt and published. Adding a manifest path alone does not deploy or backfill student records; update `starterFiles` and those actual files together, then verify the browser preview and published practice checks before release.

## Guided mini-projects

Projects are a separate `projects` collection, with their own navigation and routes. They apply skills from lessons; they are not listed as competency lessons. Each project has Markdown walkthrough steps, a normal source starter, and one finished example for comparison. `course.json` records titles and paths. The existing Club Connect authoring starter still uses one HTML file for compatibility with the production site. The React preview splits that draft into separate HTML/CSS/JavaScript files while preserving all four project-step IDs and their shared browser-local drafts. New authored projects should use physically separate files. The signup is a fictional demo without a backend or collection of personal information.

Edit `projects/club-connect/*.md` for the walkthrough and `starter.html` or `example.html` for source. Use the shared Playground build to publish changes.

## Bracket Challenge: March Tournament

An additional six-step guided mini-project, built with one editable `index.html` draft:

1. Model eight fictional schools and four quarterfinal matchups with arrays and objects.
2. Render three responsive rounds and seven games with the DOM and CSS.
3. Select winners, advance teams, and invalidate impossible downstream picks.
4. Compute weighted prediction points against fictional completed results (1, 2, and 4 points by round; 12 maximum).
5. Save fictional nickname-based entries in memory and display a sorted sample leaderboard.
6. Debug the bracket, accessibility, and edge cases; explore a React component extension.

The practice project intentionally does **not** fetch real March tournament brackets, collect student identities, persist entries on a server, or offer real multiplayer competitions. Sample entries are in-memory and reset with the preview. The Playground preserves the **source code draft** between steps. The current mini-project checker runs observable browser practice checks only; it does not issue server-verified grades.

Edit the walkthrough in `projects/bracket-challenge/*.md` and the `starter.html` / `example.html` files, and use the shared Playground content build to publish it.

## Classroom component projects

[Class Component Studio](projects/component-studio/01-plan.md) supports a common-component design vote or individually assigned component ownership. Start with a teacher-approved contract, then [build](projects/component-studio/02-build.md), [review](projects/component-studio/03-review.md), and [integrate](projects/component-studio/04-integrate.md). Use the classroom component issue template to record owners and acceptance checks. The independent React Design Lab stays separate.

The bracket project now starts from an empty file; begin with [Create your first HTML file](projects/bracket-challenge/01-scaffold.md). Each step includes a complete cumulative checkpoint.
