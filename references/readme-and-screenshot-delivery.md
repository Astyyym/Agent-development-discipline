# Screenshots and README Synchronization

## Trigger and scope

Read this procedure when a change affects visible layout, colors, navigation, pages, controls, or states; when adding or revising interface previews in a README; or before committing or publicly delivering a product with a UI. For backend, skill, or text-only changes that do not affect product visuals, check that existing illustrations remain accurate without recapturing unrelated pages.

During planning, identify affected platforms, pages, visible states, existing images, and README references. Recapture the relevant pages for a local change; cover all affected showcase images for shared navigation, theme, or component changes. Keep evidence for pages absent from the README when acceptance needs it, without adding every page to the public showcase. Recheck the showcase against the current implementation before commit or publication.

## Position in the workflow

> Define capture scope → implement and test → accept real paths in the relevant runtime → capture isolated demo data → inspect every image → synchronize README → review before commit/publication

Screenshots provide presentation and visual evidence. They do not replace interaction, persistence, native capability, printing, or platform acceptance. An unaccepted screen may be captured for diagnosis, but must not be presented as completed product behavior.

## Discover existing project capabilities

1. Read project instructions, project skills, and capture scripts. Confirm actual platform/page support, arguments, dependencies, and output locations. Prefer existing commands; do not assume authorization to create scripts, install tools, or change build workflows.
2. Determine what each script means by desktop/mobile. List desktop web, Windows desktop shell, mobile web, and native Android separately. A mobile viewport or Android User-Agent produces a web screenshot.
3. Keep concrete commands, ports, data roots, page inventories, and device configuration in project instructions or project skills. This reference owns the portable procedure.
4. If a platform lacks automation, capture the real program manually within the authorized scope, or report `blocked` / `unverified`. Do not substitute another platform's screen or interpret a successful script exit as completion across all platforms.

## Confirm data and runtime

- Use generated demo data or a dedicated test data root. Do not read or modify real ledgers, customer records, or production data to create public screenshots.
- Whether starting or reusing a service, query the application's own health/status interface to confirm its resolved data root, running version, and instance identity. Use equivalent runtime evidence when that interface is unavailable. A port, directory name, or launch argument alone does not prove isolation.
- Use controlled local connections. Where supported, Android emulators can reach a loopback service through ADB forwarding; do not expose a service to LAN/public networks or change firewall rules just to capture images.
- Exercise real pairing/login where required, using only the isolated instance and dedicated device/profile. Do not reuse personal browser profiles, real device credentials, or private accounts.
- Before publication, inspect names, contacts, addresses, QR codes, tokens, computer usernames, notifications, and device status bars. Identify demo data in captions. Reject an unsafe image; a promise to redact it later does not establish isolation.

## Platform, page, and state

| Showcase target | Capture and evidence requirements |
|---|---|
| Desktop web | Render the real service in a browser; record viewport, theme, and zoom. |
| Windows desktop shell | Capture the actual application window; confirm source/EXE identity, version, and data root. Browser images cannot prove native dialogs or window behavior. |
| Mobile web | Use a mobile browser or browser device emulation; record viewport and label the source accurately. |
| Native Android app | Run the actual APK on a dedicated emulator or test device; record version and emulator/physical-device identity. A mobile web route is not a substitute. |

Choose deterministic data and states that demonstrate the feature. Wait for data, fonts, and animations to settle; confirm the final route and key content before capture rather than relying solely on a fixed delay. Bring a scrolled region or overlay into view when it is the subject. Match theme/width acceptance to the affected scope without publishing the entire regression matrix in the README.

## Output and individual inspection

- Reuse the project's image directory and stable names. Separate public documentation images from temporary acceptance evidence. Let the project define pixel dimensions, formats, and compression, preserving readable text at the intended display size and reasonable file sizes.
- Inventory images actually generated in this run and match each expected platform/page/state to an output. Old files in the directory are not evidence of a fresh capture; a script's directory-wide count is not the current run's count.
- Verify that every image decodes and has the expected dimensions, then inspect its pixels. Reject blanks, errors, unintended pairing screens, loading placeholders, partial renders, collages, clipping, or sensitive content. Exit codes, nonzero sizes, and DOM state do not replace viewing the image.
- Clean up services, browsers, temporary profiles, device forwarding, and ports created by this task according to ownership. Preserve pre-existing environments and explicitly requested previews according to project rules, reporting anything retained.

## README and pre-commit review

1. Describe the current product. For UI products, place representative real screenshots near the beginning and explain each image's platform and purpose. Put version-by-version history in a changelog.
2. Verify page names, controls, features, versions, and data descriptions against current source and runtime results. Text and images must describe the same version, platform, and state.
3. Programmatically check local Markdown image and HTML `<img>` targets for existence, correct case, and decodability. Check related documentation links, ignore rules, and the intended commit scope for image assets.
4. Review image and text diffs, excluding temporary files, real data, and private paths. Without commit/push authorization, finish with local checks. When authorized, execute delivery separately and read back the remote to confirm that the text references and image targets are available in the same commit.
5. Accept documentation/skill-only changes with document, link, and scope checks. Do not start a capture environment when product visuals did not change.

## Minimum result record

Record platform, page/state, runtime version/instance, isolation evidence, actual command or action, image path, generation result, individual visual-review result, README synchronization result, and uncovered items. Use the existing task record rather than creating a parallel log. Public documents retain only reader-facing images and explanations.

Report `passed`, `failed`, `blocked`, and `unverified` separately, using `deferred` for explicitly postponed work. Generation may pass while visual review remains unverified. Mobile-web success leaves native Android unverified when the APK was not exercised.
