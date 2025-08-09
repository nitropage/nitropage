# Changelog

## 0.68.3

### Patch Changes

- a5fbec0: Added server error handling for several "bad request" situations related to SolidStart.
- 9806c6a: The `Section` blueprint shadow is now rendered with `box-shadow` and only switches to the filter-based `drop-shadow` strategy, if `Top Mask` or `Bottom Mask` is enabled.
- e4fb588: Fixed images in the media library not being scaled properly.
- 36685d5: Fixed a bug that caused the link widget of richtext editors in the sidebar, to be behind the sidebar.
- 11512da: Elements in the `cta` slot of the `Header` blueprint will now only be rendered once. Previously they rendered twice (for mobile and desktop breakpoints).
- 4d4f61d: CSS Module files are now manually chunked to prevent frames of unstyled content in certain situations.
- 0a6b7e6: Added a default `prisma.config.ts` file to the starter kit, as a first preparation step towards Prisma 7.
- 0c07f4a: Fixed a bug that prevented the creation of new fonts.
- a95a27a: Updated dependencies.
- 36237a6: New anchor links created in richtext fields now properly jump to the corresponding id, instead of opening in a new tab.
- 5e67125: Fixed an issue that resulted in labels ending with single characters like `Padding Y` to be rendered as `Padding`.

## 0.68.2

### Patch Changes

- 9fb0d85: Hidden the Home button in the Dashboard, when the demo mode is enabled via `VITE_NP_DEMO=1`.
- bf107d1: Fixed element preset create and delete actions, only taking effect after saving the editor.
- 00132d5: Saving the editor now doesn't cause all elements inside layout slots to be rerendered.
- 0272f9b: Fixed an issue in the editor, that caused slots inside layouts not to be rendered with `display: flex`.

## 0.68.1

### Patch Changes

- b0f2f9c: Fixed page and layout counts in the dashboard not being narrowed by project.
- 949aa07: Prevented the `<link>` tag for the global css, from being rendered twice in production.
- 98bfa8a: Column titles in the dashboard will now be hidden, if there are no entries.
- db3a193: Fixed `Image` component styles not being server rendered during development.

## 0.68.0

