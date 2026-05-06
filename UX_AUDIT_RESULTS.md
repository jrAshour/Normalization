# Direct App · UX Normalization Report
**Role:** Senior Lead Product Designer
**Date:** 2026-05-03 | **Locale:** ar-SA RTL | **Source:** Live app screenshots (15 screens)
**Method:** Pick the best EXISTING pattern from within the app. Zero new design. Apply everywhere.

---

## How to Read This Report

Each section = one interaction pattern.
For every pattern: what each product currently does → which one wins → the normalization rule.
The winning pattern is already in the app — just needs to be copied to the others.

---

## PATTERN 01 · Page Header

### What each product does today

| Product | Header Title | Right Action | Notes |
|---|---|---|---|
| Flights | "Direct" (brand) | `>` — unlabeled | Brand name ≠ page context |
| Hotels | "Direct" (brand) | `>` — unlabeled | Same problem |
| Visas (tab) | "Direct" (brand) | `>` — unlabeled | Same problem |
| Packages | "اختر رحلتك" | `>` — unlabeled | ✅ Contextual title |
| Visa Requirements | "متطلبات التأشيرة" | 🔍 search | ✅ Contextual title + recognizable icon |
| Home (الرئيسية) | Partial brand + user icon | 👤 | Different structure |
| Any modal open | "Direct" dims to dark brown | — | Good focus dimming ✅ |

### Winner → **Visa Requirements** header pattern
Contextual page title + recognizable right-action icon.

### Normalization Rule

```
ALL headers must follow this structure:
┌─────────────────────────────────────────┐
│  [← back — only on drill-down screens]  │
│      [Page Title — describes THIS page] │
│                           [Action icon] │
│  bg: #FF6B00 | text: white bold 18px    │
│  height: 56px                           │
└─────────────────────────────────────────┘
```

| Product | Title to use | Right icon |
|---|---|---|
| Flights | `البحث عن رحلات` | 🕐 (recent searches) |
| Hotels | `البحث عن فنادق` | 🕐 (recent searches) |
| Visas | `طلب تأشيرة` | — (no action needed) |
| Packages | `اختر رحلتك` ✅ already correct | — |
| Visa Requirements | `متطلبات التأشيرة` ✅ already correct | 🔍 ✅ already correct |
| Study Abroad | `الدراسة في الخارج` | — |
| Int'l License | `رخصة القيادة الدولية` | — |
| eSIM | `الشريحة الدولية` | — |
| Supporting Services | `خدمات المساندة` | — |

---

## PATTERN 02 · Back Button / Sheet Dismiss

### What each product does today

| Product | Back mechanism | Close button | Verdict |
|---|---|---|---|
| All root tabs | No back button (correct) | — | ✅ Correct |
| Flights airport picker | Drag handle only | ❌ None | ❌ Missing |
| Visa country picker | Drag handle only | ❌ None | ❌ Missing |
| Class/Pax picker | Drag handle only | ❌ None | ❌ Missing |
| Packages month picker | Drag handle only | ❌ None | ❌ Missing |

### Winner → **None currently exists** — but the drag handle pill is present on ALL sheets

### Normalization Rule

The drag handle is already there on every sheet. **Add a `×` close button at the same position on all sheets.** No new visual language — reuse the existing icon library.

```
Every bottom sheet:
┌──────────────────────┐
│    ▬ drag handle     │  ← already exists ✅
│                  [×] │  ← ADD THIS — top-left (RTL) 44×44px touch target
│   Sheet Title        │
│   ...content...      │
│  [تأكيد / CTA]       │
└──────────────────────┘

Touch target: 44×44px minimum
Position: top-left corner of sheet (RTL = top-right side of sheet)
Icon: × from existing icon set
```

Apply to: ALL 4 observed sheets (Airport, Country, Class/Pax, Month) and any future sheets.

---

## PATTERN 03 · Form Field Row

### What each product does today

| Product | Field structure | Chevron | Icon | Verdict |
|---|---|---|---|---|
| Flights | `[∨]` placeholder `[✈/📅/👥]` | Left (RTL ✅) | Right | ✅ Best |
| Hotels | `[∨]` placeholder `[📍/📅/👤]` | Left (RTL ✅) | Right | ✅ Same |
| Visas tab | `[∨]` placeholder `[🌐]` | Left (RTL ✅) | Right | ✅ Same |

