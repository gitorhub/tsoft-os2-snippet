# T-Soft OS2 Snippets

VSCode snippets for T-Soft OS2 theme development (Twig + JavaScript).

Documentation:
- Twig data-toggle: `https://os2-doc.tsoftthemes.com/docs/theme-development/tr/twig-usage/data-toggle/`
- Twig helper functions: `https://os2-doc.tsoftthemes.com/docs/theme-development/tr/twig-usage/function/`
- JavaScript usage: `https://os2-doc.tsoftthemes.com/docs/theme-development/tr/js-usage/`
- JS helper functions: `https://os2-doc.tsoftthemes.com/docs/theme-development/tr/js-usage/function/`
- JS in Twig, callbacks, theme.js:
  - `https://os2-doc.tsoftthemes.com/docs/theme-development/tr/js-usage/#twig-i%CC%87%C3%A7erisinde-javascript-i%CC%87%C5%9Flemleri`
  - `https://os2-doc.tsoftthemes.com/docs/theme-development/tr/js-usage/callback/`
  - `https://os2-doc.tsoftthemes.com/docs/theme-development/tr/js-usage/themejs/`

## Setup

1) Install Twig Language 2 for better `.twig` highlighting:
   `https://marketplace.visualstudio.com/items?itemName=mblode.twig-language-2`

2) Optional: Enable Emmet in Twig files. In VSCode settings (JSON):

```jsonc
"emmet.includeLanguages": {
  "twig": "html"
}
```

## Snippets Overview

- `snippets/twig.json` → OS2 Twig snippets
- `snippets/javascript.json` → OS2 JavaScript snippets
- `snippets/smarty-v5.json` and `snippets/javascript-v5.json` → Legacy (v5) examples

---

## Twig (OS2)

Key prefixes:
- `data-toggle` → attribute completion with all OS2 toggles
- `tfor`, `tif`, `tifel`, `tinclude`, `textends`, `tblock`, `tset`, `tfilter`, `tprint`, `ttrans`
- Helper functions: `tformat`, `tvat`, `tsnippet`, `tdump`, `tmenu`, `turl`, `tform`, `tformdata`, `trequestpath`, `texchange`, `tcategory`, `tbrand`, `tmodel`, `tproduct`, `tquery`, `tasset`, `ttheme`, `tthemeasset`, `tcsrftoken`, `tsnippeturi`
- Sections: `section-slider`, `section-banner`
- Toggle examples: `toggle-popup`, `toggle-product-loader`, `toggle-showcase`, `toggle-light-gallery`, `toggle-zoom`

Examples:

```twig
<div {{- "data-toggle=\"slider\"" -}}>
```

```twig
{{ format(P.PRICE) }}
{{ vat(P.PRICE_SELL, P.VAT) }}
{{ url(77, 'page') }}
{{ snippet('share', { IMAGE_URL: BLOG.IMG2.PATH, TITLE: BLOG.TITLE }) }}
```

```twig
{% include "snippet/path" %}
{% for ITEM in ITEMS %}{% endfor %}
```

```twig
{% set data = form('form_1', true) %}
```

```twig
<div data-toggle="showcase"></div>
```

References:
- Data toggle: `https://os2-doc.tsoftthemes.com/docs/theme-development/tr/twig-usage/data-toggle/`
- Helpers: `https://os2-doc.tsoftthemes.com/docs/theme-development/tr/twig-usage/function/`

---

## JavaScript (OS2)

Key prefixes:
- Bootstrap and lifecycle: `domready`, `ON_PAGE_READY`, `themejs`
- Twig → JS: `twig-json`
- Requests and storage: `request`, `LocalApi.get`, `LocalApi.set`, `LocalApi.remove`
- URL/cookie/utils: `getUrlParam`, `setUrlParam`, `deleteUrlParam`, `setCookie`, `getCookie`, `browser`, `isMobile`, `getLink`
- Script helpers: `evalScripts`, `evalScriptsAdd`, `scriptAdd`
- Language/Currency: `setLanguage`, `setCurrency`
- UI helpers: `modal`, `modalClose`, `notify`, `drawerClose`, `mask`, `popoverAlert`, `popoverAlertHide`, `passwordToggle`, `captchaToggle`
- Data helpers: `format`, `vat`, `priceToFloat`, `timeConverter`, `stringToObject`, `taxLoader`
- Snippet utilities: `snippetUri`, `loadSnippet`
- Form/validation/region: `checkValidity`, `formLoader`, `tsRegion`
- Components: `components.init`, `component.init`, `component.call`

Examples:

```js
document.addEventListener('DOMContentLoaded', async () => {
  await components.init();
});
```

```js
ON_PAGE_READY.push(function () {});
```

```js
const setting = {{ SETTING|json_encode|raw }};
```

```js
const res = await request('GET', '/api/endpoint');
const data = await res.json();
```

```js
notify({ text: 'Saved', className: 'success', duration: 3200 });
modal({ id: 'm1', title: 'Title', html: '...' });
```

```js
const url = snippetUri('product-comment-form', { include: 'product-detail', product_id: 1 });
loadSnippet({ url, target: '#target', callback: (html) => {} });
```

References:
- JS helpers: `https://os2-doc.tsoftthemes.com/docs/theme-development/tr/js-usage/function/`
- JS in Twig: `https://os2-doc.tsoftthemes.com/docs/theme-development/tr/js-usage/#twig-i%CC%87%C3%A7erisinde-javascript-i%CC%87%C5%9Flemleri`
- Callbacks: `https://os2-doc.tsoftthemes.com/docs/theme-development/tr/js-usage/callback/`
- Theme.js: `https://os2-doc.tsoftthemes.com/docs/theme-development/tr/js-usage/themejs/`

---

## Legacy (v5)

Legacy snippet sets are preserved:
- `snippets/smarty-v5.json`
- `snippets/javascript-v5.json`

---

## What it looks like

![JS Snippets](images/js.gif)

---

## License

MIT

