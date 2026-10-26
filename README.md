# Escala 5x2

Consulta gratuita sobre a escala 5x2 (5 dias de trabalho e 2 de folga por semana), com base na Emenda Constitucional nº 141/2026, e funil de leads para a PeopleGT.

## Páginas

- **`index.html`**: página completa para trabalhadores e empresários. Explicação, cronograma, o que muda e o que não muda, base de conhecimento, calculadora semanal e mensal, comparação entre escalas, riscos, formulário de avisos e chamada para o kit pago (só no modo empresário).
- **`leigo.html`**: versão simples, para quem está começando.
- **`politica-de-privacidade.html`**: modelo de política para o formulário. Tem campos entre colchetes para preencher, e precisa de revisão do jurídico.
- **`docs/base-de-conhecimento.md`**: fontes, regras artigo por artigo e pendências.

## Kit pago (fora do repositório)

O repositório é **público**. Por isso o kit vendido na Hotmart (`kit-pago/kit-escala-5x2.html`) está no `.gitignore` e não é publicado. Guarde o arquivo fora deste repositório, por exemplo em um repositório privado.

## Antes de publicar

Edite o início do `<script>` em `index.html`:

```js
var LEAD_ENDPOINT = "";  // URL que recebe o formulário e cria o lead no Pipedrive
var HOTMART_URL = "";    // link do checkout do kit na Hotmart
```

- **`LEAD_ENDPOINT` vazio:** o formulário avisa que o cadastro ainda não está disponível e não envia nada.
- **`HOTMART_URL` vazio:** a chamada do kit não aparece.

### Formulário para o Pipedrive

**Nunca coloque o token da API do Pipedrive na página.** Qualquer visitante conseguiria ler e usar. Use um intermediário:

1. Crie um cenário no Make (ou um Zap no Zapier) com gatilho "Webhook".
2. Copie a URL do webhook para `LEAD_ENDPOINT`.
3. No cenário, crie a pessoa e o lead no Pipedrive com os campos recebidos.
4. Se a PeopleGT já tiver um endpoint próprio que envia para o Pipedrive, ele também pode ser usado.

O formulário envia em `application/x-www-form-urlencoded` com `mode: "no-cors"`. Assim o webhook não precisa liberar CORS, mas a página não consegue ler a resposta. Confira no Make ou Zapier se os leads estão chegando.

Campos enviados: `nome`, `email`, `whatsapp`, `perfil`, `empresa`, `colaboradores`, `setor`, `consentimento_avisos`, `consentimento_peoplegt` (só se marcado), `origem`, `modo_pagina`, `data_consentimento` e as UTMs da URL (`utm_source`, `utm_medium`, `utm_campaign`, `utm_content`, `utm_term`).

### Publicação

As páginas são estáticas. Podem ir para o GitHub Pages ou qualquer hospedagem de arquivos, sem build.

## Status das informações

- A emenda foi promulgada em 16/10/2026, segundo reportagens. Ela ainda não está em vigor.
- Fontes divergem entre 15/12 e 16/12/2026 como data de início.
- O texto oficial da emenda ainda precisa ser conferido no Planalto.
- As páginas são informativas e não substituem orientação jurídica ou contábil.
