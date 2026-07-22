# Wanted Design System

A design system reconstructed from the **"Wanted Design System (Community)"** Figma
file — a large, real-world component library for **Wanted** (원티드), the Korean
job-search / career platform. The file also contains sub-brands referenced across
its pages: **Wanted Gigs** (short-term/part-time jobs), **Wanted Space** (coworking),
**Wanted Agent** (recruiter tooling), and **Wanted LaaS** (HR/People ops SaaS) — this
import focuses on the shared core system (colors, type, icons, and the primitive
component library) rather than any one product's screens, since the .fig is a
"Community" clone of the design system itself, not a specific product's file.

**Source:** Figma file "Wanted Design System (Community)" (mounted locally as a
read-only virtual filesystem for this import — no public share link was provided).
If you have the original Figma file, the frame/page names referenced throughout this
repo (`/1-Theme`, `/Color---Atomic`, `/3-Component`, `/Icon`, `/Logo`, …) map 1:1 to
its page list.

No product codebase or slide deck was attached — everything here comes from the
Figma file's components, Variables (tokens), and TEXT node styles.

---

## Index

- `styles.css` — root stylesheet; import this one file.
- `tokens/` — `fonts.css` (webfont imports), `base.css` (type scale, radii, shadow,
  spacing — hand-authored from literal values seen across the kit), `fig/fig-tokens.css`
  (all 488 Figma Variables, generated), `fig/fig-typography.css` (generated; empty —
  see Typography note below).
- `assets/logos/` — Wanted wordmark, symbol, vertical lockup, favicon (materialized
  as real vector components, not raster).
- `assets/icons/` — 223 icon glyphs as `icon-data.js` + an `<Icon name="…">` wrapper.
- `components/` — reusable primitives, grouped by concern (see Components below).
- `guidelines/` — foundation specimen cards (color, type, spacing, radii, elevation,
  logo, icon-set previews) that populate the Design System tab.

## Components

Grouped by directory. Every component reads styling from the token CSS custom
properties in `styles.css`. All were materialized directly from the Figma kit's
own component definitions — geometry, spacing, and color values are copied verbatim,
not rounded to a grid.

**`components/button/`** — ButtonButton (the 48-variant master Button: solid/outlined
× primary/assistive × sm/md/lg × icon-only × disabled), ButtonTextButtonPrimary,
ButtonRoundButtonPrimary, ButtonIconSolid, plus internal helpers (CircularCircularButton
spinner, IconsIconsButton/IconIcons/IconIcons2 icon slots, InteractionLightButton/
InteractionNormal/InteractionStrong hover-state overlays, DecorateInteraction(Normal),
RatioVertical, IconNormalBlank, IconsIconsResponsive).

**`components/badge/`** — BadgeStatus (availability dot), BadgeValue (numeric/text
pill), BadgePush (notification push badge), IconNormalDot3, RatioVertical2Badge.

**`components/chip/`** — CategoryCategory (the 16-variant category tab bar),
CategoryResourceChip… (Normal/Alternative × XSmall–Large, 8 size/style combinations),
ChipChip (24-variant filter chip), ChipFilter (dropdown filter chip), ButtonIconNormal,
GradientResourceMaskBase (edge-fade mask for scrollable chip rows), plus shared
interaction/icon/ratio helpers.

**`components/avatar/`** — AvatarAvatar (30-variant: person/company/academic ×
5 sizes × placeholder), AvatarAvatarGroup (stacked avatars), AvatarResourceImage/
Placeholder helpers for Person/Company/Academy, PushBadgePushBadge (avatar
notification dot), AvatarResourceAvatarGroupTrailing, ButtonTextAvatar.

**`components/selection/`** — ControlCheckbox (24 variants: size × state × tight ×
disabled), ControlRadio (16 variants), ControlSwitch (8 variants), plus their icon
primitives (check mark, dot, line).

