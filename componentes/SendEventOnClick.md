# SendEventOnClick

Utilizado para enviar eventos ao clicar sobre algum componente. Funciona em componentes renderizados no servidor ou em Islands.

```tsx
import { sendEvent } from "$store/sdk/analytics.tsx";
import type { AnalyticsEvent } from "apps/commerce/types.ts";

type Props = {
  event: AnalyticsEvent;
  id: string;
};

const script = ({ event, id }: Props) => `
addEventListener("load", () => {
  const element = document.getElementById("${id}");
  if (!element) return;
  
  element.addEventListener("click", () => {
    (${sendEvent})(${JSON.stringify(event)})
  });
});
`;

export function SendEventOnClick(props: Props) {
  return (
    <script
      type="module"
      dangerouslySetInnerHTML={{ __html: script(props) }}
    />
  );
}
```

## Parâmetros adicionais

| Nome | Tipo | Obrigatório | Descrição |
| --- | --- | --- | --- |
| id | string | Sim | ID do componente que acionará o evento ao ser clicado. |

## Exemplo

```tsx
<SendEventOnClick
  id={id}
  event={{
    name: "nome_do_evento",
    params: {...}, // Parâmetros do evento
  }}
/>
```
