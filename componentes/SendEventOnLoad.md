# SendEventOnLoad

Utilizado para enviar eventos ao carregar uma página. Funciona em componentes renderizados no servidor ou em Islands.

```tsx
import { sendEvent } from "$store/sdk/analytics.tsx";
import type { AnalyticsEvent } from "apps/commerce/types.ts";

type Props = {
  event: AnalyticsEvent;
}

const script = ({ event }: Props) => `
addEventListener("load", () => (${sendEvent})(${JSON.stringify(event)}));
`;

export function SendEventOnLoad(props: Props) {
  return (
    <script
      type="module"
      dangerouslySetInnerHTML={{ __html: script(props) }}
    />
  );
}
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
