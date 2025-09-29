# Xtreed Embed Offer

Aplicação para fazer embed de uma oferta upsell em qualquer plataforma web.

## 📋 Índice

- [Xtreed Embed Offer](#xtreed-embed-offer)
  - [📋 Índice](#-índice)
  - [🚀 Como obter o código de integração](#-como-obter-o-código-de-integração)
  - [💻 Instalação](#-instalação)
  - [🐛 Modo Debug](#-modo-debug)
  - [🎨 Customização](#-customização)
    - [Estilos do Card](#estilos-do-card)
    - [Fonte Customizada](#fonte-customizada)
    - [Alteração dos Textos](#alteração-dos-textos)
  - [📝 Parâmetros](#-parâmetros)
    - [Obrigatórios](#obrigatórios)
    - [Opcionais](#opcionais)
  - [💡 Exemplos](#-exemplos)
    - [Exemplo Básico](#exemplo-básico)
    - [Exemplo com Customização](#exemplo-com-customização)
    - [Exemplo com Estilos Avançados](#exemplo-com-estilos-avançados)
  - [📞 Suporte](#-suporte)

## 🚀 Como obter o código de integração

1. Na conta conectada na Xtreed, vá até **Produtos**
2. Crie ou selecione um produto
3. Acesse **Estratégias de vendas**
4. Crie ou visualize uma estratégia como **Upsell**
5. Vá até o campo **Código para integração** e copie o código
6. Cole o código onde você deseja que ele apareça no seu site

## 💻 Instalação

Com o código em mãos, cole onde você deseja que ele apareça no seu site:

```html
<div id="xtreed-root" 
     data-language="pt" 
     data-offer-id="123" 
     data-item-id="456" 
     data-environment="production">
</div>
```

## 🐛 Modo Debug

Para facilitar a integração, temos o modo debug que printa `console.log` da queryString, parâmetros passados no `xtreed-root` e alguns outros dados importantes.

**Para ativar:**
```html
data-debug="true"
```

⚠️ **Atenção:** Desative quando for para produção!

## 🎨 Customização

### Estilos do Card

Utilizamos o [xstyled](https://xstyled.dev) para fazer todo o gerenciamento de UI. Temos já alguns estilos base mas podem ser alterados conforme necessário. Veja a documentação: [https://xstyled.dev/docs/utility-props/](https://xstyled.dev/docs/utility-props/)

**Sintaxe dos estilos:** Os estilos devem ser passados como JSON usando a sintaxe do `@xstyled/styled-components` com propriedades abreviadas e valores do sistema de design tokens.

**Exemplos de sintaxe:**
- `padding: 24px` → `{"p": 6}`
- `margin: 16px` → `{"m": 4}`
- `background: #ffffff` → `{"bg": "white"}`
- `color: #1a202c` → `{"color": "gray.800"}`
- `font-size: 18px` → `{"fontSize": "18px"}`
- `border-radius: 8px` → `{"borderRadius": "8px"}`

Todas as seções do card são customizáveis (exceto estruturais), e podem ser passadas como parâmetros no código de integração:

| Parâmetro | Descrição | Exemplo |
|-----------|-----------|---------|
| `data-container-style` | Estilos do container principal, borda, background, padding, etc. | `'{"border": "2px solid gray.200", "borderRadius": "12px", "p": 6, "bg": "white"}'` |
| `data-image-wrapper-style` | Estilos do wrapper da imagem, tamanho etc. | `'{"w": "100%", "h": "200px", "overflow": "hidden", "borderRadius": "8px"}'` |
| `data-image-style` | Estilos e propriedades da imagem do produto | `'{"w": "100%", "h": "100%", "objectFit": "cover"}'` |
| `data-message-error-style` | Estilos da mensagem de erro | `'{"color": "red.500", "fontSize": "14px", "p": 3}'` |
| `data-message-success-style` | Estilos da mensagem de sucesso | `'{"color": "green.500", "fontSize": "14px", "p": 3}'` |
| `data-product-meta-style` | Estilos do container onde os meta dados do produto serão exibidos | `'{"py": 4, "px": 6}'` |
| `data-product-name-style` | Estilos do texto do nome do produto | `'{"fontSize": "20px", "fontWeight": 700, "color": "gray.800"}'` |
| `data-product-description-style` | Estilos do texto da descrição do produto | `'{"fontSize": "14px", "color": "gray.600", "lineHeight": 1.5}'` |
| `data-product-price-style` | Estilos do preço do produto | `'{"fontSize": "18px", "fontWeight": 600, "color": "green.600"}'` |
| `data-product-price-without-discount-style` | Estilos do preço sem desconto do produto (se houver) | `'{"fontSize": "14px", "color": "gray.500", "textDecoration": "line-through"}'` |
| `data-accept-button-style` | Estilos do botão de aceite de oferta | `'{"bg": "green.500", "color": "white", "px": 6, "py": 3, "borderRadius": "8px"}'` |
| `data-reject-button-style` | Estilos do botão de rejeitar oferta | `'{"bg": "transparent", "color": "gray.500", "border": "1px solid gray.200", "px": 6, "py": 3}'` |

### Fonte Customizada

Para adicionar uma fonte customizada, adicione as seguintes propriedades:

```html
data-custom-font-url="https://fonts.googleapis.com/css2?family=Bitcount+Single+Ink:wght@100..900&display=swap"
data-custom-font-name="Bitcount Single Ink"
```

- `data-custom-font-url`: URL do stylesheet da fonte (ex: Google Fonts)
- `data-custom-font-name`: Nome da fonte customizada (ex: "Bitcount Single Ink")

### Alteração dos Textos

Para alterar os textos dos botões, adicione as seguintes propriedades:

⚠️ **Atenção:** É preciso adicionar nos 3 idiomas da plataforma (pt, es, en)

```html
data-accept-button-text='{"pt": "Aceitar oferta", "es": "Aceptar oferta", "en": "Accept offer"}'
data-reject-button-text='{"pt": "Recusar oferta", "es": "Rechazar oferta", "en": "Reject offer"}'
```

## 📝 Parâmetros

### Obrigatórios

| Parâmetro | Descrição | Exemplo |
|-----------|-----------|---------|
| `id="xtreed-root"` | **Obrigatório** - Referência onde inicializar a integração (não pode ser mudado) | `id="xtreed-root"` |
| `data-language` | Idioma atual do painel Xtreed | `pt`, `en` ou `es` |
| `data-offer-id` | ID da oferta oferecida (obtido no painel Xtreed) | `"123"` |
| `data-item-id` | ID da estratégia de vendas (obtido no painel Xtreed) | `"456"` |
| `data-environment` | Ambiente da integração | `development` ou `production` |

### Opcionais

| Parâmetro | Descrição | Padrão |
|-----------|-----------|---------|
| `data-debug` | Ativa logs de debug no console | `false` |
| `data-custom-font-url` | URL da fonte customizada | - |
| `data-custom-font-name` | Nome da fonte customizada | - |
| `data-accept-button-text` | Texto do botão de aceitar (JSON com idiomas) | - |
| `data-reject-button-text` | Texto do botão de rejeitar (JSON com idiomas) | - |

## 💡 Exemplos

### Exemplo Básico

```html
<div id="xtreed-root" 
     data-language="pt" 
     data-offer-id="123" 
     data-item-id="456" 
     data-environment="production">
</div>
```

### Exemplo com Customização

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

### Exemplo com Estilos Avançados

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

## 📞 Suporte

Para dúvidas ou suporte, entre em contato através do painel Xtreed ou consulte a documentação oficial.