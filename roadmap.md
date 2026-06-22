# FlowMesa — Roadmap

## Visão geral

Este roadmap organiza a evolução do FlowMesa em fases, começando pelo núcleo operacional e avançando até a versão completa em SaaS.

A ideia é construir primeiro o que é essencial para funcionar, depois expandir com mais recursos.

---

## Fase 1 — Núcleo do sistema

### Objetivo
Criar a base mínima para o sistema funcionar de forma organizada.

### Entregas
- cadastro de empresa
- cadastro de usuários
- cadastro de clientes
- cadastro de produtos
- cadastro de categorias
- cadastro de pedidos
- cadastro de itens do pedido
- registro de pagamentos
- abertura e fechamento de caixa
- emissão de senha
- fila de impressão
- histórico de conversa no WhatsApp

### Resultado esperado
O sistema já consegue receber pedidos, registrar operação e gerar saída física básica.

---

## Fase 2 — Operação completa

### Objetivo
Fechar o fluxo de atendimento e produção.

### Entregas
- PDV de balcão
- separação por setor
- impressoras de rede
- impressoras USB com agente local
- logs de impressão
- reimpressão de documentos
- movimentações de estoque
- baixa automática de estoque
- controle de status dos pedidos

### Resultado esperado
O sistema passa a operar com mais estabilidade e controle real da produção.

---

## Fase 3 — Automação e inteligência

### Objetivo
Melhorar o atendimento e a tomada de decisão.

### Entregas
- integração com n8n
- automação do WhatsApp
- uso de contexto da conversa
- respostas automáticas mais inteligentes
- acompanhamento de status do pedido
- notificações de produção e entrega

### Resultado esperado
O atendimento começa a funcionar de forma mais fluida e automatizada.

---

## Fase 4 — SaaS e escalabilidade

### Objetivo
Transformar o sistema em produto vendável por assinatura.

### Entregas
- suporte multiempresa
- planos Base, Pro e Premium
- configuração por cliente
- personalização de módulos
- organização por subdomínio
- documentação oficial no GitHub
- estrutura pronta para novos clientes

### Resultado esperado
O FlowMesa fica pronto para ser revendido como serviço recorrente.

---

## Fase 5 — Evolução comercial

### Objetivo
Aprimorar o produto para retenção e expansão.

### Entregas
- relatórios avançados
- dashboards
- indicadores de venda
- controle de desempenho
- melhorias de usabilidade
- ajustes por feedback dos primeiros clientes

### Resultado esperado
O produto amadurece e fica mais competitivo no mercado.

---

## Ordem recomendada de construção

A sequência ideal de implementação é:

1. banco de dados
2. API interna
3. pedidos
4. clientes
5. produtos
6. WhatsApp
7. PDV
8. caixa
9. impressão
10. estoque
11. automações
12. planos comerciais
13. documentação final

---

## Critério para avançar de fase

Só avançar para a próxima fase quando a anterior estiver funcionando de forma estável.

Exemplo:
- não adianta pensar em planos se o pedido ainda não funciona
- não adianta pensar em automação se o banco ainda está incompleto
- não adianta pensar em relatórios se a operação básica ainda falha

---

## Resumo

O FlowMesa deve nascer simples, funcional e bem documentado.

Primeiro o núcleo.
Depois a operação.
Depois a automação.
Depois o SaaS.
Depois a escala.
