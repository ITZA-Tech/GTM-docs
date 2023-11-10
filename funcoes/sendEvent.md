# sendEvent

Função padrão dentro do template do storefront, responsável por acionar os eventos dentro do nosso site.

## Exemplo

```js
import { sendEvent } from "$store/sdk/analytics.tsx";

sendEvent({
  name: "nome_do_evento",
  params: {...} // Parâmetros do evento. Veja os parâmetros aceitos para cada evento.
})
```
