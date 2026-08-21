# Pacote de Design: Vilanova Defesa Criminal

Documento único com todas as decisões criativas do site. Escrito antes de qualquer geração de imagem ou vídeo. A Fase 8 (construção) consome este documento e não inventa nada por fora dele.

**Duas regras que governam este arquivo:**

1. Toda linha de texto marcada como copy vai pro site **exatamente como está escrita aqui**. A construção liga os fios, não reescreve as palavras.
2. Os números de faixa de banda e ritmo são **pontos de partida**, validados depois pelo teste de rolagem rápida.

Nível: Tier 1, uma tomada única de 6 segundos rolada pelo scroll.
Idioma do site: português do Brasil.

---

## 1. A premissa da marca

**A primeira hora.**

Uma prisão não se decide no julgamento. Ela se decide nas primeiras horas, enquanto a família ainda está tentando entender o que aconteceu. A lei dá 24 horas até a audiência de custódia, e é nesse intervalo que se define quem dorme em casa. O site inteiro ensina essa ideia e a transforma em urgência calma: cada seção é uma hora do relógio, o momento interativo faz o visitante praticar o conselho mais importante do período, e a única chamada pra ação é falar com um advogado agora, enquanto o relógio ainda corre.

Se uma seção não serve a essa ideia, ela não entra na página.

---

## 2. A paleta em tokens CSS

Tirada do mundo do vídeo: concreto frio de corredor de madrugada, poeira na luz, e a sala acesa no fim da descida. O vídeo vai do escuro pra luz, então a página abaixo dele vive na luz. Essa é a direção única: **da madrugada para a luz**.

Valores provisórios. Os finais saem amostrados da filmagem aprovada, depois do portão do vídeo.

```css
:root{
  --canvas:#E3E3DF;        /* concreto claro e frio, nunca branco puro */
  --panel:#EFEFEB;         /* cards e superfícies elevadas */
  --deep:#12161A;          /* o escuro do corredor: herói, rodapé, blocos de contraste */
  --accent:#16394F;        /* azul-tinta. A chamada pra ação e ênfase rara */
  --accent-hover:#1E4E6B;
  --accent-muted:#AFBCC5;  /* nível sussurro: bordas, brilhos, partículas */
  --text-primary:#12161A;
  --text-secondary:#585F65;
}
```

**Desvio declarado em voz alta:** a skill proíbe o visual de tela creme com serifa como reflexo automático. Aqui a tela clara não é um reflexo, é o destino da jornada: o vídeo termina numa sala acesa e a página continua dentro dessa luz. O tom é concreto frio, não creme, o acento é azul-tinta e não terracota, e o esqueleto da página é a linha de custódia, não o layout padrão. Os tons finais saem da própria filmagem.

O acento aparece em doses raras: o botão de chamada, os estados de foco, as marcas de hora acesas na linha de custódia. Em mais nenhum lugar.

---

## 3. O trio tipográfico

| Papel | Fonte | Pesos |
|---|---|---|
| Display | **Instrument Serif** | 400, 400 itálico |
| Corpo | **Archivo** | 400, 500 |
| Mono | **JetBrains Mono** | 400, 500 |

A serifa tem corte afiado e contraste alto, que lê como documento e não como boutique. A Archivo é quieta e tem acentuação portuguesa correta. A mono só aparece nas marcas de hora (`00:00`, `12:00`, `24:00`) e em rótulos pequenos, que é onde ela faz o relógio parecer um registro real.

Nada de Inter ou Roboto em display. Fontes cortadas só nos pesos usados, com `preconnect`.

---

## 4. O mapa de bandas do herói

O vídeo desce um corredor de concreto na madrugada, atravessa uma porta de vidro num estouro de luz, e repousa numa sala acesa com a luminária ligada e uma cadeira puxada.

A ação vive no centro do quadro (o ponto de fuga do corredor), então as bandas 1 a 3 moram no terço inferior, sobre a região mais calma e escura. A banda 4 sobe pro terço superior, porque o quadro final tem a mesa embaixo e espaço limpo em cima.

| Banda | Faixa (validada) | Momento da filmagem | Copy (literal) | Entrada |
|---|---|---|---|---|
| 1 | 0.00 a 0.22 | corredor escuro, a câmera começa a descer | "São três da manhã." | **descida**: as palavras deslizam pra baixo e assentam |
| 2 | 0.20 a 0.46 | a descida acelera, poeira atravessa a luz fria | "O relógio já começou a correr." | **poeira**: as letras saem de um desfoque suave, escalonadas |
| 3 | 0.44 a 0.72 | atravessa a porta de vidro, clarão e gotas na lente | "Em 24 horas, um juiz decide quem dorme em casa." | **clarão**: o texto chega junto com o estouro de luz e assenta |
| 4 | 0.70 a 1.00 | a sala acesa, a mesa, a cadeira puxada, repouso | "A luz aqui fica acesa a noite inteira." | **repouso**: sobe e para. O botão sobe por último |

