# SendEventOnIntersection

Utilizado para enviar eventos quando o componente aparecer em tela. Funciona em componentes renderizados no servidor ou em Islands.

```tsx
import { sendEvent } from "$store/sdk/analytics.tsx";
import type { AnalyticsEvent } from "apps/commerce/types.ts";

type Props = {
  event: AnalyticsEvent;
  id: string;
  threshold?: number;
  rootMargin?: string;
};

const script = ({ event, id, rootMargin = "0px", threshold = 0.5 }: Props) => `
addEventListener("load", () => {
  const element = document.getElementById("${id}");
  if (!element) return;

  const handleIntersection = (entries, _observer) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting) {
        (${sendEvent})(${JSON.stringify(event)});
        _observer.unobserve(element);
      }
    });
  };

  const options = {
    rootMargin: "${rootMargin}",
    threshold: ${threshold},
  };

  const observer = new IntersectionObserver(handleIntersection, options);
  observer.observe(element);
});
`;

export function SendEventOnIntersection(props: Props) {
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
| id | string | Sim | ID do componente que será utilizado para testar a interseção. |
| threshold | `number` ou `number[]` | Não | Um único número ou uma matriz de números que indica em qual porcentagem da visibilidade do alvo o retorno de chamada do observador deve ser executado. |
| rootMargin | string | Não | Margem ao redor do componente.<br>Pode ter valores semelhantes à propriedade de margem CSS, por exemplo.<br>"10px 20px 30px 40px" (superior, direita, inferior, esquerda).<br>Os valores podem ser porcentagens.<br>Este conjunto de valores serve para aumentar ou diminuir cada lado da caixa delimitadora do elemento antes de calcular as interseções. |

## Exemplo

```tsx
<SendEventOnIntersection
  id={id}
  event={{
    name: "nome_do_evento",
    params: {...}, // Parâmetros do evento
  }}
  threshold={0.8}
  rootMargin="10px"
/>
```
