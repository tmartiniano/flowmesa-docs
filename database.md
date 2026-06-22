# FlowMesa — Banco de Dados

## Visão geral

O banco de dados do FlowMesa foi desenhado para centralizar pedidos, clientes, conversas, caixa, estoque, impressão e configurações da empresa.

A regra principal é simples: todo dado importante precisa estar vinculado à empresa.

---

## Princípio principal

Todas as tabelas principais devem ter o campo:

- `empresa_id`

Isso garante:

- separação por cliente
- suporte a multiempresa
- segurança
- escalabilidade
- organização para SaaS

---

## Tabelas principais

## 1. empresas

Armazena os dados de cada empresa que usa o sistema.

Campos sugeridos:
- `id`
- `nome`
- `razao_social`
- `cnpj`
- `telefone`
- `email`
- `status`
- `created_at`
- `updated_at`

---

## 2. usuarios

Armazena os operadores do sistema.

Campos sugeridos:
- `id`
- `empresa_id`
- `nome`
- `email`
- `senha`
- `perfil`
- `status`
- `created_at`
- `updated_at`

Perfis possíveis:
- operador
- caixa
- gerente
- administrador

---

## 3. clientes

Armazena os consumidores finais.

Campos sugeridos:
- `id`
- `empresa_id`
- `nome`
- `telefone`
- `documento`
- `observacao`
- `status`
- `created_at`
- `updated_at`

---

## 4. conversas

Armazena o histórico do WhatsApp.

Campos já existentes:
- `id`
- `remotejid`
- `pushname`
- `role`
- `content`
- `created_at`

Campos adicionais sugeridos:
- `empresa_id`
- `cliente_id`
- `pedido_id`
- `status_conversa`
- `canal`
- `updated_at`

Status possíveis:
- nova
- em atendimento
- aguardando resposta
- pedido em montagem
- pedido confirmado
- finalizada

---

## 5. categorias

Armazena a organização dos produtos.

Campos sugeridos:
- `id`
- `empresa_id`
- `nome`
- `ordem`
- `status`
- `created_at`
- `updated_at`

---

## 6. produtos

Armazena os itens vendidos.

Campos sugeridos:
- `id`
- `empresa_id`
- `categoria_id`
- `nome`
- `descricao`
- `preco`
- `codigo_interno`
- `setor_id`
- `status`
- `imprime_senha`
- `created_at`
- `updated_at`

---

## 7. pedidos

Armazena o pedido principal.

Campos sugeridos:
- `id`
- `empresa_id`
- `cliente_id`
- `conversa_id`
- `canal`
- `numero_pedido`
- `status`
- `subtotal`
- `desconto`
- `total`
- `observacao_geral`
- `created_at`
- `updated_at`

Canais possíveis:
- whatsapp
- pdv
- interno

Status possíveis:
- rascunho
- aberto
- confirmado
- em_producao
- pronto
- entregue
- concluido
- cancelado

---

## 8. pedido_itens

Armazena os itens de cada pedido.

Campos sugeridos:
- `id`
- `empresa_id`
- `pedido_id`
- `produto_id`
- `quantidade`
- `valor_unitario`
- `subtotal`
- `observacao`
- `setor_id`
- `created_at`
- `updated_at`

---

## 9. pagamentos

Armazena os pagamentos ligados aos pedidos.

Campos sugeridos:
- `id`
- `empresa_id`
- `pedido_id`
- `caixa_id`
- `forma_pagamento`
- `valor`
- `status`
- `created_at`
- `updated_at`

Formas de pagamento possíveis:
- dinheiro
- pix
- cartao
- combinado

Status possíveis:
- pendente
- aprovado
- cancelado
- estornado

---

## 10. caixas

Armazena a abertura e fechamento do caixa.

Campos sugeridos:
- `id`
- `empresa_id`
- `usuario_id`
- `valor_abertura`
- `valor_fechamento`
- `status`
- `diferenca`
- `aberto_em`
- `fechado_em`
- `created_at`
- `updated_at`

Status possíveis:
- aberto
- fechado

---

## 11. movimentacoes_caixa

Armazena entradas e saídas do caixa.

Campos sugeridos:
- `id`
- `empresa_id`
- `caixa_id`
- `tipo`
- `valor`
- `descricao`
- `pedido_id`
- `created_at`
- `updated_at`

Tipos possíveis:
- entrada
- saida
- ajuste
- cancelamento

---

## 12. setores

Armazena os setores de produção.

Campos sugeridos:
- `id`
- `empresa_id`
- `nome`
- `ordem`
- `status`
- `created_at`
- `updated_at`

