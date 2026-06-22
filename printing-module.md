# FlowMesa — Módulo de Impressão

## Visão geral

O módulo de impressão do FlowMesa é responsável por transformar pedidos em documentos físicos ou tickets operacionais.

Ele não faz parte da regra de negócio principal:
ele funciona como um serviço independente de execução.

---

## Objetivo do módulo

O objetivo é garantir que cada pedido gere a impressão correta, no setor correto, com rastreabilidade e possibilidade de reprocessamento.

---

## O que pode ser impresso

O FlowMesa pode gerar diferentes tipos de impressão:

- ticket de produção
- senha de retirada
- comprovante interno
- resumo do pedido
- reimpressão de documento

---

## Estrutura do fluxo de impressão

## 1. Criação do pedido

Quando um pedido é confirmado, o sistema identifica o que precisa ser impresso.

---

## 2. Separação por setor

O sistema divide o pedido de acordo com os setores de produção.

Exemplos:
- cozinha
- copa
- bebidas
- retirada
- caixa

Cada setor recebe apenas os itens que lhe pertencem.

---

## 3. Criação da fila

Para cada saída necessária, o sistema cria um job na fila de impressão.

Cada job deve conter:
- pedido de origem
- setor
- tipo de documento
- impressora destino
- status
- tentativas
- erro, se houver

---

## 4. Envio para impressão

O serviço de impressão recebe o job e decide a forma de envio.

Modelos possíveis:
- impressora de rede
- impressora USB com agente local

---

## 5. Retorno de status

Depois de tentar imprimir, o sistema atualiza o status do job.

Status possíveis:
- pendente
- enviado
- impresso
- falhou
- reprocessando
- cancelado

---

## 6. Registro em log

Toda tentativa de impressão precisa ser registrada.

O log deve guardar:
- data e hora
- pedido relacionado
- impressora usada
- setor
- status final
- mensagem de erro, se houver

---

## Tipos de conexão

## Impressora de rede
A impressora recebe o job diretamente pela rede.

Vantagens:
- mais estável
- mais fácil de manter
- ideal para operação fixa

---

## Impressora USB
A impressora USB precisa de um agente local para receber o job e executar a impressão.

Vantagens:
- permite uso em estruturas menores
- atende quem não usa impressora de rede
- amplia a flexibilidade do sistema

---

## Agente local

O agente local é um pequeno serviço instalado na máquina que está fisicamente conectada à impressora USB.

Funções:
- receber jobs
- enviar para a impressora
- devolver status
- registrar falhas
- permitir reenvio

Ele não deve conter regra de negócio.
Ele apenas executa a impressão.

---

## Regras do módulo

- a impressão não deve depender da tela do operador
- falha de impressão não pode travar o pedido
- todo job precisa ter rastreio
- reimpressão precisa ficar registrada
- um pedido pode gerar vários tickets
- um setor pode usar mais de uma impressora
- o sistema deve funcionar tanto com rede quanto com USB

---

## Reimpressão

A reimpressão deve ser simples e controlada.

Casos comuns:
- papel acabou
- impressão cortada
- ticket perdido
- impressora falhou
- reenvio solicitado pelo operador

Toda reimpressão precisa gerar um novo registro de log.

---

## Relacionamento com outras tabelas

O módulo de impressão se conecta principalmente com:

- `pedidos`
- `pedido_itens`
- `setores`
- `impressoras`
- `fila_impressao`

---

## Exemplo de fluxo completo

1. O cliente faz o pedido.
2. O sistema grava o pedido no banco.
3. O sistema separa os itens por setor.
4. O módulo cria os jobs de impressão.
5. Cada job é enviado para a impressora correta.
6. O status volta para o sistema.
7. O pedido continua independente de qualquer falha.

---

## Resumo

O módulo de impressão do FlowMesa precisa ser confiável, rastreável e independente.

Ele é parte essencial da operação e não pode ser tratado como detalhe secundário.
