# Documento de Casos de Testes de Jornada - Sistema McBugs

**Sistema:** McBugs - Totem de Autoatendimento para Restaurantes  
**Versão:** 1.0  
**Data:** 2024  
**Autor:** Analista de Qualidade

---

## Casos de Teste de Jornada

Este documento contém os casos de teste funcionais a nível de jornada para o sistema McBugs, cobrindo os fluxos completos desde a seleção do tipo de pedido até a confirmação final.

---

### **CT001 - Jornada Completa - Para Comer Aqui**

#### **Objetivo**

Validar o fluxo completo de um pedido do tipo "Para comer aqui" (dine-in), desde a seleção do tipo de pedido até a confirmação final, garantindo que todos os passos funcionem corretamente em sequência.

#### **Pré-Condições**

- O sistema McBugs deve estar online e acessível.
- O navegador deve estar configurado corretamente para acessar o sistema.
- O Supabase deve estar configurado e acessível.
- O carrinho deve estar vazio.
- O usuário deve estar na página inicial do sistema.

#### **Passos**

| **Id** | **Ação**                          | **Resultado Esperado**                            |
|--------|------------------------------------|---------------------------------------------------|
| 1      | Acessar a página inicial do sistema | A página inicial deve ser carregada corretamente, exibindo o logo McBugs e as opções "Para comer aqui" e "Para levar". |
| 2      | Clicar no botão "Para comer aqui" | O sistema deve registrar o tipo de pedido como "dine-in" no localStorage e redirecionar o usuário para a página do menu (/menu). |
| 3      | Verificar a página do menu | A página do menu deve ser exibida com as categorias de produtos (Lanches, Fritas, Bebidas, Sobremesas) e a categoria "Lanches" deve estar selecionada por padrão. |
| 4      | Clicar em um produto da categoria "Lanches" (ex: Big Mock) | O sistema deve redirecionar para a página de detalhes do produto (/product/:id), exibindo imagem, nome, preço, descrição e ingredientes. |
| 5      | Verificar a quantidade inicial | A quantidade deve estar definida como 1 e o botão "Quero" deve exibir o valor total (preço × 1). |
| 6      | Aumentar a quantidade para 2 | A quantidade deve ser atualizada para 2 e o valor no botão "Quero" deve ser recalculado (preço × 2). |
| 7      | Clicar no botão "Quero" | O produto deve ser adicionado ao carrinho com quantidade 2 e o usuário deve ser redirecionado para o menu (/menu). |
| 8      | Verificar o contador do carrinho | O contador de itens no carrinho (barra inferior) deve exibir o número 2. |
| 9      | Clicar na categoria "Bebidas" | A categoria "Bebidas" deve ser selecionada e apenas os produtos de bebidas devem ser exibidos. |
| 10     | Clicar em um produto de bebida (ex: Coca-Crash) | O sistema deve redirecionar para a página de detalhes do produto de bebida. |
| 11     | Clicar no botão "Quero" (quantidade 1) | O produto de bebida deve ser adicionado ao carrinho e o usuário deve ser redirecionado para o menu. |
| 12     | Verificar o contador do carrinho atualizado | O contador de itens no carrinho deve exibir o número 3 (2 lanches + 1 bebida). |
| 13     | Clicar na barra do carrinho ou acessar /cart | O sistema deve redirecionar para a página do carrinho (/cart), exibindo todos os itens adicionados com suas quantidades e preços. |
| 14     | Verificar os itens no carrinho | Devem ser exibidos: 2x Big Mock com subtotal e 1x Coca-Crash com subtotal, além do total do pedido calculado corretamente. |
| 15     | Aumentar a quantidade do Big Mock para 3 | A quantidade do Big Mock deve ser atualizada para 3, o subtotal do item deve ser recalculado e o total do pedido deve ser atualizado. |
| 16     | Clicar no botão "Finalizar pedido" | O drawer de checkout deve ser aberto solicitando o nome do cliente. |
| 17     | Inserir o nome do cliente (ex: "João Silva") | O nome deve ser inserido no campo de input. |
| 18     | Clicar no botão "Finalizar" no drawer | O sistema deve criar o pedido no banco de dados com status "pending", tipo "dine-in", limpar o carrinho e redirecionar para a página de pagamento (/payment). |
| 19     | Verificar a página de pagamento | A página de pagamento deve exibir o resumo do pedido (número e total) e as três opções de pagamento: PIX, Cartão de Débito e Cartão de Crédito. |
| 20     | Clicar na opção "PIX" | O método de pagamento do pedido deve ser atualizado para "pix" no banco de dados e o usuário deve ser redirecionado para /payment/pix/confirm. |
| 21     | Verificar a página de confirmação | A página de confirmação deve exibir: número do pedido, total, instruções de pagamento no balcão, detalhes do pedido (cliente, tipo "Comer no local", forma de pagamento PIX, data, lista de itens) e a mensagem específica para dine-in: "Após o pagamento, aguarde ser chamado pelo número do seu pedido.". |
| 22     | Verificar os detalhes do pedido | Os detalhes devem estar corretos: cliente "João Silva", tipo "Comer no local", forma de pagamento "PIX", itens: 3x Big Mock e 1x Coca-Crash, total calculado corretamente. |
| 23     | Clicar no botão "Fazer Novo Pedido" | O pedido atual deve ser resetado, o carrinho deve ser limpo e o usuário deve ser redirecionado para a página inicial (/). |