Setores comuns:
- cozinha
- copa
- bebidas
- caixa
- retirada

---

## 13. impressoras

Armazena as impressoras configuradas.

Campos sugeridos:
- `id`
- `empresa_id`
- `nome`
- `tipo`
- `conexao`
- `ip`
- `porta`
- `setor_id`
- `status`
- `created_at`
- `updated_at`

Tipos possíveis:
- rede
- usb

Status possíveis:
- ativa
- inativa
- erro

---

## 14. fila_impressao

Armazena os jobs de impressão.

Campos sugeridos:
- `id`
- `empresa_id`
- `pedido_id`
- `pedido_item_id`
- `setor_id`
- `impressora_id`
- `tipo_documento`
- `payload`
- `status`
- `tentativas`
- `erro`
- `created_at`
- `updated_at`

Tipos de documento:
- producao
- senha
- comprovante
- resumo
- reimpressao

Status possíveis:
- pendente
- enviado
- impresso
- falhou
- reprocessando
- cancelado

---

## 15. senhas

Armazena as senhas emitidas.

Campos sugeridos:
- `id`
- `empresa_id`
- `pedido_id`
- `numero`
- `status`
- `emitida_em`
- `chamada_em`
- `atendida_em`
- `created_at`
- `updated_at`

Status possíveis:
- emitida
- impressa
- chamada
- atendida
- cancelada

---

## 16. estoque_itens

Armazena os itens do estoque.

Campos sugeridos:
- `id`
- `empresa_id`
- `nome`
- `unidade`
- `saldo_atual`
- `saldo_minimo`
- `status`
- `created_at`
- `updated_at`

---

## 17. movimentacoes_estoque

Armazena entradas e saídas do estoque.

Campos sugeridos:
- `id`
- `empresa_id`
- `estoque_item_id`
- `tipo`
- `quantidade`
- `pedido_id`
- `descricao`
- `created_at`
- `updated_at`

Tipos possíveis:
- entrada
- saida
- ajuste
- perda
- consumo

---

## Relacionamentos principais

### empresas
É a tabela principal.  
Todas as outras tabelas importantes devem apontar para ela via `empresa_id`.

### categorias
- uma empresa tem várias categorias

### produtos
- um produto pertence a uma categoria
- um produto pode estar ligado a um setor

### pedidos
- um pedido pertence a um cliente
- um pedido pode estar ligado a uma conversa
- um pedido possui vários itens
- um pedido pode ter vários pagamentos

### pedido_itens
- cada item pertence a um pedido
- cada item aponta para um produto
- cada item pode apontar para um setor

### caixas
- um caixa pertence a uma empresa
- um caixa pode ter vários pagamentos e movimentações

### setores
- um setor pode ter várias impressoras
- um setor pode receber vários itens de pedido

### fila_impressao
- cada job pertence a um pedido
- cada job pode estar ligado a um item
- cada job aponta para setor e impressora

### estoque_itens
- cada item de estoque pode ter várias movimentações

---

## Regras de integridade

- um pedido sempre deve pertencer a uma empresa
- um item de pedido sempre deve pertencer a um pedido
- um pagamento sempre deve estar ligado a um pedido
- uma impressão sempre deve ser rastreável
- uma movimentação de estoque deve ficar registrada
- uma conversa deve manter o histórico do atendimento

---

## Regras de status

## Pedido
- rascunho
- aberto
- confirmado
- em_producao
- pronto
- entregue
- concluido
- cancelado

## Conversa
- nova
- em atendimento
- aguardando resposta
- pedido em montagem
- pedido confirmado
- finalizada

## Caixa
- aberto
- fechado

## Impressão
- pendente
- enviado
- impresso
- falhou
- reprocessando
- cancelado

## Senha
- emitida
- impressa
- chamada
- atendida
- cancelada

---

## Regras importantes para o MVP

Para a primeira versão, o banco precisa obrigatoriamente suportar:

- cadastro de empresa
- cadastro de usuários
- cadastro de clientes
- cadastro de produtos
- cadastro de pedidos
- cadastro de itens do pedido
- registro de pagamentos
- abertura e fechamento de caixa
- controle de setores
- cadastro de impressoras
- fila de impressão
- emissão de senha
- movimentações de estoque
- histórico de conversa

---

## Resumo

O banco de dados do FlowMesa precisa ser simples, organizado e preparado para crescer.

A estrutura deve garantir que:

- o pedido seja único
- a empresa seja sempre identificada
- a impressão seja rastreável
- o caixa seja confiável
- o estoque seja atualizado
- o WhatsApp mantenha o histórico
- o sistema possa virar SaaS no futuro
