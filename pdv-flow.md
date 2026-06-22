# FlowMesa — Fluxo do PDV

## Visão geral

O PDV do FlowMesa é a tela de venda no balcão.

Ele serve para:
- criar pedidos rapidamente
- adicionar itens ao carrinho
- calcular totais
- registrar pagamento
- emitir senha
- enviar impressão para os setores
- finalizar a venda com controle de caixa

---

## Objetivo do fluxo

O objetivo do PDV é permitir que o operador conclua uma venda com rapidez, clareza e poucos cliques, mantendo o pedido integrado ao caixa, estoque e impressão.

---

## Etapas do fluxo

## 1. Abertura de caixa

Antes de iniciar as vendas, o operador abre o caixa do turno.

Campos comuns:
- valor inicial
- usuário responsável
- horário de abertura
- observação opcional

Se o caixa não estiver aberto, o sistema pode bloquear ou limitar o uso do PDV.

---

## 2. Acesso ao PDV

O operador entra na tela principal do PDV.

A tela deve mostrar:
- busca de produtos
- categorias
- lista de itens
- carrinho atual
- total em tempo real
- forma de pagamento
- botão de finalizar venda
- botão de emitir senha
- botão de imprimir, se necessário

---

## 3. Busca e seleção de produtos

O operador busca os produtos e adiciona os itens ao carrinho.

A busca pode funcionar por:
- nome do produto
- categoria
- código interno

Ao clicar em um item:
- ele entra no carrinho
- a quantidade pode ser ajustada
- o total é atualizado automaticamente

---

## 4. Montagem do carrinho

O carrinho exibe os itens do pedido.

Cada item pode mostrar:
- nome
- quantidade
- valor unitário
- subtotal
- observação
- setor de produção

Ações possíveis:
- aumentar quantidade
- diminuir quantidade
- remover item
- editar observação

---

## 5. Observações

O operador pode incluir observações no pedido ou por item.

Exemplos:
- sem cebola
- bem passado
- embalar separado
- entregar na retirada

Essas observações podem seguir para a impressão de produção.

---

## 6. Desconto

Se o usuário tiver permissão, o sistema pode permitir desconto.

Pode ser:
- percentual
- valor fixo

Toda alteração deve ser registrada para controle.

---

## 7. Fechamento da venda

Depois de montar o pedido, o operador escolhe a forma de pagamento.

Formas possíveis:
- dinheiro
- PIX
- cartão
- combinado

O sistema deve calcular:
- subtotal
- desconto
- total
- troco, se houver

---

## 8. Registro do pedido

Quando a venda é confirmada, o sistema cria o pedido no banco.

O pedido deve conter:
- empresa
- cliente, se houver
- canal = pdv
- itens
- observações
- valores
- status inicial

---

## 9. Separação por setor

Depois de salvar o pedido, o sistema separa os itens por setor.

Exemplos:
- cozinha
- copa
- bebidas
- retirada

Cada setor recebe apenas o que precisa produzir.

---

## 10. Geração da fila de impressão

Com o pedido confirmado, o sistema gera os jobs de impressão.

Pode gerar:
- ticket de produção
- senha de retirada
- comprovante interno
- resumo do pedido

Cada job vai para a impressora configurada do setor.

---

## 11. Emissão de senha

Se o fluxo usar retirada, o sistema gera uma senha.

A senha pode mostrar:
- número da senha
- número do pedido
- horário de emissão
- status da chamada

Status possíveis:
- emitida
- impressa
- chamada
- atendida
- cancelada

---

## 12. Atualização do caixa

Quando a venda é finalizada, o pagamento entra no caixa do turno.

O sistema deve registrar:
- forma de pagamento
- valor recebido
- troco
- vínculo com o pedido
- movimentação no caixa

---

## 13. Baixa de estoque

Se o sistema estiver integrado ao estoque, os insumos são baixados automaticamente.

Isso permite:
- controlar consumo
- identificar faltas
- registrar movimentações
- gerar alertas de mínimo

---

## 14. Acompanhamento do pedido

Depois da venda, o operador pode consultar o pedido em andamento.

Status possíveis:
- aberto
- confirmado
- em produção
- pronto
- entregue
- concluído
- cancelado

---

## 15. Finalização

Quando tudo estiver concluído:
- o pedido é finalizado
- o caixa é atualizado
- o estoque é baixado
- a impressão fica registrada
- o histórico é salvo

---

## Regras importantes

- o PDV precisa ser rápido e simples
- o operador não pode fazer muitos cliques
- o total deve atualizar em tempo real
- a venda precisa ficar ligada ao caixa
- a impressão precisa ser automática quando necessário
- o pedido do PDV deve entrar no mesmo núcleo dos pedidos do WhatsApp
- falhas de impressão não podem travar a venda

---

## Estrutura de dados relacionada

O fluxo do PDV usa principalmente as tabelas:

- `usuarios`
- `clientes`
- `pedidos`
- `pedido_itens`
- `pagamentos`
- `caixas`
- `setores`
- `impressoras`
- `fila_impressao`
- `senhas`
- `estoque_itens`
- `movimentacoes_estoque`

---

## Exemplo de fluxo completo

1. O operador abre o caixa.
2. Entra na tela do PDV.
3. Busca os produtos.
4. Adiciona itens ao carrinho.
5. Ajusta observações, se necessário.
6. Escolhe a forma de pagamento.
7. Confirma a venda.
8. O sistema grava o pedido.
9. Os tickets de produção são enviados.
10. A senha é emitida.
11. O caixa é atualizado.
12. O estoque é baixado.
13. O pedido segue para acompanhamento.

---

## Resumo

O fluxo do PDV precisa ser direto, rápido e confiável.

Ele não é apenas uma tela de venda:
é uma parte central da operação, conectada ao pedido, ao caixa, ao estoque e à produção.
