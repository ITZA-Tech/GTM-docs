# search

Registre este evento para indicar quando o usuário realizou a pesquisa. Você pode usar esse evento para identificar o conteúdo que os usuários estão pesquisando no seu site ou app. Por exemplo, você pode enviar esse evento quando um usuário acessar uma página de resultados de pesquisa depois de realizar uma pesquisa.

## Parâmetros

| Nome | Tipo | Obrigatórios | Exemplo | Descrição |
| --- | --- | --- | --- | --- |
| search_term | string | Sim | camisetas | Termo que foi pesquisado |

## Exemplo

```js
sendEvent({
  name: "search",
  params: {
    search_term: "camisetas"
  }
})
```