- [Announcement blog post](https://nitropage.org/blog/nitropage-v0-68)
- [Update Guide](https://nitropage.org/docs/update#v068)

### Minor Changes

- a0b7bc7: Drag and drop operations can now be cancelled by pressing the ESC key (#154).
- 6be4cd6: Added a new `category` option to the blueprints. The blueprints can now be filtered by category, during the element creation (#62).
- 2407bdf: Blueprint slots are now rendered by default with `display: flex` and a flex direction according to the `direction` prop, which reduces some unnecessary boilerplate. For special use cases, this default can simply be overwritten with CSS.
- 322811d: Added the publication date to the page and layout lists in the dashboard and sorted pages by url.
- 94684da: Added a new `Clean up revisions` feature in the page revisions tab, which can be used to delete old revisions in bulk (#74).
- 4914eb0: Improved precision when scrolling in number inputs and when using the scroll wheel to change the zoom factor.
- 8a7f649: Updated dependencies.
- 0168444: Editor changes not stored in page revisions, are now saved fine-grained (#57). Working on multiple pages in parallel? Piece of cake!

  E.g. if you change a `Padding` setting in a `Preset`, only this setting will be saved, unchanged settings will not be overwritten. This applies to:
  - Colors
  - Fonts
  - Presets
  - Project blueprint defaults
  - Project settings

- 0b8cfed: Aligned the colors of the scrollbars and related elements. Also narrowed the scrollbars to gain some extra space for the editor.
- 7e7390d: Completely overhauled the `Columns` blueprint and added several new settings for common use cases.
- 6510627: Added a new hint on first element creation, guiding new users.
- f88364a: Added several new keyboard shortcuts (#89):
  - Unfocus / Cancel: `Esc`
  - Select parent element: `Backspace`
  - Zoom in / out: `+` / `-`
  - Tools e.g. **S**elect: `S`

- b571603: Deleted the `Eleminate` humor.
- 96dab75: Greatly reduced the time to save pages, by optimizing the database writes in key areas. New page revisions are now created on every save, not only after publication.
- 462bfc0: Added new `defaultValue` and `optional` options to the `textData` blueprint data helper (#151).
- d608782: Slightly visually overhauled the revision list and unpublish button, added more obvious icons, added tooltips and implemented missing logic for the deletion of the currently active revision.
- 28f223a: Reordered the toolbar items and moved the primary tools to the right, closer to the sidebar.
- 8dec391: The way in which changes are synchronized between the editor's viewport and the sidebar has been completely revised (#119).

  In previous versions, every change in the editor required an expensive comparison between the states of the viewport and sidebar. This meant that the synchronization slowed down relative to the size of the page (e.g. number of elements). Now most changes are applied fine-grained, without the need for the expensive comparison.

  Also the viewport no longer unnecessarily re-renders all elements after a new page revision has been created. Smoother saving of the page!

- fa57f5a: Added open and close animations to dialogs.
- 2614103: Layout elements are now visually indicated with an icon in the element breadcrumbs.
- 65b8610: Renamed `Spacing` settings in `Flex` blueprint to `Gab` to better conform with CSS.
- 0ee8d63: The `np blueprint <name>` cli now recursively creates missing directories, if the `<name>` is a path.
- da86ebf: Added a `Preview` button to the toolbar, which can be used to preview the page before publication.
- 91d5b6a: Fine-tuned user interface styling of element related tools (create, select and move) and slightly improved the detection of the cursor position.
- e85ab5a: Increased the default server build target from `es2020` to `esnext`.
- a3cefa4: Deprecated the `cssMemo` API. It can easily be recreated by combining Solids `createMemo` and NPs `useCss`.
- 7b1158e: Overhauled confirmation dialogs, added context specific titles and reordered the buttons to "primary right".
- a2be1f2: The revisions list restore buttons can now be navigated with up/down arrow keys (#74).
- 068c6b5: Added a new `Edit Layout` button in the editor, shown when a layout element is selected. The button opens the related layout in a new editor tab.
- 7fa4c91: Added indicators to the page save and publish buttons, showing if there are unsaved modifications (#138). Trying to leave the editor with unsaved modifications, will now ask users if they wanna save first.
- 7b3d5d0: Blueprint titles inherited from filenames, are now formatted with Title Case, eg: `contactGrid` becomes `Contact Grid"`. If the filename is `index`, the parent folder name will be used instead. Options in `selectData` also are formatted with Title Case.
- 9c442d4: Added count badges for projects, pages, layouts, elements and fonts.
- be0fe4e: Used layouts are now reloaded, after saving in the editor.
- 5d7cf48: Slightly adjusted the design of `Element Breadcrumbs`, `Blueprint Selection` and `Element Settings Header`.
- 01b987c: Changed the default value of `Justify Content` to `Flex Start`, in the `Flex` blueprint.
- b455940: Improved editor support for small monitors and smoothed out editor loading visuals.
- 38334e5: Visually overhauled the editor sidebar header elements and added labels to the buttons.
- d6f8271: The page zoom can now be controlled by pressing Ctrl and using the scroll wheel.
- 55bed1a: Slightly adjusted the `Image` and `ImageContainer` components:
  - Migrated component styles from `useCss` to css modules
  - Removed `width`/`height` props from `ImageContainer`
  - The `media` prop is now optional and will fallback to placeholder data

- a1e68fe: Cleaned up obsolete code regarding page-level blueprint settings and removed the unused `blueprintDefaults` column of the `NitroPageRevision` db table. Make sure to update your database schema with `npx/pnpm np update -m`.
- 80d32e8: Visually overhauled the dashboard one more time and reduced visual jank in button loading spinners.

### Patch Changes

- 23f839f: Fixed the editor viewport not being focused after confirming the element deletion dialog.
- 9f084e9: The revision dates and editor viewport zoom value now use tabular width glyphs.
- d6f72e4: Fixed a bug that caused the `Video` blueprint to start in fullscreen on mobile devices.
- c986e89: Hidden the slots section for elements using layouts without slots.
- 2a8c62c: The `Image` blueprint now uses `figure` and `figcaption` tags (#144).
- 2d49695: Fixed the slot labels in the editor viewport, not using the proper font family.
- 59ceb01: Fixed an issue that caused upload buttons in the editor to be rendered with the wrong font family.
- 77bc6b6: Elements that are created in slots with fixed blueprints, are now selected after creation, just like elements in free slots.
- 6da8eb5: Renamed the `Tag` blueprint to `Badge` to better indicate its purpose and made the `Link` setting narrow.
- 77f7813: Fixed a bug that caused overflowing content in collapsible areas being unreachable with the cursor. For example this was the case with richtext editor dropdowns in element settings. Also sped up the collapse animation by 50ms.
- 5cd710e: Moved back the starter kit Prisma schema location from `./prisma/schema` to `./prisma`, to better follow the Prisma guidelines.
- 1a492d5: Fixed an issue that caused drag and drop indicators in vertical blueprint slots, to be rendered horizontally in some cases.
- e030900: Adjusted ui transitions across the admin.
- c26e724: Fixed the scroll restoration sometimes jumping to the wrong position, when quickly switching between tools after scrolling.
- 7b00a3f: Fixed the editor failing to save, because of invalid elements, related to deleted layouts or layout slots.
- 861a2c1: Fixed sidebar header shadow being shown in non sticky situations under Chrome.
- 3f07105: Lists in `Text` and `Markdown` blueprint now have the same spacings between the items.
- b234123: Disabled text selection in buttons across the admin dashboard and editor.
- 6389423: Fixed a bug that caused numeric inputs to activate the respective blueprint setting, even if their value has not been changed.
- 717e7ba: Fixed a bug that resulted in a `Computations created outside a createRoot or render will never be disposed` warning in the browser devtools, when closing the page editor.
- 6d2c830: Deleting a layout slot now only deletes elements directly placed inside of them, and not their entire history. Not all element versions are necessarly related to the deleted layout slot and unrelated element versions should stay alive.

## 0.67.2

### Patch Changes

- a729029: Fixed passive page elements being rendered with wrong settings after submitting forms.
- 5734a85: Updated dependencies.
- 8326183: Added bottom paddings after project and page lists in the dashboard.

## 0.67.1

### Patch Changes

- 9e2a170: Fixed broken video playback and wrong seek information under Chrome, by implementing range based video streaming for local file storage.

## 0.67.0

### Minor Changes

- dc4a40c: The richtext editor now handles missing or invalid data keys more carefully and avoids breaking the whole blueprint component.
- 646d32e: The `Heading` blueprint now uses a suitable `preset` according to the `level` setting, if no `preset` is selected.
- 6f7e62d: Added dotenv to the starter kit `start` script, to prevent environment variables from being registered too late, depending on the user code structure.
- 3085471: Update dependencies, including Tailwind 4.1, Prisma 6.5 and Sharp 0.34.

### Patch Changes

- 1042841: Fixed default values for blueprint settings not being reloaded after making code changes to a blueprint.
- acd1994: Fixed richtext not being able to be edited inside html label elements.

## 0.66.2

### Patch Changes

- 04646a1: Fixed a bug preventing server functions in `customServerFunctions` from not being matched in some cases.

## 0.66.1

### Patch Changes

- 4ac2961: Reverted import aliases in blueprint data helpers to fix broken types.
- d0e0b14: Only output the server welcome message once and don't show it in the cli.
- 242e45a: Use new cli logo from `nitropage` during `create-nitropage` scaffolding.
- 99ba6c1: Added `nitropage` and `@npio/*` to nitro esbuild to fix build errors.
- cf13f74: The welcome message on the server now shows the logo and logs an admin url according to the dev/prod mode.
- 190fadb: Removed dev request logging, as the new tanstack server function ids are very long and verbose.

## 0.66.0

### Minor Changes

- e4f14b4: Refactored the whole internal directory structure and moved `@npio/internals` back to the core. Server related public API once again can be accessed via `nitropage/server`. `@npio/server` remains available, but is deprecated and will be removed in a future version.
- 52f5c69: Added a default request body limit of 10 MB and a new `customServerFunctions` middleware option for server functions with different requirements. Renamed `parseMultipartFormData` of `@npio/filesystem` to `parseFormDataStream`.
- a7abbd8: **BREAKING CHANGE**: Reorganized the starter kit folder structure and added a plugin for improved server error handling.
  - Introduced a new `src/runtime` folder for Nitropage-specific plugin-, middleware- and config files.
  - Moved the starter kit `button` data helpers and blueprint to `src/blueprint/button`.
  - Moved the `createMiddleware` function from `nitropage/server` to `nitropage/middleware`.
  - Moved all `nitropage/cli` API's to `nitropage/server` and removed `nitropage/cli`.
  - Added a plugin with improved server error handling, compatible with SolidStart and Solid Router forms.
  - Starting the dev server doesn't output the whole configuration anymore. Use the new `np config get` cli command instead.

### Patch Changes

- 5704a8f: Added a proper README.md to the starter kit and simplified the `server.config.ts`, by moving the default values and env variables to the Nitropage core.
- 25094fa: Added a file watcher that restarts the dev server, when you make changes in `runtime/plugin.ts` and `runtime/server.config.ts`.
- 10b0724: Disabled `margin` settings of the `Heading` blueprint during element operations.
- ee8fd20: Disabled verbose database `query` logs in the dev server and instead added a new `database.prisma` section in `server.config.ts`, allowing users to customize the logging.
- Updated dependencies [e4f14b4]

## 0.65.1

### Patch Changes

- 04c2663: Fixed `Cannot read properties of undefined` error while reading `import.meta.env.PROD` during project scaffolding.

## 0.65.0

Nitropage now ships with `SolidStart` v1.1, `Vite` v6.1 and `Tailwind CSS` v4 🥳! Every dependency is up to date again 🎉.

> If you wanna upgrade a `local install` (non-docker) project, check out the general [Upgrade Guide](https://nitropage.org/docs/guides/upgrades) and especially the [v.65](https://nitropage.org/docs/guides/upgrades#v065) specific steps!

### Minor Changes

- c30941a: Increased required node version of the starter kit to >=v22.
- 39842f9: Upgraded Tailwind CSS to v4.0.
- c177fc5: Updated dependencies, especially `@solidjs/start` v1.1 and `vite` v6.1.

### Patch Changes

- 6e3843a: The layout slot dropdown will now automatically close after creating or selecting.
- 567e650: Fixed an issue that caused the last element selection indicators to wrongly stay visible after certain mouse interactions.
- 8840be3: Added `Font` setting to `Markdown` blueprint.
- 5aaada4: Cleaned up the cli demo seed and added additional example elements.
- bba1b28: Fixed the editor not starting in `Create` mode for new/empty pages.
- d6a0163: The production server now shows a welcome message on start, if no users exist. And 404 Not-Found pages show a link to /admin, only during dev.
- 4a611cf: Fixed an issue that caused the element creation to get stuck in an unresponsive state, were it didn't react to mouse clicks.
- 7e60a06: Fixed a regression, causing empty richtext editor fields to not hide in preview mode.

## 0.64.3

### Patch Changes

- 942fc21: Updated dependencies.
- 9616b58: Replaced references to nitropage.com with nitropage.org.

## 0.64.2

### Patch Changes

- 24872d4: Fixed a bug in the `Image` component potentially causing an error during page navigations, if the image is pointing to an invalid src.

## 0.64.1

### Patch Changes

- 0000715: Made `Card` and `Flex` blueprints passive and added lazy-loading for `LogoGrid` images.
- fc84365: Fixed a regression introduced with the new loading sections (6c5f5b2), causing flickering during page navigations.

## 0.64.0

### Minor Changes

- badf6dd: Added basic support for variable fonts and fonts can now be loaded via a CDN (https://fonts.coollabs.io/).
- cf8c714: Fine tuned the UI indicators of horizontal element create and drag operations.
- 6c5f5b2: Improved server response times and reduced editor jank with additional loading sections (Suspense boundaries) and by incorporating transactions in element move operations.

### Patch Changes

- 10141c8: Removed `createdAt` and `updatedAt` fields from the public data of layouts and revisions.
- bbdf6d0: Updated dependencies.

## 0.63.0

### Minor Changes

- ec882e4: Slightly reworked the responsive widths and spacings of the `Narrow` and `Documentation` blueprints, and introduced a new `Extra Wide` setting for the `Narrow` blueprint.
- 9bff9a3: Removed odd extra padding at the bottom of the `Feature Grid` and slightly optimized the mobile layout.
- a9948d6: Implemented new `autoplay`, `loop` and `mute` settings for the `Video` blueprint.
- 484b9f1: Reworked the `social` slot of the `Footer` blueprint. Elements in the slot now are listed horizontally, making it a better place for its intended use case: social icons.
- 6fc6c54: Updated the dependencies.

### Patch Changes

- ef59ba3: Fixed stylesheets being rendered as escaped html on the page, caused by a security fix in Solid v1.9.4.

## 0.62.2

### Patch Changes

- 81ebeda: Slightly, visually overhauled the fonts section in the editor sidebar.
- f74c5ba: Fixed a bug that prevented `otf` fonts from being uploaded.
- 71c876a: Added `aria-hidden` to the honeypot field of the `Footer Newsletter Form` blueprint to exclude the field from screen-readers.
- 99395a0: The border of the active `FAQ` blueprint item now uses the `Line Color` setting, instead of `Highlight Color`.
- e6ca061: Disabled the project domain field in demo instances.
- 0afdb4a: Fixed a bug in the `Section` blueprint that resulted in child elements not being selectable in some cases.
- 241eed0: Demo instance users will now instantly be redirected to the first project details.
- 585e4a0: Made the login and welcome forms more responsive.
- Updated internal dependencies [f74c5ba]

## 0.62.1

### Patch Changes

- c3ad30d: Removed a page render optimization from v0.62, that sometimes resulted in visual jank when navigating between pages with similar elements. Maybe it will be brought back as an opt-in project setting in a future release (https://codeberg.org/nitropage/nitropage/issues/130).
- 459f4e0: Fixed a bug that resulted in the page sometimes being rendered without waiting for presets and project defaults.

## 0.62.0

### Minor Changes

- 5e24c7d: Intensely overhauled the user interface:
  - Redesigned color palettes and applied colors consistently
  - Aligned the design of interactable elements
  - Improved element drag and drop UX
  - Reworked login, welcome and dashboard screens
  - Reduced visual clutter
- 116dfb1: Added `markup` (html) to the language options of `textData` and updated related starter blueprint settings. (https://codeberg.org/nitropage/nitropage/issues/123)
- 964130e: Added the new `HTML` blueprint to the starter kit.
- cc6db05: You can now double-click on a blueprint during element creation, to directly confirm your selection. (https://codeberg.org/nitropage/nitropage/issues/111)
- cebc41c: Visually overhauled editor buttons and the color presets UX.
- b289716: **BREAKING CHANGE**: Renamed the Slot `editorPadding` prop to `expand` and implemented a new `expand` utility css class that can be used to add temporary padding to blueprint elements.
- 837d1af: Users can now create reusable **layouts**, consisting of multiple elements and other layouts. Such layouts can also have areas for parent-provided content, commonly known as slots.

  > `Header`, `Main` and `Footer` slots on the page root are deprecated! Instead the blueprints listed below now include a `Html Tag` setting, allowing semantic HTML maximalists to specify any tag they want.
  >
  > - Card
  > - Flex
  > - Footer
  > - Header
  > - Style

- a1c220c: Requests to urls ending with a "/" will now be redirected to non-slash url variants. (https://codeberg.org/nitropage/nitropage/issues/124)
- 1d45c9a: The welcome wizard now automatically creates a project and shows a welcome message to new users.
- 7f2f291: Deprecated blueprint slot options `max`, `acceptBlueprint`, `acceptParentType` and `acceptParent`, and removed the options from the starter blueprints.

  Some of these options might come back, but need to be reworked. The follow up discussion can be found here:
  https://codeberg.org/nitropage/nitropage/issues/128.

- f72116a: You can now click on the already active `Elements` tab in the editor, to deselect the current element and directly jump to the Elements Overview.
- eb1b6fe: Replaced the text underline of the `Header` blueprint links with a cleaner border.
- be9bf61: **BREAKING CHANGE**: Renamed `name` and `data` props of `Rte` and `Slot` components to `key`.
- 4bb20b9: **BREAKING CHANGE**: Moved the `Rte` `path` prop functionality into the existing `key` prop and overhauled the approach to specify such paths. The new path function receives an object argument with the familiar structure of `props.data`, drastically improving the developer experience of this thing.

  Old approach:

  ```jsx
  return <props.Rte path={(d) => d("someData").someDeepValue} />;
  ```

  New approach:

  ```jsx
  return <props.Rte key={(d) => d.someData.someDeepValue} />;
  ```

- 692f913: Added line-height to the settings of the `Header` blueprint title and implemented new scale animations.
- 3c23c51: Added new `title`, `onlyIconOnMobile`, `borderRadius` and `style` settings to the `Button` blueprint and slightly fine-tuned its logic and design.
- 131e7b7: **BREAKING CHANGE**: Moved `createAdminRoute` and `createPageRoute` exports to `nitropage/routes` and moved `Admin` to `nitropage`. This change fixes some internal issues with circular imports.

  **You have to update some project files!** Please read the upgrade notes in the [v0.62](https://nitropage.org/docs/guides/upgrades#v062) docs.

- 9735d22: Improved the previews of `Code`, `Audio` and `Video` blueprints shown while creating new elements.

### Patch Changes

- 86e78c6: The fonts upload dialog now only shows supported font types.
- 069841a: Fixed the element selection border of the `Container` blueprint.
- e58cb4f: Changing the alpha (transparency) value of an empty `colorData` picker, will now assign the default color (white) to the picker.
- 61b5505: Fixed a rare occasion where project settings in the editor did not show their latest state, after saving to an existing page revision.
- 0daea5c: Don't render the `editorpadding` prop of `<Slot>`. (https://codeberg.org/nitropage/nitropage/issues/108)
- Updated dependencies

## 0.61.0

### Minor Changes

- 45472e7: Blueprints components now have access to a new `writing` prop, which is `true` if the editor is in `Write` mode.
- f2fb6ae: Updated internal dependencies.
- 0edb4f2: Improved the layout of the `Roadmap` blueprint. Roadmap sections with no title will now vertically align to other sections with a title.
- d1b62ed: The tooltips of color presets now show respective hex values (#56).
- 95dd515: The range slider of number inputs now shows up on hover (#106).
- 1bbf750: Reworked the `A` component, added support for `mailto:`, `javascript:`, `tel:` and `sms:` hrefs, and fixed inconsistencies with relative hrefs (#114).
- ac5b2d0: You can now use your mouse wheel in number inputs to change the value.
- a155b92: Multiline `textData` textareas now use a proper, yet lightweight code editor featuring tab indentation and auto-height (#17).
- f1819c5: Added a `Balanced Wrap` setting to the `Heading` blueprint, controlling if the heading should be rendered with `text-wrap: balance;`.

### Patch Changes

- b3216cf: `Section` can now be used as a child of a different element and `Flex` can now be used directly on the page.
- 6f07e8e: Disabled the default browser overscroll behavior in the admin dashboard and editor.
- 7007798: The editor now properly hides empty `<props.Rte />` fields, even if they use a custom `display` type.
- 9854096: Removed obsolete internal `Accordion` workaround and replaced it with Kobaltes [Accordion](https://kobalte.dev/docs/core/components/accordion). The workaround was previously used because of an upstream [issue](https://github.com/kobaltedev/kobalte/issues/236).
- 7f2a1ce: The last page listed in a `Documentation` navigation will now show the proper back-pagination.
- fbc8fc9: The Heading `hyphen` option now also properly affects the subtitle.
- cabc68b: The range sliders of number inputs are now properly reachable via the tab key.

## 0.60.3

### Patch Changes

- 2cf1325: Fixed the font used while dragging elements in the sidebar.
- ee37458: Fixed a bug that resulted in a `Window.getComputedStyle: Argument 1 is not an object.` error in the page preview, after moving elements.
- bb99e9f: Removed recursive heading id detection in the `Documentation` blueprint, getting rid of some false-positives. `Heading` blueprints render the `id` attribute directly on their `h`-tag since e76625e01a, which made the recursive id detection obsolete.
- 4f3b826: Hidden the pagination border from the `Documentation` blueprint, in cases where there is nothing to paginate.
- b551c76: The `Documentation` blueprint now doesn't take a full page height, if it isn't needed.

## 0.60.2

### Patch Changes

- b4d32ec: Second round fixing the `Environment variable not found: DATABASE_URL.` error, while avoiding compatibility issues with `pnpm`.

## 0.60.1

### Patch Changes

- 2064ff9: Fixed an `Environment variable not found: DATABASE_URL.` error, that happened during `npm run start`, in projects installed with `npm`.

## 0.60.0

### Minor Changes

- 26fe891: The `Text` blueprint has a new `hyphen` option.
- 5a20493: Updated dependencies, including minor updates for Prisma and Solid.
- 4823e5c: Slots with a `max` value of `0` will now stay hidden in the expanded elements list.
- 60b49b2: Parameters of the `clamp` css utility are now optional and the default value for `minScreen` has been changed from '512' to '640'.
- bf0c86b: **BREAKING CHANGE**: Renamed `Box` blueprint to `Card`, added many new settings such as `link`, `border` and reworked responsive `padding`.

  > If you used `Box` with the old dropdown-based `padding` before, you need to reapply your preferences! The new `padding` is number-based.

- 64a5dbd: Slightly improved the styling of invalid blueprints in the page preview.
- 340fcd4: Disabled spellchecking on the `textData` textarea.
- 1a8fecd: Syntax errors in blueprints now don't cause the dev-server to crash (regression from v0.59).

  Also stopped blueprints with syntax errors from unmounting prematurely. The page editor now renders such blueprints with the last valid component.

- 2806ac6: Consolidated the design of element and blueprint errors on the page preview.
- 9926075: **BREAKING CHANGE**: Removed unrelated css utilities such as `clamp` from the `nitropage/data/color` exports.

  > Please import such css utilities directly from `nitropage/css`.

- 183116a: Added new responsive `margin` settings to `Heading` and disabled the `default` slot.

  > **The `default` slot of `Heading` is deprecated!** Please stop using it and move existing elements outside. The slot will be removed in a future version.

- 77eda28: **BREAKING CHANGE**: Deleted the `Space` blueprint and consolidated it with `Flex`. Both blueprints had almost identical use cases, which led to confusion and redundant code. `Flex` now has several new options, greatly improving its usability.

  > Please edit your pages and replace broken `Space` elements (blueprint id: ktfqyfx6i7gru55hgndh0d9h) with `Flex`.

- 1273a16: Elements of invalid (e.g. deleted) blueprints will now be shown in the sidebar and can be moved from there to a new parent.

### Patch Changes

- 3d47fea: Fixed wrong element selection ui for unmounted or moved elements.
- a1fa560: Fixed link text not being wrapped in inline richtext editor.

## 0.59.0

Upgrade to SolidStart v1.0 and a ton new features!

**Release announcement**: https://nitropage.org/blog/nitropage-v0-59

**Upgrade instructions**: https://nitropage.org/docs/guides/upgrades#v059

### Minor Changes

- 92bfa36bac: New toolbar & responsive tools: Doesn't get in your way and lets you zoom the page preview.
- f5af2377a5: Youtube and Vimeo support: Share Youtube and Vimeo videos without a hassle.
- fe30d11729: Reworked element selection UI: View the name of the hovered element in all situations.
- dba7707639: Reworked link traps: Preview links and buttons glitch-free.
- 83cfdb94bd: New 'Narrow' blueprint: Narrow layouts without the fuzz.
- 90a54e90c9: S3 file storage: Upload and show media from S3 buckets.
- 90a54e90c9: Image settings: Customize "alt"-descriptions and fallback colors of your images.
- ae7bd5d60f: New 'Markdown' blueprint: Wanna write your site content with Markdown? Well now you can.
- 90a54e90c9: Focal point image cropping: Keep the important parts when cropping an image.
- 3e1042b9a6: New 'Embedded Video' blueprint: Embed videos from PeerTube, Odysee, Rumble and others, via their iframe codes.
- 92bfa36bac: SolidStart v1.0, Nitro and Vinxi: Enjoy all new features of the upgraded SolidStart framework.
- 2461265: The `A` component now appends the path of the current page to `href`s beginning with a hash (`#`).
- 92bfa36bac: Global page CSS: Globally style your pages without breaking the Nitropage Dashboard.
- 69d6935f97: Blueprint CSS without FOUCs: No more FOUCs when you import CSS files in your blueprints.
- a93f79b32b: Global server configuration: One place to configure all internal services.
- b09fa6bc29: Smaller HTML document size: Passive blueprints no longer affected by the double data problem.
- f530eeb: Enabled the `prismaSchemaFolder` setting, separated the Nitropage schema into an own file and renamed the `import-prisma` cli command to `update`.
- 04ef704: The `A` component now only externalizes links with a `href` starting with `//` or including `://`.
- 0f0c4a6178: Built-in prose styles: Consistent typography for richtext and markdown content.
- 90a54e90c9: Reworked image optimization API: Fewer lines of code for the same result.

## 0.58.1

### Patch Changes

- 00a1cbc: Fixed an issue that resulted in missing page styles (e.g. colors), after navigating from a `/admin` route back to a public Page route (#1).

## 0.58.0

### Minor Changes

- bd03784: Slightly reworked the element dragging visuals and added useful outlines showing you where you can insert new elements on the page.
- d5d41f6: When selecting a blueprint for a new element, the blueprints list is now an own scrolling container.

### Patch Changes

- 79f9335: Enforcing elements to be interactable during select, move and delete actions.
- a78f04f: Added a minimum height to richtext lines. This makes sure that empty lines do not fully collapse.

## 0.57.0

### Minor Changes

- ee63a6f: The richtext editor will now only convert text like `1. ` or `- ` to corresponding lists, if `ctrl` and `space` are pressed together.
- 9569f80: **BREAKING CHANGE!** Lists in richtext content are now again based on proper semantic html.

  Existing page content has to be manually updated! Please follow these steps to update your pages:
  1. Open your pages with richtext content including lists
  2. Make changes in content with lists, eg. press space + backspace
  3. Save + publish the related pages

  This change is related to the recently updated Quill richtext editor, ec1e95a36b and 5dead7e1b3. More info can be found here: https://github.com/quilljs/quill/issues/3957

## 0.56.0

### Minor Changes

- 6abda23: The editor page preview now updates during user input, e.g. when changing colors. These updates occur maximally at 10 frames per second.
- 2fd0781: Changed the font family of `textData` in multiline mode to monospace.
- a56fd96: Deleting an element will now open up a confirmation dialog. This change included a major rework of the internal page preview update logic.

### Patch Changes

- 46ca14f: The element duplication button in the sidebar now only shows up, if the corresponding parent slot is allowing additional elements.
- c0fa7d7: The number input now properly handles deleting decimals. E.g. deleting the last decimal of `123.4` will now result in `123.` instead of `123`, allowing the user to input a new decimal.

## 0.55.0

### Minor Changes

- e7242cc: The element database id can now be accessed in the blueprint component props via `props.element.id`.

## 0.54.1

### Patch Changes

- 1b6a6a0: Properly pinned `vite-plugin-solid` and updated `undici` peer version.
- 0ab7564: Pinned `@node-rs/xxhash` and `@solidjs/router` to the latest stable versions.

## 0.54.0

### Minor Changes

- d5b65c5: Updated internal and starter dependencies. Pinned vite-plugin-solid to the last compatible version v2.7.2.

## 0.53.2

### Patch Changes

- a2dbd6a: During the duplication of a page, the settings will now also be copied to the new page.
- 1f862a9: Fixed a bug with special characters in names of uploaded file not being properly converted to utf8.

## 0.53.1

### Patch Changes

- cee3b68: Added back in some missing spacings for richtext list items with line-wrapping text.

## 0.53.0

### Minor Changes

- 81f6c65: Added a new `passive` option to blueprint files. Passive blueprints will only be loaded on the client on route change, or if they are parents of other non-passive blueprints.

## 0.52.0

### Minor Changes

- ee3ead4: Updated the internal dependencies.

## 0.51.0

### Minor Changes

- 9fc7e4e: Uploaded files in `mediaData` now replace the currently selected files, if the quantity of the uploaded and selected files is equal.

### Patch Changes

- fdbde6e: Fixed a bug in `mediaData`: Deleting any file deselected the currently selected file.

## 0.50.1

### Patch Changes

- 8d2fed5: Relicensed the code under `Unlicense` (instead of `MIT`) and added a new README file.

## 0.50.0

### Minor Changes

- a68f11f: Slightly reworked the cursor icon that is showing during the creation of new elements.
- 0bbff66: Implemented a scroll restoration feature in the editor. When switching between different toolbar modes, the editor will now try to restore the previous scroll position.

## 0.49.0

### Minor Changes

- c2536b4: Added `compose` and `DataLense` public API's, which can be used to better organize nested richtext path functions.
- f804378: `numberData` will now default to `undefined` instead of `0`, if its `optional` configuration is enabled.

### Patch Changes

- 57718bd: Applying a text color to a link in the richtext editor now properly overrides the default link color.

## 0.48.0

### Minor Changes

- 88e9136: Added default negative z-index styles to the `ImageContainer` children, opening up the container to inner-outline design use-cases.

## 0.47.0

### Minor Changes

- 57d0438: Slightly optimized the logic used for focusing elements in the editor. A selected element will only be focused, if it isn't partially in the view already.

### Patch Changes

- f33717c: Blueprint data will now be initialized after the editor page preview (iframe) is connected. This fixes a timing error that could happen during initialization of new settings for already used blueprints.

## 0.46.0

### Minor Changes

- 6204318: Adding a new item via the `listData` ui will now directly open it, if another item was previously opened.
- b26a122: Added `subscript` and `superscript` formats to the richtext editor.

## 0.45.0

### Minor Changes

- f6b0ffc: Reworked the fade animation of the `Image` component. It now uses a css animation instead of a transition, freeing up css transitions for other uses.
- 4d6dd83: The `MediaContainer` now positions the image based on the `NitroMedia` resize position.

### Patch Changes

- ee90d16: The `MediaContainer` now properly applies the background-color of the supplied image.

## 0.44.0

### Minor Changes

- 7257611: Slightly aligned the element spacing in the editor between different toolbar modes. The `select`, `create`, `move` and `delete` modes now all use the same spacing.
- 187b93f: The prop value of `colorData` is now optional (CssColor | undefined), simplifying conditional logic for colors. `colorClass` now also only returns a class string, if its color parameter is set.
- ce58d90: `fontClass` now only returns a class string, if its font parameter is set.

## 0.43.0

### Minor Changes

- 2751a54: Adjusted the fonts testarea ui in the editor for condensed fonts.
- 5545c24: Replaced the drag related icon in the editor with a more obvious one.
- f28aed8: Optimized the order of the fonts in the editor.

### Patch Changes

- 9ff7df0: The editor dialogs now use the proper font family (Inter).
- 649cc52: Fixed a bug with the font add/remove buttons refreshing the page, instead of the font settings.

## 0.42.0

### Minor Changes

- 706549f: Moved the primary code repository to Codeberg. The Lufrai repository will be used as a backup.

## 0.41.2

### Patch Changes

- 3d3e319: Refactored the editor data handling code and fixed a bug with the presets not being updated in the editor after saving the page.

## 0.41.1

### Patch Changes

- e70ea11: Fixed a bug with the editor sometimes not showing configured fonts depending on network timing. The editor is now waiting for the fonts to be fully loaded.

## 0.41.0

### Minor Changes

- 3da6937: Slightly optimized the color picker to skip some unneeded UI rerenders.
- c63456c: Added a `Favicon` setting to the projects tab in the editor. The favicon is automatically resized and included in different formats.
- c67cb5f: The element settings header will now stick to the top, allowing the user to see the active settings tab and switch between tabs, without having to scroll to the top.
- ab833be: Added a `meta image` setting to the project and page tabs in the editor, which can be used to define an image for social media embeds. This change included a general refactor of the settings handling in the editor, adding the possibility to implement more dual (page/project) settings in the future.

## 0.40.1

### Patch Changes

- 659a8dd: Fixed a bug with the dark mode not properly applying mode-independent colors.

## 0.40.0

### Minor Changes

- 9f7d99d: Greatly reworked the UI of `colorData` adding hsl and alpha inputs, animations and a confirmation dialog for preset deletion. The `rgb` and `colorClass` helpers now expect a CssColor object as parameter (breaking change).
- 7361cc9: Implemented `colorClass` and `fontClass` primitive utilities, which can be used to set color and font styles.
- 3f4a4ac: The color picker now includes an `invert` setting, which allows you to use light colors in dark-mode and vice versa.

### Patch Changes

- 9e56760: Fixed a rare timing bug, which resulted in the tab-navigation of the editor sidebar, not always correctly sticking during scroll.
- fc3b248: The override-data tooltip is now hidden in the editor idle mode.

## 0.39.1

### Patch Changes

- ec1e95a: Updated the richtext editor list styles to the new quill 2.0 format. In particular this fixes a problem with unordered lists, which didn't show their bullets.
- ab6900c: Fixed a bug in the richtext editor, which ignored the last line if it was empty.

## 0.39.0

### Minor Changes

- d7f0db8: Added a proper `idle` mode to the editor, which can be accessed by clicking on the currently active toolbar item. In the `idle` mode the page is rendered nearly the same as live.
- a71eff2: Added a new `optional` setting to `numberData`. If `optional` is enabled, numberData can store undefined, otherwise it always will store a number, defaulting to `0`.

### Patch Changes

- f793d00: Fixed a bug that resulted in the editor always listing all fonts, instead of only the project ones.
- 9944c38: The library button of `mediaData` now only shows, if the project already has uploaded files of the corresponding file type.

## 0.38.1

### Patch Changes

- 3a58423: Updated internal dependencies.

## 0.38.0

### Minor Changes

- f14349e: The `numberData` helper now accepts `null` as `defaultValue`.
- 80f53b7: Added many additional settings to the `table` starter blueprint.
- 3fa2169: Fixed performance issues with the new richtext editor fork in Chrome and improved overall editor performance. Also updated several internal dependencies.

## 0.37.0

### Minor Changes

- 9106e6a: Slightly optimized the user interface of `listData`, adding numbers to the list items and adjusting spacings.
- 5199f77: Added a `table` blueprint to the starter.
- 8c329c6: Elements in renamed/removed slots will now still be shown in the elements list (with a warning), making it possible to move the elements to a valid slot.
- 5dead7e: Replaced the richtext editor (quill) with an own fork, using floating-ui for the tooltips.

## 0.36.0

### Minor Changes

- b88eae8: Added a light/dark scheme switcher to the editor toolbar.

## 0.35.1

### Patch Changes

- f2e065a: Fixed an uncommon timing error `t.element is undefined`, which sometimes happened during navigation between pages with many elements.

## 0.35.0

### Minor Changes

- 073ad5c: Upgraded `solid-start` to v0.3.9 and `vidstack` to v1.5.1. **Please update your solid related dependencies such as solid-js and @solidjs/meta!**

### Patch Changes

- 5356e2a: The built vite dist folder is now included in the npm tarball.

## 0.34.1

### Patch Changes

- 2fbbc30: Rebuilt the command line binaries.

## 0.34.0

### Minor Changes

- 52ac3ae: Some colors of the page editor user interface have been revised.
- 859ba14: Implemented the `multiline` option for `textData`, which will render a textarea instead of an input.
- 8a73737: Renamed the `seed-demo` cli command to `demo` and added a confirmation dialog.
- ca76348: Implemented the `Documentation` blueprint for the starter kit.
- 6b7d45a: Added a `matchHash` option to the `A` component, which is enabled by default. Links with this option will only be shown as active, if they match with the current location hash.
- beea347: The project domain input now validates the domain with a basic regex pattern.
- 3ab1695: Implemented the `Code` blueprint for the starter kit.
- fed75e5: Implemented new `user list`, `user add` and `user set` cli commands.
- 9661ceb: Made the `username` and `email` fields from `NitroUser` unique. **Please update your database schema with "`npm run import-prisma -m`"!**

### Patch Changes

- 75ebb50: Fixed a bug in the `demo` cli command, which incorrectly hashed the demo admin password.
- 795b943: Fixed memory leak in richtext component and lowered memory usage.
- e2bfc30: Slightly reworked the richtext editor so that it doesn't break with no toolbar items.

## 0.33.0

### Minor Changes

- 43bd1cd: Further improved the image optimization API and added a new `aspectRatios` option to `createResize`.

### Patch Changes

- b1f6dc3: Fixed a bug in the `blueprint` cli scaffolding command, which still generated the code with `NitroComponent` instead of `BlueprintComponent`.

## 0.32.0

### Minor Changes

- 85abec3: Renamed lots of internal and external occurences of the word `Nitro` to other suitable alternatives, to better differentiate `Nitropage` from the unrelated [Nitro](https://nitro.unjs.io/) technology. **You need to upgrade your starter kits! The blueprint filename prefix was changed from `nitro` to `np`. The placeholder image `public/nitro-placeholder.webp` was renamed to `np-placeholder.webp`. Please also check your `vite.config.ts` and use the new default export from `nitropage/vite`.**
- f93fe40: Made the `useVisibilityObserver` API publicly available for use in blueprints.

## 0.31.0

### Minor Changes

- 2a4b324: Added a bit of transparency to the toolbar buttons.
- d0a85a1: Reworked the `mediaData` blueprint data, including its API. Next to images, it now also supports audio, video and document file uploads.

## 0.30.0

### Minor Changes

- 6e5c732: `useResize` now also returns an object with `Source`, which can be used for typescript purposes.
- 870ddac: Renamed the Image, Text and Separator starter blueprints, added full-width options and new aspect ratios.
- c8259a5: Replaced the background grid texture of the editor element selection with a png, resulting in a minor performance win.

### Patch Changes

- b93be45: Image decode errors during the load of the editor iframe will now be catched.
- 97ad1c4: Fixed a bug in the checkboxes of the editor, which sometimes rendered with a wrong height after element selection.

## 0.29.0

### Minor Changes

- 161d8aa: Cropped the placeholder image to a square aspect ratio.
- 328c20e: Internally optimized the visibility observer for images. It now uses a shared instance, which should slightly improve page load speed, especially for pages with many images.

### Patch Changes

- 37f384b: Fixed an issue with the `import-prisma` cli command, which crashed if the prisma client wasn't already generated.

## 0.28.0

### Minor Changes

- 9f11f30: Reworked the `MediaContainer`, `MediaImage`, `ImageContainer` and `Image` APIs, renamed `fadeTime` to `fadeDuration` and implemented native lazy loading.
- 0c47a5a: The page editor now starts in the "Create new elements" mode on empty pages.
- 0260ee4: Implemented a basic atom feed which can be accessed via `/feed/`. Only pages with the new setting `Include In Feed` are included in the feed.
- ebb7aed: Rewritten admin notifications with `kobalte` and removed obsolete `solid-toast` dependency.

## 0.27.1

### Patch Changes

- 117ec04: Removed an unnecessary `:` in the urls of the new sitemaps.

## 0.27.0

### Minor Changes

- 2e01615: Nitropage now automatically generates proper sitemaps, listing all published pages of the corresponding domain. The sitemap can be accessed via `/sitemap.xml`.

## 0.26.0

### Minor Changes

- db383e3: Implemented the presets feature in the editor. Element settings can now be stored in presets, which can be used across multiple pages. This also includes reworks of common editor workflows, such as the ability to quickly switch between element- and project blueprint data.

## 0.25.0

### Minor Changes

- 116e503: Added common seo metatags for facebook (og) and twitter.

## 0.24.3

### Patch Changes

- 77069dd: Fixed an issue that prevent the login screen from showing up in expired admin sessions.

## 0.24.2

### Patch Changes

- f8459e5: Fixed a bug with the richtext editor, not being able to load in npm environments.

## 0.24.1

### Patch Changes

- 5033de1: Added missing domain value to the demo database seed.

## 0.24.0

### Minor Changes

- 58c23c2: Added the noindex robots metatag to admin routes.

### Patch Changes

- c64c201: Fixed a bug with the admin page visit links, which used localhost on non-localhost domains.

## 0.23.1

### Patch Changes

- ae2a79f: Updated the peer dependencies.

## 0.23.0

### Minor Changes

- 3f39799: Implemented the multisite feature (`projects`) which allows to host multiple websites on a single Nitropage instance.
- 7fd1659: Blueprints can now be async functions, which will be used for localization lazy loading.
- dcbc04b: The decrypted session data will now be cached during server requests, avoiding multiple session decryptions for the same request.
- 7e4b3de: Added a middleware to the `entry-server.tsx` which will be used at a later time, to implement features such as `sitemap.xml generation`. Please update the `entry-server.tsx` in your projects accordingly.

### Patch Changes

- a2a4eb1: Fixed a bug with the font preloading, not using the best available font format in certain cases.

## 0.22.0

### Minor Changes

- 1c6624f: Added save (Ctrl+S) & publish (Ctrl+P) keyboard shortcuts to the editor.
- 686a72c: Implemented an element duplication button in the elements sidebar.
- 7726b6e: Added an icon to the dropdown elements, visually differentiating them from text inputs.
- f1926e9: Slightly optimized the elements breadcrumbs and slots interface, by replacing the Overview-icon, changing the Slots-title to Overview and properly aligning element buttons.

## 0.21.2

### Patch Changes

- c35b76b: Fixed a bug that resulted in richtext not being editable, if it just freshly spawned from a `defaultValue`.

## 0.21.1

### Patch Changes

- 1b8ad20: Updated the demo seed data to the new `listData` schema.

## 0.21.0

### Minor Changes

- 4eb84f7: Added the `path` prop to `Rte`, allowing developers to use the richtext editor in nested `listData` situations. This is a breaking change. Please note: the `listData` getter field `.items` was renamed to `byId`, making it consistent with the `useMedia` `byId` field.
- ea79833: Updated the richtext editor design, bringing its presence more in balance with the other ui elements.

### Patch Changes

- 553d9b6: The `fontData` family dropdown will now show ids of fonts without a family name.
- dc4ea08: Reworked the richtext editor focus and state handling, fixing several ux blockers.

## 0.20.0

### Minor Changes

- 47bf1db: Slightly optimized the client side pageload performance of richtext elements, by avoiding innerHTML during hydration.
- 221187b: Blueprints will now only listen for code changes in development, this is a small memory usage and startup optimization.
- 9ee7c0e: Improved the design of admin form input elements. The inputs related to `fontData` now also are rendered with the consistent design.

### Patch Changes

- f9eb836: Uploaded font file's Mime will now be detected with [file-type](https://github.com/sindresorhus/file-type).
- 2e7113d: Styles for fonts and colors will now only be rendered once on the server.

## 0.19.0

### Minor Changes

- 5a3c4d8: Added a `toolbarFull` export to `rteData`, which can be used to enable all toolbar options.
- 6a283aa: Slightly improved the styling of the richtext editor toolbar and increased its z-index.

## 0.18.0

### Minor Changes

- 4c4cddf: Increased the optimized image browser cache max-age to one year.
- 4d024f4: Added support for img props to `MediaImage`.

## 0.17.1

### Patch Changes

- 4bf3646: Updated the `mediaData` editor input component to the new media API.

## 0.17.0

### Minor Changes

- ddb4bba: Reworked the media API, added 2x pixel ratio image variants and implemented NitroMedia specific components. This is a breaking change and blueprints using the media API have to be updated.

## 0.16.0

### Minor Changes

- 91456a3: Slightly optimized the spacing of the elements list in the editor.

### Patch Changes

- d03fa43: Fixed a bug that resulted in the removal of page preview styles during the initialization of the editor. The bug came up with solid 1.8.7 which slightly changed the timing/order of effects.

## 0.15.0

### Minor Changes

- 57aa0da: Added the original resource object as a third item to the result of `useMedia`.
- f30c1df: Upgraded to Prisma 5.0. Please update your prisma schema file (remove the obsolete `previewFeatures` line).
- 99635f3: Disabled page blueprint settings for now. The functionality will likely be replaced with a more flexible presets feature.

### Patch Changes

- ef6a917: Fixed a bug in the accordion of the page & global settings, which resulted in inputs inside the accordion not being focusable on first try.
- 44d818f: Fixed a bug with the editor inputs which updated their state on blur even if the value was unchanged.
- e7c1255: Fixed a visual bug in the listData item title rendering. Long item titles will now properly be shortened with ellipsis (`...`).

## 0.14.0

### Minor Changes

- 0cef823: Further improved the target element indication during create and move actions.

## 0.13.0

### Minor Changes

- 4187d3c: The elements list in the editor sidebar will now highlight the current target element during create / move actions.
- eab21d9: Slightly optimized the richtext editor theme to better integrate it into Nitropage.

## 0.12.0

### Minor Changes

- 6235984: The `mediaData` file upload input will now be cleared after an upload.

### Patch Changes

- e1fd917: Changing the editor viewport width now doesnt show horizontal scrollbars in the sidebar.
- a9d337f: Fixed a bug with the viewport resize handler that caused Chrome to lunatically resize the viewport in certain situations.

## 0.11.2

### Patch Changes

- bd2508d: Fixed a bug which caused the page editor to reload its full state (loosing unsaved changes) after media file deletions.

## 0.11.1

### Patch Changes

- a273988: Fixed a bug that resulted in the page meta description not being loaded in the editor.
- 46141dd: The not found page now properly renders its meta description during 404 responses.

## 0.11.0

### Minor Changes

- 9086c54: Implemented a custom solid-start adapter and added a production server to the starter kit.

### Patch Changes

- 5051cdc: Removed Image alt fallback value.
- f612a9e: Not found images in the mediaData library now don't take up the whole library space.

## 0.10.0

### Minor Changes

- db6904b: Added `lorem` and `shortLorem` options to `rteData` which will set a corresponding lorem-ipsum defaultValue.
- f4a7a2c: Implemented a demo mode which can be enabled with the `VITE_NITRO_DEMO` env variable. Also added a `seed-demo` command to the cli which will clean up the current database and add demo data.
- ad31ec2: Implemented a settings cache flushing mechanism and related env variables `NITRO_SETTINGS_CACHE_MAXAGE`, `NITRO_SETTINGS_CACHE_FLUSH_AGE`.
- 4b6c50c: Opening non-existing / invalid page ids in the admin via `/admin/page/xyz`, will now result in a redirect back to `/admin`.
- 7177b36: Added a new `Contact Grid` blueprint to the starter.
- 0e6bb24: Added a background pattern to the mediaList image selection, making transparent images more recognizable.
- 64f96fb: Added a new `Logo Grid` blueprint to the starter.
- ee000f7: Renamed `cssData` back to `colorData`, hopefully this will be the last time ;).
- df6d32f: Added tooltips to the editor toolbar.
- bfea53f: Overhauled the project blueprint data defaults using the new settings architecture. **Old blueprint defaults will not automatically be migrated**.
- 300d1d0: `cssData` color presets can now be deselected.

### Patch Changes

- e87a168: Page related styles are now propery getting removed during client-side navigation to the admin.
- 7b92ae2: Fixed a bug that caused editor select elements to trigger redundant onChange events.

## 0.9.0

### Minor Changes

- c956f97: Implemented the `props.slotElements` helper which returns an array of element ids related to a specific slot.
- a27c643: The prisma db log level now depends on the production / development env the server is running in.
- ac02171: The slot name in the `Elements` tab is now more clearly separated from its elements.
- 7076443: Implemented the `Flex` blueprint for the starter kit.
- 3d5b029: Reworked the way how page and project settings are stored in the db. This is an important preparation step for the later support of multiple projects and domains. Since this is another breaking change in the schema, old databases created with 0.8.0 are not compatible.
- af5f983: Overhauled the color presets with the new database settings architecture and implemented the `page background` setting. **Color presets created with v0.8.0 will not automatically be migrated to the new format**.
- 08406cd: Enabled the prisma json protocol in the starter kit.
- 3c3ef1b: Implemented the `meta description` in page settings.
- f834c0b: Implemented the `Footer Newsletter-Form` starter kit blueprint.

### Patch Changes

- 173839f: The `listData` `sortItems` helper now stricly checks if the provided data actually has a `.ids` property.

## 0.8.0

### Minor Changes

- 49fa246: The `listData` items in the sidebar now load their sub items separately from the sidebar. Previously the sidebar flashed duing the loading.
- d0dbe63: Moved the `nitro-placeholder.webp` image from `public/media` to `public`.
- 5901953: The label for blueprint data without an explicit title will now be capitalized.
- 74760fa: Properly integrated the admin font (Inter) and moved admin styles into a separate css file. Removed admin lazy loading from the starter template.
- c59078d: Implemented `listData` default value handling and added `defaultItems` option.
- 660ff8f: Moved the bare example to `packages/starter`.
- 07feb6a: Improved ux of `mediaData` with `max` 1: the user can now directly replace an already selected image, by clicking on another one from the library.
- 66b7767: Added an unpublish button to the page settings.
- c455eec: Added a `Is 404 page` setting to the page settings. The page having this setting enabled, will be shown on 404 routes.
- c3b473c: Uploaded media and fonts will now be connected to the project. This is a preparation step for later support of multiple projects.
- f7d3cdf: Uploaded media files are now saved on the server with a unique public id. The NitroMedia database record has new fields including the original file name and extension. **Since this is a breaking change in the schema, old databases created with 0.7.0 are not compatible.**
- f77aaf0: Renamed `avoidOverlay` element prop to `lax` and inverted its value.
- b67cd2a: Implemented the `Feature Grid` blueprint for the starter.
- 9d42c99: Internal links in richtext now use solid routers client side navigation.
- cf42452: Improved the visual clarity and intent of the root/overview button in the elements breadcrumbs.
- ad6b6e4: The `sortItems` helper of `listData` now returns an array with `[item, id]` values.
- fccfc17: Renamed `Globals` tab of the editor to `Project`.
- 60b46fe: Changed the admin font family from Jakarta to Inter.
- 8dd35ef: Rename `listData` `sortedItems` helper to `sortItems`.
- 22735c0: Global and page blueprint data will now be initialized with defaultValues as early as possible. Before this change, the data only was initialized after specific user interactions.
- 0c40963: Richtext links will now be highlighted in the sidebar editor.
- 4a43b18: Added project table to the database schema. Pages now have to be related to a project. Since this is a breaking change in the schema, old databases created with 0.7.0 are not compatible.
- b399fb3: Added default richtext link styles to the starter project.

### Patch Changes

- 691cadf: Select (dropdown) fields in the admin now show the default value, if the selected one is invalid.
- 0bb243b: Small visual improvement of the element breadcrumbs.
- 1a7c9d7: Fixed a bug in the richtext editor regarding copy/pasting.
- 3f367a4: Fixed a bug with `toggleData` resulting in always returning `true`, if `defaultValue` was set to `true`.
- 8485f01: The placeholder during element drag operations, now has a consistent width and height.
- 260ef20: Following up to 62f944c6ee, the richtext editor in the sidebar still didn't keep its focus in all cases. This should be fixed now.
- 82a578d: Fixed a bug in the blueprint data "clear all" button, which resulted in broken (non-reactive) state. Also changed the button icon and label to better communicate its effect.
- 06a71f2: In certain cases the options-element of selects was wrongly rendered behind other elements. This is fixed.

## 0.7.0

### Minor Changes

- 23a7cee: The page-view buttons in the editor and dashboard now reuse existing page tabs.
- b179545: Switched around the richtext editor colors behaviour. Now the inline richtext editor shows the real text colors during editing and the sidebar editor shows the text in black. Also added a border around editable inline richtext editors.
- 0e8fd16: The blueprint components, including their server$ functions, are now preloaded on the server in admin routes. Also fixed a bug that resulted in blueprints getting loaded on the server twice on non-admin routes.
- 74ef945: Added better support for `class` and `classList` props in `Image` and `ImageContainer` components.
- 77d0f86: Added a `blurhash` value to the `PlaceholderImage`.
- 64210d2: Replaced the toolbar add icon with a more obvious one.
- e69ea2b: Empty slots will now only be highlighted when the user is creating / moving elements.

### Patch Changes

- 6abdbf9: The non-wide `selectData` select will now properly use ellipsis overflow for long item titles.
- 84e6d6d: Fixed a bug in the admin `Select` component, which resulted in a ui crash on undefined values.
- 62f944c: Richtext Editors in the sidebar now don't loose focus on toolbar button clicks and properly apply related text/format changes.

## 0.6.3

### Patch Changes

- 02fd33c: The `Rte` component's `class` prop wont be rendered anymore, if its `undefined`.

## 0.6.2

### Patch Changes

- cf46227: Uploaded svg's will not be converted to webp anymore.

## 0.6.1

### Patch Changes

- bc0d572: Reworked the `ViteRestart` vite plugin, replacing the vite builtin file watcher with a separate chokidar watcher and thereby fixing an issue that broke HMR for non-blueprint components in the `blueprints` folder.
- 5f08b04: Changed the event handling of the richtext editor, so that it only listens and reacts to text changes made by the user. Eg. if the user changes some content via a inline richtext editor, the related editor in the sidebar will also apply that change, but it will not again inform other editors about this change.

## 0.6.0

### Minor Changes

- 3d15c04: Selecting a richtext with the inline text editor does now also navigate to the corresponding element in the sidebar.

## 0.5.2

### Patch Changes

- 43addb5: The `rteData` editor now only enables its list format, if it has list specific toolbar items.

## 0.5.1

### Patch Changes

- 33e71af: The style tag for fonts is now properly rendered with a closing tag, if no fonts are defined.

## 0.5.0

### Minor Changes

- 77e50de: Removed the `rte` option from `rteData`. The `toolbar` option can now directly be declared in the `rteData` options.

### Patch Changes

- 762d62c: Fixed a rare bug were by switching from the element creation tool, to a different one, while no element creation place was set, future element creation attempts stopped working and the user had to reload the editor.

## 0.4.0

### Minor Changes

- f9cb89b: Images in the mediaData selection are now listed without cropping.
- 208b81e: Optimized editor drag and drop when inserting/moving elements into empty slots.
- 208b81e: Reworked the ui elements of empty slots. The slot name now shows up during insert/move operations.
- 6bc7195: The `rgb` function `opacity` parameter now accepts strings.
- 58a3cd2: The elements list now clearly indicates invalid blueprints and shows a corresponding delete button.
- 76f8e6c: Added component and class props to Rte component.

### Patch Changes

- 3a86177: The `fontCss` function of `nitropage/data/font` now just returns an empty style object when its called with no font, instead of throwing.

## 0.3.0

### Minor Changes

- 9e8e71f: The resource behind `useMedia` now automatically uses `.latest` instead of `resource()` during HMR and therefore avoid Suspense during development.
- 05e25f1: Reworked the way how blueprints are loaded. The new way triggers solid suspense on route change and makes sure that all blueprints are loaded, before the new page starts to render.

## 0.2.0

### Minor Changes

- 9dcf51c: Uploaded images are resized to a max width of 2000 pixels.
- 1a449b9: The `selectData` item `label` option was renamed to `title`. This makes it consistent with the blueprint data `title` option.
- 1391457: The editor iframe state `reconcile` now properly merges incoming state. Previously it fully replaced old objects with the incoming ones, resulting in many redundant effect (ui) updates.
- 56b6b8e: Added `@kobalte/core` to nitroVite ssr noExternal.
- fb0e751: Cleaned up the listData item accordion ui.
- 90dd488: useMedia now returns a getter that will automatically access the resource data via .latest in admin.
- 7bbc9ab: Disabled suspense for `useResize` in the editor. Elements in the editor now already render, while images still are being loaded.
- 50cb825: Blueprints in the editor now are reconciled with merging. This reduces redundant store subscription updates.
- 0c23447: When creating new items in listData, they are now initialized with the `defaultValue` from their corresponding blueprint data.
- aab720a: Added a `defaultValue` option to `rteData`.
- 1b814d9: Added a `sortedItems` helper to `listData`, which does return the list items in the order as sorted by the user.
- 78d0c2d: Addded a PlaceholderImage to `nitropage/data/media`.

### Patch Changes

- cf0a90d: Cleaned up the image/delete layout of `mediaData`.
- 6af80d2: Move sidebar-elements expand/shrink-icon to the left.
- 79e6b06: Removed `color` from the html attributes of ImageContainer.
- 350cf40: Cleaned up the upload/library layout of `mediaData`.
- 738d79a: The override checkbox for rteData now probably reacts when it is unchecked.
- b99ee91: Deleting a selected file in `mediaData` now resets the media ids length. This fixes a bug which blocked the user from selecting a new file, after they deleted another one.
- 9a8d13c: Made `selectData` item `title` optional. Items without a `title` will now alternatively show the `value` in the list.

## 0.1.0

### Minor Changes

- 8872da0: Simplified and cleared up the blueprint consumer API.
- 8872da0: Reworked the editor UI, adding a deep elements tree view, cleaned up the breadcrumbs, improved the element selection handles and added several large and small tweaks.

### [0.0.4](https://git.lufrai.com:222/nitropage/nitropage/compare/v0.0.3...v0.0.4) (2023-04-16)

### Bug Fixes

- move globby resolveRealPath to try / catch ([5841f72](https://git.lufrai.com:222/nitropage/nitropage/commit/5841f72f2852fa2ebf8b0b042434bd31d0d45827))
- use html conform sizes for SlashIcon ([1a7fe83](https://git.lufrai.com:222/nitropage/nitropage/commit/1a7fe836f9b8eb6a95e7dba2812bd5b10f4d1a47))

### [0.0.3](https://git.lufrai.com:222/nitropage/nitropage/compare/v0.0.2...v0.0.3) (2023-04-16)

### Bug Fixes

- exclude nitropage from optimizeDeps in flat node_modules environments ([4025577](https://git.lufrai.com:222/nitropage/nitropage/commit/40255774e8c929d5a819210483bae34e8f7f78b8))

### [0.0.2](https://git.lufrai.com:222/nitropage/nitropage/compare/v0.0.1...v0.0.2) (2023-04-15)

### 0.0.1 (2023-04-15)

### Features

- add env variables for nitropage auth ([3defbb4](https://git.lufrai.com:222/nitropage/nitropage/commit/3defbb43dc322a86780b588db0b334dc73256b05))
- add migrate option to import-prisma cli ([280a400](https://git.lufrai.com:222/nitropage/nitropage/commit/280a400d6cb9f0027e645e870790d17de6681179))
- add proper plus icon to ColorInput ([2de25cd](https://git.lufrai.com:222/nitropage/nitropage/commit/2de25cd4ac601b5cf0ef6905bef34f30926453c0))
- add server$ page list to example blueprint ([293fde2](https://git.lufrai.com:222/nitropage/nitropage/commit/293fde2ec8547164f574c3539ae56b73b41ec9fd))
- add standard-version ([6712176](https://git.lufrai.com:222/nitropage/nitropage/commit/671217678f4f32f295e12e88d5d2c1de56fc43ef))
- add support for colors with custom alpha ([f424fc2](https://git.lufrai.com:222/nitropage/nitropage/commit/f424fc203c900e1761b41f86931139da105c3f22))
- add toolbar lock icons ([6dd8fc4](https://git.lufrai.com:222/nitropage/nitropage/commit/6dd8fc40f544af83d3bb13124ac0262a281fa733))
- capitalize blueprint titles ([fcc3734](https://git.lufrai.com:222/nitropage/nitropage/commit/fcc3734cc3614693bbc5ef67f23ead19ee13430b))
- create pages unpublished ([de5ec08](https://git.lufrai.com:222/nitropage/nitropage/commit/de5ec088887509fd242ac3964c86a61be0ada818))
- disable overflow-x scroll in editor frame ([5982dd9](https://git.lufrai.com:222/nitropage/nitropage/commit/5982dd9013ecca77d13734d675c353e7f5fdc2db))
- handle iron unseal errors ([bb04564](https://git.lufrai.com:222/nitropage/nitropage/commit/bb04564957b66518fa691668f795e7f9ce72e667))
- implement admin Checkbox component ([75e8e64](https://git.lufrai.com:222/nitropage/nitropage/commit/75e8e6443bb16cde23444782f971761a55d118a3))
- implement admin sessions and users ([0f23b0c](https://git.lufrai.com:222/nitropage/nitropage/commit/0f23b0cce9998bcc646c4ec87b35d0e645044c1e))
- implement auth cookie renewal ([bbdfc77](https://git.lufrai.com:222/nitropage/nitropage/commit/bbdfc777dea84fe87644195a54c1ba1bf378657e))
- implement better blueprint file format ([cf80d6e](https://git.lufrai.com:222/nitropage/nitropage/commit/cf80d6ea2766017d34316d109c623e490f31f246))
- implement blueprint scaffold cli ([036943a](https://git.lufrai.com:222/nitropage/nitropage/commit/036943a2128c019f11d3bc9c77578ae46f253ac9))
- implement CSRF token ([a22778c](https://git.lufrai.com:222/nitropage/nitropage/commit/a22778c86ca9ea7f8f0e856d1834c1d213622df7))
- implement editor loading spinner ([df28934](https://git.lufrai.com:222/nitropage/nitropage/commit/df28934e3e23dd37a1bd0329a58d481a85db8724))
- implement example list blueprint ([2ab4c96](https://git.lufrai.com:222/nitropage/nitropage/commit/2ab4c969d4c91b924eaf1e7a6786d591fc6cbb6e))
- implement font data, improve editor ux and rte ([f88043b](https://git.lufrai.com:222/nitropage/nitropage/commit/f88043b03b12dfe216a8d996b1e68f22065171b6))
- implement HideSlot component ([81ce371](https://git.lufrai.com:222/nitropage/nitropage/commit/81ce371f2278e7018cd5744cdc711473761372f1))
- implement import-prisma cli command ([d63f06b](https://git.lufrai.com:222/nitropage/nitropage/commit/d63f06b2ccd447c49d55b9f74219db1dff8f2d2c))
- implement list data and optimize data ssr ([8f35a04](https://git.lufrai.com:222/nitropage/nitropage/commit/8f35a04139ed7f8e5eda7cc0e9b676cca08bf2da))
- implement mediaData ([98cdb8f](https://git.lufrai.com:222/nitropage/nitropage/commit/98cdb8f1023ca05d223ad6272ef21a8abcc2b9b7))
- implement page delete ([30ff481](https://git.lufrai.com:222/nitropage/nitropage/commit/30ff4813eaeaf12d5cefa5976778e14bdc38a800))
- implement page save, publish and revisions ([9dc5756](https://git.lufrai.com:222/nitropage/nitropage/commit/9dc5756e31d7c00aa491640232ff5eea77e12e81))
- implement page title ([b05a29c](https://git.lufrai.com:222/nitropage/nitropage/commit/b05a29c3122ff1f2bbcec8c5b32926fa92ac9173))
- implement richtext colors ([9df036c](https://git.lufrai.com:222/nitropage/nitropage/commit/9df036cbcabe186c7dc0ecf5a1368a6e10281629))
- implement textData ([31169af](https://git.lufrai.com:222/nitropage/nitropage/commit/31169af60ada548a8212d4a5d6691b93ba727253))
- import Root directly from nitropage ([b1013c9](https://git.lufrai.com:222/nitropage/nitropage/commit/b1013c9b04e1918bf6d00d951f2cf3ed32944cac))
- improve code splitting of zod ([abcdd83](https://git.lufrai.com:222/nitropage/nitropage/commit/abcdd836bf6fac948050ea1b7d273109b486e201))
- improve selected toolbar circle contrast ([a600429](https://git.lufrai.com:222/nitropage/nitropage/commit/a600429180cc9416e2f514a890e32d59e4537dac))
- initial commit ([d7b5b57](https://git.lufrai.com:222/nitropage/nitropage/commit/d7b5b57fdf5697086546ec99cad6a6fd6f988b59))
- logout from admin after death of cookie ([478d504](https://git.lufrai.com:222/nitropage/nitropage/commit/478d5047b6253c27a76210e1f41c89c98e59f1f8))
- lowercase example blueprints ([42cf9e5](https://git.lufrai.com:222/nitropage/nitropage/commit/42cf9e5fe585b8faed773ddb95756114b195b7a9))
- move peerDependencies to pnpm workspace ([a9b705a](https://git.lufrai.com:222/nitropage/nitropage/commit/a9b705a611a9a318ca0bb1d69423348b04f5a7d9))
- move toolbar to left side and add lock button ([41134cd](https://git.lufrai.com:222/nitropage/nitropage/commit/41134cd394ffece4c14181d931585d8f209e30df))
- move vite config changes to nitropage src ([a797e3c](https://git.lufrai.com:222/nitropage/nitropage/commit/a797e3c107af9e2c3ca5d0ecda3a2ac21d50ae58))
- only load page specific blueprints ([0f5aea1](https://git.lufrai.com:222/nitropage/nitropage/commit/0f5aea1228590ac8927b37267fb46949acda2bed))
- register quill globals only once ([cce6450](https://git.lufrai.com:222/nitropage/nitropage/commit/cce645016e2121ef443e8ed4173c8648d9bf2aea))
- remove shadow from RteInput BlueprintData ([d2428d3](https://git.lufrai.com:222/nitropage/nitropage/commit/d2428d37741bef48c3acd65a61e959c550a64805))
- rename colorData to cssData ([4db16e1](https://git.lufrai.com:222/nitropage/nitropage/commit/4db16e1e570e41074a77a1e00af01ee48079c007))
- rename slug field to urlPath ([bae19a5](https://git.lufrai.com:222/nitropage/nitropage/commit/bae19a5f245d51cc03eff392a6d90861f9b7fe15))
- render SettingsWrappers after HMR config is loaded ([fb122d7](https://git.lufrai.com:222/nitropage/nitropage/commit/fb122d778f0aa4d609b957f9a77fa35dc49310f7))
- scroll element into view vertically centered ([c221a9f](https://git.lufrai.com:222/nitropage/nitropage/commit/c221a9ff789cfc36fbdfc0bb4a95c92dae143fd0))
- show notification after saving or publishing page ([9cf1146](https://git.lufrai.com:222/nitropage/nitropage/commit/9cf1146c3c6449900e04915ac0922d277aa24e49))
- switch editor sidebar font to Inter ([2bcc425](https://git.lufrai.com:222/nitropage/nitropage/commit/2bcc425ed745e7aa069da99d1b1f6ffbd5f85ea4))
- update example blueprint ([61bcf3c](https://git.lufrai.com:222/nitropage/nitropage/commit/61bcf3cf2cd9bb8e002609226dda9cc2eb1612a5))
- update example blueprints to new blueprint format ([c78562a](https://git.lufrai.com:222/nitropage/nitropage/commit/c78562a8b4c521ebac9b185b3de1e22053f80465))
- use element history id in editor as frontend key ([f1b5aca](https://git.lufrai.com:222/nitropage/nitropage/commit/f1b5acae11d92a827ac21c5a7eb3a226d5a1647a))
- use HandMoveIcon in editor elementsTab list ([557dfd1](https://git.lufrai.com:222/nitropage/nitropage/commit/557dfd1239ab915e5bb8a7c0fc763978821cb75c))
- use hot config ([0a86849](https://git.lufrai.com:222/nitropage/nitropage/commit/0a868494dd274094587ff12065f1e05a57725bd2))
- use slate-700 color for sidebar element grab icon ([411ef6d](https://git.lufrai.com:222/nitropage/nitropage/commit/411ef6dcb85f8a722b5a25979cff5298c4f1e9ae))
- vite optimize nitropage dependencies early ([f0bc2a5](https://git.lufrai.com:222/nitropage/nitropage/commit/f0bc2a55d9aa519ed124e54ec547ac8bf659110b))

### Bug Fixes

- add block class to empty rte content check ([a1c19a7](https://git.lufrai.com:222/nitropage/nitropage/commit/a1c19a74a7482e3a2cb2c604408e06bf60b62319))
- add quotes around data-element scrollIntoView selector ([99a5e45](https://git.lufrai.com:222/nitropage/nitropage/commit/99a5e45d667455584df6d479ea44773f7320ca20))
- detect failed element insert and properly restart inserting ([b2e1c33](https://git.lufrai.com:222/nitropage/nitropage/commit/b2e1c337efe45cc3e83b26720e8c8b32b2ed1853))
- on insert cancel splice draft element with proper index ([84ea493](https://git.lufrai.com:222/nitropage/nitropage/commit/84ea4932ba6ea966870ea276e7ca2a9d3eb29f9d))
- remove overflow hidden from BlueprintDataInputLayout ([211f70d](https://git.lufrai.com:222/nitropage/nitropage/commit/211f70d8a9088ba3475e31487ca3490752b6689c))
- set fela specificityPrefix to avoid css priority clashes ([29ab240](https://git.lufrai.com:222/nitropage/nitropage/commit/29ab240274b07551ccb0073c6ab2b5399bff0385))
- update blueprint template in scaffolder cli ([e01fd39](https://git.lufrai.com:222/nitropage/nitropage/commit/e01fd390d706a07afd3d5ceb7b4ed2175e289e16))
