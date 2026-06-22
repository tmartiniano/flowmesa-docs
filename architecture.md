# FlowMesa — Arquitetura

## Visão geral

O FlowMesa é um sistema de operação para atendimento via WhatsApp, balcão, PDV, caixa, estoque e impressão por setor.

A proposta é centralizar tudo em um único fluxo de pedido, para que o sistema funcione de forma organizada e escalável.

---

## Objetivo da arquitetura

A arquitetura do FlowMesa foi pensada para:

- unificar pedidos de diferentes canais
- organizar a produção por setor
- registrar caixa e estoque
- permitir impressão em rede ou USB
- facilitar a evolução para SaaS
- manter o sistema documentado e modular

---

## Camadas do sistema

### 1. Camada de entrada
Responsável por receber as interações do cliente ou operador.

Canais principais:
- WhatsApp
- PDV de balcão
- painel administrativo

### 2. Camada de orquestração
Responsável por decidir o que acontece com cada evento recebido.

Componentes:
- n8n
- automações
- fluxos de atendimento
- integração com IA, se necessário

### 3. Camada de negócio
Responsável por armazenar e processar os dados do sistema.

Base de dados:
- Supabase

### 4. Camada de execução física
Responsável por realizar a saída no mundo real.

Componentes:
- impressora de rede
- impressora USB com agente local
- senhas de retirada
- tickets de produção

---

## Serviços principais

### WhatsApp
Canal de atendimento ao cliente.

Funções:
- receber mensagens
- responder automaticamente
- manter histórico da conversa
- iniciar ou continuar pedidos
- atualizar status do atendimento

### n8n
Camada de automação e orquestração.

Funções:
- receber eventos
- consultar dados
- decidir a próxima etapa
- chamar a API interna
- disparar impressão
- atualizar estados do pedido

### Supabase
Banco de dados central do sistema.

Funções:
- armazenar clientes
- armazenar pedidos
- armazenar conversas
- armazenar produtos
- armazenar caixa
- armazenar estoque
- armazenar fila de impressão

### API interna
Camada responsável pelas regras de negócio.

Funções:
- criar pedidos
- atualizar pedidos
- gerar senhas
- registrar pagamentos
- baixar estoque
- criar jobs de impressão

### Serviço de impressão
Camada responsável por executar a impressão.

Funções:
- receber jobs
- escolher a impressora correta
- imprimir em rede ou USB
- registrar status
- permitir reprocessamento
- salvar logs técnicos

---

## Fluxo principal do sistema

### Entrada do pedido
O pedido pode entrar por:
- WhatsApp
- balcão
- operador interno

### Identificação
O sistema identifica:
- empresa
- cliente
- canal
- itens
- observações
- forma de pagamento
- setores envolvidos

### Gravação
O pedido é salvo no banco de dados com seus itens e status inicial.

### Separação por setor
Cada item é direcionado para o setor correto:
- cozinha
- copa
- bebidas
- caixa
- retirada

### Impressão
O sistema gera jobs separados para cada setor ou documento necessário.

### Pagamento
O pagamento é vinculado ao pedido e ao caixa.

### Estoque
Os insumos são baixados automaticamente conforme a venda.

### Finalização
O pedido é concluído com status final e histórico salvo.

---

## Estrutura de impressão

A impressão no FlowMesa é tratada como serviço independente.

### Tipos de impressão
- produção
- senha
- comprovante
- resumo interno
- reimpressão

### Modelos de conexão
- impressora de rede
- impressora USB com agente local

### Regras
- cada job deve ter status próprio
- falha de impressão não pode travar o pedido
- reimpressão deve ficar registrada
- setores podem ter impressoras diferentes
- um pedido pode gerar vários tickets

---

## Modelo de operação multiempresa

O FlowMesa precisa funcionar como SaaS.

### Regra principal
Todas as tabelas principais precisam ter vínculo com a empresa.

### Isso permite:
- separar dados por cliente
- usar a mesma base para várias empresas
- escalar o sistema com segurança
- vender por assinatura

---

## Módulos funcionais

### Comercial
- WhatsApp
- catálogo
- pedidos
- clientes

### Operacional
- produção por setor
- impressão
- senha
- fila de impressão

### Financeiro
- caixa
- pagamentos
- fechamento
- divergência

### Estoque
- entradas
- saídas
- consumo
- alertas

### Administrativo
- usuários
- empresas
- permissões
- configurações
- relatórios

---

## Princípios da arquitetura

- o pedido deve ter um fluxo único
- WhatsApp e PDV devem gravar no mesmo núcleo
- impressão deve ser separada da regra de negócio
- o sistema precisa suportar falhas sem parar a operação
- tudo relevante deve ser registrado em log
- a documentação deve acompanhar o projeto desde o início

---

## Ordem recomendada de implementação

1. banco de dados
2. API interna
3. fluxo de pedidos
4. PDV
5. WhatsApp
6. fila de impressão
7. caixa
8. estoque
9. logs
10. documentação final

---

## Resumo

O FlowMesa foi desenhado para funcionar como uma plataforma única, modular e escalável.

A base técnica ideal é:

- WhatsApp como entrada
- n8n como orquestração
- Supabase como banco
- API interna como regra de negócio
- serviço de impressão como saída física
- GitHub como documentação oficial