### Winner → **Flights / Hotels / Visas** — all identical, already normalized ✅

### Normalization Rule

All three search products already share the exact same field pattern. **Packages and Supporting Services must adopt it** for any search/filter inputs they introduce.

```
Field anatomy (RTL):
┌────────────────────────────────────────┐
│ [∨]   placeholder text           [icon]│
│       or selected value                │
└────────────────────────────────────────┘
Height: 52px | Border: 1px #E5E5E5 | Radius: 8px
Chevron: left side | Context icon: right side
```

---

## PATTERN 04 · Bottom Sheet Picker (Search-in-Sheet)

### What each product does today

| Sheet | Search bar | Tabs | Row content | Selection feedback |
|---|---|---|---|---|
| Flights airport picker | ✅ "من أين تود أن تسافر؟" | ✅ من / إلى | ✅ IATA + City bold + Country | ✅ Orange row highlight |
| Visa country picker | ✅ "ابحث هنا" | ❌ None (single direction) | ✅ Flag emoji + Country name | ❌ No selection highlight |
| Class/Pax picker | ❌ No search | ❌ N/A | Radio + stepper | ✅ Orange radio fill |
| Month picker | ❌ No search | ❌ N/A | Month pills (greyed) | ❌ Not working |

### Winner → **Flights airport picker** — most complete: search + tabs + rich rows + selection feedback

### Normalization Rule

For any sheet that presents a **selectable list** (country, city, program, destination):

```
Sheet structure:
┌──────────────────────────────────────┐
│  ▬           [sheet title]       [×] │
│  [tab1 (active)] [tab2]              │  only if >1 direction
│  ┌──────────────────────────────┐   │
│  │ 🔍  ابحث هنا                 │   │  always show search
│  └──────────────────────────────┘   │
│  [icon]  [Primary label bold]        │  row anatomy
│          [Secondary label muted]     │
│  ─────────────────────────────────   │  divider
│  [selected row = orange bg tint]     │  ← copy from flights
└──────────────────────────────────────┘
```

Apply to: Visa country picker (add selection highlight), Month picker (fix pill states), any future list picker.

---

## PATTERN 05 · List Row Anatomy

### What each product does today

| Product | Row structure | Visual weight | Verdict |
|---|---|---|---|
| Flights airport | `[✈ icon]` `[City BOLD]` `[جميع المطارات]` / `[Country muted]` | 3-level hierarchy ✅ | ✅ Best |
| Visa countries | `[Flag emoji]` `[Country name]` `[(الإلكترونية) badge]` | 2-level ✅ | ✅ Good |
| Supporting services home grid | `[outline icon]` `[Label 2 lines]` | 2-level | ⚠️ Icon too small |
| Visa Req. destination cards | `[Photo]` `[Flag]` `[Name]` | Visual card | ✅ Best for browse |

### Winner → **Flights airport row** for list pickers, **Visa Req. photo card** for browse/discovery

### Normalization Rule

**Rule A — List picker rows** (inside bottom sheets):
```
[24px icon]  [Primary — 16px bold]        ← City / Country / Program name
             [Secondary — 12px muted]     ← Detail (airport type / country / institute)
             [Badge — 11px orange pill]   ← Optional: "(الإلكترونية)" "(جديد)" etc.
Touch target: min 48px height per row
```

**Rule B — Browse/discovery cards** (home screen sections):
```
[Full-bleed photo 160×100px]
[Flag emoji + Name label]              ← copy from Visa Req. cards
```

Apply Rule A to: Visa picker, Month picker, Study Abroad program picker, any future search results.
Apply Rule B to: Packages categories, Study Abroad destinations, eSIM plans.

---

## PATTERN 06 · CTA Button

### What each product does today

| Product | Label | Width | Position | State shown |
|---|---|---|---|---|
| Flights | `بحث` | 100% | Inline after form | Active only |
| Hotels | `ابحث` | 100% | Inline after form | Active only |
| Visas tab | ❌ **None** | — | — | — |
| Packages month sheet | `تأكيد` | 100% | Bottom of sheet | Active only |
| Visa Requirements | `ابدأ طلب التأشيرة` | 100% | ✅ Bottom-anchored | Active only |

