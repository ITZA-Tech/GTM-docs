# SendEventOnLoad

Utilizado para enviar eventos ao carregar uma página. Funciona em componentes renderizados no servidor ou em Islands.

```tsx
import { sendEvent } from "$store/sdk/analytics.tsx";
import type { AnalyticsEvent } from "apps/commerce/types.ts";

export const SendEventOnLoad = <E extends AnalyticsEvent>({ event, id }: {
  event: E;
  id: string;
}) => (
  <script
    type="module"
    dangerouslySetInnerHTML={{
      __html: `addEventListener("load", () => (${sendEvent})(${
        JSON.stringify(
          event,
        )
      }))`,
    }}
  />
);
```

## Exemplo

```tsx
<SendEventOnLoad
  event={{
    name: "nome_do_evento",
    params: {...}, // Parâmetros do evento
  }}
/>
```
