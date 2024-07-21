# useCallback

Quando criamos uma função em JavaScript, essa função é alocada em um espaço na memoria. Quando estamos criando uma função dentro de um componente, toda vez que esse componente rerenderizar, a mesma função será criada em um espaço de memoria diferente, todas as funções e variáveis do componente são redeclaradas, dessa forma, o nosso componente entende que é uma função nova e rerenderiza, pois a função que você cria na primeira vez que um componente é renderizado será diferente daquela criada nas próximas renderizações. Ao colocar essa função dentro do Hook useCallback, o React saberá que é a mesma função, assim ela não será criada novamente.

## Quando usar?

Esse Hook é utilizado para melhorar o desempenho da aplicação, evitando renderizações e processamentos desnecessários. Imagine que você quer buscar dados de uma API, e essa API te retorna uma quantidade enorme de dados, não é interessante fazer essa busca toda vez que o componente renderizar.

## Como usar?

O Hook useCallback recebe como argumentos, uma função de callback e um array de dependências.

Temos aqui um componente App com um contador e um botão

```jsx
const myFn = useCallback(fn, deps)
```

```jsx
const myFn = useCallback(() => {
	// escopo da funçãoo
}, [])
```

Nesse exemplo, vamos ter como base o funcionamento do componente <Button />, onde nosso componente irá 

```jsx
const Button = function ({ children, ...props }) {
  useEffect(() => {
    console.log('BUTTON: RE-RENDER');
  });

  useEffect(() => {
    console.log('BUTTON: ONCLICK CHANGED');
  }, [props.onClick]);

  return <button {...props}>{children}</button>;
};
```

```jsx
import React, { useState, useCallback } from 'react';

function App() {
  const [counter, setCounter] = useState(0);

  const incrementCounter = (num) => {
    setCounter(counter + num);
  };

  return (
    <div className="App">
      <p>Teste</p>
      <h1>C1: {counter}</h1>
      <button onClick={incrementCounter}>Incrementar</button>
    </div>
  );
}

export default App;
```