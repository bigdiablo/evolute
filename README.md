# Evolute

A pure CSS/HTML component library for building clean, responsive UI interfaces. No JavaScript frameworks required.

## Components

### 1. Buttons

Use the `.btn` class combined with a variant modifier.

**Variants:**
- **`.btn-primary`** — solid primary background, white text
- **`.btn-secondary`** — light gray background, dark text
- **`.btn-accent`** — primary-light background, white text
- **`.btn-outline`** — transparent with primary border
- **`.btn-danger`** — red background, white text

**Basic usage:**

```html
<button class="btn btn-primary">Submit</button>
<button class="btn btn-secondary">Cancel</button>
<button class="btn btn-accent">Submit</button>
<button class="btn btn-outline">Download</button>
<button class="btn btn-danger">Remove</button>
```

**With icon (inline SVG):**

```html
<button class="btn btn-primary">
    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none"
         stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
        <polyline points="20 6 9 17 4 12"/>
    </svg>
    Submit
</button>
```

SVGs inside `.btn` are automatically sized to `16x16`.

**Disabled state:**

```html
<button class="btn btn-primary" disabled>Print</button>
```

Disabled buttons get `opacity: 0.5` and `cursor: not-allowed`.

**Button groups (Back/Next pattern):**

```html
<div class="button-wrapper">
    <button class="btn btn-secondary">
        <!-- left arrow SVG -->
        Back
    </button>
    <button class="btn btn-primary">
        Next
        <!-- right arrow SVG -->
    </button>
</div>
```

---

### 2. Actions (Link-style)

Standalone action links with auto-generated icons via CSS `::before` pseudo-elements.

**Available actions:**
- **`.action-view`** — eye icon, primary color
- **`.action-edit`** — pencil icon, primary color
- **`.action-delete`** — trash icon, red color
- **`.action-copy`** — copy icon, primary color

```html
<a href="#" class="action-view">View</a>
<a href="#" class="action-edit">Edit</a>
<a href="#" class="action-delete">Delete</a>
<a href="#" class="action-copy">Copy</a>
```

Icons are embedded as SVG data URIs in CSS — no extra assets needed. Wrap multiple actions in a `.links` container for horizontal layout:

```html
<div class="links">
    <a href="#" class="action-view">View</a>
    <a href="#" class="action-edit">Edit</a>
    <a href="#" class="action-delete">Delete</a>
    <a href="#" class="action-copy">Copy</a>
</div>
```

---

### 3. Badges

Inline status indicators with a colored dot (`::before` pseudo-element).

**Variants:**
- **`.badge.success`** — green (bg-success)
- **`.badge.danger`** — red (bg-error)
- **`.badge.warning`** — amber (bg-warning)
- **`.badge.info`** — blue (bg-info)
- **`.badge.neutral`** — gray (bg-light)

```html
<span class="badge success">Active</span>
<span class="badge danger">Inactive</span>
<span class="badge warning">Pending</span>
<span class="badge info">Exclusive</span>
<span class="badge neutral">Shared</span>
```

Each badge automatically renders a small colored circle before the text.

---

### 4. Card

A container with border, rounded corners, and internal padding. Use it to group form fields or content.

```html
<div class="card">
    <!-- content here -->
</div>
```

Optional title with bottom border:

```html
<div class="card">
    <div class="title">Card Title</div>
    <!-- content -->
</div>
```

**Responsive:** On screens ≤ 800px, padding and gap shrink automatically.

---

### 5. Form Fields

Wrap each input inside a `.field` container with a `.label`.

**Supported input types:** text, email, password, number, tel, date, search, url.

```html
<div class="field">
    <label class="label">Account Name</label>
    <input class="input" type="text" placeholder="Acme Leads Inc.">
</div>
```

**Select dropdown:**

