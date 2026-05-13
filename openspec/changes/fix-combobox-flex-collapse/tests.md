## Tests

- [ ] **Combobox root element has min-width: min-content in stylesheet**
    - **Type:** unit
    - **Given:** Combobox.scss is compiled
    - **When:** `.widget-combobox` rule is inspected
    - **Then:** `min-width` resolves to `min-content`, not `0`
    - **Status:** pending

- [ ] **Single-select combobox renders with visible width in flex container with align-content center**
    - **Type:** e2e
    - **Given:** Single-select Combobox placed inside a flex container with `align-content: center` (row)
    - **When:** Page loads with no interaction
    - **Then:** Combobox bounding rect width is greater than 10px (not collapsed)
    - **Status:** pending

- [ ] **Multiselect combobox renders with visible width in flex container with align-content center**
    - **Type:** e2e
    - **Given:** Multiselect Combobox with no selected items placed inside flex container with `align-content: center` (row)
    - **When:** Page loads with no interaction
    - **Then:** Combobox bounding rect width is greater than 10px (not collapsed)
    - **Status:** pending

- [ ] **Multiselect inactive input still collapses to 1px (intentional behavior preserved)**
    - **Type:** unit
    - **Given:** Combobox rendered in multiselect mode with no active selection
    - **When:** `.widget-combobox-input` is inspected inside `.widget-combobox-multiselect:not(.widget-combobox-input-container-active)`
    - **Then:** `.widget-combobox-input` has `width: 1px` applied (cursor-hiding behavior unchanged)
    - **Status:** pending

- [ ] **Combobox in constrained container (fixed width parent) does not overflow**
    - **Type:** e2e
    - **Given:** Combobox inside a container with explicit `width: 100px`
    - **When:** Page loads
    - **Then:** Combobox bounding rect width does not exceed 100px
    - **Status:** pending
