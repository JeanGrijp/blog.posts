# Micro Front-End

# **O que são *Micro Front-ends*?**

O termo ganhou notoriedade quando foi publicado pela primeira vez no [Technology Radar da ThoughtWorks](https://www.thoughtworks.com/radar/techniques/micro-frontends) em 2016, sugerindo que as técnicas de microsserviços fossem aplicados também no desenvolvimento *front-end*. Os times internos começaram a chamar isto de ***micro front-ends***.

> a web application is broken up by its pages and features, with each feature being owned end-to-end by a single team — ThoughtWorks
> 

## **As principais ideias que sustentam os Micro Front-ends**

1. Cada time deve ser capaz de escolher e atualizar sua *stack* tecnológica de forma independente.
2. O código de cada serviço deve ser isolado e auto-contido, sem estados compartilhados ou variáveis globais.
3. Onde a ideia 2 não for aplicável, deve haver uma convenção na nomenclatura de *Local Storage*, *Cookies*, eventos e outros recursos para evitar conflitos.
4. Prefira os recursos nativos do *browser* ao invés de *API* customizadas.
5. A *feature* desenvolvida deve ser resiliente e utilizável, mesmo que haja problemas ao carregar o código *JavaScript.*