```html
<div class="field">
    <label class="label">Connection Type</label>
    <select class="select">
        <option value="" disabled selected>Select a type</option>
        <option>Publisher</option>
        <option>Buyer</option>
        <option>Wholesale</option>
    </select>
</div>
```

**Textarea:**

```html
<div class="field">
    <label class="label">Notes</label>
    <textarea class="textarea" placeholder="Enter notes..."></textarea>
</div>
```

**States:**
- **Hover** — border color changes to `--color-muted`
- **Focus** — border color changes to `--color-primary`
- **Placeholder** — styled with `--color-muted`

All form controls (`.input`, `.select`, `.textarea`) share the same border, padding, and transition styles.

---

### 6. Checkbox Group

Use `.checkboxes` to create a group of checkbox options.

**Layout variants:**

#### Stacked (default)
Vertical column layout.

```html
<div class="checkboxes">
    <span class="label">Features</span>
    <label class="option"><input type="checkbox" checked> API Integration</label>
    <label class="option"><input type="checkbox"> Webhook Delivery</label>
    <label class="option"><input type="checkbox"> Data Import</label>
</div>
```

#### Inline
Horizontal row with wrapping.

```html
<div class="checkboxes inline">
    <span class="label">Channels</span>
    <label class="option"><input type="checkbox" checked> Email</label>
    <label class="option"><input type="checkbox"> SMS</label>
    <label class="option"><input type="checkbox"> Push</label>
</div>
```

#### Grid (3 columns)
CSS Grid with 3 equal columns.

```html
<div class="checkboxes grid">
    <span class="label">Permissions</span>
    <label class="option"><input type="checkbox" checked> Orders</label>
    <label class="option"><input type="checkbox"> Leads</label>
    <label class="option"><input type="checkbox"> Channels</label>
    <label class="option"><input type="checkbox"> Connections</label>
    <label class="option"><input type="checkbox"> Reports</label>
    <label class="option"><input type="checkbox" checked> Subscriptions</label>
</div>
```

#### Pills
Hidden checkbox inputs, styled as selectable pill buttons. Uses `:has(input:checked)` for the selected state.

```html
<div class="checkboxes pills">
    <span class="label">Roles</span>
    <label class="option"><input type="checkbox" checked> Publisher</label>
    <label class="option"><input type="checkbox"> Buyer</label>
    <label class="option"><input type="checkbox"> Seller</label>
</div>
```

Selected pills get `--color-primary` border and `--bg-info` background.

---

### 7. Radio Group

Identical structure to checkboxes, using `.radios` instead. Only one selection per group via the `name` attribute.

**Same layout variants:** default (stacked), `.inline`, `.grid`, `.pills`.

```html
<div class="radios">
    <span class="label">Plan</span>
    <label class="option"><input type="radio" name="plan" checked> Basic</label>
    <label class="option"><input type="radio" name="plan"> Professional</label>
    <label class="option"><input type="radio" name="plan"> Enterprise</label>
</div>
```

**Inline:**

```html
<div class="radios inline">
    <span class="label">Frequency</span>
    <label class="option"><input type="radio" name="freq" checked> Daily</label>
    <label class="option"><input type="radio" name="freq"> Weekly</label>
    <label class="option"><input type="radio" name="freq"> Monthly</label>
</div>
```

**Grid:**

```html
<div class="radios grid">
    <span class="label">Bid Type</span>
    <label class="option"><input type="radio" name="bid" checked> Fixed Price</label>
    <label class="option"><input type="radio" name="bid"> Auction</label>
    <label class="option"><input type="radio" name="bid"> Custom</label>
</div>
```

**Pills:**

```html
<div class="radios pills">
    <span class="label">Status</span>
    <label class="option"><input type="radio" name="status" checked> Active</label>
    <label class="option"><input type="radio" name="status"> Paused</label>
    <label class="option"><input type="radio" name="status"> Closed</label>
</div>
```

---

### 8. Modal

