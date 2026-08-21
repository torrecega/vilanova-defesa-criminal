# Vilanova Defesa Criminal

**No ar em [torrecega.github.io/vilanova-defesa-criminal](https://torrecega.github.io/vilanova-defesa-criminal/)**

Site cinematográfico de rolagem para um escritório de defesa criminal. Um vídeo gerado por IA toca para frente conforme o visitante desce a página e para trás quando sobe, as legendas contam a história ao redor dele, e abaixo do herói a página vira um site de verdade com uma única chamada para ação.

**Vilanova Defesa Criminal é um escritório fictício, criado como demonstração.** O nome, os depoimentos e as imagens são inventados e não representam pessoas ou casos reais. As faixas de honorários citadas são referências públicas de mercado.

## A ideia única

*A primeira hora.* Uma prisão se decide nas primeiras 24 horas, até a audiência de custódia, e não no julgamento. Cada seção da página é uma hora do relógio, de `00:00` a `24:00`, e o elemento assinatura é a linha de custódia: um fio vertical na lateral que se desenha conforme o visitante desce e acende a hora da seção ativa.

## Estrutura

```
site/               a pasta que vai para o ar
  index.html        a página inteira, sem etapa de build
  assets/           as imagens do herói
DESIGN-PACKAGE.md   todas as decisões criativas, escritas antes do código
review/             capturas de tela da auditoria
```

`site/` é HTML, CSS e JavaScript puro. Sem framework, sem npm, sem etapa de build.

## Ver localmente

```bash
npx http-server site -p 8213 -c-1
```

Abrir `http://127.0.0.1:8213/` no navegador. Abrir o `index.html` com dois cliques também funciona, mas mostra a versão de imagem parada, porque o navegador bloqueia o carregamento do vídeo em endereços de arquivo local.

## Estado atual

A página está completa e testada. O vídeo do herói ainda não foi gerado, então o site roda no seu estado de reserva: as duas imagens desenhadas à mão em SVG carregam a jornada, com as legendas e o clarão funcionando normalmente. Quando o vídeo existir, ele entra em `site/assets/hero-scrub.mp4` e o resto continua igual.

## Auditoria

| Verificação | Resultado |
|---|---|
| Contraste do pior pixel sob cada legenda | 6,18 / 5,92 / 5,41 / 5,61 (piso 3,5) |
| Teste de rolagem rápida, passos de 120px | 7, 7, 8 e 10 passos legíveis (mínimo 5) |
| Trechos da jornada sem texto na tela | nenhum |
| Erros no console | zero, no computador, no celular e em movimento reduzido |
| Vazamento horizontal em 375px, 1280px, 1440px | nenhum |
| Peso total | 55 KB de página, 9 KB de imagens |

## Uma ressalva honesta

O formulário mostra a mensagem de sucesso mas não envia nada, porque é um site estático sem servidor. Para receber mensagens de verdade, troque por um link de e-mail ou por um serviço gratuito de formulário. O telefone na tela é ilustrativo e está marcado como tal.