### Winner → **Visa Requirements CTA** — label formula + bottom-anchored position

Label formula used: **`[فعل أمر] + [الموضوع]`** = imperative verb + object

### Normalization Rule

```
CTA anatomy:
┌────────────────────────────────────────┐
│          [فعل أمر] + [الموضوع]         │
└────────────────────────────────────────┘
Height: 52px | Width: 100% | Radius: 8px
Color: #FF6B00 | Text: white bold 16px
Position: sticky to bottom safe area on any screen with a single primary action
```

**Unified label table — apply immediately:**

| Product | Current label | ✅ Normalized label |
|---|---|---|
| Flights | `بحث` | `ابحث عن رحلات` |
| Hotels | `ابحث` | `ابحث عن فنادق` |
| Visas tab | ❌ Missing | `ابدأ طلب التأشيرة` |
| Packages | `تأكيد` (in sheet) | `اختر هذه الفترة` |
| Visa Requirements | `ابدأ طلب التأشيرة` | ✅ Keep as-is |
| Study Abroad | Unknown | `ابدأ طلب القبول` |
| Int'l License | Unknown | `استخرج رخصتي` |
| eSIM | Unknown | `احصل على الشريحة` |
| Supporting services | Unknown | `ابدأ الطلب` |

---

## PATTERN 07 · Top Tab Bar (Vertical Switcher)

### What each product does today

```
[تأشيرات 🛂] [طيران ✈️] [فنادق 🏨] [بكجات 📦] [مزيد›]
```
- Icon + label per tab ✅
- Orange underline for active ✅
- Horizontal scroll — but 5th tab clipped with no scroll signal ❌
- Tab order: Visas first (rightmost in RTL) — but Flights is likely most-used ⚠️

### Winner → Current tab bar is correct in structure — needs 2 fixes only

### Normalization Rule

1. **Reorder tabs by usage frequency** (right→left in RTL):
   `[طيران] [فنادق] [تأشيرات] [باقات] [المزيد›]`

2. **Signal scrollability** — show 4.5 tabs (half-tab visible on left edge), not 4 clipped:
   Keep all other tab styling exactly as-is.

---

## PATTERN 08 · Bottom Navigation Bar

### What each product does today

```
[المزيد …] [متطلبات التأشيرة ≡] [طلباتي 📋] [الرئيسية 🏠]
```
- Consistent icon + label ✅
- Orange active state ✅
- "متطلبات التأشيرة" label is too long for a tab (9 Arabic chars) ❌

### Winner → Current structure is correct — needs 1 label fix

### Normalization Rule

Shorten the long tab label:
```
Current:  متطلبات التأشيرة  →  Normalized: متطلبات
```
All other bottom nav items unchanged. Keep same icons, colors, sizing.

---

## PATTERN 09 · Supporting Services Grid (Home Screen)

### What was observed

The home screen's "خدمة مساندة للسفر" section shows 4 service cards:
```
[🚗 رخصة دولية - دفتر] [📄 تعبئة نماذج السفر] [🎓 قبول جامعات] [☂️ تأمين طبي]
```
- Outline icon (monochrome) + 2-line label
- Horizontal scroll row
- Same card size for all services ✅
- No background tint to differentiate service types ❌ — hard to scan

### Winner → **Current grid** is structurally correct

### Normalization Rule

Keep the grid. Only change: add a **category color dot** (1 color per service domain) to help scan:

```
Each service card:
┌──────────┐
│  [icon]  │  ← 32px, monochrome (already ✅)
│  Label   │  ← 2 lines max (already ✅)
│    ●     │  ← ADD: 6px category color dot at bottom
└──────────┘
Colors: Flights=blue | Hotels=teal | Visas=orange(existing) | Study=green | License=purple
```

This uses zero new components — just the existing card + a colored dot.

---

## PATTERN 10 · Country / Destination Selector Pattern

Two different patterns exist for the same task (selecting a destination):

| Where | Pattern | Verdict |
|---|---|---|
| Visa tab search | Bottom sheet with search + flag list ("اختر الدولة") | ✅ Good |
| Visa Requirements tab | Horizontal scrollable flag tabs at top of page | ✅ Also good — but only works for short lists |
| Packages browse | Full-screen image cards | ✅ Best for inspiration/discovery |

