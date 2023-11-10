# add_to_cart

Esse evento indica que um item foi adicionado a um carrinho de compras.

## Parâmetros

| Nome | Tipo | Obrigatório | Exemplo | Descrição |
|---|---|---|---|---|
| currency | string | Sim&#42; | BRL | Moeda dos itens associados ao evento, no [formato ISO 4217](https://en.wikipedia.org/wiki/ISO_4217#Active_codes) de três letras.<br>&#42; Se você definir `value`, será necessário user o parâmetro currency para que as métricas de receita sejam calculadas corretamente. |
| value | number | Sim&#42; | 7.77 | Valor monetário do evento.<br>&#42; O parâmetro `value` costuma ser necessário para gerar relatórios importantes. Se você [marca o evento como uma conversão](https://support.google.com/analytics/answer/9267568?hl=pt-br), é recomendável definir `value`.<br>&#42; O parâmetro `currency` é obrigatório quando você define `value`. |
| items | [Array&#60;Item&#62;](#item) | Sim |  | Itens do evento. |

## Item

Definição do tipo `Item` utilizado no parâmetro `items` do evento `add_to_cart`.

| Nome | Tipo | Obrigatório | Exemplo | Descrição |
|---|---|---|---|---|
| item_id | string | Sim&#42;| 12345_67890 (skuID_productID) | ID do sku + ID do produto.<br>&#42; É preciso especificar item_id ou item_name.|
| item_name | string | Sim&#42;| Camiseta Stan and Friends | Nome do item.<br>&#42;É preciso especificar item_id ou item_name.|
| affiliation | string | Não | Store | Uma afiliação de produto para indicar uma empresa fornecedora ou loja física. <br>Observação: "affiliation" está disponível apenas no escopo do item.|
| coupon | string | Não | SUMMER_FUN | Nome/código do cupom associado ao item. Os parâmetros coupon no nível do evento e do item são independentes. |
| creative_name | string | Não | summer_banner2 | Nome do criativo promocional. Se definido, o parâmetro creative_name no nível do evento é ignorado. Se não foi definido, é usado o parâmetro creative_name no nível do evento (quando presente). |
| creative_slot | string | Não | featured_app_1 | Nome do slot do criativo promocional associado ao item. Se definido, o parâmetro creative_slot no nível do evento é ignorado. Se não foi definido, é usado o parâmetro creative_slot no nível do evento (quando presente). |
| discount | number | Não | 2,22 | Valor do desconto monetário associado ao item. |
| index | number | Não | 5 | Índice/posição do item em uma lista. |
| item_brand | string | Não | Store | Marca do item. |
| item_category | string | Não | Vestuário | Categoria do item. Quando usada como parte de uma hierarquia de categorias ou taxonomia, é a primeira categoria. |
| item_category2 | string | Não | Adulto | Hierarquia da segunda categoria ou taxonomia adicional do item. |
| item_category3 | string | Não | Camisas | Hierarquia da terceira categoria ou taxonomia adicional do item. |
| item_category4 | string | Não | Gola redonda | Hierarquia da quarta categoria ou taxonomia adicional do item. |
| item_category5 | string | Não | Manga curta | Hierarquia da quinta categoria ou taxonomia adicional do item. |
 | item_list_id | string | Não | related_products | ID da lista em que o item foi apresentado ao usuário. Se definido, o parâmetro item_list_id no nível do evento é ignorado. Se não foi definido, é usado o parâmetro item_list_id no nível do evento (quando presente). |
| item_list_name | string | Não | Produtos relacionados | Nome da lista em que o item foi apresentado ao usuário. Se definido, o parâmetro item_list_name no nível do evento é ignorado. Se não foi definido, é usado o parâmetro item_list_name no nível do evento (quando presente).|
| item_variant | string | Não | verde | Variante, código exclusivo ou descrição do item para detalhes/opções adicionais. |
| location_id | string | Não | ChIJIQBpAG2ahYAR_6128GcTUEo (o ID de lugar do Google para São Francisco) | O local físico associado ao item, como a localização da filial da loja. É recomendável usar o ID de lugar do Google que corresponde ao item associado. Também é possível usar um ID de local personalizado. Observação: "location id" está disponível apenas no escopo do item.|
| price | number | Não | 9,99 | Valor monetário do item em unidades do parâmetro de moeda especificado.|
| promotion_id | string | Não | P_12345 | ID da promoção associada ao item. Se definido, o parâmetro promotion_id no nível do evento é ignorado. Se não foi definido, é usado o parâmetro promotion_id no nível do evento (quando presente). |
| promotion_name | string | Não | Promoção de verão | Nome da promoção associada ao item. Se definido, o parâmetro promotion_name no nível do evento é ignorado. Se não foi definido, é usado o parâmetro promotion_name no nível do evento (quando presente).|
| quantity | number | Não | 1 | Quantidade do item. Se não for definido, quantity vai usar o valor "1".|

Além dos parâmetros prescritos, você pode incluir até 27 [parâmetros personalizados](https://developers.google.com/analytics/devguides/collection/ga4/item-scoped-ecommerce?hl=pt-br) na matriz items.

## Exemplo

```js
sendEvent({
  name: "add_to_cart",
  params: {
    currency: "BRL",
    value: 7.77,
    coupon: "SUMMER_FUN",
    shipping_tier: "Ground",
    items: [
      {
        item_id: "12345_67890 (skuID_productID)",
        item_name: "Stan and Friends Tee",
        affiliation: "Merchandise Store",
        coupon: "SUMMER_FUN",
        discount: 2.22,
        index: 0,
        item_brand: "Store",
        item_category: "Apparel",
        item_category2: "Adult",
        item_category3: "Shirts",
        item_category4: "Crew",
        item_category5: "Short sleeve",
        item_list_id: "related_products",
        item_list_name: "Related Products",
        item_variant: "green",
        location_id: "ChIJIQBpAG2ahYAR_6128GcTUEo",
        price: 9.99,
        quantity: 1
      }
    ]
  }
});
```
