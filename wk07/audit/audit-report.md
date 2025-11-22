# axe DevTools Audit Report — Week 7

**Date**: [2025-11-22]
**Page scanned**: http://localhost:8080/tasks
**axe version**: [4.8.2]

---

## Summary

- **Auto**: [3]
- **Manual**: [4]

---

## Violations Found

### 1. Color Contrast (Serious)
**WCAG**: 1.4.3 Contrast (Minimum) - Level AA
**Issue**: Button text (#6c757d) on white background = 4.2:1 (needs 4.5:1)
**Element**: `<button>Delete</button>` in task list
**Impact**: Low vision, colour-blind people struggle to read
**Fix**: Change button colour to #5a6268 (meets 4.53:1)

---

### 2. Missing Form Labels (Critical)
**WCAG**: 3.3.2 Labels or Instructions - Level A
**Issue**: Input field has no associated `<label>`
**Element**: `<input id="title" name="title">`
**Impact**: People using screen readers don't know what the field is for
**Fix**: Add `<label for="title">Task title</label>`

---

### 3. Keyboard (Critical)
**WCAG**: 2.1.1 Keyboard - Level A
**Issue**: Keyboard does not always function as planned (does not always appear)
**Element**: 'edit task'
**Impact**: User can not always use site as intended
**Fix**: Add keyboard element for all sections

---

## Needs Review (Manual Check Required)

### 1. Link Purpose (Best Practice)
**WCAG**: 2.4.4 Link Purpose (In Context) - Level A
**Issue**: Link text is "here" (not descriptive)
**Element**: `<a href="/docs">Click here</a>`
**Manual check**: Review if context makes purpose clear

---

## Passed Checks (Sample)

- ✅ HTML lang attribute
- ✅ Unique IDs
- ✅ Valid ARIA attributes
- ✅ Landmark roles
- ✅ Skip link present

---

## Priority Fixes (Week 7)

Based on severity + inclusion risk:
1. **Missing form labels** (Critical, WCAG A) - FIX NOW
2. **Color contrast** (Serious, WCAG AA) - FIX NOW
3. **Link purpose** (Best practice) - Defer to Week 10

---

## Principle 1: Perceivable

### 1.4.3 Contrast (Minimum) - Level AA
- [ ] **Text**: All text 4.5:1 contrast minimum
- [ ] **Large text**: 18pt+ or 14pt bold - 3:1 minimum
- [ ] **UI components**: Buttons, inputs, borders - 3:1 minimum

**Test method**: Use Chrome DevTools Color Picker or [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/)

**Findings**: Title of Tasks, Colouring of Button Text

---

### 1.4.10 Reflow - Level AA
- [ ] **Zoom to 400%**: Content reflows without horizontal scroll
- [ ] **Viewport 320px wide**: No loss of content or functionality

**Test method**: Chrome DevTools → Responsive mode → 320×568 → Zoom to 400%

**Findings**: Overflow of boxes

---

## Principle 2: Operable

### 2.1.1 Keyboard - Level A
- [ ] **All interactive elements** reachable via Tab
- [ ] **Focus order** matches visual order
- [ ] **No keyboard traps** (can Tab out of all elements)

**Test method**: Unplug mouse, use Tab/Shift+Tab/Enter/Space only

**Findings**: Top right-hand corner buttons can not be accessed

---

### 2.4.1 Bypass Blocks - Level A
- [ ] **Skip link** present and functional
- [ ] **Landmarks** (nav, main, aside) for screen reader navigation

**Test method**: Press Tab once → "Skip to main content" appears → Enter → focus jumps

**Findings**: Links not loading pages

---

### 2.4.3 Focus Order - Level A
- [ ] **Logical sequence**: Tab follows reading order
- [ ] **No unexpected jumps**: Focus doesn't skip sections

**Test method**: Tab through entire page, note order

**Findings**: No illogical jumps (?)

---

### 2.4.7 Focus Visible - Level AA
- [ ] **All focusable elements** show clear visual indicator
- [ ] **Indicator visible** against all backgrounds

**Test method**: Tab through page, confirm blue outline visible

**Findings**: /

---

## Principle 3: Understandable

### 3.3.1 Error Identification - Level A
- [ ] **Error messages** identify what's wrong in text
- [ ] **Errors associated** with fields (`aria-describedby`, `aria-invalid`)

**Test method**: Submit empty form, check error display

**Findings**: /

---

### 3.3.2 Labels or Instructions - Level A
- [ ] **All inputs** have `<label>` or `aria-label`
- [ ] **Labels descriptive** ("Task title" not "Title")

**Test method**: Check all `<input>`, `<select>`, `<textarea>` have labels

**Findings**: /

---

## Principle 4: Robust

### 4.1.3 Status Messages - Level AA
- [ ] **ARIA live regions** for dynamic updates
- [ ] **Success/error messages** announced by screen reader

**Test method**: NVDA on → add task → confirm "Task added" announced

**Findings**: No status message announced

---