# React.memo

# `React.memo`

```jsx
const MyComponent = React.memo(function MyComponent(props) {
  /* renderize usando props */
});
```

`O React.memo` é um [*higher order component*](https://pt-br.reactjs.org/docs/higher-order-components.html).

Se seu componente renderiza o mesmo resultado dados os mesmos props, você pode envolver nele uma chamada para `React.memo` para um aumento no desempenho em alguns casos, através da memoização do resultado. Isto significa que o React vai pular a renderização do componente e reutilizar o último resultado renderizado.

`React.memo` verifica apenas as alterações de prop. Se o seu componente funcional envolvido em `React.memo` tiver um [`useState`](https://pt-br.reactjs.org/docs/hooks-state.html), [`useReducer`](https://pt-br.reactjs.org/docs/hooks-reference.html#usereducer) ou [`useContext`](https://pt-br.reactjs.org/docs/hooks-reference.html#usecontext) Hook em sua implementação, ele ainda será renderizado quando o estado ou o contexto mudar.

Por padrão, ele irá comparar apenas superficialmente os objetos nos props. Se você quiser controle sob a comparação, você também pode prover uma função customizada de comparação como segundo argumento.

```jsx
function MyComponent(props) {
  /* renderize usando props */
}
function areEqual(prevProps, nextProps) {
  /*
  se prevProps e nextProps renderizam o mesmo resultado,
  retorne true.
  caso contrário, retorne false.
  */
}
export default React.memo(MyComponent, areEqual);
```

Este método existe somente como uma [**otimização de performance](https://pt-br.reactjs.org/docs/optimizing-performance.html).** Não conte com ele para “prevenir” uma renderização, pois isso pode levar a *bugs*.