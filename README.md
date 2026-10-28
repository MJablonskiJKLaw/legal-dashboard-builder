# Legal Dashboard Builder

Legal Dashboard Builder turns a legal document (a memorandum, a legal opinion, an analysis or a pleading) into an interactive web page your client will actually read. The page opens with the key facts, walks through the findings with charts, timelines, option and risk matrices, and links every quotation to the full text of the document or of the source it comes from.

The result is a single, self-contained HTML file. You can send it, open it offline, or publish it as a Claude artifact and share a link.

The builder runs inside Claude as an artifact. Claude reads the document on the account of the person using the builder.

**Get started:** download `legal-dashboard-builder.html` and publish it as an artifact on your Claude account (see [Install the builder](#install-the-builder) below).

---

## Where it comes from

At our firm we used a Claude skill to present legal opinions and memoranda to clients as visual dashboards rather than long Word files. The builder packages that idea as an artifact anyone can use, without the firm’s branding: you bring the document, your own design system and your own sources.

---

## What you need

- A Claude account (claude.ai or the Claude app). The builder asks Claude to read the document, so usage counts towards the limits of the person using it.
- The document as PDF with a text layer, Word (.docx), Markdown, plain text or HTML. Scanned PDFs need OCR first.

---

## Install the builder

1. Download `legal-dashboard-builder.html` from this repository.
2. Open a chat with Claude, attach the file and ask:

   > Publish the attached file legal-dashboard-builder.html as an artifact without changing it. Declare the capabilities it uses: `sample` and `downloads`.

3. Open the artifact and start with step 1 below. If you want colleagues to use your copy, share it: on Free, Pro and Max plans use **Publish**. On Team and Enterprise plans artifacts are shared within the organisation by default; an owner can enable external sharing so that anyone with the link can open it.

Opening the HTML file directly in a browser, or hosting it on GitHub Pages, will not work: the builder needs Claude to read the document and shows a notice when Claude is not available.

---

## How to work with the builder

The builder has four steps: **Material → Plan → Quotations → Dashboard**. Your work is kept in your browser, so you can close the page and come back to it.

### Step 1: Material

1. **Load the document.** Drop the file, choose it, paste the text, or load a whole folder. With a folder or several files (or a .zip), the builder picks the main document by its name (e.g. “opinion”, “memorandum”, “analysis”) and treats the other files as full texts of the sources it cites. You can change which file is the main one.
2. **Fill in the details:** the dashboard title (or leave it to Claude), the recipients, and the language of the dashboard (English, Polish, German, French, Spanish or Italian).
3. **Add a legal disclaimer.** Insert the standard one in the dashboard’s language, type your own, or load it from a .md, .txt or .docx file.
4. **Choose the design.** Start from one of four ready-made styles, or give the builder your own design system:
   - describe it in a few sentences,
   - upload a design-system skill (`SKILL.md` or a `.skill`/`.zip` package),
   - upload a design export as `.zip`,
   - or upload a single CSS, JSON or Markdown file with your tokens.

   The builder takes colours, fonts, corner radius and the brand voice from it. Fonts included in a package are embedded in the dashboard; a logo found in the package is used in the header. When your own system is loaded, the ready-made styles are switched off.
5. **Add images** if you want them: backgrounds for the opening and chapter screens, a logo, or figures. Use only images you have the right to publish.
6. Click **Build the plan**.

**Your design system is an artifact on claude.ai?** A published page cannot read other artifacts, so get a .zip first: open a chat with Claude, paste the link to the design artifact and ask Claude to prepare a .zip with its design system (colour tokens, CSS, fonts and logo). The builder shows this request ready to copy.

**Your document links to its sources?** The builder reads hyperlinks from Word, PDF, HTML and Markdown files and attaches them to the matching references. To get the full texts behind those links as well, open a chat with Claude, attach the document and use the request shown in the builder: Claude fetches the sources and returns one .zip with the document and a Markdown file per source. Load that .zip in step 1.

### Step 2: Plan

Claude proposes the structure of the page: a guiding idea, then sections of different types (opening, key findings, chapter screens with images, text, key numbers, charts, timelines, tables, flow diagrams, comparisons, the argument, sources, options matrix, risk matrix, next steps, caveat).

You can:

- drag sections to change their order, or move them with the arrows,
- select two or more sections and merge them, or split a long one in two,
- change a section’s type, title, content points and image,
- delete sections or add new ones,
- leave a note for Claude on any section and on the page as a whole,
- adjust colours and fonts in the side panel.

**Rebuild the plan** sends your structure and notes back to Claude. Every rebuild is kept as a version (v1, v2…), so you can go back.

When the plan is right, click **Check quotations**.

### Step 3: Quotations

Every quotation is compared with the text of the document and marked:

- **green:** identical to the document,
- **yellow:** close to the document, but the wording differs (the builder shows the closest passage and can replace the quotation with it),
- **red:** not found in the document.

For each quotation you can correct the text and its location, see it in context, leave a note for Claude, **Accept** it, or remove it from the dashboard. **Correct quotations with notes** asks Claude to find the verbatim passage that matches each note.

For each source you can correct the citation, add a link to the official source, and attach its full text: pick a file loaded in step 1, upload one, or paste the text copied from a website. With a full text attached, quotations are also checked against the source itself, and the dashboard can show them in the source rather than in the document. Choose this at the top of the step.

The **Deploy the dashboard** button becomes active once every quotation and every reference has been decided. None of the markings from this step appear in the dashboard: the client sees only accepted quotations and accepted links.

### Step 4: Dashboard

Claude writes the final content of each section. Check the result in the preview (desktop and mobile views, full screen), then **Save HTML file** or **Copy HTML**.

To share the dashboard as a link, upload its HTML file to a chat with Claude and ask Claude to publish it as an artifact.

---

## What the dashboard contains

- A header with your logo, the menu and a full-screen button.
- An opening screen with the title, recipients, document date and a panel of key facts.
- The sections from your plan, with charts, timelines, tables, diagrams and matrices drawn from the figures in the document.
- Quotations in framed blocks. Clicking one opens a side panel with the passage, its location and citation, the full text of the document or of the source with the passage highlighted, and a link to the official source where you accepted one.
- A footer with your disclaimer and a note that the page presents the document and does not replace it.

---


## Privacy and confidentiality

- The document, the sources and your notes are sent to Claude on the account of the person using the builder. The builder itself has no server and stores nothing outside the browser.
- Work in progress is kept in the browser’s local storage. **New project** clears it. Use it after working on a shared computer.
- The generated dashboard contains the full text of the document, and the full texts of any sources you attached, so that quotations can be shown in context. Treat the file like the document itself.

---

## Limits and good practice

- Claude reads up to about 120,000 characters of the main document. Longer documents are truncated, and the builder tells you so.
- A single source text is kept up to 400,000 characters.
- Browser storage holds a few megabytes. A large folder of sources may not survive a page reload; load it again if needed.
- The builder checks quotations against the texts you give it. It cannot check whether a source you did not attach says what the document claims. That check stays with the author.
- Fonts embedded from a design system must be licensed for embedding in files you share. Some literature is published under licences that restrict redistributing the full text.
- The dashboard summarises a document; it is not legal advice on its own. Read every section against the document before sending it.

---

## Licence

MIT. See [LICENSE.md](LICENSE.md).
