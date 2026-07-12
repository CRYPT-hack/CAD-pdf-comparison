# Redline Review

Open `index.html` in Chrome or Edge. Load the previous (A) and revised (B) PDFs, choose the pages to compare, then select **Compare drawings**. All PDF rendering and comparison occurs locally in the browser. The page loads pdf.js and jsPDF from public CDNs, but it does not upload drawings to a server.

## Professional drawing-review workflow

This version is deliberately modelled on commercial drawing-comparison workflows:

- **Page align** for revisions exported with the same page position.
- **Auto align** for small position and scale changes. It measures drawing content rather than white paper, then applies a translation and limited scale correction.
- **Manual alignment** for difficult drawings: choose the same three stable drawing points in both PDFs. This produces a full affine transform (translation, scale, rotation and skew) and is the reliable fallback when automatic registration is not good enough.
- **Select compare window** to exclude a title block, notes, or other noisy parts of every selected sheet.
- **Cloud markup** output, a side-by-side review, a coloured overlay, change navigation, a CSV change list and a marked-up PDF export.

## Detector behaviour

The detector compares binary drawing ink after alignment. It permits a 2–3 px match tolerance so normal PDF anti-aliasing does not become a change. It only bridges one empty 4 px cell between nearby unmatched marks; it does not repeatedly expand the full difference grid, which was the source of the previous vague, full-sheet regions.

The tag list is intentionally conservative. It includes tag-like text only when the tag lies within a detected cloud; date strings, short text fragments and common headers are excluded.

## Recommended operating procedure

1. Start at **High** detail, sensitivity **6**, Auto alignment, and Ignore markup enabled.
2. View the **Overlay**. Common ink is dark, previous-only ink is teal, and revised-only ink is red.
3. If the overlay has doubled lines across the sheet, choose **Manual**, set three points on stable geometry (not text or a cloud), and compare again.
4. Use **Select compare window** when a title block or general notes are creating irrelevant changes.
5. Increase sensitivity to 8–10 only for very small termination-table text; this also makes the detector more likely to include faint print artefacts.

This is a PDF-image comparison tool. Native DWG object comparison remains more semantically accurate when the original DWG files are available.