A centered dialog with `.header`, `.body`, and `.footer` sections. Can be displayed inside an `.overlay` for a backdrop effect.

**Basic structure:**

```html
<div class="overlay">
    <div class="modal">
        <div class="header">
            <span class="label">Terms & Conditions</span>
            <button class="close">
                <svg class="icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"
                     fill="none" stroke="currentColor" stroke-width="2"
                     stroke-linecap="round" stroke-linejoin="round">
                    <line x1="18" y1="6" x2="6" y2="18"/>
                    <line x1="6" y1="6" x2="18" y2="18"/>
                </svg>
            </button>
        </div>
        <div class="body">
            <h2 class="title">Terms & Conditions</h2>
            <p class="description">Your content here...</p>
        </div>
        <div class="footer">
            <button class="btn btn-secondary">
                <!-- close SVG --> Cancel
            </button>
            <button class="btn btn-primary">
                <!-- action SVG --> Confirm
            </button>
        </div>
    </div>
</div>
```

**Sections:**
- **`.header`** — top bar with uppercase `.label` and `.close` button
- **`.body`** — scrollable content area with `.title` and `.description` paragraphs
- **`.footer`** — action buttons row with `--bg-light` background

**`.close` button:** A 32x32 icon button with hover background. The SVG inside uses class `.icon` (18x18).

**Responsive (≤ 800px):** Modal stretches to 90vw, footer stacks buttons vertically.

---

### 9. Modal with Form

A modal variant containing a `.form` inside the `.body`.

```html
<div class="modal">
    <div class="header">
        <span class="label">New Connection</span>
        <button class="close"><!-- close SVG --></button>
    </div>
    <div class="body">
        <h2 class="title">Create Publisher Connection</h2>
        <div class="form">
            <div class="field">
                <label class="label">Account Name</label>
                <input class="input" type="text" placeholder="Acme Leads Inc.">
            </div>
            <div class="field">
                <label class="label">Contact Email</label>
                <input class="input" type="email" placeholder="contact@acmeleads.com">
            </div>
            <div class="field">
                <label class="label">Connection Type</label>
                <select class="select">
                    <option value="" disabled selected>Select a type</option>
                    <option>Publisher</option>
                    <option>Buyer</option>
                </select>
            </div>
            <div class="field">
                <label class="label">Notes</label>
                <textarea class="textarea" placeholder="Describe requirements..."></textarea>
            </div>
        </div>
    </div>
    <div class="footer">
        <button class="btn btn-secondary"><!-- X SVG --> Cancel</button>
        <button class="btn btn-primary"><!-- + SVG --> Create Connection</button>
    </div>
</div>
```

**Multi-column rows** inside the form:

```html
<div class="form">
    <div class="row">
        <div class="field">
            <label class="label">First Name</label>
            <input class="input" type="text">
        </div>
        <div class="field">
            <label class="label">Last Name</label>
            <input class="input" type="text">
        </div>
    </div>
</div>
```

`.row` arranges fields side by side. On mobile (≤ 800px), rows stack vertically.

---

### 10. Table

A styled data table with hover rows, inline actions, and mobile-responsive card layout.

```html
<table class="table">
    <thead>
        <tr>
            <th>Channel</th>
            <th>Publisher</th>
            <th>Lead Type</th>
            <th>Bid</th>
            <th>Status</th>
            <th>Actions</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td data-label="Channel">Auto Insurance</td>
            <td data-label="Publisher">Acme Leads Inc.</td>
            <td data-label="Lead Type"><span class="badge info">Exclusive</span></td>
            <td data-label="Bid">$12.50</td>
            <td data-label="Status"><span class="badge success">Active</span></td>
            <td data-label="Actions">
                <div class="actions">
                    <a href="#" class="action view">
                        <!-- eye SVG --> View
                    </a>
                    <a href="#" class="action edit">
                        <!-- pencil SVG --> Edit
                    </a>
                    <a href="#" class="action delete">
                        <!-- trash SVG --> Delete
                    </a>
                </div>
            </td>
        </tr>
    </tbody>
</table>
```