**`components/card/`** — CardCard (content/job card, platform × skeleton),
CardListCard (compact list row card), CardResourceNormalSave / ListTrailingContent
(bookmark affordance), CardResourceNormalTopContent, ThumbnailThumbnail, GradientSolid,
SkeletonRectangle/SkeletonText (loading placeholders), RatioHorizontal, ControlToggleIcon2.

**`components/alert/`** — AlertAlert (platform-aware alert), AlertResourceDialog
(confirm/cancel dialog shell), AlertResourceAction, PresentationAlertResourceBackground,
ButtonText (text-button used inside alerts), CircularCircular (spinner).

**`components/navigation/`** — BottomNavigationBottomNavigation (3-platform tab bar:
iOS/Android/Web), BottomNavigationResourceContent, BottomNavigationResourceTabWeb,
IconNavigationRecruit/Career/Social/MyPage/Menu (the 5 primary nav glyphs),
SpacingBottomSafeArea4/5 (device safe-area fillers).

**`components/forms/`** — BasicDivider (horizontal/vertical rule), AutoCompleteAutoComplete
(the 10-variant search auto-complete dropdown), AutoCompleteResourceItemAction/Title,
CellResourceTrailingContentValue, CheckboxResourceControl, ListCellResourceLeadingContent(3),
ScrollBarScrollBar.

**`components/feedback/`** — ToastToast (4-variant toast/snackbar), TooltipTooltip
(+ TooltipResourceMedium/SmallArrow variants for placement), ContentBadgeContentBadge
(12-variant inline content badge), CircularWanted (brand-mark loading spinner),
ActionAreaActionArea (sticky bottom action-bar shell), ActionAreaResourceActions/
CompactPreset/ExtraPreset (its button/chip content presets), ChipMultiSelect
(6-variant multi-select chip), CheckMarkResourceControl (16-variant checkmark
control), CustomGradient (decorative gradient), DecorateDimmer (scrim overlay),
IconNormalCircleCheck2/CircleExclamation2/CircleInfo2/TriangleExclamation2 (toast
status glyphs), ControlCheckMark, SafeAreaBottom.

**`assets/icons/Icon.jsx`** — `<Icon name="…" size={24} />` wrapper over 223
materialized glyphs (outline + filled pairs, arrows, chevrons, social/brand logos,
navigation icons). See `Icon.d.ts` for the full name list.

**`assets/logos/`** — LogoHorizontalWantedBlack/White, LogoVerticalWantedBlack/White,
LogoCircleWantedBlack/White, LogoWantedFavicon, plus their underlying
LogoResourceAssetSymbolWanted / LogoResourceAssetLogotypeWanted6 vector primitives.

### Coverage vs. the source file

The source Figma file defines **770 component sets + 315 standalone symbols
(≈959 total families)** — an entire company's product-wide component library
spanning 20+ pages (auth, job listings, resumes, chat, community feed, career
content, LaaS admin screens, iOS/Android/Web platform variants, etc).

This import builds **312 components across 13 directories**: the shared visual
primitives (Button, Badge, Chip/Category, Avatar, Checkbox/Radio/Switch, Card,
Alert, Bottom Navigation, Divider/AutoComplete, Toast/Tooltip/ContentBadge/ActionArea,
Select/SegmentedControl/Tab/Snackbar/TopNavigation, TextField/Popover/Footer/Pagination,
Modal/BottomSheet) plus their internal helper parts, the full 223-glyph icon set,
and the full logo lockup set. It intentionally does NOT build the hundreds of
product-specific compositions (resume builder cells,
chat bubbles, community post cards, LaaS admin tables, per-screen "Content" variants,
academy/company instance-specific avatars, etc.) — those are one-off screen
assemblies built FROM these primitives, not additional primitives themselves.

**Tokens and typography are at full coverage**: all 6 Variable collections (488
variables: Atomic, Ungrouped, Theme, Modal, Component, Frame — including every
theme mode: Light/Dark, Mobile/Desktop, and the 4 density modes Small/Large/
XLarge/Xlarge) are in `tokens/fig/fig-tokens.css`. The file defines **no named
TEXT/EFFECT styles** — every text layer sets font-family/size/weight/line-height
literally per-node — so there is no `fig-typography.css` content to extract;
the type scale in `tokens/base.css` was instead reverse-engineered from the
literal sizes repeated across hundreds of TEXT nodes (see METADATA's font-size
histograms) and cross-checked against the Component/Frame page specimens.

