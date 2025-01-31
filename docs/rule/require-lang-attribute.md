# require-lang-attribute

✅ The `extends: 'recommended'` property in a configuration file enables this rule.

A missing or invalid `lang` attribute can cause an application to fail legal conformance for digital accessibility requirements.

This rule's objective is to ensure that Ember applications achieve [WCAG Success Criterion 3.1.1: Language of Page](https://www.w3.org/WAI/WCAG21/Understanding/language-of-page.html), by declaring a valid IETF's BCP 47 language tag for the `lang` attribute. The state of the `lang` attribute has a usability impact on the experience of users that require screen-reading assistive technology. When the attribute is properly assigned:

> "Both assistive technologies and conventional user agents can render text more accurately when the language of the Web page is identified. Screen readers can load the correct pronunciation rules. Visual browsers can display characters and scripts correctly. Media players can show captions correctly. **As a result, users with disabilities will be better able to understand the content.**"
>
> **Source: [WCAG Success Criterion 3.1.1: Intent](https://www.w3.org/WAI/WCAG21/Understanding/language-of-page.html#intent)**

When the language of the page cannot be identified, the integrity of the above information cannot be guaranteed.

Consider any of the following use cases:

- the application developer is unaware that Ember now includes the lang attribute
- the application does not require internationalization
- the application's content is in a language that is not English
- an end-user with a screen reader turned on, whose operating system (OS) is set to a different language, navigates to that page with their screen reader turned on
- the screen reader would attempt to read the page in the language that is defined by the lang attribute on the page, but the supporting element information ("button", "link", etc) is read out in the language that is set by the operating system.

## Examples

This rule **forbids** the following:

```hbs
<html></html>
```

```hbs
<html lang=""></html>
```

```hbs
<html lang="abracadabra"></Html>
```

This rule **allows** the following:

```hbs
<html lang="en"></html>
```

```hbs
<html lang="en-US"></html>
```

```hbs
<html lang={{lang}}></html>
```

## Migration

Add the `lang` attribute to the `app/index.html` file in your Ember app. If you use an internationalization addon like `ember-intl`, note that this will not conflict with that addon.

## Configuration

- boolean -- if `true`, default configuration is applied

- object -- containing the following property:
  - boolean -- `validateValues` -- if `true`, the rule checks whether the value in the `lang` attribute is a known IETF's BCP 47 language tag
    (default: `true`)

## References

- [WCAG Success Criterion 3.1.1: Language of Page](https://www.w3.org/WAI/WCAG21/Understanding/language-of-page.html)
