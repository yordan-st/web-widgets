## Why

Combobox shrinks to 1px when placed in a flex container with `align-content: center` (row). The widget becomes unusable — invisible to the user — without any CSS override from the app developer.

## What changes

`packages/pluggableWidgets/combobox-web/src/ui/Combobox.scss` — `.widget-combobox` rule (line 21).

Replace `min-width: 0` with `min-width: min-content`.

`min-width: 0` was set to allow the widget to shrink inside flex containers (standard flex override). But `min-content` is the correct floor — it lets the widget shrink to its intrinsic minimum (the smallest it can be while still showing content) rather than collapsing to 0/1px.

## Root cause

`.widget-combobox-multiselect:not(.widget-combobox-input-container-active) .widget-combobox-input` has `width: 1px` — intentional, hides the text cursor in inactive multiselect state.

`.widget-combobox` has `min-width: 0` — allows flex children to shrink below intrinsic size.

When `align-content: center` is applied to the parent container, flex does not use `flex-grow` to determine the cross-axis size; it uses the item's minimum width. With `min-width: 0`, that resolves to 1px (the input's explicit width). With `min-width: min-content`, flex can still shrink the widget but not below its content's natural minimum.

## Impact

Must not break:

- Single-select combobox layout in all container types
- Multiselect combobox layout (active and inactive states)
- Combobox inside constrained containers that intentionally restrict width
- Atlas UI demo site rendering (already unaffected per ticket)