**To extend coverage**, re-attach the .fig and run `fig_materialize` against any
of the ~647 remaining families listed in `/METADATA.md`'s "Component families"
section (e.g. Resume/Career-specific cards, Chat bubble variants, LaaS admin
table rows, Date Picker, Rating, Stepper, File Upload, Table, Comment, Job/
Community post cards) — group them into `components/<concern>/` the same way
this pass did. When a materialize batch re-extracts a shared low-level primitive
(icon/interaction-state/ratio-box) that another directory already owns, delete
the duplicate and re-point its importer(s) at the canonical copy (see e.g.
`components/overlay/*Ovl.jsx` for the pattern) rather than shipping two
competing definitions.

**`components/navigation2/`** — a second navigation/input batch: SelectSelect
(dropdown select field), SegmentedControlSegmentedControl (solid/outlined segmented
tabs), TabTab (underline tab), SnackbarSnackbar, TopNavigationTopNavigation
(desktop header bar) + its resource parts (Leading/Trailing/Action Normal/Float,
ToolTab/ToolSegmented, Contents), MenuMenu + MenuResourceItemCell/ActionArea
(dropdown menu), ListCellListCell, RadioResourceControl, ButtonIconBackground,
GradientMask/GradientResourceMaskSize, IconNormalChevronDown3/Up3/Right2.
(Its internal helpers that duplicate other directories' primitives — Avatar,
Button, Interaction states, Ratio boxes, etc. — re-export the canonical copy
from its home directory rather than redefining it, suffixed `…Nav2`.)

**`components/forms2/`** — TextinputTextfield (the single-line text-input master
component: normal/positive/negative status × active/focus × leading/trailing
content), TextinputResourceBackground/Interaction/TextfieldTrailingContent/
TextfieldButton (its resource parts), PopoverPopover + PopoverResourceContents,
FooterFooter (site footer), PaginationDots + PageIndicatorResourceDotNormal(2) +
PaginationResourceDotSmallAdaptive/White (carousel/pagination dots),
LogoWantedLogoHorizontal3, LogoResourceNormalHorizontalWanted11,
LogoWantedResourceRatio2, ButtonText3, IconsIcons4, CircularCircular2,
InteractionLight2, InteractionNormal2, IconNormalBlank5.

**`components/overlay/`** — ModalResourceModal (bottom-sheet/dialog shell),
ModalResourceNavigation (its header bar) + ResourceContents/2/3/4 and
ResourceTool/2 (tab/segmented-control slot variants), ModalResourceHandle
(drag handle), ModalResourceContentsCustom, ButtonText2, TopNavigationResourceLeadingDefault.

### Coverage & scope decision (read this first)

**312 of 959 families are built. The remaining ~647 are intentionally not
built**, for these concrete reasons — verified by searching the source file
directly, not assumed:

1. **~255 of the 315 "standalone" symbols are named content instances, not
   reusable primitives** — e.g. `Avatar/Resource/Image/Company/네이버` (a Naver
   logo baked into one avatar instance), `Avatar/Resource/Image/Person/짱구`
   (a specific illustrated person), `Avatar/Resource/Image/Academy/고려대`
   (Korea University). These are pre-filled *data*, not components a consumer
   would reuse — the generic shape they all share (`Avatar/Resource/Image/
   Company`, `/Person`, `/Academic`) IS built, in `components/avatar/`.
