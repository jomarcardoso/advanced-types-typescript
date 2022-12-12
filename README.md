# Tipos avançados em TypeScript

## Função em que um tipo é baseado em outro

Os tipos genéricos podem ser omitidos se usar valor padrão ou `extends`. Nessse caso como queremos um tipo dinâmico baseado em outro valor, vamos usar o `extends` para servir um "guia" e dizer sem especificar o tipo que se espera.

```ts
type FunctionBase = (...any: Any[]) => any;

const conditional = <T extends FunctionBase>(
  condition: boolean,
  function: T,
  ...args: Parameters<T>
): ReturnType<T> | void => {
  if (condition) {
    return function(...args);
  }
}
```
