# BRA-Icons

BRA-Icons é um catálogo autoral, SVG-First, criado para equipes que precisam de uma linguagem visual mais refinada, consistente e memorável do que coleções genéricas. Ele foi desenhado para acelerar interfaces digitais, materiais promocionais, áreas logadas, landing pages, dashboards e fluxos de produto com um vocabulário visual em português brasileiro, tornando a escolha do ícone mais intuitiva desde o conceito até a implementação.

Para designers, isso reduz atrito entre ideia, nomenclatura e aplicação. Em vez de adaptar a interface a nomes frios ou ambíguos, você trabalha com termos claros como alerta, carteira, notificações, usuário-aprovado, relatório e validar. O resultado é um acervo mais fácil de explorar, mais fácil de padronizar em equipe e mais coerente na entrega final.

## Por que escolher o BRA-Icons

- Linguagem visual autoral, com identidade própria e presença mais marcante para produtos digitais.
- Nomenclatura semântica em português brasileiro, facilitando busca, especificação e handoff.
- Catálogo amplo, com 2.078 ícones prontos para cenários institucionais, comerciais, operacionais e de produto.
- Consumo simples em HTML com span, i ou svg, sem exigir framework específico.
- Personalização natural por cor e tamanho usando currentColor e medidas do próprio layout.
- Pronto para uso local ou por CDN, com onboarding rápido para protótipos e produto em produção.

## O que o designer ganha na prática

- Mais velocidade para montar telas, componentes e estados de interface.
- Menos ambiguidade na escolha de ícones durante criação, revisão e aprovação.
- Melhor consistência entre linguagem visual, protótipo e implementação.
- Facilidade para aplicar o mesmo ícone em menus, botões, cards, tabelas, status e chamadas de ação.
- Um catálogo pensado para crescer sem perder coerência semântica.

## Instalação rápida

### Opção 1: via CDN

O modo mais rápido para publicar o catálogo completo é carregar a folha de estilos do bundle via CDN.

> Observação: o bundle público do BRA-Icons é CSS. Por isso, o consumo correto via CDN usa o arquivo .css do bundle publicado.

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/jepasa/bra-icons@0.2.1/bundle/bra-icons.bundle.min.css">
```

Se quiser travar uma versão específica para evitar mudanças inesperadas, substitua `@latest` pela versão publicada desejada.

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/jepasa/bra-icons@0.2.1/bundle/bra-icons.bundle.min.css">
```

### Opção 2: uso local no seu projeto

Se preferir manter os arquivos no próprio projeto, copie a folha de estilos compilada para a sua pasta de assets e referencie-a no HTML.

```html
<link rel="stylesheet" href="./assets/css/bra-icons.bundle.min.css">
```

Esse fluxo é indicado quando a equipe quer controle total sobre cache, empacotamento e distribuição interna.

### Opção 3: uso local com sprite SVG

Se você preferir trabalhar com a tag svg no markup, mantenha o arquivo do sprite acessível junto aos seus assets.

```html
<link rel="stylesheet" href="./assets/css/bra-icons.css">
```

Depois, use o sprite no HTML:

```html
<svg class="bra-icon" data-bra-icon="buscar" aria-hidden="true">
  <use href="./assets/bra-icons.svg#buscar"></use>
</svg>
```

## Como usar

### Uso recomendado com span

```html
<span class="bra-icon bra-icon--alerta" data-bra-icon="alerta" aria-hidden="true"></span>
```

### Uso alternativo com i

```html
<i class="bra-icon bra-icon--calendario" data-bra-icon="calendario" aria-hidden="true"></i>
```

### Exemplo com rótulo acessível

```html
<span class="bra-icon bra-icon--aprovado" data-bra-icon="aprovado" role="img" aria-label="Aprovado"></span>
```

## Padrão de uso recomendado

- Use sempre a classe base `bra-icon`.
- Para o modo por classe, complemente com `bra-icon--nome-do-icone`.
- Use `data-bra-icon` quando quiser facilitar inspeção, auditoria de DOM e manutenção futura.
- Quando o ícone for apenas decorativo, mantenha `aria-hidden="true"`.
- Quando o ícone carregar significado sozinho, use `role="img"` com `aria-label`.

## Como personalizar

O BRA-Icons foi construído para seguir a cor do texto e escalar com facilidade no layout. Na prática, isso permite ajustar cor, tamanho e contexto visual sem editar o vetor do ícone.

### Cor

Os ícones acompanham a propriedade `color` do elemento ou do container.

```css
.botao-primario {
  color: #0f5a43;
}

.botao-primario .bra-icon {
  color: currentColor;
}
```

### Tamanho

No consumo por classe, o tamanho acompanha a medida do próprio elemento. O caminho mais simples é controlar isso com `font-size`.

```css
.bra-icon {
  font-size: 20px;
}

.hero-card .bra-icon {
  font-size: 32px;
}
```

### Alinhamento em componentes

```css
.acao-com-icone {
  display: inline-flex;
  align-items: center;
  gap: 0.625rem;
}
```

### Exemplo em botão

```html
<button type="button" class="acao-com-icone">
  <span class="bra-icon bra-icon--baixar" data-bra-icon="baixar" aria-hidden="true"></span>
  Baixar catálogo
</button>
```

### Exemplo em menu

```html
<a href="/financeiro" class="acao-com-icone">
  <i class="bra-icon bra-icon--financeiro" data-bra-icon="financeiro" aria-hidden="true"></i>
  Financeiro
</a>
```

### Exemplo em card de status

```html
<div class="acao-com-icone" style="color:#0e8a57;">
  <span class="bra-icon bra-icon--confirmado" data-bra-icon="confirmado" aria-hidden="true"></span>
  Operação confirmada
</div>
```

### Compilar somente os ícones desejados

Se você quiser gerar uma versão mais enxuta do BRA-Icons para usar só os ícones realmente presentes no seu projeto, pode informar a lista desejada no comando.

Exemplo com os nomes diretamente na linha de comando:

```bash
npm run build:subset -- --icons alerta,arquivo,carrinho
```

Exemplo usando um arquivo com a sua seleção:

```text
alerta
arquivo
carrinho
confirmado
financeiro
```

```bash
npm run build:subset -- --icons-file ./meus-icones.txt
```

Se quiser apenas validar a seleção antes de gerar o pacote, use:

```bash
npm run build:subset:check -- --icons alerta,arquivo,carrinho
```

Esse fluxo é útil quando o objetivo é reduzir o pacote final e levar para produção apenas os ícones realmente usados na interface. Se a sua prioridade for simplicidade máxima, o bundle completo via CDN continua sendo a opção mais direta.

## Quando usar cada formato

- span: melhor para a maioria das interfaces, protótipos HTML e componentes de interface.
- i: útil quando seu projeto já segue esse padrão em menus, listas ou legados visuais.
- svg com sprite: ideal quando você quer trabalhar diretamente com SVG no markup.

## Boas práticas para times de design

- Escolha um conjunto preferencial de ícones por contexto para manter consistência entre telas.
- Evite alternar ícones muito parecidos para a mesma ação ao longo do produto.
- Prefira os nomes semânticos do catálogo na especificação visual, no handoff e nos componentes.
- Use variações de cor e contexto visual para reforçar hierarquia sem precisar trocar de ícone desnecessariamente.
- Em interfaces densas, combine ícone + rótulo quando houver risco de ambiguidade.

## Catálogo completo

O índice abaixo lista todo o acervo disponível neste momento, com nome semântico, descrição de uso e tags de busca.

<details>
<summary>Ver tabela completa de ícones</summary>

| Nome | Descricao | Tags |
| --- | --- | --- |
| adicionar | Adicionar, criar novo item ou expandir. | adicionar, acao, comando, criar, novo, ações |
| adicionar-circulo | Representa adicionar circulo, útil para ações, comandos e interações diretas na interface. | adicionar-circulo, adicionar, circulo, acao, comando, ações |
| adicionar-circulo-destaque | Representa adicionar circulo destaque, útil para ações, comandos e interações diretas na interface. | adicionar-circulo-destaque, adicionar, circulo, destaque, acao, ações |
| adicionar-circulo-dotted | Representa adicionar circulo dotted, útil para ações, comandos e interações diretas na interface. | adicionar-circulo-dotted, adicionar, circulo, dotted, acao, ações |
| adicionar-cortado-minus | Representa adicionar cortado minus, útil para ações, comandos e interações diretas na interface. | adicionar-cortado-minus, adicionar, cortado, minus, acao, ações |
| adicionar-icon | Representa adicionar icon, útil para ações, comandos e interações diretas na interface. | adicionar-icon, adicionar, icon, acao, comando, ações |
| adicionar-no | Adição de no, expansão estrutural ou hierarquia. | adicionar-no, adicionar, sistema, infraestrutura, adicao, no, nó |
| adicionar-quadrado | Representa adicionar quadrado, útil para ações, comandos e interações diretas na interface. | adicionar-quadrado, adicionar, quadrado, acao, comando, ações |
| adicionar-quadrado-destaque | Representa adicionar quadrado destaque, útil para ações, comandos e interações diretas na interface. | adicionar-quadrado-destaque, adicionar, quadrado, destaque, acao, ações |
| adicionar-quadrado-dotted | Representa adicionar quadrado dotted, útil para ações, comandos e interações diretas na interface. | adicionar-quadrado-dotted, adicionar, quadrado, dotted, acao, ações |
| adicionar-usuario | Adição de usuário, convite ou novo cadastro. | adicionar-usuario, adicionar, usuario, acesso, adicao, usuário, usuários |
| agenda-confirmada | Agenda validada, compromisso confirmado ou data aprovada. | agenda-confirmada, agenda, confirmada, tempo, validada, agendamento |
| agua | Representa agua, útil para configuração, integrações e recursos digitais. | agua, sistema, infraestrutura |
| aguardando | Espera, processamento, fila ou transição em andamento. | aguardando, agenda, tempo, espera, processamento, agendamento |
| ajuste-tecnico | Ferramenta de ajuste técnico, manutenção fina ou configuração avançada. | ajuste-tecnico, ajuste, tecnico, sistema, infraestrutura, técnico |
| ajustes | Ajustes manuais, parametrização ou refinamento operacional. | ajustes, sistema, infraestrutura, manuais, parametrizacao |
| ajustes-finos | Ajustes secundarios, tuning fino ou configuração complementar. | ajustes-finos, ajustes, finos, sistema, infraestrutura |
| alarme | Representa alarme, útil para configuração, integrações e recursos digitais. | alarme, sistema, infraestrutura |
| alarme-destaque | Representa alarme destaque, útil para configuração, integrações e recursos digitais. | alarme-destaque, alarme, destaque, sistema, infraestrutura |
| alerta | Alerta moderado, atenção ou exceção nao critica. | alerta, status, estado, moderado, atencao, estados |
| alexa | Representa alexa, útil para configuração, integrações e recursos digitais. | alexa, sistema, infraestrutura |
| alfabeto | Representa alfabeto, útil para configuração, integrações e recursos digitais. | alfabeto, sistema, infraestrutura |
| alfabeto-maiusculo | Representa alfabeto maiusculo, útil para configuração, integrações e recursos digitais. | alfabeto-maiusculo, alfabeto, maiusculo, sistema, infraestrutura |
| alinhar-base | Representa alinhar base, útil para configuração, integrações e recursos digitais. | alinhar-base, alinhar, base, sistema, infraestrutura |
| alinhar-centro | Representa alinhar centro, útil para configuração, integrações e recursos digitais. | alinhar-centro, alinhar, centro, sistema, infraestrutura |
| alinhar-fim | Representa alinhar fim, útil para configuração, integrações e recursos digitais. | alinhar-fim, alinhar, fim, sistema, infraestrutura |
| alinhar-inicio | Representa alinhar inicio, útil para navegação, direção e fluxo de interface. | alinhar-inicio, alinhar, inicio, navegacao, fluxo, navegação |
| alinhar-meio | Representa alinhar meio, útil para configuração, integrações e recursos digitais. | alinhar-meio, alinhar, meio, sistema, infraestrutura |
| alinhar-topo | Representa alinhar topo, útil para configuração, integrações e recursos digitais. | alinhar-topo, alinhar, topo, sistema, infraestrutura |
| alipay | Representa alipay, útil para configuração, integrações e recursos digitais. | alipay, sistema, infraestrutura |
| alternancia-off | Representa alternancia off, útil para configuração, integrações e recursos digitais. | alternancia-off, alternancia, off, sistema, infraestrutura |
| alternancia-on | Representa alternancia on, útil para configuração, integrações e recursos digitais. | alternancia-on, alternancia, sistema, infraestrutura, on |
| alternancias | Representa alternancias, útil para configuração, integrações e recursos digitais. | alternancias, sistema, infraestrutura |
| alternativo | Representa alternativo, útil para configuração, integrações e recursos digitais. | alternativo, sistema, infraestrutura |
| alto-falante | Representa alto falante, útil para configuração, integrações e recursos digitais. | alto-falante, alto, falante, sistema, infraestrutura |
| alto-falante-destaque | Representa alto falante destaque, útil para configuração, integrações e recursos digitais. | alto-falante-destaque, alto, falante, destaque, sistema, infraestrutura |
| alvo | Representa alvo, útil para configuração, integrações e recursos digitais. | alvo, sistema, infraestrutura |
| amazon | Representa amazon, útil para configuração, integrações e recursos digitais. | amazon, sistema, infraestrutura |
| amd | Representa amd, útil para configuração, integrações e recursos digitais. | amd, sistema, infraestrutura |
| ampulheta | Representa ampulheta, útil para tempo, agenda e acompanhamento de prazos. | ampulheta, agenda, tempo, agendamento |
| ampulheta-base | Representa ampulheta base, útil para tempo, agenda e acompanhamento de prazos. | ampulheta-base, ampulheta, base, agenda, tempo, agendamento |
| ampulheta-topo | Representa ampulheta topo, útil para tempo, agenda e acompanhamento de prazos. | ampulheta-topo, ampulheta, topo, agenda, tempo, agendamento |
| android | Representa android, útil para configuração, integrações e recursos digitais. | android, sistema, infraestrutura |
| android2 | Representa android2, útil para configuração, integrações e recursos digitais. | android2, sistema, infraestrutura |
| anthropic | Representa anthropic, útil para configuração, integrações e recursos digitais. | anthropic, sistema, infraestrutura |
| aplicativo | Representa aplicativo, útil para configuração, integrações e recursos digitais. | aplicativo, sistema, infraestrutura |
| aplicativo-indicador | Representa aplicativo indicador, útil para métricas, indicadores e leitura de dados. | aplicativo-indicador, aplicativo, indicador, dados, analise, análise |
| apple | Representa apple, útil para configuração, integrações e recursos digitais. | apple, sistema, infraestrutura |
| apple-music | Representa apple music, útil para configuração, integrações e recursos digitais. | apple-music, apple, music, sistema, infraestrutura |
| aprovado | Aprovacao formal, item homologado ou validado em fluxo. | aprovado, status, estado, aprovacao, formal, estados |
| arco-iris | Representa arco iris, útil para configuração, integrações e recursos digitais. | arco-iris, arco, iris, sistema, infraestrutura |
| armazenamento | Disco, armazenamento persistente ou backup local. | armazenamento, logistica, operacao, disco, persistente, logística, operações |
| arquivo | Ação ou área de arquivamento, histórico congelado ou itens antigos. | arquivo, documento, arquivamento, historico, congelado, arquivos, mídia |
| arquivo-adicionar | Representa arquivo adicionar, útil para documentos, conteúdo e organização de arquivos. | arquivo-adicionar, arquivo, adicionar, documento, arquivos, mídia |
| arquivo-adicionar-destaque | Representa arquivo adicionar destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-adicionar-destaque, arquivo, adicionar, destaque, documento, arquivos, mídia |
| arquivo-ai | Representa arquivo ai, útil para documentos, conteúdo e organização de arquivos. | arquivo-ai, arquivo, documento, ai, arquivos, mídia |
| arquivo-barra-grafico | Representa arquivo barra grafico, útil para documentos, conteúdo e organização de arquivos. | arquivo-barra-grafico, arquivo, barra, grafico, documento, arquivos, mídia |
| arquivo-barra-grafico-destaque | Representa arquivo barra grafico destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-barra-grafico-destaque, arquivo, barra, grafico, destaque, arquivos, mídia |
| arquivo-binary | Representa arquivo binary, útil para documentos, conteúdo e organização de arquivos. | arquivo-binary, arquivo, binary, documento, arquivos, mídia |
| arquivo-binary-destaque | Representa arquivo binary destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-binary-destaque, arquivo, binary, destaque, documento, arquivos, mídia |
| arquivo-break | Representa arquivo break, útil para documentos, conteúdo e organização de arquivos. | arquivo-break, arquivo, break, documento, arquivos, mídia |
| arquivo-break-destaque | Representa arquivo break destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-break-destaque, arquivo, break, destaque, documento, arquivos, mídia |
| arquivo-cadeado | Representa arquivo cadeado, útil para documentos, conteúdo e organização de arquivos. | arquivo-cadeado, arquivo, cadeado, documento, arquivos, mídia |
| arquivo-cadeado-destaque | Representa arquivo cadeado destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-cadeado-destaque, arquivo, cadeado, destaque, documento, arquivos, mídia |
| arquivo-cavalete | Representa arquivo cavalete, útil para documentos, conteúdo e organização de arquivos. | arquivo-cavalete, arquivo, cavalete, documento, arquivos, mídia |
| arquivo-cavalete-destaque | Representa arquivo cavalete destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-cavalete-destaque, arquivo, cavalete, destaque, documento, arquivos, mídia |
| arquivo-codigo | Representa arquivo codigo, útil para documentos, conteúdo e organização de arquivos. | arquivo-codigo, arquivo, codigo, documento, arquivos, mídia |
| arquivo-codigo-destaque | Representa arquivo codigo destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-codigo-destaque, arquivo, codigo, destaque, documento, arquivos, mídia |
| arquivo-confirmado | Representa arquivo confirmado, útil para documentos, conteúdo e organização de arquivos. | arquivo-confirmado, arquivo, confirmado, documento, arquivos, mídia |
| arquivo-confirmado-destaque | Representa arquivo confirmado destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-confirmado-destaque, arquivo, confirmado, destaque, documento, arquivos, mídia |
| arquivo-cs | Representa arquivo cs, útil para documentos, conteúdo e organização de arquivos. | arquivo-cs, arquivo, documento, cs, arquivos, mídia |
| arquivo-css | Representa arquivo css, útil para documentos, conteúdo e organização de arquivos. | arquivo-css, arquivo, css, documento, arquivos, mídia |
| arquivo-csv | Representa arquivo csv, útil para documentos, conteúdo e organização de arquivos. | arquivo-csv, arquivo, csv, documento, arquivos, mídia |
| arquivo-destaque | Representa arquivo destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-destaque, arquivo, destaque, documento, arquivos, mídia |
| arquivo-destaque-icon | Representa arquivo destaque icon, útil para documentos, conteúdo e organização de arquivos. | arquivo-destaque-icon, arquivo, destaque, icon, documento, arquivos, mídia |
| arquivo-diff | Representa arquivo diff, útil para documentos, conteúdo e organização de arquivos. | arquivo-diff, arquivo, diff, documento, arquivos, mídia |
| arquivo-diff-destaque | Representa arquivo diff destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-diff-destaque, arquivo, diff, destaque, documento, arquivos, mídia |
| arquivo-doc | Representa arquivo doc, útil para documentos, conteúdo e organização de arquivos. | arquivo-doc, arquivo, doc, documento, arquivos, mídia |
| arquivo-docx | Representa arquivo docx, útil para documentos, conteúdo e organização de arquivos. | arquivo-docx, arquivo, docx, documento, arquivos, mídia |
| arquivo-earmark | Representa arquivo earmark, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark, arquivo, earmark, documento, arquivos, mídia |
| arquivo-earmark-adicionar | Representa arquivo earmark adicionar, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-adicionar, arquivo, earmark, adicionar, documento, arquivos, mídia |
| arquivo-earmark-adicionar-destaque | Representa arquivo earmark adicionar destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-adicionar-destaque, arquivo, earmark, adicionar, destaque, arquivos, mídia |
| arquivo-earmark-barra-grafico | Representa arquivo earmark barra grafico, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-barra-grafico, arquivo, earmark, barra, grafico, arquivos, mídia |
| arquivo-earmark-barra-grafico-destaque | Representa arquivo earmark barra grafico destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-barra-grafico-destaque, arquivo, earmark, barra, grafico, destaque, arquivos, mídia |
| arquivo-earmark-binary | Representa arquivo earmark binary, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-binary, arquivo, earmark, binary, documento, arquivos, mídia |
| arquivo-earmark-binary-destaque | Representa arquivo earmark binary destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-binary-destaque, arquivo, earmark, binary, destaque, arquivos, mídia |
| arquivo-earmark-break | Representa arquivo earmark break, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-break, arquivo, earmark, break, documento, arquivos, mídia |
| arquivo-earmark-break-destaque | Representa arquivo earmark break destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-break-destaque, arquivo, earmark, break, destaque, arquivos, mídia |
| arquivo-earmark-cadeado | Representa arquivo earmark cadeado, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-cadeado, arquivo, earmark, cadeado, documento, arquivos, mídia |
| arquivo-earmark-cadeado-destaque | Representa arquivo earmark cadeado destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-cadeado-destaque, arquivo, earmark, cadeado, destaque, arquivos, mídia |
| arquivo-earmark-cavalete | Representa arquivo earmark cavalete, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-cavalete, arquivo, earmark, cavalete, documento, arquivos, mídia |
| arquivo-earmark-cavalete-destaque | Representa arquivo earmark cavalete destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-cavalete-destaque, arquivo, earmark, cavalete, destaque, arquivos, mídia |
| arquivo-earmark-codigo | Representa arquivo earmark codigo, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-codigo, arquivo, earmark, codigo, documento, arquivos, mídia |
| arquivo-earmark-codigo-destaque | Representa arquivo earmark codigo destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-codigo-destaque, arquivo, earmark, codigo, destaque, arquivos, mídia |
| arquivo-earmark-confirmado | Representa arquivo earmark confirmado, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-confirmado, arquivo, earmark, confirmado, documento, arquivos, mídia |
| arquivo-earmark-confirmado-destaque | Representa arquivo earmark confirmado destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-confirmado-destaque, arquivo, earmark, confirmado, destaque, arquivos, mídia |
| arquivo-earmark-destaque | Representa arquivo earmark destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-destaque, arquivo, earmark, destaque, documento, arquivos, mídia |
| arquivo-earmark-diff | Representa arquivo earmark diff, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-diff, arquivo, earmark, diff, documento, arquivos, mídia |
| arquivo-earmark-diff-destaque | Representa arquivo earmark diff destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-diff-destaque, arquivo, earmark, diff, destaque, arquivos, mídia |
| arquivo-earmark-excel | Representa arquivo earmark excel, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-excel, arquivo, earmark, excel, documento, arquivos, mídia |
| arquivo-earmark-excel-destaque | Representa arquivo earmark excel destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-excel-destaque, arquivo, earmark, excel, destaque, arquivos, mídia |
| arquivo-earmark-font | Representa arquivo earmark font, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-font, arquivo, earmark, font, documento, arquivos, mídia |
| arquivo-earmark-font-destaque | Representa arquivo earmark font destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-font-destaque, arquivo, earmark, font, destaque, arquivos, mídia |
| arquivo-earmark-imagem | Representa arquivo earmark imagem, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-imagem, arquivo, earmark, imagem, documento, arquivos, mídia |
| arquivo-earmark-imagem-destaque | Representa arquivo earmark imagem destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-imagem-destaque, arquivo, earmark, imagem, destaque, arquivos, mídia |
| arquivo-earmark-lock2 | Representa arquivo earmark lock2, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-lock2, arquivo, earmark, lock2, documento, arquivos, mídia |
| arquivo-earmark-lock2-destaque | Representa arquivo earmark lock2 destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-lock2-destaque, arquivo, earmark, lock2, destaque, arquivos, mídia |
| arquivo-earmark-medical | Representa arquivo earmark medical, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-medical, arquivo, earmark, medical, documento, arquivos, mídia |
| arquivo-earmark-medical-destaque | Representa arquivo earmark medical destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-medical-destaque, arquivo, earmark, medical, destaque, arquivos, mídia |
| arquivo-earmark-minus | Representa arquivo earmark minus, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-minus, arquivo, earmark, minus, documento, arquivos, mídia |
| arquivo-earmark-minus-destaque | Representa arquivo earmark minus destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-minus-destaque, arquivo, earmark, minus, destaque, arquivos, mídia |
| arquivo-earmark-musica | Representa arquivo earmark musica, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-musica, arquivo, earmark, musica, documento, arquivos, mídia |
| arquivo-earmark-musica-destaque | Representa arquivo earmark musica destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-musica-destaque, arquivo, earmark, musica, destaque, arquivos, mídia |
| arquivo-earmark-pdf | Representa arquivo earmark pdf, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-pdf, arquivo, earmark, pdf, documento, arquivos, mídia |
| arquivo-earmark-pdf-destaque | Representa arquivo earmark pdf destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-pdf-destaque, arquivo, earmark, pdf, destaque, arquivos, mídia |
| arquivo-earmark-pessoa | Representa arquivo earmark pessoa, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-pessoa, arquivo, earmark, pessoa, documento, arquivos, mídia |
| arquivo-earmark-pessoa-destaque | Representa arquivo earmark pessoa destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-pessoa-destaque, arquivo, earmark, pessoa, destaque, arquivos, mídia |
| arquivo-earmark-post | Representa arquivo earmark post, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-post, arquivo, earmark, post, documento, arquivos, mídia |
| arquivo-earmark-post-destaque | Representa arquivo earmark post destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-post-destaque, arquivo, earmark, post, destaque, arquivos, mídia |
| arquivo-earmark-ppt | Representa arquivo earmark ppt, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-ppt, arquivo, earmark, ppt, documento, arquivos, mídia |
| arquivo-earmark-ppt-destaque | Representa arquivo earmark ppt destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-ppt-destaque, arquivo, earmark, ppt, destaque, arquivos, mídia |
| arquivo-earmark-remover | Representa arquivo earmark remover, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-remover, arquivo, earmark, remover, documento, arquivos, mídia |
| arquivo-earmark-remover-destaque | Representa arquivo earmark remover destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-remover-destaque, arquivo, earmark, remover, destaque, arquivos, mídia |
| arquivo-earmark-reproduzir | Representa arquivo earmark reproduzir, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-reproduzir, arquivo, earmark, reproduzir, documento, arquivos, mídia |
| arquivo-earmark-reproduzir-destaque | Representa arquivo earmark reproduzir destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-reproduzir-destaque, arquivo, earmark, reproduzir, destaque, arquivos, mídia |
| arquivo-earmark-richtext | Representa arquivo earmark richtext, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-richtext, arquivo, earmark, richtext, documento, arquivos, mídia |
| arquivo-earmark-richtext-destaque | Representa arquivo earmark richtext destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-richtext-destaque, arquivo, earmark, richtext, destaque, arquivos, mídia |
| arquivo-earmark-ruled | Representa arquivo earmark ruled, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-ruled, arquivo, earmark, ruled, documento, arquivos, mídia |
| arquivo-earmark-ruled-destaque | Representa arquivo earmark ruled destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-ruled-destaque, arquivo, earmark, ruled, destaque, arquivos, mídia |
| arquivo-earmark-seta-baixo | Representa arquivo earmark seta baixo, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-seta-baixo, arquivo, earmark, seta, baixo, arquivos, mídia |
| arquivo-earmark-seta-baixo-destaque | Representa arquivo earmark seta baixo destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-seta-baixo-destaque, arquivo, earmark, seta, baixo, destaque, arquivos, mídia |
| arquivo-earmark-seta-cima | Representa arquivo earmark seta cima, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-seta-cima, arquivo, earmark, seta, cima, arquivos, mídia |
| arquivo-earmark-seta-cima-destaque | Representa arquivo earmark seta cima destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-seta-cima-destaque, arquivo, earmark, seta, cima, destaque, arquivos, mídia |
| arquivo-earmark-slides | Representa arquivo earmark slides, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-slides, arquivo, earmark, slides, documento, arquivos, mídia |
| arquivo-earmark-slides-destaque | Representa arquivo earmark slides destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-slides-destaque, arquivo, earmark, slides, destaque, arquivos, mídia |
| arquivo-earmark-spreadsheet | Representa arquivo earmark spreadsheet, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-spreadsheet, arquivo, earmark, spreadsheet, documento, arquivos, mídia |
| arquivo-earmark-spreadsheet-destaque | Representa arquivo earmark spreadsheet destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-spreadsheet-destaque, arquivo, earmark, spreadsheet, destaque, arquivos, mídia |
| arquivo-earmark-texto-destaque | Representa arquivo earmark texto destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-texto-destaque, arquivo, earmark, texto, destaque, arquivos, mídia |
| arquivo-earmark-word | Representa arquivo earmark word, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-word, arquivo, earmark, word, documento, arquivos, mídia |
| arquivo-earmark-word-destaque | Representa arquivo earmark word destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-word-destaque, arquivo, earmark, word, destaque, arquivos, mídia |
| arquivo-earmark-zip | Representa arquivo earmark zip, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-zip, arquivo, earmark, zip, documento, arquivos, mídia |
| arquivo-earmark-zip-destaque | Representa arquivo earmark zip destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-earmark-zip-destaque, arquivo, earmark, zip, destaque, arquivos, mídia |
| arquivo-excel | Representa arquivo excel, útil para documentos, conteúdo e organização de arquivos. | arquivo-excel, arquivo, excel, documento, arquivos, mídia |
| arquivo-excel-destaque | Representa arquivo excel destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-excel-destaque, arquivo, excel, destaque, documento, arquivos, mídia |
| arquivo-exe | Representa arquivo exe, útil para documentos, conteúdo e organização de arquivos. | arquivo-exe, arquivo, exe, documento, arquivos, mídia |
| arquivo-font | Representa arquivo font, útil para documentos, conteúdo e organização de arquivos. | arquivo-font, arquivo, font, documento, arquivos, mídia |
| arquivo-font-destaque | Representa arquivo font destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-font-destaque, arquivo, font, destaque, documento, arquivos, mídia |
| arquivo-gif | Representa arquivo gif, útil para documentos, conteúdo e organização de arquivos. | arquivo-gif, arquivo, gif, documento, arquivos, mídia |
| arquivo-heic | Representa arquivo heic, útil para documentos, conteúdo e organização de arquivos. | arquivo-heic, arquivo, heic, documento, arquivos, mídia |
| arquivo-html | Representa arquivo html, útil para documentos, conteúdo e organização de arquivos. | arquivo-html, arquivo, html, documento, arquivos, mídia |
| arquivo-icon | Representa arquivo icon, útil para documentos, conteúdo e organização de arquivos. | arquivo-icon, arquivo, icon, documento, arquivos, mídia |
| arquivo-imagem | Representa arquivo imagem, útil para documentos, conteúdo e organização de arquivos. | arquivo-imagem, arquivo, imagem, documento, arquivos, mídia |
| arquivo-imagem-destaque | Representa arquivo imagem destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-imagem-destaque, arquivo, imagem, destaque, documento, arquivos, mídia |
| arquivo-java | Representa arquivo java, útil para documentos, conteúdo e organização de arquivos. | arquivo-java, arquivo, java, documento, arquivos, mídia |
| arquivo-jpg | Representa arquivo jpg, útil para documentos, conteúdo e organização de arquivos. | arquivo-jpg, arquivo, jpg, documento, arquivos, mídia |
| arquivo-js | Representa arquivo js, útil para documentos, conteúdo e organização de arquivos. | arquivo-js, arquivo, documento, js, arquivos, mídia |
| arquivo-json | Representa arquivo json, útil para documentos, conteúdo e organização de arquivos. | arquivo-json, arquivo, json, documento, arquivos, mídia |
| arquivo-jsx | Representa arquivo jsx, útil para documentos, conteúdo e organização de arquivos. | arquivo-jsx, arquivo, jsx, documento, arquivos, mídia |
| arquivo-key | Representa arquivo key, útil para documentos, conteúdo e organização de arquivos. | arquivo-key, arquivo, key, documento, arquivos, mídia |
| arquivo-lock2-destaque | Representa arquivo lock2 destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-lock2-destaque, arquivo, lock2, destaque, documento, arquivos, mídia |
| arquivo-m4p | Representa arquivo m4p, útil para documentos, conteúdo e organização de arquivos. | arquivo-m4p, arquivo, m4p, documento, arquivos, mídia |
| arquivo-md | Representa arquivo md, útil para documentos, conteúdo e organização de arquivos. | arquivo-md, arquivo, documento, md, arquivos, mídia |
| arquivo-mdx | Representa arquivo mdx, útil para documentos, conteúdo e organização de arquivos. | arquivo-mdx, arquivo, mdx, documento, arquivos, mídia |
| arquivo-medical | Representa arquivo medical, útil para documentos, conteúdo e organização de arquivos. | arquivo-medical, arquivo, medical, documento, arquivos, mídia |
| arquivo-medical-destaque | Representa arquivo medical destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-medical-destaque, arquivo, medical, destaque, documento, arquivos, mídia |
| arquivo-minus | Representa arquivo minus, útil para documentos, conteúdo e organização de arquivos. | arquivo-minus, arquivo, minus, documento, arquivos, mídia |
| arquivo-minus-destaque | Representa arquivo minus destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-minus-destaque, arquivo, minus, destaque, documento, arquivos, mídia |
| arquivo-mov | Representa arquivo mov, útil para documentos, conteúdo e organização de arquivos. | arquivo-mov, arquivo, mov, documento, arquivos, mídia |
| arquivo-mp3 | Representa arquivo mp3, útil para documentos, conteúdo e organização de arquivos. | arquivo-mp3, arquivo, mp3, documento, arquivos, mídia |
| arquivo-mp4 | Representa arquivo mp4, útil para documentos, conteúdo e organização de arquivos. | arquivo-mp4, arquivo, mp4, documento, arquivos, mídia |
| arquivo-musica | Representa arquivo musica, útil para documentos, conteúdo e organização de arquivos. | arquivo-musica, arquivo, musica, documento, arquivos, mídia |
| arquivo-musica-destaque | Representa arquivo musica destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-musica-destaque, arquivo, musica, destaque, documento, arquivos, mídia |
| arquivo-otf | Representa arquivo otf, útil para documentos, conteúdo e organização de arquivos. | arquivo-otf, arquivo, otf, documento, arquivos, mídia |
| arquivo-pdf | Representa arquivo pdf, útil para documentos, conteúdo e organização de arquivos. | arquivo-pdf, arquivo, pdf, documento, arquivos, mídia |
| arquivo-pdf-destaque | Representa arquivo pdf destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-pdf-destaque, arquivo, pdf, destaque, documento, arquivos, mídia |
| arquivo-pdf-icon | Representa arquivo pdf icon, útil para documentos, conteúdo e organização de arquivos. | arquivo-pdf-icon, arquivo, pdf, icon, documento, arquivos, mídia |
| arquivo-pessoa | Representa arquivo pessoa, útil para documentos, conteúdo e organização de arquivos. | arquivo-pessoa, arquivo, pessoa, documento, arquivos, mídia |
| arquivo-pessoa-destaque | Representa arquivo pessoa destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-pessoa-destaque, arquivo, pessoa, destaque, documento, arquivos, mídia |
| arquivo-php | Representa arquivo php, útil para documentos, conteúdo e organização de arquivos. | arquivo-php, arquivo, php, documento, arquivos, mídia |
| arquivo-png | Representa arquivo png, útil para documentos, conteúdo e organização de arquivos. | arquivo-png, arquivo, png, documento, arquivos, mídia |
| arquivo-post | Representa arquivo post, útil para documentos, conteúdo e organização de arquivos. | arquivo-post, arquivo, post, documento, arquivos, mídia |
| arquivo-post-destaque | Representa arquivo post destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-post-destaque, arquivo, post, destaque, documento, arquivos, mídia |
| arquivo-ppt | Representa arquivo ppt, útil para documentos, conteúdo e organização de arquivos. | arquivo-ppt, arquivo, ppt, documento, arquivos, mídia |
| arquivo-ppt-destaque | Representa arquivo ppt destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-ppt-destaque, arquivo, ppt, destaque, documento, arquivos, mídia |
| arquivo-ppt-icon | Representa arquivo ppt icon, útil para documentos, conteúdo e organização de arquivos. | arquivo-ppt-icon, arquivo, ppt, icon, documento, arquivos, mídia |
| arquivo-psd | Representa arquivo psd, útil para documentos, conteúdo e organização de arquivos. | arquivo-psd, arquivo, psd, documento, arquivos, mídia |
| arquivo-py | Representa arquivo py, útil para documentos, conteúdo e organização de arquivos. | arquivo-py, arquivo, documento, py, arquivos, mídia |
| arquivo-raw | Representa arquivo raw, útil para documentos, conteúdo e organização de arquivos. | arquivo-raw, arquivo, raw, documento, arquivos, mídia |
| arquivo-rb | Representa arquivo rb, útil para documentos, conteúdo e organização de arquivos. | arquivo-rb, arquivo, documento, rb, arquivos, mídia |
| arquivo-remover | Representa arquivo remover, útil para documentos, conteúdo e organização de arquivos. | arquivo-remover, arquivo, remover, documento, arquivos, mídia |
| arquivo-remover-destaque | Representa arquivo remover destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-remover-destaque, arquivo, remover, destaque, documento, arquivos, mídia |
| arquivo-reproduzir | Representa arquivo reproduzir, útil para documentos, conteúdo e organização de arquivos. | arquivo-reproduzir, arquivo, reproduzir, documento, arquivos, mídia |
| arquivo-reproduzir-destaque | Representa arquivo reproduzir destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-reproduzir-destaque, arquivo, reproduzir, destaque, documento, arquivos, mídia |
| arquivo-richtext | Representa arquivo richtext, útil para documentos, conteúdo e organização de arquivos. | arquivo-richtext, arquivo, richtext, documento, arquivos, mídia |
| arquivo-richtext-destaque | Representa arquivo richtext destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-richtext-destaque, arquivo, richtext, destaque, documento, arquivos, mídia |
| arquivo-ruled | Representa arquivo ruled, útil para documentos, conteúdo e organização de arquivos. | arquivo-ruled, arquivo, ruled, documento, arquivos, mídia |
| arquivo-ruled-destaque | Representa arquivo ruled destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-ruled-destaque, arquivo, ruled, destaque, documento, arquivos, mídia |
| arquivo-sass | Representa arquivo sass, útil para documentos, conteúdo e organização de arquivos. | arquivo-sass, arquivo, sass, documento, arquivos, mídia |
| arquivo-scss | Representa arquivo scss, útil para documentos, conteúdo e organização de arquivos. | arquivo-scss, arquivo, scss, documento, arquivos, mídia |
| arquivo-seta-baixo | Representa arquivo seta baixo, útil para documentos, conteúdo e organização de arquivos. | arquivo-seta-baixo, arquivo, seta, baixo, documento, arquivos, mídia |
| arquivo-seta-baixo-destaque | Representa arquivo seta baixo destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-seta-baixo-destaque, arquivo, seta, baixo, destaque, arquivos, mídia |
| arquivo-seta-cima | Representa arquivo seta cima, útil para documentos, conteúdo e organização de arquivos. | arquivo-seta-cima, arquivo, seta, cima, documento, arquivos, mídia |
| arquivo-seta-cima-destaque | Representa arquivo seta cima destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-seta-cima-destaque, arquivo, seta, cima, destaque, arquivos, mídia |
| arquivo-sh | Representa arquivo sh, útil para documentos, conteúdo e organização de arquivos. | arquivo-sh, arquivo, documento, sh, arquivos, mídia |
| arquivo-slides | Representa arquivo slides, útil para documentos, conteúdo e organização de arquivos. | arquivo-slides, arquivo, slides, documento, arquivos, mídia |
| arquivo-slides-destaque | Representa arquivo slides destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-slides-destaque, arquivo, slides, destaque, documento, arquivos, mídia |
| arquivo-spreadsheet | Representa arquivo spreadsheet, útil para documentos, conteúdo e organização de arquivos. | arquivo-spreadsheet, arquivo, spreadsheet, documento, arquivos, mídia |
| arquivo-spreadsheet-destaque | Representa arquivo spreadsheet destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-spreadsheet-destaque, arquivo, spreadsheet, destaque, documento, arquivos, mídia |
| arquivo-sql | Representa arquivo sql, útil para documentos, conteúdo e organização de arquivos. | arquivo-sql, arquivo, sql, documento, arquivos, mídia |
| arquivo-svg | Representa arquivo svg, útil para documentos, conteúdo e organização de arquivos. | arquivo-svg, arquivo, svg, documento, arquivos, mídia |
| arquivo-texto | Arquivo textual simples, anotação ou conteúdo descritivo. | arquivo-texto, arquivo, texto, documento, textual, arquivos, mídia |
| arquivo-texto-destaque | Representa arquivo texto destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-texto-destaque, arquivo, texto, destaque, documento, arquivos, mídia |
| arquivo-tiff | Representa arquivo tiff, útil para documentos, conteúdo e organização de arquivos. | arquivo-tiff, arquivo, tiff, documento, arquivos, mídia |
| arquivo-tsx | Representa arquivo tsx, útil para documentos, conteúdo e organização de arquivos. | arquivo-tsx, arquivo, tsx, documento, arquivos, mídia |
| arquivo-ttf | Representa arquivo ttf, útil para documentos, conteúdo e organização de arquivos. | arquivo-ttf, arquivo, ttf, documento, arquivos, mídia |
| arquivo-txt | Representa arquivo txt, útil para documentos, conteúdo e organização de arquivos. | arquivo-txt, arquivo, txt, documento, arquivos, mídia |
| arquivo-wav | Representa arquivo wav, útil para documentos, conteúdo e organização de arquivos. | arquivo-wav, arquivo, wav, documento, arquivos, mídia |
| arquivo-woff | Representa arquivo woff, útil para documentos, conteúdo e organização de arquivos. | arquivo-woff, arquivo, woff, documento, arquivos, mídia |
| arquivo-word | Representa arquivo word, útil para documentos, conteúdo e organização de arquivos. | arquivo-word, arquivo, word, documento, arquivos, mídia |
| arquivo-word-destaque | Representa arquivo word destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-word-destaque, arquivo, word, destaque, documento, arquivos, mídia |
| arquivo-xls | Representa arquivo xls, útil para documentos, conteúdo e organização de arquivos. | arquivo-xls, arquivo, xls, documento, arquivos, mídia |
| arquivo-xml | Representa arquivo xml, útil para documentos, conteúdo e organização de arquivos. | arquivo-xml, arquivo, xml, documento, arquivos, mídia |
| arquivo-yml | Representa arquivo yml, útil para documentos, conteúdo e organização de arquivos. | arquivo-yml, arquivo, yml, documento, arquivos, mídia |
| arquivo-zip | Representa arquivo zip, útil para documentos, conteúdo e organização de arquivos. | arquivo-zip, arquivo, zip, documento, arquivos, mídia |
| arquivo-zip-destaque | Representa arquivo zip destaque, útil para documentos, conteúdo e organização de arquivos. | arquivo-zip-destaque, arquivo, zip, destaque, documento, arquivos, mídia |
| arquivos | Representa arquivos, útil para configuração, integrações e recursos digitais. | arquivos, sistema, infraestrutura |
| arquivos-alternativo | Representa arquivos alternativo, útil para configuração, integrações e recursos digitais. | arquivos-alternativo, arquivos, alternativo, sistema, infraestrutura |
| arrastar | Arrastar, reordenar ou manipular elementos verticalmente. | arrastar, acao, comando, reordenar, manipular, ações |
| arrastar-horizontal | Representa arrastar horizontal, útil para configuração, integrações e recursos digitais. | arrastar-horizontal, arrastar, horizontal, sistema, infraestrutura |
| arrows | Representa arrows, útil para configuração, integrações e recursos digitais. | arrows, sistema, infraestrutura |
| arrows-angle-contract | Representa arrows angle contract, útil para configuração, integrações e recursos digitais. | arrows-angle-contract, arrows, angle, contract, sistema, infraestrutura |
| arrows-angle-expand | Representa arrows angle expand, útil para configuração, integrações e recursos digitais. | arrows-angle-expand, arrows, angle, expand, sistema, infraestrutura |
| arrows-collapse | Representa arrows collapse, útil para configuração, integrações e recursos digitais. | arrows-collapse, arrows, collapse, sistema, infraestrutura |
| arrows-collapse-vertical | Representa arrows collapse vertical, útil para configuração, integrações e recursos digitais. | arrows-collapse-vertical, arrows, collapse, vertical, sistema, infraestrutura |
| arrows-expand | Representa arrows expand, útil para configuração, integrações e recursos digitais. | arrows-expand, arrows, expand, sistema, infraestrutura |
| arrows-expand-vertical | Representa arrows expand vertical, útil para configuração, integrações e recursos digitais. | arrows-expand-vertical, arrows, expand, vertical, sistema, infraestrutura |
| arrows-move | Representa arrows move, útil para configuração, integrações e recursos digitais. | arrows-move, arrows, move, sistema, infraestrutura |
| arrows-tela-cheia | Representa arrows tela cheia, útil para configuração, integrações e recursos digitais. | arrows-tela-cheia, arrows, tela, cheia, sistema, infraestrutura |
| arrows-vertical | Representa arrows vertical, útil para configuração, integrações e recursos digitais. | arrows-vertical, arrows, vertical, sistema, infraestrutura |
| artigo | Artigo, post, conteúdo editorial ou texto longo. | artigo, arquivo, documento, post, editorial, arquivos, mídia |
| arvore | Representa arvore, útil para configuração, integrações e recursos digitais. | arvore, sistema, infraestrutura |
| arvore-destaque | Representa arvore destaque, útil para configuração, integrações e recursos digitais. | arvore-destaque, arvore, destaque, sistema, infraestrutura |
| aspect-ratio | Representa aspect ratio, útil para configuração, integrações e recursos digitais. | aspect-ratio, aspect, ratio, sistema, infraestrutura |
| aspect-ratio-destaque | Representa aspect ratio destaque, útil para configuração, integrações e recursos digitais. | aspect-ratio-destaque, aspect, ratio, destaque, sistema, infraestrutura |
| asterisk | Representa asterisk, útil para configuração, integrações e recursos digitais. | asterisk, sistema, infraestrutura |
| at | Representa at, útil para configuração, integrações e recursos digitais. | at, sistema, infraestrutura |
| atividade | Indicador de atividade, status vivo ou movimento operacional. | atividade, status, estado, indicador, vivo, estados |
| avaliacao | Avaliação parcial, nota intermediaria ou destaque moderado. | avaliacao, status, estado, parcial, nota, avaliação, estados |
| avancar | Representa avancar, útil para navegação, direção e fluxo de interface. | avancar, navegacao, fluxo, navegação |
| avancar-circulo | Avanço principal, CTA de continuidade ou acesso rápido. | avancar-circulo, avancar, circulo, navegacao, fluxo, avançar, círculo, navegação |
| avancar-destaque | Representa avancar destaque, útil para navegação, direção e fluxo de interface. | avancar-destaque, avancar, destaque, navegacao, fluxo, navegação |
| avatar | Avatar, conta pessoal ou representação circular de usuário. | avatar, usuario, acesso, conta, pessoal, usuários |
| aviao | Representa aviao, útil para configuração, integrações e recursos digitais. | aviao, sistema, infraestrutura |
| aviao-destaque | Representa aviao destaque, útil para configuração, integrações e recursos digitais. | aviao-destaque, aviao, destaque, sistema, infraestrutura |
| aviao-motores | Representa aviao motores, útil para configuração, integrações e recursos digitais. | aviao-motores, aviao, motores, sistema, infraestrutura |
| aviao-motores-destaque | Representa aviao motores destaque, útil para configuração, integrações e recursos digitais. | aviao-motores-destaque, aviao, motores, destaque, sistema, infraestrutura |
| aviso | Aviso, risco ou pendencia que requer atenção. | aviso, status, estado, risco, pendencia, estados |
| aviso-destaque | Aviso crítico com maior peso visual. | aviso-destaque, aviso, destaque, status, estado, estados |
| award-destaque | Representa award destaque, útil para configuração, integrações e recursos digitais. | award-destaque, award, destaque, sistema, infraestrutura |
| backpack | Representa backpack, útil para configuração, integrações e recursos digitais. | backpack, sistema, infraestrutura |
| backpack-destaque | Representa backpack destaque, útil para configuração, integrações e recursos digitais. | backpack-destaque, backpack, destaque, sistema, infraestrutura |
| backpack2 | Representa backpack2, útil para configuração, integrações e recursos digitais. | backpack2, sistema, infraestrutura |
| backpack2-destaque | Representa backpack2 destaque, útil para configuração, integrações e recursos digitais. | backpack2-destaque, backpack2, destaque, sistema, infraestrutura |
| backpack3 | Representa backpack3, útil para configuração, integrações e recursos digitais. | backpack3, sistema, infraestrutura |
| backpack3-destaque | Representa backpack3 destaque, útil para configuração, integrações e recursos digitais. | backpack3-destaque, backpack3, destaque, sistema, infraestrutura |
| backpack4 | Representa backpack4, útil para configuração, integrações e recursos digitais. | backpack4, sistema, infraestrutura |
| backpack4-destaque | Representa backpack4 destaque, útil para configuração, integrações e recursos digitais. | backpack4-destaque, backpack4, destaque, sistema, infraestrutura |
| backspace | Representa backspace, útil para configuração, integrações e recursos digitais. | backspace, sistema, infraestrutura |
| backspace-destaque | Representa backspace destaque, útil para configuração, integrações e recursos digitais. | backspace-destaque, backspace, destaque, sistema, infraestrutura |
| backspace-reverse | Representa backspace reverse, útil para configuração, integrações e recursos digitais. | backspace-reverse, backspace, reverse, sistema, infraestrutura |
| backspace-reverse-destaque | Representa backspace reverse destaque, útil para configuração, integrações e recursos digitais. | backspace-reverse-destaque, backspace, reverse, destaque, sistema, infraestrutura |
| bagagem | Representa bagagem, útil para configuração, integrações e recursos digitais. | bagagem, sistema, infraestrutura |
| bagagem-destaque | Representa bagagem destaque, útil para configuração, integrações e recursos digitais. | bagagem-destaque, bagagem, destaque, sistema, infraestrutura |
| baixar | Baixar arquivo, exportar dado ou recuperar recurso. | baixar, acao, comando, arquivo, exportar, ações |
| baixar-circulo | Download destacado em ação circular. | baixar-circulo, baixar, circulo, acao, comando, círculo, ações |
| balde | Representa balde, útil para configuração, integrações e recursos digitais. | balde, sistema, infraestrutura |
| balde-destaque | Representa balde destaque, útil para configuração, integrações e recursos digitais. | balde-destaque, balde, destaque, sistema, infraestrutura |
| balloon | Representa balloon, útil para configuração, integrações e recursos digitais. | balloon, sistema, infraestrutura |
| balloon-coracao | Representa balloon coracao, útil para configuração, integrações e recursos digitais. | balloon-coracao, balloon, coracao, sistema, infraestrutura |
| balloon-coracao-destaque | Representa balloon coracao destaque, útil para configuração, integrações e recursos digitais. | balloon-coracao-destaque, balloon, coracao, destaque, sistema, infraestrutura |
| balloon-destaque | Representa balloon destaque, útil para configuração, integrações e recursos digitais. | balloon-destaque, balloon, destaque, sistema, infraestrutura |
| ban | Representa ban, útil para configuração, integrações e recursos digitais. | ban, sistema, infraestrutura |
| ban-destaque | Representa ban destaque, útil para configuração, integrações e recursos digitais. | ban-destaque, ban, destaque, sistema, infraestrutura |
| banco-dados | Representa banco dados, útil para métricas, indicadores e leitura de dados. | banco-dados, banco, dados, analise, análise |
| banco-dados-add | Representa banco dados add, útil para métricas, indicadores e leitura de dados. | banco-dados-add, banco, dados, add, analise, análise |
| banco-dados-baixo | Representa banco dados baixo, útil para navegação, direção e fluxo de interface. | banco-dados-baixo, banco, dados, baixo, navegacao, navegação |
| banco-dados-cadeado | Representa banco dados cadeado, útil para segurança, controle de acesso e confiança operacional. | banco-dados-cadeado, banco, dados, cadeado, seguranca, segurança, permissões |
| banco-dados-cima | Representa banco dados cima, útil para navegação, direção e fluxo de interface. | banco-dados-cima, banco, dados, cima, navegacao, navegação |
| banco-dados-confirmado | Representa banco dados confirmado, útil para feedback visual, status e comunicação de estado. | banco-dados-confirmado, banco, dados, confirmado, status, estados |
| banco-dados-cortado | Representa banco dados cortado, útil para métricas, indicadores e leitura de dados. | banco-dados-cortado, banco, dados, cortado, analise, análise |
| banco-dados-destaque | Representa banco dados destaque, útil para métricas, indicadores e leitura de dados. | banco-dados-destaque, banco, dados, destaque, analise, análise |
| banco-dados-destaque-add | Representa banco dados destaque add, útil para métricas, indicadores e leitura de dados. | banco-dados-destaque-add, banco, dados, destaque, add, análise |
| banco-dados-destaque-baixo | Representa banco dados destaque baixo, útil para navegação, direção e fluxo de interface. | banco-dados-destaque-baixo, banco, dados, destaque, baixo, navegação |
| banco-dados-destaque-cadeado | Representa banco dados destaque cadeado, útil para segurança, controle de acesso e confiança operacional. | banco-dados-destaque-cadeado, banco, dados, destaque, cadeado, segurança, permissões |
| banco-dados-destaque-cima | Representa banco dados destaque cima, útil para navegação, direção e fluxo de interface. | banco-dados-destaque-cima, banco, dados, destaque, cima, navegação |
| banco-dados-destaque-confirmado | Representa banco dados destaque confirmado, útil para feedback visual, status e comunicação de estado. | banco-dados-destaque-confirmado, banco, dados, destaque, confirmado, estados |
| banco-dados-destaque-cortado | Representa banco dados destaque cortado, útil para métricas, indicadores e leitura de dados. | banco-dados-destaque-cortado, banco, dados, destaque, cortado, análise |
| banco-dados-destaque-engrenagem | Representa banco dados destaque engrenagem, útil para métricas, indicadores e leitura de dados. | banco-dados-destaque-engrenagem, banco, dados, destaque, engrenagem, análise |
| banco-dados-destaque-exclamacao | Representa banco dados destaque exclamacao, útil para métricas, indicadores e leitura de dados. | banco-dados-destaque-exclamacao, banco, dados, destaque, exclamacao, análise |
| banco-dados-destaque-menos | Representa banco dados destaque menos, útil para métricas, indicadores e leitura de dados. | banco-dados-destaque-menos, banco, dados, destaque, menos, análise |
| banco-dados-destaque-remover | Representa banco dados destaque remover, útil para ações, comandos e interações diretas na interface. | banco-dados-destaque-remover, banco, dados, destaque, remover, ações |
| banco-dados-engrenagem | Representa banco dados engrenagem, útil para métricas, indicadores e leitura de dados. | banco-dados-engrenagem, banco, dados, engrenagem, analise, análise |
| banco-dados-exclamacao | Representa banco dados exclamacao, útil para métricas, indicadores e leitura de dados. | banco-dados-exclamacao, banco, dados, exclamacao, analise, análise |
| banco-dados-menos | Representa banco dados menos, útil para métricas, indicadores e leitura de dados. | banco-dados-menos, banco, dados, menos, analise, análise |
| banco-dados-remover | Representa banco dados remover, útil para ações, comandos e interações diretas na interface. | banco-dados-remover, banco, dados, remover, acao, ações |
| bandaid | Representa bandaid, útil para configuração, integrações e recursos digitais. | bandaid, sistema, infraestrutura |
| bandaid-destaque | Representa bandaid destaque, útil para configuração, integrações e recursos digitais. | bandaid-destaque, bandaid, destaque, sistema, infraestrutura |
| bandeira | Representa bandeira, útil para configuração, integrações e recursos digitais. | bandeira, sistema, infraestrutura |
| bandeira-destaque | Representa bandeira destaque, útil para configuração, integrações e recursos digitais. | bandeira-destaque, bandeira, destaque, sistema, infraestrutura |
| bank | Representa bank, útil para configuração, integrações e recursos digitais. | bank, sistema, infraestrutura |
| bank2 | Representa bank2, útil para configuração, integrações e recursos digitais. | bank2, sistema, infraestrutura |
| barra-chart | Representa barra chart, útil para métricas, indicadores e leitura de dados. | barra-chart, barra, chart, dados, analise, análise |
| barra-chart-destaque | Representa barra chart destaque, útil para métricas, indicadores e leitura de dados. | barra-chart-destaque, barra, chart, destaque, dados, análise |
| barra-chart-linha-destaque | Representa barra chart linha destaque, útil para métricas, indicadores e leitura de dados. | barra-chart-linha-destaque, barra, chart, linha, destaque, dados, análise |
| barra-chart-steps | Representa barra chart steps, útil para métricas, indicadores e leitura de dados. | barra-chart-steps, barra, chart, steps, dados, análise |
| basket2 | Representa basket2, útil para configuração, integrações e recursos digitais. | basket2, sistema, infraestrutura |
| basket2-destaque | Representa basket2 destaque, útil para configuração, integrações e recursos digitais. | basket2-destaque, basket2, destaque, sistema, infraestrutura |
| basket3 | Representa basket3, útil para configuração, integrações e recursos digitais. | basket3, sistema, infraestrutura |
| basket3-destaque | Representa basket3 destaque, útil para configuração, integrações e recursos digitais. | basket3-destaque, basket3, destaque, sistema, infraestrutura |
| bateria | Representa bateria, útil para configuração, integrações e recursos digitais. | bateria, sistema, infraestrutura |
| bateria-baixa | Representa bateria baixa, útil para configuração, integrações e recursos digitais. | bateria-baixa, bateria, baixa, sistema, infraestrutura |
| bateria-carregando | Representa bateria carregando, útil para configuração, integrações e recursos digitais. | bateria-carregando, bateria, carregando, sistema, infraestrutura |
| bateria-cheia | Representa bateria cheia, útil para configuração, integrações e recursos digitais. | bateria-cheia, bateria, cheia, sistema, infraestrutura |
| bateria-metade | Representa bateria metade, útil para configuração, integrações e recursos digitais. | bateria-metade, bateria, metade, sistema, infraestrutura |
| behance | Representa behance, útil para configuração, integrações e recursos digitais. | behance, sistema, infraestrutura |
| bequer | Representa bequer, útil para configuração, integrações e recursos digitais. | bequer, sistema, infraestrutura |
| bequer-destaque | Representa bequer destaque, útil para configuração, integrações e recursos digitais. | bequer-destaque, bequer, destaque, sistema, infraestrutura |
| bezier | Representa bezier, útil para configuração, integrações e recursos digitais. | bezier, sistema, infraestrutura |
| bezier2 | Representa bezier2, útil para configuração, integrações e recursos digitais. | bezier2, sistema, infraestrutura |
| bicycle | Representa bicycle, útil para configuração, integrações e recursos digitais. | bicycle, sistema, infraestrutura |
| bing | Representa bing, útil para configuração, integrações e recursos digitais. | bing, sistema, infraestrutura |
| binoculars | Representa binoculars, útil para configuração, integrações e recursos digitais. | binoculars, sistema, infraestrutura |
| binoculars-destaque | Representa binoculars destaque, útil para configuração, integrações e recursos digitais. | binoculars-destaque, binoculars, destaque, sistema, infraestrutura |
| bloqueio | Bloqueio, restrição, privacidade ou controle de acesso. | bloqueio, seguranca, permissao, restricao, privacidade, segurança, permissões |
| bluesky | Representa bluesky, útil para configuração, integrações e recursos digitais. | bluesky, sistema, infraestrutura |
| bluetooth | Representa bluetooth, útil para configuração, integrações e recursos digitais. | bluetooth, sistema, infraestrutura |
| bolsa | Representa bolsa, útil para configuração, integrações e recursos digitais. | bolsa, sistema, infraestrutura |
| bolsa-destaque | Representa bolsa destaque, útil para configuração, integrações e recursos digitais. | bolsa-destaque, bolsa, destaque, sistema, infraestrutura |
| bookmarks | Representa bookmarks, útil para configuração, integrações e recursos digitais. | bookmarks, sistema, infraestrutura |
| bookmarks-destaque | Representa bookmarks destaque, útil para configuração, integrações e recursos digitais. | bookmarks-destaque, bookmarks, destaque, sistema, infraestrutura |
| bookshelf | Representa bookshelf, útil para configuração, integrações e recursos digitais. | bookshelf, sistema, infraestrutura |
| boombox | Representa boombox, útil para configuração, integrações e recursos digitais. | boombox, sistema, infraestrutura |
| boombox-destaque | Representa boombox destaque, útil para configuração, integrações e recursos digitais. | boombox-destaque, boombox, destaque, sistema, infraestrutura |
| framework-base | Representa marca de framework, útil para identidade visual, integrações e contexto digital. | framework, marca, identidade, integracoes, digital |
| framework-base-destaque | Representa marca de framework em destaque, útil para identidade visual, integrações e contexto digital. | framework, marca, destaque, identidade, integracoes |
| framework-reinicio | Representa marca de framework em reinicio visual, útil para identidade, integrações e contexto digital. | framework, reinicio, marca, identidade, integracoes |
| borda | Representa borda, útil para configuração, integrações e recursos digitais. | borda, sistema, infraestrutura |
| borda-all | Representa borda all, útil para configuração, integrações e recursos digitais. | borda-all, borda, all, sistema, infraestrutura |
| borda-base | Representa borda base, útil para configuração, integrações e recursos digitais. | borda-base, borda, base, sistema, infraestrutura |
| borda-centro | Representa borda centro, útil para configuração, integrações e recursos digitais. | borda-centro, borda, centro, sistema, infraestrutura |
| borda-direita | Representa borda direita, útil para navegação, direção e fluxo de interface. | borda-direita, borda, direita, navegacao, fluxo, navegação |
| borda-esquerda | Representa borda esquerda, útil para navegação, direção e fluxo de interface. | borda-esquerda, borda, esquerda, navegacao, fluxo, navegação |
| borda-inner | Representa borda inner, útil para configuração, integrações e recursos digitais. | borda-inner, borda, inner, sistema, infraestrutura |
| borda-meio | Representa borda meio, útil para configuração, integrações e recursos digitais. | borda-meio, borda, meio, sistema, infraestrutura |
| borda-outer | Representa borda outer, útil para configuração, integrações e recursos digitais. | borda-outer, borda, outer, sistema, infraestrutura |
| borda-style | Representa borda style, útil para configuração, integrações e recursos digitais. | borda-style, borda, style, sistema, infraestrutura |
| borda-topo | Representa borda topo, útil para configuração, integrações e recursos digitais. | borda-topo, borda, topo, sistema, infraestrutura |
| borda-width | Representa borda width, útil para configuração, integrações e recursos digitais. | borda-width, borda, width, sistema, infraestrutura |
| borracha | Representa borracha, útil para configuração, integrações e recursos digitais. | borracha, sistema, infraestrutura |
| borracha-destaque | Representa borracha destaque, útil para configuração, integrações e recursos digitais. | borracha-destaque, borracha, destaque, sistema, infraestrutura |
| bounding-caixa | Representa bounding caixa, útil para operação, movimentação e contexto logístico. | bounding-caixa, bounding, caixa, logistica, operacao, logística, operações |
| bounding-caixa-circles | Representa bounding caixa circles, útil para operação, movimentação e contexto logístico. | bounding-caixa-circles, bounding, caixa, circles, logistica, logística, operações |
| box2 | Representa box2, útil para configuração, integrações e recursos digitais. | box2, sistema, infraestrutura |
| box2-coracao | Representa box2 coracao, útil para configuração, integrações e recursos digitais. | box2-coracao, box2, coracao, sistema, infraestrutura |
| box2-coracao-destaque | Representa box2 coracao destaque, útil para configuração, integrações e recursos digitais. | box2-coracao-destaque, box2, coracao, destaque, sistema, infraestrutura |
| box2-destaque | Representa box2 destaque, útil para configuração, integrações e recursos digitais. | box2-destaque, box2, destaque, sistema, infraestrutura |
| braces | Representa braces, útil para configuração, integrações e recursos digitais. | braces, sistema, infraestrutura |
| braces-asterisk | Representa braces asterisk, útil para configuração, integrações e recursos digitais. | braces-asterisk, braces, asterisk, sistema, infraestrutura |
| bricks | Representa bricks, útil para configuração, integrações e recursos digitais. | bricks, sistema, infraestrutura |
| brilho-alternativo-high | Representa brilho alternativo high, útil para configuração, integrações e recursos digitais. | brilho-alternativo-high, brilho, alternativo, high, sistema, infraestrutura |
| brilho-alternativo-high-destaque | Representa brilho alternativo high destaque, útil para configuração, integrações e recursos digitais. | brilho-alternativo-high-destaque, brilho, alternativo, high, destaque, sistema, infraestrutura |
| brilho-alternativo-low | Representa brilho alternativo low, útil para configuração, integrações e recursos digitais. | brilho-alternativo-low, brilho, alternativo, low, sistema, infraestrutura |
| brilho-alternativo-low-destaque | Representa brilho alternativo low destaque, útil para configuração, integrações e recursos digitais. | brilho-alternativo-low-destaque, brilho, alternativo, low, destaque, sistema, infraestrutura |
| brilho-high | Representa brilho high, útil para configuração, integrações e recursos digitais. | brilho-high, brilho, high, sistema, infraestrutura |
| brilho-high-destaque | Representa brilho high destaque, útil para configuração, integrações e recursos digitais. | brilho-high-destaque, brilho, high, destaque, sistema, infraestrutura |
| brilho-low | Representa brilho low, útil para configuração, integrações e recursos digitais. | brilho-low, brilho, low, sistema, infraestrutura |
| brilho-low-destaque | Representa brilho low destaque, útil para configuração, integrações e recursos digitais. | brilho-low-destaque, brilho, low, destaque, sistema, infraestrutura |
| brilliance | Representa brilliance, útil para configuração, integrações e recursos digitais. | brilliance, sistema, infraestrutura |
| bug | Representa bug, útil para configuração, integrações e recursos digitais. | bug, sistema, infraestrutura |
| bug-destaque | Representa bug destaque, útil para configuração, integrações e recursos digitais. | bug-destaque, bug, destaque, sistema, infraestrutura |
| buildings | Representa buildings, útil para configuração, integrações e recursos digitais. | buildings, sistema, infraestrutura |
| buildings-destaque | Representa buildings destaque, útil para configuração, integrações e recursos digitais. | buildings-destaque, buildings, destaque, sistema, infraestrutura |
| buscar | Busca, consulta, localizar ou filtrar por termo. | buscar, acao, comando, busca, consulta, ações |
| buscar-coracao | Representa buscar coracao, útil para ações, comandos e interações diretas na interface. | buscar-coracao, buscar, coracao, acao, comando, ações |
| buscar-coracao-destaque | Representa buscar coracao destaque, útil para ações, comandos e interações diretas na interface. | buscar-coracao-destaque, buscar, coracao, destaque, acao, ações |
| bussola | Representa bussola, útil para configuração, integrações e recursos digitais. | bussola, sistema, infraestrutura |
| bussola-destaque | Representa bussola destaque, útil para configuração, integrações e recursos digitais. | bussola-destaque, bussola, destaque, sistema, infraestrutura |
| cadeado-destaque | Representa cadeado destaque, útil para segurança, controle de acesso e confiança operacional. | cadeado-destaque, cadeado, destaque, seguranca, permissao, segurança, permissões |
| caixa | Pacote, entrega, estoque embalado ou item logístico. | caixa, logistica, operacao, pacote, entrega, logística, operações |
| caixa-correio | Representa caixa correio, útil para operação, movimentação e contexto logístico. | caixa-correio, caixa, correio, logistica, operacao, logística, operações |
| caixa-correio-bandeira | Representa caixa correio bandeira, útil para operação, movimentação e contexto logístico. | caixa-correio-bandeira, caixa, correio, bandeira, logistica, logística, operações |
| caixa-destaque | Representa caixa destaque, útil para operação, movimentação e contexto logístico. | caixa-destaque, caixa, destaque, logistica, operacao, logística, operações |
| caixa-entrada | Caixa de entrada, recebidos ou fila interna. | caixa-entrada, caixa, entrada, sistema, infraestrutura |
| caixa-icon | Representa caixa icon, útil para operação, movimentação e contexto logístico. | caixa-icon, caixa, icon, logistica, operacao, logística, operações |
| caixa-seam-destaque | Representa caixa seam destaque, útil para operação, movimentação e contexto logístico. | caixa-seam-destaque, caixa, seam, destaque, logistica, logística, operações |
| caixa-seta-baixo | Representa caixa seta baixo, útil para navegação, direção e fluxo de interface. | caixa-seta-baixo, caixa, seta, baixo, navegacao, navegação |
| caixa-seta-baixo-direita | Representa caixa seta baixo direita, útil para navegação, direção e fluxo de interface. | caixa-seta-baixo-direita, caixa, seta, baixo, direita, navegação |
| caixa-seta-baixo-esquerda | Representa caixa seta baixo esquerda, útil para navegação, direção e fluxo de interface. | caixa-seta-baixo-esquerda, caixa, seta, baixo, esquerda, navegação |
| caixa-seta-cima | Representa caixa seta cima, útil para navegação, direção e fluxo de interface. | caixa-seta-cima, caixa, seta, cima, navegacao, navegação |
| caixa-seta-cima-direita | Representa caixa seta cima direita, útil para navegação, direção e fluxo de interface. | caixa-seta-cima-direita, caixa, seta, cima, direita, navegação |
| caixa-seta-cima-esquerda | Representa caixa seta cima esquerda, útil para navegação, direção e fluxo de interface. | caixa-seta-cima-esquerda, caixa, seta, cima, esquerda, navegação |
| caixa-seta-in-baixo | Representa caixa seta in baixo, útil para navegação, direção e fluxo de interface. | caixa-seta-in-baixo, caixa, seta, baixo, navegacao, in, navegação |
| caixa-seta-in-baixo-direita | Representa caixa seta in baixo direita, útil para navegação, direção e fluxo de interface. | caixa-seta-in-baixo-direita, caixa, seta, baixo, direita, in, navegação |
| caixa-seta-in-baixo-esquerda | Representa caixa seta in baixo esquerda, útil para navegação, direção e fluxo de interface. | caixa-seta-in-baixo-esquerda, caixa, seta, baixo, esquerda, in, navegação |
| caixa-seta-in-cima | Representa caixa seta in cima, útil para navegação, direção e fluxo de interface. | caixa-seta-in-cima, caixa, seta, cima, navegacao, in, navegação |
| caixa-seta-in-cima-direita | Representa caixa seta in cima direita, útil para navegação, direção e fluxo de interface. | caixa-seta-in-cima-direita, caixa, seta, cima, direita, in, navegação |
| caixa-seta-in-cima-esquerda | Representa caixa seta in cima esquerda, útil para navegação, direção e fluxo de interface. | caixa-seta-in-cima-esquerda, caixa, seta, cima, esquerda, in, navegação |
| caixa-seta-in-esquerda | Representa caixa seta in esquerda, útil para navegação, direção e fluxo de interface. | caixa-seta-in-esquerda, caixa, seta, esquerda, navegacao, in, navegação |
| caixa-voz | Representa caixa voz, útil para operação, movimentação e contexto logístico. | caixa-voz, caixa, voz, logistica, operacao, logística, operações |
| caixas | Representa caixas, útil para configuração, integrações e recursos digitais. | caixas, sistema, infraestrutura |
| cake | Representa cake, útil para configuração, integrações e recursos digitais. | cake, sistema, infraestrutura |
| cake-destaque | Representa cake destaque, útil para configuração, integrações e recursos digitais. | cake-destaque, cake, destaque, sistema, infraestrutura |
| cake2 | Representa cake2, útil para configuração, integrações e recursos digitais. | cake2, sistema, infraestrutura |
| cake2-destaque | Representa cake2 destaque, útil para configuração, integrações e recursos digitais. | cake2-destaque, cake2, destaque, sistema, infraestrutura |
| calculadora | Representa calculadora, útil para configuração, integrações e recursos digitais. | calculadora, sistema, infraestrutura |
| calculadora-destaque | Representa calculadora destaque, útil para configuração, integrações e recursos digitais. | calculadora-destaque, calculadora, destaque, sistema, infraestrutura |
| calendar2 | Representa calendar2, útil para configuração, integrações e recursos digitais. | calendar2, sistema, infraestrutura |
| calendar2-adicionar | Representa calendar2 adicionar, útil para ações, comandos e interações diretas na interface. | calendar2-adicionar, calendar2, adicionar, acao, comando, ações |
| calendar2-adicionar-destaque | Representa calendar2 adicionar destaque, útil para ações, comandos e interações diretas na interface. | calendar2-adicionar-destaque, calendar2, adicionar, destaque, acao, ações |
| calendar2-confirmado | Representa calendar2 confirmado, útil para feedback visual, status e comunicação de estado. | calendar2-confirmado, calendar2, confirmado, status, estado, estados |
| calendar2-confirmado-destaque | Representa calendar2 confirmado destaque, útil para feedback visual, status e comunicação de estado. | calendar2-confirmado-destaque, calendar2, confirmado, destaque, status, estados |
| calendar2-coracao | Representa calendar2 coracao, útil para configuração, integrações e recursos digitais. | calendar2-coracao, calendar2, coracao, sistema, infraestrutura |
| calendar2-coracao-destaque | Representa calendar2 coracao destaque, útil para configuração, integrações e recursos digitais. | calendar2-coracao-destaque, calendar2, coracao, destaque, sistema, infraestrutura |
| calendar2-date | Representa calendar2 date, útil para configuração, integrações e recursos digitais. | calendar2-date, calendar2, date, sistema, infraestrutura |
| calendar2-date-destaque | Representa calendar2 date destaque, útil para configuração, integrações e recursos digitais. | calendar2-date-destaque, calendar2, date, destaque, sistema, infraestrutura |
| calendar2-day | Representa calendar2 day, útil para configuração, integrações e recursos digitais. | calendar2-day, calendar2, day, sistema, infraestrutura |
| calendar2-day-destaque | Representa calendar2 day destaque, útil para configuração, integrações e recursos digitais. | calendar2-day-destaque, calendar2, day, destaque, sistema, infraestrutura |
| calendar2-destaque | Representa calendar2 destaque, útil para configuração, integrações e recursos digitais. | calendar2-destaque, calendar2, destaque, sistema, infraestrutura |
| calendar2-event | Representa calendar2 event, útil para configuração, integrações e recursos digitais. | calendar2-event, calendar2, event, sistema, infraestrutura |
| calendar2-event-destaque | Representa calendar2 event destaque, útil para configuração, integrações e recursos digitais. | calendar2-event-destaque, calendar2, event, destaque, sistema, infraestrutura |
| calendar2-minus | Representa calendar2 minus, útil para configuração, integrações e recursos digitais. | calendar2-minus, calendar2, minus, sistema, infraestrutura |
| calendar2-minus-destaque | Representa calendar2 minus destaque, útil para configuração, integrações e recursos digitais. | calendar2-minus-destaque, calendar2, minus, destaque, sistema, infraestrutura |
| calendar2-month | Representa calendar2 month, útil para configuração, integrações e recursos digitais. | calendar2-month, calendar2, month, sistema, infraestrutura |
| calendar2-month-destaque | Representa calendar2 month destaque, útil para configuração, integrações e recursos digitais. | calendar2-month-destaque, calendar2, month, destaque, sistema, infraestrutura |
| calendar2-range | Representa calendar2 range, útil para configuração, integrações e recursos digitais. | calendar2-range, calendar2, range, sistema, infraestrutura |
| calendar2-range-destaque | Representa calendar2 range destaque, útil para configuração, integrações e recursos digitais. | calendar2-range-destaque, calendar2, range, destaque, sistema, infraestrutura |
| calendar2-remover | Representa calendar2 remover, útil para ações, comandos e interações diretas na interface. | calendar2-remover, calendar2, remover, acao, comando, ações |
| calendar2-remover-destaque | Representa calendar2 remover destaque, útil para ações, comandos e interações diretas na interface. | calendar2-remover-destaque, calendar2, remover, destaque, acao, ações |
| calendar2-week | Representa calendar2 week, útil para configuração, integrações e recursos digitais. | calendar2-week, calendar2, week, sistema, infraestrutura |
| calendar2-week-destaque | Representa calendar2 week destaque, útil para configuração, integrações e recursos digitais. | calendar2-week-destaque, calendar2, week, destaque, sistema, infraestrutura |
| calendar3-destaque | Representa calendar3 destaque, útil para configuração, integrações e recursos digitais. | calendar3-destaque, calendar3, destaque, sistema, infraestrutura |
| calendar3-event | Representa calendar3 event, útil para configuração, integrações e recursos digitais. | calendar3-event, calendar3, event, sistema, infraestrutura |
| calendar3-event-destaque | Representa calendar3 event destaque, útil para configuração, integrações e recursos digitais. | calendar3-event-destaque, calendar3, event, destaque, sistema, infraestrutura |
| calendar3-range | Representa calendar3 range, útil para configuração, integrações e recursos digitais. | calendar3-range, calendar3, range, sistema, infraestrutura |
| calendar3-range-destaque | Representa calendar3 range destaque, útil para configuração, integrações e recursos digitais. | calendar3-range-destaque, calendar3, range, destaque, sistema, infraestrutura |
| calendar3-week | Representa calendar3 week, útil para configuração, integrações e recursos digitais. | calendar3-week, calendar3, week, sistema, infraestrutura |
| calendar3-week-destaque | Representa calendar3 week destaque, útil para configuração, integrações e recursos digitais. | calendar3-week-destaque, calendar3, week, destaque, sistema, infraestrutura |
| calendar4 | Representa calendar4, útil para configuração, integrações e recursos digitais. | calendar4, sistema, infraestrutura |
| calendar4-event | Representa calendar4 event, útil para configuração, integrações e recursos digitais. | calendar4-event, calendar4, event, sistema, infraestrutura |
| calendar4-range | Representa calendar4 range, útil para configuração, integrações e recursos digitais. | calendar4-range, calendar4, range, sistema, infraestrutura |
| calendar4-week | Representa calendar4 week, útil para configuração, integrações e recursos digitais. | calendar4-week, calendar4, week, sistema, infraestrutura |
| calendario | Visão geral de calendário, agenda mensal ou datas. | calendario, agenda, tempo, geral, mensal, calendário, agendamento |
| calendario-adicionar | Representa calendario adicionar, útil para ações, comandos e interações diretas na interface. | calendario-adicionar, calendario, adicionar, acao, comando, ações |
| calendario-adicionar-destaque | Representa calendario adicionar destaque, útil para ações, comandos e interações diretas na interface. | calendario-adicionar-destaque, calendario, adicionar, destaque, acao, ações |
| calendario-confirmado-destaque | Representa calendario confirmado destaque, útil para feedback visual, status e comunicação de estado. | calendario-confirmado-destaque, calendario, confirmado, destaque, status, estados |
| calendario-coracao | Representa calendario coracao, útil para tempo, agenda e acompanhamento de prazos. | calendario-coracao, calendario, coracao, agenda, tempo, agendamento |
| calendario-coracao-destaque | Representa calendario coracao destaque, útil para tempo, agenda e acompanhamento de prazos. | calendario-coracao-destaque, calendario, coracao, destaque, agenda, tempo, agendamento |
| calendario-date | Representa calendario date, útil para tempo, agenda e acompanhamento de prazos. | calendario-date, calendario, date, agenda, tempo, agendamento |
| calendario-date-destaque | Representa calendario date destaque, útil para tempo, agenda e acompanhamento de prazos. | calendario-date-destaque, calendario, date, destaque, agenda, tempo, agendamento |
| calendario-day | Representa calendario day, útil para tempo, agenda e acompanhamento de prazos. | calendario-day, calendario, day, agenda, tempo, agendamento |
| calendario-day-destaque | Representa calendario day destaque, útil para tempo, agenda e acompanhamento de prazos. | calendario-day-destaque, calendario, day, destaque, agenda, tempo, agendamento |
| calendario-destaque | Representa calendario destaque, útil para tempo, agenda e acompanhamento de prazos. | calendario-destaque, calendario, destaque, agenda, tempo, agendamento |
| calendario-event-destaque | Representa calendario event destaque, útil para tempo, agenda e acompanhamento de prazos. | calendario-event-destaque, calendario, event, destaque, agenda, tempo, agendamento |
| calendario-icon | Representa calendario icon, útil para tempo, agenda e acompanhamento de prazos. | calendario-icon, calendario, icon, agenda, tempo, agendamento |
| calendario-minus | Representa calendario minus, útil para tempo, agenda e acompanhamento de prazos. | calendario-minus, calendario, minus, agenda, tempo, agendamento |
| calendario-minus-destaque | Representa calendario minus destaque, útil para tempo, agenda e acompanhamento de prazos. | calendario-minus-destaque, calendario, minus, destaque, agenda, tempo, agendamento |
| calendario-month | Representa calendario month, útil para tempo, agenda e acompanhamento de prazos. | calendario-month, calendario, month, agenda, tempo, agendamento |
| calendario-month-destaque | Representa calendario month destaque, útil para tempo, agenda e acompanhamento de prazos. | calendario-month-destaque, calendario, month, destaque, agenda, tempo, agendamento |
| calendario-range | Representa calendario range, útil para tempo, agenda e acompanhamento de prazos. | calendario-range, calendario, range, agenda, tempo, agendamento |
| calendario-range-destaque | Representa calendario range destaque, útil para tempo, agenda e acompanhamento de prazos. | calendario-range-destaque, calendario, range, destaque, agenda, tempo, agendamento |
| calendario-remover | Representa calendario remover, útil para ações, comandos e interações diretas na interface. | calendario-remover, calendario, remover, acao, comando, ações |
| calendario-remover-destaque | Representa calendario remover destaque, útil para ações, comandos e interações diretas na interface. | calendario-remover-destaque, calendario, remover, destaque, acao, ações |
| calendario-week | Representa calendario week, útil para tempo, agenda e acompanhamento de prazos. | calendario-week, calendario, week, agenda, tempo, agendamento |
| calendario-week-destaque | Representa calendario week destaque, útil para tempo, agenda e acompanhamento de prazos. | calendario-week-destaque, calendario, week, destaque, agenda, tempo, agendamento |
| camada-avancar | Representa camada avancar, útil para navegação, direção e fluxo de interface. | camada-avancar, camada, avancar, navegacao, fluxo, navegação |
| camada-backward | Representa camada backward, útil para configuração, integrações e recursos digitais. | camada-backward, camada, backward, sistema, infraestrutura |
| camadas | Representa camadas, útil para configuração, integrações e recursos digitais. | camadas, sistema, infraestrutura |
| camadas-destaque | Representa camadas destaque, útil para configuração, integrações e recursos digitais. | camadas-destaque, camadas, destaque, sistema, infraestrutura |
| camadas-half | Representa camadas half, útil para configuração, integrações e recursos digitais. | camadas-half, camadas, half, sistema, infraestrutura |
| camera | Representa camera, útil para configuração, integrações e recursos digitais. | camera, sistema, infraestrutura |
| camera-destaque | Representa camera destaque, útil para configuração, integrações e recursos digitais. | camera-destaque, camera, destaque, sistema, infraestrutura |
| camera-reels | Representa camera reels, útil para configuração, integrações e recursos digitais. | camera-reels, camera, reels, sistema, infraestrutura |
| camera-reels-destaque | Representa camera reels destaque, útil para configuração, integrações e recursos digitais. | camera-reels-destaque, camera, reels, destaque, sistema, infraestrutura |
| camera-video | Representa camera video, útil para documentos, conteúdo e organização de arquivos. | camera-video, camera, video, arquivo, documento, arquivos, mídia |
| camera-video-destaque | Representa camera video destaque, útil para documentos, conteúdo e organização de arquivos. | camera-video-destaque, camera, video, destaque, arquivo, arquivos, mídia |
| camera-video-off | Representa camera video off, útil para documentos, conteúdo e organização de arquivos. | camera-video-off, camera, video, off, arquivo, arquivos, mídia |
| camera-video-off-destaque | Representa camera video off destaque, útil para documentos, conteúdo e organização de arquivos. | camera-video-off-destaque, camera, video, off, destaque, arquivos, mídia |
| camera2 | Representa camera2, útil para configuração, integrações e recursos digitais. | camera2, sistema, infraestrutura |
| caminhao | Representa caminhao, útil para operação, movimentação e contexto logístico. | caminhao, logistica, operacao, logística, operações |
| caminhao-flatbed | Representa caminhao flatbed, útil para operação, movimentação e contexto logístico. | caminhao-flatbed, caminhao, flatbed, logistica, operacao, logística, operações |
| caminhao-frente | Representa caminhao frente, útil para operação, movimentação e contexto logístico. | caminhao-frente, caminhao, frente, logistica, operacao, logística, operações |
| caminhao-frente-destaque | Representa caminhao frente destaque, útil para operação, movimentação e contexto logístico. | caminhao-frente-destaque, caminhao, frente, destaque, logistica, logística, operações |
| caneta | Representa caneta, útil para configuração, integrações e recursos digitais. | caneta, sistema, infraestrutura |
| caneta-destaque | Representa caneta destaque, útil para configuração, integrações e recursos digitais. | caneta-destaque, caneta, destaque, sistema, infraestrutura |
| capslock | Representa capslock, útil para configuração, integrações e recursos digitais. | capslock, sistema, infraestrutura |
| capslock-destaque | Representa capslock destaque, útil para configuração, integrações e recursos digitais. | capslock-destaque, capslock, destaque, sistema, infraestrutura |
| capsula | Representa capsula, útil para configuração, integrações e recursos digitais. | capsula, sistema, infraestrutura |
| capsula-pill | Representa capsula pill, útil para configuração, integrações e recursos digitais. | capsula-pill, capsula, pill, sistema, infraestrutura |
| card-checklist | Representa card checklist, útil para configuração, integrações e recursos digitais. | card-checklist, card, checklist, sistema, infraestrutura |
| card-heading | Representa card heading, útil para configuração, integrações e recursos digitais. | card-heading, card, heading, sistema, infraestrutura |
| card-imagem | Representa card imagem, útil para documentos, conteúdo e organização de arquivos. | card-imagem, card, imagem, arquivo, documento, arquivos, mídia |
| card-texto | Representa card texto, útil para configuração, integrações e recursos digitais. | card-texto, card, texto, sistema, infraestrutura |
| cards | Lista estruturada em cards, módulos ou atalhos. | cards, layout, visualizacao, lista, estruturada, visualização |
| carrinho | Carrinho, compra em andamento ou pedido aberto. | carrinho, compra, pedido, andamento, aberto, comércio, faturamento |
| carrinho-adicionar | Representa carrinho adicionar, útil para ações, comandos e interações diretas na interface. | carrinho-adicionar, carrinho, adicionar, acao, comando, ações |
| carrinho-adicionar-destaque | Representa carrinho adicionar destaque, útil para ações, comandos e interações diretas na interface. | carrinho-adicionar-destaque, carrinho, adicionar, destaque, acao, ações |
| carrinho-confirmado | Representa carrinho confirmado, útil para feedback visual, status e comunicação de estado. | carrinho-confirmado, carrinho, confirmado, status, estado, estados |
| carrinho-confirmado-destaque | Representa carrinho confirmado destaque, útil para feedback visual, status e comunicação de estado. | carrinho-confirmado-destaque, carrinho, confirmado, destaque, status, estados |
| carrinho-destaque | Representa carrinho destaque, útil para compras, vendas, cobrança e contexto financeiro. | carrinho-destaque, carrinho, destaque, compra, pedido, comércio, faturamento |
| carrinho-icon | Representa carrinho icon, útil para compras, vendas, cobrança e contexto financeiro. | carrinho-icon, carrinho, icon, compra, pedido, comércio, faturamento |
| carrinho-menos | Representa carrinho menos, útil para compras, vendas, cobrança e contexto financeiro. | carrinho-menos, carrinho, menos, compra, pedido, comércio, faturamento |
| carrinho-menos-destaque | Representa carrinho menos destaque, útil para compras, vendas, cobrança e contexto financeiro. | carrinho-menos-destaque, carrinho, menos, destaque, compra, comércio, faturamento |
| carrinho-remover | Representa carrinho remover, útil para ações, comandos e interações diretas na interface. | carrinho-remover, carrinho, remover, acao, comando, ações |
| carrinho-remover-destaque | Representa carrinho remover destaque, útil para ações, comandos e interações diretas na interface. | carrinho-remover-destaque, carrinho, remover, destaque, acao, ações |
| carro-eletrico-frente | Representa carro eletrico frente, útil para configuração, integrações e recursos digitais. | carro-eletrico-frente, carro, eletrico, frente, sistema, infraestrutura |
| carro-eletrico-frente-destaque | Representa carro eletrico frente destaque, útil para configuração, integrações e recursos digitais. | carro-eletrico-frente-destaque, carro, eletrico, frente, destaque, sistema, infraestrutura |
| carro-frente | Representa carro frente, útil para configuração, integrações e recursos digitais. | carro-frente, carro, frente, sistema, infraestrutura |
| carro-frente-destaque | Representa carro frente destaque, útil para configuração, integrações e recursos digitais. | carro-frente-destaque, carro, frente, destaque, sistema, infraestrutura |
| cart2 | Representa cart2, útil para configuração, integrações e recursos digitais. | cart2, sistema, infraestrutura |
| cart4 | Representa cart4, útil para configuração, integrações e recursos digitais. | cart4, sistema, infraestrutura |
| cartao-postal | Representa cartao postal, útil para configuração, integrações e recursos digitais. | cartao-postal, cartao, postal, sistema, infraestrutura |
| cartao-postal-coracao | Representa cartao postal coracao, útil para configuração, integrações e recursos digitais. | cartao-postal-coracao, cartao, postal, coracao, sistema, infraestrutura |
| cartao-postal-coracao-destaque | Representa cartao postal coracao destaque, útil para configuração, integrações e recursos digitais. | cartao-postal-coracao-destaque, cartao, postal, coracao, destaque, sistema, infraestrutura |
| cartao-postal-destaque | Representa cartao postal destaque, útil para configuração, integrações e recursos digitais. | cartao-postal-destaque, cartao, postal, destaque, sistema, infraestrutura |
| cartao-sd | Representa cartao sd, útil para configuração, integrações e recursos digitais. | cartao-sd, cartao, sistema, infraestrutura, sd |
| cartao-sd-destaque | Representa cartao sd destaque, útil para configuração, integrações e recursos digitais. | cartao-sd-destaque, cartao, destaque, sistema, infraestrutura, sd |
| carteira | Carteira, saldo, pagamentos ou concentrador financeiro. | carteira, compra, pedido, saldo, pagamentos, comércio, faturamento |
| carteira-destaque | Representa carteira destaque, útil para compras, vendas, cobrança e contexto financeiro. | carteira-destaque, carteira, destaque, compra, pedido, comércio, faturamento |
| carteira-icon | Representa carteira icon, útil para compras, vendas, cobrança e contexto financeiro. | carteira-icon, carteira, icon, compra, pedido, comércio, faturamento |
| casa-add | Representa casa add, útil para configuração, integrações e recursos digitais. | casa-add, casa, add, sistema, infraestrutura |
| casa-add-destaque | Representa casa add destaque, útil para configuração, integrações e recursos digitais. | casa-add-destaque, casa, add, destaque, sistema, infraestrutura |
| casa-baixo | Representa casa baixo, útil para navegação, direção e fluxo de interface. | casa-baixo, casa, baixo, navegacao, fluxo, navegação |
| casa-baixo-destaque | Representa casa baixo destaque, útil para navegação, direção e fluxo de interface. | casa-baixo-destaque, casa, baixo, destaque, navegacao, navegação |
| casa-cadeado | Representa casa cadeado, útil para segurança, controle de acesso e confiança operacional. | casa-cadeado, casa, cadeado, seguranca, permissao, segurança, permissões |
| casa-cadeado-destaque | Representa casa cadeado destaque, útil para segurança, controle de acesso e confiança operacional. | casa-cadeado-destaque, casa, cadeado, destaque, seguranca, segurança, permissões |
| casa-cima | Representa casa cima, útil para navegação, direção e fluxo de interface. | casa-cima, casa, cima, navegacao, fluxo, navegação |
| casa-cima-destaque | Representa casa cima destaque, útil para navegação, direção e fluxo de interface. | casa-cima-destaque, casa, cima, destaque, navegacao, navegação |
| casa-confirmado | Representa casa confirmado, útil para feedback visual, status e comunicação de estado. | casa-confirmado, casa, confirmado, status, estado, estados |
| casa-confirmado-destaque | Representa casa confirmado destaque, útil para feedback visual, status e comunicação de estado. | casa-confirmado-destaque, casa, confirmado, destaque, status, estados |
| casa-coracao | Representa casa coracao, útil para configuração, integrações e recursos digitais. | casa-coracao, casa, coracao, sistema, infraestrutura |
| casa-coracao-destaque | Representa casa coracao destaque, útil para configuração, integrações e recursos digitais. | casa-coracao-destaque, casa, coracao, destaque, sistema, infraestrutura |
| casa-cortado | Representa casa cortado, útil para configuração, integrações e recursos digitais. | casa-cortado, casa, cortado, sistema, infraestrutura |
| casa-cortado-destaque | Representa casa cortado destaque, útil para configuração, integrações e recursos digitais. | casa-cortado-destaque, casa, cortado, destaque, sistema, infraestrutura |
| casa-destaque | Representa casa destaque, útil para configuração, integrações e recursos digitais. | casa-destaque, casa, destaque, sistema, infraestrutura |
| casa-engrenagem | Representa casa engrenagem, útil para configuração, integrações e recursos digitais. | casa-engrenagem, casa, engrenagem, sistema, infraestrutura |
| casa-engrenagem-destaque | Representa casa engrenagem destaque, útil para configuração, integrações e recursos digitais. | casa-engrenagem-destaque, casa, engrenagem, destaque, sistema, infraestrutura |
| casa-exclamacao | Representa casa exclamacao, útil para configuração, integrações e recursos digitais. | casa-exclamacao, casa, exclamacao, sistema, infraestrutura |
| casa-exclamacao-destaque | Representa casa exclamacao destaque, útil para configuração, integrações e recursos digitais. | casa-exclamacao-destaque, casa, exclamacao, destaque, sistema, infraestrutura |
| casa-menos | Representa casa menos, útil para configuração, integrações e recursos digitais. | casa-menos, casa, menos, sistema, infraestrutura |
| casa-menos-destaque | Representa casa menos destaque, útil para configuração, integrações e recursos digitais. | casa-menos-destaque, casa, menos, destaque, sistema, infraestrutura |
| casa-porta-destaque | Representa casa porta destaque, útil para configuração, integrações e recursos digitais. | casa-porta-destaque, casa, porta, destaque, sistema, infraestrutura |
| casa-remover | Representa casa remover, útil para ações, comandos e interações diretas na interface. | casa-remover, casa, remover, acao, comando, ações |
| casa-remover-destaque | Representa casa remover destaque, útil para ações, comandos e interações diretas na interface. | casa-remover-destaque, casa, remover, destaque, acao, ações |
| cassette | Representa cassette, útil para configuração, integrações e recursos digitais. | cassette, sistema, infraestrutura |
| cassette-destaque | Representa cassette destaque, útil para configuração, integrações e recursos digitais. | cassette-destaque, cassette, destaque, sistema, infraestrutura |
| cavalete | Representa cavalete, útil para configuração, integrações e recursos digitais. | cavalete, sistema, infraestrutura |
| cavalete-destaque | Representa cavalete destaque, útil para configuração, integrações e recursos digitais. | cavalete-destaque, cavalete, destaque, sistema, infraestrutura |
| cc-circulo | Representa cc circulo, útil para configuração, integrações e recursos digitais. | cc-circulo, circulo, sistema, infraestrutura, cc |
| cc-circulo-destaque | Representa cc circulo destaque, útil para configuração, integrações e recursos digitais. | cc-circulo-destaque, circulo, destaque, sistema, infraestrutura, cc |
| cc-quadrado | Representa cc quadrado, útil para configuração, integrações e recursos digitais. | cc-quadrado, quadrado, sistema, infraestrutura, cc |
| cc-quadrado-destaque | Representa cc quadrado destaque, útil para configuração, integrações e recursos digitais. | cc-quadrado-destaque, quadrado, destaque, sistema, infraestrutura, cc |
| certificado | Selo de conformidade, verificação ou credencial válida. | certificado, aprendizado, conhecimento, selo, conformidade |
| cesta | Representa cesta, útil para configuração, integrações e recursos digitais. | cesta, sistema, infraestrutura |
| cesta-destaque | Representa cesta destaque, útil para configuração, integrações e recursos digitais. | cesta-destaque, cesta, destaque, sistema, infraestrutura |
| chamado | Ticket simples, ingresso, protocolo ou item de atendimento. | chamado, mensagem, contato, ticket, ingresso, comunicação |
| chamado-detalhe | Ticket com detalhe operacional, protocolo ou caso estruturado. | chamado-detalhe, chamado, detalhe, mensagem, contato, comunicação |
| chat | Representa chat, útil para mensagens, contato e fluxos de atendimento. | chat, mensagem, contato, comunicação |
| chat-citacao | Representa chat citacao, útil para mensagens, contato e fluxos de atendimento. | chat-citacao, chat, citacao, mensagem, contato, comunicação |
| chat-citacao-destaque | Representa chat citacao destaque, útil para mensagens, contato e fluxos de atendimento. | chat-citacao-destaque, chat, citacao, destaque, mensagem, comunicação |
| chat-coracao | Representa chat coracao, útil para mensagens, contato e fluxos de atendimento. | chat-coracao, chat, coracao, mensagem, contato, comunicação |
| chat-coracao-destaque | Representa chat coracao destaque, útil para mensagens, contato e fluxos de atendimento. | chat-coracao-destaque, chat, coracao, destaque, mensagem, comunicação |
| chat-destaque | Representa chat destaque, útil para mensagens, contato e fluxos de atendimento. | chat-destaque, chat, destaque, mensagem, contato, comunicação |
| chat-direita | Representa chat direita, útil para navegação, direção e fluxo de interface. | chat-direita, chat, direita, navegacao, fluxo, navegação |
| chat-direita-citacao | Representa chat direita citacao, útil para navegação, direção e fluxo de interface. | chat-direita-citacao, chat, direita, citacao, navegacao, navegação |
| chat-direita-citacao-destaque | Representa chat direita citacao destaque, útil para navegação, direção e fluxo de interface. | chat-direita-citacao-destaque, chat, direita, citacao, destaque, navegação |
| chat-direita-coracao | Representa chat direita coracao, útil para navegação, direção e fluxo de interface. | chat-direita-coracao, chat, direita, coracao, navegacao, navegação |
| chat-direita-coracao-destaque | Representa chat direita coracao destaque, útil para navegação, direção e fluxo de interface. | chat-direita-coracao-destaque, chat, direita, coracao, destaque, navegação |
| chat-direita-destaque | Representa chat direita destaque, útil para navegação, direção e fluxo de interface. | chat-direita-destaque, chat, direita, destaque, navegacao, navegação |
| chat-direita-dots | Representa chat direita dots, útil para navegação, direção e fluxo de interface. | chat-direita-dots, chat, direita, dots, navegacao, navegação |
| chat-direita-dots-destaque | Representa chat direita dots destaque, útil para navegação, direção e fluxo de interface. | chat-direita-dots-destaque, chat, direita, dots, destaque, navegação |
| chat-direita-texto | Representa chat direita texto, útil para navegação, direção e fluxo de interface. | chat-direita-texto, chat, direita, texto, navegacao, navegação |
| chat-direita-texto-destaque | Representa chat direita texto destaque, útil para navegação, direção e fluxo de interface. | chat-direita-texto-destaque, chat, direita, texto, destaque, navegação |
| chat-dots | Representa chat dots, útil para mensagens, contato e fluxos de atendimento. | chat-dots, chat, dots, mensagem, contato, comunicação |
| chat-dots-destaque | Representa chat dots destaque, útil para mensagens, contato e fluxos de atendimento. | chat-dots-destaque, chat, dots, destaque, mensagem, comunicação |
| chat-esquerda | Representa chat esquerda, útil para navegação, direção e fluxo de interface. | chat-esquerda, chat, esquerda, navegacao, fluxo, navegação |
| chat-esquerda-citacao | Representa chat esquerda citacao, útil para navegação, direção e fluxo de interface. | chat-esquerda-citacao, chat, esquerda, citacao, navegacao, navegação |
| chat-esquerda-citacao-destaque | Representa chat esquerda citacao destaque, útil para navegação, direção e fluxo de interface. | chat-esquerda-citacao-destaque, chat, esquerda, citacao, destaque, navegação |
| chat-esquerda-coracao | Representa chat esquerda coracao, útil para navegação, direção e fluxo de interface. | chat-esquerda-coracao, chat, esquerda, coracao, navegacao, navegação |
| chat-esquerda-coracao-destaque | Representa chat esquerda coracao destaque, útil para navegação, direção e fluxo de interface. | chat-esquerda-coracao-destaque, chat, esquerda, coracao, destaque, navegação |
| chat-esquerda-destaque | Representa chat esquerda destaque, útil para navegação, direção e fluxo de interface. | chat-esquerda-destaque, chat, esquerda, destaque, navegacao, navegação |
| chat-esquerda-dots | Representa chat esquerda dots, útil para navegação, direção e fluxo de interface. | chat-esquerda-dots, chat, esquerda, dots, navegacao, navegação |
| chat-esquerda-dots-destaque | Representa chat esquerda dots destaque, útil para navegação, direção e fluxo de interface. | chat-esquerda-dots-destaque, chat, esquerda, dots, destaque, navegação |
| chat-esquerda-texto | Representa chat esquerda texto, útil para navegação, direção e fluxo de interface. | chat-esquerda-texto, chat, esquerda, texto, navegacao, navegação |
| chat-esquerda-texto-destaque | Representa chat esquerda texto destaque, útil para navegação, direção e fluxo de interface. | chat-esquerda-texto-destaque, chat, esquerda, texto, destaque, navegação |
| chat-quadrado | Representa chat quadrado, útil para mensagens, contato e fluxos de atendimento. | chat-quadrado, chat, quadrado, mensagem, contato, comunicação |
| chat-quadrado-citacao | Representa chat quadrado citacao, útil para mensagens, contato e fluxos de atendimento. | chat-quadrado-citacao, chat, quadrado, citacao, mensagem, comunicação |
| chat-quadrado-citacao-destaque | Representa chat quadrado citacao destaque, útil para mensagens, contato e fluxos de atendimento. | chat-quadrado-citacao-destaque, chat, quadrado, citacao, destaque, comunicação |
| chat-quadrado-coracao | Representa chat quadrado coracao, útil para mensagens, contato e fluxos de atendimento. | chat-quadrado-coracao, chat, quadrado, coracao, mensagem, comunicação |
| chat-quadrado-coracao-destaque | Representa chat quadrado coracao destaque, útil para mensagens, contato e fluxos de atendimento. | chat-quadrado-coracao-destaque, chat, quadrado, coracao, destaque, comunicação |
| chat-quadrado-destaque | Representa chat quadrado destaque, útil para mensagens, contato e fluxos de atendimento. | chat-quadrado-destaque, chat, quadrado, destaque, mensagem, comunicação |
| chat-quadrado-dots | Representa chat quadrado dots, útil para mensagens, contato e fluxos de atendimento. | chat-quadrado-dots, chat, quadrado, dots, mensagem, comunicação |
| chat-quadrado-dots-destaque | Representa chat quadrado dots destaque, útil para mensagens, contato e fluxos de atendimento. | chat-quadrado-dots-destaque, chat, quadrado, dots, destaque, comunicação |
| chat-quadrado-texto-destaque | Representa chat quadrado texto destaque, útil para mensagens, contato e fluxos de atendimento. | chat-quadrado-texto-destaque, chat, quadrado, texto, destaque, comunicação |
| chat-texto | Representa chat texto, útil para mensagens, contato e fluxos de atendimento. | chat-texto, chat, texto, mensagem, contato, comunicação |
| chat-texto-destaque | Representa chat texto destaque, útil para mensagens, contato e fluxos de atendimento. | chat-texto-destaque, chat, texto, destaque, mensagem, comunicação |
| chave | Credencial, chave de acesso ou segurança. | chave, seguranca, permissao, credencial, acesso, segurança, permissões |
| chave-destaque | Representa chave destaque, útil para segurança, controle de acesso e confiança operacional. | chave-destaque, chave, destaque, seguranca, permissao, segurança, permissões |
| chave-inglesa | Representa chave inglesa, útil para segurança, controle de acesso e confiança operacional. | chave-inglesa, chave, inglesa, seguranca, permissao, segurança, permissões |
| chave-inglesa-adjustable-circulo | Representa chave inglesa adjustable circulo, útil para segurança, controle de acesso e confiança operacional. | chave-inglesa-adjustable-circulo, chave, inglesa, adjustable, circulo, segurança, permissões |
| chave-inglesa-adjustable-circulo-destaque | Representa chave inglesa adjustable circulo destaque, útil para segurança, controle de acesso e confiança operacional. | chave-inglesa-adjustable-circulo-destaque, chave, inglesa, adjustable, circulo, destaque, segurança, permissões |
| check2-quadrado | Representa check2 quadrado, útil para configuração, integrações e recursos digitais. | check2-quadrado, check2, quadrado, sistema, infraestrutura |
| checklist | Checklist de tarefa, auditoria concluída ou validação operacional. | checklist, sistema, infraestrutura, tarefa, auditoria |
| chevron-barra-baixo | Representa chevron barra baixo, útil para navegação, direção e fluxo de interface. | chevron-barra-baixo, chevron, barra, baixo, navegacao, navegação |
| chevron-barra-cima | Representa chevron barra cima, útil para navegação, direção e fluxo de interface. | chevron-barra-cima, chevron, barra, cima, navegacao, navegação |
| chevron-barra-contract | Representa chevron barra contract, útil para métricas, indicadores e leitura de dados. | chevron-barra-contract, chevron, barra, contract, dados, análise |
| chevron-barra-direita | Representa chevron barra direita, útil para navegação, direção e fluxo de interface. | chevron-barra-direita, chevron, barra, direita, navegacao, navegação |
| chevron-barra-esquerda | Representa chevron barra esquerda, útil para navegação, direção e fluxo de interface. | chevron-barra-esquerda, chevron, barra, esquerda, navegacao, navegação |
| chevron-barra-expand | Representa chevron barra expand, útil para métricas, indicadores e leitura de dados. | chevron-barra-expand, chevron, barra, expand, dados, análise |
| chevron-compact-baixo | Representa chevron compact baixo, útil para navegação, direção e fluxo de interface. | chevron-compact-baixo, chevron, compact, baixo, navegacao, navegação |
| chevron-compact-cima | Representa chevron compact cima, útil para navegação, direção e fluxo de interface. | chevron-compact-cima, chevron, compact, cima, navegacao, navegação |
| chevron-compact-direita | Representa chevron compact direita, útil para navegação, direção e fluxo de interface. | chevron-compact-direita, chevron, compact, direita, navegacao, navegação |
| chevron-compact-esquerda | Representa chevron compact esquerda, útil para navegação, direção e fluxo de interface. | chevron-compact-esquerda, chevron, compact, esquerda, navegacao, navegação |
| chevron-contract | Representa chevron contract, útil para configuração, integrações e recursos digitais. | chevron-contract, chevron, contract, sistema, infraestrutura |
| chevron-double-baixo | Representa chevron double baixo, útil para navegação, direção e fluxo de interface. | chevron-double-baixo, chevron, double, baixo, navegacao, navegação |
| chevron-double-cima | Representa chevron double cima, útil para navegação, direção e fluxo de interface. | chevron-double-cima, chevron, double, cima, navegacao, navegação |
| chevron-double-direita | Representa chevron double direita, útil para navegação, direção e fluxo de interface. | chevron-double-direita, chevron, double, direita, navegacao, navegação |
| chevron-double-esquerda | Representa chevron double esquerda, útil para navegação, direção e fluxo de interface. | chevron-double-esquerda, chevron, double, esquerda, navegacao, navegação |
| chevron-expand | Representa chevron expand, útil para configuração, integrações e recursos digitais. | chevron-expand, chevron, expand, sistema, infraestrutura |
| chip-sim | Representa chip sim, útil para configuração, integrações e recursos digitais. | chip-sim, chip, sim, sistema, infraestrutura |
| chip-sim-cortado | Representa chip sim cortado, útil para configuração, integrações e recursos digitais. | chip-sim-cortado, chip, sim, cortado, sistema, infraestrutura |
| chip-sim-cortado-destaque | Representa chip sim cortado destaque, útil para configuração, integrações e recursos digitais. | chip-sim-cortado-destaque, chip, sim, cortado, destaque, sistema, infraestrutura |
| chip-sim-destaque | Representa chip sim destaque, útil para configuração, integrações e recursos digitais. | chip-sim-destaque, chip, sim, destaque, sistema, infraestrutura |
| circulo | Representa circulo, útil para configuração, integrações e recursos digitais. | circulo, sistema, infraestrutura |
| circulo-destaque | Representa circulo destaque, útil para configuração, integrações e recursos digitais. | circulo-destaque, circulo, destaque, sistema, infraestrutura |
| circulo-half | Representa circulo half, útil para configuração, integrações e recursos digitais. | circulo-half, circulo, half, sistema, infraestrutura |
| circulo-quadrado | Representa circulo quadrado, útil para configuração, integrações e recursos digitais. | circulo-quadrado, circulo, quadrado, sistema, infraestrutura |
| citacao | Representa citacao, útil para configuração, integrações e recursos digitais. | citacao, sistema, infraestrutura |
| citacao-direita | Representa citacao direita, útil para navegação, direção e fluxo de interface. | citacao-direita, citacao, direita, navegacao, fluxo, navegação |
| citacao-esquerda | Representa citacao esquerda, útil para navegação, direção e fluxo de interface. | citacao-esquerda, citacao, esquerda, navegacao, fluxo, navegação |
| claude | Representa claude, útil para configuração, integrações e recursos digitais. | claude, sistema, infraestrutura |
| clipboard2 | Representa clipboard2, útil para configuração, integrações e recursos digitais. | clipboard2, sistema, infraestrutura |
| clipboard2-adicionar | Representa clipboard2 adicionar, útil para ações, comandos e interações diretas na interface. | clipboard2-adicionar, clipboard2, adicionar, acao, comando, ações |
| clipboard2-adicionar-destaque | Representa clipboard2 adicionar destaque, útil para ações, comandos e interações diretas na interface. | clipboard2-adicionar-destaque, clipboard2, adicionar, destaque, acao, ações |
| clipboard2-confirmado | Representa clipboard2 confirmado, útil para feedback visual, status e comunicação de estado. | clipboard2-confirmado, clipboard2, confirmado, status, estado, estados |
| clipboard2-confirmado-destaque | Representa clipboard2 confirmado destaque, útil para feedback visual, status e comunicação de estado. | clipboard2-confirmado-destaque, clipboard2, confirmado, destaque, status, estados |
| clipboard2-coracao | Representa clipboard2 coracao, útil para configuração, integrações e recursos digitais. | clipboard2-coracao, clipboard2, coracao, sistema, infraestrutura |
| clipboard2-coracao-destaque | Representa clipboard2 coracao destaque, útil para configuração, integrações e recursos digitais. | clipboard2-coracao-destaque, clipboard2, coracao, destaque, sistema, infraestrutura |
| clipboard2-data-destaque | Representa clipboard2 data destaque, útil para configuração, integrações e recursos digitais. | clipboard2-data-destaque, clipboard2, data, destaque, sistema, infraestrutura |
| clipboard2-destaque | Representa clipboard2 destaque, útil para configuração, integrações e recursos digitais. | clipboard2-destaque, clipboard2, destaque, sistema, infraestrutura |
| clipboard2-minus | Representa clipboard2 minus, útil para configuração, integrações e recursos digitais. | clipboard2-minus, clipboard2, minus, sistema, infraestrutura |
| clipboard2-minus-destaque | Representa clipboard2 minus destaque, útil para configuração, integrações e recursos digitais. | clipboard2-minus-destaque, clipboard2, minus, destaque, sistema, infraestrutura |
| clipboard2-pulse | Representa clipboard2 pulse, útil para configuração, integrações e recursos digitais. | clipboard2-pulse, clipboard2, pulse, sistema, infraestrutura |
| clipboard2-pulse-destaque | Representa clipboard2 pulse destaque, útil para configuração, integrações e recursos digitais. | clipboard2-pulse-destaque, clipboard2, pulse, destaque, sistema, infraestrutura |
| clipboard2-remover | Representa clipboard2 remover, útil para ações, comandos e interações diretas na interface. | clipboard2-remover, clipboard2, remover, acao, comando, ações |
| clipboard2-remover-destaque | Representa clipboard2 remover destaque, útil para ações, comandos e interações diretas na interface. | clipboard2-remover-destaque, clipboard2, remover, destaque, acao, ações |
| clipe | Representa clipe, útil para configuração, integrações e recursos digitais. | clipe, sistema, infraestrutura |
| clouds | Representa clouds, útil para configuração, integrações e recursos digitais. | clouds, sistema, infraestrutura |
| clouds-destaque | Representa clouds destaque, útil para configuração, integrações e recursos digitais. | clouds-destaque, clouds, destaque, sistema, infraestrutura |
| cloudy | Representa cloudy, útil para configuração, integrações e recursos digitais. | cloudy, sistema, infraestrutura |
| cloudy-destaque | Representa cloudy destaque, útil para configuração, integrações e recursos digitais. | cloudy-destaque, cloudy, destaque, sistema, infraestrutura |
| codigo | Representa codigo, útil para documentos, conteúdo e organização de arquivos. | codigo, arquivo, documento, arquivos, mídia |
| codigo-cortado | Representa codigo cortado, útil para documentos, conteúdo e organização de arquivos. | codigo-cortado, codigo, cortado, arquivo, documento, arquivos, mídia |
| codigo-qr | QR Code, acesso rápido, leitura ou autenticação visual. | codigo-qr, codigo, sistema, infraestrutura, code, qr, código |
| codigo-qr-scan | Representa codigo qr scan, útil para documentos, conteúdo e organização de arquivos. | codigo-qr-scan, codigo, scan, arquivo, documento, qr, arquivos, mídia |
| codigo-quadrado | Representa codigo quadrado, útil para documentos, conteúdo e organização de arquivos. | codigo-quadrado, codigo, quadrado, arquivo, documento, arquivos, mídia |
| cofre | Representa cofre, útil para configuração, integrações e recursos digitais. | cofre, sistema, infraestrutura |
| cofre-bank | Representa cofre bank, útil para configuração, integrações e recursos digitais. | cofre-bank, cofre, bank, sistema, infraestrutura |
| cofre-bank-destaque | Representa cofre bank destaque, útil para configuração, integrações e recursos digitais. | cofre-bank-destaque, cofre, bank, destaque, sistema, infraestrutura |
| cofre-destaque | Representa cofre destaque, útil para configuração, integrações e recursos digitais. | cofre-destaque, cofre, destaque, sistema, infraestrutura |
| colecao | Conjunto de itens, galeria ou agrupamento visual. | arquivo, documento, conjunto, galeria, coleção, arquivos, mídia |
| colecao-destaque | Representa colecao destaque, útil para documentos, conteúdo e organização de arquivos. | colecao-destaque, destaque, arquivo, documento, arquivos, mídia |
| colecao-reproduzir-destaque | Representa colecao reproduzir destaque, útil para documentos, conteúdo e organização de arquivos. | colecao-reproduzir-destaque, reproduzir, destaque, arquivo, arquivos, mídia |
| colunas | Layout em colunas, estrutura de painel ou divisão visual. | colunas, layout, visualizacao, estrutura, painel, visualização |
| colunas-gap | Representa colunas gap, útil para estrutura visual, composição e exibição de interface. | colunas-gap, colunas, gap, layout, visualizacao, visualização |
| colunas-icon | Representa colunas icon, útil para estrutura visual, composição e exibição de interface. | colunas-icon, colunas, icon, layout, visualizacao, visualização |
| combustivel-pump | Representa combustivel pump, útil para configuração, integrações e recursos digitais. | combustivel-pump, combustivel, pump, sistema, infraestrutura |
| combustivel-pump-destaque | Representa combustivel pump destaque, útil para configuração, integrações e recursos digitais. | combustivel-pump-destaque, combustivel, pump, destaque, sistema, infraestrutura |
| combustivel-pump-diesel | Representa combustivel pump diesel, útil para configuração, integrações e recursos digitais. | combustivel-pump-diesel, combustivel, pump, diesel, sistema, infraestrutura |
| combustivel-pump-diesel-destaque | Representa combustivel pump diesel destaque, útil para configuração, integrações e recursos digitais. | combustivel-pump-diesel-destaque, combustivel, pump, diesel, destaque, sistema, infraestrutura |
| command | Representa command, útil para configuração, integrações e recursos digitais. | command, sistema, infraestrutura |
| compartilhar | Representa compartilhar, útil para configuração, integrações e recursos digitais. | compartilhar, sistema, infraestrutura |
| compartilhar-destaque | Representa compartilhar destaque, útil para configuração, integrações e recursos digitais. | compartilhar-destaque, compartilhar, destaque, sistema, infraestrutura |
| concluir-todos | Confirmação em massa, todos selecionados ou tudo resolvido. | concluir-todos, concluir, todos, acao, comando, ações |
| cone | Representa cone, útil para configuração, integrações e recursos digitais. | cone, sistema, infraestrutura |
| cone-striped | Representa cone striped, útil para configuração, integrações e recursos digitais. | cone-striped, cone, striped, sistema, infraestrutura |
| configuracoes | Configurações, preferencias, sistema ou ajustes. | configuracoes, sistema, infraestrutura, preferencias, ajustes, configurações |
| confirmado | Confirmação, validação positiva ou operação concluída. | confirmado, status, estado, confirmacao, validacao, estados |
| confirmado-all | Representa confirmado all, útil para feedback visual, status e comunicação de estado. | confirmado-all, confirmado, all, status, estado, estados |
| confirmado-destaque | Sucesso enfático, conclusão definitiva ou estado positivo forte. | confirmado-destaque, confirmado, destaque, status, estado, estados |
| confirmado-icon | Representa confirmado icon, útil para feedback visual, status e comunicação de estado. | confirmado-icon, confirmado, icon, status, estado, estados |
| confirmado-quadrado | Representa confirmado quadrado, útil para feedback visual, status e comunicação de estado. | confirmado-quadrado, confirmado, quadrado, status, estado, estados |
| confirmado-quadrado-destaque | Representa confirmado quadrado destaque, útil para feedback visual, status e comunicação de estado. | confirmado-quadrado-destaque, confirmado, quadrado, destaque, status, estados |
| contato | Cadastro, contato detalhado ou ficha pessoal. | contato, usuario, acesso, cadastro, detalhado, usuários |
| controle | Representa controle, útil para configuração, integrações e recursos digitais. | controle, sistema, infraestrutura |
| conversa | Conversa, atendimento, mensagem textual ou suporte. | conversa, mensagem, contato, atendimento, textual, comunicação |
| cookie | Representa cookie, útil para configuração, integrações e recursos digitais. | cookie, sistema, infraestrutura |
| copiar | Representa copiar, útil para ações, comandos e interações diretas na interface. | copiar, acao, comando, ações |
| copo | Representa copo, útil para configuração, integrações e recursos digitais. | copo, sistema, infraestrutura |
| copo-destaque | Representa copo destaque, útil para configuração, integrações e recursos digitais. | copo-destaque, copo, destaque, sistema, infraestrutura |
| copo-hot | Representa copo hot, útil para configuração, integrações e recursos digitais. | copo-hot, copo, hot, sistema, infraestrutura |
| copo-hot-destaque | Representa copo hot destaque, útil para configuração, integrações e recursos digitais. | copo-hot-destaque, copo, hot, destaque, sistema, infraestrutura |
| copo-straw | Representa copo straw, útil para configuração, integrações e recursos digitais. | copo-straw, copo, straw, sistema, infraestrutura |
| coracao | Representa coracao, útil para configuração, integrações e recursos digitais. | coracao, sistema, infraestrutura |
| coracao-destaque | Representa coracao destaque, útil para configuração, integrações e recursos digitais. | coracao-destaque, coracao, destaque, sistema, infraestrutura |
| coracao-half | Representa coracao half, útil para configuração, integrações e recursos digitais. | coracao-half, coracao, half, sistema, infraestrutura |
| coracao-pulse | Representa coracao pulse, útil para configuração, integrações e recursos digitais. | coracao-pulse, coracao, pulse, sistema, infraestrutura |
| coracao-pulse-destaque | Representa coracao pulse destaque, útil para configuração, integrações e recursos digitais. | coracao-pulse-destaque, coracao, pulse, destaque, sistema, infraestrutura |
| coracao-seta | Representa coracao seta, útil para navegação, direção e fluxo de interface. | coracao-seta, coracao, seta, navegacao, fluxo, navegação |
| coracoes | Representa coracoes, útil para configuração, integrações e recursos digitais. | coracoes, sistema, infraestrutura |
| corpo-texto | Representa corpo texto, útil para configuração, integrações e recursos digitais. | corpo-texto, corpo, texto, sistema, infraestrutura |
| cortado | Representa cortado, útil para configuração, integrações e recursos digitais. | cortado, sistema, infraestrutura |
| cortado-circulo | Representa cortado circulo, útil para configuração, integrações e recursos digitais. | cortado-circulo, cortado, circulo, sistema, infraestrutura |
| cortado-circulo-destaque | Representa cortado circulo destaque, útil para configuração, integrações e recursos digitais. | cortado-circulo-destaque, cortado, circulo, destaque, sistema, infraestrutura |
| cortado-lg | Representa cortado lg, útil para configuração, integrações e recursos digitais. | cortado-lg, cortado, sistema, infraestrutura, lg |
| cortado-quadrado | Representa cortado quadrado, útil para configuração, integrações e recursos digitais. | cortado-quadrado, cortado, quadrado, sistema, infraestrutura |
| cortado-quadrado-destaque | Representa cortado quadrado destaque, útil para configuração, integrações e recursos digitais. | cortado-quadrado-destaque, cortado, quadrado, destaque, sistema, infraestrutura |
| credito-card | Representa credito card, útil para configuração, integrações e recursos digitais. | credito-card, credito, card, sistema, infraestrutura |
| credito-card-destaque | Representa credito card destaque, útil para configuração, integrações e recursos digitais. | credito-card-destaque, credito, card, destaque, sistema, infraestrutura |
| credito-card-numero-2-frente | Representa credito card numero 2 frente, útil para configuração, integrações e recursos digitais. | credito-card-numero-2-frente, credito, card, numero, frente, 2, sistema, infraestrutura |
| credito-card-numero-2-frente-destaque | Representa credito card numero 2 frente destaque, útil para configuração, integrações e recursos digitais. | credito-card-numero-2-frente-destaque, credito, card, numero, frente, 2, destaque, sistema |
| credito-card-numero-2-voltar | Representa credito card numero 2 voltar, útil para navegação, direção e fluxo de interface. | credito-card-numero-2-voltar, credito, card, numero, voltar, 2, navegação |
| credito-card-numero-2-voltar-destaque | Representa credito card numero 2 voltar destaque, útil para navegação, direção e fluxo de interface. | credito-card-numero-2-voltar-destaque, credito, card, numero, voltar, 2, destaque, navegação |
| crescimento | Crescimento, tendência positiva ou evolução de performance. | crescimento, dados, analise, tendencia, positiva, análise |
| cronometro | Contagem, duração, medição de tempo ou SLA. | cronometro, agenda, tempo, contagem, duracao, cronômetro, agendamento |
| cronometro-destaque | Representa cronometro destaque, útil para tempo, agenda e acompanhamento de prazos. | cronometro-destaque, cronometro, destaque, agenda, tempo, agendamento |
| crosshair | Representa crosshair, útil para configuração, integrações e recursos digitais. | crosshair, sistema, infraestrutura |
| crosshair2 | Representa crosshair2, útil para configuração, integrações e recursos digitais. | crosshair2, sistema, infraestrutura |
| css-icon | Representa css icon, útil para configuração, integrações e recursos digitais. | css-icon, css, icon, sistema, infraestrutura |
| currency-bitcoin | Representa currency bitcoin, útil para configuração, integrações e recursos digitais. | currency-bitcoin, currency, bitcoin, sistema, infraestrutura |
| currency-euro | Representa currency euro, útil para configuração, integrações e recursos digitais. | currency-euro, currency, euro, sistema, infraestrutura |
| currency-exchange | Representa currency exchange, útil para configuração, integrações e recursos digitais. | currency-exchange, currency, exchange, sistema, infraestrutura |
| currency-pound | Representa currency pound, útil para configuração, integrações e recursos digitais. | currency-pound, currency, pound, sistema, infraestrutura |
| currency-rupee | Representa currency rupee, útil para configuração, integrações e recursos digitais. | currency-rupee, currency, rupee, sistema, infraestrutura |
| currency-yen | Representa currency yen, útil para configuração, integrações e recursos digitais. | currency-yen, currency, yen, sistema, infraestrutura |
| cursor | Representa cursor, útil para configuração, integrações e recursos digitais. | cursor, sistema, infraestrutura |
| cursor-destaque | Representa cursor destaque, útil para configuração, integrações e recursos digitais. | cursor-destaque, cursor, destaque, sistema, infraestrutura |
| cursor-texto | Representa cursor texto, útil para configuração, integrações e recursos digitais. | cursor-texto, cursor, texto, sistema, infraestrutura |
| dado-numero-1 | Representa dado numero 1, útil para configuração, integrações e recursos digitais. | dado-numero-1, dado, numero, sistema, infraestrutura, 1 |
| dado-numero-1-destaque | Representa dado numero 1 destaque, útil para configuração, integrações e recursos digitais. | dado-numero-1-destaque, dado, numero, destaque, sistema, 1, infraestrutura |
| dado-numero-2 | Representa dado numero 2, útil para configuração, integrações e recursos digitais. | dado-numero-2, dado, numero, sistema, infraestrutura, 2 |
| dado-numero-2-destaque | Representa dado numero 2 destaque, útil para configuração, integrações e recursos digitais. | dado-numero-2-destaque, dado, numero, destaque, sistema, 2, infraestrutura |
| dado-numero-3 | Representa dado numero 3, útil para configuração, integrações e recursos digitais. | dado-numero-3, dado, numero, sistema, infraestrutura, 3 |
| dado-numero-3-destaque | Representa dado numero 3 destaque, útil para configuração, integrações e recursos digitais. | dado-numero-3-destaque, dado, numero, destaque, sistema, 3, infraestrutura |
| dado-numero-4 | Representa dado numero 4, útil para configuração, integrações e recursos digitais. | dado-numero-4, dado, numero, sistema, infraestrutura, 4 |
| dado-numero-4-destaque | Representa dado numero 4 destaque, útil para configuração, integrações e recursos digitais. | dado-numero-4-destaque, dado, numero, destaque, sistema, 4, infraestrutura |
| dado-numero-5 | Representa dado numero 5, útil para configuração, integrações e recursos digitais. | dado-numero-5, dado, numero, sistema, infraestrutura, 5 |
| dado-numero-5-destaque | Representa dado numero 5 destaque, útil para configuração, integrações e recursos digitais. | dado-numero-5-destaque, dado, numero, destaque, sistema, 5, infraestrutura |
| dado-numero-6 | Representa dado numero 6, útil para configuração, integrações e recursos digitais. | dado-numero-6, dado, numero, sistema, infraestrutura, 6 |
| dado-numero-6-destaque | Representa dado numero 6 destaque, útil para configuração, integrações e recursos digitais. | dado-numero-6-destaque, dado, numero, destaque, sistema, 6, infraestrutura |
| desbloquear | Representa desbloquear, útil para configuração, integrações e recursos digitais. | desbloquear, sistema, infraestrutura |
| desbloquear-2 | Representa desbloquear 2, útil para configuração, integrações e recursos digitais. | desbloquear-2, desbloquear, sistema, infraestrutura, 2 |
| desbloquear-2-destaque | Representa desbloquear 2 destaque, útil para configuração, integrações e recursos digitais. | desbloquear-2-destaque, desbloquear, destaque, sistema, infraestrutura, 2 |
| desbloquear-destaque | Representa desbloquear destaque, útil para configuração, integrações e recursos digitais. | desbloquear-destaque, desbloquear, destaque, sistema, infraestrutura |
| desempenho | Painel de desempenho, velocidade ou indicador principal. | desempenho, dados, analise, painel, velocidade, análise |
| desfazer | Retorno, desfazer ou recarga com sentido de reversão. | desfazer, navegacao, fluxo, retorno, recarga, navegação |
| diagram-numero-2 | Representa diagram numero 2, útil para configuração, integrações e recursos digitais. | diagram-numero-2, diagram, numero, sistema, infraestrutura, 2 |
| diagram-numero-2-destaque | Representa diagram numero 2 destaque, útil para configuração, integrações e recursos digitais. | diagram-numero-2-destaque, diagram, numero, destaque, sistema, 2, infraestrutura |
| diagram-numero-3-destaque | Representa diagram numero 3 destaque, útil para configuração, integrações e recursos digitais. | diagram-numero-3-destaque, diagram, numero, destaque, sistema, 3, infraestrutura |
| dinheiro | Representa dinheiro, útil para configuração, integrações e recursos digitais. | dinheiro, sistema, infraestrutura |
| dinheiro-moeda | Representa dinheiro moeda, útil para configuração, integrações e recursos digitais. | dinheiro-moeda, dinheiro, moeda, sistema, infraestrutura |
| direcao | Direcionamento, escolha de caminho ou roteamento. | direcao, navegacao, fluxo, direcionamento, escolha, direção, navegação |
| direita | Navegacao para direita ou avancar curto. | direita, navegacao, fluxo, avancar, curto, navegação |
| disco | Representa disco, útil para configuração, integrações e recursos digitais. | disco, sistema, infraestrutura |
| disco-destaque | Representa disco destaque, útil para configuração, integrações e recursos digitais. | disco-destaque, disco, destaque, sistema, infraestrutura |
| discord | Representa discord, útil para configuração, integrações e recursos digitais. | discord, sistema, infraestrutura |
| display | Representa display, útil para configuração, integrações e recursos digitais. | display, sistema, infraestrutura |
| display-destaque | Representa display destaque, útil para configuração, integrações e recursos digitais. | display-destaque, display, destaque, sistema, infraestrutura |
| displayport | Representa displayport, útil para configuração, integrações e recursos digitais. | displayport, sistema, infraestrutura |
| displayport-destaque | Representa displayport destaque, útil para configuração, integrações e recursos digitais. | displayport-destaque, displayport, destaque, sistema, infraestrutura |
| dispositivo-hdd | Representa dispositivo hdd, útil para configuração, integrações e recursos digitais. | dispositivo-hdd, dispositivo, hdd, sistema, infraestrutura |
| dispositivo-hdd-destaque | Representa dispositivo hdd destaque, útil para configuração, integrações e recursos digitais. | dispositivo-hdd-destaque, dispositivo, hdd, destaque, sistema, infraestrutura |
| dispositivo-ssd | Representa dispositivo ssd, útil para configuração, integrações e recursos digitais. | dispositivo-ssd, dispositivo, ssd, sistema, infraestrutura |
| dispositivo-ssd-destaque | Representa dispositivo ssd destaque, útil para configuração, integrações e recursos digitais. | dispositivo-ssd-destaque, dispositivo, ssd, destaque, sistema, infraestrutura |
| disquete | Representa disquete, útil para configuração, integrações e recursos digitais. | disquete, sistema, infraestrutura |
| disquete-destaque | Representa disquete destaque, útil para configuração, integrações e recursos digitais. | disquete-destaque, disquete, destaque, sistema, infraestrutura |
| distribute-horizontal | Representa distribute horizontal, útil para configuração, integrações e recursos digitais. | distribute-horizontal, distribute, horizontal, sistema, infraestrutura |
| distribute-vertical | Representa distribute vertical, útil para configuração, integrações e recursos digitais. | distribute-vertical, distribute, vertical, sistema, infraestrutura |
| documento | Documento textual, relatório ou conteúdo formal. | documento, arquivo, textual, relatorio, formal, arquivos, mídia |
| documento-protegido | Arquivo protegido, acesso restrito ou conteúdo confidencial. | documento-protegido, documento, protegido, arquivo, acesso, arquivos, mídia |
| dot | Representa dot, útil para configuração, integrações e recursos digitais. | dot, sistema, infraestrutura |
| dpad | Representa dpad, útil para configuração, integrações e recursos digitais. | dpad, sistema, infraestrutura |
| dpad-destaque | Representa dpad destaque, útil para configuração, integrações e recursos digitais. | dpad-destaque, dpad, destaque, sistema, infraestrutura |
| dribbble | Representa dribbble, útil para configuração, integrações e recursos digitais. | dribbble, sistema, infraestrutura |
| dropbox | Representa dropbox, útil para configuração, integrações e recursos digitais. | dropbox, sistema, infraestrutura |
| droplet | Representa droplet, útil para configuração, integrações e recursos digitais. | droplet, sistema, infraestrutura |
| droplet-destaque | Representa droplet destaque, útil para configuração, integrações e recursos digitais. | droplet-destaque, droplet, destaque, sistema, infraestrutura |
| droplet-half | Representa droplet half, útil para configuração, integrações e recursos digitais. | droplet-half, droplet, half, sistema, infraestrutura |
| duffle | Representa duffle, útil para configuração, integrações e recursos digitais. | duffle, sistema, infraestrutura |
| duffle-destaque | Representa duffle destaque, útil para configuração, integrações e recursos digitais. | duffle-destaque, duffle, destaque, sistema, infraestrutura |
| earbuds | Representa earbuds, útil para configuração, integrações e recursos digitais. | earbuds, sistema, infraestrutura |
| easel2 | Representa easel2, útil para configuração, integrações e recursos digitais. | easel2, sistema, infraestrutura |
| easel2-destaque | Representa easel2 destaque, útil para configuração, integrações e recursos digitais. | easel2-destaque, easel2, destaque, sistema, infraestrutura |
| easel3 | Representa easel3, útil para configuração, integrações e recursos digitais. | easel3, sistema, infraestrutura |
| easel3-destaque | Representa easel3 destaque, útil para configuração, integrações e recursos digitais. | easel3-destaque, easel3, destaque, sistema, infraestrutura |
| editar | Editar, revisar ou ajustar conteúdo. | editar, acao, comando, revisar, ajustar, ações |
| editar-detalhe | Edição com formulario, anotação ou composer. | editar-detalhe, editar, detalhe, acao, comando, ações |
| ejetar | Representa ejetar, útil para configuração, integrações e recursos digitais. | ejetar, sistema, infraestrutura |
| ejetar-destaque | Representa ejetar destaque, útil para configuração, integrações e recursos digitais. | ejetar-destaque, ejetar, destaque, sistema, infraestrutura |
| email-confirmado | Email confirmado, mensagem entregue ou canal validado. | email-confirmado, email, confirmado, mensagem, contato, comunicação |
| embaralhar | Representa embaralhar, útil para configuração, integrações e recursos digitais. | embaralhar, sistema, infraestrutura |
| emoji-angry | Representa emoji angry, útil para configuração, integrações e recursos digitais. | emoji-angry, emoji, angry, sistema, infraestrutura |
| emoji-angry-destaque | Representa emoji angry destaque, útil para configuração, integrações e recursos digitais. | emoji-angry-destaque, emoji, angry, destaque, sistema, infraestrutura |
| emoji-astonished | Representa emoji astonished, útil para configuração, integrações e recursos digitais. | emoji-astonished, emoji, astonished, sistema, infraestrutura |
| emoji-astonished-destaque | Representa emoji astonished destaque, útil para configuração, integrações e recursos digitais. | emoji-astonished-destaque, emoji, astonished, destaque, sistema, infraestrutura |
| emoji-coracao-eyes | Representa emoji coracao eyes, útil para configuração, integrações e recursos digitais. | emoji-coracao-eyes, emoji, coracao, eyes, sistema, infraestrutura |
| emoji-coracao-eyes-destaque | Representa emoji coracao eyes destaque, útil para configuração, integrações e recursos digitais. | emoji-coracao-eyes-destaque, emoji, coracao, eyes, destaque, sistema, infraestrutura |
| emoji-dizzy | Representa emoji dizzy, útil para configuração, integrações e recursos digitais. | emoji-dizzy, emoji, dizzy, sistema, infraestrutura |
| emoji-dizzy-destaque | Representa emoji dizzy destaque, útil para configuração, integrações e recursos digitais. | emoji-dizzy-destaque, emoji, dizzy, destaque, sistema, infraestrutura |
| emoji-expressionless | Representa emoji expressionless, útil para configuração, integrações e recursos digitais. | emoji-expressionless, emoji, expressionless, sistema, infraestrutura |
| emoji-expressionless-destaque | Representa emoji expressionless destaque, útil para configuração, integrações e recursos digitais. | emoji-expressionless-destaque, emoji, expressionless, destaque, sistema, infraestrutura |
| emoji-frown | Representa emoji frown, útil para configuração, integrações e recursos digitais. | emoji-frown, emoji, frown, sistema, infraestrutura |
| emoji-frown-destaque | Representa emoji frown destaque, útil para configuração, integrações e recursos digitais. | emoji-frown-destaque, emoji, frown, destaque, sistema, infraestrutura |
| emoji-grimace | Representa emoji grimace, útil para configuração, integrações e recursos digitais. | emoji-grimace, emoji, grimace, sistema, infraestrutura |
| emoji-grimace-destaque | Representa emoji grimace destaque, útil para configuração, integrações e recursos digitais. | emoji-grimace-destaque, emoji, grimace, destaque, sistema, infraestrutura |
| emoji-grin | Representa emoji grin, útil para configuração, integrações e recursos digitais. | emoji-grin, emoji, grin, sistema, infraestrutura |
| emoji-grin-destaque | Representa emoji grin destaque, útil para configuração, integrações e recursos digitais. | emoji-grin-destaque, emoji, grin, destaque, sistema, infraestrutura |
| emoji-kiss | Representa emoji kiss, útil para configuração, integrações e recursos digitais. | emoji-kiss, emoji, kiss, sistema, infraestrutura |
| emoji-kiss-destaque | Representa emoji kiss destaque, útil para configuração, integrações e recursos digitais. | emoji-kiss-destaque, emoji, kiss, destaque, sistema, infraestrutura |
| emoji-laughing | Representa emoji laughing, útil para configuração, integrações e recursos digitais. | emoji-laughing, emoji, laughing, sistema, infraestrutura |
| emoji-laughing-destaque | Representa emoji laughing destaque, útil para configuração, integrações e recursos digitais. | emoji-laughing-destaque, emoji, laughing, destaque, sistema, infraestrutura |
| emoji-neutral | Representa emoji neutral, útil para configuração, integrações e recursos digitais. | emoji-neutral, emoji, neutral, sistema, infraestrutura |
| emoji-neutral-destaque | Representa emoji neutral destaque, útil para configuração, integrações e recursos digitais. | emoji-neutral-destaque, emoji, neutral, destaque, sistema, infraestrutura |
| emoji-oculos-escuros | Representa emoji oculos escuros, útil para configuração, integrações e recursos digitais. | emoji-oculos-escuros, emoji, oculos, escuros, sistema, infraestrutura |
| emoji-oculos-escuros-destaque | Representa emoji oculos escuros destaque, útil para configuração, integrações e recursos digitais. | emoji-oculos-escuros-destaque, emoji, oculos, escuros, destaque, sistema, infraestrutura |
| emoji-smile | Representa emoji smile, útil para configuração, integrações e recursos digitais. | emoji-smile, emoji, smile, sistema, infraestrutura |
| emoji-smile-destaque | Representa emoji smile destaque, útil para configuração, integrações e recursos digitais. | emoji-smile-destaque, emoji, smile, destaque, sistema, infraestrutura |
| emoji-smile-upside-baixo | Representa emoji smile upside baixo, útil para navegação, direção e fluxo de interface. | emoji-smile-upside-baixo, emoji, smile, upside, baixo, navegação |
| emoji-smile-upside-baixo-destaque | Representa emoji smile upside baixo destaque, útil para navegação, direção e fluxo de interface. | emoji-smile-upside-baixo-destaque, emoji, smile, upside, baixo, destaque, navegação |
| emoji-surprise | Representa emoji surprise, útil para configuração, integrações e recursos digitais. | emoji-surprise, emoji, surprise, sistema, infraestrutura |
| emoji-surprise-destaque | Representa emoji surprise destaque, útil para configuração, integrações e recursos digitais. | emoji-surprise-destaque, emoji, surprise, destaque, sistema, infraestrutura |
| emoji-tear | Representa emoji tear, útil para configuração, integrações e recursos digitais. | emoji-tear, emoji, tear, sistema, infraestrutura |
| emoji-tear-destaque | Representa emoji tear destaque, útil para configuração, integrações e recursos digitais. | emoji-tear-destaque, emoji, tear, destaque, sistema, infraestrutura |
| emoji-wink | Representa emoji wink, útil para configuração, integrações e recursos digitais. | emoji-wink, emoji, wink, sistema, infraestrutura |
| emoji-wink-destaque | Representa emoji wink destaque, útil para configuração, integrações e recursos digitais. | emoji-wink-destaque, emoji, wink, destaque, sistema, infraestrutura |
| empresa | Empresa, organização, unidade comercial ou sede. | empresa, sistema, infraestrutura, organizacao, unidade |
| encaminhar | Encaminhamento, retorno contextual à direita ou resposta derivada. | encaminhar, navegacao, fluxo, encaminhamento, retorno, navegação |
| energia | Energia, rapidez, automacao ou ação instantanea. | energia, sistema, infraestrutura, rapidez, automacao |
| energia-destaque | Energia enfatizada ou ação rapida em destaque. | energia-destaque, energia, destaque, sistema, infraestrutura |
| energia-icon | Representa energia icon, útil para configuração, integrações e recursos digitais. | energia-icon, energia, icon, sistema, infraestrutura |
| engrenagem-destaque | Representa engrenagem destaque, útil para configuração, integrações e recursos digitais. | engrenagem-destaque, engrenagem, destaque, sistema, infraestrutura |
| engrenagem-wide | Representa engrenagem wide, útil para configuração, integrações e recursos digitais. | engrenagem-wide, engrenagem, wide, sistema, infraestrutura |
| engrenagem-wide-connected | Representa engrenagem wide connected, útil para configuração, integrações e recursos digitais. | engrenagem-wide-connected, engrenagem, wide, connected, sistema, infraestrutura |
| entrada | Representa entrada, útil para configuração, integrações e recursos digitais. | entrada, sistema, infraestrutura |
| entrada-cursor | Representa entrada cursor, útil para configuração, integrações e recursos digitais. | entrada-cursor, entrada, cursor, sistema, infraestrutura |
| entrada-cursor-texto | Representa entrada cursor texto, útil para configuração, integrações e recursos digitais. | entrada-cursor-texto, entrada, cursor, texto, sistema, infraestrutura |
| entradas | Representa entradas, útil para configuração, integrações e recursos digitais. | entradas, sistema, infraestrutura |
| entradas-destaque | Representa entradas destaque, útil para configuração, integrações e recursos digitais. | entradas-destaque, entradas, destaque, sistema, infraestrutura |
| entrar | Entrada no sistema, autenticação ou sessão iniciada. | entrar, seguranca, permissao, entrada, autenticacao, segurança, permissões |
| envelope | Representa envelope, útil para configuração, integrações e recursos digitais. | envelope, sistema, infraestrutura |
| envelope-adicionar | Representa envelope adicionar, útil para ações, comandos e interações diretas na interface. | envelope-adicionar, envelope, adicionar, acao, comando, ações |
| envelope-adicionar-destaque | Representa envelope adicionar destaque, útil para ações, comandos e interações diretas na interface. | envelope-adicionar-destaque, envelope, adicionar, destaque, acao, ações |
| envelope-at | Representa envelope at, útil para configuração, integrações e recursos digitais. | envelope-at, envelope, sistema, infraestrutura, at |
| envelope-at-destaque | Representa envelope at destaque, útil para configuração, integrações e recursos digitais. | envelope-at-destaque, envelope, destaque, sistema, infraestrutura, at |
| envelope-confirmado-destaque | Representa envelope confirmado destaque, útil para feedback visual, status e comunicação de estado. | envelope-confirmado-destaque, envelope, confirmado, destaque, status, estados |
| envelope-coracao | Representa envelope coracao, útil para configuração, integrações e recursos digitais. | envelope-coracao, envelope, coracao, sistema, infraestrutura |
| envelope-coracao-destaque | Representa envelope coracao destaque, útil para configuração, integrações e recursos digitais. | envelope-coracao-destaque, envelope, coracao, destaque, sistema, infraestrutura |
| envelope-cortado | Representa envelope cortado, útil para configuração, integrações e recursos digitais. | envelope-cortado, envelope, cortado, sistema, infraestrutura |
| envelope-cortado-destaque | Representa envelope cortado destaque, útil para configuração, integrações e recursos digitais. | envelope-cortado-destaque, envelope, cortado, destaque, sistema, infraestrutura |
| envelope-destaque | Representa envelope destaque, útil para configuração, integrações e recursos digitais. | envelope-destaque, envelope, destaque, sistema, infraestrutura |
| envelope-exclamacao | Representa envelope exclamacao, útil para configuração, integrações e recursos digitais. | envelope-exclamacao, envelope, exclamacao, sistema, infraestrutura |
| envelope-exclamacao-destaque | Representa envelope exclamacao destaque, útil para configuração, integrações e recursos digitais. | envelope-exclamacao-destaque, envelope, exclamacao, destaque, sistema, infraestrutura |
| envelope-menos | Representa envelope menos, útil para configuração, integrações e recursos digitais. | envelope-menos, envelope, menos, sistema, infraestrutura |
| envelope-menos-destaque | Representa envelope menos destaque, útil para configuração, integrações e recursos digitais. | envelope-menos-destaque, envelope, menos, destaque, sistema, infraestrutura |
| envelope-open | Representa envelope open, útil para configuração, integrações e recursos digitais. | envelope-open, envelope, open, sistema, infraestrutura |
| envelope-open-coracao | Representa envelope open coracao, útil para configuração, integrações e recursos digitais. | envelope-open-coracao, envelope, open, coracao, sistema, infraestrutura |
| envelope-open-coracao-destaque | Representa envelope open coracao destaque, útil para configuração, integrações e recursos digitais. | envelope-open-coracao-destaque, envelope, open, coracao, destaque, sistema, infraestrutura |
| envelope-open-destaque | Representa envelope open destaque, útil para configuração, integrações e recursos digitais. | envelope-open-destaque, envelope, open, destaque, sistema, infraestrutura |
| envelope-paper-coracao | Representa envelope paper coracao, útil para configuração, integrações e recursos digitais. | envelope-paper-coracao, envelope, paper, coracao, sistema, infraestrutura |
| envelope-paper-coracao-destaque | Representa envelope paper coracao destaque, útil para configuração, integrações e recursos digitais. | envelope-paper-coracao-destaque, envelope, paper, coracao, destaque, sistema, infraestrutura |
| envelope-paper-destaque | Representa envelope paper destaque, útil para configuração, integrações e recursos digitais. | envelope-paper-destaque, envelope, paper, destaque, sistema, infraestrutura |
| envelope-remover | Representa envelope remover, útil para ações, comandos e interações diretas na interface. | envelope-remover, envelope, remover, acao, comando, ações |
| envelope-remover-destaque | Representa envelope remover destaque, útil para ações, comandos e interações diretas na interface. | envelope-remover-destaque, envelope, remover, destaque, acao, ações |
| envelope-seta-baixo | Representa envelope seta baixo, útil para navegação, direção e fluxo de interface. | envelope-seta-baixo, envelope, seta, baixo, navegacao, navegação |
| envelope-seta-baixo-destaque | Representa envelope seta baixo destaque, útil para navegação, direção e fluxo de interface. | envelope-seta-baixo-destaque, envelope, seta, baixo, destaque, navegação |
| envelope-seta-cima | Representa envelope seta cima, útil para navegação, direção e fluxo de interface. | envelope-seta-cima, envelope, seta, cima, navegacao, navegação |
| envelope-seta-cima-destaque | Representa envelope seta cima destaque, útil para navegação, direção e fluxo de interface. | envelope-seta-cima-destaque, envelope, seta, cima, destaque, navegação |
| enviar | Enviar, despachar mensagem ou acionar fluxo. | enviar, acao, comando, despachar, mensagem, ações |
| enviar-adicionar | Representa enviar adicionar, útil para ações, comandos e interações diretas na interface. | enviar-adicionar, enviar, adicionar, acao, comando, ações |
| enviar-adicionar-destaque | Representa enviar adicionar destaque, útil para ações, comandos e interações diretas na interface. | enviar-adicionar-destaque, enviar, adicionar, destaque, acao, ações |
| enviar-arquivo | Enviar arquivo, importar recurso ou publicar item. | enviar-arquivo, enviar, arquivo, acao, comando, ações |
| enviar-confirmado | Representa enviar confirmado, útil para feedback visual, status e comunicação de estado. | enviar-confirmado, enviar, confirmado, status, estado, estados |
| enviar-confirmado-destaque | Representa enviar confirmado destaque, útil para feedback visual, status e comunicação de estado. | enviar-confirmado-destaque, enviar, confirmado, destaque, status, estados |
| enviar-cortado | Representa enviar cortado, útil para ações, comandos e interações diretas na interface. | enviar-cortado, enviar, cortado, acao, comando, ações |
| enviar-cortado-destaque | Representa enviar cortado destaque, útil para ações, comandos e interações diretas na interface. | enviar-cortado-destaque, enviar, cortado, destaque, acao, ações |
| enviar-destaque | Representa enviar destaque, útil para ações, comandos e interações diretas na interface. | enviar-destaque, enviar, destaque, acao, comando, ações |
| enviar-exclamacao | Representa enviar exclamacao, útil para ações, comandos e interações diretas na interface. | enviar-exclamacao, enviar, exclamacao, acao, comando, ações |
| enviar-exclamacao-destaque | Representa enviar exclamacao destaque, útil para ações, comandos e interações diretas na interface. | enviar-exclamacao-destaque, enviar, exclamacao, destaque, acao, ações |
| enviar-menos | Representa enviar menos, útil para ações, comandos e interações diretas na interface. | enviar-menos, enviar, menos, acao, comando, ações |
| enviar-menos-destaque | Representa enviar menos destaque, útil para ações, comandos e interações diretas na interface. | enviar-menos-destaque, enviar, menos, destaque, acao, ações |
| enviar-remover | Representa enviar remover, útil para ações, comandos e interações diretas na interface. | enviar-remover, enviar, remover, acao, comando, ações |
| enviar-remover-destaque | Representa enviar remover destaque, útil para ações, comandos e interações diretas na interface. | enviar-remover-destaque, enviar, remover, destaque, acao, ações |
| enviar-seta-baixo | Representa enviar seta baixo, útil para navegação, direção e fluxo de interface. | enviar-seta-baixo, enviar, seta, baixo, navegacao, navegação |
| enviar-seta-baixo-destaque | Representa enviar seta baixo destaque, útil para navegação, direção e fluxo de interface. | enviar-seta-baixo-destaque, enviar, seta, baixo, destaque, navegação |
| enviar-seta-cima | Representa enviar seta cima, útil para navegação, direção e fluxo de interface. | enviar-seta-cima, enviar, seta, cima, navegacao, navegação |
| enviar-seta-cima-destaque | Representa enviar seta cima destaque, útil para navegação, direção e fluxo de interface. | enviar-seta-cima-destaque, enviar, seta, cima, destaque, navegação |
| equipe | Grupo destacado, comunidade ou conjunto principal de usuários. | equipe, usuario, acesso, grupo, destacado, usuários |
| erro | Erro, negação ou encerramento com estado negativo. | erro, sistema, infraestrutura, negacao, encerramento |
| escape | Representa escape, útil para configuração, integrações e recursos digitais. | escape, sistema, infraestrutura |
| escudo | Representa escudo, útil para segurança, controle de acesso e confiança operacional. | escudo, seguranca, permissao, segurança, permissões |
| escudo-adicionar | Representa escudo adicionar, útil para ações, comandos e interações diretas na interface. | escudo-adicionar, escudo, adicionar, acao, comando, ações |
| escudo-cadeado-destaque | Representa escudo cadeado destaque, útil para segurança, controle de acesso e confiança operacional. | escudo-cadeado-destaque, escudo, cadeado, destaque, seguranca, segurança, permissões |
| escudo-cortado | Representa escudo cortado, útil para segurança, controle de acesso e confiança operacional. | escudo-cortado, escudo, cortado, seguranca, permissao, segurança, permissões |
| escudo-cortado-destaque | Representa escudo cortado destaque, útil para segurança, controle de acesso e confiança operacional. | escudo-cortado-destaque, escudo, cortado, destaque, seguranca, segurança, permissões |
| escudo-destaque | Representa escudo destaque, útil para segurança, controle de acesso e confiança operacional. | escudo-destaque, escudo, destaque, seguranca, permissao, segurança, permissões |
| escudo-destaque-adicionar | Representa escudo destaque adicionar, útil para ações, comandos e interações diretas na interface. | escudo-destaque-adicionar, escudo, destaque, adicionar, acao, ações |
| escudo-destaque-confirmado | Representa escudo destaque confirmado, útil para feedback visual, status e comunicação de estado. | escudo-destaque-confirmado, escudo, destaque, confirmado, status, estados |
| escudo-destaque-exclamacao | Representa escudo destaque exclamacao, útil para segurança, controle de acesso e confiança operacional. | escudo-destaque-exclamacao, escudo, destaque, exclamacao, seguranca, segurança, permissões |
| escudo-destaque-minus | Representa escudo destaque minus, útil para segurança, controle de acesso e confiança operacional. | escudo-destaque-minus, escudo, destaque, minus, seguranca, segurança, permissões |
| escudo-destaque-remover | Representa escudo destaque remover, útil para ações, comandos e interações diretas na interface. | escudo-destaque-remover, escudo, destaque, remover, acao, ações |
| escudo-minus | Representa escudo minus, útil para segurança, controle de acesso e confiança operacional. | escudo-minus, escudo, minus, seguranca, permissao, segurança, permissões |
| escudo-remover | Representa escudo remover, útil para ações, comandos e interações diretas na interface. | escudo-remover, escudo, remover, acao, comando, ações |
| escudo-shaded | Representa escudo shaded, útil para segurança, controle de acesso e confiança operacional. | escudo-shaded, escudo, shaded, seguranca, permissao, segurança, permissões |
| esquerda | Navegacao para esquerda ou retorno curto. | esquerda, navegacao, fluxo, retorno, curto, navegação |
| estrela | Representa estrela, útil para feedback visual, status e comunicação de estado. | estrela, status, estado, estados |
| estrela-destaque | Representa estrela destaque, útil para feedback visual, status e comunicação de estado. | estrela-destaque, estrela, destaque, status, estado, estados |
| estrelas | Destaque premium, favoritismo elevado ou brilho institucional. | estrelas, status, estado, destaque, premium, estados |
| estrutura | Relações estruturais, topologia, fluxo ou arquitetura. | estrutura, sistema, infraestrutura, relacoes, estruturais |
| ethernet | Representa ethernet, útil para configuração, integrações e recursos digitais. | ethernet, sistema, infraestrutura |
| etiqueta | Etiqueta, categoria comercial, promocao ou marcação. | etiqueta, compra, pedido, categoria, comercial, comércio, faturamento |
| etiqueta-destaque | Representa etiqueta destaque, útil para compras, vendas, cobrança e contexto financeiro. | etiqueta-destaque, etiqueta, destaque, compra, pedido, comércio, faturamento |
| etiquetas | Representa etiquetas, útil para configuração, integrações e recursos digitais. | etiquetas, sistema, infraestrutura |
| etiquetas-destaque | Representa etiquetas destaque, útil para configuração, integrações e recursos digitais. | etiquetas-destaque, etiquetas, destaque, sistema, infraestrutura |
| ev-station | Representa ev station, útil para configuração, integrações e recursos digitais. | ev-station, station, sistema, infraestrutura, ev |
| ev-station-destaque | Representa ev station destaque, útil para configuração, integrações e recursos digitais. | ev-station-destaque, station, destaque, sistema, infraestrutura, ev |
| evento | Evento datado, agendamento ou marco no calendário. | evento, agenda, tempo, datado, agendamento |
| exclamacao | Representa exclamacao, útil para configuração, integrações e recursos digitais. | exclamacao, sistema, infraestrutura |
| exclamacao-circulo-destaque | Representa exclamacao circulo destaque, útil para configuração, integrações e recursos digitais. | exclamacao-circulo-destaque, exclamacao, circulo, destaque, sistema, infraestrutura |
| exclamacao-lg | Representa exclamacao lg, útil para configuração, integrações e recursos digitais. | exclamacao-lg, exclamacao, sistema, infraestrutura, lg |
| exclamacao-losango | Representa exclamacao losango, útil para configuração, integrações e recursos digitais. | exclamacao-losango, exclamacao, losango, sistema, infraestrutura |
| exclamacao-losango-destaque | Representa exclamacao losango destaque, útil para configuração, integrações e recursos digitais. | exclamacao-losango-destaque, exclamacao, losango, destaque, sistema, infraestrutura |
| exclamacao-octagon | Representa exclamacao octagon, útil para configuração, integrações e recursos digitais. | exclamacao-octagon, exclamacao, octagon, sistema, infraestrutura |
| exclamacao-octagon-destaque | Representa exclamacao octagon destaque, útil para configuração, integrações e recursos digitais. | exclamacao-octagon-destaque, exclamacao, octagon, destaque, sistema, infraestrutura |
| exclamacao-quadrado | Representa exclamacao quadrado, útil para configuração, integrações e recursos digitais. | exclamacao-quadrado, exclamacao, quadrado, sistema, infraestrutura |
| exclamacao-quadrado-destaque | Representa exclamacao quadrado destaque, útil para configuração, integrações e recursos digitais. | exclamacao-quadrado-destaque, exclamacao, quadrado, destaque, sistema, infraestrutura |
| exclude | Representa exclude, útil para configuração, integrações e recursos digitais. | exclude, sistema, infraestrutura |
| excluir | Exclusao simples, descarte ou remocao direta. | excluir, acao, comando, exclusao, descarte, ações |
| excluir-definitivo | Exclusao alternativa, lixeira reforcada ou remocao definitiva. | excluir-definitivo, excluir, definitivo, acao, comando, ações |
| expandir | Expandir, abrir menu ou indicar direção inferior. | expandir, navegacao, fluxo, abrir, menu, navegação |
| explicit | Representa explicit, útil para configuração, integrações e recursos digitais. | explicit, sistema, infraestrutura |
| explicit-destaque | Representa explicit destaque, útil para configuração, integrações e recursos digitais. | explicit-destaque, explicit, destaque, sistema, infraestrutura |
| exposure | Representa exposure, útil para configuração, integrações e recursos digitais. | exposure, sistema, infraestrutura |
| eyedropper | Representa eyedropper, útil para configuração, integrações e recursos digitais. | eyedropper, sistema, infraestrutura |
| eyeglasses | Representa eyeglasses, útil para configuração, integrações e recursos digitais. | eyeglasses, sistema, infraestrutura |
| facebook | Representa facebook, útil para configuração, integrações e recursos digitais. | facebook, sistema, infraestrutura |
| favorito | Conteúdo salvo, favorito ou item priorizado. | favorito, arquivo, documento, salvo, priorizado, arquivos, mídia |
| feather | Representa feather, útil para configuração, integrações e recursos digitais. | feather, sistema, infraestrutura |
| feather2 | Representa feather2, útil para configuração, integrações e recursos digitais. | feather2, sistema, infraestrutura |
| fechar | Fechar, cancelar ou dispensar elemento atual. | fechar, sistema, infraestrutura, cancelar, dispensar |
| ferramentas | Ferramentas, manutenção, operação tecnica ou utilitarios. | ferramentas, sistema, infraestrutura, manutencao, operacao |
| filetype-aac | Representa filetype aac, útil para configuração, integrações e recursos digitais. | filetype-aac, filetype, aac, sistema, infraestrutura |
| filetype-bmp | Representa filetype bmp, útil para configuração, integrações e recursos digitais. | filetype-bmp, filetype, bmp, sistema, infraestrutura |
| filetype-pptx | Representa filetype pptx, útil para configuração, integrações e recursos digitais. | filetype-pptx, filetype, pptx, sistema, infraestrutura |
| filetype-xlsx | Representa filetype xlsx, útil para documentos, conteúdo e organização de arquivos. | filetype-xlsx, filetype, xlsx, arquivo, documento, arquivos, mídia |
| filme | Representa filme, útil para configuração, integrações e recursos digitais. | filme, sistema, infraestrutura |
| filtro | Filtro, refinamento ou segmentacao de resultados. | filtro, acao, comando, refinamento, segmentacao, ações |
| filtro-circulo | Representa filtro circulo, útil para configuração, integrações e recursos digitais. | filtro-circulo, filtro, circulo, sistema, infraestrutura |
| filtro-circulo-destaque | Representa filtro circulo destaque, útil para configuração, integrações e recursos digitais. | filtro-circulo-destaque, filtro, circulo, destaque, sistema, infraestrutura |
| filtro-direita | Representa filtro direita, útil para navegação, direção e fluxo de interface. | filtro-direita, filtro, direita, navegacao, fluxo, navegação |
| filtro-esquerda | Representa filtro esquerda, útil para navegação, direção e fluxo de interface. | filtro-esquerda, filtro, esquerda, navegacao, fluxo, navegação |
| filtro-icon | Representa filtro icon, útil para configuração, integrações e recursos digitais. | filtro-icon, filtro, icon, sistema, infraestrutura |
| filtro-quadrado | Representa filtro quadrado, útil para configuração, integrações e recursos digitais. | filtro-quadrado, filtro, quadrado, sistema, infraestrutura |
| filtro-quadrado-destaque | Representa filtro quadrado destaque, útil para configuração, integrações e recursos digitais. | filtro-quadrado-destaque, filtro, quadrado, destaque, sistema, infraestrutura |
| financeiro | Financeiro, cobrança, receita ou acumulado monetario. | financeiro, compra, pedido, cobranca, receita, comércio, faturamento |
| fingerprint | Representa fingerprint, útil para configuração, integrações e recursos digitais. | fingerprint, sistema, infraestrutura |
| flask | Representa flask, útil para configuração, integrações e recursos digitais. | flask, sistema, infraestrutura |
| flask-destaque | Representa flask destaque, útil para configuração, integrações e recursos digitais. | flask-destaque, flask, destaque, sistema, infraestrutura |
| flask-florence | Representa flask florence, útil para configuração, integrações e recursos digitais. | flask-florence, flask, florence, sistema, infraestrutura |
| flask-florence-destaque | Representa flask florence destaque, útil para configuração, integrações e recursos digitais. | flask-florence-destaque, flask, florence, destaque, sistema, infraestrutura |
| floppy2 | Representa floppy2, útil para configuração, integrações e recursos digitais. | floppy2, sistema, infraestrutura |
| floppy2-destaque | Representa floppy2 destaque, útil para configuração, integrações e recursos digitais. | floppy2-destaque, floppy2, destaque, sistema, infraestrutura |
| flower1 | Representa flower1, útil para configuração, integrações e recursos digitais. | flower1, sistema, infraestrutura |
| flower2 | Representa flower2, útil para configuração, integrações e recursos digitais. | flower2, sistema, infraestrutura |
| flower3 | Representa flower3, útil para configuração, integrações e recursos digitais. | flower3, sistema, infraestrutura |
| fogo | Representa fogo, útil para configuração, integrações e recursos digitais. | fogo, sistema, infraestrutura |
| foguete | Representa foguete, útil para configuração, integrações e recursos digitais. | foguete, sistema, infraestrutura |
| foguete-destaque | Representa foguete destaque, útil para configuração, integrações e recursos digitais. | foguete-destaque, foguete, destaque, sistema, infraestrutura |
| foguete-takeoff | Representa foguete takeoff, útil para configuração, integrações e recursos digitais. | foguete-takeoff, foguete, takeoff, sistema, infraestrutura |
| foguete-takeoff-destaque | Representa foguete takeoff destaque, útil para configuração, integrações e recursos digitais. | foguete-takeoff-destaque, foguete, takeoff, destaque, sistema, infraestrutura |
| fone | Representa fone, útil para configuração, integrações e recursos digitais. | fone, sistema, infraestrutura |
| fontes | Representa fontes, útil para configuração, integrações e recursos digitais. | fontes, sistema, infraestrutura |
| formacao | Formação, aprendizado, curso ou trilha educacional. | formacao, aprendizado, conhecimento, curso, trilha, formação |
| frente | Representa frente, útil para configuração, integrações e recursos digitais. | frente, sistema, infraestrutura |
| funnel-destaque | Representa funnel destaque, útil para configuração, integrações e recursos digitais. | funnel-destaque, funnel, destaque, sistema, infraestrutura |
| garfo-faca | Representa garfo faca, útil para configuração, integrações e recursos digitais. | garfo-faca, garfo, faca, sistema, infraestrutura |
| gema | Representa gema, útil para configuração, integrações e recursos digitais. | gema, sistema, infraestrutura |
| genero-ambiguous | Representa genero ambiguous, útil para configuração, integrações e recursos digitais. | genero-ambiguous, genero, ambiguous, sistema, infraestrutura |
| genero-female | Representa genero female, útil para configuração, integrações e recursos digitais. | genero-female, genero, female, sistema, infraestrutura |
| genero-male | Representa genero male, útil para configuração, integrações e recursos digitais. | genero-male, genero, male, sistema, infraestrutura |
| genero-neuter | Representa genero neuter, útil para configuração, integrações e recursos digitais. | genero-neuter, genero, neuter, sistema, infraestrutura |
| genero-trans | Representa genero trans, útil para configuração, integrações e recursos digitais. | genero-trans, genero, trans, sistema, infraestrutura |
| git | Representa git, útil para configuração, integrações e recursos digitais. | git, sistema, infraestrutura |
| github | Representa github, útil para configuração, integrações e recursos digitais. | github, sistema, infraestrutura |
| gitlab | Representa gitlab, útil para configuração, integrações e recursos digitais. | gitlab, sistema, infraestrutura |
| globo-americas | Representa globo americas, útil para configuração, integrações e recursos digitais. | globo-americas, globo, americas, sistema, infraestrutura |
| globo-americas-destaque | Representa globo americas destaque, útil para configuração, integrações e recursos digitais. | globo-americas-destaque, globo, americas, destaque, sistema, infraestrutura |
| globo-asia-australia | Representa globo asia australia, útil para configuração, integrações e recursos digitais. | globo-asia-australia, globo, asia, australia, sistema, infraestrutura |
| globo-asia-australia-destaque | Representa globo asia australia destaque, útil para configuração, integrações e recursos digitais. | globo-asia-australia-destaque, globo, asia, australia, destaque, sistema, infraestrutura |
| globo-central-south-asia | Representa globo central south asia, útil para configuração, integrações e recursos digitais. | globo-central-south-asia, globo, central, south, asia, sistema, infraestrutura |
| globo-central-south-asia-destaque | Representa globo central south asia destaque, útil para configuração, integrações e recursos digitais. | globo-central-south-asia-destaque, globo, central, south, asia, destaque, sistema, infraestrutura |
| globo-europe-africa | Representa globo europe africa, útil para configuração, integrações e recursos digitais. | globo-europe-africa, globo, europe, africa, sistema, infraestrutura |
| globo-europe-africa-destaque | Representa globo europe africa destaque, útil para configuração, integrações e recursos digitais. | globo-europe-africa-destaque, globo, europe, africa, destaque, sistema, infraestrutura |
| google | Representa google, útil para configuração, integrações e recursos digitais. | google, sistema, infraestrutura |
| google-play | Representa google play, útil para configuração, integrações e recursos digitais. | google-play, google, play, sistema, infraestrutura |
| grade | Grade básica, apps, módulos ou visão matricial. | grade, layout, visualizacao, basica, apps, visualização |
| grade-1x2-destaque | Representa grade 1x2 destaque, útil para estrutura visual, composição e exibição de interface. | grade-1x2-destaque, grade, 1x2, destaque, layout, visualização |
| grade-3x2 | Representa grade 3x2, útil para estrutura visual, composição e exibição de interface. | grade-3x2, grade, 3x2, layout, visualizacao, visualização |
| grade-3x2-gap | Representa grade 3x2 gap, útil para estrutura visual, composição e exibição de interface. | grade-3x2-gap, grade, 3x2, gap, layout, visualização |
| grade-3x2-gap-destaque | Representa grade 3x2 gap destaque, útil para estrutura visual, composição e exibição de interface. | grade-3x2-gap-destaque, grade, 3x2, gap, destaque, layout, visualização |
| grade-3x3 | Representa grade 3x3, útil para estrutura visual, composição e exibição de interface. | grade-3x3, grade, 3x3, layout, visualizacao, visualização |
| grade-3x3-gap-destaque | Representa grade 3x3 gap destaque, útil para estrutura visual, composição e exibição de interface. | grade-3x3-gap-destaque, grade, 3x3, gap, destaque, layout, visualização |
| grade-destaque | Versão sólida da grade de apps ou módulos. | grade-destaque, grade, destaque, layout, visualizacao, visualização |
| grafico | Indicador de métricas, relatórios e comparativos numéricos. | grafico, dados, analise, indicador, metricas, gráfico, análise |
| grafico-baixo | Representa grafico baixo, útil para navegação, direção e fluxo de interface. | grafico-baixo, grafico, baixo, navegacao, fluxo, navegação |
| grafico-baixo-seta | Representa grafico baixo seta, útil para navegação, direção e fluxo de interface. | grafico-baixo-seta, grafico, baixo, seta, navegacao, navegação |
| grafico-cima | Representa grafico cima, útil para navegação, direção e fluxo de interface. | grafico-cima, grafico, cima, navegacao, fluxo, navegação |
| gravar | Representa gravar, útil para configuração, integrações e recursos digitais. | gravar, sistema, infraestrutura |
| gravar-btn | Representa gravar btn, útil para configuração, integrações e recursos digitais. | gravar-btn, gravar, btn, sistema, infraestrutura |
| gravar-btn-destaque | Representa gravar btn destaque, útil para configuração, integrações e recursos digitais. | gravar-btn-destaque, gravar, btn, destaque, sistema, infraestrutura |
| gravar-circulo | Representa gravar circulo, útil para configuração, integrações e recursos digitais. | gravar-circulo, gravar, circulo, sistema, infraestrutura |
| gravar-circulo-destaque | Representa gravar circulo destaque, útil para configuração, integrações e recursos digitais. | gravar-circulo-destaque, gravar, circulo, destaque, sistema, infraestrutura |
| gravar-destaque | Representa gravar destaque, útil para configuração, integrações e recursos digitais. | gravar-destaque, gravar, destaque, sistema, infraestrutura |
| guarda-chuva | Representa guarda chuva, útil para configuração, integrações e recursos digitais. | guarda-chuva, guarda, chuva, sistema, infraestrutura |
| guarda-chuva-destaque | Representa guarda chuva destaque, útil para configuração, integrações e recursos digitais. | guarda-chuva-destaque, guarda, chuva, destaque, sistema, infraestrutura |
| h-circulo | Representa h circulo, útil para configuração, integrações e recursos digitais. | h-circulo, circulo, sistema, infraestrutura, h |
| h-circulo-destaque | Representa h circulo destaque, útil para configuração, integrações e recursos digitais. | h-circulo-destaque, circulo, destaque, sistema, infraestrutura, h |
| h-quadrado | Representa h quadrado, útil para configuração, integrações e recursos digitais. | h-quadrado, quadrado, sistema, infraestrutura, h |
| h-quadrado-destaque | Representa h quadrado destaque, útil para configuração, integrações e recursos digitais. | h-quadrado-destaque, quadrado, destaque, sistema, infraestrutura, h |
| hash | Representa hash, útil para configuração, integrações e recursos digitais. | hash, sistema, infraestrutura |
| hdd-destaque | Representa hdd destaque, útil para configuração, integrações e recursos digitais. | hdd-destaque, hdd, destaque, sistema, infraestrutura |
| hdd-network | Representa hdd network, útil para configuração, integrações e recursos digitais. | hdd-network, hdd, network, sistema, infraestrutura |
| hdd-network-destaque | Representa hdd network destaque, útil para configuração, integrações e recursos digitais. | hdd-network-destaque, hdd, network, destaque, sistema, infraestrutura |
| hdd-pilha | Representa hdd pilha, útil para configuração, integrações e recursos digitais. | hdd-pilha, hdd, pilha, sistema, infraestrutura |
| hdd-pilha-destaque | Representa hdd pilha destaque, útil para configuração, integrações e recursos digitais. | hdd-pilha-destaque, hdd, pilha, destaque, sistema, infraestrutura |
| hdd-rack | Representa hdd rack, útil para configuração, integrações e recursos digitais. | hdd-rack, hdd, rack, sistema, infraestrutura |
| hdd-rack-destaque | Representa hdd rack destaque, útil para configuração, integrações e recursos digitais. | hdd-rack-destaque, hdd, rack, destaque, sistema, infraestrutura |
| hdmi | Representa hdmi, útil para configuração, integrações e recursos digitais. | hdmi, sistema, infraestrutura |
| hdmi-destaque | Representa hdmi destaque, útil para configuração, integrações e recursos digitais. | hdmi-destaque, hdmi, destaque, sistema, infraestrutura |
| headset-vr | Representa headset vr, útil para configuração, integrações e recursos digitais. | headset-vr, headset, sistema, infraestrutura, vr |
| heartbreak | Representa heartbreak, útil para configuração, integrações e recursos digitais. | heartbreak, sistema, infraestrutura |
| heartbreak-destaque | Representa heartbreak destaque, útil para configuração, integrações e recursos digitais. | heartbreak-destaque, heartbreak, destaque, sistema, infraestrutura |
| heptagon | Representa heptagon, útil para configuração, integrações e recursos digitais. | heptagon, sistema, infraestrutura |
| heptagon-destaque | Representa heptagon destaque, útil para configuração, integrações e recursos digitais. | heptagon-destaque, heptagon, destaque, sistema, infraestrutura |
| heptagon-half | Representa heptagon half, útil para configuração, integrações e recursos digitais. | heptagon-half, heptagon, half, sistema, infraestrutura |
| hexagono | Representa hexagono, útil para configuração, integrações e recursos digitais. | hexagono, sistema, infraestrutura |
| hexagono-destaque | Representa hexagono destaque, útil para configuração, integrações e recursos digitais. | hexagono-destaque, hexagono, destaque, sistema, infraestrutura |
| hexagono-half | Representa hexagono half, útil para configuração, integrações e recursos digitais. | hexagono-half, hexagono, half, sistema, infraestrutura |
| highlighter | Representa highlighter, útil para configuração, integrações e recursos digitais. | highlighter, sistema, infraestrutura |
| highlights | Representa highlights, útil para configuração, integrações e recursos digitais. | highlights, sistema, infraestrutura |
| historico | Histórico temporal, revisões, logs ou retrospecção. | historico, agenda, tempo, temporal, revisoes, histórico, agendamento |
| horario | Horário, prazo simples ou referencia temporal neutra. | horario, agenda, tempo, prazo, referencia, horário, agendamento |
| hospital | Representa hospital, útil para configuração, integrações e recursos digitais. | hospital, sistema, infraestrutura |
| hospital-destaque | Representa hospital destaque, útil para configuração, integrações e recursos digitais. | hospital-destaque, hospital, destaque, sistema, infraestrutura |
| houses | Representa houses, útil para configuração, integrações e recursos digitais. | houses, sistema, infraestrutura |
| houses-destaque | Representa houses destaque, útil para configuração, integrações e recursos digitais. | houses-destaque, houses, destaque, sistema, infraestrutura |
| hurricane | Representa hurricane, útil para configuração, integrações e recursos digitais. | hurricane, sistema, infraestrutura |
| hypnotize | Representa hypnotize, útil para configuração, integrações e recursos digitais. | hypnotize, sistema, infraestrutura |
| ima | Representa ima, útil para configuração, integrações e recursos digitais. | ima, sistema, infraestrutura |
| ima-destaque | Representa ima destaque, útil para configuração, integrações e recursos digitais. | ima-destaque, ima, destaque, sistema, infraestrutura |
| imagem | Imagem, banner, galeria ou mídia estática. | imagem, arquivo, documento, banner, galeria, arquivos, mídia |
| imagem-alternativo | Representa imagem alternativo, útil para documentos, conteúdo e organização de arquivos. | imagem-alternativo, imagem, alternativo, arquivo, documento, arquivos, mídia |
| imagem-destaque | Representa imagem destaque, útil para documentos, conteúdo e organização de arquivos. | imagem-destaque, imagem, destaque, arquivo, documento, arquivos, mídia |
| imagens | Representa imagens, útil para configuração, integrações e recursos digitais. | imagens, sistema, infraestrutura |
| impressora | Representa impressora, útil para configuração, integrações e recursos digitais. | impressora, sistema, infraestrutura |
| impressora-destaque | Representa impressora destaque, útil para configuração, integrações e recursos digitais. | impressora-destaque, impressora, destaque, sistema, infraestrutura |
| impulso | Carga, impulso, performance elevada ou aceleracao. | impulso, sistema, infraestrutura, carga, performance |
| incognito | Representa incognito, útil para configuração, integrações e recursos digitais. | incognito, sistema, infraestrutura |
| indentacao | Representa indentacao, útil para configuração, integrações e recursos digitais. | indentacao, sistema, infraestrutura |
| indicador-baixo | Representa indicador baixo, útil para navegação, direção e fluxo de interface. | indicador-baixo, indicador, baixo, navegacao, fluxo, navegação |
| indicador-baixo-destaque | Representa indicador baixo destaque, útil para navegação, direção e fluxo de interface. | indicador-baixo-destaque, indicador, baixo, destaque, navegacao, navegação |
| indicador-baixo-quadrado | Representa indicador baixo quadrado, útil para navegação, direção e fluxo de interface. | indicador-baixo-quadrado, indicador, baixo, quadrado, navegacao, navegação |
| indicador-baixo-quadrado-destaque | Representa indicador baixo quadrado destaque, útil para navegação, direção e fluxo de interface. | indicador-baixo-quadrado-destaque, indicador, baixo, quadrado, destaque, navegação |
| indicador-cima | Representa indicador cima, útil para navegação, direção e fluxo de interface. | indicador-cima, indicador, cima, navegacao, fluxo, navegação |
| indicador-cima-destaque | Representa indicador cima destaque, útil para navegação, direção e fluxo de interface. | indicador-cima-destaque, indicador, cima, destaque, navegacao, navegação |
| indicador-cima-quadrado | Representa indicador cima quadrado, útil para navegação, direção e fluxo de interface. | indicador-cima-quadrado, indicador, cima, quadrado, navegacao, navegação |
| indicador-cima-quadrado-destaque | Representa indicador cima quadrado destaque, útil para navegação, direção e fluxo de interface. | indicador-cima-quadrado-destaque, indicador, cima, quadrado, destaque, navegação |
| indicador-direita | Representa indicador direita, útil para navegação, direção e fluxo de interface. | indicador-direita, indicador, direita, navegacao, fluxo, navegação |
| indicador-direita-destaque | Representa indicador direita destaque, útil para navegação, direção e fluxo de interface. | indicador-direita-destaque, indicador, direita, destaque, navegacao, navegação |
| indicador-direita-quadrado | Representa indicador direita quadrado, útil para navegação, direção e fluxo de interface. | indicador-direita-quadrado, indicador, direita, quadrado, navegacao, navegação |
| indicador-direita-quadrado-destaque | Representa indicador direita quadrado destaque, útil para navegação, direção e fluxo de interface. | indicador-direita-quadrado-destaque, indicador, direita, quadrado, destaque, navegação |
| indicador-esquerda | Representa indicador esquerda, útil para navegação, direção e fluxo de interface. | indicador-esquerda, indicador, esquerda, navegacao, fluxo, navegação |
| indicador-esquerda-destaque | Representa indicador esquerda destaque, útil para navegação, direção e fluxo de interface. | indicador-esquerda-destaque, indicador, esquerda, destaque, navegacao, navegação |
| indicador-esquerda-quadrado | Representa indicador esquerda quadrado, útil para navegação, direção e fluxo de interface. | indicador-esquerda-quadrado, indicador, esquerda, quadrado, navegacao, navegação |
| indicador-esquerda-quadrado-destaque | Representa indicador esquerda quadrado destaque, útil para navegação, direção e fluxo de interface. | indicador-esquerda-quadrado-destaque, indicador, esquerda, quadrado, destaque, navegação |
| infinity | Representa infinity, útil para configuração, integrações e recursos digitais. | infinity, sistema, infraestrutura |
| informacao | Representa informacao, útil para configuração, integrações e recursos digitais. | informacao, sistema, infraestrutura |
| informacao-circulo | Representa informacao circulo, útil para configuração, integrações e recursos digitais. | informacao-circulo, informacao, circulo, sistema, infraestrutura |
| informacao-circulo-destaque | Representa informacao circulo destaque, útil para configuração, integrações e recursos digitais. | informacao-circulo-destaque, informacao, circulo, destaque, sistema, infraestrutura |
| informacao-lg | Representa informacao lg, útil para configuração, integrações e recursos digitais. | informacao-lg, informacao, sistema, infraestrutura, lg |
| informacao-quadrado | Representa informacao quadrado, útil para configuração, integrações e recursos digitais. | informacao-quadrado, informacao, quadrado, sistema, infraestrutura |
| informacao-quadrado-destaque | Representa informacao quadrado destaque, útil para configuração, integrações e recursos digitais. | informacao-quadrado-destaque, informacao, quadrado, destaque, sistema, infraestrutura |
| ingresso | Representa ingresso, útil para configuração, integrações e recursos digitais. | ingresso, sistema, infraestrutura |
| ingresso-destaque | Representa ingresso destaque, útil para configuração, integrações e recursos digitais. | ingresso-destaque, ingresso, destaque, sistema, infraestrutura |
| ingresso-detailed-destaque | Representa ingresso detailed destaque, útil para configuração, integrações e recursos digitais. | ingresso-detailed-destaque, ingresso, detailed, destaque, sistema, infraestrutura |
| ingresso-perforated-destaque | Representa ingresso perforated destaque, útil para configuração, integrações e recursos digitais. | ingresso-perforated-destaque, ingresso, perforated, destaque, sistema, infraestrutura |
| inicio | Inicio, dashboard raiz ou página principal. | inicio, navegacao, fluxo, dashboard, raiz, início, navegação |
| instagram | Representa instagram, útil para configuração, integrações e recursos digitais. | instagram, sistema, infraestrutura |
| integracao | Integração, conexao de servico ou extensibilidade. | integracao, sistema, infraestrutura, conexao, servico, integração |
| intersecao | Representa intersecao, útil para configuração, integrações e recursos digitais. | intersecao, sistema, infraestrutura |
| janela | Representa janela, útil para estrutura visual, composição e exibição de interface. | janela, layout, visualizacao, visualização |
| janela-adicionar | Representa janela adicionar, útil para ações, comandos e interações diretas na interface. | janela-adicionar, janela, adicionar, acao, comando, ações |
| janela-desktop | Representa janela desktop, útil para estrutura visual, composição e exibição de interface. | janela-desktop, janela, desktop, layout, visualizacao, visualização |
| janela-dividida | Representa janela dividida, útil para estrutura visual, composição e exibição de interface. | janela-dividida, janela, dividida, layout, visualizacao, visualização |
| janela-dock | Representa janela dock, útil para estrutura visual, composição e exibição de interface. | janela-dock, janela, dock, layout, visualizacao, visualização |
| janela-lateral | Representa janela lateral, útil para estrutura visual, composição e exibição de interface. | janela-lateral, janela, lateral, layout, visualizacao, visualização |
| janela-menos | Representa janela menos, útil para estrutura visual, composição e exibição de interface. | janela-menos, janela, menos, layout, visualizacao, visualização |
| janela-pilha | Representa janela pilha, útil para estrutura visual, composição e exibição de interface. | janela-pilha, janela, pilha, layout, visualizacao, visualização |
| janela-remover | Representa janela remover, útil para ações, comandos e interações diretas na interface. | janela-remover, janela, remover, acao, comando, ações |
| janela-tela-cheia | Representa janela tela cheia, útil para estrutura visual, composição e exibição de interface. | janela-tela-cheia, janela, tela, cheia, layout, visualização |
| javascript-icon | Representa javascript icon, útil para configuração, integrações e recursos digitais. | javascript-icon, javascript, icon, sistema, infraestrutura |
| jornal | Representa jornal, útil para configuração, integrações e recursos digitais. | jornal, sistema, infraestrutura |
| jornal-adicionar | Representa jornal adicionar, útil para ações, comandos e interações diretas na interface. | jornal-adicionar, jornal, adicionar, acao, comando, ações |
| jornal-album | Representa jornal album, útil para configuração, integrações e recursos digitais. | jornal-album, jornal, album, sistema, infraestrutura |
| jornal-codigo | Representa jornal codigo, útil para documentos, conteúdo e organização de arquivos. | jornal-codigo, jornal, codigo, arquivo, documento, arquivos, mídia |
| jornal-confirmado | Representa jornal confirmado, útil para feedback visual, status e comunicação de estado. | jornal-confirmado, jornal, confirmado, status, estado, estados |
| jornal-icon | Representa jornal icon, útil para configuração, integrações e recursos digitais. | jornal-icon, jornal, icon, sistema, infraestrutura |
| jornal-marcador | Representa jornal marcador, útil para configuração, integrações e recursos digitais. | jornal-marcador, jornal, marcador, sistema, infraestrutura |
| jornal-marcador-destaque | Representa jornal marcador destaque, útil para configuração, integrações e recursos digitais. | jornal-marcador-destaque, jornal, marcador, destaque, sistema, infraestrutura |
| jornal-medical | Representa jornal medical, útil para configuração, integrações e recursos digitais. | jornal-medical, jornal, medical, sistema, infraestrutura |
| jornal-minus | Representa jornal minus, útil para configuração, integrações e recursos digitais. | jornal-minus, jornal, minus, sistema, infraestrutura |
| jornal-remover | Representa jornal remover, útil para ações, comandos e interações diretas na interface. | jornal-remover, jornal, remover, acao, comando, ações |
| jornal-richtext | Representa jornal richtext, útil para configuração, integrações e recursos digitais. | jornal-richtext, jornal, richtext, sistema, infraestrutura |
| jornal-seta-baixo | Representa jornal seta baixo, útil para navegação, direção e fluxo de interface. | jornal-seta-baixo, jornal, seta, baixo, navegacao, navegação |
| jornal-seta-cima | Representa jornal seta cima, útil para navegação, direção e fluxo de interface. | jornal-seta-cima, jornal, seta, cima, navegacao, navegação |
| journals | Representa journals, útil para configuração, integrações e recursos digitais. | journals, sistema, infraestrutura |
| joystick | Representa joystick, útil para configuração, integrações e recursos digitais. | joystick, sistema, infraestrutura |
| justificar | Representa justificar, útil para configuração, integrações e recursos digitais. | justificar, sistema, infraestrutura |
| justificar-direita | Representa justificar direita, útil para navegação, direção e fluxo de interface. | justificar-direita, justificar, direita, navegacao, fluxo, navegação |
| justificar-esquerda | Representa justificar esquerda, útil para navegação, direção e fluxo de interface. | justificar-esquerda, justificar, esquerda, navegacao, fluxo, navegação |
| kanban | Representa kanban, útil para configuração, integrações e recursos digitais. | kanban, sistema, infraestrutura |
| kanban-destaque | Representa kanban destaque, útil para configuração, integrações e recursos digitais. | kanban-destaque, kanban, destaque, sistema, infraestrutura |
| ladder | Representa ladder, útil para configuração, integrações e recursos digitais. | ladder, sistema, infraestrutura |
| lampada | Representa lampada, útil para configuração, integrações e recursos digitais. | lampada, sistema, infraestrutura |
| lampada-destaque | Representa lampada destaque, útil para configuração, integrações e recursos digitais. | lampada-destaque, lampada, destaque, sistema, infraestrutura |
| lampada-destaque-icon | Representa lampada destaque icon, útil para configuração, integrações e recursos digitais. | lampada-destaque-icon, lampada, destaque, icon, sistema, infraestrutura |
| lampada-icon | Representa lampada icon, útil para configuração, integrações e recursos digitais. | lampada-icon, lampada, icon, sistema, infraestrutura |
| lampada-off | Representa lampada off, útil para configuração, integrações e recursos digitais. | lampada-off, lampada, off, sistema, infraestrutura |
| lampada-off-destaque | Representa lampada off destaque, útil para configuração, integrações e recursos digitais. | lampada-off-destaque, lampada, off, destaque, sistema, infraestrutura |
| lapis-destaque | Representa lapis destaque, útil para configuração, integrações e recursos digitais. | lapis-destaque, lapis, destaque, sistema, infraestrutura |
| layout | Template, composição de página ou estrutura de interface. | layout, visualizacao, template, composicao, pagina, visualização |
| layout-sidebar | Representa layout sidebar, útil para estrutura visual, composição e exibição de interface. | layout-sidebar, layout, sidebar, visualizacao, visualização |
| layout-sidebar-inset | Representa layout sidebar inset, útil para estrutura visual, composição e exibição de interface. | layout-sidebar-inset, layout, sidebar, inset, visualizacao, visualização |
| layout-sidebar-inset-reverse | Representa layout sidebar inset reverse, útil para estrutura visual, composição e exibição de interface. | layout-sidebar-inset-reverse, layout, sidebar, inset, reverse, visualização |
| layout-sidebar-reverse | Representa layout sidebar reverse, útil para estrutura visual, composição e exibição de interface. | layout-sidebar-reverse, layout, sidebar, reverse, visualizacao, visualização |
| layout-split | Representa layout split, útil para estrutura visual, composição e exibição de interface. | layout-split, layout, split, visualizacao, visualização |
| layout-texto-janela-reverse | Representa layout texto janela reverse, útil para estrutura visual, composição e exibição de interface. | layout-texto-janela-reverse, layout, texto, janela, reverse, visualização |
| layout-texto-sidebar | Representa layout texto sidebar, útil para estrutura visual, composição e exibição de interface. | layout-texto-sidebar, layout, texto, sidebar, visualizacao, visualização |
| layout-texto-sidebar-reverse | Representa layout texto sidebar reverse, útil para estrutura visual, composição e exibição de interface. | layout-texto-sidebar-reverse, layout, texto, sidebar, reverse, visualização |
| layout-three-colunas | Representa layout three colunas, útil para estrutura visual, composição e exibição de interface. | layout-three-colunas, layout, three, colunas, visualizacao, visualização |
| layout-wtf | Representa layout wtf, útil para estrutura visual, composição e exibição de interface. | layout-wtf, layout, wtf, visualizacao, visualização |
| leaf | Representa leaf, útil para configuração, integrações e recursos digitais. | leaf, sistema, infraestrutura |
| leaf-destaque | Representa leaf destaque, útil para configuração, integrações e recursos digitais. | leaf-destaque, leaf, destaque, sistema, infraestrutura |
| lembrete | Representa lembrete, útil para configuração, integrações e recursos digitais. | lembrete, sistema, infraestrutura |
| lembrete-destaque | Representa lembrete destaque, útil para configuração, integrações e recursos digitais. | lembrete-destaque, lembrete, destaque, sistema, infraestrutura |
| lembretes | Representa lembretes, útil para configuração, integrações e recursos digitais. | lembretes, sistema, infraestrutura |
| lembretes-destaque | Representa lembretes destaque, útil para configuração, integrações e recursos digitais. | lembretes-destaque, lembretes, destaque, sistema, infraestrutura |
| letra-c-circulo | Representa letra c circulo, útil para configuração, integrações e recursos digitais. | letra-c-circulo, letra, circulo, sistema, infraestrutura, c |
| letra-c-circulo-destaque | Representa letra c circulo destaque, útil para configuração, integrações e recursos digitais. | letra-c-circulo-destaque, letra, circulo, destaque, sistema, c, infraestrutura |
| letra-c-quadrado | Representa letra c quadrado, útil para configuração, integrações e recursos digitais. | letra-c-quadrado, letra, quadrado, sistema, infraestrutura, c |
| letra-c-quadrado-destaque | Representa letra c quadrado destaque, útil para configuração, integrações e recursos digitais. | letra-c-quadrado-destaque, letra, quadrado, destaque, sistema, c, infraestrutura |
| letra-p-circulo | Representa letra p circulo, útil para configuração, integrações e recursos digitais. | letra-p-circulo, letra, circulo, sistema, infraestrutura, p |
| letra-p-circulo-destaque | Representa letra p circulo destaque, útil para configuração, integrações e recursos digitais. | letra-p-circulo-destaque, letra, circulo, destaque, sistema, p, infraestrutura |
| letra-p-quadrado | Representa letra p quadrado, útil para configuração, integrações e recursos digitais. | letra-p-quadrado, letra, quadrado, sistema, infraestrutura, p |
| letra-p-quadrado-destaque | Representa letra p quadrado destaque, útil para configuração, integrações e recursos digitais. | letra-p-quadrado-destaque, letra, quadrado, destaque, sistema, p, infraestrutura |
| letra-r-circulo | Representa letra r circulo, útil para configuração, integrações e recursos digitais. | letra-r-circulo, letra, circulo, sistema, infraestrutura, r |
| letra-r-circulo-destaque | Representa letra r circulo destaque, útil para configuração, integrações e recursos digitais. | letra-r-circulo-destaque, letra, circulo, destaque, sistema, r, infraestrutura |
| letra-r-quadrado | Representa letra r quadrado, útil para configuração, integrações e recursos digitais. | letra-r-quadrado, letra, quadrado, sistema, infraestrutura, r |
| letra-r-quadrado-destaque | Representa letra r quadrado destaque, útil para configuração, integrações e recursos digitais. | letra-r-quadrado-destaque, letra, quadrado, destaque, sistema, r, infraestrutura |
| letra-x-circulo-destaque | Representa letra x circulo destaque, útil para configuração, integrações e recursos digitais. | letra-x-circulo-destaque, letra, circulo, destaque, sistema, x, infraestrutura |
| letra-x-quadrado | Representa letra x quadrado, útil para configuração, integrações e recursos digitais. | letra-x-quadrado, letra, quadrado, sistema, infraestrutura, x |
| letra-x-quadrado-destaque | Representa letra x quadrado destaque, útil para configuração, integrações e recursos digitais. | letra-x-quadrado-destaque, letra, quadrado, destaque, sistema, x, infraestrutura |
| line | Representa line, útil para configuração, integrações e recursos digitais. | line, sistema, infraestrutura |
| linha-horizontal | Representa linha horizontal, útil para configuração, integrações e recursos digitais. | linha-horizontal, linha, horizontal, sistema, infraestrutura |
| link | Representa link, útil para navegação, direção e fluxo de interface. | link, navegacao, fluxo, navegação |
| link-externo | Link, conexao externa ou navegacao para fora. | link-externo, link, externo, navegacao, fluxo, navegação |
| linkedin | Representa linkedin, útil para configuração, integrações e recursos digitais. | linkedin, sistema, infraestrutura |
| lista | Lista linear, menu textual ou itens sequenciais. | lista, sistema, infraestrutura, linear, menu |
| lista-colunas | Representa lista colunas, útil para estrutura visual, composição e exibição de interface. | lista-colunas, lista, colunas, layout, visualizacao, visualização |
| lista-colunas-reverse | Representa lista colunas reverse, útil para estrutura visual, composição e exibição de interface. | lista-colunas-reverse, lista, colunas, reverse, layout, visualização |
| lista-confirmado | Representa lista confirmado, útil para feedback visual, status e comunicação de estado. | lista-confirmado, lista, confirmado, status, estado, estados |
| lista-estrelas | Representa lista estrelas, útil para estrutura visual, composição e exibição de interface. | lista-estrelas, lista, estrelas, layout, visualizacao, visualização |
| lista-nested | Representa lista nested, útil para estrutura visual, composição e exibição de interface. | lista-nested, lista, nested, layout, visualizacao, visualização |
| lista-ol | Representa lista ol, útil para estrutura visual, composição e exibição de interface. | lista-ol, lista, layout, visualizacao, ol, visualização |
| lista-task | Representa lista task, útil para estrutura visual, composição e exibição de interface. | lista-task, lista, task, layout, visualizacao, visualização |
| lista-ul | Representa lista ul, útil para estrutura visual, composição e exibição de interface. | lista-ul, lista, layout, visualizacao, ul, visualização |
| livro-destaque | Representa livro destaque, útil para educação, referência e organização de conhecimento. | livro-destaque, livro, destaque, aprendizado, conhecimento |
| livro-half | Representa livro half, útil para educação, referência e organização de conhecimento. | livro-half, livro, half, aprendizado, conhecimento |
| lixeira-destaque | Representa lixeira destaque, útil para configuração, integrações e recursos digitais. | lixeira-destaque, lixeira, destaque, sistema, infraestrutura |
| localizacao | Representa localizacao, útil para configuração, integrações e recursos digitais. | localizacao, sistema, infraestrutura |
| localizacao-alternativo | Representa localizacao alternativo, útil para configuração, integrações e recursos digitais. | localizacao-alternativo, localizacao, alternativo, sistema, infraestrutura |
| localizacao-alternativo-destaque | Representa localizacao alternativo destaque, útil para configuração, integrações e recursos digitais. | localizacao-alternativo-destaque, localizacao, alternativo, destaque, sistema, infraestrutura |
| localizacao-destaque | Representa localizacao destaque, útil para configuração, integrações e recursos digitais. | localizacao-destaque, localizacao, destaque, sistema, infraestrutura |
| loja | Loja, catalogo comercial ou frente de venda. | loja, compra, pedido, catalogo, comercial, comércio, faturamento |
| loja-janela | Representa loja janela, útil para compras, vendas, cobrança e contexto financeiro. | loja-janela, loja, janela, compra, pedido, comércio, faturamento |
| losango | Representa losango, útil para configuração, integrações e recursos digitais. | losango, sistema, infraestrutura |
| losango-destaque | Representa losango destaque, útil para configuração, integrações e recursos digitais. | losango-destaque, losango, destaque, sistema, infraestrutura |
| losango-half | Representa losango half, útil para configuração, integrações e recursos digitais. | losango-half, losango, half, sistema, infraestrutura |
| lua | Representa lua, útil para configuração, integrações e recursos digitais. | lua, sistema, infraestrutura |
| lua-destaque | Representa lua destaque, útil para configuração, integrações e recursos digitais. | lua-destaque, lua, destaque, sistema, infraestrutura |
| lua-estrelas | Representa lua estrelas, útil para configuração, integrações e recursos digitais. | lua-estrelas, lua, estrelas, sistema, infraestrutura |
| lua-estrelas-destaque | Representa lua estrelas destaque, útil para configuração, integrações e recursos digitais. | lua-estrelas-destaque, lua, estrelas, destaque, sistema, infraestrutura |
| magic | Representa magic, útil para configuração, integrações e recursos digitais. | magic, sistema, infraestrutura |
| mailbox2 | Representa mailbox2, útil para configuração, integrações e recursos digitais. | mailbox2, sistema, infraestrutura |
| mailbox2-bandeira | Representa mailbox2 bandeira, útil para configuração, integrações e recursos digitais. | mailbox2-bandeira, mailbox2, bandeira, sistema, infraestrutura |
| mala | Representa mala, útil para configuração, integrações e recursos digitais. | mala, sistema, infraestrutura |
| mala-destaque | Representa mala destaque, útil para configuração, integrações e recursos digitais. | mala-destaque, mala, destaque, sistema, infraestrutura |
| mala-lg | Representa mala lg, útil para configuração, integrações e recursos digitais. | mala-lg, mala, sistema, infraestrutura, lg |
| mala-lg-destaque | Representa mala lg destaque, útil para configuração, integrações e recursos digitais. | mala-lg-destaque, mala, destaque, sistema, infraestrutura, lg |
| maleta | Representa maleta, útil para configuração, integrações e recursos digitais. | maleta, sistema, infraestrutura |
| maleta-destaque | Representa maleta destaque, útil para configuração, integrações e recursos digitais. | maleta-destaque, maleta, destaque, sistema, infraestrutura |
| manual | Base de conhecimento, guia, manual ou documentacao. | manual, arquivo, documento, base, conhecimento, arquivos, mídia |
| mao-index | Representa mao index, útil para configuração, integrações e recursos digitais. | mao-index, mao, index, sistema, infraestrutura |
| mao-index-destaque | Representa mao index destaque, útil para configuração, integrações e recursos digitais. | mao-index-destaque, mao, index, destaque, sistema, infraestrutura |
| mao-index-thumb | Representa mao index thumb, útil para configuração, integrações e recursos digitais. | mao-index-thumb, mao, index, thumb, sistema, infraestrutura |
| mao-index-thumb-destaque | Representa mao index thumb destaque, útil para configuração, integrações e recursos digitais. | mao-index-thumb-destaque, mao, index, thumb, destaque, sistema, infraestrutura |
| mao-thumbs-baixo | Representa mao thumbs baixo, útil para navegação, direção e fluxo de interface. | mao-thumbs-baixo, mao, thumbs, baixo, navegacao, navegação |
| mao-thumbs-baixo-destaque | Representa mao thumbs baixo destaque, útil para navegação, direção e fluxo de interface. | mao-thumbs-baixo-destaque, mao, thumbs, baixo, destaque, navegação |
| mao-thumbs-cima | Representa mao thumbs cima, útil para navegação, direção e fluxo de interface. | mao-thumbs-cima, mao, thumbs, cima, navegacao, navegação |
| mao-thumbs-cima-destaque | Representa mao thumbs cima destaque, útil para navegação, direção e fluxo de interface. | mao-thumbs-cima-destaque, mao, thumbs, cima, destaque, navegação |
| map | Representa map, útil para configuração, integrações e recursos digitais. | map, sistema, infraestrutura |
| map-destaque | Representa map destaque, útil para configuração, integrações e recursos digitais. | map-destaque, map, destaque, sistema, infraestrutura |
| marcador | Representa marcador, útil para configuração, integrações e recursos digitais. | marcador, sistema, infraestrutura |
| marcador-adicionar | Representa marcador adicionar, útil para ações, comandos e interações diretas na interface. | marcador-adicionar, marcador, adicionar, acao, comando, ações |
| marcador-adicionar-destaque | Representa marcador adicionar destaque, útil para ações, comandos e interações diretas na interface. | marcador-adicionar-destaque, marcador, adicionar, destaque, acao, ações |
| marcador-confirmado | Representa marcador confirmado, útil para feedback visual, status e comunicação de estado. | marcador-confirmado, marcador, confirmado, status, estado, estados |
| marcador-confirmado-destaque | Representa marcador confirmado destaque, útil para feedback visual, status e comunicação de estado. | marcador-confirmado-destaque, marcador, confirmado, destaque, status, estados |
| marcador-coracao | Representa marcador coracao, útil para configuração, integrações e recursos digitais. | marcador-coracao, marcador, coracao, sistema, infraestrutura |
| marcador-coracao-destaque | Representa marcador coracao destaque, útil para configuração, integrações e recursos digitais. | marcador-coracao-destaque, marcador, coracao, destaque, sistema, infraestrutura |
| marcador-destaque | Representa marcador destaque, útil para configuração, integrações e recursos digitais. | marcador-destaque, marcador, destaque, sistema, infraestrutura |
| marcador-estrela-destaque | Representa marcador estrela destaque, útil para feedback visual, status e comunicação de estado. | marcador-estrela-destaque, marcador, estrela, destaque, status, estados |
| marcador-menos | Representa marcador menos, útil para configuração, integrações e recursos digitais. | marcador-menos, marcador, menos, sistema, infraestrutura |
| marcador-menos-destaque | Representa marcador menos destaque, útil para configuração, integrações e recursos digitais. | marcador-menos-destaque, marcador, menos, destaque, sistema, infraestrutura |
| marcador-remover | Representa marcador remover, útil para ações, comandos e interações diretas na interface. | marcador-remover, marcador, remover, acao, comando, ações |
| marcador-remover-destaque | Representa marcador remover destaque, útil para ações, comandos e interações diretas na interface. | marcador-remover-destaque, marcador, remover, destaque, acao, ações |
| marcar | Confirmação simples, marcar ou validar item unico. | marcar, acao, comando, confirmacao, validar, ações |
| markdown | Representa markdown, útil para configuração, integrações e recursos digitais. | markdown, sistema, infraestrutura |
| markdown-destaque | Representa markdown destaque, útil para configuração, integrações e recursos digitais. | markdown-destaque, markdown, destaque, sistema, infraestrutura |
| marker-tip | Representa marker tip, útil para configuração, integrações e recursos digitais. | marker-tip, marker, tip, sistema, infraestrutura |
| martelo | Representa martelo, útil para configuração, integrações e recursos digitais. | martelo, sistema, infraestrutura |
| mascara | Representa mascara, útil para configuração, integrações e recursos digitais. | mascara, sistema, infraestrutura |
| mastodon | Representa mastodon, útil para configuração, integrações e recursos digitais. | mastodon, sistema, infraestrutura |
| medidor-copo | Representa medidor copo, útil para configuração, integrações e recursos digitais. | medidor-copo, medidor, copo, sistema, infraestrutura |
| medidor-copo-destaque | Representa medidor copo destaque, útil para configuração, integrações e recursos digitais. | medidor-copo-destaque, medidor, copo, destaque, sistema, infraestrutura |
| medium | Representa medium, útil para configuração, integrações e recursos digitais. | medium, sistema, infraestrutura |
| megaphone | Representa megaphone, útil para configuração, integrações e recursos digitais. | megaphone, sistema, infraestrutura |
| megaphone-destaque | Representa megaphone destaque, útil para configuração, integrações e recursos digitais. | megaphone-destaque, megaphone, destaque, sistema, infraestrutura |
| memoria | Memória, recurso técnico ou capacidade computacional. | memoria, sistema, infraestrutura, recurso, tecnico, memória |
| menos | Representa menos, útil para configuração, integrações e recursos digitais. | menos, sistema, infraestrutura |
| menos-circulo | Representa menos circulo, útil para configuração, integrações e recursos digitais. | menos-circulo, menos, circulo, sistema, infraestrutura |
| menos-circulo-destaque | Representa menos circulo destaque, útil para configuração, integrações e recursos digitais. | menos-circulo-destaque, menos, circulo, destaque, sistema, infraestrutura |
| menos-circulo-dotted | Representa menos circulo dotted, útil para configuração, integrações e recursos digitais. | menos-circulo-dotted, menos, circulo, dotted, sistema, infraestrutura |
| menos-lg | Representa menos lg, útil para configuração, integrações e recursos digitais. | menos-lg, menos, sistema, infraestrutura, lg |
| menos-quadrado | Representa menos quadrado, útil para configuração, integrações e recursos digitais. | menos-quadrado, menos, quadrado, sistema, infraestrutura |
| menos-quadrado-destaque | Representa menos quadrado destaque, útil para configuração, integrações e recursos digitais. | menos-quadrado-destaque, menos, quadrado, destaque, sistema, infraestrutura |
| menos-quadrado-dotted | Representa menos quadrado dotted, útil para configuração, integrações e recursos digitais. | menos-quadrado-dotted, menos, quadrado, dotted, sistema, infraestrutura |
| mensagem | Envio de mensagem, rascunho ou correspondência ativa. | mensagem, contato, envio, rascunho, correspondencia, comunicação |
| menu-app | Representa menu app, útil para navegação, direção e fluxo de interface. | menu-app, menu, app, navegacao, fluxo, navegação |
| menu-app-destaque | Representa menu app destaque, útil para navegação, direção e fluxo de interface. | menu-app-destaque, menu, app, destaque, navegacao, navegação |
| menu-baixo | Representa menu baixo, útil para navegação, direção e fluxo de interface. | menu-baixo, menu, baixo, navegacao, fluxo, navegação |
| menu-button | Representa menu button, útil para navegação, direção e fluxo de interface. | menu-button, menu, button, navegacao, fluxo, navegação |
| menu-button-destaque | Representa menu button destaque, útil para navegação, direção e fluxo de interface. | menu-button-destaque, menu, button, destaque, navegacao, navegação |
| menu-button-wide | Representa menu button wide, útil para navegação, direção e fluxo de interface. | menu-button-wide, menu, button, wide, navegacao, navegação |
| menu-button-wide-destaque | Representa menu button wide destaque, útil para navegação, direção e fluxo de interface. | menu-button-wide-destaque, menu, button, wide, destaque, navegação |
| menu-cima | Representa menu cima, útil para navegação, direção e fluxo de interface. | menu-cima, menu, cima, navegacao, fluxo, navegação |
| messenger | Representa messenger, útil para configuração, integrações e recursos digitais. | messenger, sistema, infraestrutura |
| meta | Representa meta, útil para configuração, integrações e recursos digitais. | meta, sistema, infraestrutura |
| microfone | Representa microfone, útil para configuração, integrações e recursos digitais. | microfone, sistema, infraestrutura |
| microfone-destaque | Representa microfone destaque, útil para configuração, integrações e recursos digitais. | microfone-destaque, microfone, destaque, sistema, infraestrutura |
| microfone-mute | Representa microfone mute, útil para configuração, integrações e recursos digitais. | microfone-mute, microfone, mute, sistema, infraestrutura |
| microfone-mute-destaque | Representa microfone mute destaque, útil para configuração, integrações e recursos digitais. | microfone-mute-destaque, microfone, mute, destaque, sistema, infraestrutura |
| microsoft | Representa microsoft, útil para configuração, integrações e recursos digitais. | microsoft, sistema, infraestrutura |
| microsoft-teams | Representa microsoft teams, útil para configuração, integrações e recursos digitais. | microsoft-teams, microsoft, teams, sistema, infraestrutura |
| midia | Biblioteca de mídia ativa, playlist ou conteúdo reproduzivel. | midia, arquivo, documento, biblioteca, ativa, mídia, arquivos |
| modem | Representa modem, útil para configuração, integrações e recursos digitais. | modem, sistema, infraestrutura |
| modem-destaque | Representa modem destaque, útil para configuração, integrações e recursos digitais. | modem-destaque, modem, destaque, sistema, infraestrutura |
| moeda | Representa moeda, útil para configuração, integrações e recursos digitais. | moeda, sistema, infraestrutura |
| moisture | Representa moisture, útil para configuração, integrações e recursos digitais. | moisture, sistema, infraestrutura |
| mortarboard-destaque | Representa mortarboard destaque, útil para configuração, integrações e recursos digitais. | mortarboard-destaque, mortarboard, destaque, sistema, infraestrutura |
| motherboard | Representa motherboard, útil para configuração, integrações e recursos digitais. | motherboard, sistema, infraestrutura |
| motherboard-destaque | Representa motherboard destaque, útil para configuração, integrações e recursos digitais. | motherboard-destaque, motherboard, destaque, sistema, infraestrutura |
| mouse | Representa mouse, útil para configuração, integrações e recursos digitais. | mouse, sistema, infraestrutura |
| mouse-destaque | Representa mouse destaque, útil para configuração, integrações e recursos digitais. | mouse-destaque, mouse, destaque, sistema, infraestrutura |
| mouse2 | Representa mouse2, útil para configuração, integrações e recursos digitais. | mouse2, sistema, infraestrutura |
| mouse2-destaque | Representa mouse2 destaque, útil para configuração, integrações e recursos digitais. | mouse2-destaque, mouse2, destaque, sistema, infraestrutura |
| mouse3 | Representa mouse3, útil para configuração, integrações e recursos digitais. | mouse3, sistema, infraestrutura |
| mouse3-destaque | Representa mouse3 destaque, útil para configuração, integrações e recursos digitais. | mouse3-destaque, mouse3, destaque, sistema, infraestrutura |
| musica-note | Representa musica note, útil para configuração, integrações e recursos digitais. | musica-note, musica, note, sistema, infraestrutura |
| musica-note-beamed | Representa musica note beamed, útil para configuração, integrações e recursos digitais. | musica-note-beamed, musica, note, beamed, sistema, infraestrutura |
| musica-note-lista | Representa musica note lista, útil para estrutura visual, composição e exibição de interface. | musica-note-lista, musica, note, lista, layout, visualização |
| musica-player | Representa musica player, útil para configuração, integrações e recursos digitais. | musica-player, musica, player, sistema, infraestrutura |
| musica-player-destaque | Representa musica player destaque, útil para configuração, integrações e recursos digitais. | musica-player-destaque, musica, player, destaque, sistema, infraestrutura |
| navegador-chrome | Representa navegador chrome, útil para configuração, integrações e recursos digitais. | navegador-chrome, navegador, chrome, sistema, infraestrutura |
| navegador-edge | Representa navegador edge, útil para configuração, integrações e recursos digitais. | navegador-edge, navegador, edge, sistema, infraestrutura |
| navegador-firefox | Representa navegador firefox, útil para configuração, integrações e recursos digitais. | navegador-firefox, navegador, firefox, sistema, infraestrutura |
| navegador-safari | Representa navegador safari, útil para configuração, integrações e recursos digitais. | navegador-safari, navegador, safari, sistema, infraestrutura |
| neve | Representa neve, útil para configuração, integrações e recursos digitais. | neve, sistema, infraestrutura |
| nintendo-switch | Representa nintendo switch, útil para configuração, integrações e recursos digitais. | nintendo-switch, nintendo, switch, sistema, infraestrutura |
| node-adicionar-destaque | Representa node adicionar destaque, útil para ações, comandos e interações diretas na interface. | node-adicionar-destaque, node, adicionar, destaque, acao, ações |
| node-minus | Representa node minus, útil para configuração, integrações e recursos digitais. | node-minus, node, minus, sistema, infraestrutura |
| node-minus-destaque | Representa node minus destaque, útil para configuração, integrações e recursos digitais. | node-minus-destaque, node, minus, destaque, sistema, infraestrutura |
| noise-reduction | Representa noise reduction, útil para configuração, integrações e recursos digitais. | noise-reduction, noise, reduction, sistema, infraestrutura |
| notebook | Representa notebook, útil para configuração, integrações e recursos digitais. | notebook, sistema, infraestrutura |
| notebook-destaque | Representa notebook destaque, útil para configuração, integrações e recursos digitais. | notebook-destaque, notebook, destaque, sistema, infraestrutura |
| notificacoes | Alertas, notificações e eventos pendentes. | notificacoes, mensagem, contato, alertas, eventos, notificações, comunicação |
| numero-0-circulo | Representa numero 0 circulo, útil para configuração, integrações e recursos digitais. | numero-0-circulo, numero, circulo, sistema, infraestrutura, 0 |
| numero-0-circulo-destaque | Representa numero 0 circulo destaque, útil para configuração, integrações e recursos digitais. | numero-0-circulo-destaque, numero, circulo, destaque, sistema, 0, infraestrutura |
| numero-0-quadrado | Representa numero 0 quadrado, útil para configuração, integrações e recursos digitais. | numero-0-quadrado, numero, quadrado, sistema, infraestrutura, 0 |
| numero-0-quadrado-destaque | Representa numero 0 quadrado destaque, útil para configuração, integrações e recursos digitais. | numero-0-quadrado-destaque, numero, quadrado, destaque, sistema, 0, infraestrutura |
| numero-1-circulo | Representa numero 1 circulo, útil para configuração, integrações e recursos digitais. | numero-1-circulo, numero, circulo, sistema, infraestrutura, 1 |
| numero-1-circulo-destaque | Representa numero 1 circulo destaque, útil para configuração, integrações e recursos digitais. | numero-1-circulo-destaque, numero, circulo, destaque, sistema, 1, infraestrutura |
| numero-1-quadrado | Representa numero 1 quadrado, útil para configuração, integrações e recursos digitais. | numero-1-quadrado, numero, quadrado, sistema, infraestrutura, 1 |
| numero-1-quadrado-destaque | Representa numero 1 quadrado destaque, útil para configuração, integrações e recursos digitais. | numero-1-quadrado-destaque, numero, quadrado, destaque, sistema, 1, infraestrutura |
| numero-2-circulo | Representa numero 2 circulo, útil para configuração, integrações e recursos digitais. | numero-2-circulo, numero, circulo, sistema, infraestrutura, 2 |
| numero-2-circulo-destaque | Representa numero 2 circulo destaque, útil para configuração, integrações e recursos digitais. | numero-2-circulo-destaque, numero, circulo, destaque, sistema, 2, infraestrutura |
| numero-2-quadrado | Representa numero 2 quadrado, útil para configuração, integrações e recursos digitais. | numero-2-quadrado, numero, quadrado, sistema, infraestrutura, 2 |
| numero-2-quadrado-destaque | Representa numero 2 quadrado destaque, útil para configuração, integrações e recursos digitais. | numero-2-quadrado-destaque, numero, quadrado, destaque, sistema, 2, infraestrutura |
| numero-3-circulo | Representa numero 3 circulo, útil para configuração, integrações e recursos digitais. | numero-3-circulo, numero, circulo, sistema, infraestrutura, 3 |
| numero-3-circulo-destaque | Representa numero 3 circulo destaque, útil para configuração, integrações e recursos digitais. | numero-3-circulo-destaque, numero, circulo, destaque, sistema, 3, infraestrutura |
| numero-3-quadrado | Representa numero 3 quadrado, útil para configuração, integrações e recursos digitais. | numero-3-quadrado, numero, quadrado, sistema, infraestrutura, 3 |
| numero-3-quadrado-destaque | Representa numero 3 quadrado destaque, útil para configuração, integrações e recursos digitais. | numero-3-quadrado-destaque, numero, quadrado, destaque, sistema, 3, infraestrutura |
| numero-4-circulo | Representa numero 4 circulo, útil para configuração, integrações e recursos digitais. | numero-4-circulo, numero, circulo, sistema, infraestrutura, 4 |
| numero-4-circulo-destaque | Representa numero 4 circulo destaque, útil para configuração, integrações e recursos digitais. | numero-4-circulo-destaque, numero, circulo, destaque, sistema, 4, infraestrutura |
| numero-4-quadrado | Representa numero 4 quadrado, útil para configuração, integrações e recursos digitais. | numero-4-quadrado, numero, quadrado, sistema, infraestrutura, 4 |
| numero-4-quadrado-destaque | Representa numero 4 quadrado destaque, útil para configuração, integrações e recursos digitais. | numero-4-quadrado-destaque, numero, quadrado, destaque, sistema, 4, infraestrutura |
| numero-5-circulo | Representa numero 5 circulo, útil para configuração, integrações e recursos digitais. | numero-5-circulo, numero, circulo, sistema, infraestrutura, 5 |
| numero-5-circulo-destaque | Representa numero 5 circulo destaque, útil para configuração, integrações e recursos digitais. | numero-5-circulo-destaque, numero, circulo, destaque, sistema, 5, infraestrutura |
| numero-5-quadrado | Representa numero 5 quadrado, útil para configuração, integrações e recursos digitais. | numero-5-quadrado, numero, quadrado, sistema, infraestrutura, 5 |
| numero-5-quadrado-destaque | Representa numero 5 quadrado destaque, útil para configuração, integrações e recursos digitais. | numero-5-quadrado-destaque, numero, quadrado, destaque, sistema, 5, infraestrutura |
| numero-6-circulo | Representa numero 6 circulo, útil para configuração, integrações e recursos digitais. | numero-6-circulo, numero, circulo, sistema, infraestrutura, 6 |
| numero-6-circulo-destaque | Representa numero 6 circulo destaque, útil para configuração, integrações e recursos digitais. | numero-6-circulo-destaque, numero, circulo, destaque, sistema, 6, infraestrutura |
| numero-6-quadrado | Representa numero 6 quadrado, útil para configuração, integrações e recursos digitais. | numero-6-quadrado, numero, quadrado, sistema, infraestrutura, 6 |
| numero-6-quadrado-destaque | Representa numero 6 quadrado destaque, útil para configuração, integrações e recursos digitais. | numero-6-quadrado-destaque, numero, quadrado, destaque, sistema, 6, infraestrutura |
| numero-7-circulo | Representa numero 7 circulo, útil para configuração, integrações e recursos digitais. | numero-7-circulo, numero, circulo, sistema, infraestrutura, 7 |
| numero-7-circulo-destaque | Representa numero 7 circulo destaque, útil para configuração, integrações e recursos digitais. | numero-7-circulo-destaque, numero, circulo, destaque, sistema, 7, infraestrutura |
| numero-7-quadrado | Representa numero 7 quadrado, útil para configuração, integrações e recursos digitais. | numero-7-quadrado, numero, quadrado, sistema, infraestrutura, 7 |
| numero-7-quadrado-destaque | Representa numero 7 quadrado destaque, útil para configuração, integrações e recursos digitais. | numero-7-quadrado-destaque, numero, quadrado, destaque, sistema, 7, infraestrutura |
| numero-8-circulo | Representa numero 8 circulo, útil para configuração, integrações e recursos digitais. | numero-8-circulo, numero, circulo, sistema, infraestrutura, 8 |
| numero-8-circulo-destaque | Representa numero 8 circulo destaque, útil para configuração, integrações e recursos digitais. | numero-8-circulo-destaque, numero, circulo, destaque, sistema, 8, infraestrutura |
| numero-8-quadrado | Representa numero 8 quadrado, útil para configuração, integrações e recursos digitais. | numero-8-quadrado, numero, quadrado, sistema, infraestrutura, 8 |
| numero-8-quadrado-destaque | Representa numero 8 quadrado destaque, útil para configuração, integrações e recursos digitais. | numero-8-quadrado-destaque, numero, quadrado, destaque, sistema, 8, infraestrutura |
| numero-9-circulo | Representa numero 9 circulo, útil para configuração, integrações e recursos digitais. | numero-9-circulo, numero, circulo, sistema, infraestrutura, 9 |
| numero-9-circulo-destaque | Representa numero 9 circulo destaque, útil para configuração, integrações e recursos digitais. | numero-9-circulo-destaque, numero, circulo, destaque, sistema, 9, infraestrutura |
| numero-9-quadrado | Representa numero 9 quadrado, útil para configuração, integrações e recursos digitais. | numero-9-quadrado, numero, quadrado, sistema, infraestrutura, 9 |
| numero-9-quadrado-destaque | Representa numero 9 quadrado destaque, útil para configuração, integrações e recursos digitais. | numero-9-quadrado-destaque, numero, quadrado, destaque, sistema, 9, infraestrutura |
| numeros-123 | Representa numeros 123, útil para configuração, integrações e recursos digitais. | numeros-123, numeros, 123, sistema, infraestrutura |
| nuvem | Representa nuvem, útil para configuração, integrações e recursos digitais. | nuvem, sistema, infraestrutura |
| nuvem-adicionar | Representa nuvem adicionar, útil para ações, comandos e interações diretas na interface. | nuvem-adicionar, nuvem, adicionar, acao, comando, ações |
| nuvem-adicionar-destaque | Representa nuvem adicionar destaque, útil para ações, comandos e interações diretas na interface. | nuvem-adicionar-destaque, nuvem, adicionar, destaque, acao, ações |
| nuvem-baixar | Representa nuvem baixar, útil para ações, comandos e interações diretas na interface. | nuvem-baixar, nuvem, baixar, acao, comando, ações |
| nuvem-baixar-destaque | Representa nuvem baixar destaque, útil para ações, comandos e interações diretas na interface. | nuvem-baixar-destaque, nuvem, baixar, destaque, acao, ações |
| nuvem-confirmado | Representa nuvem confirmado, útil para feedback visual, status e comunicação de estado. | nuvem-confirmado, nuvem, confirmado, status, estado, estados |
| nuvem-confirmado-destaque | Representa nuvem confirmado destaque, útil para feedback visual, status e comunicação de estado. | nuvem-confirmado-destaque, nuvem, confirmado, destaque, status, estados |
| nuvem-cortado | Representa nuvem cortado, útil para configuração, integrações e recursos digitais. | nuvem-cortado, nuvem, cortado, sistema, infraestrutura |
| nuvem-cortado-destaque | Representa nuvem cortado destaque, útil para configuração, integrações e recursos digitais. | nuvem-cortado-destaque, nuvem, cortado, destaque, sistema, infraestrutura |
| nuvem-destaque | Representa nuvem destaque, útil para configuração, integrações e recursos digitais. | nuvem-destaque, nuvem, destaque, sistema, infraestrutura |
| nuvem-drizzle | Representa nuvem drizzle, útil para configuração, integrações e recursos digitais. | nuvem-drizzle, nuvem, drizzle, sistema, infraestrutura |
| nuvem-drizzle-destaque | Representa nuvem drizzle destaque, útil para configuração, integrações e recursos digitais. | nuvem-drizzle-destaque, nuvem, drizzle, destaque, sistema, infraestrutura |
| nuvem-fog | Representa nuvem fog, útil para configuração, integrações e recursos digitais. | nuvem-fog, nuvem, fog, sistema, infraestrutura |
| nuvem-fog-destaque | Representa nuvem fog destaque, útil para configuração, integrações e recursos digitais. | nuvem-fog-destaque, nuvem, fog, destaque, sistema, infraestrutura |
| nuvem-fog2 | Representa nuvem fog2, útil para configuração, integrações e recursos digitais. | nuvem-fog2, nuvem, fog2, sistema, infraestrutura |
| nuvem-fog2-destaque | Representa nuvem fog2 destaque, útil para configuração, integrações e recursos digitais. | nuvem-fog2-destaque, nuvem, fog2, destaque, sistema, infraestrutura |
| nuvem-hail | Representa nuvem hail, útil para configuração, integrações e recursos digitais. | nuvem-hail, nuvem, hail, sistema, infraestrutura |
| nuvem-hail-destaque | Representa nuvem hail destaque, útil para configuração, integrações e recursos digitais. | nuvem-hail-destaque, nuvem, hail, destaque, sistema, infraestrutura |
| nuvem-haze | Representa nuvem haze, útil para configuração, integrações e recursos digitais. | nuvem-haze, nuvem, haze, sistema, infraestrutura |
| nuvem-haze-destaque | Representa nuvem haze destaque, útil para configuração, integrações e recursos digitais. | nuvem-haze-destaque, nuvem, haze, destaque, sistema, infraestrutura |
| nuvem-haze2 | Representa nuvem haze2, útil para configuração, integrações e recursos digitais. | nuvem-haze2, nuvem, haze2, sistema, infraestrutura |
| nuvem-haze2-destaque | Representa nuvem haze2 destaque, útil para configuração, integrações e recursos digitais. | nuvem-haze2-destaque, nuvem, haze2, destaque, sistema, infraestrutura |
| nuvem-lua | Representa nuvem lua, útil para configuração, integrações e recursos digitais. | nuvem-lua, nuvem, lua, sistema, infraestrutura |
| nuvem-lua-destaque | Representa nuvem lua destaque, útil para configuração, integrações e recursos digitais. | nuvem-lua-destaque, nuvem, lua, destaque, sistema, infraestrutura |
| nuvem-minus | Representa nuvem minus, útil para configuração, integrações e recursos digitais. | nuvem-minus, nuvem, minus, sistema, infraestrutura |
| nuvem-minus-destaque | Representa nuvem minus destaque, útil para configuração, integrações e recursos digitais. | nuvem-minus-destaque, nuvem, minus, destaque, sistema, infraestrutura |
| nuvem-neve | Representa nuvem neve, útil para configuração, integrações e recursos digitais. | nuvem-neve, nuvem, neve, sistema, infraestrutura |
| nuvem-neve-destaque | Representa nuvem neve destaque, útil para configuração, integrações e recursos digitais. | nuvem-neve-destaque, nuvem, neve, destaque, sistema, infraestrutura |
| nuvem-rain | Representa nuvem rain, útil para configuração, integrações e recursos digitais. | nuvem-rain, nuvem, rain, sistema, infraestrutura |
| nuvem-rain-destaque | Representa nuvem rain destaque, útil para configuração, integrações e recursos digitais. | nuvem-rain-destaque, nuvem, rain, destaque, sistema, infraestrutura |
| nuvem-rain-heavy | Representa nuvem rain heavy, útil para configuração, integrações e recursos digitais. | nuvem-rain-heavy, nuvem, rain, heavy, sistema, infraestrutura |
| nuvem-rain-heavy-destaque | Representa nuvem rain heavy destaque, útil para configuração, integrações e recursos digitais. | nuvem-rain-heavy-destaque, nuvem, rain, heavy, destaque, sistema, infraestrutura |
| nuvem-raio | Representa nuvem raio, útil para configuração, integrações e recursos digitais. | nuvem-raio, nuvem, raio, sistema, infraestrutura |
| nuvem-raio-destaque | Representa nuvem raio destaque, útil para configuração, integrações e recursos digitais. | nuvem-raio-destaque, nuvem, raio, destaque, sistema, infraestrutura |
| nuvem-raio-rain | Representa nuvem raio rain, útil para configuração, integrações e recursos digitais. | nuvem-raio-rain, nuvem, raio, rain, sistema, infraestrutura |
| nuvem-raio-rain-destaque | Representa nuvem raio rain destaque, útil para configuração, integrações e recursos digitais. | nuvem-raio-rain-destaque, nuvem, raio, rain, destaque, sistema, infraestrutura |
| nuvem-seta-baixo | Representa nuvem seta baixo, útil para navegação, direção e fluxo de interface. | nuvem-seta-baixo, nuvem, seta, baixo, navegacao, navegação |
| nuvem-seta-baixo-destaque | Representa nuvem seta baixo destaque, útil para navegação, direção e fluxo de interface. | nuvem-seta-baixo-destaque, nuvem, seta, baixo, destaque, navegação |
| nuvem-seta-cima | Representa nuvem seta cima, útil para navegação, direção e fluxo de interface. | nuvem-seta-cima, nuvem, seta, cima, navegacao, navegação |
| nuvem-seta-cima-destaque | Representa nuvem seta cima destaque, útil para navegação, direção e fluxo de interface. | nuvem-seta-cima-destaque, nuvem, seta, cima, destaque, navegação |
| nuvem-sleet | Representa nuvem sleet, útil para configuração, integrações e recursos digitais. | nuvem-sleet, nuvem, sleet, sistema, infraestrutura |
| nuvem-sleet-destaque | Representa nuvem sleet destaque, útil para configuração, integrações e recursos digitais. | nuvem-sleet-destaque, nuvem, sleet, destaque, sistema, infraestrutura |
| nuvem-sol | Representa nuvem sol, útil para configuração, integrações e recursos digitais. | nuvem-sol, nuvem, sol, sistema, infraestrutura |
| nuvem-sol-destaque | Representa nuvem sol destaque, útil para configuração, integrações e recursos digitais. | nuvem-sol-destaque, nuvem, sol, destaque, sistema, infraestrutura |
| nuvem-upload | Representa nuvem upload, útil para configuração, integrações e recursos digitais. | nuvem-upload, nuvem, upload, sistema, infraestrutura |
| nuvem-upload-destaque | Representa nuvem upload destaque, útil para configuração, integrações e recursos digitais. | nuvem-upload-destaque, nuvem, upload, destaque, sistema, infraestrutura |
| nvidia | Representa nvidia, útil para configuração, integrações e recursos digitais. | nvidia, sistema, infraestrutura |
| nvme | Representa nvme, útil para configuração, integrações e recursos digitais. | nvme, sistema, infraestrutura |
| nvme-destaque | Representa nvme destaque, útil para configuração, integrações e recursos digitais. | nvme-destaque, nvme, destaque, sistema, infraestrutura |
| octagon | Representa octagon, útil para configuração, integrações e recursos digitais. | octagon, sistema, infraestrutura |
| octagon-destaque | Representa octagon destaque, útil para configuração, integrações e recursos digitais. | octagon-destaque, octagon, destaque, sistema, infraestrutura |
| octagon-half | Representa octagon half, útil para configuração, integrações e recursos digitais. | octagon-half, octagon, half, sistema, infraestrutura |
| oculos-escuros | Representa oculos escuros, útil para configuração, integrações e recursos digitais. | oculos-escuros, oculos, escuros, sistema, infraestrutura |
| olho-cortado | Representa olho cortado, útil para configuração, integrações e recursos digitais. | olho-cortado, olho, cortado, sistema, infraestrutura |
| olho-cortado-destaque | Representa olho cortado destaque, útil para configuração, integrações e recursos digitais. | olho-cortado-destaque, olho, cortado, destaque, sistema, infraestrutura |
| olho-destaque | Representa olho destaque, útil para configuração, integrações e recursos digitais. | olho-destaque, olho, destaque, sistema, infraestrutura |
| onda-sonora | Representa onda sonora, útil para configuração, integrações e recursos digitais. | onda-sonora, onda, sonora, sistema, infraestrutura |
| onibus-frente | Representa onibus frente, útil para configuração, integrações e recursos digitais. | onibus-frente, onibus, frente, sistema, infraestrutura |
| onibus-frente-destaque | Representa onibus frente destaque, útil para configuração, integrações e recursos digitais. | onibus-frente-destaque, onibus, frente, destaque, sistema, infraestrutura |
| opcao | Representa opcao, útil para configuração, integrações e recursos digitais. | opcao, sistema, infraestrutura |
| opcoes | Preferencias em grade, selecao de opcoes ou matriz configuravel. | opcoes, layout, visualizacao, preferencias, grade, opções, visualização |
| openai | Representa openai, útil para configuração, integrações e recursos digitais. | openai, sistema, infraestrutura |
| opencollective | Representa opencollective, útil para configuração, integrações e recursos digitais. | opencollective, sistema, infraestrutura |
| operador | Usuário com contexto operacional, ownership ou ambiente de trabalho. | operador, usuario, acesso, operacional, ownership, usuários |
| optical-audio | Representa optical audio, útil para configuração, integrações e recursos digitais. | optical-audio, optical, audio, sistema, infraestrutura |
| optical-audio-destaque | Representa optical audio destaque, útil para configuração, integrações e recursos digitais. | optical-audio-destaque, optical, audio, destaque, sistema, infraestrutura |
| orelha | Representa orelha, útil para configuração, integrações e recursos digitais. | orelha, sistema, infraestrutura |
| orelha-destaque | Representa orelha destaque, útil para configuração, integrações e recursos digitais. | orelha-destaque, orelha, destaque, sistema, infraestrutura |
| ortografia | Representa ortografia, útil para configuração, integrações e recursos digitais. | ortografia, sistema, infraestrutura |
| ovo | Representa ovo, útil para configuração, integrações e recursos digitais. | ovo, sistema, infraestrutura |
| ovo-destaque | Representa ovo destaque, útil para configuração, integrações e recursos digitais. | ovo-destaque, ovo, destaque, sistema, infraestrutura |
| ovo-fried | Representa ovo fried, útil para configuração, integrações e recursos digitais. | ovo-fried, ovo, fried, sistema, infraestrutura |
| painel | Grade completa para dashboard, atalhos ou mosaico. | painel, layout, visualizacao, grade, completa, visualização |
| paint-balde | Representa paint balde, útil para configuração, integrações e recursos digitais. | paint-balde, paint, balde, sistema, infraestrutura |
| paleta-destaque | Representa paleta destaque, útil para configuração, integrações e recursos digitais. | paleta-destaque, paleta, destaque, sistema, infraestrutura |
| palette2 | Representa palette2, útil para configuração, integrações e recursos digitais. | palette2, sistema, infraestrutura |
| paragrafo | Representa paragrafo, útil para configuração, integrações e recursos digitais. | paragrafo, sistema, infraestrutura |
| parar | Representa parar, útil para configuração, integrações e recursos digitais. | parar, sistema, infraestrutura |
| parar-btn | Representa parar btn, útil para configuração, integrações e recursos digitais. | parar-btn, parar, btn, sistema, infraestrutura |
| parar-btn-destaque | Representa parar btn destaque, útil para configuração, integrações e recursos digitais. | parar-btn-destaque, parar, btn, destaque, sistema, infraestrutura |
| parar-circulo | Representa parar circulo, útil para configuração, integrações e recursos digitais. | parar-circulo, parar, circulo, sistema, infraestrutura |
| parar-circulo-destaque | Representa parar circulo destaque, útil para configuração, integrações e recursos digitais. | parar-circulo-destaque, parar, circulo, destaque, sistema, infraestrutura |
| parar-destaque | Representa parar destaque, útil para configuração, integrações e recursos digitais. | parar-destaque, parar, destaque, sistema, infraestrutura |
| passaporte | Representa passaporte, útil para configuração, integrações e recursos digitais. | passaporte, sistema, infraestrutura |
| passaporte-destaque | Representa passaporte destaque, útil para configuração, integrações e recursos digitais. | passaporte-destaque, passaporte, destaque, sistema, infraestrutura |
| passe | Representa passe, útil para configuração, integrações e recursos digitais. | passe, sistema, infraestrutura |
| passe-destaque | Representa passe destaque, útil para configuração, integrações e recursos digitais. | passe-destaque, passe, destaque, sistema, infraestrutura |
| pasta | Pasta fechada, agrupamento ou repositorio de itens. | pasta, arquivo, documento, fechada, agrupamento, arquivos, mídia |
| pasta-aberta | Pasta aberta, navegacao em estrutura ou diretório ativo. | pasta-aberta, pasta, aberta, arquivo, documento, arquivos, mídia |
| pasta-adicionar | Representa pasta adicionar, útil para documentos, conteúdo e organização de arquivos. | pasta-adicionar, pasta, adicionar, arquivo, documento, arquivos, mídia |
| pasta-confirmado | Representa pasta confirmado, útil para documentos, conteúdo e organização de arquivos. | pasta-confirmado, pasta, confirmado, arquivo, documento, arquivos, mídia |
| pasta-destaque | Representa pasta destaque, útil para documentos, conteúdo e organização de arquivos. | pasta-destaque, pasta, destaque, arquivo, documento, arquivos, mídia |
| pasta-icon | Representa pasta icon, útil para documentos, conteúdo e organização de arquivos. | pasta-icon, pasta, icon, arquivo, documento, arquivos, mídia |
| pasta-minus | Representa pasta minus, útil para documentos, conteúdo e organização de arquivos. | pasta-minus, pasta, minus, arquivo, documento, arquivos, mídia |
| pasta-remover | Representa pasta remover, útil para documentos, conteúdo e organização de arquivos. | pasta-remover, pasta, remover, arquivo, documento, arquivos, mídia |
| pasta-symlink | Representa pasta symlink, útil para documentos, conteúdo e organização de arquivos. | pasta-symlink, pasta, symlink, arquivo, documento, arquivos, mídia |
| pasta-symlink-destaque | Representa pasta symlink destaque, útil para documentos, conteúdo e organização de arquivos. | pasta-symlink-destaque, pasta, symlink, destaque, arquivo, arquivos, mídia |
| patinete | Representa patinete, útil para configuração, integrações e recursos digitais. | patinete, sistema, infraestrutura |
| pausar | Pausa, suspensão temporaria ou interrupcao controlada. | pausar, acao, comando, pausa, suspensao, ações |
| pausar-btn | Representa pausar btn, útil para ações, comandos e interações diretas na interface. | pausar-btn, pausar, btn, acao, comando, ações |
| pausar-btn-destaque | Representa pausar btn destaque, útil para ações, comandos e interações diretas na interface. | pausar-btn-destaque, pausar, btn, destaque, acao, ações |
| pausar-circulo-destaque | Representa pausar circulo destaque, útil para ações, comandos e interações diretas na interface. | pausar-circulo-destaque, pausar, circulo, destaque, acao, ações |
| pausar-destaque | Representa pausar destaque, útil para ações, comandos e interações diretas na interface. | pausar-destaque, pausar, destaque, acao, comando, ações |
| pausar-icon | Representa pausar icon, útil para ações, comandos e interações diretas na interface. | pausar-icon, pausar, icon, acao, comando, ações |
| paypal | Representa paypal, útil para configuração, integrações e recursos digitais. | paypal, sistema, infraestrutura |
| paz | Representa paz, útil para configuração, integrações e recursos digitais. | paz, sistema, infraestrutura |
| paz-destaque | Representa paz destaque, útil para configuração, integrações e recursos digitais. | paz-destaque, paz, destaque, sistema, infraestrutura |
| pc | Representa pc, útil para configuração, integrações e recursos digitais. | pc, sistema, infraestrutura |
| pc-display | Representa pc display, útil para configuração, integrações e recursos digitais. | pc-display, display, sistema, infraestrutura, pc |
| pc-display-horizontal | Representa pc display horizontal, útil para configuração, integrações e recursos digitais. | pc-display-horizontal, display, horizontal, sistema, infraestrutura, pc |
| pc-horizontal | Representa pc horizontal, útil para configuração, integrações e recursos digitais. | pc-horizontal, horizontal, sistema, infraestrutura, pc |
| pci-card | Representa pci card, útil para configuração, integrações e recursos digitais. | pci-card, pci, card, sistema, infraestrutura |
| pci-card-network | Representa pci card network, útil para configuração, integrações e recursos digitais. | pci-card-network, pci, card, network, sistema, infraestrutura |
| pci-card-sound | Representa pci card sound, útil para configuração, integrações e recursos digitais. | pci-card-sound, pci, card, sound, sistema, infraestrutura |
| pen-drive | Representa pen drive, útil para configuração, integrações e recursos digitais. | pen-drive, pen, drive, sistema, infraestrutura |
| pen-drive-destaque | Representa pen drive destaque, útil para configuração, integrações e recursos digitais. | pen-drive-destaque, pen, drive, destaque, sistema, infraestrutura |
| pentagono | Representa pentagono, útil para configuração, integrações e recursos digitais. | pentagono, sistema, infraestrutura |
| pentagono-destaque | Representa pentagono destaque, útil para configuração, integrações e recursos digitais. | pentagono-destaque, pentagono, destaque, sistema, infraestrutura |
| pentagono-half | Representa pentagono half, útil para configuração, integrações e recursos digitais. | pentagono-half, pentagono, half, sistema, infraestrutura |
| percent | Representa percent, útil para configuração, integrações e recursos digitais. | percent, sistema, infraestrutura |
| perfil | Identidade profissional, credencial ou perfil qualificado. | perfil, usuario, acesso, identidade, profissional, usuários |
| pergunta | Representa pergunta, útil para configuração, integrações e recursos digitais. | pergunta, sistema, infraestrutura |
| pergunta-circulo | Representa pergunta circulo, útil para configuração, integrações e recursos digitais. | pergunta-circulo, pergunta, circulo, sistema, infraestrutura |
| pergunta-circulo-destaque | Representa pergunta circulo destaque, útil para configuração, integrações e recursos digitais. | pergunta-circulo-destaque, pergunta, circulo, destaque, sistema, infraestrutura |
| pergunta-lg | Representa pergunta lg, útil para configuração, integrações e recursos digitais. | pergunta-lg, pergunta, sistema, infraestrutura, lg |
| pergunta-losango | Representa pergunta losango, útil para configuração, integrações e recursos digitais. | pergunta-losango, pergunta, losango, sistema, infraestrutura |
| pergunta-losango-destaque | Representa pergunta losango destaque, útil para configuração, integrações e recursos digitais. | pergunta-losango-destaque, pergunta, losango, destaque, sistema, infraestrutura |
| pergunta-octagon | Representa pergunta octagon, útil para configuração, integrações e recursos digitais. | pergunta-octagon, pergunta, octagon, sistema, infraestrutura |
| pergunta-octagon-destaque | Representa pergunta octagon destaque, útil para configuração, integrações e recursos digitais. | pergunta-octagon-destaque, pergunta, octagon, destaque, sistema, infraestrutura |
| pergunta-quadrado | Representa pergunta quadrado, útil para configuração, integrações e recursos digitais. | pergunta-quadrado, pergunta, quadrado, sistema, infraestrutura |
| pergunta-quadrado-destaque | Representa pergunta quadrado destaque, útil para configuração, integrações e recursos digitais. | pergunta-quadrado-destaque, pergunta, quadrado, destaque, sistema, infraestrutura |
| perplexity | Representa perplexity, útil para configuração, integrações e recursos digitais. | perplexity, sistema, infraestrutura |
| pessoa-add | Representa pessoa add, útil para usuários, identidade, perfis e controle de acesso. | pessoa-add, pessoa, add, usuario, acesso, usuários |
| pessoa-adicionar-destaque | Representa pessoa adicionar destaque, útil para usuários, identidade, perfis e controle de acesso. | pessoa-adicionar-destaque, pessoa, adicionar, destaque, usuario, usuários, acesso |
| pessoa-arms-cima | Representa pessoa arms cima, útil para usuários, identidade, perfis e controle de acesso. | pessoa-arms-cima, pessoa, arms, cima, usuario, usuários, acesso |
| pessoa-baixo | Representa pessoa baixo, útil para usuários, identidade, perfis e controle de acesso. | pessoa-baixo, pessoa, baixo, usuario, acesso, usuários |
| pessoa-bounding-caixa | Representa pessoa bounding caixa, útil para usuários, identidade, perfis e controle de acesso. | pessoa-bounding-caixa, pessoa, bounding, caixa, usuario, usuários, acesso |
| pessoa-cadeado | Representa pessoa cadeado, útil para usuários, identidade, perfis e controle de acesso. | pessoa-cadeado, pessoa, cadeado, usuario, acesso, usuários |
| pessoa-cima | Representa pessoa cima, útil para usuários, identidade, perfis e controle de acesso. | pessoa-cima, pessoa, cima, usuario, acesso, usuários |
| pessoa-confirmado-destaque | Representa pessoa confirmado destaque, útil para usuários, identidade, perfis e controle de acesso. | pessoa-confirmado-destaque, pessoa, confirmado, destaque, usuario, usuários, acesso |
| pessoa-coracao | Representa pessoa coracao, útil para usuários, identidade, perfis e controle de acesso. | pessoa-coracao, pessoa, coracao, usuario, acesso, usuários |
| pessoa-coracoes | Representa pessoa coracoes, útil para usuários, identidade, perfis e controle de acesso. | pessoa-coracoes, pessoa, coracoes, usuario, acesso, usuários |
| pessoa-cortado | Representa pessoa cortado, útil para usuários, identidade, perfis e controle de acesso. | pessoa-cortado, pessoa, cortado, usuario, acesso, usuários |
| pessoa-destaque | Representa pessoa destaque, útil para usuários, identidade, perfis e controle de acesso. | pessoa-destaque, pessoa, destaque, usuario, acesso, usuários |
| pessoa-destaque-add | Representa pessoa destaque add, útil para usuários, identidade, perfis e controle de acesso. | pessoa-destaque-add, pessoa, destaque, add, usuario, usuários, acesso |
| pessoa-destaque-baixo | Representa pessoa destaque baixo, útil para usuários, identidade, perfis e controle de acesso. | pessoa-destaque-baixo, pessoa, destaque, baixo, usuario, usuários, acesso |
| pessoa-destaque-cadeado | Representa pessoa destaque cadeado, útil para usuários, identidade, perfis e controle de acesso. | pessoa-destaque-cadeado, pessoa, destaque, cadeado, usuario, usuários, acesso |
| pessoa-destaque-cima | Representa pessoa destaque cima, útil para usuários, identidade, perfis e controle de acesso. | pessoa-destaque-cima, pessoa, destaque, cima, usuario, usuários, acesso |
| pessoa-destaque-confirmado | Representa pessoa destaque confirmado, útil para usuários, identidade, perfis e controle de acesso. | pessoa-destaque-confirmado, pessoa, destaque, confirmado, usuario, usuários, acesso |
| pessoa-destaque-cortado | Representa pessoa destaque cortado, útil para usuários, identidade, perfis e controle de acesso. | pessoa-destaque-cortado, pessoa, destaque, cortado, usuario, usuários, acesso |
| pessoa-destaque-engrenagem | Representa pessoa destaque engrenagem, útil para usuários, identidade, perfis e controle de acesso. | pessoa-destaque-engrenagem, pessoa, destaque, engrenagem, usuario, usuários, acesso |
| pessoa-destaque-exclamacao | Representa pessoa destaque exclamacao, útil para usuários, identidade, perfis e controle de acesso. | pessoa-destaque-exclamacao, pessoa, destaque, exclamacao, usuario, usuários, acesso |
| pessoa-destaque-menos | Representa pessoa destaque menos, útil para usuários, identidade, perfis e controle de acesso. | pessoa-destaque-menos, pessoa, destaque, menos, usuario, usuários, acesso |
| pessoa-destaque-remover | Representa pessoa destaque remover, útil para usuários, identidade, perfis e controle de acesso. | pessoa-destaque-remover, pessoa, destaque, remover, usuario, usuários, acesso |
| pessoa-engrenagem | Representa pessoa engrenagem, útil para usuários, identidade, perfis e controle de acesso. | pessoa-engrenagem, pessoa, engrenagem, usuario, acesso, usuários |
| pessoa-exclamacao | Representa pessoa exclamacao, útil para usuários, identidade, perfis e controle de acesso. | pessoa-exclamacao, pessoa, exclamacao, usuario, acesso, usuários |
| pessoa-menos | Representa pessoa menos, útil para usuários, identidade, perfis e controle de acesso. | pessoa-menos, pessoa, menos, usuario, acesso, usuários |
| pessoa-menos-destaque | Representa pessoa menos destaque, útil para usuários, identidade, perfis e controle de acesso. | pessoa-menos-destaque, pessoa, menos, destaque, usuario, usuários, acesso |
| pessoa-quadrado | Representa pessoa quadrado, útil para usuários, identidade, perfis e controle de acesso. | pessoa-quadrado, pessoa, quadrado, usuario, acesso, usuários |
| pessoa-raised-mao | Representa pessoa raised mao, útil para usuários, identidade, perfis e controle de acesso. | pessoa-raised-mao, pessoa, raised, mao, usuario, usuários, acesso |
| pessoa-remover | Representa pessoa remover, útil para usuários, identidade, perfis e controle de acesso. | pessoa-remover, pessoa, remover, usuario, acesso, usuários |
| pessoa-remover-destaque | Representa pessoa remover destaque, útil para usuários, identidade, perfis e controle de acesso. | pessoa-remover-destaque, pessoa, remover, destaque, usuario, usuários, acesso |
| pessoa-rolodex | Representa pessoa rolodex, útil para usuários, identidade, perfis e controle de acesso. | pessoa-rolodex, pessoa, rolodex, usuario, acesso, usuários |
| pessoa-selo-destaque | Representa pessoa selo destaque, útil para usuários, identidade, perfis e controle de acesso. | pessoa-selo-destaque, pessoa, selo, destaque, usuario, usuários, acesso |
| pessoa-standing | Representa pessoa standing, útil para usuários, identidade, perfis e controle de acesso. | pessoa-standing, pessoa, standing, usuario, acesso, usuários |
| pessoa-standing-dress | Representa pessoa standing dress, útil para usuários, identidade, perfis e controle de acesso. | pessoa-standing-dress, pessoa, standing, dress, usuario, usuários, acesso |
| pessoa-vcard | Representa pessoa vcard, útil para usuários, identidade, perfis e controle de acesso. | pessoa-vcard, pessoa, vcard, usuario, acesso, usuários |
| pessoa-vcard-destaque | Representa pessoa vcard destaque, útil para usuários, identidade, perfis e controle de acesso. | pessoa-vcard-destaque, pessoa, vcard, destaque, usuario, usuários, acesso |
| pessoa-video | Representa pessoa video, útil para documentos, conteúdo e organização de arquivos. | pessoa-video, pessoa, video, arquivo, documento, arquivos, mídia |
| pessoa-video2 | Representa pessoa video2, útil para usuários, identidade, perfis e controle de acesso. | pessoa-video2, pessoa, video2, usuario, acesso, usuários |
| pessoa-video3 | Representa pessoa video3, útil para usuários, identidade, perfis e controle de acesso. | pessoa-video3, pessoa, video3, usuario, acesso, usuários |
| pessoa-walking | Representa pessoa walking, útil para usuários, identidade, perfis e controle de acesso. | pessoa-walking, pessoa, walking, usuario, acesso, usuários |
| pessoa-wheelchair | Representa pessoa wheelchair, útil para usuários, identidade, perfis e controle de acesso. | pessoa-wheelchair, pessoa, wheelchair, usuario, acesso, usuários |
| pilha | Representa pilha, útil para configuração, integrações e recursos digitais. | pilha, sistema, infraestrutura |
| pilha-overflow | Representa pilha overflow, útil para configuração, integrações e recursos digitais. | pilha-overflow, pilha, overflow, sistema, infraestrutura |
| pincel | Representa pincel, útil para configuração, integrações e recursos digitais. | pincel, sistema, infraestrutura |
| pincel-destaque | Representa pincel destaque, útil para configuração, integrações e recursos digitais. | pincel-destaque, pincel, destaque, sistema, infraestrutura |
| pino | Representa pino, útil para configuração, integrações e recursos digitais. | pino, sistema, infraestrutura |
| pino-angle | Representa pino angle, útil para configuração, integrações e recursos digitais. | pino-angle, pino, angle, sistema, infraestrutura |
| pino-angle-destaque | Representa pino angle destaque, útil para configuração, integrações e recursos digitais. | pino-angle-destaque, pino, angle, destaque, sistema, infraestrutura |
| pino-destaque | Representa pino destaque, útil para configuração, integrações e recursos digitais. | pino-destaque, pino, destaque, sistema, infraestrutura |
| pino-map | Representa pino map, útil para configuração, integrações e recursos digitais. | pino-map, pino, map, sistema, infraestrutura |
| pino-map-destaque | Representa pino map destaque, útil para configuração, integrações e recursos digitais. | pino-map-destaque, pino, map, destaque, sistema, infraestrutura |
| pinterest | Representa pinterest, útil para configuração, integrações e recursos digitais. | pinterest, sistema, infraestrutura |
| pip | Representa pip, útil para configuração, integrações e recursos digitais. | pip, sistema, infraestrutura |
| pip-destaque | Representa pip destaque, útil para configuração, integrações e recursos digitais. | pip-destaque, pip, destaque, sistema, infraestrutura |
| pizza-chart | Representa pizza chart, útil para métricas, indicadores e leitura de dados. | pizza-chart, pizza, chart, dados, analise, análise |
| pizza-chart-destaque | Representa pizza chart destaque, útil para métricas, indicadores e leitura de dados. | pizza-chart-destaque, pizza, chart, destaque, dados, análise |
| placa-dead-fim | Representa placa dead fim, útil para configuração, integrações e recursos digitais. | placa-dead-fim, placa, dead, fim, sistema, infraestrutura |
| placa-dead-fim-destaque | Representa placa dead fim destaque, útil para configuração, integrações e recursos digitais. | placa-dead-fim-destaque, placa, dead, fim, destaque, sistema, infraestrutura |
| placa-do-not-enter | Representa placa do not enter, útil para configuração, integrações e recursos digitais. | placa-do-not-enter, placa, not, enter, sistema, do, infraestrutura |
| placa-do-not-enter-destaque | Representa placa do not enter destaque, útil para configuração, integrações e recursos digitais. | placa-do-not-enter-destaque, placa, not, enter, destaque, do, sistema, infraestrutura |
| placa-gpu | Representa placa gpu, útil para configuração, integrações e recursos digitais. | placa-gpu, placa, gpu, sistema, infraestrutura |
| placa-intersection | Representa placa intersection, útil para configuração, integrações e recursos digitais. | placa-intersection, placa, intersection, sistema, infraestrutura |
| placa-intersection-destaque | Representa placa intersection destaque, útil para configuração, integrações e recursos digitais. | placa-intersection-destaque, placa, intersection, destaque, sistema, infraestrutura |
| placa-intersection-letra-t | Representa placa intersection letra t, útil para configuração, integrações e recursos digitais. | placa-intersection-letra-t, placa, intersection, letra, sistema, t, infraestrutura |
| placa-intersection-letra-t-destaque | Representa placa intersection letra t destaque, útil para configuração, integrações e recursos digitais. | placa-intersection-letra-t-destaque, placa, intersection, letra, destaque, t, sistema, infraestrutura |
| placa-intersection-letra-y | Representa placa intersection letra y, útil para configuração, integrações e recursos digitais. | placa-intersection-letra-y, placa, intersection, letra, sistema, y, infraestrutura |
| placa-intersection-letra-y-destaque | Representa placa intersection letra y destaque, útil para configuração, integrações e recursos digitais. | placa-intersection-letra-y-destaque, placa, intersection, letra, destaque, y, sistema, infraestrutura |
| placa-intersection-side | Representa placa intersection side, útil para configuração, integrações e recursos digitais. | placa-intersection-side, placa, intersection, side, sistema, infraestrutura |
| placa-intersection-side-destaque | Representa placa intersection side destaque, útil para configuração, integrações e recursos digitais. | placa-intersection-side-destaque, placa, intersection, side, destaque, sistema, infraestrutura |
| placa-merge-direita | Representa placa merge direita, útil para navegação, direção e fluxo de interface. | placa-merge-direita, placa, merge, direita, navegacao, navegação |
| placa-merge-direita-destaque | Representa placa merge direita destaque, útil para navegação, direção e fluxo de interface. | placa-merge-direita-destaque, placa, merge, direita, destaque, navegação |
| placa-merge-esquerda | Representa placa merge esquerda, útil para navegação, direção e fluxo de interface. | placa-merge-esquerda, placa, merge, esquerda, navegacao, navegação |
| placa-merge-esquerda-destaque | Representa placa merge esquerda destaque, útil para navegação, direção e fluxo de interface. | placa-merge-esquerda-destaque, placa, merge, esquerda, destaque, navegação |
| placa-no-direita-turn | Representa placa no direita turn, útil para navegação, direção e fluxo de interface. | placa-no-direita-turn, placa, direita, turn, navegacao, no, navegação |
| placa-no-direita-turn-destaque | Representa placa no direita turn destaque, útil para navegação, direção e fluxo de interface. | placa-no-direita-turn-destaque, placa, direita, turn, destaque, no, navegação |
| placa-no-esquerda-turn | Representa placa no esquerda turn, útil para navegação, direção e fluxo de interface. | placa-no-esquerda-turn, placa, esquerda, turn, navegacao, no, navegação |
| placa-no-esquerda-turn-destaque | Representa placa no esquerda turn destaque, útil para navegação, direção e fluxo de interface. | placa-no-esquerda-turn-destaque, placa, esquerda, turn, destaque, no, navegação |
| placa-no-parking | Representa placa no parking, útil para configuração, integrações e recursos digitais. | placa-no-parking, placa, parking, sistema, infraestrutura, no |
| placa-no-parking-destaque | Representa placa no parking destaque, útil para configuração, integrações e recursos digitais. | placa-no-parking-destaque, placa, parking, destaque, sistema, no, infraestrutura |
| placa-parar | Representa placa parar, útil para configuração, integrações e recursos digitais. | placa-parar, placa, parar, sistema, infraestrutura |
| placa-parar-destaque | Representa placa parar destaque, útil para configuração, integrações e recursos digitais. | placa-parar-destaque, placa, parar, destaque, sistema, infraestrutura |
| placa-parar-lights | Representa placa parar lights, útil para configuração, integrações e recursos digitais. | placa-parar-lights, placa, parar, lights, sistema, infraestrutura |
| placa-parar-lights-destaque | Representa placa parar lights destaque, útil para configuração, integrações e recursos digitais. | placa-parar-lights-destaque, placa, parar, lights, destaque, sistema, infraestrutura |
| placa-railroad | Representa placa railroad, útil para configuração, integrações e recursos digitais. | placa-railroad, placa, railroad, sistema, infraestrutura |
| placa-railroad-destaque | Representa placa railroad destaque, útil para configuração, integrações e recursos digitais. | placa-railroad-destaque, placa, railroad, destaque, sistema, infraestrutura |
| placa-turn-direita | Representa placa turn direita, útil para navegação, direção e fluxo de interface. | placa-turn-direita, placa, turn, direita, navegacao, navegação |
| placa-turn-direita-destaque | Representa placa turn direita destaque, útil para navegação, direção e fluxo de interface. | placa-turn-direita-destaque, placa, turn, direita, destaque, navegação |
| placa-turn-esquerda | Representa placa turn esquerda, útil para navegação, direção e fluxo de interface. | placa-turn-esquerda, placa, turn, esquerda, navegacao, navegação |
| placa-turn-esquerda-destaque | Representa placa turn esquerda destaque, útil para navegação, direção e fluxo de interface. | placa-turn-esquerda-destaque, placa, turn, esquerda, destaque, navegação |
| placa-turn-slight-direita | Representa placa turn slight direita, útil para navegação, direção e fluxo de interface. | placa-turn-slight-direita, placa, turn, slight, direita, navegação |
| placa-turn-slight-direita-destaque | Representa placa turn slight direita destaque, útil para navegação, direção e fluxo de interface. | placa-turn-slight-direita-destaque, placa, turn, slight, direita, destaque, navegação |
| placa-turn-slight-esquerda | Representa placa turn slight esquerda, útil para navegação, direção e fluxo de interface. | placa-turn-slight-esquerda, placa, turn, slight, esquerda, navegação |
| placa-turn-slight-esquerda-destaque | Representa placa turn slight esquerda destaque, útil para navegação, direção e fluxo de interface. | placa-turn-slight-esquerda-destaque, placa, turn, slight, esquerda, destaque, navegação |
| placa-yield | Representa placa yield, útil para configuração, integrações e recursos digitais. | placa-yield, placa, yield, sistema, infraestrutura |
| placa-yield-destaque | Representa placa yield destaque, útil para configuração, integrações e recursos digitais. | placa-yield-destaque, placa, yield, destaque, sistema, infraestrutura |
| playstation | Representa playstation, útil para configuração, integrações e recursos digitais. | playstation, sistema, infraestrutura |
| plug-destaque | Representa plug destaque, útil para configuração, integrações e recursos digitais. | plug-destaque, plug, destaque, sistema, infraestrutura |
| plugin | Representa plugin, útil para configuração, integrações e recursos digitais. | plugin, sistema, infraestrutura |
| porca | Representa porca, útil para configuração, integrações e recursos digitais. | porca, sistema, infraestrutura |
| porca-destaque | Representa porca destaque, útil para configuração, integrações e recursos digitais. | porca-destaque, porca, destaque, sistema, infraestrutura |
| porta-closed | Representa porta closed, útil para configuração, integrações e recursos digitais. | porta-closed, porta, closed, sistema, infraestrutura |
| porta-closed-destaque | Representa porta closed destaque, útil para configuração, integrações e recursos digitais. | porta-closed-destaque, porta, closed, destaque, sistema, infraestrutura |
| porta-open | Representa porta open, útil para configuração, integrações e recursos digitais. | porta-open, porta, open, sistema, infraestrutura |
| porta-open-destaque | Representa porta open destaque, útil para configuração, integrações e recursos digitais. | porta-open-destaque, porta, open, destaque, sistema, infraestrutura |
| portal | Entrada da área principal, portal ou acesso inicial. | portal, navegacao, fluxo, entrada, acesso, navegação |
| postagem | Representa postagem, útil para configuração, integrações e recursos digitais. | postagem, sistema, infraestrutura |
| postagem-coracao | Representa postagem coracao, útil para configuração, integrações e recursos digitais. | postagem-coracao, postagem, coracao, sistema, infraestrutura |
| postagem-coracao-destaque | Representa postagem coracao destaque, útil para configuração, integrações e recursos digitais. | postagem-coracao-destaque, postagem, coracao, destaque, sistema, infraestrutura |
| postagem-destaque | Representa postagem destaque, útil para configuração, integrações e recursos digitais. | postagem-destaque, postagem, destaque, sistema, infraestrutura |
| prancheta | Representa prancheta, útil para configuração, integrações e recursos digitais. | prancheta, sistema, infraestrutura |
| prancheta-adicionar | Representa prancheta adicionar, útil para ações, comandos e interações diretas na interface. | prancheta-adicionar, prancheta, adicionar, acao, comando, ações |
| prancheta-adicionar-destaque | Representa prancheta adicionar destaque, útil para ações, comandos e interações diretas na interface. | prancheta-adicionar-destaque, prancheta, adicionar, destaque, acao, ações |
| prancheta-confirmado-destaque | Representa prancheta confirmado destaque, útil para feedback visual, status e comunicação de estado. | prancheta-confirmado-destaque, prancheta, confirmado, destaque, status, estados |
| prancheta-coracao | Representa prancheta coracao, útil para configuração, integrações e recursos digitais. | prancheta-coracao, prancheta, coracao, sistema, infraestrutura |
| prancheta-coracao-destaque | Representa prancheta coracao destaque, útil para configuração, integrações e recursos digitais. | prancheta-coracao-destaque, prancheta, coracao, destaque, sistema, infraestrutura |
| prancheta-data | Representa prancheta data, útil para configuração, integrações e recursos digitais. | prancheta-data, prancheta, data, sistema, infraestrutura |
| prancheta-data-destaque | Representa prancheta data destaque, útil para configuração, integrações e recursos digitais. | prancheta-data-destaque, prancheta, data, destaque, sistema, infraestrutura |
| prancheta-destaque | Representa prancheta destaque, útil para configuração, integrações e recursos digitais. | prancheta-destaque, prancheta, destaque, sistema, infraestrutura |
| prancheta-minus | Representa prancheta minus, útil para configuração, integrações e recursos digitais. | prancheta-minus, prancheta, minus, sistema, infraestrutura |
| prancheta-minus-destaque | Representa prancheta minus destaque, útil para configuração, integrações e recursos digitais. | prancheta-minus-destaque, prancheta, minus, destaque, sistema, infraestrutura |
| prancheta-pulse | Representa prancheta pulse, útil para configuração, integrações e recursos digitais. | prancheta-pulse, prancheta, pulse, sistema, infraestrutura |
| prancheta-remover | Representa prancheta remover, útil para ações, comandos e interações diretas na interface. | prancheta-remover, prancheta, remover, acao, comando, ações |
| prancheta-remover-destaque | Representa prancheta remover destaque, útil para ações, comandos e interações diretas na interface. | prancheta-remover-destaque, prancheta, remover, destaque, acao, ações |
| predio-add | Representa predio add, útil para configuração, integrações e recursos digitais. | predio-add, predio, add, sistema, infraestrutura |
| predio-baixo | Representa predio baixo, útil para navegação, direção e fluxo de interface. | predio-baixo, predio, baixo, navegacao, fluxo, navegação |
| predio-cadeado | Representa predio cadeado, útil para segurança, controle de acesso e confiança operacional. | predio-cadeado, predio, cadeado, seguranca, permissao, segurança, permissões |
| predio-cima | Representa predio cima, útil para navegação, direção e fluxo de interface. | predio-cima, predio, cima, navegacao, fluxo, navegação |
| predio-confirmado | Representa predio confirmado, útil para feedback visual, status e comunicação de estado. | predio-confirmado, predio, confirmado, status, estado, estados |
| predio-cortado | Representa predio cortado, útil para configuração, integrações e recursos digitais. | predio-cortado, predio, cortado, sistema, infraestrutura |
| predio-destaque | Representa predio destaque, útil para configuração, integrações e recursos digitais. | predio-destaque, predio, destaque, sistema, infraestrutura |
| predio-destaque-add | Representa predio destaque add, útil para configuração, integrações e recursos digitais. | predio-destaque-add, predio, destaque, add, sistema, infraestrutura |
| predio-destaque-baixo | Representa predio destaque baixo, útil para navegação, direção e fluxo de interface. | predio-destaque-baixo, predio, destaque, baixo, navegacao, navegação |
| predio-destaque-cadeado | Representa predio destaque cadeado, útil para segurança, controle de acesso e confiança operacional. | predio-destaque-cadeado, predio, destaque, cadeado, seguranca, segurança, permissões |
| predio-destaque-cima | Representa predio destaque cima, útil para navegação, direção e fluxo de interface. | predio-destaque-cima, predio, destaque, cima, navegacao, navegação |
| predio-destaque-confirmado | Representa predio destaque confirmado, útil para feedback visual, status e comunicação de estado. | predio-destaque-confirmado, predio, destaque, confirmado, status, estados |
| predio-destaque-cortado | Representa predio destaque cortado, útil para configuração, integrações e recursos digitais. | predio-destaque-cortado, predio, destaque, cortado, sistema, infraestrutura |
| predio-destaque-engrenagem | Representa predio destaque engrenagem, útil para configuração, integrações e recursos digitais. | predio-destaque-engrenagem, predio, destaque, engrenagem, sistema, infraestrutura |
| predio-destaque-exclamacao | Representa predio destaque exclamacao, útil para configuração, integrações e recursos digitais. | predio-destaque-exclamacao, predio, destaque, exclamacao, sistema, infraestrutura |
| predio-destaque-menos | Representa predio destaque menos, útil para configuração, integrações e recursos digitais. | predio-destaque-menos, predio, destaque, menos, sistema, infraestrutura |
| predio-destaque-remover | Representa predio destaque remover, útil para ações, comandos e interações diretas na interface. | predio-destaque-remover, predio, destaque, remover, acao, ações |
| predio-engrenagem | Representa predio engrenagem, útil para configuração, integrações e recursos digitais. | predio-engrenagem, predio, engrenagem, sistema, infraestrutura |
| predio-exclamacao | Representa predio exclamacao, útil para configuração, integrações e recursos digitais. | predio-exclamacao, predio, exclamacao, sistema, infraestrutura |
| predio-menos | Representa predio menos, útil para configuração, integrações e recursos digitais. | predio-menos, predio, menos, sistema, infraestrutura |
| predio-remover | Representa predio remover, útil para ações, comandos e interações diretas na interface. | predio-remover, predio, remover, acao, comando, ações |
| premio | Selo de conquista, destaque, premiação ou qualidade. | premio, status, estado, selo, conquista, prêmio, estados |
| prescription2 | Representa prescription2, útil para configuração, integrações e recursos digitais. | prescription2, sistema, infraestrutura |
| presente | Representa presente, útil para configuração, integrações e recursos digitais. | presente, sistema, infraestrutura |
| presente-destaque | Representa presente destaque, útil para configuração, integrações e recursos digitais. | presente-destaque, presente, destaque, sistema, infraestrutura |
| processamento | Processamento, servidor, desempenho técnico ou compute. | processamento, sistema, infraestrutura, servidor, desempenho |
| processamento-destaque | Representa processamento destaque, útil para configuração, integrações e recursos digitais. | processamento-destaque, processamento, destaque, sistema, infraestrutura |
| projetor | Representa projetor, útil para configuração, integrações e recursos digitais. | projetor, sistema, infraestrutura |
| projetor-destaque | Representa projetor destaque, útil para configuração, integrações e recursos digitais. | projetor-destaque, projetor, destaque, sistema, infraestrutura |
| pular-avancar | Representa pular avancar, útil para navegação, direção e fluxo de interface. | pular-avancar, pular, avancar, navegacao, fluxo, navegação |
| pular-avancar-btn | Representa pular avancar btn, útil para navegação, direção e fluxo de interface. | pular-avancar-btn, pular, avancar, btn, navegacao, navegação |
| pular-avancar-btn-destaque | Representa pular avancar btn destaque, útil para navegação, direção e fluxo de interface. | pular-avancar-btn-destaque, pular, avancar, btn, destaque, navegação |
| pular-avancar-circulo | Representa pular avancar circulo, útil para navegação, direção e fluxo de interface. | pular-avancar-circulo, pular, avancar, circulo, navegacao, navegação |
| pular-avancar-circulo-destaque | Representa pular avancar circulo destaque, útil para navegação, direção e fluxo de interface. | pular-avancar-circulo-destaque, pular, avancar, circulo, destaque, navegação |
| pular-avancar-destaque | Representa pular avancar destaque, útil para navegação, direção e fluxo de interface. | pular-avancar-destaque, pular, avancar, destaque, navegacao, navegação |
| pular-backward | Representa pular backward, útil para configuração, integrações e recursos digitais. | pular-backward, pular, backward, sistema, infraestrutura |
| pular-backward-btn | Representa pular backward btn, útil para configuração, integrações e recursos digitais. | pular-backward-btn, pular, backward, btn, sistema, infraestrutura |
| pular-backward-btn-destaque | Representa pular backward btn destaque, útil para configuração, integrações e recursos digitais. | pular-backward-btn-destaque, pular, backward, btn, destaque, sistema, infraestrutura |
| pular-backward-circulo | Representa pular backward circulo, útil para configuração, integrações e recursos digitais. | pular-backward-circulo, pular, backward, circulo, sistema, infraestrutura |
| pular-backward-circulo-destaque | Representa pular backward circulo destaque, útil para configuração, integrações e recursos digitais. | pular-backward-circulo-destaque, pular, backward, circulo, destaque, sistema, infraestrutura |
| pular-backward-destaque | Representa pular backward destaque, útil para configuração, integrações e recursos digitais. | pular-backward-destaque, pular, backward, destaque, sistema, infraestrutura |
| pular-fim | Representa pular fim, útil para configuração, integrações e recursos digitais. | pular-fim, pular, fim, sistema, infraestrutura |
| pular-fim-btn | Representa pular fim btn, útil para configuração, integrações e recursos digitais. | pular-fim-btn, pular, fim, btn, sistema, infraestrutura |
| pular-fim-btn-destaque | Representa pular fim btn destaque, útil para configuração, integrações e recursos digitais. | pular-fim-btn-destaque, pular, fim, btn, destaque, sistema, infraestrutura |
| pular-fim-circulo | Representa pular fim circulo, útil para configuração, integrações e recursos digitais. | pular-fim-circulo, pular, fim, circulo, sistema, infraestrutura |
| pular-fim-circulo-destaque | Representa pular fim circulo destaque, útil para configuração, integrações e recursos digitais. | pular-fim-circulo-destaque, pular, fim, circulo, destaque, sistema, infraestrutura |
| pular-fim-destaque | Representa pular fim destaque, útil para configuração, integrações e recursos digitais. | pular-fim-destaque, pular, fim, destaque, sistema, infraestrutura |
| pular-inicio | Representa pular inicio, útil para navegação, direção e fluxo de interface. | pular-inicio, pular, inicio, navegacao, fluxo, navegação |
| pular-inicio-btn | Representa pular inicio btn, útil para navegação, direção e fluxo de interface. | pular-inicio-btn, pular, inicio, btn, navegacao, navegação |
| pular-inicio-btn-destaque | Representa pular inicio btn destaque, útil para navegação, direção e fluxo de interface. | pular-inicio-btn-destaque, pular, inicio, btn, destaque, navegação |
| pular-inicio-circulo | Representa pular inicio circulo, útil para navegação, direção e fluxo de interface. | pular-inicio-circulo, pular, inicio, circulo, navegacao, navegação |
| pular-inicio-circulo-destaque | Representa pular inicio circulo destaque, útil para navegação, direção e fluxo de interface. | pular-inicio-circulo-destaque, pular, inicio, circulo, destaque, navegação |
| pular-inicio-destaque | Representa pular inicio destaque, útil para navegação, direção e fluxo de interface. | pular-inicio-destaque, pular, inicio, destaque, navegacao, navegação |
| pulmoes | Representa pulmoes, útil para configuração, integrações e recursos digitais. | pulmoes, sistema, infraestrutura |
| pulmoes-destaque | Representa pulmoes destaque, útil para configuração, integrações e recursos digitais. | pulmoes-destaque, pulmoes, destaque, sistema, infraestrutura |
| quadrado | Representa quadrado, útil para configuração, integrações e recursos digitais. | quadrado, sistema, infraestrutura |
| quadrado-destaque | Representa quadrado destaque, útil para configuração, integrações e recursos digitais. | quadrado-destaque, quadrado, destaque, sistema, infraestrutura |
| quadrado-half | Representa quadrado half, útil para configuração, integrações e recursos digitais. | quadrado-half, quadrado, half, sistema, infraestrutura |
| quebra-cabeca | Representa quebra cabeca, útil para configuração, integrações e recursos digitais. | quebra-cabeca, quebra, cabeca, sistema, infraestrutura |
| quebra-cabeca-destaque | Representa quebra cabeca destaque, útil para configuração, integrações e recursos digitais. | quebra-cabeca-destaque, quebra, cabeca, destaque, sistema, infraestrutura |
| quora | Representa quora, útil para configuração, integrações e recursos digitais. | quora, sistema, infraestrutura |
| radar | Representa radar, útil para configuração, integrações e recursos digitais. | radar, sistema, infraestrutura |
| radioativo | Representa radioativo, útil para configuração, integrações e recursos digitais. | radioativo, sistema, infraestrutura |
| raio-charge-destaque | Representa raio charge destaque, útil para configuração, integrações e recursos digitais. | raio-charge-destaque, raio, charge, destaque, sistema, infraestrutura |
| rapido-avancar | Representa rapido avancar, útil para navegação, direção e fluxo de interface. | rapido-avancar, rapido, avancar, navegacao, fluxo, navegação |
| rapido-avancar-btn | Representa rapido avancar btn, útil para navegação, direção e fluxo de interface. | rapido-avancar-btn, rapido, avancar, btn, navegacao, navegação |
| rapido-avancar-btn-destaque | Representa rapido avancar btn destaque, útil para navegação, direção e fluxo de interface. | rapido-avancar-btn-destaque, rapido, avancar, btn, destaque, navegação |
| rapido-avancar-circulo | Representa rapido avancar circulo, útil para navegação, direção e fluxo de interface. | rapido-avancar-circulo, rapido, avancar, circulo, navegacao, navegação |
| rapido-avancar-circulo-destaque | Representa rapido avancar circulo destaque, útil para navegação, direção e fluxo de interface. | rapido-avancar-circulo-destaque, rapido, avancar, circulo, destaque, navegação |
| rapido-avancar-destaque | Representa rapido avancar destaque, útil para navegação, direção e fluxo de interface. | rapido-avancar-destaque, rapido, avancar, destaque, navegacao, navegação |
| receita | Representa receita, útil para configuração, integrações e recursos digitais. | receita, sistema, infraestrutura |
| recibo | Recibo, comprovante, faturamento ou pedido formalizado. | recibo, compra, pedido, comprovante, faturamento, comércio |
| recibo-cutoff | Representa recibo cutoff, útil para compras, vendas, cobrança e contexto financeiro. | recibo-cutoff, recibo, cutoff, compra, pedido, comércio, faturamento |
| reciclar | Representa reciclar, útil para configuração, integrações e recursos digitais. | reciclar, sistema, infraestrutura |
| recolher | Recolher, subir nivel ou indicar direção superior. | recolher, navegacao, fluxo, subir, nivel, navegação |
| record2 | Representa record2, útil para configuração, integrações e recursos digitais. | record2, sistema, infraestrutura |
| record2-destaque | Representa record2 destaque, útil para configuração, integrações e recursos digitais. | record2-destaque, record2, destaque, sistema, infraestrutura |
| recorte | Representa recorte, útil para configuração, integrações e recursos digitais. | recorte, sistema, infraestrutura |
| reddit | Representa reddit, útil para configuração, integrações e recursos digitais. | reddit, sistema, infraestrutura |
| rede-global | Rede global, conectividade externa ou distribuição. | rede-global, rede, global, sistema, infraestrutura |
| regex | Representa regex, útil para configuração, integrações e recursos digitais. | regex, sistema, infraestrutura |
| reguas | Representa reguas, útil para configuração, integrações e recursos digitais. | reguas, sistema, infraestrutura |
| relatorio | Dados tabulados, relatório operacional ou coleta estruturada. | relatorio, dados, analise, tabulados, operacional, relatório, análise |
| relogio | Representa relogio, útil para tempo, agenda e acompanhamento de prazos. | relogio, agenda, tempo, agendamento |
| relogio-destaque | Representa relogio destaque, útil para tempo, agenda e acompanhamento de prazos. | relogio-destaque, relogio, destaque, agenda, tempo, agendamento |
| remover | Representa remover, útil para ações, comandos e interações diretas na interface. | remover, acao, comando, ações |
| remover-losango | Representa remover losango, útil para ações, comandos e interações diretas na interface. | remover-losango, remover, losango, acao, comando, ações |
| remover-losango-destaque | Representa remover losango destaque, útil para ações, comandos e interações diretas na interface. | remover-losango-destaque, remover, losango, destaque, acao, ações |
| remover-octagon | Representa remover octagon, útil para ações, comandos e interações diretas na interface. | remover-octagon, remover, octagon, acao, comando, ações |
| remover-octagon-destaque | Representa remover octagon destaque, útil para ações, comandos e interações diretas na interface. | remover-octagon-destaque, remover, octagon, destaque, acao, ações |
| repeat | Representa repeat, útil para configuração, integrações e recursos digitais. | repeat, sistema, infraestrutura |
| repeat-numero-1 | Representa repeat numero 1, útil para configuração, integrações e recursos digitais. | repeat-numero-1, repeat, numero, sistema, infraestrutura, 1 |
| reproduzir | Iniciar reprodução, demonstracao ou executar mídia. | reproduzir, arquivo, documento, iniciar, reproducao, arquivos, mídia |
| reproduzir-btn | Representa reproduzir btn, útil para configuração, integrações e recursos digitais. | reproduzir-btn, reproduzir, btn, sistema, infraestrutura |
| reproduzir-btn-destaque | Representa reproduzir btn destaque, útil para configuração, integrações e recursos digitais. | reproduzir-btn-destaque, reproduzir, btn, destaque, sistema, infraestrutura |
| reproduzir-circulo-destaque | Representa reproduzir circulo destaque, útil para configuração, integrações e recursos digitais. | reproduzir-circulo-destaque, reproduzir, circulo, destaque, sistema, infraestrutura |
| reproduzir-destaque | Representa reproduzir destaque, útil para configuração, integrações e recursos digitais. | reproduzir-destaque, reproduzir, destaque, sistema, infraestrutura |
| reproduzir-icon | Representa reproduzir icon, útil para configuração, integrações e recursos digitais. | reproduzir-icon, reproduzir, icon, sistema, infraestrutura |
| responder | Representa responder, útil para configuração, integrações e recursos digitais. | responder, sistema, infraestrutura |
| responder-all | Representa responder all, útil para configuração, integrações e recursos digitais. | responder-all, responder, all, sistema, infraestrutura |
| responder-all-destaque | Representa responder all destaque, útil para configuração, integrações e recursos digitais. | responder-all-destaque, responder, all, destaque, sistema, infraestrutura |
| responder-destaque | Representa responder destaque, útil para configuração, integrações e recursos digitais. | responder-destaque, responder, destaque, sistema, infraestrutura |
| retornar | Saída, retorno ao contexto anterior ou evasão lateral. | retornar, seguranca, permissao, saida, retorno, segurança, permissões |
| rewind | Representa rewind, útil para configuração, integrações e recursos digitais. | rewind, sistema, infraestrutura |
| rewind-btn | Representa rewind btn, útil para configuração, integrações e recursos digitais. | rewind-btn, rewind, btn, sistema, infraestrutura |
| rewind-btn-destaque | Representa rewind btn destaque, útil para configuração, integrações e recursos digitais. | rewind-btn-destaque, rewind, btn, destaque, sistema, infraestrutura |
| rewind-circulo | Representa rewind circulo, útil para configuração, integrações e recursos digitais. | rewind-circulo, rewind, circulo, sistema, infraestrutura |
| rewind-circulo-destaque | Representa rewind circulo destaque, útil para configuração, integrações e recursos digitais. | rewind-circulo-destaque, rewind, circulo, destaque, sistema, infraestrutura |
| rewind-destaque | Representa rewind destaque, útil para configuração, integrações e recursos digitais. | rewind-destaque, rewind, destaque, sistema, infraestrutura |
| robot | Representa robot, útil para configuração, integrações e recursos digitais. | robot, sistema, infraestrutura |
| roteador | Representa roteador, útil para configuração, integrações e recursos digitais. | roteador, sistema, infraestrutura |
| roteador-destaque | Representa roteador destaque, útil para configuração, integrações e recursos digitais. | roteador-destaque, roteador, destaque, sistema, infraestrutura |
| rss | Representa rss, útil para configuração, integrações e recursos digitais. | rss, sistema, infraestrutura |
| rss-destaque | Representa rss destaque, útil para configuração, integrações e recursos digitais. | rss-destaque, rss, destaque, sistema, infraestrutura |
| sacola | Sacola comercial para compra, pedido ou vitrine. | sacola, compra, pedido, comercial, vitrine, comércio, faturamento |
| sacola-adicionar | Representa sacola adicionar, útil para ações, comandos e interações diretas na interface. | sacola-adicionar, sacola, adicionar, acao, comando, ações |
| sacola-adicionar-destaque | Representa sacola adicionar destaque, útil para ações, comandos e interações diretas na interface. | sacola-adicionar-destaque, sacola, adicionar, destaque, acao, ações |
| sacola-concluida | Sacola com confirmação, checkout aprovado ou pedido concluído. | sacola-concluida, sacola, concluida, compra, pedido, concluída, comércio, faturamento |
| sacola-confirmado-destaque | Representa sacola confirmado destaque, útil para feedback visual, status e comunicação de estado. | sacola-confirmado-destaque, sacola, confirmado, destaque, status, estados |
| sacola-coracao | Representa sacola coracao, útil para configuração, integrações e recursos digitais. | sacola-coracao, sacola, coracao, sistema, infraestrutura |
| sacola-coracao-destaque | Representa sacola coracao destaque, útil para configuração, integrações e recursos digitais. | sacola-coracao-destaque, sacola, coracao, destaque, sistema, infraestrutura |
| sacola-destaque | Representa sacola destaque, útil para configuração, integrações e recursos digitais. | sacola-destaque, sacola, destaque, sistema, infraestrutura |
| sacola-menos | Representa sacola menos, útil para configuração, integrações e recursos digitais. | sacola-menos, sacola, menos, sistema, infraestrutura |
| sacola-menos-destaque | Representa sacola menos destaque, útil para configuração, integrações e recursos digitais. | sacola-menos-destaque, sacola, menos, destaque, sistema, infraestrutura |
| sacola-remover | Representa sacola remover, útil para ações, comandos e interações diretas na interface. | sacola-remover, sacola, remover, acao, comando, ações |
| sacola-remover-destaque | Representa sacola remover destaque, útil para ações, comandos e interações diretas na interface. | sacola-remover-destaque, sacola, remover, destaque, acao, ações |
| safe2 | Representa safe2, útil para configuração, integrações e recursos digitais. | safe2, sistema, infraestrutura |
| safe2-destaque | Representa safe2 destaque, útil para configuração, integrações e recursos digitais. | safe2-destaque, safe2, destaque, sistema, infraestrutura |
| sair | Logout, saída principal ou redirecionamento para fora do contexto. | sair, seguranca, permissao, logout, saida, segurança, permissões |
| salvar | Representa salvar, útil para configuração, integrações e recursos digitais. | salvar, sistema, infraestrutura |
| salvar-destaque | Representa salvar destaque, útil para configuração, integrações e recursos digitais. | salvar-destaque, salvar, destaque, sistema, infraestrutura |
| save2 | Representa save2, útil para configuração, integrações e recursos digitais. | save2, sistema, infraestrutura |
| save2-destaque | Representa save2 destaque, útil para configuração, integrações e recursos digitais. | save2-destaque, save2, destaque, sistema, infraestrutura |
| screwdriver | Representa screwdriver, útil para configuração, integrações e recursos digitais. | screwdriver, sistema, infraestrutura |
| segmented-nav | Representa segmented nav, útil para configuração, integrações e recursos digitais. | segmented-nav, segmented, nav, sistema, infraestrutura |
| seguranca-alerta | Alerta de segurança, risco ou conformidade comprometida. | seguranca-alerta, seguranca, alerta, permissao, risco, segurança, permissões |
| seguranca-confirmada | Proteção confirmada, política válida ou ambiente seguro. | seguranca-confirmada, seguranca, confirmada, permissao, protecao, segurança, permissões |
| seguranca-protegida | Proteção reforcada, dado sensivel ou acesso blindado. | seguranca-protegida, seguranca, protegida, permissao, protecao, segurança, permissões |
| selo-3d | Representa selo 3d, útil para configuração, integrações e recursos digitais. | selo-3d, selo, sistema, infraestrutura, 3d |
| selo-3d-destaque | Representa selo 3d destaque, útil para configuração, integrações e recursos digitais. | selo-3d-destaque, selo, destaque, sistema, infraestrutura, 3d |
| selo-4k | Representa selo 4k, útil para configuração, integrações e recursos digitais. | selo-4k, selo, sistema, infraestrutura, 4k |
| selo-4k-destaque | Representa selo 4k destaque, útil para configuração, integrações e recursos digitais. | selo-4k-destaque, selo, destaque, sistema, infraestrutura, 4k |
| selo-8k | Representa selo 8k, útil para configuração, integrações e recursos digitais. | selo-8k, selo, sistema, infraestrutura, 8k |
| selo-8k-destaque | Representa selo 8k destaque, útil para configuração, integrações e recursos digitais. | selo-8k-destaque, selo, destaque, sistema, infraestrutura, 8k |
| selo-ad | Representa selo ad, útil para configuração, integrações e recursos digitais. | selo-ad, selo, sistema, infraestrutura, ad |
| selo-ad-destaque | Representa selo ad destaque, útil para configuração, integrações e recursos digitais. | selo-ad-destaque, selo, destaque, sistema, infraestrutura, ad |
| selo-adicionar | Representa selo adicionar, útil para ações, comandos e interações diretas na interface. | selo-adicionar, selo, adicionar, acao, comando, ações |
| selo-adicionar-destaque | Representa selo adicionar destaque, útil para ações, comandos e interações diretas na interface. | selo-adicionar-destaque, selo, adicionar, destaque, acao, ações |
| selo-ar | Representa selo ar, útil para configuração, integrações e recursos digitais. | selo-ar, selo, sistema, infraestrutura, ar |
| selo-ar-destaque | Representa selo ar destaque, útil para configuração, integrações e recursos digitais. | selo-ar-destaque, selo, destaque, sistema, infraestrutura, ar |
| selo-cc | Representa selo cc, útil para configuração, integrações e recursos digitais. | selo-cc, selo, sistema, infraestrutura, cc |
| selo-cc-destaque | Representa selo cc destaque, útil para configuração, integrações e recursos digitais. | selo-cc-destaque, selo, destaque, sistema, infraestrutura, cc |
| selo-confirmado-destaque | Representa selo confirmado destaque, útil para feedback visual, status e comunicação de estado. | selo-confirmado-destaque, selo, confirmado, destaque, status, estados |
| selo-exclamacao | Representa selo exclamacao, útil para configuração, integrações e recursos digitais. | selo-exclamacao, selo, exclamacao, sistema, infraestrutura |
| selo-exclamacao-destaque | Representa selo exclamacao destaque, útil para configuração, integrações e recursos digitais. | selo-exclamacao-destaque, selo, exclamacao, destaque, sistema, infraestrutura |
| selo-hd | Representa selo hd, útil para configuração, integrações e recursos digitais. | selo-hd, selo, sistema, infraestrutura, hd |
| selo-hd-destaque | Representa selo hd destaque, útil para configuração, integrações e recursos digitais. | selo-hd-destaque, selo, destaque, sistema, infraestrutura, hd |
| selo-minus | Representa selo minus, útil para configuração, integrações e recursos digitais. | selo-minus, selo, minus, sistema, infraestrutura |
| selo-minus-destaque | Representa selo minus destaque, útil para configuração, integrações e recursos digitais. | selo-minus-destaque, selo, minus, destaque, sistema, infraestrutura |
| selo-pergunta | Representa selo pergunta, útil para configuração, integrações e recursos digitais. | selo-pergunta, selo, pergunta, sistema, infraestrutura |
| selo-pergunta-destaque | Representa selo pergunta destaque, útil para configuração, integrações e recursos digitais. | selo-pergunta-destaque, selo, pergunta, destaque, sistema, infraestrutura |
| selo-sd | Representa selo sd, útil para configuração, integrações e recursos digitais. | selo-sd, selo, sistema, infraestrutura, sd |
| selo-sd-destaque | Representa selo sd destaque, útil para configuração, integrações e recursos digitais. | selo-sd-destaque, selo, destaque, sistema, infraestrutura, sd |
| selo-tm | Representa selo tm, útil para configuração, integrações e recursos digitais. | selo-tm, selo, sistema, infraestrutura, tm |
| selo-tm-destaque | Representa selo tm destaque, útil para configuração, integrações e recursos digitais. | selo-tm-destaque, selo, destaque, sistema, infraestrutura, tm |
| selo-vo | Representa selo vo, útil para configuração, integrações e recursos digitais. | selo-vo, selo, sistema, infraestrutura, vo |
| selo-vo-destaque | Representa selo vo destaque, útil para configuração, integrações e recursos digitais. | selo-vo-destaque, selo, destaque, sistema, infraestrutura, vo |
| selo-vr | Representa selo vr, útil para configuração, integrações e recursos digitais. | selo-vr, selo, sistema, infraestrutura, vr |
| selo-vr-destaque | Representa selo vr destaque, útil para configuração, integrações e recursos digitais. | selo-vr-destaque, selo, destaque, sistema, infraestrutura, vr |
| selo-wc | Representa selo wc, útil para configuração, integrações e recursos digitais. | selo-wc, selo, sistema, infraestrutura, wc |
| selo-wc-destaque | Representa selo wc destaque, útil para configuração, integrações e recursos digitais. | selo-wc-destaque, selo, destaque, sistema, infraestrutura, wc |
| semaforo | Representa semaforo, útil para configuração, integrações e recursos digitais. | semaforo, sistema, infraestrutura |
| semaforo-destaque | Representa semaforo destaque, útil para configuração, integrações e recursos digitais. | semaforo-destaque, semaforo, destaque, sistema, infraestrutura |
| servidor | Representa servidor, útil para configuração, integrações e recursos digitais. | servidor, sistema, infraestrutura |
| seta-90graus-baixo | Representa seta 90graus baixo, útil para navegação, direção e fluxo de interface. | seta-90graus-baixo, seta, 90graus, baixo, navegacao, navegação |
| seta-90graus-cima | Representa seta 90graus cima, útil para navegação, direção e fluxo de interface. | seta-90graus-cima, seta, 90graus, cima, navegacao, navegação |
| seta-90graus-direita | Representa seta 90graus direita, útil para navegação, direção e fluxo de interface. | seta-90graus-direita, seta, 90graus, direita, navegacao, navegação |
| seta-90graus-esquerda | Representa seta 90graus esquerda, útil para navegação, direção e fluxo de interface. | seta-90graus-esquerda, seta, 90graus, esquerda, navegacao, navegação |
| seta-baixo | Representa seta baixo, útil para navegação, direção e fluxo de interface. | seta-baixo, seta, baixo, navegacao, fluxo, navegação |
| seta-baixo-cima | Representa seta baixo cima, útil para navegação, direção e fluxo de interface. | seta-baixo-cima, seta, baixo, cima, navegacao, navegação |
| seta-baixo-circulo-destaque | Representa seta baixo circulo destaque, útil para navegação, direção e fluxo de interface. | seta-baixo-circulo-destaque, seta, baixo, circulo, destaque, navegação |
| seta-baixo-direita | Representa seta baixo direita, útil para navegação, direção e fluxo de interface. | seta-baixo-direita, seta, baixo, direita, navegacao, navegação |
| seta-baixo-direita-circulo | Representa seta baixo direita circulo, útil para navegação, direção e fluxo de interface. | seta-baixo-direita-circulo, seta, baixo, direita, circulo, navegação |
| seta-baixo-direita-circulo-destaque | Representa seta baixo direita circulo destaque, útil para navegação, direção e fluxo de interface. | seta-baixo-direita-circulo-destaque, seta, baixo, direita, circulo, destaque, navegação |
| seta-baixo-direita-quadrado | Representa seta baixo direita quadrado, útil para navegação, direção e fluxo de interface. | seta-baixo-direita-quadrado, seta, baixo, direita, quadrado, navegação |
| seta-baixo-direita-quadrado-destaque | Representa seta baixo direita quadrado destaque, útil para navegação, direção e fluxo de interface. | seta-baixo-direita-quadrado-destaque, seta, baixo, direita, quadrado, destaque, navegação |
| seta-baixo-esquerda | Representa seta baixo esquerda, útil para navegação, direção e fluxo de interface. | seta-baixo-esquerda, seta, baixo, esquerda, navegacao, navegação |
| seta-baixo-esquerda-circulo | Representa seta baixo esquerda circulo, útil para navegação, direção e fluxo de interface. | seta-baixo-esquerda-circulo, seta, baixo, esquerda, circulo, navegação |
| seta-baixo-esquerda-circulo-destaque | Representa seta baixo esquerda circulo destaque, útil para navegação, direção e fluxo de interface. | seta-baixo-esquerda-circulo-destaque, seta, baixo, esquerda, circulo, destaque, navegação |
| seta-baixo-esquerda-quadrado | Representa seta baixo esquerda quadrado, útil para navegação, direção e fluxo de interface. | seta-baixo-esquerda-quadrado, seta, baixo, esquerda, quadrado, navegação |
| seta-baixo-esquerda-quadrado-destaque | Representa seta baixo esquerda quadrado destaque, útil para navegação, direção e fluxo de interface. | seta-baixo-esquerda-quadrado-destaque, seta, baixo, esquerda, quadrado, destaque, navegação |
| seta-baixo-quadrado | Representa seta baixo quadrado, útil para navegação, direção e fluxo de interface. | seta-baixo-quadrado, seta, baixo, quadrado, navegacao, navegação |
| seta-baixo-quadrado-destaque | Representa seta baixo quadrado destaque, útil para navegação, direção e fluxo de interface. | seta-baixo-quadrado-destaque, seta, baixo, quadrado, destaque, navegação |
| seta-baixo-short | Representa seta baixo short, útil para navegação, direção e fluxo de interface. | seta-baixo-short, seta, baixo, short, navegacao, navegação |
| seta-barra-baixo | Representa seta barra baixo, útil para navegação, direção e fluxo de interface. | seta-barra-baixo, seta, barra, baixo, navegacao, navegação |
| seta-barra-cima | Representa seta barra cima, útil para navegação, direção e fluxo de interface. | seta-barra-cima, seta, barra, cima, navegacao, navegação |
| seta-barra-direita | Representa seta barra direita, útil para navegação, direção e fluxo de interface. | seta-barra-direita, seta, barra, direita, navegacao, navegação |
| seta-barra-esquerda | Representa seta barra esquerda, útil para navegação, direção e fluxo de interface. | seta-barra-esquerda, seta, barra, esquerda, navegacao, navegação |
| seta-cima | Representa seta cima, útil para navegação, direção e fluxo de interface. | seta-cima, seta, cima, navegacao, fluxo, navegação |
| seta-cima-circulo | Representa seta cima circulo, útil para navegação, direção e fluxo de interface. | seta-cima-circulo, seta, cima, circulo, navegacao, navegação |
| seta-cima-circulo-destaque | Representa seta cima circulo destaque, útil para navegação, direção e fluxo de interface. | seta-cima-circulo-destaque, seta, cima, circulo, destaque, navegação |
| seta-cima-direita | Representa seta cima direita, útil para navegação, direção e fluxo de interface. | seta-cima-direita, seta, cima, direita, navegacao, navegação |
| seta-cima-direita-circulo | Representa seta cima direita circulo, útil para navegação, direção e fluxo de interface. | seta-cima-direita-circulo, seta, cima, direita, circulo, navegação |
| seta-cima-direita-circulo-destaque | Representa seta cima direita circulo destaque, útil para navegação, direção e fluxo de interface. | seta-cima-direita-circulo-destaque, seta, cima, direita, circulo, destaque, navegação |
| seta-cima-direita-quadrado | Representa seta cima direita quadrado, útil para navegação, direção e fluxo de interface. | seta-cima-direita-quadrado, seta, cima, direita, quadrado, navegação |
| seta-cima-direita-quadrado-destaque | Representa seta cima direita quadrado destaque, útil para navegação, direção e fluxo de interface. | seta-cima-direita-quadrado-destaque, seta, cima, direita, quadrado, destaque, navegação |
| seta-cima-esquerda | Representa seta cima esquerda, útil para navegação, direção e fluxo de interface. | seta-cima-esquerda, seta, cima, esquerda, navegacao, navegação |
| seta-cima-esquerda-circulo | Representa seta cima esquerda circulo, útil para navegação, direção e fluxo de interface. | seta-cima-esquerda-circulo, seta, cima, esquerda, circulo, navegação |
| seta-cima-esquerda-circulo-destaque | Representa seta cima esquerda circulo destaque, útil para navegação, direção e fluxo de interface. | seta-cima-esquerda-circulo-destaque, seta, cima, esquerda, circulo, destaque, navegação |
| seta-cima-esquerda-quadrado | Representa seta cima esquerda quadrado, útil para navegação, direção e fluxo de interface. | seta-cima-esquerda-quadrado, seta, cima, esquerda, quadrado, navegação |
| seta-cima-esquerda-quadrado-destaque | Representa seta cima esquerda quadrado destaque, útil para navegação, direção e fluxo de interface. | seta-cima-esquerda-quadrado-destaque, seta, cima, esquerda, quadrado, destaque, navegação |
| seta-cima-quadrado | Representa seta cima quadrado, útil para navegação, direção e fluxo de interface. | seta-cima-quadrado, seta, cima, quadrado, navegacao, navegação |
| seta-cima-quadrado-destaque | Representa seta cima quadrado destaque, útil para navegação, direção e fluxo de interface. | seta-cima-quadrado-destaque, seta, cima, quadrado, destaque, navegação |
| seta-cima-short | Representa seta cima short, útil para navegação, direção e fluxo de interface. | seta-cima-short, seta, cima, short, navegacao, navegação |
| seta-direita | Representa seta direita, útil para navegação, direção e fluxo de interface. | seta-direita, seta, direita, navegacao, fluxo, navegação |
| seta-direita-circulo-destaque | Representa seta direita circulo destaque, útil para navegação, direção e fluxo de interface. | seta-direita-circulo-destaque, seta, direita, circulo, destaque, navegação |
| seta-direita-quadrado | Representa seta direita quadrado, útil para navegação, direção e fluxo de interface. | seta-direita-quadrado, seta, direita, quadrado, navegacao, navegação |
| seta-direita-quadrado-destaque | Representa seta direita quadrado destaque, útil para navegação, direção e fluxo de interface. | seta-direita-quadrado-destaque, seta, direita, quadrado, destaque, navegação |
| seta-direita-short | Representa seta direita short, útil para navegação, direção e fluxo de interface. | seta-direita-short, seta, direita, short, navegacao, navegação |
| seta-esquerda | Representa seta esquerda, útil para navegação, direção e fluxo de interface. | seta-esquerda, seta, esquerda, navegacao, fluxo, navegação |
| seta-esquerda-circulo | Representa seta esquerda circulo, útil para navegação, direção e fluxo de interface. | seta-esquerda-circulo, seta, esquerda, circulo, navegacao, navegação |
| seta-esquerda-circulo-destaque | Representa seta esquerda circulo destaque, útil para navegação, direção e fluxo de interface. | seta-esquerda-circulo-destaque, seta, esquerda, circulo, destaque, navegação |
| seta-esquerda-direita | Representa seta esquerda direita, útil para navegação, direção e fluxo de interface. | seta-esquerda-direita, seta, esquerda, direita, navegacao, navegação |
| seta-esquerda-quadrado | Representa seta esquerda quadrado, útil para navegação, direção e fluxo de interface. | seta-esquerda-quadrado, seta, esquerda, quadrado, navegacao, navegação |
| seta-esquerda-quadrado-destaque | Representa seta esquerda quadrado destaque, útil para navegação, direção e fluxo de interface. | seta-esquerda-quadrado-destaque, seta, esquerda, quadrado, destaque, navegação |
| seta-esquerda-short | Representa seta esquerda short, útil para navegação, direção e fluxo de interface. | seta-esquerda-short, seta, esquerda, short, navegacao, navegação |
| seta-horario | Representa seta horario, útil para navegação, direção e fluxo de interface. | seta-horario, seta, horario, navegacao, fluxo, navegação |
| seta-through-coracao | Representa seta through coracao, útil para navegação, direção e fluxo de interface. | seta-through-coracao, seta, through, coracao, navegacao, navegação |
| seta-through-coracao-destaque | Representa seta through coracao destaque, útil para navegação, direção e fluxo de interface. | seta-through-coracao-destaque, seta, through, coracao, destaque, navegação |
| shadows | Representa shadows, útil para configuração, integrações e recursos digitais. | shadows, sistema, infraestrutura |
| shift | Representa shift, útil para configuração, integrações e recursos digitais. | shift, sistema, infraestrutura |
| shift-destaque | Representa shift destaque, útil para configuração, integrações e recursos digitais. | shift-destaque, shift, destaque, sistema, infraestrutura |
| signal | Representa signal, útil para configuração, integrações e recursos digitais. | signal, sistema, infraestrutura |
| simetria-horizontal | Representa simetria horizontal, útil para configuração, integrações e recursos digitais. | simetria-horizontal, simetria, horizontal, sistema, infraestrutura |
| simetria-vertical | Representa simetria vertical, útil para configuração, integrações e recursos digitais. | simetria-vertical, simetria, vertical, sistema, infraestrutura |
| sina-weibo | Representa sina weibo, útil para configuração, integrações e recursos digitais. | sina-weibo, sina, weibo, sistema, infraestrutura |
| sinal-numero-0 | Representa sinal numero 0, útil para configuração, integrações e recursos digitais. | sinal-numero-0, sinal, numero, sistema, infraestrutura, 0 |
| sinal-numero-1 | Representa sinal numero 1, útil para configuração, integrações e recursos digitais. | sinal-numero-1, sinal, numero, sistema, infraestrutura, 1 |
| sinal-numero-2 | Representa sinal numero 2, útil para configuração, integrações e recursos digitais. | sinal-numero-2, sinal, numero, sistema, infraestrutura, 2 |
| sinal-numero-3 | Representa sinal numero 3, útil para configuração, integrações e recursos digitais. | sinal-numero-3, sinal, numero, sistema, infraestrutura, 3 |
| sinal-numero-4 | Representa sinal numero 4, útil para configuração, integrações e recursos digitais. | sinal-numero-4, sinal, numero, sistema, infraestrutura, 4 |
| sinalizacao | Representa sinalizacao, útil para configuração, integrações e recursos digitais. | sinalizacao, sistema, infraestrutura |
| sinalizacao-destaque | Representa sinalizacao destaque, útil para configuração, integrações e recursos digitais. | sinalizacao-destaque, sinalizacao, destaque, sistema, infraestrutura |
| sinalizacao-numero-2 | Representa sinalizacao numero 2, útil para configuração, integrações e recursos digitais. | sinalizacao-numero-2, sinalizacao, numero, sistema, infraestrutura, 2 |
| sinalizacao-numero-2-destaque | Representa sinalizacao numero 2 destaque, útil para configuração, integrações e recursos digitais. | sinalizacao-numero-2-destaque, sinalizacao, numero, destaque, sistema, 2, infraestrutura |
| sinalizacao-split-destaque | Representa sinalizacao split destaque, útil para configuração, integrações e recursos digitais. | sinalizacao-split-destaque, sinalizacao, split, destaque, sistema, infraestrutura |
| sincronizar | Sincronização, repetição de processo ou reconciliação de dados. | sincronizar, sistema, infraestrutura, sincronizacao, repeticao |
| sino-cortado | Representa sino cortado, útil para configuração, integrações e recursos digitais. | sino-cortado, sino, cortado, sistema, infraestrutura |
| sino-cortado-destaque | Representa sino cortado destaque, útil para configuração, integrações e recursos digitais. | sino-cortado-destaque, sino, cortado, destaque, sistema, infraestrutura |
| sino-destaque | Representa sino destaque, útil para configuração, integrações e recursos digitais. | sino-destaque, sino, destaque, sistema, infraestrutura |
| site | Internet, alcance global, site ou público amplo. | site, sistema, infraestrutura, internet, alcance |
| skype | Representa skype, útil para configuração, integrações e recursos digitais. | skype, sistema, infraestrutura |
| slack | Representa slack, útil para configuração, integrações e recursos digitais. | slack, sistema, infraestrutura |
| sliders2-vertical | Representa sliders2 vertical, útil para configuração, integrações e recursos digitais. | sliders2-vertical, sliders2, vertical, sistema, infraestrutura |
| smartwatch | Representa smartwatch, útil para configuração, integrações e recursos digitais. | smartwatch, sistema, infraestrutura |
| snapchat | Representa snapchat, útil para configuração, integrações e recursos digitais. | snapchat, sistema, infraestrutura |
| snow2 | Representa snow2, útil para configuração, integrações e recursos digitais. | snow2, sistema, infraestrutura |
| snow3 | Representa snow3, útil para configuração, integrações e recursos digitais. | snow3, sistema, infraestrutura |
| sol | Representa sol, útil para configuração, integrações e recursos digitais. | sol, sistema, infraestrutura |
| sol-destaque | Representa sol destaque, útil para configuração, integrações e recursos digitais. | sol-destaque, sol, destaque, sistema, infraestrutura |
| sort-alpha-baixo | Representa sort alpha baixo, útil para navegação, direção e fluxo de interface. | sort-alpha-baixo, sort, alpha, baixo, navegacao, navegação |
| sort-alpha-baixo-alternativo | Representa sort alpha baixo alternativo, útil para navegação, direção e fluxo de interface. | sort-alpha-baixo-alternativo, sort, alpha, baixo, alternativo, navegação |
| sort-alpha-cima | Representa sort alpha cima, útil para navegação, direção e fluxo de interface. | sort-alpha-cima, sort, alpha, cima, navegacao, navegação |
| sort-alpha-cima-alternativo | Representa sort alpha cima alternativo, útil para navegação, direção e fluxo de interface. | sort-alpha-cima-alternativo, sort, alpha, cima, alternativo, navegação |
| sort-baixo | Representa sort baixo, útil para navegação, direção e fluxo de interface. | sort-baixo, sort, baixo, navegacao, fluxo, navegação |
| sort-baixo-alternativo | Representa sort baixo alternativo, útil para navegação, direção e fluxo de interface. | sort-baixo-alternativo, sort, baixo, alternativo, navegacao, navegação |
| sort-cima | Representa sort cima, útil para navegação, direção e fluxo de interface. | sort-cima, sort, cima, navegacao, fluxo, navegação |
| sort-cima-alternativo | Representa sort cima alternativo, útil para navegação, direção e fluxo de interface. | sort-cima-alternativo, sort, cima, alternativo, navegacao, navegação |
| sort-numeric-baixo | Representa sort numeric baixo, útil para navegação, direção e fluxo de interface. | sort-numeric-baixo, sort, numeric, baixo, navegacao, navegação |
| sort-numeric-baixo-alternativo | Representa sort numeric baixo alternativo, útil para navegação, direção e fluxo de interface. | sort-numeric-baixo-alternativo, sort, numeric, baixo, alternativo, navegação |
| sort-numeric-cima | Representa sort numeric cima, útil para navegação, direção e fluxo de interface. | sort-numeric-cima, sort, numeric, cima, navegacao, navegação |
| sort-numeric-cima-alternativo | Representa sort numeric cima alternativo, útil para navegação, direção e fluxo de interface. | sort-numeric-cima-alternativo, sort, numeric, cima, alternativo, navegação |
| sourceforge | Representa sourceforge, útil para configuração, integrações e recursos digitais. | sourceforge, sistema, infraestrutura |
| speedometer | Representa speedometer, útil para configuração, integrações e recursos digitais. | speedometer, sistema, infraestrutura |
| spotify | Representa spotify, útil para configuração, integrações e recursos digitais. | spotify, sistema, infraestrutura |
| steam | Representa steam, útil para configuração, integrações e recursos digitais. | steam, sistema, infraestrutura |
| strava | Representa strava, útil para configuração, integrações e recursos digitais. | strava, sistema, infraestrutura |
| stripe | Representa stripe, útil para configuração, integrações e recursos digitais. | stripe, sistema, infraestrutura |
| subscrito | Representa subscrito, útil para configuração, integrações e recursos digitais. | subscrito, sistema, infraestrutura |
| substack | Representa substack, útil para configuração, integrações e recursos digitais. | substack, sistema, infraestrutura |
| subtract | Representa subtract, útil para configuração, integrações e recursos digitais. | subtract, sistema, infraestrutura |
| suit-club | Representa suit club, útil para configuração, integrações e recursos digitais. | suit-club, suit, club, sistema, infraestrutura |
| suit-club-destaque | Representa suit club destaque, útil para configuração, integrações e recursos digitais. | suit-club-destaque, suit, club, destaque, sistema, infraestrutura |
| suit-coracao | Representa suit coracao, útil para configuração, integrações e recursos digitais. | suit-coracao, suit, coracao, sistema, infraestrutura |
| suit-coracao-destaque | Representa suit coracao destaque, útil para configuração, integrações e recursos digitais. | suit-coracao-destaque, suit, coracao, destaque, sistema, infraestrutura |
| suit-losango | Representa suit losango, útil para configuração, integrações e recursos digitais. | suit-losango, suit, losango, sistema, infraestrutura |
| suit-losango-destaque | Representa suit losango destaque, útil para configuração, integrações e recursos digitais. | suit-losango-destaque, suit, losango, destaque, sistema, infraestrutura |
| suit-spade | Representa suit spade, útil para configuração, integrações e recursos digitais. | suit-spade, suit, spade, sistema, infraestrutura |
| suit-spade-destaque | Representa suit spade destaque, útil para configuração, integrações e recursos digitais. | suit-spade-destaque, suit, spade, destaque, sistema, infraestrutura |
| suitcase2 | Representa suitcase2, útil para configuração, integrações e recursos digitais. | suitcase2, sistema, infraestrutura |
| suitcase2-destaque | Representa suitcase2 destaque, útil para configuração, integrações e recursos digitais. | suitcase2-destaque, suitcase2, destaque, sistema, infraestrutura |
| sunrise | Representa sunrise, útil para configuração, integrações e recursos digitais. | sunrise, sistema, infraestrutura |
| sunrise-destaque | Representa sunrise destaque, útil para configuração, integrações e recursos digitais. | sunrise-destaque, sunrise, destaque, sistema, infraestrutura |
| sunset | Representa sunset, útil para configuração, integrações e recursos digitais. | sunset, sistema, infraestrutura |
| sunset-destaque | Representa sunset destaque, útil para configuração, integrações e recursos digitais. | sunset-destaque, sunset, destaque, sistema, infraestrutura |
| superscript | Representa superscript, útil para configuração, integrações e recursos digitais. | superscript, sistema, infraestrutura |
| suporte | Atendimento, helpdesk, operação assistida ou suporte humano. | suporte, mensagem, contato, atendimento, helpdesk, comunicação |
| table | Representa table, útil para configuração, integrações e recursos digitais. | table, sistema, infraestrutura |
| tablet | Representa tablet, útil para configuração, integrações e recursos digitais. | tablet, sistema, infraestrutura |
| tablet-destaque | Representa tablet destaque, útil para configuração, integrações e recursos digitais. | tablet-destaque, tablet, destaque, sistema, infraestrutura |
| tablet-landscape | Representa tablet landscape, útil para configuração, integrações e recursos digitais. | tablet-landscape, tablet, landscape, sistema, infraestrutura |
| tablet-landscape-destaque | Representa tablet landscape destaque, útil para configuração, integrações e recursos digitais. | tablet-landscape-destaque, tablet, landscape, destaque, sistema, infraestrutura |
| taxi-frente | Representa taxi frente, útil para configuração, integrações e recursos digitais. | taxi-frente, taxi, frente, sistema, infraestrutura |
| taxi-frente-destaque | Representa taxi frente destaque, útil para configuração, integrações e recursos digitais. | taxi-frente-destaque, taxi, frente, destaque, sistema, infraestrutura |
| teclado | Representa teclado, útil para configuração, integrações e recursos digitais. | teclado, sistema, infraestrutura |
| teclado-destaque | Representa teclado destaque, útil para configuração, integrações e recursos digitais. | teclado-destaque, teclado, destaque, sistema, infraestrutura |
| tela-cheia | Representa tela cheia, útil para configuração, integrações e recursos digitais. | tela-cheia, tela, cheia, sistema, infraestrutura |
| tela-cheia-exit | Representa tela cheia exit, útil para configuração, integrações e recursos digitais. | tela-cheia-exit, tela, cheia, exit, sistema, infraestrutura |
| telefone | Telefone, contato direto ou suporte por voz. | telefone, mensagem, contato, direto, suporte, comunicação |
| telefone-adicionar | Representa telefone adicionar, útil para ações, comandos e interações diretas na interface. | telefone-adicionar, telefone, adicionar, acao, comando, ações |
| telefone-adicionar-destaque | Representa telefone adicionar destaque, útil para ações, comandos e interações diretas na interface. | telefone-adicionar-destaque, telefone, adicionar, destaque, acao, ações |
| telefone-avancar | Representa telefone avancar, útil para navegação, direção e fluxo de interface. | telefone-avancar, telefone, avancar, navegacao, fluxo, navegação |
| telefone-avancar-destaque | Representa telefone avancar destaque, útil para navegação, direção e fluxo de interface. | telefone-avancar-destaque, telefone, avancar, destaque, navegacao, navegação |
| telefone-destaque | Representa telefone destaque, útil para mensagens, contato e fluxos de atendimento. | telefone-destaque, telefone, destaque, mensagem, contato, comunicação |
| telefone-destaque-icon | Representa telefone destaque icon, útil para mensagens, contato e fluxos de atendimento. | telefone-destaque-icon, telefone, destaque, icon, mensagem, comunicação |
| telefone-flip | Representa telefone flip, útil para mensagens, contato e fluxos de atendimento. | telefone-flip, telefone, flip, mensagem, contato, comunicação |
| telefone-icon | Representa telefone icon, útil para mensagens, contato e fluxos de atendimento. | telefone-icon, telefone, icon, mensagem, contato, comunicação |
| telefone-inbound | Representa telefone inbound, útil para mensagens, contato e fluxos de atendimento. | telefone-inbound, telefone, inbound, mensagem, contato, comunicação |
| telefone-inbound-destaque | Representa telefone inbound destaque, útil para mensagens, contato e fluxos de atendimento. | telefone-inbound-destaque, telefone, inbound, destaque, mensagem, comunicação |
| telefone-landscape | Representa telefone landscape, útil para mensagens, contato e fluxos de atendimento. | telefone-landscape, telefone, landscape, mensagem, contato, comunicação |
| telefone-landscape-destaque | Representa telefone landscape destaque, útil para mensagens, contato e fluxos de atendimento. | telefone-landscape-destaque, telefone, landscape, destaque, mensagem, comunicação |
| telefone-minus | Representa telefone minus, útil para mensagens, contato e fluxos de atendimento. | telefone-minus, telefone, minus, mensagem, contato, comunicação |
| telefone-minus-destaque | Representa telefone minus destaque, útil para mensagens, contato e fluxos de atendimento. | telefone-minus-destaque, telefone, minus, destaque, mensagem, comunicação |
| telefone-outbound | Representa telefone outbound, útil para mensagens, contato e fluxos de atendimento. | telefone-outbound, telefone, outbound, mensagem, contato, comunicação |
| telefone-outbound-destaque | Representa telefone outbound destaque, útil para mensagens, contato e fluxos de atendimento. | telefone-outbound-destaque, telefone, outbound, destaque, mensagem, comunicação |
| telefone-remover | Representa telefone remover, útil para ações, comandos e interações diretas na interface. | telefone-remover, telefone, remover, acao, comando, ações |
| telefone-remover-destaque | Representa telefone remover destaque, útil para ações, comandos e interações diretas na interface. | telefone-remover-destaque, telefone, remover, destaque, acao, ações |
| telefone-vibrate | Representa telefone vibrate, útil para mensagens, contato e fluxos de atendimento. | telefone-vibrate, telefone, vibrate, mensagem, contato, comunicação |
| telefone-vibrate-destaque | Representa telefone vibrate destaque, útil para mensagens, contato e fluxos de atendimento. | telefone-vibrate-destaque, telefone, vibrate, destaque, mensagem, comunicação |
| telegram | Representa telegram, útil para configuração, integrações e recursos digitais. | telegram, sistema, infraestrutura |
| tema | Tema, visual, personalizacao ou design. | tema, sistema, infraestrutura, visual, personalizacao |
| tencent-qq | Representa tencent qq, útil para configuração, integrações e recursos digitais. | tencent-qq, tencent, sistema, infraestrutura, qq |
| terminal | Representa terminal, útil para configuração, integrações e recursos digitais. | terminal, sistema, infraestrutura |
| terminal-adicionar | Representa terminal adicionar, útil para ações, comandos e interações diretas na interface. | terminal-adicionar, terminal, adicionar, acao, comando, ações |
| terminal-destaque | Representa terminal destaque, útil para configuração, integrações e recursos digitais. | terminal-destaque, terminal, destaque, sistema, infraestrutura |
| terminal-menos | Representa terminal menos, útil para configuração, integrações e recursos digitais. | terminal-menos, terminal, menos, sistema, infraestrutura |
| terminal-remover | Representa terminal remover, útil para ações, comandos e interações diretas na interface. | terminal-remover, terminal, remover, acao, comando, ações |
| terminal-split | Representa terminal split, útil para configuração, integrações e recursos digitais. | terminal-split, terminal, split, sistema, infraestrutura |
| termometro | Representa termometro, útil para configuração, integrações e recursos digitais. | termometro, sistema, infraestrutura |
| termometro-half | Representa termometro half, útil para configuração, integrações e recursos digitais. | termometro-half, termometro, half, sistema, infraestrutura |
| termometro-high | Representa termometro high, útil para configuração, integrações e recursos digitais. | termometro-high, termometro, high, sistema, infraestrutura |
| termometro-low | Representa termometro low, útil para configuração, integrações e recursos digitais. | termometro-low, termometro, low, sistema, infraestrutura |
| termometro-neve | Representa termometro neve, útil para configuração, integrações e recursos digitais. | termometro-neve, termometro, neve, sistema, infraestrutura |
| termometro-sol | Representa termometro sol, útil para configuração, integrações e recursos digitais. | termometro-sol, termometro, sol, sistema, infraestrutura |
| tesoura | Representa tesoura, útil para configuração, integrações e recursos digitais. | tesoura, sistema, infraestrutura |
| textarea | Representa textarea, útil para configuração, integrações e recursos digitais. | textarea, sistema, infraestrutura |
| textarea-letra-t | Representa textarea letra t, útil para configuração, integrações e recursos digitais. | textarea-letra-t, textarea, letra, sistema, infraestrutura, t |
| textarea-resize | Representa textarea resize, útil para configuração, integrações e recursos digitais. | textarea-resize, textarea, resize, sistema, infraestrutura |
| texto-centro | Representa texto centro, útil para configuração, integrações e recursos digitais. | texto-centro, texto, centro, sistema, infraestrutura |
| texto-direita | Representa texto direita, útil para navegação, direção e fluxo de interface. | texto-direita, texto, direita, navegacao, fluxo, navegação |
| texto-esquerda | Representa texto esquerda, útil para navegação, direção e fluxo de interface. | texto-esquerda, texto, esquerda, navegacao, fluxo, navegação |
| texto-indentacao-direita | Representa texto indentacao direita, útil para navegação, direção e fluxo de interface. | texto-indentacao-direita, texto, indentacao, direita, navegacao, navegação |
| texto-indentacao-esquerda | Representa texto indentacao esquerda, útil para navegação, direção e fluxo de interface. | texto-indentacao-esquerda, texto, indentacao, esquerda, navegacao, navegação |
| texto-paragrafo | Representa texto paragrafo, útil para configuração, integrações e recursos digitais. | texto-paragrafo, texto, paragrafo, sistema, infraestrutura |
| texto-wrap | Representa texto wrap, útil para configuração, integrações e recursos digitais. | texto-wrap, texto, wrap, sistema, infraestrutura |
| threads | Representa threads, útil para configuração, integrações e recursos digitais. | threads, sistema, infraestrutura |
| threads-destaque | Representa threads destaque, útil para configuração, integrações e recursos digitais. | threads-destaque, threads, destaque, sistema, infraestrutura |
| three-dots | Representa three dots, útil para configuração, integrações e recursos digitais. | three-dots, three, dots, sistema, infraestrutura |
| three-dots-vertical | Representa three dots vertical, útil para configuração, integrações e recursos digitais. | three-dots-vertical, three, dots, vertical, sistema, infraestrutura |
| tiktok | Representa tiktok, útil para configuração, integrações e recursos digitais. | tiktok, sistema, infraestrutura |
| toggle2-off | Representa toggle2 off, útil para configuração, integrações e recursos digitais. | toggle2-off, toggle2, off, sistema, infraestrutura |
| toggle2-on | Representa toggle2 on, útil para configuração, integrações e recursos digitais. | toggle2-on, toggle2, sistema, infraestrutura, on |
| toggles2 | Representa toggles2, útil para configuração, integrações e recursos digitais. | toggles2, sistema, infraestrutura |
| tomada | Representa tomada, útil para configuração, integrações e recursos digitais. | tomada, sistema, infraestrutura |
| tornado | Representa tornado, útil para configuração, integrações e recursos digitais. | tornado, sistema, infraestrutura |
| translate | Representa translate, útil para configuração, integrações e recursos digitais. | translate, sistema, infraestrutura |
| transmissao | Representa transmissao, útil para configuração, integrações e recursos digitais. | transmissao, sistema, infraestrutura |
| transmissao-icon | Representa transmissao icon, útil para configuração, integrações e recursos digitais. | transmissao-icon, transmissao, icon, sistema, infraestrutura |
| transmissao-pino | Representa transmissao pino, útil para configuração, integrações e recursos digitais. | transmissao-pino, transmissao, pino, sistema, infraestrutura |
| transparency | Representa transparency, útil para configuração, integrações e recursos digitais. | transparency, sistema, infraestrutura |
| trash2 | Representa trash2, útil para configuração, integrações e recursos digitais. | trash2, sistema, infraestrutura |
| trash2-destaque | Representa trash2 destaque, útil para configuração, integrações e recursos digitais. | trash2-destaque, trash2, destaque, sistema, infraestrutura |
| trash3-destaque | Representa trash3 destaque, útil para configuração, integrações e recursos digitais. | trash3-destaque, trash3, destaque, sistema, infraestrutura |
| trello | Representa trello, útil para configuração, integrações e recursos digitais. | trello, sistema, infraestrutura |
| trem-freight-frente | Representa trem freight frente, útil para configuração, integrações e recursos digitais. | trem-freight-frente, trem, freight, frente, sistema, infraestrutura |
| trem-freight-frente-destaque | Representa trem freight frente destaque, útil para configuração, integrações e recursos digitais. | trem-freight-frente-destaque, trem, freight, frente, destaque, sistema, infraestrutura |
| trem-frente | Representa trem frente, útil para configuração, integrações e recursos digitais. | trem-frente, trem, frente, sistema, infraestrutura |
| trem-frente-destaque | Representa trem frente destaque, útil para configuração, integrações e recursos digitais. | trem-frente-destaque, trem, frente, destaque, sistema, infraestrutura |
| trem-lightrail-frente | Representa trem lightrail frente, útil para configuração, integrações e recursos digitais. | trem-lightrail-frente, trem, lightrail, frente, sistema, infraestrutura |
| trem-lightrail-frente-destaque | Representa trem lightrail frente destaque, útil para configuração, integrações e recursos digitais. | trem-lightrail-frente-destaque, trem, lightrail, frente, destaque, sistema, infraestrutura |
| triangulo | Representa triangulo, útil para configuração, integrações e recursos digitais. | triangulo, sistema, infraestrutura |
| triangulo-destaque | Representa triangulo destaque, útil para configuração, integrações e recursos digitais. | triangulo-destaque, triangulo, destaque, sistema, infraestrutura |
| triangulo-half | Representa triangulo half, útil para configuração, integrações e recursos digitais. | triangulo-half, triangulo, half, sistema, infraestrutura |
| trofeu | Representa trofeu, útil para configuração, integrações e recursos digitais. | trofeu, sistema, infraestrutura |
| trofeu-destaque | Representa trofeu destaque, útil para configuração, integrações e recursos digitais. | trofeu-destaque, trofeu, destaque, sistema, infraestrutura |
| tropical-storm | Representa tropical storm, útil para configuração, integrações e recursos digitais. | tropical-storm, tropical, storm, sistema, infraestrutura |
| trovao | Representa trovao, útil para configuração, integrações e recursos digitais. | trovao, sistema, infraestrutura |
| trovao-destaque | Representa trovao destaque, útil para configuração, integrações e recursos digitais. | trovao-destaque, trovao, destaque, sistema, infraestrutura |
| tsunami | Representa tsunami, útil para configuração, integrações e recursos digitais. | tsunami, sistema, infraestrutura |
| tux | Representa tux, útil para configuração, integrações e recursos digitais. | tux, sistema, infraestrutura |
| tv | Representa tv, útil para configuração, integrações e recursos digitais. | tv, sistema, infraestrutura |
| tv-destaque | Representa tv destaque, útil para configuração, integrações e recursos digitais. | tv-destaque, destaque, sistema, infraestrutura, tv |
| twitch | Representa twitch, útil para configuração, integrações e recursos digitais. | twitch, sistema, infraestrutura |
| twitter | Representa twitter, útil para configuração, integrações e recursos digitais. | twitter, sistema, infraestrutura |
| twitter-x | Representa twitter x, útil para configuração, integrações e recursos digitais. | twitter-x, twitter, sistema, infraestrutura, x |
| type | Representa type, útil para configuração, integrações e recursos digitais. | type, sistema, infraestrutura |
| type-bold | Representa type bold, útil para configuração, integrações e recursos digitais. | type-bold, type, bold, sistema, infraestrutura |
| type-h1 | Representa type h1, útil para configuração, integrações e recursos digitais. | type-h1, type, sistema, infraestrutura, h1 |
| type-h2 | Representa type h2, útil para configuração, integrações e recursos digitais. | type-h2, type, sistema, infraestrutura, h2 |
| type-h3 | Representa type h3, útil para configuração, integrações e recursos digitais. | type-h3, type, sistema, infraestrutura, h3 |
| type-h4 | Representa type h4, útil para configuração, integrações e recursos digitais. | type-h4, type, sistema, infraestrutura, h4 |
| type-h5 | Representa type h5, útil para configuração, integrações e recursos digitais. | type-h5, type, sistema, infraestrutura, h5 |
| type-h6 | Representa type h6, útil para configuração, integrações e recursos digitais. | type-h6, type, sistema, infraestrutura, h6 |
| type-italic | Representa type italic, útil para configuração, integrações e recursos digitais. | type-italic, type, italic, sistema, infraestrutura |
| type-strikethrough | Representa type strikethrough, útil para configuração, integrações e recursos digitais. | type-strikethrough, type, strikethrough, sistema, infraestrutura |
| type-underline | Representa type underline, útil para configuração, integrações e recursos digitais. | type-underline, type, underline, sistema, infraestrutura |
| typescript-icon | Representa typescript icon, útil para configuração, integrações e recursos digitais. | typescript-icon, typescript, icon, sistema, infraestrutura |
| ubuntu | Representa ubuntu, útil para configuração, integrações e recursos digitais. | ubuntu, sistema, infraestrutura |
| ui-checks | Representa ui checks, útil para configuração, integrações e recursos digitais. | ui-checks, checks, sistema, infraestrutura, ui |
| ui-radios | Representa ui radios, útil para configuração, integrações e recursos digitais. | ui-radios, radios, sistema, infraestrutura, ui |
| ui-radios-grade | Representa ui radios grade, útil para estrutura visual, composição e exibição de interface. | ui-radios-grade, radios, grade, layout, visualizacao, ui, visualização |
| uniao | Representa uniao, útil para configuração, integrações e recursos digitais. | uniao, sistema, infraestrutura |
| unindent | Representa unindent, útil para configuração, integrações e recursos digitais. | unindent, sistema, infraestrutura |
| unity | Representa unity, útil para configuração, integrações e recursos digitais. | unity, sistema, infraestrutura |
| universal-access | Representa universal access, útil para configuração, integrações e recursos digitais. | universal-access, universal, access, sistema, infraestrutura |
| universal-access-circulo | Representa universal access circulo, útil para configuração, integrações e recursos digitais. | universal-access-circulo, universal, access, circulo, sistema, infraestrutura |
| upc | Representa upc, útil para configuração, integrações e recursos digitais. | upc, sistema, infraestrutura |
| upc-scan | Representa upc scan, útil para configuração, integrações e recursos digitais. | upc-scan, upc, scan, sistema, infraestrutura |
| usb | Representa usb, útil para configuração, integrações e recursos digitais. | usb, sistema, infraestrutura |
| usb-c | Representa usb c, útil para configuração, integrações e recursos digitais. | usb-c, usb, sistema, infraestrutura, c |
| usb-c-destaque | Representa usb c destaque, útil para configuração, integrações e recursos digitais. | usb-c-destaque, usb, destaque, sistema, infraestrutura, c |
| usb-destaque | Representa usb destaque, útil para configuração, integrações e recursos digitais. | usb-destaque, usb, destaque, sistema, infraestrutura |
| usb-micro | Representa usb micro, útil para configuração, integrações e recursos digitais. | usb-micro, usb, micro, sistema, infraestrutura |
| usb-micro-destaque | Representa usb micro destaque, útil para configuração, integrações e recursos digitais. | usb-micro-destaque, usb, micro, destaque, sistema, infraestrutura |
| usb-mini | Representa usb mini, útil para configuração, integrações e recursos digitais. | usb-mini, usb, mini, sistema, infraestrutura |
| usb-mini-destaque | Representa usb mini destaque, útil para configuração, integrações e recursos digitais. | usb-mini-destaque, usb, mini, destaque, sistema, infraestrutura |
| usb-plug | Representa usb plug, útil para configuração, integrações e recursos digitais. | usb-plug, usb, plug, sistema, infraestrutura |
| usb-plug-destaque | Representa usb plug destaque, útil para configuração, integrações e recursos digitais. | usb-plug-destaque, usb, plug, destaque, sistema, infraestrutura |
| usb-symbol | Representa usb symbol, útil para configuração, integrações e recursos digitais. | usb-symbol, usb, symbol, sistema, infraestrutura |
| usuario | Usuário individual, perfil simples ou pessoa. | usuario, acesso, individual, perfil, pessoa, usuário, usuários |
| usuario-aprovado | Usuário aprovado, verificado ou vinculado com sucesso. | usuario-aprovado, usuario, aprovado, sistema, infraestrutura, usuário |
| usuarios | Grupo de usuários, equipe ou público coletivo. | usuarios, usuario, acesso, grupo, equipe, usuários |
| vagonete | Representa vagonete, útil para configuração, integrações e recursos digitais. | vagonete, sistema, infraestrutura |
| vagonete-loaded | Representa vagonete loaded, útil para configuração, integrações e recursos digitais. | vagonete-loaded, vagonete, loaded, sistema, infraestrutura |
| valentine | Representa valentine, útil para configuração, integrações e recursos digitais. | valentine, sistema, infraestrutura |
| valentine2 | Representa valentine2, útil para configuração, integrações e recursos digitais. | valentine2, sistema, infraestrutura |
| validar | Confirmação secundaria ou marca de verificação compacta. | validar, acao, comando, confirmacao, marca, ações |
| valor | Valor monetario, precificação ou referencia financeira. | valor, compra, pedido, monetario, precificacao, comércio, faturamento |
| ventilador | Representa ventilador, útil para configuração, integrações e recursos digitais. | ventilador, sistema, infraestrutura |
| vetor-caneta | Representa vetor caneta, útil para configuração, integrações e recursos digitais. | vetor-caneta, vetor, caneta, sistema, infraestrutura |
| vida-preserver | Representa vida preserver, útil para configuração, integrações e recursos digitais. | vida-preserver, vida, preserver, sistema, infraestrutura |
| vignette | Representa vignette, útil para configuração, integrações e recursos digitais. | vignette, sistema, infraestrutura |
| vimeo | Representa vimeo, útil para configuração, integrações e recursos digitais. | vimeo, sistema, infraestrutura |
| vinil | Representa vinil, útil para configuração, integrações e recursos digitais. | vinil, sistema, infraestrutura |
| vinil-destaque | Representa vinil destaque, útil para configuração, integrações e recursos digitais. | vinil-destaque, vinil, destaque, sistema, infraestrutura |
| virus | Representa virus, útil para configuração, integrações e recursos digitais. | virus, sistema, infraestrutura |
| virus2 | Representa virus2, útil para configuração, integrações e recursos digitais. | virus2, sistema, infraestrutura |
| visao-lista | Representa visao lista, útil para estrutura visual, composição e exibição de interface. | visao-lista, lista, layout, visualizacao, visao, visualização |
| visao-stacked | Representa visao stacked, útil para configuração, integrações e recursos digitais. | visao-stacked, stacked, sistema, infraestrutura, visao |
| visualizar | Visualização, preview, monitoramento ou permissão de ver. | visualizar, seguranca, permissao, visualizacao, preview, segurança, permissões |
| voltar | Retorno para etapa anterior, resposta ou volta contextual. | voltar, navegacao, fluxo, retorno, etapa, navegação |
| voltar-icon | Representa voltar icon, útil para navegação, direção e fluxo de interface. | voltar-icon, voltar, icon, navegacao, fluxo, navegação |
| volume-baixo | Representa volume baixo, útil para navegação, direção e fluxo de interface. | volume-baixo, volume, baixo, navegacao, fluxo, navegação |
| volume-baixo-destaque | Representa volume baixo destaque, útil para navegação, direção e fluxo de interface. | volume-baixo-destaque, volume, baixo, destaque, navegacao, navegação |
| volume-cima | Representa volume cima, útil para navegação, direção e fluxo de interface. | volume-cima, volume, cima, navegacao, fluxo, navegação |
| volume-cima-destaque | Representa volume cima destaque, útil para navegação, direção e fluxo de interface. | volume-cima-destaque, volume, cima, destaque, navegacao, navegação |
| volume-mute | Representa volume mute, útil para configuração, integrações e recursos digitais. | volume-mute, volume, mute, sistema, infraestrutura |
| volume-mute-destaque | Representa volume mute destaque, útil para configuração, integrações e recursos digitais. | volume-mute-destaque, volume, mute, destaque, sistema, infraestrutura |
| volume-off | Representa volume off, útil para configuração, integrações e recursos digitais. | volume-off, volume, off, sistema, infraestrutura |
| volume-off-destaque | Representa volume off destaque, útil para configuração, integrações e recursos digitais. | volume-off-destaque, volume, off, destaque, sistema, infraestrutura |
| vr | Representa vr, útil para configuração, integrações e recursos digitais. | vr, sistema, infraestrutura |
| webcam | Representa webcam, útil para configuração, integrações e recursos digitais. | webcam, sistema, infraestrutura |
| webcam-destaque | Representa webcam destaque, útil para configuração, integrações e recursos digitais. | webcam-destaque, webcam, destaque, sistema, infraestrutura |
| wechat | Representa wechat, útil para configuração, integrações e recursos digitais. | wechat, sistema, infraestrutura |
| whatsapp | Representa whatsapp, útil para configuração, integrações e recursos digitais. | whatsapp, sistema, infraestrutura |
| wifi | Representa wifi, útil para configuração, integrações e recursos digitais. | wifi, sistema, infraestrutura |
| wifi-numero-1 | Representa wifi numero 1, útil para configuração, integrações e recursos digitais. | wifi-numero-1, wifi, numero, sistema, infraestrutura, 1 |
| wifi-numero-2 | Representa wifi numero 2, útil para configuração, integrações e recursos digitais. | wifi-numero-2, wifi, numero, sistema, infraestrutura, 2 |
| wifi-off | Representa wifi off, útil para configuração, integrações e recursos digitais. | wifi-off, wifi, off, sistema, infraestrutura |
| wikipedia | Representa wikipedia, útil para configuração, integrações e recursos digitais. | wikipedia, sistema, infraestrutura |
| wind | Representa wind, útil para configuração, integrações e recursos digitais. | wind, sistema, infraestrutura |
| windows | Representa windows, útil para configuração, integrações e recursos digitais. | windows, sistema, infraestrutura |
| wordpress | Representa wordpress, útil para configuração, integrações e recursos digitais. | wordpress, sistema, infraestrutura |
| xbox | Representa xbox, útil para configuração, integrações e recursos digitais. | xbox, sistema, infraestrutura |
| yelp | Representa yelp, útil para configuração, integrações e recursos digitais. | yelp, sistema, infraestrutura |
| yin-yang | Representa yin yang, útil para configuração, integrações e recursos digitais. | yin-yang, yin, yang, sistema, infraestrutura |
| youtube | Representa youtube, útil para configuração, integrações e recursos digitais. | youtube, sistema, infraestrutura |
| zoom-in | Representa zoom in, útil para configuração, integrações e recursos digitais. | zoom-in, zoom, sistema, infraestrutura, in |
| zoom-out | Representa zoom out, útil para configuração, integrações e recursos digitais. | zoom-out, zoom, out, sistema, infraestrutura |

</details>

## Licenciamento

BRA-Icons é um produto proprietário. O uso do catálogo depende de autorização e das condições comerciais aplicáveis ao projeto.
