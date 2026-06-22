# FlowMesa — Fluxo do WhatsApp

## Visão geral

O WhatsApp é um dos canais de entrada do FlowMesa.

Ele serve para:
- receber mensagens do cliente
- iniciar atendimentos
- montar pedidos
- consultar histórico
- confirmar pedidos
- acompanhar o status da produção
- finalizar o atendimento

---

## Objetivo do fluxo

O objetivo do fluxo do WhatsApp é transformar uma conversa em um pedido organizado, com histórico salvo, cliente identificado e produção encaminhada para o setor correto.

---

## Etapas do atendimento

## 1. Entrada da mensagem

O cliente envia uma mensagem para o número da empresa.

Exemplos:
- saudação
- dúvida sobre produtos
- pedido de atendimento
- pedido direto
- retorno de conversa anterior

---

## 2. Identificação do cliente

O sistema identifica o cliente pelo número de telefone.

Se o cliente já existir:
- o histórico é recuperado
- a conversa continua de onde parou
- pedidos anteriores podem ser consultados

Se o cliente não existir:
- um novo cadastro pode ser iniciado
- a conversa começa do zero
- o nome e o telefone são registrados

---

## 3. Consulta do contexto

Antes de responder, o sistema consulta o contexto da conversa.

O contexto pode incluir:
- últimas mensagens
- último pedido
- status atual
- preferências do cliente
- etapa do atendimento

Isso ajuda a IA a responder de forma mais natural e útil.

---

## 4. Resposta automática

O sistema responde com base no contexto da conversa.

Respostas possíveis:
- saudação inicial
- envio do cardápio
- retomada de atendimento
- confirmação de itens
- solicitação de pagamento
- aviso de pedido em produção
- aviso de pedido pronto

---

## 5. Escolha dos itens

O cliente informa os produtos que deseja.

Exemplo:
- 2 espetos de carne
- 1 refrigerante
- 1 água

O sistema registra os itens no pedido.

---

## 6. Criação do pedido

Quando os itens são confirmados, o sistema cria o pedido.

O pedido precisa guardar:
- empresa
- cliente
- canal de origem
- itens
- quantidades
- observações
- subtotal
- total
- status

---

## 7. Separação por setor

Depois de criar o pedido, o sistema separa os itens por setor.

Exemplos:
- cozinha
- copa
- bebidas
- caixa
- retirada

Cada item segue para o setor correto.

---

## 8. Geração da fila de impressão

Depois da separação, o sistema gera os jobs de impressão.

Pode gerar:
- ticket da cozinha
- ticket da copa
- ticket de bebidas
- senha do pedido
- comprovante interno

---

## 9. Confirmação do pedido

O sistema envia ao cliente a confirmação do pedido.

A mensagem pode incluir:
- número do pedido
- valor total
- forma de pagamento
- tempo estimado
- status atual

---

## 10. Pagamento

Se o fluxo exigir pagamento antecipado, o sistema registra a forma escolhida.

Formas possíveis:
- dinheiro
- PIX
- cartão
- combinado

---

## 11. Produção

Com o pedido confirmado, a produção começa.

O sistema atualiza o status para algo como:
- confirmado
- em produção
- pronto

---

## 12. Finalização

Quando o pedido estiver pronto e entregue:
- o status é finalizado
- o histórico fica salvo
- a conversa pode ser encerrada
- o cliente pode ser atendido novamente depois

---

## Status da conversa

A conversa pode passar por estes estados:

- nova
- em atendimento
- aguardando resposta
- pedido em montagem
- pedido confirmado
- em produção
- pedido pronto
- finalizada

---

## Regras importantes

- toda conversa deve ser salva
- todo pedido deve ter vínculo com a conversa
- o sistema deve manter o contexto entre mensagens
- a IA deve usar o histórico para responder melhor
- o pedido do WhatsApp deve cair no mesmo núcleo do PDV
- a impressão deve acontecer sem depender da tela do operador

---

## Estrutura de dados relacionada

O fluxo do WhatsApp usa principalmente as tabelas:

- `clientes`
- `conversas`
- `pedidos`
- `pedido_itens`
- `pagamentos`
- `fila_impressao`
- `senhas`

---

## Exemplo de fluxo completo

1. O cliente manda "quero 2 espetos de carne e 1 refrigerante".
2. O sistema identifica o número.
3. O histórico é consultado.
4. A IA responde pedindo confirmação.
5. O pedido é criado no banco.
6. Os itens são separados por setor.
7. Os tickets são enviados para impressão.
8. O sistema informa o número do pedido.
9. O cliente acompanha o status até a entrega.

---

## Resumo

O fluxo do WhatsApp precisa ser simples, organizado e rastreável.

A conversa não é apenas um chat:
ela é a porta de entrada para o pedido, a produção e o caixa.
