# Gaargi Pandit portfolio

This is an HTML and CSS-only portfolio. Each project keeps its own visual theme—including its typography, palette, backgrounds, layouts, buttons, and galleries—while `shared.css` provides the site-wide navigation, sticky header, footer, scrollbar, keyboard focus treatment, and image-preview overlay.

## Consistency contract

- Project CSS owns the project's colors, type, backgrounds, decorative effects, and content layout.
- `shared.css` owns `.site-header`, `.site-footer`, `.skip-link`, `.preview`, and `.close`. Do not redefine those components in a project stylesheet.
- Load the project stylesheet first and `../shared.css` last, so the shared interaction and accessibility rules remain dependable.
- Reuse established content classes such as `.mybanner`, `.brief`, `.drawings`, `.renderings`, `.photo-gallery`, `.thumb`, and `.portrait` when they fit. The project's CSS can still make those sections look unique.
- Keep the site HTML and CSS only. Image previews use native HTML popovers and do not require JavaScript or add entries to Back-button history.

## Add a project

1. Copy `generic_one_image_project` and rename the folder.
2. Keep project images inside that folder's `assets` directory.
3. Update the page title, description, headings, copy, image paths, alternative text, and theme variables.
4. Preserve the shared header, skip link, footer, and stylesheet order from the template.
5. Add one unique preview ID for each full-size image. The trigger's `popovertarget` and preview `id` must match.
6. Add the project to the main portfolio when it is featured, then to the appropriate chronology and category pages.
7. Check every link and image path using the exact capitalization of its file or folder.

## HTML-only image preview pattern

```html
<button
  type="button"
  class="preview-trigger"
  popovertarget="artwork-1"
  popovertargetaction="show"
  aria-label="Open image preview: Describe the artwork"
>
  <img src="assets/artwork-1.jpg" class="thumb" alt="Describe the artwork" />
</button>

<div
  id="artwork-1"
  class="preview"
  popover="auto"
  role="dialog"
  aria-label="Image preview"
>
  <button
    type="button"
    class="close"
    popovertarget="artwork-1"
    popovertargetaction="hide"
    aria-label="Close image preview"
    autofocus
  >&times;</button>
  <figure class="preview__figure">
    <img src="assets/artwork-1.jpg" alt="Describe the artwork" />
    <figcaption class="preview__caption" aria-hidden="true">
      Describe the artwork
    </figcaption>
  </figure>
</div>
```

The caption repeats the image's `alt` text and appears when the image is hovered. Keep both texts identical. The browser closes an open preview with its close button, the Escape key, or a click outside the image. Keep the preview markup outside `<main>` as shown in the template.

Use lowercase `index.html` consistently. File and folder names are case-sensitive when the site is published.