2. **A large share of the 770 "sets" are duplicate/legacy re-declarations of
   the same component on older pages.** This file carries at least two parallel
   organizations of the same design system: a newer, cleaned-up `/1-Theme
   /2-Element/3-Component` tree and an older flat `/Component`, `/Component2`,
   `/Basic`, `/Decorate`, `/Element` tree with duplicate names (e.g. `Control/
   Checkbox` appears 3 times across pages with different variant counts —
   3, 3, and 48 — because it's the same control redefined at different points
   in the file's history). We built the fullest/newest version of each; the
   older duplicates are superseded, not missing.
3. **Deep icon-state permutations were consolidated, not skipped.** The
   `Decorate/Opacity` (15/15/15/17-variant) and `Decorate/Interaction` families
   are per-state overlay swatches already represented by the single
   `Interaction{Normal,Light,Strong}` components we built — enumerating every
   opacity step as a separate "component" would just be re-listing token
   values, which already live in `tokens/fig/fig-tokens.css`.
4. **Screen-specific one-off compositions were not built as primitives**, per
   the instructions governing this import (build the shared component
   library, not the product screens) — things like `Content` (19 variants of
   one job-detail page's body states), `Arrow with Texts`/`Arrow with Texts -
   Algorithm` (a one-off diagram on a single explainer frame), `agent alt 3`
   (an illustration variant used once). These are page content, not design-
   system components.
5. **Genuinely new, reusable families we have NOT yet built** (real gaps, not
   exclusions): Date Picker, autocomplete's remaining item-cell variants,
   deeper Menu/Dropdown state permutations, and the LaaS/Agent/Space
   sub-brand-specific screens implied by the file's page list but not present
   as extractable components on the pages this pass covered. These are the
   best next candidates if coverage should keep growing — re-attach the .fig
   and materialize them the same way this pass did (see the pattern in
   `components/overlay/*Ovl.jsx` for de-duplicating shared primitives across
   directories).

Every family we DID build is named in the full export list below and grouped
by directory above; nothing in that list is a placeholder or a stub.

### Full component export list

Every `<Name>` exported to `window.WantedDesignSystem_*` (public primitives above,
plus their internal sub-parts — icons, ratio boxes, interaction overlays — which
compile as components too since they carry sibling `.d.ts` files):

AlertAlert, AlertResourceAction, AlertResourceDialog, AutoCompleteAutoComplete,
AutoCompleteResourceItemAction, AutoCompleteResourceItemTitle, AvatarAvatar,
AvatarAvatarGroup, AvatarResourceAvatarGroupTrailing, AvatarResourceImageAcademy,
AvatarResourceImageCompany, AvatarResourceImagePerson3,
AvatarResourceImagePerson3Navigation, AvatarResourcePlaceholderAcademy,
AvatarResourcePlaceholderCompany, AvatarResourcePlaceholderPerson2, BadgePush,
BadgeStatus, BadgeValue, BasicDivider, BottomNavigationBottomNavigation,
BottomNavigationResourceContent, BottomNavigationResourceTabWeb, ButtonButton,
ButtonIconNormal, ButtonIconSolid, ButtonRoundButtonPrimary, ButtonText,
ButtonTextAvatar, ButtonTextButtonPrimary, CardCard, CardListCard,
CardResourceListLeadingContent, CardResourceListTrailingContent2,
CardResourceNormalSave, CardResourceNormalTopContent, CategoryCategory,
CategoryResourceChipAlternativeLarge, CategoryResourceChipAlternativeNormal,
CategoryResourceChipAlternativeSmall, CategoryResourceChipAlternativeXSmall,
CategoryResourceChipNormalLarge, CategoryResourceChipNormalNormal,
CategoryResourceChipNormalSmall, CategoryResourceChipNormalXSmall,
CellResourceTrailingContentValue, CheckboxResourceControl, ChipChip, ChipFilter,
CircularCircular, CircularCircularAvatar, CircularCircularButton, ControlCheckbox,
ControlRadio, ControlSwitch, ControlToggleIcon2, DecorateInteraction,
DecorateInteractionChip, DecorateInteractionNormal, GradientResourceMaskBase,
GradientSolid, Icon, IconIcons, IconIcons2, IconIcons2Chip, IconNavigationCareer,
IconNavigationMenu, IconNavigationMyPage, IconNavigationRecruit,
IconNavigationSocial, IconNormalBlank, IconNormalBlank3, IconNormalBlank3Avatar,
IconNormalBlank3Button, IconNormalBlank3Card, IconNormalBlank3Chip,
IconNormalBlank3Forms, IconNormalBlank3Navigation, IconNormalBlankChip,
IconNormalBookmark2, IconNormalCheck, IconNormalCheck3, IconNormalChevronDown,
IconNormalChevronUp, IconNormalDot, IconNormalDot3, IconNormalLineHorizontal,
IconNormalLineHorizontal3, IconsIcons, IconsIconsAvatar, IconsIconsButton,
IconsIconsChip, IconsIconsForms, IconsIconsResponsive, InteractionLight,
InteractionLightAvatar, InteractionLightButton, InteractionLightChip,
InteractionLightForms, InteractionNormal, InteractionNormalAvatar,
InteractionNormalButton, InteractionNormalCard, InteractionNormalChip,
InteractionNormalForms, InteractionStrong, InteractionStrongChip,
ListCellResourceLeadingContent, ListCellResourceLeadingContent3,
LogoCircleWantedBlack, LogoCircleWantedWhite, LogoHorizontalWantedBlack,
LogoHorizontalWantedWhite, LogoResourceAssetLogotypeWanted6,
LogoResourceAssetSymbolWanted, LogoVerticalWantedBlack, LogoVerticalWantedWhite,
LogoWantedFavicon, PresentationAlertResourceBackground, PushBadgePushBadge,
PushBadgePushBadgeChip, RatioHorizontal, RatioVertical, RatioVertical2,
RatioVertical2Avatar, RatioVertical2Badge, RatioVertical2Button,
RatioVertical2Card, RatioVertical2Chip, RatioVertical2Forms,
RatioVertical2Navigation, RatioVerticalChip, RatioVerticalSelection,
ScrollBarScrollBar, SkeletonRectangle, SkeletonText, SpacingBottomSafeArea4,
SpacingBottomSafeArea5, ThumbnailResourceOverlayCustom, ThumbnailThumbnail.

Also from `components/feedback/`: ActionAreaActionArea, ActionAreaResourceActions,
ActionAreaResourceCompactPreset, ActionAreaResourceExtraPreset,
CheckMarkResourceControl, ChipMultiSelect, CircularWanted, ContentBadgeContentBadge,
ControlCheckMark, CustomGradient, DecorateDimmer, GradientSolid2,
IconNormalCircleCheck2, IconNormalCircleExclamation2, IconNormalCircleInfo2,
IconNormalTriangleExclamation2, SafeAreaBottom, ToastToast,
TooltipResourceMediumArrow, TooltipResourceMediumArrowHorizontal,
TooltipResourceMediumArrowVertical, TooltipResourceSmallArrow,
TooltipResourceSmallArrowHorizontal, TooltipResourceSmallArrowVertical, TooltipTooltip.

Also from `components/navigation2/`: ButtonIconBackground, GradientMask,
GradientResourceMaskSize, IconNormalChevronDown3, IconNormalChevronRight2,
IconNormalChevronUp3, ListCellListCell, ListCellResourceLeadingContent2,
MenuMenu, MenuResourceActionAreaLeading, MenuResourceActionAreaTrailing,
MenuResourceItemCell, RadioResourceControl, SegmentedControlResourceKnob,
SegmentedControlSegmentedControl, SelectResourceBackground, SelectResourceChip,
SelectResourceLeadingContent, SelectSelect, SnackbarSnackbar, SpacingStatus5,
SpacingStatus6, TabResourceTab, TabTab, TextinputResourceInteraction,
TopNavigationResourceActionFloat, TopNavigationResourceActionFloat2,
TopNavigationResourceActionNormal, TopNavigationResourceContents,
TopNavigationResourceLeadingFloat, TopNavigationResourceLeadingNormal,
TopNavigationResourceLeadingNormal2, TopNavigationResourceLeadingNormal3,
TopNavigationResourceTrailingNormal,
TopNavigationResourceToolSegmented, TopNavigationResourceToolTab,
TopNavigationTopNavigation, plus the `…Nav2`-suffixed re-exports of primitives
already listed above: AvatarAvatarNav2, AvatarResourceImageAcademyNav2,
AvatarResourceImageCompanyNav2, AvatarResourceImagePerson3Nav2,
AvatarResourcePlaceholderAcademyNav2, AvatarResourcePlaceholderCompanyNav2,
AvatarResourcePlaceholderPerson2Nav2, ButtonButtonNav2, ButtonIconNormalNav2,
ButtonTextNav2, CellResourceTrailingContentValueNav2, CheckboxResourceControlNav2,
CircularCircularNav2, GradientResourceMaskBaseNav2, IconNormalBlank3Nav2,
IconNormalCheck3Nav2, IconNormalCircleExclamation2Nav2, IconNormalDot3Nav2,
IconNormalLineHorizontal3Nav2, IconsIconsNav2, InteractionLightNav2,
InteractionNormalNav2, InteractionStrongNav2, ListCellResourceLeadingContentNav2,
ListCellResourceLeadingContent3Nav2, PushBadgePushBadgeNav2, RatioVertical2Nav2,
ScrollBarScrollBarNav2.

Also from `components/forms2/`: AutoCompleteResourceItemActionF2, ButtonButtonF2,
ButtonIconNormalF2, ButtonText3, CircularCircular2, CircularCircularF2,
ContentBadgeContentBadgeF2, FooterFooter, IconNormalBlank3F2,
IconNormalCircleCheck2F2, IconNormalCircleExclamation2F2, IconsIcons4, IconsIconsF2,
InteractionLight2, InteractionLightF2, InteractionNormal2, InteractionNormalF2,
InteractionStrongF2, LogoResourceAssetLogotypeWanted6F2, LogoResourceAssetSymbolWantedF2,
LogoResourceNormalHorizontalWanted11, LogoWantedLogoHorizontal3, LogoWantedResourceRatio2,
PageIndicatorResourceDotNormal, PageIndicatorResourceDotNormal2, PaginationDots,
PaginationResourceDotSmallAdaptive, PaginationResourceDotSmallWhite, PopoverPopover,
PopoverResourceContents, PushBadgePushBadgeF2, RatioHorizontalF2, RatioVertical2F2,
RatioVertical3, TextinputResourceBackground, TextinputResourceInteraction,
TextinputResourceTextfieldButton, TextinputResourceTextfieldTrailingConten,
TextinputTextfield. Plus `components/navigation2/TextinputResourceInteractionNav2`
(re-export of the forms2 canonical copy).

Also from `components/overlay/`: ActionAreaResourceActionsOvl,
ActionAreaResourceCompactPresetOvl, ButtonButtonOvl, ButtonIconNormalOvl,
ButtonText2, ButtonTextOvl, ChipChipOvl, CircularCircularOvl,
GradientResourceMaskBaseOvl, GradientSolid2Ovl, GradientSolidOvl,
IconNormalBlank3Ovl, IconNormalCheck3Ovl, IconNormalCircleInfo2Ovl, IconsIconsOvl,
InteractionLightOvl, InteractionNormalOvl, InteractionStrongOvl,
ModalResourceContentsCustom, ModalResourceHandle, ModalResourceModal,
ModalResourceNavigation, ModalResourceNavigationResourceContents,
ModalResourceNavigationResourceContents2, ModalResourceNavigationResourceContents3,
ModalResourceNavigationResourceContents4, ModalResourceNavigationResourceTool,
ModalResourceNavigationResourceTool2, PushBadgePushBadgeOvl, RatioVertical2Ovl,
RatioVertical3Ovl, SafeAreaBottomOvl, SegmentedControlResourceKnobOvl,
SegmentedControlSegmentedControlOvl, SpacingBottomSafeArea4Ovl,
SpacingBottomSafeArea5Ovl, TabResourceTabOvl, TabTabOvl,
TopNavigationResourceActionNormalOvl, TopNavigationResourceLeadingDefault,
TopNavigationResourceLeadingNormalOvl.

### Intentional additions

- **`Icon.jsx`** — a thin `<Icon name size style>` wrapper is not a Figma component
  itself; it's the standard glue for consuming the 223-glyph `icon-data.js` map.

---

## Content fundamentals

Pulled from the Korean copy embedded in the kit's cards, dialogs, and category
lists (job categories, dialog copy like "정말 삭제하시겠어요?", section descriptions
like "일관된 브랜드 아이덴티티와 시각적 스타일을 유지하기 위해 정의된 색상 모음입니다.").

- **Language**: Korean-first UI copy throughout (job categories, nav labels,
  dialog text); English is used for component/token *names* only (e.g.
  "Primary Button", "Category/Chip/Normal"). Any product built on this system
  for a Korean audience should default to Korean copy.
- **Tone**: plain, direct, functional — documentation-style sentences with no
  exclamation points or forced enthusiasm ("정의된 색상 모음입니다" = "This is the
  defined color set," not "Check out our colors!").
  Descriptions read like an internal design-team handbook, not marketing copy.
  This tracks with Wanted's product identity as a job-search platform: users are
  professionals evaluating job opportunities, not casual consumers being sold to.
- **Formality**: uses the formal/polite Korean sentence ending (합니다/입니다) rather
  than casual speech — appropriate for a professional recruiting product.
- **Numerals**: salary and count figures render in monospace (SF Mono) — signals
  "this is a precise, scannable number" (e.g. compensation, view counts).
- **Emoji**: none observed in UI copy. A small number of 💎 (diamond) glyphs appear
  as internal Figma *layer-naming* annotations on premium/paid avatar variants —
  that's a file-organization convention, not product-facing emoji usage.
- **Confirmation dialogs**: phrased as direct questions to the user ("~하시겠어요?"
  pattern), not declarative warnings — keeps the tone conversational even in
  formal register.

## Visual foundations

- **Color**: a large neutral ramp (`Common`/`Cool-Neutral`, 0–100 steps) carries
  almost all UI chrome — `rgb(0,0,0)` and `rgb(255,255,255)` alone account for
  the two most-used fills/text colors in the entire file. A single blue
  (`rgb(0,102,255)` / `--primary-normal`) is the sole primary brand color, used
  sparingly for CTAs and links. A small accent palette (violet, pink, red-orange,
  lime, cyan, green, orange) exists for category tags and content badges only —
  never for primary actions. Status colors (positive green, cautionary orange,
  negative red) are distinct from the accent palette.
- **Type**: Pretendard JP end-to-end (Medium for body/UI at 14–16px, SemiBold for
  emphasis/labels, Bold for headings 24–56px) — a Korean/Japanese/Latin variable
  typeface, not a Latin-only web font. Wanted Sans appears only 16–30 times in the
  whole file (vs. thousands of Pretendard JP uses) — reserved for a handful of
  large marketing/display moments, not general UI. Tracking is slightly negative
  on headings (-0.027em) and slightly positive on body copy (0.006em) — typical
  Korean-optimized letter-spacing.
- **Spacing**: 4px-based scale; the Frame/Component token collections encode this
  directly as `Padding/Horizontal` `Padding/Vertical` pairs that change per density
  mode (Small=12/4, Large=20/4, XLarge=24/8).
- **Backgrounds**: flat solid fills dominate; no full-bleed photography or
  hand-drawn illustration patterns were found in the extracted assets. The few
  large raster images in METADATA's "Images" list are large hero/profile photos
  (product photography), not decorative patterns. No repeating textures or noise
  grain observed. No gradients used for backgrounds generally — a few `Custom
  Gradient` and `Background Gradient` components exist as isolated decorative
  elements (e.g. card top-fade), not a system-wide motif.
- **Cards / elevation**: the signature elevation move is an **inset 1px hairline
  border-shadow** (`box-shadow: inset 0 0 0 1px rgba(112,115,124,0.22)`) on
  resting cards — not an outer drop shadow. Outer shadows are reserved for
  popovers/menus and dialogs (soft, low-opacity, multi-layer). This is captured
  as `--shadow-card` / `--shadow-popover` / `--shadow-dialog` in `tokens/base.css`.
- **Corner radii**: cards and large surfaces use large radii (20–32px); buttons
  and controls use smaller radii (8–16px); pills/tags/avatars are fully round.
  Radius tokens scale UP with density mode (Small=12 → XLarge=20 for the shared
  `--radius` primitive) rather than staying fixed.
- **Borders**: line/stroke colors are all low-opacity black (`rgba(112,115,124,
  0.22–0.32)`) rather than solid grays — this is what gives the "hairline" look
  its softness at both light backgrounds.
- **Hover / press states**: a dedicated `Decorate/Interaction` component family
  (Normal/Light/Strong states) provides a semi-transparent black/white overlay
  for press/hover feedback rather than darkening or lightening the base fill
  color directly — this is a deliberate overlay system, reusable over any
  background color.
- **Shadows (popover/dialog)**: layered, low-opacity black shadows
  (`rgba(23,23,23,0.06–0.12)` at increasing blur/offset) — soft and diffuse,
  never a hard drop shadow.
- **Transparency / blur**: `Background/Transparent` tokens (`rgba(255,255,255,
  0.08/0.28)`) exist for overlays on top of imagery/scrims; no backdrop-blur
  usage was found in the extracted geometry.
- **Animation**: `Circular/Circular` (Animate: true/false variant) is the only
  explicit animation-bearing component — a loading spinner. No easing/duration
  tokens exist in the Variable collections, implying animation choices are left
  to implementation rather than systematized.
- **Imagery color vibe**: the largest extracted raster assets are neutral
  product/profile photography (JPEG, several MB) — no consistent color-grade
  or filter is inferable from geometry alone; treat as ordinary photography,
  not stylized/branded imagery.

## Iconography

- **System**: a single in-house icon family (not a public icon font/library) —
  ~223+ glyphs on a 24×24 grid, each with `Fill: true/false` variants (outline vs.
  filled) and some with `Thick`/`Tight`/`Small` size variants (chevrons, arrows).
  Extracted as flat SVG path data in `assets/icons/icon-data.js` (not a webfont).
- **Usage**: single-color glyphs that paint with `currentColor` — recolor via CSS
  `color`, matching the Wanted convention of icons inheriting surrounding text/
  label color rather than carrying fixed colors.
  Every icon is a `24px` viewBox by default; component variants that need smaller
  renditions (bottom-nav tab icons, chevrons) use the `Small`/`Tight` variants
  rather than just scaling the same glyph down.
- **Brand/social logos**: Apple, Google, Facebook, Kakao, Instagram, LinkedIn,
  Naver Blog, YouTube, Microsoft, X, Brunch — all included as icon-family members
  (used for social login buttons), extracted alongside the general icon set.
  These render actual brand marks (source geometry), not our approximations.
  **Not** a Wanted-original mark — reproduce these only for their standard "sign in
  with X" purpose, not as decoration.
- **Emoji / unicode-as-icon**: none found; the only non-icon glyph usage is the
  💎 layer-naming convention mentioned above (internal Figma organization only).
- **Format**: SVG path data (not PNG/raster icons) throughout — consistent with a
  scalable, single-color icon system.

## Logo

The Wanted wordmark (horizontal/vertical lockups + circular symbol + favicon) was
extracted directly from the file's `/Logo` page as real vector geometry — see
`assets/logos/`. Black/White/Dark/Light color variants all exist in the source;
this import materializes the Black and White variants (add more with
`fig_materialize` against the remaining `Logo…Dark`/`…Light` component names if
needed). Sub-brand lockups (Wanted Gigs, Wanted Space, Wanted Agent, Wanted LaaS,
Wanted OneID) also exist in the source under the same page and can be pulled the
same way.

---

## Sources referenced

- Figma file: **"Wanted Design System (Community)"** (attached to this project as
  a mounted, read-only virtual filesystem — no public URL was provided by the user).
- No GitHub repository, codebase, or slide deck was attached to this project.
