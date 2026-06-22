# FlowMesa — Checklist de Deploy

## Visão geral

Este checklist organiza os passos necessários para colocar o FlowMesa no ar com segurança, estabilidade e estrutura correta.

A ideia é evitar esquecer configuração, dependências, variáveis e validações básicas antes de liberar o sistema.

---

## 1. Estrutura da VPS

Verificar se a VPS está pronta para receber o projeto.

### Itens
- sistema operacional instalado
- acesso SSH funcionando
- disco disponível
- memória suficiente
- CPU suficiente
- firewall configurado
- portas necessárias liberadas

---

## 2. Subdomínios

Confirmar os subdomínios usados pelo sistema.

Exemplos:
- painel
- API
- n8n
- WhatsApp
- documentação

### Itens
- DNS apontado corretamente
- SSL habilitado
- acesso por HTTPS funcionando

---

## 3. Banco de dados

Preparar o banco para receber os dados do sistema.

### Itens
- criar base
- criar tabelas
- criar relacionamentos
- validar campos obrigatórios
- revisar índices
- confirmar suporte a multiempresa

---

## 4. Variáveis de ambiente

Conferir se todas as variáveis necessárias estão configuradas.

### Itens
- credenciais do banco
- URL da API
- chave de integração
- dados do WhatsApp
- dados do n8n
- chaves de segurança
- URLs internas

---

## 5. Containers

Se o sistema usar Docker, validar os containers.

### Itens
- API
- banco
- n8n
- serviço de impressão
- frontend
- integrações

### Verificações
- container sobe sem erro
- container reinicia corretamente
- logs não mostram falhas graves
- rede interna entre containers está funcionando

---

## 6. Integração com WhatsApp

Validar a conexão com o canal de atendimento.

### Itens
- número configurado
- QR Code gerado
- conexão ativa
- mensagens chegando
- mensagens saindo
- histórico sendo salvo

---

## 7. Fluxo do pedido

Testar o fluxo completo.

### Itens
- pedido recebido
- cliente identificado
- itens registrados
- pedido salvo
- pagamento vinculado
- impressão gerada
- status atualizado
- histórico preservado

---

## 8. Impressão

Validar a operação física.

### Itens
- impressora de rede testada
- impressora USB testada
- agente local funcionando
- fila de impressão funcionando
- reimpressão funcionando
- logs gerados corretamente

---

## 9. Caixa

Validar o fluxo financeiro.

### Itens
- abertura de caixa
- registro de venda
- formas de pagamento
- fechamento de caixa
- conferência de valores
- divergência, se houver

---

## 10. Estoque

Validar a movimentação dos itens.

### Itens
- consumo automático
- entrada manual
- saída manual
- alerta de mínimo
- histórico de movimentações

---

## 11. Segurança

Garantir o básico de proteção.

### Itens
- autenticação ativa
- permissões por perfil
- dados protegidos por empresa
- acesso externo restrito
- logs de erro habilitados

---

## 12. Teste final

Fazer um teste completo antes de liberar.

### Roteiro
1. abrir o sistema
2. entrar como usuário
3. registrar pedido
4. confirmar item
5. disparar impressão
6. registrar pagamento
7. baixar estoque
8. fechar pedido
9. revisar logs

---

## 13. Backup

Garantir recuperação em caso de falha.

### Itens
- backup do banco
- backup de arquivos
- backup de configurações
- plano de restauração
- rotina de checagem

---

## 14. Monitoramento

Acompanhar o sistema depois de subir.

### Itens
- logs de aplicação
- logs de impressão
- logs de integração
- falhas de conexão
- uso de memória
- uso de CPU
- espaço em disco

---

## 15. Checklist final antes de produção

Antes de liberar, confirmar:

- [ ] domínio acessa por HTTPS
- [ ] banco está funcionando
- [ ] API responde
- [ ] WhatsApp conecta
- [ ] n8n executa fluxos
- [ ] impressão responde
- [ ] caixa abre e fecha
- [ ] estoque baixa corretamente
- [ ] logs estão ativos
- [ ] backup está habilitado

---

## Resumo

Este checklist existe para evitar erro de deploy e facilitar a implantação do FlowMesa em ambientes reais.

Se tudo acima estiver validado, o sistema está pronto para ir para produção com muito mais segurança.
