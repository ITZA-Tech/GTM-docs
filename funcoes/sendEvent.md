# sendEvent

Função padrão dentro do template do [storefront](https://github.com/deco-sites/storefront/blob/main/sdk/analytics.tsx), responsável por acionar os eventos dentro do nosso site.

## Exemplo

```ts
import type { AnalyticsEvent } from "apps/commerce/types.ts";

export const sendEvent = <E extends AnalyticsEvent>(event: E) => {
  window.DECO.events.dispatch(event);
};

sendEvent({
  name: "nome_do_evento",
  params: {...} // Parâmetros do evento. Veja os parâmetros aceitos para cada evento.
})
```
