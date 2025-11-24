### List of Issues
- **Form fields lack labels:** All inputs and textarea require associated `<label>` tags or `aria-label` attributes.
- **Image missing alt attribute:** Robot image needs `alt=""` (if decorative) or a descriptive `alt`.
- **No ARIA landmarks or semantic headings:** Main content area and form should use appropriate roles, and headings must follow semantic structure.
- **HTML lang missing:** Add `<html lang="en">`.
- **Image not fully displayed at 100% zoom; no scrollbar:** Image must reflow or be scrollable.
- **'Done' button alignment:** Button is not visually aligned with form fields.
- **Focus styles inconsistent across devices:** Inputs only show focus on mobile, not desktop.

### Detailed Bug Report

**Title:** Form fields missing accessible labels
**Steps to Reproduce:**
1. Open the page.
2. Use a screen reader or inspect each input/textarea.
3. Note there’s no label associated with any field.

**Expected Result:**  
Screen reader announces each field’s label.

**Actual Result:**  
Only placeholder text is announced; purpose unclear.

**Severity:**  
High

**Suggested Fix:**  
Add `<label>` tags or `aria-label` attributes for all form fields.

**1. Image Not Fully Displayed and No Scroll Bar**

**Title:** Robot image not fully displayed at 100% zoom; no scroll bar available
WCAG Criteria Violated: 1.4.10 Reflow, 1.4.4 Resize Text

**Severity:**
Medium

**Steps to Reproduce:**

1. Load the contact page in a standard desktop browser at 100% zoom.

2. Observe the robot image on the right side of the form.

3. The image is partially hidden and cannot be viewed fully unless zoomed out to 50%.

4. Try to scroll horizontally or vertically; no scroll bar appears to access the rest of the image.

**Expected Result:**
Robot image should be fully visible at 100% zoom, or scroll bars should appear to enable complete viewing.

**Actual Result:**
Part of the robot image is hidden off-screen, and users cannot scroll to view the full image.

**Suggested Fix:**  
Use responsive CSS:

Set max-width: 100% and height: auto on the image.

Contains image within a scrollable container, or ensure layout adapts at different zoom levels.

**2. Focus Styles Inconsistent Across Devices**

**Title:**Focus indicator for input fields only appears on mobile, not desktop
WCAG Criteria Violated: 2.4.7 Focus Visible

**Severity:** Medium

**Steps to Reproduce:**

1. Open the page in a desktop browser.

2. Tab into or click each input field and textarea.

3. Note that on desktop, no visible border or color change occurs during focus.

4. Repeat the test on a mobile device; the border turns light orange.

**Expected Result:**
All interactive form controls should show a clearly visible and consistent focus indicator across desktop and mobile.

**Actual Result:**
Focus indicator appears only on mobile view.

**Suggested Fix:**  
Add a CSS rule for desktop:

css
input:focus, textarea:focus {
  border: 2px solid #FFA500;
  outline: none;
}

**3. ‘Done’ Button Misalignment with Form Controls**

**Title:**‘Done’ button is not visually aligned with input fields
WCAG Criteria Violated: 1.3.2 Meaningful Sequence
Severity: Low to Medium

**Steps to Reproduce:**

1. Open the contact page.

2. Observe the position of the 'Done' button relative to the form fields.

3. Notice the button is not directly grouped or aligned with Full name, Email, and Message boxes.

**Expected Result:**
‘Done’ button should be properly aligned and visually grouped with corresponding input fields.

**Actual Result:**
Button appears offset or misaligned, creating a confusing layout.

**Suggested Fix:**
Use CSS flexbox or grid for layout:

css
form {
  display: flex;
  flex-direction: column;
  align-items: stretch; /* Or align-items: center; as appropriate */
}
Test alignment on all devices and browser widths.

