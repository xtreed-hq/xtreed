# Xtreed Embed Offer

Application to embed an upsell offer into any web platform.

## 📋 Table of Contents

- [Xtreed Embed Offer](#xtreed-embed-offer)
  - [📋 Table of Contents](#-table-of-contents)
  - [🚀 How to get the integration code](#-how-to-get-the-integration-code)
  - [💻 Installation](#-installation)
  - [🐛 Debug Mode](#-debug-mode)
  - [🎨 Customization](#-customization)
    - [Card Styles](#card-styles)
    - [Custom Font](#custom-font)
    - [Text Overrides](#text-overrides)
  - [📝 Parameters](#-parameters)
    - [Required](#required)
    - [Optional](#optional)
  - [💡 Examples](#-examples)
    - [Basic Example](#basic-example)
    - [Example with Customization](#example-with-customization)
    - [Example with Advanced Styles](#example-with-advanced-styles)
  - [📞 Support](#-support)

## 🚀 How to get the integration code

1. In your connected Xtreed account, go to **Products**
2. Create or select a product
3. Open **Sales strategies**
4. Create or view a strategy such as **Upsell**
5. Go to the **Integration code** field and copy the code
6. Paste the code where you want it to appear on your site

## 💻 Installation

With the code in hand, paste it where you want it to appear on your site:

```html
<div id="xtreed-root" 
     data-language="pt" 
     data-offer-id="123" 
     data-item-id="456" 
     data-environment="production">
</div>
```

## 🐛 Debug Mode

To make integration easier, we provide a debug mode that prints `console.log` for the query string, parameters passed in `xtreed-root`, and some other important data.

**To enable:**
```html
data-debug="true"
```

⚠️ **Attention:** Disable it for production!

## 🎨 Customization

### Card Styles

We use [xstyled](https://xstyled.dev) to manage the UI. We already provide some base styles, but they can be changed as needed. See the docs: [https://xstyled.dev/docs/utility-props/](https://xstyled.dev/docs/utility-props/)

**Style syntax:** Styles must be passed as JSON using the `@xstyled/styled-components` syntax with shorthand properties and values from the design token system.

**Syntax examples:**
- `padding: 24px` → `{"p": 6}`
- `margin: 16px` → `{"m": 4}`
- `background: #ffffff` → `{"bg": "white"}`
- `color: #1a202c` → `{"color": "gray.800"}`
- `font-size: 18px` → `{"fontSize": "18px"}`
- `border-radius: 8px` → `{"borderRadius": "8px"}`

All card sections are customizable (except structural ones) and can be passed as parameters in the integration code:

| Parameter | Description | Example |
|-----------|-------------|---------|
| `data-container-style` | Styles for the main container, border, background, padding, etc. | `'{"border": "2px solid gray.200", "borderRadius": "12px", "p": 6, "bg": "white"}'` |
| `data-image-wrapper-style` | Styles for the image wrapper, sizing, etc. | `'{"w": "100%", "h": "200px", "overflow": "hidden", "borderRadius": "8px"}'` |
| `data-image-style` | Styles and properties of the product image | `'{"w": "100%", "h": "100%", "objectFit": "cover"}'` |
| `data-message-error-style` | Styles for the error message | `'{"color": "red.500", "fontSize": "14px", "p": 3}'` |
| `data-message-success-style` | Styles for the success message | `'{"color": "green.500", "fontSize": "14px", "p": 3}'` |
| `data-product-meta-style` | Styles for the container where product metadata will be displayed | `'{"py": 4, "px": 6}'` |
| `data-product-name-style` | Styles for the product name text | `'{"fontSize": "20px", "fontWeight": 700, "color": "gray.800"}'` |
| `data-product-description-style` | Styles for the product description text | `'{"fontSize": "14px", "color": "gray.600", "lineHeight": 1.5}'` |
| `data-product-price-style` | Styles for the product price | `'{"fontSize": "18px", "fontWeight": 600, "color": "green.600"}'` |
| `data-product-price-without-discount-style` | Styles for the product price without discount (if any) | `'{"fontSize": "14px", "color": "gray.500", "textDecoration": "line-through"}'` |
| `data-accept-button-style` | Styles for the accept offer button | `'{"bg": "green.500", "color": "white", "px": 6, "py": 3, "borderRadius": "8px"}'` |
| `data-reject-button-style` | Styles for the reject offer button | `'{"bg": "transparent", "color": "gray.500", "border": "1px solid gray.200", "px": 6, "py": 3}'` |

### Custom Font

To add a custom font, add the following properties:

```html
data-custom-font-url="https://fonts.googleapis.com/css2?family=Bitcount+Single+Ink:wght@100..900&display=swap"
data-custom-font-name="Bitcount Single Ink"
```

- `data-custom-font-url`: Stylesheet URL for the font (e.g., Google Fonts)
- `data-custom-font-name`: Name of the custom font (e.g., "Bitcount Single Ink")

### Text Overrides

To change the button texts, add the following properties:

⚠️ **Attention:** You must provide all 3 platform languages (pt, es, en)

```html
data-accept-button-text='{"pt": "Aceitar oferta", "es": "Aceptar oferta", "en": "Accept offer"}'
data-reject-button-text='{"pt": "Recusar oferta", "es": "Rechazar oferta", "en": "Reject offer"}'
```

## 📝 Parameters

### Required

| Parameter | Description | Example |
|-----------|-------------|---------|
| `id="xtreed-root"` | **Required** - Reference where the integration is initialized (cannot be changed) | `id="xtreed-root"` |
| `data-language` | Current language from the Xtreed dashboard | `pt`, `en` or `es` |
| `data-offer-id` | ID of the offered offer (obtained in the Xtreed dashboard) | `"123"` |
| `data-item-id` | ID of the sales strategy (obtained in the Xtreed dashboard) | `"456"` |
| `data-environment` | Integration environment | `development` or `production` |

### Optional

| Parameter | Description | Default |
|-----------|-------------|---------|
| `data-debug` | Enables debug logs in the console | `false` |
| `data-custom-font-url` | URL of the custom font | - |
| `data-custom-font-name` | Name of the custom font | - |
| `data-accept-button-text` | Accept button text (JSON with languages) | - |
| `data-reject-button-text` | Reject button text (JSON with languages) | - |

## 💡 Examples

### Basic Example

```html
<div id="xtreed-root" 
     data-language="pt" 
     data-offer-id="123" 
     data-item-id="456" 
     data-environment="production">
</div>
```

### Example with Customization

```html
<div id="xtreed-root" 
     data-language="pt" 
     data-offer-id="123" 
     data-item-id="456" 
     data-environment="production"
     data-debug="true"
     data-custom-font-url="https://fonts.googleapis.com/css2?family=Inter:wght@400;600&display=swap"
     data-custom-font-name="Inter"
     data-container-style='{"border": "2px solid gray.200", "borderRadius": "12px", "p": 6, "bg": "white"}'
     data-product-name-style='{"fontSize": "24px", "fontWeight": 600, "color": "gray.800"}'
     data-accept-button-style='{"bg": "green.500", "color": "white", "px": 6, "py": 3, "borderRadius": "8px", "border": "none"}'
     data-accept-button-text='{"pt": "Aceitar oferta", "es": "Aceptar oferta", "en": "Accept offer"}'
     data-reject-button-text='{"pt": "Recusar oferta", "es": "Rechazar oferta", "en": "Reject offer"}'>
</div>
```

### Example with Advanced Styles

```html
<div id="xtreed-root" 
     data-language="pt" 
     data-offer-id="123" 
     data-item-id="456" 
     data-environment="production"
     data-container-style='{"maxWidth": "400px", "mx": "auto", "boxShadow": "0 4px 6px rgba(0, 0, 0, 0.1)"}'
     data-image-wrapper-style='{"w": "100%", "h": "200px", "overflow": "hidden", "borderRadius": "8px"}'
     data-image-style='{"w": "100%", "h": "100%", "objectFit": "cover"}'
     data-product-meta-style='{"py": 4}'
     data-product-name-style='{"fontSize": "20px", "fontWeight": 700, "mb": 2, "color": "gray.700"}'
     data-product-description-style='{"fontSize": "14px", "color": "gray.500", "lineHeight": 1.5, "mb": 4}'
     data-product-price-style='{"fontSize": "18px", "fontWeight": 600, "color": "green.600"}'
     data-accept-button-style='{"w": "100%", "bg": "linear-gradient(135deg, blue.500 0%, purple.600 100%)", "color": "white", "py": 3.5, "borderRadius": "8px", "border": "none", "fontWeight": 600, "cursor": "pointer"}'
     data-reject-button-style='{"w": "100%", "bg": "transparent", "color": "gray.500", "py": 3.5, "border": "1px solid gray.200", "borderRadius": "8px", "mt": 2, "cursor": "pointer"}'>
</div>
```

## 📞 Support

For questions or support, contact us through the Xtreed dashboard or consult the official documentation.
