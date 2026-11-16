# jerettdeguzman.github.io

My engineering portfolio, live at **https://jerettdeguzman.github.io**.

Plain HTML and one CSS file. No framework, no build step, nothing to install
except Git and Python. GitHub Pages publishes whatever is on the `main` branch,
usually within a minute of a push.

## What's where

```
index.html             Home: summary, project list, competencies, education, contact
experience.html        VEX U, bar back, research paper
projects/*.html        One page per project (all share the same layout)
images/                Every image on the site
styles.css             All styling. Colors and fonts are variables at the top.
resume.pdf             The PHONE-FREE robotics résumé, linked from every header
```

The source documents (printed portfolio, master `.tex`, notebook, lab
calculations) live in `../reference/`, outside this repo on purpose, so they
can't be committed. Keep it that way. **This repo is public.**

## Preview changes before pushing

From this folder:

```
python -m http.server
```

Open http://localhost:8000. This serves the folder to your browser exactly the
way GitHub Pages will. Stop it with Ctrl+C. To check phone layout, open the
browser's dev tools (F12) and turn on the device toolbar (Ctrl+Shift+M).

## Publish changes

```
git add -A
git status            # read this list: nothing private should be in it
git commit -m "Say what changed"
git push
```

## Change a sentence

Open the page, find the sentence, edit it, save, preview, publish. Two habits:

- Put `&nbsp;` between a number and its unit (`15&nbsp;V`) so they never split
  across lines.
- Write `&amp;` for `&` in HTML (`Power &amp; Feedback Control`).

## Change a color or font

Edit the variables at the top of `styles.css` (section 1). Every page uses
them, so one edit changes the whole site.

## Add a project page

1. **Image(s).** Put two images in `images/`, named with a short prefix for the
   project (e.g. `pp_sim.png`, `pp_grasp.jpg`). Shrink photos to about 1000 px
   wide first; anything under ~200 KB is fine.
2. **Page.** Copy an existing page, e.g. `projects/trajectory.html`, to
   `projects/pick-and-place.html`. Then edit, top to bottom:
   - `<title>` and `<meta name="description">`
   - the link-preview block right below them (`og:title`, `og:description`,
     `og:url`, `og:image`): copy the title and description, set the URL to the
     new page's full address, and point the image at one of its images (use a
     full `https://jerettdeguzman.github.io/images/...` address, and a .png or
     .jpg, not .webp)
   - the kicker (`kicker-left` = category, `kicker-right` = term · course)
   - `<h1>` title, the `challenge` sentence, and the `tools` line
   - the four metric boxes (value + label)
   - the two figures: `src`, `width`/`height` (the image's pixel size), `alt`
     (describe what the image shows), and the caption. Add `class="frame fit"`
     for diagrams and plots so nothing gets cropped; plain `class="frame"`
     for photos.
   - **What I did** bullets, then **My role / Result / Takeaway** (swap
     "Result" for "Debugging" if that's the real story)
3. **Home page card.** In `index.html`, find the comment above the project
   list. Copy one `<li class="project-card"> … </li>` block, paste it at the
   **top** of the list (newest/most relevant first), and change the link,
   thumbnail image, kicker, title, and one-sentence description.
4. Preview, check at phone width, publish.

## Update the résumé

1. In the master `.tex`, compile the website copy **without the phone number**
   (set `\phonefalse` if you added that toggle).
2. Before it goes in this folder, open the PDF and confirm there's no phone
   number in it.
3. Save it here as `resume.pdf`, replacing the old one (same name, so every
   link keeps working).
4. Publish. If the old version still shows, hard-refresh (Ctrl+F5).

## Rules for this site

- No phone number anywhere, including inside `resume.pdf`.
- Nothing from `reference/`, lab reports, transcripts, or W-2s.
- No made-up metrics, quotes, or testimonials. If a number isn't in my notes,
  it doesn't go on the site.
