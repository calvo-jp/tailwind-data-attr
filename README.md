# tailwind-data-attr

A [TailwindCSS](https://tailwindcss.com/) plugin to style your components using their [data attributes](https://developer.mozilla.org/en-US/docs/Learn_web_development/Howto/Solve_HTML_problems/Use_data_attributes).

## Installation

```bash
npm install -D tailwind-data-attr
```

## Usage

Add the plugin to your tailwind config

```ts
// tailwind.config.ts
import type {Config} from 'tailwindcss';
import dataAttr from 'tailwind-data-attr';

export default {
  content: ['./src/**/*.{js,ts,jsx,tsx}'],
  plugins: [
    // using the default prefix: "ui"
    dataAttr,

    // or using a custom prefix
    dataAttr({
      prefix: 'custom-prefix',
    }),
  ],
} satisfies Config
```

Style your components

```tsx
import {Button} from '$lib/components/Button';

export function Component() {
  return (
    <Button className="ui-loading:opacity-50">
      Save
    </Button>
  );
}
```

### Using inverse variants

To apply the style to the component only when the data attribute is not present, you can add the `-not` prefix before the variant.

```tsx
<Component className="ui-not-hover:bg-gray-50" />
```

### Using group variants

You can add `-group` before the variant to apply the style to the component if its parent has the specific data attribute present.

```tsx
<ParentComponent className="group">
  <ChildComponent className="ui-group-hover:bg-gray-50" />
</ParentComponent>
```

### Using peer variants

You can add `-peer` before the variant to apply the style to the component if its sibling has the specific data attribute present.

```tsx
<ParentComponent>
  <ChildComponent className="ui-peer-hover:bg-gray-50" />
  <ChildComponent className="peer ui-hover:bg-gray-50" />
</ParentComponent>
```

## Variants and their equivalent data attributes

|  Variant                  | Data attributes                            |
|---------------------------|--------------------------------------------|
| `hover`                   | `data-hover`                               |
| `focus`                   | `data-focus`                               |
| `focus-visible`           | `data-focus-visible`                       |
| `focusable`               | `data-focusable`                           |
| `active`                  | `data-active`                              |
| `invalid`                 | `data-invalid`                             |
| `disabled`                | `data-disabled`                            |
| `readonly`                | `data-readonly`                            |
| `current`                 | `data-current`                             |
| `inview`                  | `data-inview`                              |
| `copied`                  | `data-copied`                              |
| `collapsible`             | `data-collapsible`                         |
| `highlighted`             | `data-highlighted`                         |
| `selected`                | `data-selected`                            |
| `placeholder-shown`       | `data-placeholder-shown`                   |
| `autoresize`              | `data-autoresize`                          |
| `required`                | `data-required`                            |
| `dragging`                | `data-dragging`                            |
| `complete`                | `data-complete`                            |
| `incomplete`              | `data-incomplete`                          |
| `expanded`                | `data-expanded`                            |
| `half`                    | `data-half`                                |
| `first`                   | `data-first`                               |
| `mounted`                 | `data-mounted`                             |
| `overlap`                 | `data-overlap`                             |
| `sibling`                 | `data-sibling`                             |
| `paused`                  | `data-paused`                              |
| `pressed`                 | `data-pressed`                             |
| `loading`                 | `data-loading`                             |
| `on`                      | `data-state="on"`                          |
| `off`                     | `data-state="off"`                         |
| `open`                    | `data-state="open"`                        |
| `closed`                  | `data-state="closed"`                      |
| `hidden`                  | `data-state="hidden"`                      |
| `visible`                 | `data-state="visible"`                     |
| `checked`                 | `data-checked`, `data-state="checked"`     |
| `unchecked`               | `data-unchecked`, `data-state="unchecked"` |
| `indeterminate`           | `data-state="indeterminate"`               |
| `vertical`                | `data-orientation="vertical"`              |
| `horizontal`              | `data-orientation="horizontal"`            |
| `placement-top`           | `data-placement="top"`                     |
| `placement-top-end`       | `data-placement="top-end"`                 |
| `placement-top-start`     | `data-placement="top-start"`               |
| `placement-left`          | `data-placement="left"`                    |
| `placement-left-end`      | `data-placement="left-end"`                |
| `placement-left-start`    | `data-placement="left-start"`              |
| `placement-right`         | `data-placement="right"`                   |
| `placement-right-end`     | `data-placement="right-end"`               |
| `placement-right-start`   | `data-placement="right-start"`             |
| `placement-bottom`        | `data-placement="bottom"`                  |
| `placement-bottom-end`    | `data-placement="bottom-end"`              |
| `placement-bottom-start`  | `data-placement="bottom-start"`            |
| `side-top`                | `data-side="top"`                          |
| `side-left`               | `data-side="left"`                         |
| `side-right`              | `data-side="right"`                        |
| `side-bottom`             | `data-side="bottom"`                       |
| `align-center`            | `data-align="center"`                      |
| `align-start`             | `data-align="start"`                       |
| `align-end`               | `data-align="end"`                         |
| `today`                   | `data-today`                               |
| `weekend`                 | `data-weekend`                             |
| `in-range`                | `data-in-range`                            |
| `range-start`             | `data-range-start`                         |
| `range-end`               | `data-range-end`                           |
| `view-day`                | `data-view="day"`                          |
| `view-month`              | `data-view="month"`                        |
| `view-year`               | `data-view="year"`                         |
| `under-value`             | `data-state="under-value"`                 |
| `over-value`              | `data-state="over-value"`                  |
| `delete-intent`           | `data-delete-intent`                       |
| `unit-hour`               | `data-unit="hour"`                         |
| `unit-minute`             | `data-unit="minute"`                       |
| `unit-second`             | `data-unit="second"`                       |
| `unit-period`             | `data-unit="period"`                       |
| `channel-hue`             | `data-channel="hue"`                       |
| `channel-saturation`      | `data-channel="saturation"`                |
| `channel-brightness`      | `data-channel="brightness"`                |
| `channel-lightness`       | `data-channel="lightness"`                 |
| `channel-red`             | `data-channel="red"`                       |
| `channel-green`           | `data-channel="green"`                     |
| `channel-blue`            | `data-channel="blue"`                      |
| `channel-alpha`           | `data-channel="alpha"`                     |
| `channel-hex`             | `data-channel="hex"`                       |
| `channel-css`             | `data-channel="css"`                       |
| `tour-highlighted`        | `data-tour-highlighted`                    |
| `scroll-lock`             | `data-scroll-lock`                         |
| `inert`                   | `data-inert`                               |
| `scope-<value>`           | `data-scope="<value>"`                     |
| `part-<value>`            | `data-part="<value>"`                      |
| `value-<value>`           | `data-value="<value>"`                     |
| `valuetext-<value>`       | `data-valuetext="<value>"`                 |
| `index-<value>`           | `data-index="<value>"`                     |
| `columns-<value>`         | `data-columns="<value>"`                   |
| `branch-<value>`          | `data-branch="<value>"`                    |
| `depth-<value>`           | `data-depth="<value>"`                     |
| `path-<value>`            | `data-path="<value>"`                      |
| `type-<value>`            | `data-type="<value>"`                      |

