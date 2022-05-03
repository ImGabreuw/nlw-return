# Stage 1

> ## **Vite**

Os navegadores não conseguem acompanhar o ritmo de lançamento de novas funcionalidades do JavaScript, por isso foi criado ferramentas denominados de **transcompilador**.


Os **transcompilador** servem para converter o código fonte, escrito em uma versão mais recete do JavaScript, em uma mais antiga e consolidada na maioria dos navegadores. Essa ferramenta gera um único arquivo, comumente chamado de _bundle_, resultado desse processo.

> **OBS**: a versão do JavaScript utilizado no _bundle_ é configurável.

Alternativas do Vite:

- [_Babel_](https://babeljs.io/),

- [_Webpack_](https://webpack.js.org/)

> ## **React**

### **Componente**

O conceito de **componente** é um dos pilares do React.

Um componente pode ser definido da seguinte forma:

```ts
function App() {
  return <h1>Hello World!</h1>
}
```

Ou seja, uma **função** que retorna uma **HTML** (JSX ou TSX).

**IMPORTANTE**: para retornar múltiplos componentes é necessário utilizar um elemento por volta desses componentes, por exemplo:

```ts
function App() {
  return (
    <>
      <h1>Hello World!</h1>
      <h1>Hello World!</h1>
      <h1>Hello World!</h1>
      <h1>Hello World!</h1>
    </>
  )
}
```

> `<></>` (_fragment_) é um elemento exclusivo do React, é como uma `div`, porém ele não entra na hierarquia de elementos do DOM.

```ts
function App() {
  return (
    [
      <h1>Hello World!</h1>,
      <h1>Hello World!</h1>,
      <h1>Hello World!</h1>,
      <h1>Hello World!</h1>,
    ]
  )
}
```

> A forma acima não é muito utilizado.

### **Propriedades**

O conceito de **propriedades** é o outro pilar do React.

Todo componente pode ter 0 ou mais propriedades e são declaradas da seguinte forma:

> **OBS**: por convenção, o nome do parâmetro de um componente que possua propriedade(s) é `props`

```ts
function App(props) {
  // ...
}
```

É possível utilizar a **atribuição via desestruturação** (destructuring assignment):

```ts
function App({ ... }) {
  // ...
}
```

> ## **Phosphor-icons**

[_Phosphor-icons_](https://github.com/phosphor-icons/phosphor-home) é uma biblioteca que fornece uma variedade de ícones, além de possibilitar a customização dos mesmos de forma extremamente simples.

> ## **Machetes do Chrome DevTools**

### Descobrir a cor de um elemento

1. Botão direito no elemento que você deseja descobrir a cor

2. Clicar em `inspecionar` (`Inspect`)

3. Na aba `Elements` (na aba do DevTools do Chrome), clicar na aba `Computed`

4. Buscar a propriedade que possua essa cor (Ex: `background-color`)

5. Clicar `SHIFT` + `Botão esquerdo` em cima da cor para visualizar o formato desejado dessa cor

> ## **Bibliotecas de acessibilidade**

- [Reakit](https://reakit.io/)

- [Radix UI](https://www.radix-ui.com/)

- [Headless UI](https://headlessui.dev/)

Essas bibliotecas são implementações do [_ARIA_](https://developer.mozilla.org/pt-BR/docs/Web/Accessibility/ARIA).

### **Headless UI**

Essa biblioteca de acessibilidade foi desenvolvido pela equipe do Tailwind CSS e por isso possuí uma integração com o Tailwind CSS, trazendo alguns comportamentos padrão de acessibilidade para os componentes.

Sem _Headless UI_:

```ts
import { ChatTeardropDots } from "phosphor-react";
import { useState } from "react";

export function Widget() {
  const [isWidgetOpen, setIsWidgetOpen] = useState(false);

  function toggleWidgetVisibility() {
    setIsWidgetOpen(!isWidgetOpen);
  }

  return (
    <div className="absolute bottom-5 right-5">
      { isWidgetOpen && <p>Hello World!</p> }

      <button onClick={toggleWidgetVisibility} className="flex items-center bg-brand-500 rounded-full px-3 h-12 text-white group">
        <ChatTeardropDots className="w-6 h-6" />

        <span className="max-w-0 overflow-hidden group-hover:max-w-xs transition-all duration-500 ease-linear">
          <span className="pl-2"></span>
          Feedback
        </span>
      </button>
    </div>
  );
}
```

Com _Headless UI_:

```ts
import { ChatTeardropDots } from "phosphor-react";
import { Popover } from "@headlessui/react"

export function Widget() {
  return (
    <Popover className="absolute bottom-5 right-5">
      <Popover.Panel>Hello World!</Popover.Panel>

      <Popover.Button className="flex items-center bg-brand-500 rounded-full px-3 h-12 text-white group">
        <ChatTeardropDots className="w-6 h-6" />

        <span className="max-w-0 overflow-hidden group-hover:max-w-xs transition-all duration-500 ease-linear">
          <span className="pl-2"></span>
          Feedback
        </span>
      </Popover.Button>
    </Popover>
  );
}
``` 