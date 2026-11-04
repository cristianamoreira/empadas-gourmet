# Empadas Gourmet — protótipo do site de pedidos

Loja do amigo da Cristiana. Av. Miguel Perrela, 987 — loja 17, bairro Castelo,
Belo Horizonte (ao lado do supermercado EPA). Seg a sáb. Duas funcionárias.
Ainda sem delivery, sem Instagram e sem iFood.

## Como abrir

```bash
cd ~/empadas-gourmet
python3 -m http.server 4178
```

Depois abra <http://localhost:4178> no celular ou no navegador.
São dois arquivos estáticos, sem build e sem dependência:

| Arquivo | O que é |
|---|---|
| `index.html` | A loja — cardápio, carrinho, checkout, envio pelo WhatsApp |
| `painel.html` | A visão das funcionárias — fila de pedidos, "começar" / "está pronto" |

## Escopo: só o que existe hoje

Um único modo de pedido — **retirar na loja**. O cliente monta o pedido, escolhe
uma janela de 15 minutos e busca no balcão. Sem entrega, sem encomenda, sem
congelados: nada que a loja ainda não venda aparece na tela.

O cardápio é exatamente o do quadro da loja — 7 empadas, 9 salgados, 7 bebidas
e 6 bebidas quentes, com os preços reais. Nenhum item inventado.

O horário de funcionamento é respeitado: fora do expediente o site mostra
"fechado" e oferece as janelas do próximo dia de funcionamento, deixando isso
explícito na tela e na mensagem do WhatsApp.

## Pendências com o dono

1. ~~Número do WhatsApp~~ — **cadastrado**: (31) 99995-0503, celular pessoal do
   proprietário, provisório até ele providenciar um número do negócio
   (`CFG.whatsapp` no `index.html`). Recomendado migrar para WhatsApp Business.
2. **Horário real de abertura e fechamento** — hoje está chutado como 07–19h de
   seg a sex e 07–14h no sábado (`CFG.horario`).
3. **O que é "refresco" no combo de R$ 8,99** da vitrine? Se for refrigerante lata
   (R$ 7,00), o combo dá 38% de desconto sobre R$ 14,50. Se for o mini (R$ 3,50),
   dá 18%. O combo ainda não está no site por causa dessa dúvida.
4. **Tempo de preparo** — `CFG.prepMin` está em 20 min (intervalo entre o pedido
   e a primeira janela oferecida). Precisa bater com a realidade da cozinha.

## Ideias que ficaram de fora de propósito

Saíram do protótipo para ele não discutir hipótese, mas seguem na mesa:
caixas de congelados para assar em casa, uma linha de doces (a fachada anuncia
"DOCES E SALGADOS" e não há nenhum), encomenda para festa e coffee break, e
delivery. Entram quando a loja de fato oferecer.

## Observações sobre o cardápio atual

- **Preço único de R$ 7,50 em quase tudo.** Frango simples e frango com bacon e
  catupiry custam o mesmo ao cliente, mas não custam o mesmo para produzir. Em
  bairro de renda alta isso é margem perdida — vale um degrau de preço por sabor.
- **Seis das sete empadas são de frango.** Falta carne seca, camarão, palmito puro
  e uma opção vegetariana, que são os sabores que sustentam preço mais alto.
- **Nenhum doce**, apesar da fachada prometer.
- **Bebida quente tem margem melhor que salgado** e já está no cardápio — café
  e achocolatado combinam bem com uma linha de doces na parte da tarde.

## Limites do protótipo

Não há servidor. O pedido vai para o WhatsApp da loja e fica salvo no
`localStorage` do próprio navegador só para alimentar o `painel.html` na
demonstração. Num sistema real seriam necessários backend, notificação push com
alerta sonoro e pagamento por Pix integrado.

## Decisão ainda em aberto

Construir produto próprio, contratar plataforma pronta (Goomer R$ 59–224/mês,
Cardápio Web, Anota AI) ou um híbrido. Este protótipo serve justamente para o
dono opinar antes dessa escolha — ele é descartável.
