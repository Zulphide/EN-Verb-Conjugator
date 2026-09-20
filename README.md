# English Verb Conjugator

A lightweight static web app designed to help English learners practice verb conjugation through short, timed quiz rounds. The app is built for classroom use and supports multiple verb sets by loading data from a Google Sheet, making it easy to tailor practice for a specific class or unit.

## Overview

This project is a single-page application that:

- presents a verb prompt with a subject pronoun
- asks the learner to write the correct conjugated form
- checks the response against the target tense
- shows the correct answer and allows review through a conjugation reference link
- tracks score and completion for a quiz session

The app is intentionally simple and portable: it runs as a static site with no backend or database, which makes it easy to host on GitHub Pages, a classroom server, or a local machine.

## Features

- tense selection for common English verb forms
  - present
  - past
  - future
  - present progressive
  - past progressive
  - present perfect
  - past perfect
- configurable quiz length
- class-specific verb lists via Google Sheets CSV URL
- custom URL support for alternate vocabulary sets
- score summary after each quiz
- automatic conjugation reference links to Reverso
- responsive layout for classroom and personal use

## How it works

1. User selects a class or custom Google Sheets source.
2. The app fetches a published CSV export from the sheet.
3. Verb rows are parsed into a simple object model using the base form and tense data.
4. The app randomly generates prompts using a subject pronoun and verb.
5. The learner inputs the correct sentence or conjugated phrase.
6. The app compares the answer, displays feedback, and tracks the score.

## Data source

The app expects a Google Sheet with a published CSV export. The typical flow is:

- publish the sheet to the web
- copy the published CSV URL
- paste it into the app’s custom URL field or select a preset class

The app reads the sheet as CSV and expects at least a header row plus data rows. It looks for a base verb field such as `base`, `infinitive`, `present`, or `verb`.

## Local usage

Because this is a static site, there is no installation step or package manager required.

### Option 1: open directly

Open `index.html` in a browser.

### Option 2: serve locally

From the project root, run:

```bash
python -m http.server 8000
```

Then open:

```text
http://localhost:8000
```

This is the recommended option because it is more reliable for browser fetches to external spreadsheet data.

## Project structure

```text
.
├── index.html
├── README.md
├── LICENSE
└── (optional future assets: styles/, scripts/, data/)
```

## Scope and limitations

This app is intentionally focused on a classroom learning use case. It does not currently include:

- user accounts or saved progress
- a backend API
- persistent analytics
- multi-language support
- teacher dashboards
- offline vocabulary packs
- advanced grammar explanations

## Suggested improvements

These improvements fit the app’s current scope without changing its lightweight static nature:

### High-value improvements

- local fallback dataset: if the Google Sheet is unavailable, the app should still work with a bundled sample list
- stronger CSV parsing: use a proper CSV parser that handles quoted entries and commas more reliably
- duplicate filtering: avoid repeating the same verb multiple times in a single quiz
- difficulty modes: beginner/intermediate/advanced by verb complexity or irregularity
- answer normalization: accept minor spelling or punctuation variations without unfairly marking correct answers wrong
- accessibility polish: better focus states, screen-reader labels, keyboard shortcuts, and larger touch targets

### Good feature additions

- practice by tense family or verb category
- “show hint” and “reveal answer” options
- progress history using localStorage
- practice mode vs. quiz mode
- optional pronunciation or example sentence support
- score streak tracking and review summaries

### Nice-to-have classroom features

- class selector and saved lists per section
- review of missed verbs after the quiz
- exportable score history
- printable worksheets or vocabulary decks

## License

This project is distributed under the MIT license. See [LICENSE](LICENSE) for details.

## Notes

This project was built as a practical teaching tool rather than a full web application framework. Its strength is simplicity, speed, and easy customization for classroom vocabulary practice.

