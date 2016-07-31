# `hot-deep-target-behavior`

Polymer behaviors that will give your elements the ability to have a selector in their attribute. The selector will do a _deep_ search into _all_ effective/distributed children. This means that you can write an element like this:

```
<your-element target-id="#input-field">
  <p>This is the light DOM for this element</p>
  <paper-input id="input-field"></paper-input>
</your_element>
```

The `_target`property of `your-element` will be the `paper-input` element.

Three behaviors are defined:

## `Hotplate.DeepTargetBehavior`

Using this behavior, your element will have the property `target-id`, which will accept a selector. When your element is `ready()`ed, it will do a _deep_ search into its effective/distributed children, and will make sure that `_target` will point to the first matching element.

## `Hotplate.DeepSelectorsBehavior`

(cover `excludeSelector`)

## `Hotplate.DeepAllSelectorsBehavior`

(cover `excludeSelector`)

## Low level functions available when including this file

By including `hot-deep-target-behavior.html`, your element will have access to:

- `queryEffectiveChildrenDeep( slctr, excludeSlctr )`
- `queryAllEffectiveChildrenDeep( slctr, excludeSlctr )`
- `Polymer( node ).queryDistributedElementsDeep(selectors, firstOnly, excludeSelector)` (used by the two previous calls)

They mirror the calls available in Polymer. Apart from the `Deep` postfix, they are compatible. The optional `firstOnly` parameter allows to have more optimised code, since the search will stop after the first occurrence is found. The optional parameter `excludeSelector` is there to allow widgets to set sections of the searching tree as impenetrable.