As faixas acima já não são mais pontos de partida: o teste de rolagem rápida foi rodado e mexeu nelas. As faixas originais deixavam três buracos sem texto nenhum na tela, entre uma fala e a outra. Agora elas se sobrepõem de propósito, uma some enquanto a outra nasce. Altura do herói: 600vh.

Resultado medido do teste, em passos de rolagem de 120px: cada fala fica totalmente legível por 7, 7, 8 e 10 passos seguidos, contra o mínimo de 5. Em passos agressivos de 360px nenhuma fala é pulável. Trechos sem texto na tela: nenhum.

Botão da banda 4, e única chamada da página inteira: **"Falar com um advogado agora"**

Cada banda ganha um platô longo totalmente visível, com rampas curtas nas bordas, medido em distância de rolagem e não em segundos. Nenhuma banda pode ser pulada num passo de 360px.

---

## 5. O bloco do herói estático

O que aparece no celular e em movimento reduzido, composto sobre o quadro final (a sala acesa), sem jornada por trás.

- **Título:** "Em 24 horas, um juiz decide quem dorme em casa."
- **Subtítulo:** "Defesa criminal com plantão de verdade. Você fala com um advogado, não com uma caixa postal."
- **Botão:** "Falar com um advogado agora"

---

## 6. O plano abaixo da dobra

Todas as seções apontam pra mesma âncora de chamada. Nenhuma vizinha repete o esqueleto da anterior.

### Barra de navegação
`Vilanova` + `Defesa Criminal` à esquerda. À direita, o rótulo mono `PLANTÃO 24H` e o botão da chamada.

### 00:00 · A primeira hora
**Título:** "A defesa começa antes do processo."
**Texto:** "Quase tudo que decide uma prisão acontece antes de qualquer julgamento. Nas primeiras horas o boletim é escrito, as versões são registradas e a pessoa presta declarações sem saber o peso do que fala. Depois disso, cada erro custa meses pra desfazer. É por isso que a gente atende de madrugada."

### 01:00 · O que fazer agora
Três passos, cada um com sua própria imagem gerada. Todos recebem tratamento igual, porque um passo sem imagem lê como buraco.

1. **"Não explique nada na delegacia."**
   "A vontade de esclarecer é natural e é a armadilha mais comum. Tudo que for dito ali é registrado e pode ser usado depois."
2. **"Peça pra pessoa ficar em silêncio."**
   "O silêncio não conta contra ninguém. Ele vale até o advogado chegar, e chegar é problema nosso."
3. **"Separe RG, CPF, comprovante de residência e de trabalho."**
   "Esses papéis mostram vínculo com o lugar onde a pessoa vive. Eles pesam na audiência de custódia."

### 12:00 · Segure o silêncio (o momento interativo)
O visitante pressiona e segura. Enquanto segura, o ruído da tela se acalma: linhas trêmulas atrás do bloco vão se aquietando até o silêncio. Soltar cedo deixa o ruído voltar suave, nunca de estalo. Completar acende os três cartões em sequência.

- **Rótulo do controle:** "Segure para silenciar"
- **Enquanto segura:** "Segurando..."
- **Ao completar:** "Silêncio."
- **Cartão 1:** "O que você diz na delegacia vira prova."
- **Cartão 2:** "O silêncio não é confissão. É direito."
- **Cartão 3:** "Ele vale até o advogado chegar."

Em movimento reduzido, os três cartões já aparecem acesos, sem precisar segurar.

### 18:00 · Quem já passou por isso
Três falas curtas, em linguagem de cliente. Layout diferente das seções vizinhas: fitas horizontais, não cards em grade.

- "Liguei às quatro da manhã achando que ia cair na caixa postal. Um advogado atendeu."
- "Foi a primeira vez em três dias que alguém me explicou o que estava acontecendo."
- "Meu filho dormiu em casa na noite seguinte. Eu não achava que era possível."

### 20:00 · Quanto custa, sem enrolação
**Título:** "O preço, antes de você perguntar."
**Texto de abertura:** "Quase nenhum site de advogado fala isso. A gente fala, porque quem está desesperado merece saber onde está pisando."

| Situação | Faixa |
|---|---|
| Audiência de custódia isolada | R$ 2.000 a R$ 8.000 |
| Caso simples, acompanhamento completo | a partir de R$ 3.000 |
| Caso com perícia ou risco de preventiva | acima de R$ 15.000 |

**Nota abaixo da tabela:** "São faixas, não etiquetas. O valor final depende do que aconteceu, de onde o processo está e da urgência. Parcelamento é possível e é comum. O combinado sai por escrito antes de qualquer coisa."

### 22:00 · As perguntas que ninguém responde
1. **"Por que não usar a Defensoria Pública?"**
   "A Defensoria é um direito seu e os defensores são bons. A diferença é volume. Um defensor cuida de centenas de casos ao mesmo tempo. Contratar não compra competência, compra atenção e velocidade."
2. **"Vocês atendem de madrugada mesmo?"**
   "Sim. O telefone do plantão toca no celular de um advogado, não numa central."
3. **"E se vocês sumirem depois que eu pagar?"**
   "Você recebe o número direto de quem cuida do seu caso e um retorno a cada movimentação. Se ficarmos 48 horas sem falar com você, a gente está errado."
