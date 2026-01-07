# T-Soft OS2 Snippets

VS Code snippets for **T-Soft OS2 theme development** using **Twig** and **JavaScript**.

> This VS Code extension is developed and maintained by  
> **T-Soft / OS2 Theme Team**  
> GitHub repository: https://github.com/gitorhub/tsoft-os2-snippet

- VS Code Marketplace: https://marketplace.visualstudio.com/items?itemName=tsoft-v5-snippet.tsoft-os2-snippet  
- Open VSX: https://open-vsx.org/extension/tsoft-v5-snippet/tsoft-os2-snippet

---

## Setup

### 1. Install Twig Language 2

Install **Twig Language 2** for better `.twig` syntax highlighting:

```text
https://marketplace.visualstudio.com/items?itemName=mblode.twig-language-2
```

### 2. Enable Emmet in Twig (Optional)

Add the following to your VS Code **settings.json**:

```jsonc
{
  "emmet.includeLanguages": {
    "twig": "html"
  }
}
```

---

## Documentation

- **Twig data-toggle**: Built-in OS2 `data-toggle` attributes and helpers  
- **Twig helper functions**: Common OS2 Twig helpers (`format`, `vat`, `url`, `snippet`, etc.)  
- **JavaScript usage**: OS2 JavaScript lifecycle and initialization  
- **JS helper functions**: Request, UI, snippet, and utility helpers  
- **JS in Twig**: Passing Twig data into JavaScript safely

---

## Requirements

- Visual Studio Code `>= 1.80.0`
- Basic knowledge of Twig and JavaScript
- T-Soft OS2 theme structure

---


### Requirements

- Visual Studio Code >= 1.80.0
- Basic knowledge of Twig and JavaScript
- T-Soft OS2 theme structure

### Twig (OS2)

- **Key prefixes**
  - `data-toggle` → Attribute completion with all OS2 toggles
- **Twig blocks & helpers**
  - `tfor`, `tif`, `tifel`, `tinclude`, `textends`, `tblock`, `tset`, `tfilter`, `tprint`, `ttrans`
- **Helper functions**
  - `tformat`, `tvat`, `tsnippet`, `tdump`, `tmenu`, `turl`, `tform`, `tformdata`, `trequestpath`, `texchange`, `tcategory`, `tbrand`, `tmodel`, `tproduct`, `tquery`, `tasset`, `ttheme`, `tthemeasset`, `tcsrftoken`, `tsnippeturi`
- **Sections**
  - `section-slider`, `section-banner`
- **Toggle examples**
  - `toggle-popup`, `toggle-product-loader`, `toggle-showcase`, `toggle-light-gallery`, `toggle-zoom`

#### Examples

```twig
<div {{- "data-toggle=\"slider\"" -}}>

{{ format(P.PRICE) }}
{{ vat(P.PRICE_SELL, P.VAT) }}
{{ url(77, 'page') }}
{{ snippet('share', { IMAGE_URL: BLOG.IMG2.PATH, TITLE: BLOG.TITLE }) }}

{% include "snippet/path" %}
{% for ITEM in ITEMS %}{% endfor %}

{% set data = form('form_1', true) %}

<div data-toggle="showcase"></div>
```

### JavaScript (OS2)

- **Bootstrap & lifecycle**
  - `domready`, `ON_PAGE_READY`, `themejs`
- **Twig → JS**
  - `twig-json`
- **Requests & storage**
  - `request`, `LocalApi.get`, `LocalApi.set`, `LocalApi.remove`
- **URL, cookie & utils**
  - `getUrlParam`, `setUrlParam`, `deleteUrlParam`, `setCookie`, `getCookie`, `browser`, `isMobile`, `getLink`
- **Script helpers**
  - `evalScripts`, `evalScriptsAdd`, `scriptAdd`
- **Language & currency**
  - `setLanguage`, `setCurrency`
- **UI helpers**
  - `modal`, `modalClose`, `notify`, `drawerClose`, `mask`, `popoverAlert`, `popoverAlertHide`, `passwordToggle`, `captchaToggle`
- **Data helpers**
  - `format`, `vat`, `priceToFloat`, `timeConverter`, `stringToObject`, `taxLoader`
- **Snippet utilities**
  - `snippetUri`, `loadSnippet`
- **Forms & region**
  - `checkValidity`, `formLoader`, `tsRegion`
- **Components**
  - `components.init`, `component.init`, `component.call`

#### Examples

```javascript
document.addEventListener('DOMContentLoaded', async () => {
  await components.init();
});

ON_PAGE_READY.push(function () {});

const setting = {{ SETTING|json_encode|raw }};

const res = await request('GET', '/api/endpoint');
const data = await res.json();

notify({ text: 'Saved', className: 'success', duration: 3200 });
modal({ id: 'm1', title: 'Title', html: '...' });

const url = snippetUri('product-comment-form', {
  include: 'product-detail',
  product_id: 1
});

loadSnippet({
  url,
  target: '#target',
  callback: (html) => {}
});
```

### What it looks like

### Disclaimer

This extension provides editor snippets only.  
It does not modify runtime behavior or include production code.

## License

MIT
