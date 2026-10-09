# AUDIT → RECOMMENDATION → IMPLEMENTATION → VERIFY
## Target
- Repository: gantulu/ns01
- File: sample.html
- Primary reference: https://nusantara-cargo.com/
- Audit date: 2026-10-09

## 1. Audit findings
1. The page contains header/navigation, hero, tracking form, shipping-cost form, service cards, feature/statistics section, footer, and a live-chat widget.
2. The document references root-relative assets: /assets/style.css and /uploads/media/* . These will resolve only when the file is served from a compatible site root with those assets available.
3. Tracking and shipping forms depend on /tracking.php and /ongkir.php. Their backend behavior has not been verified.
4. Live chat depends on /chat_api.php with customer_messages and customer_send actions. The static HTML does not implement that API.
5. Responsive CSS breakpoints exist, but no browser/device screenshot or interactive test was available in this audit.
6. The reference website could not be fetched with the available web access. Exact visual/content parity remains unverified; no claim of pixel-perfect matching is made.
7. Some service descriptions and the email address in the sample may not be confirmed against the live reference and should be checked before production use.

## 2. Recommendations
- Preserve the current page structure while improving form labels and metadata.
- Require a valid positive shipment weight and use accessible labels for form controls.
- Make the chat message area a live log for assistive technologies.
- Stop the chat polling interval when the chat panel closes; support Escape to close and restore focus.
- Verify all assets, endpoints, contact details, and content against the live reference before claiming parity.
- Test at mobile, tablet, and desktop widths, plus keyboard-only navigation and form submission.

## 3. Implementation completed in sample.html
- Added meta description and theme color.
- Added explicit accessible labels to tracking and shipping form controls.
- Made shipment weight required with a positive minimum and integer step.
- Added role=log and aria-relevant to the live-chat message region.
- Stop live-chat polling when the panel closes.
- Added Escape-to-close behavior and returns focus to the chat launcher.

## 4. Verification status
- Static file read before and after change: passed.
- Change commit: see GitHub history for this file.
- Browser rendering/responsive visual test: not performed.
- Live PHP form endpoints and chat API: not verified.
- Exact comparison with https://nusantara-cargo.com/: blocked because the reference site could not be fetched by the available web access.
