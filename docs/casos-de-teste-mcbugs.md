# Documento de Casos de Teste - Sistema McBugs

**Sistema:** McBugs - Totem de Autoatendimento para Restaurantes  
**Versão:** 1.0  
**Data:** 2024  
**Autor:** Analista de Qualidade

---

## Índice

1. [Fluxo de Seleção de Tipo de Pedido](#fluxo-de-seleção-de-tipo-de-pedido)
2. [Fluxo de Navegação no Menu](#fluxo-de-navegação-no-menu)
3. [Fluxo de Visualização e Adição de Produtos](#fluxo-de-visualização-e-adição-de-produtos)
4. [Fluxo de Gerenciamento do Carrinho](#fluxo-de-gerenciamento-do-carrinho)
5. [Fluxo de Finalização de Pedido](#fluxo-de-finalização-de-pedido)
6. [Fluxo de Pagamento](#fluxo-de-pagamento)
7. [Fluxo de Confirmação de Pedido](#fluxo-de-confirmação-de-pedido)
8. [Cenários de Erro e Validação](#cenários-de-erro-e-validação)

---

## Fluxo de Seleção de Tipo de Pedido

### **CT001 - Selecionar Pedido para Comer no Local**

#### **Objetivo**

Validar que o sistema permite ao usuário selecionar a opção "Para comer aqui" e redireciona corretamente para a página do menu.

#### **Pré-Condições**

- O sistema McBugs deve estar online e acessível.
- O navegador deve estar configurado corretamente para acessar o sistema.
- O usuário deve estar na página inicial do sistema.

#### **Passos**

| **Id** | **Ação**                          | **Resultado Esperado**                            |
|--------|------------------------------------|---------------------------------------------------|
| 1      | Acessar a página inicial do sistema | A página inicial deve ser carregada corretamente, exibindo o logo McBugs e as opções "Para comer aqui" e "Para levar". |
| 2      | Verificar a exibição das opções disponíveis | Deve ser exibida a opção "Para comer aqui" com ícone correspondente e a opção "Para levar" com ícone correspondente. |
| 3      | Clicar no botão "Para comer aqui" | O sistema deve registrar o tipo de pedido como "dine-in" e redirecionar o usuário para a página do menu (/menu). |

#### **Resultados Esperados**

- O tipo de pedido "dine-in" deve ser salvo no localStorage.
- O usuário deve ser redirecionado para a página do menu.
- A navegação deve ocorrer sem erros.

#### **Critérios de Aceitação**

- A página inicial deve ser exibida sem erros.
- O botão "Para comer aqui" deve estar visível e clicável.
- Após o clique, o redirecionamento para /menu deve ocorrer corretamente.
- O tipo de pedido deve ser persistido no localStorage.

---

### **CT002 - Selecionar Pedido para Levar**

#### **Objetivo**

Validar que o sistema permite ao usuário selecionar a opção "Para levar" e redireciona corretamente para a página do menu.

#### **Pré-Condições**

- O sistema McBugs deve estar online e acessível.
- O navegador deve estar configurado corretamente para acessar o sistema.
- O usuário deve estar na página inicial do sistema.

#### **Passos**

| **Id** | **Ação**                          | **Resultado Esperado**                            |
|--------|------------------------------------|---------------------------------------------------|
| 1      | Acessar a página inicial do sistema | A página inicial deve ser carregada corretamente, exibindo o logo McBugs e as opções "Para comer aqui" e "Para levar". |
| 2      | Verificar a exibição das opções disponíveis | Deve ser exibida a opção "Para comer aqui" com ícone correspondente e a opção "Para levar" com ícone correspondente. |
| 3      | Clicar no botão "Para levar" | O sistema deve registrar o tipo de pedido como "takeaway" e redirecionar o usuário para a página do menu (/menu). |

#### **Resultados Esperados**

- O tipo de pedido "takeaway" deve ser salvo no localStorage.
- O usuário deve ser redirecionado para a página do menu.
- A navegação deve ocorrer sem erros.

#### **Critérios de Aceitação**

- A página inicial deve ser exibida sem erros.
- O botão "Para levar" deve estar visível e clicável.
- Após o clique, o redirecionamento para /menu deve ocorrer corretamente.
- O tipo de pedido deve ser persistido no localStorage.

---

## Fluxo de Navegação no Menu

### **CT003 - Visualizar Menu com Categorias**

#### **Objetivo**

Validar que o sistema exibe corretamente o menu com todas as categorias de produtos disponíveis.

#### **Pré-Condições**

- O sistema McBugs deve estar online e acessível.
- O usuário deve ter selecionado um tipo de pedido (dine-in ou takeaway).
- O usuário deve estar na página do menu (/menu).

#### **Passos**

| **Id** | **Ação**                          | **Resultado Esperado**                            |
|--------|------------------------------------|---------------------------------------------------|
| 1      | Acessar a página do menu | A página do menu deve ser carregada corretamente, exibindo a imagem hero, informações do restaurante e as categorias de produtos. |
| 2      | Verificar a exibição das categorias | Devem ser exibidas as categorias: Lanches, Fritas, Bebidas e Sobremesas. |
| 3      | Verificar a categoria padrão selecionada | A categoria "Lanches" deve estar selecionada por padrão. |
| 4      | Verificar os produtos exibidos | Devem ser exibidos apenas os produtos da categoria "Lanches" no grid de produtos. |

#### **Resultados Esperados**

- O menu deve exibir todas as categorias disponíveis.
- A categoria "Lanches" deve estar selecionada por padrão.
- Apenas os produtos da categoria selecionada devem ser exibidos.
- Cada produto deve exibir imagem, nome e preço.

#### **Critérios de Aceitação**

- Todas as categorias devem estar visíveis e acessíveis.
- A categoria padrão deve ser "Lanches".
- Os produtos devem ser filtrados corretamente por categoria.
- A barra de carrinho deve estar visível na parte inferior da tela.

---

### **CT004 - Alternar entre Categorias de Produtos**

#### **Objetivo**

Validar que o sistema permite alternar entre as diferentes categorias de produtos e exibe corretamente os produtos de cada categoria.

#### **Pré-Condições**

- O sistema McBugs deve estar online e acessível.
- O usuário deve estar na página do menu (/menu).
- A categoria "Lanches" deve estar selecionada por padrão.

#### **Passos**

| **Id** | **Ação**                          | **Resultado Esperado**                            |
|--------|------------------------------------|---------------------------------------------------|
| 1      | Verificar a categoria atual | A categoria "Lanches" deve estar selecionada e os produtos de lanches devem ser exibidos. |
| 2      | Clicar na categoria "Fritas" | A categoria "Fritas" deve ser selecionada e apenas os produtos de fritas devem ser exibidos. |
| 3      | Clicar na categoria "Bebidas" | A categoria "Bebidas" deve ser selecionada e apenas os produtos de bebidas devem ser exibidos. |
| 4      | Clicar na categoria "Sobremesas" | A categoria "Sobremesas" deve ser selecionada e apenas os produtos de sobremesas devem ser exibidos. |
| 5      | Retornar para a categoria "Lanches" | A categoria "Lanches" deve ser selecionada novamente e os produtos de lanches devem ser exibidos. |

#### **Resultados Esperados**

- Ao clicar em uma categoria, apenas os produtos dessa categoria devem ser exibidos.
- A categoria selecionada deve estar visualmente destacada.
- A transição entre categorias deve ser suave e sem erros.

#### **Critérios de Aceitação**

- Todas as categorias devem ser clicáveis e funcionais.
- O filtro de produtos deve funcionar corretamente para cada categoria.
- Não deve haver produtos de outras categorias sendo exibidos quando uma categoria específica está selecionada.

---

### **CT005 - Navegar de Volta para a Página Inicial**

#### **Objetivo**

Validar que o sistema permite retornar à página inicial a partir do menu.

#### **Pré-Condições**

- O sistema McBugs deve estar online e acessível.
- O usuário deve estar na página do menu (/menu).

#### **Passos**

| **Id** | **Ação**                          | **Resultado Esperado**                            |
|--------|------------------------------------|---------------------------------------------------|
| 1      | Verificar a presença do botão de voltar | Deve existir um botão de voltar (seta para esquerda) no canto superior esquerdo da página. |
| 2      | Clicar no botão de voltar | O sistema deve redirecionar o usuário para a página inicial (/). |

#### **Resultados Esperados**

- O botão de voltar deve estar visível e acessível.
- Ao clicar, o usuário deve ser redirecionado para a página inicial.
- A navegação deve ocorrer sem erros.

#### **Critérios de Aceitação**

- O botão de voltar deve estar sempre visível na página do menu.
- O redirecionamento para a página inicial deve ocorrer corretamente.
- Não deve haver perda de dados durante a navegação.

---

## Fluxo de Visualização e Adição de Produtos

### **CT006 - Visualizar Detalhes de um Produto**

#### **Objetivo**

Validar que o sistema exibe corretamente todos os detalhes de um produto quando o usuário clica nele.

#### **Pré-Condições**

- O sistema McBugs deve estar online e acessível.
- O usuário deve estar na página do menu (/menu).
- Deve haver produtos disponíveis para visualização.

#### **Passos**

| **Id** | **Ação**                          | **Resultado Esperado**                            |
|--------|------------------------------------|---------------------------------------------------|
| 1      | Clicar em um produto no menu | O sistema deve redirecionar para a página de detalhes do produto (/product/:id). |
| 2      | Verificar a exibição da imagem do produto | A imagem do produto deve ser exibida em destaque na parte superior da página. |
| 3      | Verificar as informações do produto | Devem ser exibidos: nome do produto, preço, descrição e ingredientes (se disponíveis). |
| 4      | Verificar o controle de quantidade | Deve ser exibido um controle de quantidade com valor padrão de 1. |
| 5      | Verificar o botão de adicionar ao carrinho | Deve ser exibido um botão "Quero" com o valor total calculado (preço × quantidade). |

#### **Resultados Esperados**

- A página de detalhes do produto deve ser carregada corretamente.
- Todas as informações do produto devem estar visíveis e corretas.
- O controle de quantidade deve estar funcional.
- O valor total deve ser calculado corretamente baseado na quantidade selecionada.

#### **Critérios de Aceitação**

- A página de detalhes deve exibir todas as informações do produto corretamente.
- A imagem do produto deve ser carregada sem erros.
- O controle de quantidade deve permitir aumentar e diminuir a quantidade.
- O valor total no botão deve ser atualizado dinamicamente conforme a quantidade muda.

---

### **CT007 - Aumentar Quantidade de um Produto**

#### **Objetivo**

Validar que o sistema permite aumentar a quantidade de um produto na página de detalhes.

#### **Pré-Condições**

- O sistema McBugs deve estar online e acessível.
- O usuário deve estar na página de detalhes de um produto (/product/:id).
- A quantidade inicial deve ser 1.

#### **Passos**

| **Id** | **Ação**                          | **Resultado Esperado**                            |
|--------|------------------------------------|---------------------------------------------------|
| 1      | Verificar a quantidade inicial | A quantidade deve estar definida como 1. |
| 2      | Clicar no botão de aumentar quantidade (+) | A quantidade deve ser incrementada para 2. |
| 3      | Verificar o valor total no botão | O valor total no botão "Quero" deve ser atualizado para (preço × 2). |
| 4      | Clicar novamente no botão de aumentar | A quantidade deve ser incrementada para 3 e o valor total deve ser atualizado. |

#### **Resultados Esperados**

- A quantidade deve ser incrementada corretamente a cada clique.
- O valor total deve ser recalculado dinamicamente.
- Não deve haver limite máximo de quantidade (ou deve respeitar um limite se existir).

#### **Critérios de Aceitação**

- O botão de aumentar quantidade deve estar funcional.
- A quantidade deve ser atualizada imediatamente após o clique.
- O valor total deve refletir corretamente a quantidade selecionada.

---

### **CT008 - Diminuir Quantidade de um Produto**

#### **Objetivo**

Validar que o sistema permite diminuir a quantidade de um produto na página de detalhes, respeitando o valor mínimo de 1.

#### **Pré-Condições**

- O sistema McBugs deve estar online e acessível.
- O usuário deve estar na página de detalhes de um produto (/product/:id).
- A quantidade deve ser maior que 1.

#### **Passos**

| **Id** | **Ação**                          | **Resultado Esperado**                            |
|--------|------------------------------------|---------------------------------------------------|
| 1      | Aumentar a quantidade para 3 | A quantidade deve estar definida como 3. |
| 2      | Clicar no botão de diminuir quantidade (-) | A quantidade deve ser decrementada para 2. |
| 3      | Verificar o valor total no botão | O valor total no botão "Quero" deve ser atualizado para (preço × 2). |
| 4      | Diminuir a quantidade até 1 | A quantidade deve ser decrementada para 1 e o valor total deve ser atualizado. |
| 5      | Tentar diminuir quando a quantidade é 1 | A quantidade deve permanecer em 1 (não deve ser possível diminuir abaixo de 1). |

#### **Resultados Esperados**

- A quantidade deve ser decrementada corretamente a cada clique.
- O valor total deve ser recalculado dinamicamente.
- A quantidade não deve ser permitida abaixo de 1.

#### **Critérios de Aceitação**

- O botão de diminuir quantidade deve estar funcional.
- A quantidade deve ser atualizada imediatamente após o clique.
- A quantidade mínima deve ser respeitada (não pode ser menor que 1).
- O valor total deve refletir corretamente a quantidade selecionada.

---

### **CT009 - Adicionar Produto ao Carrinho**

#### **Objetivo**

Validar que o sistema permite adicionar um produto ao carrinho com a quantidade selecionada.

#### **Pré-Condições**

- O sistema McBugs deve estar online e acessível.
- O usuário deve estar na página de detalhes de um produto (/product/:id).
- O carrinho pode estar vazio ou conter outros produtos.

#### **Passos**

| **Id** | **Ação**                          | **Resultado Esperado**                            |
|--------|------------------------------------|---------------------------------------------------|
| 1      | Selecionar uma quantidade para o produto | A quantidade deve estar definida (ex: 2). |
| 2      | Verificar o valor total no botão | O botão "Quero" deve exibir o valor total calculado (preço × quantidade). |
| 3      | Clicar no botão "Quero" | O produto deve ser adicionado ao carrinho com a quantidade selecionada e o usuário deve ser redirecionado para o menu (/menu). |
| 4      | Verificar o carrinho | O contador de itens no carrinho deve ser atualizado refletindo a quantidade adicionada. |

#### **Resultados Esperados**

- O produto deve ser adicionado ao carrinho com sucesso.
- A quantidade selecionada deve ser respeitada.
- O usuário deve ser redirecionado para o menu após adicionar o produto.
- O carrinho deve ser atualizado visualmente.

#### **Critérios de Aceitação**

- O produto deve ser adicionado ao carrinho corretamente.
- A quantidade adicionada deve corresponder à quantidade selecionada.
- O redirecionamento para o menu deve ocorrer após a adição.
- O contador de itens no carrinho deve ser atualizado.

---

### **CT010 - Adicionar o Mesmo Produto Múltiplas Vezes**

#### **Objetivo**

Validar que o sistema agrupa corretamente quando o mesmo produto é adicionado ao carrinho múltiplas vezes.

#### **Pré-Condições**

- O sistema McBugs deve estar online e acessível.
- O usuário deve estar na página do menu (/menu).
- O carrinho pode estar vazio ou conter produtos.

#### **Passos**

| **Id** | **Ação**                          | **Resultado Esperado**                            |
|--------|------------------------------------|---------------------------------------------------|
| 1      | Adicionar um produto ao carrinho (quantidade 1) | O produto deve ser adicionado ao carrinho. |
| 2      | Adicionar o mesmo produto novamente (quantidade 2) | A quantidade do produto no carrinho deve ser atualizada para 3 (1 + 2), não criando um item duplicado. |
| 3      | Verificar o carrinho | O carrinho deve conter apenas uma entrada para o produto com quantidade total de 3. |

#### **Resultados Esperados**

- O sistema deve agrupar produtos idênticos no carrinho.
- A quantidade deve ser somada quando o mesmo produto é adicionado novamente.
- Não deve haver itens duplicados no carrinho.

#### **Critérios de Aceitação**

- Produtos idênticos devem ser agrupados no carrinho.
- A quantidade deve ser somada corretamente.
- Não deve haver duplicação de itens no carrinho.

---

## Fluxo de Gerenciamento do Carrinho

### **CT011 - Visualizar Carrinho Vazio**

#### **Objetivo**

Validar que o sistema exibe corretamente a mensagem quando o carrinho está vazio.

#### **Pré-Condições**

- O sistema McBugs deve estar online e acessível.
- O carrinho deve estar vazio.
- O usuário deve acessar a página do carrinho (/cart).

#### **Passos**

| **Id** | **Ação**                          | **Resultado Esperado**                            |
|--------|------------------------------------|---------------------------------------------------|
| 1      | Acessar a página do carrinho | A página do carrinho deve ser carregada. |
| 2      | Verificar a mensagem exibida | Deve ser exibida uma mensagem indicando que o carrinho está vazio: "Nada Encontrado Aqui" e "Seu carrinho está vazio. Adicione alguns itens deliciosos!". |
| 3      | Verificar o botão de ação | Deve ser exibido um botão "Ver cardápio" que redireciona para o menu. |
| 4      | Clicar no botão "Ver cardápio" | O usuário deve ser redirecionado para a página do menu (/menu). |

#### **Resultados Esperados**

- A mensagem de carrinho vazio deve ser exibida claramente.
- O botão de ação deve estar funcional.
- A navegação para o menu deve funcionar corretamente.

#### **Critérios de Aceitação**

- A mensagem de carrinho vazio deve ser exibida quando não há itens.
- O botão "Ver cardápio" deve redirecionar corretamente para o menu.
- A interface deve ser clara e intuitiva.

---

### **CT012 - Visualizar Itens do Carrinho**

#### **Objetivo**

Validar que o sistema exibe corretamente todos os itens adicionados ao carrinho com suas informações.

#### **Pré-Condições**

- O sistema McBugs deve estar online e acessível.
- O carrinho deve conter pelo menos um item.
- O usuário deve acessar a página do carrinho (/cart).

#### **Passos**

| **Id** | **Ação**                          | **Resultado Esperado**                            |
|--------|------------------------------------|---------------------------------------------------|
| 1      | Acessar a página do carrinho | A página do carrinho deve ser carregada. |
| 2      | Verificar a exibição dos itens | Cada item do carrinho deve exibir: imagem do produto, nome, preço unitário, quantidade e subtotal. |
| 3      | Verificar o total do pedido | Deve ser exibido o total do pedido calculado corretamente (soma de todos os subtotais). |
| 4      | Verificar os botões de ação | Devem ser exibidos os botões "Finalizar pedido" e "Continuar comprando". |

#### **Resultados Esperados**

- Todos os itens do carrinho devem ser exibidos corretamente.
- As informações de cada item devem estar completas e corretas.
- O total do pedido deve ser calculado corretamente.

#### **Critérios de Aceitação**

- Todos os itens do carrinho devem ser exibidos.
- As informações de cada item devem estar corretas (nome, preço, quantidade, subtotal).
- O total do pedido deve ser calculado corretamente.
- Os botões de ação devem estar visíveis e funcionais.

---

### **CT013 - Aumentar Quantidade de Item no Carrinho**

#### **Objetivo**

Validar que o sistema permite aumentar a quantidade de um item diretamente no carrinho.

#### **Pré-Condições**

- O sistema McBugs deve estar online e acessível.
- O carrinho deve conter pelo menos um item.
- O usuário deve estar na página do carrinho (/cart).

#### **Passos**

| **Id** | **Ação**                          | **Resultado Esperado**                            |
|--------|------------------------------------|---------------------------------------------------|
| 1      | Verificar a quantidade atual de um item | A quantidade atual do item deve ser exibida (ex: 1). |
| 2      | Clicar no botão de aumentar quantidade (+) | A quantidade do item deve ser incrementada (ex: 2). |
| 3      | Verificar o subtotal do item | O subtotal do item deve ser atualizado (preço × nova quantidade). |
| 4      | Verificar o total do pedido | O total do pedido deve ser recalculado e atualizado. |

#### **Resultados Esperados**

- A quantidade do item deve ser incrementada corretamente.
- O subtotal do item deve ser recalculado.
- O total do pedido deve ser atualizado.

#### **Critérios de Aceitação**

- O botão de aumentar quantidade deve estar funcional.
- A quantidade deve ser atualizada imediatamente.
- Os valores (subtotal e total) devem ser recalculados corretamente.

---

### **CT014 - Diminuir Quantidade de Item no Carrinho**

#### **Objetivo**

Validar que o sistema permite diminuir a quantidade de um item no carrinho e remove o item quando a quantidade chega a zero.

#### **Pré-Condições**

- O sistema McBugs deve estar online e acessível.
- O carrinho deve conter pelo menos um item com quantidade maior que 1.
- O usuário deve estar na página do carrinho (/cart).

#### **Passos**

| **Id** | **Ação**                          | **Resultado Esperado**                            |
|--------|------------------------------------|---------------------------------------------------|
| 1      | Verificar a quantidade atual de um item | A quantidade atual do item deve ser maior que 1 (ex: 3). |
| 2      | Clicar no botão de diminuir quantidade (-) | A quantidade do item deve ser decrementada (ex: 2). |
| 3      | Verificar o subtotal do item | O subtotal do item deve ser atualizado (preço × nova quantidade). |
| 4      | Verificar o total do pedido | O total do pedido deve ser recalculado e atualizado. |
| 5      | Diminuir a quantidade até 0 | O item deve ser removido do carrinho quando a quantidade chega a 0. |

#### **Resultados Esperados**

- A quantidade do item deve ser decrementada corretamente.
- O subtotal do item deve ser recalculado.
- O total do pedido deve ser atualizado.
- O item deve ser removido quando a quantidade chega a 0.

#### **Critérios de Aceitação**

- O botão de diminuir quantidade deve estar funcional.
- A quantidade deve ser atualizada imediatamente.
- Os valores (subtotal e total) devem ser recalculados corretamente.
- O item deve ser removido automaticamente quando a quantidade chega a 0.

---

### **CT015 - Remover Item do Carrinho**

#### **Objetivo**

Validar que o sistema permite remover um item do carrinho completamente.

#### **Pré-Condições**

- O sistema McBugs deve estar online e acessível.
- O carrinho deve conter pelo menos um item.
- O usuário deve estar na página do carrinho (/cart).

#### **Passos**

| **Id** | **Ação**                          | **Resultado Esperado**                            |
|--------|------------------------------------|---------------------------------------------------|
| 1      | Verificar os itens no carrinho | Deve haver pelo menos um item no carrinho. |
| 2      | Clicar no botão de remover item (ícone de lixeira) | O item deve ser removido do carrinho imediatamente. |
| 3      | Verificar o total do pedido | O total do pedido deve ser recalculado sem incluir o item removido. |
| 4      | Verificar se o item foi removido | O item não deve mais aparecer na lista de itens do carrinho. |

#### **Resultados Esperados**

- O item deve ser removido do carrinho imediatamente.
- O total do pedido deve ser recalculado corretamente.
- A interface deve ser atualizada sem o item removido.

#### **Critérios de Aceitação**

- O botão de remover item deve estar funcional.
- O item deve ser removido imediatamente após o clique.
- O total do pedido deve ser recalculado corretamente.
- Se o carrinho ficar vazio, a mensagem de carrinho vazio deve ser exibida.

---

### **CT016 - Continuar Comprando a Partir do Carrinho**

#### **Objetivo**

Validar que o sistema permite retornar ao menu para continuar adicionando produtos ao carrinho.

#### **Pré-Condições**

- O sistema McBugs deve estar online e acessível.
- O carrinho deve conter pelo menos um item.
- O usuário deve estar na página do carrinho (/cart).

#### **Passos**

| **Id** | **Ação**                          | **Resultado Esperado**                            |
|--------|------------------------------------|---------------------------------------------------|
| 1      | Verificar os itens no carrinho | Deve haver itens no carrinho. |
| 2      | Clicar no botão "Continuar comprando" | O usuário deve ser redirecionado para a página do menu (/menu). |
| 3      | Verificar que os itens foram preservados | Os itens do carrinho devem permanecer no carrinho após retornar ao menu. |
| 4      | Adicionar um novo produto | O novo produto deve ser adicionado ao carrinho junto com os itens existentes. |

#### **Resultados Esperados**

- O usuário deve ser redirecionado para o menu.
- Os itens do carrinho devem ser preservados.
- Novos produtos podem ser adicionados ao carrinho existente.

#### **Critérios de Aceitação**

- O botão "Continuar comprando" deve redirecionar para o menu.
- Os itens do carrinho devem ser preservados durante a navegação.
- Novos produtos devem ser adicionados corretamente ao carrinho existente.

---

## Fluxo de Finalização de Pedido

### **CT017 - Finalizar Pedido com Nome Válido**

#### **Objetivo**

Validar que o sistema permite finalizar um pedido quando o usuário informa um nome válido.

#### **Pré-Condições**

- O sistema McBugs deve estar online e acessível.
- O carrinho deve conter pelo menos um item.
- O usuário deve estar na página do carrinho (/cart).
- O Supabase deve estar configurado e acessível.

#### **Passos**

| **Id** | **Ação**                          | **Resultado Esperado**                            |
|--------|------------------------------------|---------------------------------------------------|
| 1      | Clicar no botão "Finalizar pedido" | O drawer de checkout deve ser aberto solicitando o nome do cliente. |
| 2      | Verificar o campo de nome | Deve ser exibido um campo de input para inserir o nome. |
| 3      | Inserir um nome válido (ex: "João Silva") | O nome deve ser inserido no campo. |
| 4      | Clicar no botão "Finalizar" | O sistema deve criar o pedido no banco de dados, limpar o carrinho e redirecionar para a página de pagamento (/payment). |
| 5      | Verificar o redirecionamento | O usuário deve ser redirecionado para a página de pagamento com o pedido criado. |

#### **Resultados Esperados**

- O drawer de checkout deve ser aberto corretamente.
- O pedido deve ser criado no banco de dados com status "pending".
- O carrinho deve ser limpo após a criação do pedido.
- O usuário deve ser redirecionado para a página de pagamento.

#### **Critérios de Aceitação**

- O drawer de checkout deve abrir quando o botão "Finalizar pedido" é clicado.
- O campo de nome deve aceitar entrada de texto.
- O pedido deve ser criado no banco de dados com todas as informações corretas.
- O carrinho deve ser limpo após a criação do pedido.
- O redirecionamento para a página de pagamento deve ocorrer corretamente.

---

### **CT018 - Tentar Finalizar Pedido sem Informar Nome**

#### **Objetivo**

Validar que o sistema não permite finalizar um pedido sem informar o nome do cliente.

#### **Pré-Condições**

- O sistema McBugs deve estar online e acessível.
- O carrinho deve conter pelo menos um item.
- O usuário deve estar na página do carrinho (/cart).

#### **Passos**

| **Id** | **Ação**                          | **Resultado Esperado**                            |
|--------|------------------------------------|---------------------------------------------------|
| 1      | Clicar no botão "Finalizar pedido" | O drawer de checkout deve ser aberto. |
| 2      | Deixar o campo de nome vazio | O campo de nome deve estar vazio. |
| 3      | Tentar clicar no botão "Finalizar" | O botão deve estar desabilitado ou deve ser exibida uma mensagem de validação indicando que o nome é obrigatório. |
| 4      | Verificar que o pedido não foi criado | O pedido não deve ser criado e o usuário deve permanecer na página do carrinho. |

#### **Resultados Esperados**

- O sistema deve validar que o nome é obrigatório.
- O pedido não deve ser criado sem o nome.
- Uma mensagem de validação deve ser exibida (se aplicável).

#### **Critérios de Aceitação**

- O campo de nome deve ser obrigatório.
- O sistema deve impedir a criação do pedido sem o nome.
- Uma validação apropriada deve ser exibida ao usuário.

---

### **CT019 - Cancelar Finalização de Pedido**

#### **Objetivo**

Validar que o sistema permite cancelar a finalização do pedido e retornar ao carrinho.

#### **Pré-Condições**

- O sistema McBugs deve estar online e acessível.
- O carrinho deve conter pelo menos um item.
- O usuário deve estar na página do carrinho (/cart).

#### **Passos**

| **Id** | **Ação**                          | **Resultado Esperado**                            |
|--------|------------------------------------|---------------------------------------------------|
| 1      | Clicar no botão "Finalizar pedido" | O drawer de checkout deve ser aberto. |
| 2      | Clicar no botão "Cancelar" | O drawer deve ser fechado e o usuário deve retornar à página do carrinho. |
| 3      | Verificar que os itens foram preservados | Os itens do carrinho devem permanecer intactos. |
| 4      | Verificar que o pedido não foi criado | Nenhum pedido deve ser criado no banco de dados. |

#### **Resultados Esperados**

- O drawer deve ser fechado corretamente.
- Os itens do carrinho devem ser preservados.
- Nenhum pedido deve ser criado.

#### **Critérios de Aceitação**

- O botão "Cancelar" deve fechar o drawer.
- Os itens do carrinho devem ser preservados após o cancelamento.
- Nenhum pedido deve ser criado quando o usuário cancela.

---

## Fluxo de Pagamento

### **CT020 - Visualizar Opções de Pagamento**

#### **Objetivo**

Validar que o sistema exibe corretamente todas as opções de pagamento disponíveis.

#### **Pré-Condições**

- O sistema McBugs deve estar online e acessível.
- Deve existir um pedido criado (currentOrder).
- O usuário deve estar na página de pagamento (/payment).

#### **Passos**

| **Id** | **Ação**                          | **Resultado Esperado**                            |
|--------|------------------------------------|---------------------------------------------------|
| 1      | Acessar a página de pagamento | A página de pagamento deve ser carregada. |
| 2      | Verificar o resumo do pedido | Deve ser exibido um card com o número do pedido e o total. |
| 3      | Verificar as opções de pagamento | Devem ser exibidas três opções: PIX, Cartão de Débito e Cartão de Crédito. |
| 4      | Verificar as informações de cada opção | Cada opção deve exibir: ícone, nome e descrição "Pagamento no balcão na hora da retirada". |
| 5      | Verificar o botão de cancelar pedido | Deve ser exibido um botão "Cancelar Pedido" na parte inferior da página. |

#### **Resultados Esperados**

- Todas as opções de pagamento devem ser exibidas.
- O resumo do pedido deve estar visível e correto.
- As informações de cada método de pagamento devem estar claras.

#### **Critérios de Aceitação**

- Todas as três opções de pagamento devem estar visíveis.
- O resumo do pedido deve exibir o número e o total corretamente.
- Cada opção de pagamento deve ter informações claras e visíveis.

---

### **CT021 - Selecionar Pagamento via PIX**

#### **Objetivo**

Validar que o sistema permite selecionar o pagamento via PIX e redireciona para a confirmação.

#### **Pré-Condições**

- O sistema McBugs deve estar online e acessível.
- Deve existir um pedido criado (currentOrder).
- O usuário deve estar na página de pagamento (/payment).

#### **Passos**

| **Id** | **Ação**                          | **Resultado Esperado**                            |
|--------|------------------------------------|---------------------------------------------------|
| 1      | Verificar a opção PIX | A opção PIX deve estar visível com ícone e descrição. |
| 2      | Clicar na opção PIX | O método de pagamento do pedido deve ser atualizado para "pix" e o usuário deve ser redirecionado para /payment/pix/confirm. |
| 3      | Verificar o redirecionamento | O usuário deve estar na página de confirmação de pagamento PIX. |

#### **Resultados Esperados**

- O método de pagamento deve ser atualizado no banco de dados.
- O usuário deve ser redirecionado para a página de confirmação PIX.
- A navegação deve ocorrer sem erros.

#### **Critérios de Aceitação**

- A opção PIX deve ser clicável.
- O método de pagamento deve ser atualizado corretamente.
- O redirecionamento deve ocorrer corretamente.

---

### **CT022 - Selecionar Pagamento via Cartão de Débito**

#### **Objetivo**

Validar que o sistema permite selecionar o pagamento via cartão de débito e redireciona para a confirmação.

#### **Pré-Condições**

- O sistema McBugs deve estar online e acessível.
- Deve existir um pedido criado (currentOrder).
- O usuário deve estar na página de pagamento (/payment).

#### **Passos**

| **Id** | **Ação**                          | **Resultado Esperado**                            |
|--------|------------------------------------|---------------------------------------------------|
| 1      | Verificar a opção Cartão de Débito | A opção Cartão de Débito deve estar visível com ícone e descrição. |
| 2      | Clicar na opção Cartão de Débito | O método de pagamento do pedido deve ser atualizado para "debit" e o usuário deve ser redirecionado para /payment/debit/confirm. |
| 3      | Verificar o redirecionamento | O usuário deve estar na página de confirmação de pagamento. |

#### **Resultados Esperados**

- O método de pagamento deve ser atualizado no banco de dados.
- O usuário deve ser redirecionado para a página de confirmação.
- A navegação deve ocorrer sem erros.

#### **Critérios de Aceitação**

- A opção Cartão de Débito deve ser clicável.
- O método de pagamento deve ser atualizado corretamente.
- O redirecionamento deve ocorrer corretamente.

---

### **CT023 - Selecionar Pagamento via Cartão de Crédito**

#### **Objetivo**

Validar que o sistema permite selecionar o pagamento via cartão de crédito e redireciona para a confirmação.

#### **Pré-Condições**

- O sistema McBugs deve estar online e acessível.
- Deve existir um pedido criado (currentOrder).
- O usuário deve estar na página de pagamento (/payment).

#### **Passos**

| **Id** | **Ação**                          | **Resultado Esperado**                            |
|--------|------------------------------------|---------------------------------------------------|
| 1      | Verificar a opção Cartão de Crédito | A opção Cartão de Crédito deve estar visível com ícone e descrição. |
| 2      | Clicar na opção Cartão de Crédito | O método de pagamento do pedido deve ser atualizado para "credit" e o usuário deve ser redirecionado para /payment/credit/confirm. |
| 3      | Verificar o redirecionamento | O usuário deve estar na página de confirmação de pagamento. |

#### **Resultados Esperados**

- O método de pagamento deve ser atualizado no banco de dados.
- O usuário deve ser redirecionado para a página de confirmação.
- A navegação deve ocorrer sem erros.

#### **Critérios de Aceitação**

- A opção Cartão de Crédito deve ser clicável.
- O método de pagamento deve ser atualizado corretamente.
- O redirecionamento deve ocorrer corretamente.

---

### **CT024 - Cancelar Pedido na Página de Pagamento**

#### **Objetivo**

Validar que o sistema permite cancelar um pedido na página de pagamento.

#### **Pré-Condições**

- O sistema McBugs deve estar online e acessível.
- Deve existir um pedido criado (currentOrder).
- O usuário deve estar na página de pagamento (/payment).

#### **Passos**

| **Id** | **Ação**                          | **Resultado Esperado**                            |
|--------|------------------------------------|---------------------------------------------------|
| 1      | Verificar o botão "Cancelar Pedido" | O botão "Cancelar Pedido" deve estar visível na parte inferior da página. |
| 2      | Clicar no botão "Cancelar Pedido" | O pedido deve ser cancelado no banco de dados (status = "cancelled"), o carrinho deve ser limpo e o usuário deve ser redirecionado para a página inicial (/). |
| 3      | Verificar o redirecionamento | O usuário deve estar na página inicial. |
| 4      | Verificar que o pedido foi cancelado | O pedido deve ter status "cancelled" no banco de dados. |

#### **Resultados Esperados**

- O pedido deve ser cancelado no banco de dados.
- O carrinho deve ser limpo.
- O usuário deve ser redirecionado para a página inicial.

#### **Critérios de Aceitação**

- O botão "Cancelar Pedido" deve estar funcional.
- O pedido deve ser atualizado com status "cancelled" no banco de dados.
- O carrinho e localStorage devem ser limpos.
- O redirecionamento para a página inicial deve ocorrer corretamente.

---

### **CT025 - Acessar Página de Pagamento sem Pedido**

#### **Objetivo**

Validar que o sistema redireciona o usuário quando tenta acessar a página de pagamento sem um pedido criado.

#### **Pré-Condições**

- O sistema McBugs deve estar online e acessível.
- Não deve existir um pedido criado (currentOrder = null).
- O usuário deve tentar acessar a página de pagamento (/payment).

#### **Passos**

| **Id** | **Ação**                          | **Resultado Esperado**                            |
|--------|------------------------------------|---------------------------------------------------|
| 1      | Tentar acessar a página de pagamento diretamente | O sistema deve detectar que não há pedido criado. |
| 2      | Verificar o redirecionamento | O usuário deve ser redirecionado automaticamente para a página inicial (/). |

#### **Resultados Esperados**

- O sistema deve detectar a ausência de um pedido.
- O usuário deve ser redirecionado para a página inicial.

#### **Critérios de Aceitação**

- O sistema deve validar a existência de um pedido antes de exibir a página de pagamento.
- O redirecionamento automático deve ocorrer quando não há pedido.

---

## Fluxo de Confirmação de Pedido

### **CT026 - Visualizar Confirmação de Pedido PIX**

#### **Objetivo**

Validar que o sistema exibe corretamente a página de confirmação de pedido para pagamento via PIX.

#### **Pré-Condições**

- O sistema McBugs deve estar online e acessível.
- Deve existir um pedido criado com método de pagamento PIX.
- O usuário deve estar na página de confirmação de pagamento PIX (/payment/pix/confirm).

#### **Passos**

| **Id** | **Ação**                          | **Resultado Esperado**                            |
|--------|------------------------------------|---------------------------------------------------|
| 1      | Acessar a página de confirmação PIX | A página de confirmação deve ser carregada. |
| 2      | Verificar o resumo do pedido | Deve ser exibido o número do pedido e o total. |
| 3      | Verificar as instruções de pagamento | Deve ser exibida uma mensagem indicando "Pagamento no Balcão" e instruções para pagar com PIX. |
| 4      | Verificar os detalhes do pedido | Devem ser exibidos: cliente, tipo de pedido, forma de pagamento, data e lista de itens. |
| 5      | Verificar o botão "Fazer Novo Pedido" | Deve ser exibido um botão para fazer um novo pedido. |

#### **Resultados Esperados**

- Todas as informações do pedido devem ser exibidas corretamente.
- As instruções de pagamento devem estar claras.
- O botão de ação deve estar visível e funcional.

#### **Critérios de Aceitação**

- O resumo do pedido deve estar correto.
- As instruções de pagamento devem estar claras.
- Os detalhes do pedido devem estar completos e corretos.
- O botão "Fazer Novo Pedido" deve estar funcional.

---

### **CT027 - Visualizar Confirmação de Pedido Cartão**

#### **Objetivo**

Validar que o sistema exibe corretamente a página de confirmação de pedido para pagamento via cartão.

#### **Pré-Condições**

- O sistema McBugs deve estar online e acessível.
- Deve existir um pedido criado com método de pagamento cartão (débito ou crédito).
- O usuário deve estar na página de confirmação de pagamento (/payment/:method/confirm).

#### **Passos**

| **Id** | **Ação**                          | **Resultado Esperado**                            |
|--------|------------------------------------|---------------------------------------------------|
| 1      | Acessar a página de confirmação | A página de confirmação deve ser carregada. |
| 2      | Verificar o resumo do pedido | Deve ser exibido o número do pedido e o total. |
| 3      | Verificar as instruções de pagamento | Deve ser exibida uma mensagem indicando "Pagamento no Balcão" e instruções para pagar com cartão. |
| 4      | Verificar os detalhes do pedido | Devem ser exibidos: cliente, tipo de pedido, forma de pagamento, data e lista de itens. |
| 5      | Verificar o botão "Fazer Novo Pedido" | Deve ser exibido um botão para fazer um novo pedido. |

#### **Resultados Esperados**

- Todas as informações do pedido devem ser exibidas corretamente.
- As instruções de pagamento devem estar claras.
- O botão de ação deve estar visível e funcional.

#### **Critérios de Aceitação**

- O resumo do pedido deve estar correto.
- As instruções de pagamento devem estar claras.
- Os detalhes do pedido devem estar completos e corretos.
- O botão "Fazer Novo Pedido" deve estar funcional.

---

### **CT028 - Fazer Novo Pedido Após Confirmação**

#### **Objetivo**

Validar que o sistema permite iniciar um novo pedido após a confirmação do pedido anterior.

#### **Pré-Condições**

- O sistema McBugs deve estar online e acessível.
- Deve existir um pedido confirmado.
- O usuário deve estar na página de confirmação de pagamento.

#### **Passos**

| **Id** | **Ação**                          | **Resultado Esperado**                            |
|--------|------------------------------------|---------------------------------------------------|
| 1      | Verificar o botão "Fazer Novo Pedido" | O botão deve estar visível na página de confirmação. |
| 2      | Clicar no botão "Fazer Novo Pedido" | O pedido atual deve ser resetado, o carrinho deve ser limpo e o usuário deve ser redirecionado para a página inicial (/). |
| 3      | Verificar o redirecionamento | O usuário deve estar na página inicial. |
| 4      | Verificar que o carrinho está vazio | O carrinho deve estar vazio e pronto para um novo pedido. |

#### **Resultados Esperados**

- O pedido atual deve ser resetado.
- O carrinho deve ser limpo.
- O usuário deve ser redirecionado para a página inicial.

#### **Critérios de Aceitação**

- O botão "Fazer Novo Pedido" deve estar funcional.
- O pedido e carrinho devem ser limpos corretamente.
- O redirecionamento para a página inicial deve ocorrer corretamente.
- O sistema deve estar pronto para iniciar um novo pedido.

---

### **CT029 - Verificar Mensagem para Pedido Dine-In**

#### **Objetivo**

Validar que o sistema exibe uma mensagem específica para pedidos do tipo "dine-in" na confirmação.

#### **Pré-Condições**

- O sistema McBugs deve estar online e acessível.
- Deve existir um pedido criado com tipo "dine-in".
- O usuário deve estar na página de confirmação de pagamento.

#### **Passos**

| **Id** | **Ação**                          | **Resultado Esperado**                            |
|--------|------------------------------------|---------------------------------------------------|
| 1      | Verificar o tipo de pedido | O pedido deve ser do tipo "dine-in" (Comer no local). |
| 2      | Verificar a mensagem exibida | Deve ser exibida uma mensagem informando: "Após o pagamento, aguarde ser chamado pelo número do seu pedido.". |
| 3      | Verificar que a mensagem não aparece para takeaway | Se o pedido fosse "takeaway", a mensagem não deveria aparecer. |

#### **Resultados Esperados**

- A mensagem específica para dine-in deve ser exibida.
- A mensagem deve estar clara e informativa.

#### **Critérios de Aceitação**

- A mensagem deve ser exibida apenas para pedidos do tipo "dine-in".
- A mensagem deve estar clara e informativa.
- A mensagem não deve aparecer para pedidos do tipo "takeaway".

---

## Cenários de Erro e Validação

### **CT030 - Acessar Página de Produto Inexistente**

#### **Objetivo**

Validar que o sistema trata corretamente o acesso a uma página de produto que não existe.

#### **Pré-Condições**

- O sistema McBugs deve estar online e acessível.
- O usuário deve tentar acessar uma URL de produto inexistente (/product/id-inexistente).

#### **Passos**

| **Id** | **Ação**                          | **Resultado Esperado**                            |
|--------|------------------------------------|---------------------------------------------------|
| 1      | Tentar acessar uma URL de produto inexistente | O sistema deve detectar que o produto não existe. |
| 2      | Verificar a mensagem exibida | Deve ser exibida uma mensagem indicando "Produto não encontrado". |

#### **Resultados Esperados**

- O sistema deve detectar que o produto não existe.
- Uma mensagem apropriada deve ser exibida ao usuário.

#### **Critérios de Aceitação**

- O sistema deve validar a existência do produto antes de exibir a página.
- Uma mensagem clara deve ser exibida quando o produto não existe.
- O sistema não deve quebrar ou exibir erros técnicos.

---

### **CT031 - Acessar Rota Inexistente**

#### **Objetivo**

Validar que o sistema trata corretamente o acesso a rotas que não existem no sistema.

#### **Pré-Condições**

- O sistema McBugs deve estar online e acessível.
- O usuário deve tentar acessar uma rota inexistente (ex: /rota-inexistente).

#### **Passos**

| **Id** | **Ação**                          | **Resultado Esperado**                            |
|--------|------------------------------------|---------------------------------------------------|
| 1      | Tentar acessar uma rota inexistente | O sistema deve detectar que a rota não existe. |
| 2      | Verificar a página exibida | Deve ser exibida a página "NotFound" (404) com uma mensagem apropriada. |

#### **Resultados Esperados**

- O sistema deve detectar que a rota não existe.
- A página 404 deve ser exibida com uma mensagem apropriada.

#### **Critérios de Aceitação**

- O sistema deve tratar rotas inexistentes corretamente.
- A página 404 deve ser exibida quando uma rota não existe.
- O sistema não deve quebrar ou exibir erros técnicos.

---

### **CT032 - Persistência do Carrinho no LocalStorage**

#### **Objetivo**

Validar que o sistema persiste os itens do carrinho no localStorage e os recupera após recarregar a página.

#### **Pré-Condições**

- O sistema McBugs deve estar online e acessível.
- O carrinho deve conter pelo menos um item.

#### **Passos**

| **Id** | **Ação**                          | **Resultado Esperado**                            |
|--------|------------------------------------|---------------------------------------------------|
| 1      | Adicionar itens ao carrinho | Os itens devem ser adicionados ao carrinho. |
| 2      | Verificar o localStorage | Os itens devem ser salvos no localStorage. |
| 3      | Recarregar a página (F5) | A página deve ser recarregada. |
| 4      | Verificar o carrinho após recarregar | Os itens do carrinho devem ser recuperados do localStorage e exibidos corretamente. |

#### **Resultados Esperados**

- Os itens do carrinho devem ser salvos no localStorage.
- Os itens devem ser recuperados após recarregar a página.
- O carrinho deve manter os itens corretamente.

#### **Critérios de Aceitação**

- Os itens do carrinho devem ser persistidos no localStorage.
- Os itens devem ser recuperados corretamente após recarregar a página.
- O carrinho deve funcionar corretamente após a recuperação.

---

### **CT033 - Persistência do Tipo de Pedido no LocalStorage**

#### **Objetivo**

Validar que o sistema persiste o tipo de pedido no localStorage e o recupera após recarregar a página.

#### **Pré-Condições**

- O sistema McBugs deve estar online e acessível.
- O usuário deve ter selecionado um tipo de pedido (dine-in ou takeaway).

#### **Passos**

| **Id** | **Ação**                          | **Resultado Esperado**                            |
|--------|------------------------------------|---------------------------------------------------|
| 1      | Selecionar um tipo de pedido | O tipo de pedido deve ser selecionado (ex: "dine-in"). |
| 2      | Verificar o localStorage | O tipo de pedido deve ser salvo no localStorage. |
| 3      | Recarregar a página (F5) | A página deve ser recarregada. |
| 4      | Verificar o tipo de pedido após recarregar | O tipo de pedido deve ser recuperado do localStorage e mantido. |

#### **Resultados Esperados**

- O tipo de pedido deve ser salvo no localStorage.
- O tipo de pedido deve ser recuperado após recarregar a página.
- O tipo de pedido deve ser mantido corretamente.

#### **Critérios de Aceitação**

- O tipo de pedido deve ser persistido no localStorage.
- O tipo de pedido deve ser recuperado corretamente após recarregar a página.
- O tipo de pedido deve ser mantido durante a navegação.

---

### **CT034 - Cálculo Correto do Total do Pedido**

#### **Objetivo**

Validar que o sistema calcula corretamente o total do pedido considerando todos os itens e suas quantidades.

#### **Pré-Condições**

- O sistema McBugs deve estar online e acessível.
- O carrinho deve conter múltiplos itens com quantidades diferentes.

#### **Passos**

| **Id** | **Ação**                          | **Resultado Esperado**                            |
|--------|------------------------------------|---------------------------------------------------|
| 1      | Adicionar item 1 com quantidade 2 (preço R$ 10,00) | O item deve ser adicionado ao carrinho. |
| 2      | Adicionar item 2 com quantidade 1 (preço R$ 15,00) | O item deve ser adicionado ao carrinho. |
| 3      | Adicionar item 3 com quantidade 3 (preço R$ 5,00) | O item deve ser adicionado ao carrinho. |
| 4      | Verificar o total do pedido | O total deve ser calculado como: (2 × R$ 10,00) + (1 × R$ 15,00) + (3 × R$ 5,00) = R$ 50,00. |
| 5      | Alterar a quantidade de um item | O total deve ser recalculado corretamente. |

#### **Resultados Esperados**

- O total do pedido deve ser calculado corretamente.
- O cálculo deve considerar todas as quantidades e preços.
- O total deve ser atualizado quando as quantidades mudam.

#### **Critérios de Aceitação**

- O cálculo do total deve estar correto.
- O total deve ser atualizado dinamicamente quando itens são adicionados, removidos ou quantidades alteradas.
- O formato de exibição do preço deve estar correto (R$ X,XX).

---

### **CT035 - Validação de Conexão com Banco de Dados**

#### **Objetivo**

Validar que o sistema trata corretamente erros de conexão com o banco de dados ao criar um pedido.

#### **Pré-Condições**

- O sistema McBugs deve estar online e acessível.
- O carrinho deve conter pelo menos um item.
- O Supabase deve estar inacessível ou com problemas de conexão (simular).

#### **Passos**

| **Id** | **Ação**                          | **Resultado Esperado**                            |
|--------|------------------------------------|---------------------------------------------------|
| 1      | Simular falha de conexão com o banco | O banco de dados deve estar inacessível. |
| 2      | Tentar finalizar um pedido | O sistema deve detectar o erro de conexão. |
| 3      | Verificar o tratamento do erro | Deve ser exibida uma mensagem de erro apropriada ao usuário. |
| 4      | Verificar que o carrinho foi preservado | Os itens do carrinho devem ser preservados (não devem ser limpos). |

#### **Resultados Esperados**

- O sistema deve detectar erros de conexão com o banco de dados.
- Uma mensagem de erro apropriada deve ser exibida.
- Os dados do carrinho devem ser preservados.

#### **Critérios de Aceitação**

- O sistema deve tratar erros de conexão com o banco de dados.
- Uma mensagem de erro clara deve ser exibida ao usuário.
- Os dados do carrinho devem ser preservados em caso de erro.
- O sistema não deve quebrar ou exibir erros técnicos ao usuário.

---

## Resumo dos Casos de Teste

Este documento contém **35 casos de teste** cobrindo os principais fluxos do sistema McBugs:

- **Fluxo de Seleção de Tipo de Pedido:** 2 casos de teste
- **Fluxo de Navegação no Menu:** 3 casos de teste
- **Fluxo de Visualização e Adição de Produtos:** 5 casos de teste
- **Fluxo de Gerenciamento do Carrinho:** 6 casos de teste
- **Fluxo de Finalização de Pedido:** 3 casos de teste
- **Fluxo de Pagamento:** 6 casos de teste
- **Fluxo de Confirmação de Pedido:** 4 casos de teste
- **Cenários de Erro e Validação:** 6 casos de teste

Todos os casos de teste foram elaborados seguindo o padrão estabelecido, com objetivo claro, pré-condições definidas, passos detalhados, resultados esperados e critérios de aceitação bem especificados.

---

**Fim do Documento**