#### **Resultados Esperados**

- O tipo de pedido "dine-in" deve ser selecionado e persistido corretamente.
- Os produtos devem ser adicionados ao carrinho com as quantidades corretas.
- O carrinho deve exibir todos os itens e calcular o total corretamente.
- O pedido deve ser criado no banco de dados com todas as informações corretas (tipo "dine-in", itens, total, status "pending").
- O método de pagamento deve ser atualizado corretamente.
- A página de confirmação deve exibir todas as informações do pedido corretamente.
- A mensagem específica para dine-in deve ser exibida na confirmação.
- O sistema deve permitir iniciar um novo pedido após a confirmação.

#### **Critérios de Aceitação**

- Todos os passos da jornada devem ser executados sem erros.
- O tipo de pedido "dine-in" deve ser mantido durante toda a jornada.
- O carrinho deve funcionar corretamente (adicionar, atualizar quantidades, calcular total).
- O pedido deve ser criado no banco de dados com status "pending" e tipo "dine-in".
- O método de pagamento deve ser atualizado corretamente no banco de dados.
- A página de confirmação deve exibir todas as informações corretas.
- A mensagem específica para pedidos dine-in deve ser exibida.
- O sistema deve permitir iniciar um novo pedido após a confirmação.
- Não deve haver perda de dados durante a navegação.
- O localStorage deve ser gerenciado corretamente (salvar e limpar quando apropriado).

---

### **CT002 - Jornada Completa - Para Levar**

#### **Objetivo**

Validar o fluxo completo de um pedido do tipo "Para levar" (takeaway), desde a seleção do tipo de pedido até a confirmação final, garantindo que todos os passos funcionem corretamente em sequência.

#### **Pré-Condições**

- O sistema McBugs deve estar online e acessível.
- O navegador deve estar configurado corretamente para acessar o sistema.
- O Supabase deve estar configurado e acessível.
- O carrinho deve estar vazio.
- O usuário deve estar na página inicial do sistema.

#### **Passos**

