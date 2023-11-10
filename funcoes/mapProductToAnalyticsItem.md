# mapProductToAnalyticsItem

Função utilizada para transformar o objeto do produto em Item compatível com os parâmetros dos eventos.

## Parâmetros

| Nome | Tipo | Obrigatório | Exemplo |
|---|---|---|---|
| product | [Product](https://github.com/deco-cx/apps/blob/main/commerce/types.ts#L360) | Sim ||
| breadcrumbList | [BreadcrumbList](https://github.com/deco-cx/apps/blob/main/commerce/types.ts#L425) | Não ||
| price | number | Não | 7.77 |
| listPrice | number | Não | 9.99 |
| index | number | Não | 0 |
| quantity | number | Não | 1 |
| coupon | string | Não | SUMMER_FUN |

## Exemplo

```js
// ProductShelf.tsx
import { mapProductToAnalyticsItem } from "apps/commerce/utils/productToAnalyticsItem.ts";

<SendEventOnLoad
  event={{
    name: "view_item_list",
    params: {
      item_list_id: "related_products",
      item_list_name: "Produtos relacionados",
      items: products.map((product) =>
        mapProductToAnalyticsItem({
          product,
          ...(useOffer(product.offers)),
        })
      ),
    },
  }}
/>
```