**Key features:**
- **`data-label` attribute** — required on every `<td>`. On mobile, `thead` is hidden and each cell displays `data-label` as the row header via `::before`.
- **`.actions`** — flex container for inline action links
- **`.action.view`**, **`.action.edit`**, **`.action.delete`** — styled action links with icons
- **Row hover** — applies `--bg-light` background

**Badges inside tables** work exactly the same as standalone badges.

---

### 11. Table with Colspan & Rowspan

Use native HTML `colspan` and `rowspan` attributes within `.table`.

```html
<table class="table">
    <thead>
        <tr>
            <th>Publisher</th>
            <th>Channel</th>
            <th>Lead Type</th>
            <th>Orders</th>
            <th>Revenue</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan="2" data-label="Publisher">Acme Leads Inc.</td>
            <td data-label="Channel">Auto Insurance</td>
            <td data-label="Lead Type"><span class="badge info">Exclusive</span></td>
            <td data-label="Orders">1,250</td>
            <td data-label="Revenue">$15,625</td>
        </tr>
        <tr>
            <td data-label="Channel">Home Insurance</td>
            <td data-label="Lead Type"><span class="badge neutral">Shared</span></td>
            <td data-label="Orders">830</td>
            <td data-label="Revenue">$7,262</td>
        </tr>
        <tr class="summary">
            <td colspan="3">Total</td>
            <td data-label="Orders">10,350</td>
            <td data-label="Revenue">$179,579</td>
        </tr>
    </tbody>
</table>
```

**Special styles:**
- **`td[rowspan]`** — gets `vertical-align: top`, `font-weight: 500`, and subtle `--bg-light` background
- **`tr.summary`** — bold text (`font-weight: 600`) with `--bg-light` background, no bottom border
- **Mobile** — `rowspan` has no effect in flex layout; `colspan` cells display full-width; `thead` is hidden

---

### 12. Overlay

A full-screen fixed backdrop for modals.

```html
<div class="overlay">
    <!-- modal or any centered content -->
</div>
```

Covers the entire viewport with `--overlay` (semi-transparent black). Centers its child content both vertically and horizontally.

---

## File Structure

```
evolute/
├── main.css        # Core component styles + dashboard/login styles
├── main.js         # Dashboard runtime (mobile menu, DOM cleanup)
├── evolute.css     # Extended/override styles for dashboard
```

- **`main.css`** — Contains all component styles (buttons, modals, tables, forms, badges, etc.) plus login page and dashboard layout styles.
- **`evolute.css`** — Additional overrides and layout helpers for the live dashboard application (grid layouts, tab colors, operator-only styles).
- **`main.js`** — Minimal vanilla JS that runs on dashboard pages only: cleans legacy DOM elements, injects a mobile hamburger menu, and toggles sidebar visibility.

---

## Responsive Behavior

All components adapt at the **800px** breakpoint:

| Component | Desktop | Mobile (≤ 800px) |
|-----------|---------|-------------------|
| **Modal** | Fixed width, centered | 90vw width, stacked footer buttons |
| **Table** | Standard table layout | Cards layout, `thead` hidden, `data-label` shown |
| **Card** | 20px padding/gap | 16px padding/gap |
| **Form rows** | Side-by-side fields | Stacked vertically |
| **Wrapper** | 40px padding, 60px gap | 24px padding, 40px gap |

---

## Tips

- All SVG icons use `stroke="currentColor"` so they inherit the parent's text color.
- Buttons inside `.btn` automatically size SVGs to 16x16.
- Use `data-label` on every `<td>` for proper mobile table rendering.
- The `.pills` variant for checkboxes/radios relies on the CSS `:has()` selector (supported in all modern browsers).
- To theme the library, override the CSS custom properties in `:root`.
