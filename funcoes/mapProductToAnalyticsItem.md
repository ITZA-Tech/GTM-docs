# mapProductToAnalyticsItem

Função utilizada para transformar o objeto do produto em Item compatível com os parâmetros dos eventos.

## Parâmetros

| Nome | Tipo | Obrigatório | Exemplo | Descrição |
|---|---|---|---|---|
| product | [Product](https://github.com/deco-cx/apps/blob/main/commerce/types.ts#L360) | Sim | | |
| breadcrumbList | [BreadcrumbList](https://github.com/deco-cx/apps/blob/main/commerce/types.ts#L425) | Não | | |
| price | number | Não | 7.77 | O preço de oferta de um produto ou de um componente de preço quando anexado a PriceSpecification e seus subtipos. |
| listPrice | number | Não | 9.99 | Representa o preço de tabela (o preço pelo qual um produto é realmente anunciado) de um produto oferecido. |
| index | number | Não | 0 | Índice/posição do item em uma lista. |
| quantity | number | Não | 1 | Quantidade do item.<br>Se não for definido, quantity vai usar o valor "1". |
| coupon | string | Não | SUMMER_FUN | Nome/código do cupom associado ao evento.<br>Os parâmetros `coupon` no nível do evento e do item são independentes. |

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