| **Id** | **Ação**                          | **Resultado Esperado**                            |
|--------|------------------------------------|---------------------------------------------------|
| 1      | Acessar a página inicial do sistema | A página inicial deve ser carregada corretamente, exibindo o logo McBugs e as opções "Para comer aqui" e "Para levar". |
| 2      | Clicar no botão "Para levar" | O sistema deve registrar o tipo de pedido como "takeaway" no localStorage e redirecionar o usuário para a página do menu (/menu). |
| 3      | Verificar a página do menu | A página do menu deve ser exibida com as categorias de produtos (Lanches, Fritas, Bebidas, Sobremesas) e a categoria "Lanches" deve estar selecionada por padrão. |
| 4      | Clicar na categoria "Fritas" | A categoria "Fritas" deve ser selecionada e apenas os produtos de fritas devem ser exibidos. |
| 5      | Clicar em um produto de fritas (ex: Batatas Full Stack) | O sistema deve redirecionar para a página de detalhes do produto, exibindo imagem, nome, preço, descrição e ingredientes. |
| 6      | Aumentar a quantidade para 2 | A quantidade deve ser atualizada para 2 e o valor no botão "Quero" deve ser recalculado. |
| 7      | Clicar no botão "Quero" | O produto deve ser adicionado ao carrinho com quantidade 2 e o usuário deve ser redirecionado para o menu. |
| 8      | Clicar na categoria "Lanches" | A categoria "Lanches" deve ser selecionada e os produtos de lanches devem ser exibidos. |
| 9      | Clicar em um lanche (ex: Duplo Deploy) | O sistema deve redirecionar para a página de detalhes do lanche. |
| 10     | Clicar no botão "Quero" (quantidade 1) | O lanche deve ser adicionado ao carrinho e o usuário deve ser redirecionado para o menu. |
| 11     | Clicar na categoria "Sobremesas" | A categoria "Sobremesas" deve ser selecionada e os produtos de sobremesas devem ser exibidos. |
| 12     | Clicar em uma sobremesa (ex: Casquinha Vanilla JS) | O sistema deve redirecionar para a página de detalhes da sobremesa. |
| 13     | Clicar no botão "Quero" (quantidade 1) | A sobremesa deve ser adicionada ao carrinho e o usuário deve ser redirecionado para o menu. |
| 14     | Verificar o contador do carrinho | O contador de itens no carrinho deve exibir o número 4 (2 fritas + 1 lanche + 1 sobremesa). |
| 15     | Clicar na barra do carrinho | O sistema deve redirecionar para a página do carrinho (/cart), exibindo todos os itens adicionados. |
| 16     | Verificar os itens no carrinho | Devem ser exibidos: 2x Batatas Full Stack, 1x Duplo Deploy e 1x Casquinha Vanilla JS, com seus respectivos subtotais e o total do pedido calculado corretamente. |
| 17     | Remover a sobremesa do carrinho | A sobremesa deve ser removida do carrinho e o total do pedido deve ser recalculado. |
| 18     | Verificar o total atualizado | O total do pedido deve ser recalculado sem incluir a sobremesa removida. |
| 19     | Clicar no botão "Finalizar pedido" | O drawer de checkout deve ser aberto solicitando o nome do cliente. |
| 20     | Inserir o nome do cliente (ex: "Maria Santos") | O nome deve ser inserido no campo de input. |
| 21     | Clicar no botão "Finalizar" no drawer | O sistema deve criar o pedido no banco de dados com status "pending", tipo "takeaway", limpar o carrinho e redirecionar para a página de pagamento (/payment). |
| 22     | Verificar a página de pagamento | A página de pagamento deve exibir o resumo do pedido (número e total) e as três opções de pagamento: PIX, Cartão de Débito e Cartão de Crédito. |
| 23     | Clicar na opção "Cartão de Crédito" | O método de pagamento do pedido deve ser atualizado para "credit" no banco de dados e o usuário deve ser redirecionado para /payment/credit/confirm. |
| 24     | Verificar a página de confirmação | A página de confirmação deve exibir: número do pedido, total, instruções de pagamento no balcão, detalhes do pedido (cliente, tipo "Para levar", forma de pagamento Cartão de Crédito, data, lista de itens). |
| 25     | Verificar que não há mensagem para takeaway | A mensagem "Após o pagamento, aguarde ser chamado pelo número do seu pedido." NÃO deve ser exibida, pois o pedido é do tipo "takeaway". |
| 26     | Verificar os detalhes do pedido | Os detalhes devem estar corretos: cliente "Maria Santos", tipo "Para levar", forma de pagamento "Cartão de Crédito", itens: 2x Batatas Full Stack e 1x Duplo Deploy, total calculado corretamente. |
| 27     | Clicar no botão "Fazer Novo Pedido" | O pedido atual deve ser resetado, o carrinho deve ser limpo e o usuário deve ser redirecionado para a página inicial (/). |

#### **Resultados Esperados**

- O tipo de pedido "takeaway" deve ser selecionado e persistido corretamente.
- Os produtos de diferentes categorias devem ser adicionados ao carrinho corretamente.
- O carrinho deve permitir remover itens e recalcular o total corretamente.
- O pedido deve ser criado no banco de dados com todas as informações corretas (tipo "takeaway", itens, total, status "pending").
- O método de pagamento deve ser atualizado corretamente.
- A página de confirmação deve exibir todas as informações do pedido corretamente.
- A mensagem específica para dine-in NÃO deve ser exibida para pedidos takeaway.
- O sistema deve permitir iniciar um novo pedido após a confirmação.

#### **Critérios de Aceitação**

- Todos os passos da jornada devem ser executados sem erros.
- O tipo de pedido "takeaway" deve ser mantido durante toda a jornada.
- O carrinho deve funcionar corretamente (adicionar, remover, atualizar quantidades, calcular total).
- O pedido deve ser criado no banco de dados com status "pending" e tipo "takeaway".
- O método de pagamento deve ser atualizado corretamente no banco de dados.
- A página de confirmação deve exibir todas as informações corretas.
- A mensagem específica para dine-in NÃO deve ser exibida para pedidos takeaway.
- O sistema deve permitir iniciar um novo pedido após a confirmação.
- Não deve haver perda de dados durante a navegação.
- O localStorage deve ser gerenciado corretamente (salvar e limpar quando apropriado).

---

## Resumo

Este documento contém **2 casos de teste de jornada** que cobrem os fluxos completos end-to-end do sistema McBugs:

- **CT001 - Jornada Completa - Para Comer Aqui:** Valida o fluxo completo de um pedido do tipo "dine-in" com 23 passos detalhados.
- **CT002 - Jornada Completa - Para Levar:** Valida o fluxo completo de um pedido do tipo "takeaway" com 27 passos detalhados.

Ambos os casos de teste foram elaborados seguindo o padrão estabelecido, com objetivo claro, pré-condições definidas, passos detalhados em formato de tabela, resultados esperados e critérios de aceitação bem especificados. Os casos validam toda a experiência do usuário desde a seleção do tipo de pedido até a confirmação final, garantindo que todos os componentes funcionem corretamente em sequência.

---

**Fim do Documento**

