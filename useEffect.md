# useEffect

**O que o `useEffect` faz?** Usamos o `useEffect` quando queremos monitorar as mudanças em uma variável, executando uma função cada vez que ocorrer uma mudança. O termo Effect vem de efeito colateral, sempre que uma variável do Array de dependências mudar, esse efeito colateral será executado.

O Effect Hook (Hook de Efeito) te permite executar efeitos colaterais em componentes funcionais:

```jsx
import { useContext, useEffect } from "react";
import { CountContext } from "../../context/CountContext";

function Count() {
  const { count, setcount } = useContext(CountContext);

  useEffect(() => {
    console.log("a variável de estado count mudou, ativando o useEffect");
  }, [count]);

  return (
    <>
      <h1>contador: {count}</h1>
      <button onClick={() => setcount(count + 1)}>incrementar</button>
      <button onClick={() => setcount(count - 1)}>decrementar</button>
    </>
  );
}

export default Count;
```

Nesse exemplo, estamos monitorando as mudanças sofridas pela variável de estado count, e toda vez que essa variável sofrer uma mudança, a função de callback será chamada pelo useEffect, exibindo no terminal a mensagem:

```jsx
console.log("a variável de estado count mudou, ativando o useEffect");
```

Se não for passado nenhuma variável no Array de dependências, o useEffect irá ser executado uma única vez, assim que o componente renderizar.

```jsx
import { useContext, useEffect } from "react";
import { CountContext } from "../../context/CountContext";

function Count() {
  const { count, setcount } = useContext(CountContext);

  useEffect(() => {
    console.log("a variável de estado count mudou, ativando o useEffect");
  }, []);

  return (
    <>
      <h1>contador: {count}</h1>
      <button onClick={() => setcount(count + 1)}>incrementar</button>
      <button onClick={() => setcount(count - 1)}>decrementar</button>
    </>
  );
}

export default Count;
```