4. **"Meu parente já falou na delegacia. Estragou tudo?"**
   "Na maioria das vezes, não. Muita coisa dita ali pode ser contextualizada ou contestada depois. Quanto antes a gente entrar, mais fácil."
5. **"Quanto tempo demora?"**
   "A audiência de custódia é em até 24 horas depois da prisão. O resto depende do caso, e a gente diz um prazo real na primeira conversa, não um prazo bonito."

### 24:00 · A chamada final
**Título:** "O relógio não para enquanto você decide."
**Texto:** "Ligue agora. Se preferir escrever, escreva. Alguém responde."
**Botão principal:** "Falar com um advogado agora"

**Formulário:**
- Campo 1: "Seu nome"
- Campo 2: "Seu telefone"
- Campo 3: "O que aconteceu" / placeholder: "Escreva do seu jeito. Não precisa de termo técnico."
- Botão: "Enviar agora"
- Sucesso: "Recebido. Um advogado liga pra você em minutos, não em dias."

**Tratamento do formulário neste site:** estado de sucesso só no navegador. A mensagem não vai pra lugar nenhum, porque este é um site de demonstração sem servidor. A chamada de verdade é o botão de telefone, que funciona de fato. Se um dia isso virar um escritório real, a troca é de um minuto: ou um link de e-mail, ou um serviço gratuito de formulário que entrega na caixa de entrada.

### Rodapé
Marca, o rótulo mono `PLANTÃO 24H`, telefone, e a declaração:

"Vilanova Defesa Criminal é um escritório fictício, criado como demonstração de site. O nome, os depoimentos e as imagens são inventados e não representam pessoas ou casos reais. As faixas de honorários citadas são referências públicas de mercado."

---

## 7. O plano da camada vetorial

**O elemento assinatura: a linha de custódia.** Um fio vertical de 1px na lateral esquerda, correndo a página inteira, com marcas de hora em mono (`00:00`, `01:00`, `12:00`, `18:00`, `20:00`, `22:00`, `24:00`). Cada seção está ancorada numa hora. O fio se desenha conforme o visitante desce, e a marca da seção ativa acende no acento. É a espinha da página: tirar a linha muda a página inteira, porque é ela que transforma uma pilha de seções numa contagem regressiva.

Outros elementos, todos desenhados à mão em SVG:
- **Divisores de seção** como marcas de régua curtas, não linhas cheias.
- **Poeira em suspensão**, nível sussurro, sobre a camada de fundo fixa. Doze partículas, deriva lenta, opacidade baixíssima.
- **Uma camada de fundo fixa atrás de tudo:** um degradê de luz muito suave que deriva num ciclo de 90 segundos, no mundo da filmagem, pra rolar parecer atravessar um lugar e não passar por caixas empilhadas.

Movimento reduzido é honrado em tudo: a linha aparece desenhada por inteiro, as partículas param, os estados finais ficam visíveis.

---

## 8. A lista de engenharia

A construção segue o padrão inteiro, sem meia-memória:

- Vídeo buscado como Blob, com anel de carregamento honesto quando passar de 8 MB.
- Tempo exibido interpolado num laço rAF que descansa, normalizado por delta de tempo.
- Buscas de quadro com trava, pra nunca sobrepor.
- Escrita no DOM só quando muda.
- Ritmo de banda em distância de rolagem, validado pelo teste de rolagem rápida (passos de 120px, 240px e 360px).
- Sistema de legibilidade em quatro camadas, auditado contra o **pior quadro** de cada banda, mínimo 3.5:1.
- Os cinco portões do herói estático, mantidos vivos com escutas de mudança.
- A página fica completa e bonita mesmo se o vídeo nunca carregar.
- Movimento reduzido honrado nos dois sentidos, ao vivo.
- `overflow-x: clip` em `html` e `body`, com `hidden` declarado antes como reserva.
- Marcos semânticos, link de pular pro conteúdo, hierarquia real de títulos, vídeo decorativo fora da ordem de tabulação.
- Contraste calculado, não chutado: 4.5:1 em texto corrido, 3:1 em texto grande e bordas.
- Alvos de toque de no mínimo 44px em ponteiro grosso.
- Título real, meta descrição, `theme-color` e favicon SVG embutido com a marca.
- `og:image` e `og:url` deixados com marcação `<!-- DEPLOY STEP -->` e preenchidos com a URL real na hora de publicar.
- O padrão de site inteiro animado: linhas que se desenham, poeira sussurrada, brilho suave em texto-chave, uma entrada única por momento, suavização em tudo.

---

## 9. O portão do texto

Todo texto voltado ao visitante escrito acima vai pro site literalmente. A página construída precisa passar o portão da Fase 9 antes de qualquer pessoa ver: zero travessões longos, zero palavras de catálogo corporativo, e a varredura de vícios de escrita automática no corpo do texto.

Os recursos deliberados desta marca são artesanato e ficam: as horas como títulos de seção, o trio "Não explique. Peça silêncio. Separe os papéis.", e a batida curta "Silêncio." no fim do momento interativo. A varredura caça o que entrou sozinho, não o que foi escolhido.