### Normalization Rule — use the right pattern for the right context

```
List > 8 items  →  Bottom sheet with search (copy Visa tab pattern)
List ≤ 8 items  →  Horizontal flag tabs (copy Visa Requirements pattern)  
Discovery mode  →  Photo cards grid (copy Packages pattern)
```

Apply this decision matrix to: Visa, Hotels city, Flights destination, Study Abroad country, Int'l License country.

---

## PATTERN 11 · Trust / Reassurance Messaging

### What was observed

Only **Visa Requirements** has a trust message:
> `ℹ️ جميع بياناتك محمية وآمنة — AES-256`

### Winner → **Visa Requirements** — only product that addresses user anxiety

### Normalization Rule

Add one trust line above every primary CTA on screens that collect personal data:

```
ℹ️ جميع بياناتك محمية وآمنة    ← copy exactly from Visa Requirements
```

Apply to: Visa application form, Hotel checkout, Flight checkout, Study Abroad form, Int'l License form.
**Do not add it** to: search screens (no data collected yet), browse screens.

---

## Summary: The 11 Normalized Patterns

| # | Pattern | Winner Source | Who must adopt it |
|---|---|---|---|
| 01 | Page header title | Visa Requirements + Packages | Flights, Hotels, Visas, Study, License, eSIM |
| 02 | Sheet close button `×` | *(none yet — add to all)* | All 4 bottom sheets |
| 03 | Form field row | Flights / Hotels / Visas *(already shared)* | Packages, Supporting Services |
| 04 | Search-in-sheet | Flights airport picker | Visa picker, Month picker, future pickers |
| 05A | List row anatomy | Flights airport row | Visa picker, Study Abroad, eSIM |
| 05B | Browse card | Visa Requirements photo card | Packages, Study destinations |
| 06 | CTA label formula | Visa Requirements | Flights, Hotels, Visas, Packages, Study, License, eSIM |
| 07 | Top tab order | *(reorder only)* | Top tab bar |
| 08 | Bottom nav label | *(shorten 1 label)* | متطلبات → متطلبات |
| 09 | Service grid | Current grid ✅ + color dot | Home screen services |
| 10 | Destination selector logic | Contextual (3 patterns) | All verticals with destination input |
| 11 | Trust message | Visa Requirements | Checkout screens for all verticals |

---

## Ranking: Interaction Clarity (1 = most complete, least friction)

| Rank | Product | Score /10 | Why |
|---|---|---|---|
| 🥇 1 | **Visa Requirements** | **9/10** | Contextual header, flag tabs, anchored CTA with best label, trust message, fewest steps |
| 🥈 2 | **Flights** | **8/10** | Best form design, smart من/إلى sheet, swap icon, trip type toggle, rich airport rows |
| 🥉 3 | **Hotels** | **7/10** | Clean 3-field form, fast path — only issue: CTA label + truncated field |
| 4 | **Packages** | **5/10** | Visual browse works but month picker is broken, back chevron RTL direction wrong |
| 5 | **Visas (tab)** | **4/10** | Good country list but no CTA, vast empty state after selection |
| 6 | **Study Abroad / قبول جامعات** | **3/10** | Only accessible from home grid, no dedicated screen captured — architecture problem |
| 7 | **Int'l License / eSIM / Supporting** | **2/10** | Buried 2 taps deep in home scroll, no navigation entry point from any tab |

---

## One Decision Per Pattern — Apply Now

These are copy jobs, not design work:

```
1. Header title    → copy "متطلبات التأشيرة" style to: Flights, Hotels, Visas, Study, License, eSIM
2. Sheet ×         → add × close icon top-left of ALL 4 existing bottom sheets
3. CTA labels      → update 5 button labels to "[فعل] + [موضوع]" formula
4. Trust line      → copy ℹ️ line from Visa Requirements to checkout screens
5. Airport picker  → use as template for ALL list pickers (add search + highlight to visa picker)
6. Tab order       → reorder top tabs: طيران first (rightmost RTL)
7. Tab label       → متطلبات التأشيرة → متطلبات
```

**Estimated effort: All 7 changes are text/icon/copy updates — no layout or component changes needed.**
