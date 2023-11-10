# SendEventOnClick

Utilizado para enviar eventos ao clicar sobre algum componente. Funciona em componentes renderizados no servidor ou em Islands.

```tsx
import { sendEvent } from "..."; // Veja mais em "eventos/sendEvent.md"
import type { AnalyticsEvent } from "apps/commerce/types.ts";

export const SendEventOnClick = <E extends AnalyticsEvent>({ event, id }: {
  event: E;
  id: string;
}) => (
  <script
    type="module"
    dangerouslySetInnerHTML={{
      __html:
        `addEventListener("load", () => {const element = document.getElementById("${id}"); element && element.addEventListener("click", () => (${sendEvent})(${
          JSON.stringify(event)
        }));})`,
    }}
  />
);
```

## Exemplo

```tsx
<SendEventOnClick
  id={id} // ID do componente que será clicado
  event={{
    name: "nome_do_evento",
    params: {...}, // Parâmetros do evento
  }}
/>
```
