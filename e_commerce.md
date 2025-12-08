# EVENTSORTMING - E-COMMERCE

O Event Storming (Tempestade de Eventos) é uma metodologia de *workshop* flexível e colaborativa, ideal para **modelar e-commerce**, um domínio de negócio intrinsecamente complexo.

A metodologia Event Storming não se limita a um único diagrama, mas sim a uma progressão de níveis que leva o entendimento do negócio à arquitetura de *software*. O modelo completo de e-commerce é tipicamente mapeado usando essa progressão, começando com o nível estratégico (*Big Picture*) para definir o escopo e as fronteiras.

O modelo a seguir simula um **Big Picture (BPES)**, que foca na exploração de ponta a ponta do domínio, seguido pela aplicação dos conceitos do **Process Modeling (PLES)** para detalhar o fluxo central de pedido.

***

## 1. Notação Fundamental do E-commerce (Linguagem Ubíqua)

O Event Storming utiliza notas adesivas coloridas, onde cada cor representa um conceito específico no domínio de negócio.

| Elemento | Cor Padrão | Função no E-commerce | Exemplo | Fontes |
| :--- | :--- | :--- | :--- | :--- |
| **Evento de Domínio** | Laranja (Orange) | Um fato relevante que **já ocorreu** (verbo no passado) e que é crucial para o negócio. | **Order Placed** (Pedido Realizado); **Payment Processed** (Pagamento Processado); **Order Shipped** (Pedido Enviado). | |
| **Comando / Ação** | Azul (Blue) | A **intenção** ou solicitação de ação que causa um evento, tipicamente um *Verbo + Substantivo*. | **Place Order** (Fazer Pedido); **Process Payment** (Processar Pagamento); **Add to Cart** (Adicionar ao Carrinho). | |
| **Ator / Pessoa** | Amarelo (Small Yellow) | A entidade (humana ou sistema) que **inicia** um Comando. | **Customer** (Cliente); **Warehouse Staff** (Funcionário do Armazém); **Sales Representative**. | |
| **Sistema Externo** | Rosa (Pink) | Dependência ou serviço de terceiros tratado como **"caixa preta"** fora do controle direto do domínio modelado. | **Payment Gateway** (Stripe, PayPal); **Shipping Partner**; **Fraud Detection System**; **Tax Compliance Software**. | |
| **Política** | Lilás/Roxo (Purple/Lilac) | Regra de negócio automatizada (ou manual) que **reage** a um Evento e dispara um novo Comando (o "cola" lógica). | *Se Order Placed, Tentar Fraud Check*. *Se Payment Processed, Reservar Inventory*. | |
| **Aggregate** | Amarelo Claro / Tan | Uma **entidade de domínio** que executa o Comando, garantindo a consistência transacional. É a unidade fundamental de um Microsserviço. | **Order Aggregate**; **Inventory Aggregate**; **Customer Aggregate**. | |
| **Read Model** | Verde (Green) | A **informação** que o Ator precisa ver para tomar uma decisão ou emitir um Comando (ex: uma lista, um relatório). | *Product attributes* (Atributos do Produto); *Reviews* (Avaliações); *Price* (Preço). | |
| **Hot Spot** | Magenta / Vermelho | Áreas de **problemas, conflitos, gargalos** ou inconsistências que requerem atenção. | "Item é frequentemente perdido no armazém". | |

## 2. Modelagem Estratégica: Ciclo de Vida do Pedido e Contextos Delimitados (Bounded Contexts)

O Event Storming para e-commerce é tipicamente dividido em **Contextos Delimitados (BCs)**, que emergem da modelagem e se alinham aos microsserviços. O fluxo cronológico abaixo ilustra as interações entre esses contextos.

### Contextos Delimitados Emergentes no E-commerce:

| BC (Microsserviço) | Foco Principal |
| :--- | :--- |
| **Catalogue & Inventory** | Gestão de produtos, preços e disponibilidade de estoque. |
| **Order Management** | Ciclo de vida do pedido (da colocação ao envio). |
| **Payment & Billing** | Processamento financeiro, faturamento e conformidade fiscal. |
| **Shipping & Logistics** | Coordenação com parceiros de entrega. |

### Fluxo Detalhado do Pedido (Exemplo Combinado BPES/PLES)

O fluxo principal (caminho feliz) de um e-commerce é uma sequência de Eventos (Laranja), Comandos (Azul) e reações (Políticas/Agregados) que atravessam estes contextos.

---

### A. Contexto: Catálogo e Compra

O cliente interage com a loja antes de iniciar o processo de *checkout*.

| Etapa | Fluxo Event Storming | Elemento |
| :--- | :--- | :--- |
| **1. Navegação** | **Customer** | Ator (Yellow) |
| | $\rightarrow$ | **Browse Product** | Comando (Blue) |
| | **Visualização de Detalhes** | Read Model (Green) - Mostra *Product attributes, Price, Reviews* |
| **2. Adição ao Carrinho** | **Customer** | Ator (Yellow) |
| | $\rightarrow$ | **Add Item to Cart** | Comando (Blue) |
| | **Cart Aggregate** | Aggregate (Tan/Yellow) |
| | $\rightarrow$ | **Item Added to Cart** | Evento (Orange) |

---

### B. Contexto: Gestão de Pedidos & Pagamento

Esta é a área mais complexa, envolvendo coordenação e sistemas externos.

| Etapa | Fluxo Event Storming | Elemento |
| :--- | :--- | :--- |
| **3. Fechamento do Pedido** | **Customer** | Ator (Yellow) |
| | $\rightarrow$ | **Place Order** | Comando (Blue) |
| | **Order Aggregate** | Aggregate (Tan/Yellow) - *Define o Pedido* |
| | $\rightarrow$ | **Order Placed** | Evento (Orange) - *Sinaliza o início do processamento* |
| **4. Verificação de Fraude** | **Order Placed** | Evento (Orange) |
| | $\rightarrow$ | **Policy: *Verificar Fraude*** | Política (Purple) - *Regra de negócio automática* |
| | $\rightarrow$ | **Request Fraud Check** | Comando (Blue) |
| | **Fraud Detection System** | Sistema Externo (Pink) |
| | $\rightarrow$ | **Fraud Check Completed** | Evento (Orange) |
| **5. Processamento do Pagamento** | **Order Placed** | Evento (Orange) |
| | $\rightarrow$ | **Policy: *Tentar Processar Pagamento*** | Política (Purple) |
| | $\rightarrow$ | **Process Payment** | Comando (Blue) |
| | **Payment Gateway** | Sistema Externo (Pink) |
| | $\rightarrow$ | **Payment Processed** | Evento (Orange) |

---

### C. Contexto: Inventário e Logística

O fluxo se move para a reserva física e o envio, dependendo do sucesso da verificação de fraude e do pagamento.

| Etapa | Fluxo Event Storming | Elemento |
| :--- | :--- | :--- |
| **6. Reserva de Estoque** | **Payment Processed** e **Fraud Check Completed** | Eventos (Orange) |
| | $\rightarrow$ | **Policy: *Reservar Inventário*** | Política (Purple) |
| | $\rightarrow$ | **Reserve Inventory** | Comando (Blue) |
| | **Inventory Aggregate** | Aggregate (Tan/Yellow) - *Garante consistência de estoque* |
| | $\rightarrow$ | **Inventory Reserved** | Evento (Orange) |
| **7. Preparação para Envio** | **Inventory Reserved** | Evento (Orange) |
| | $\rightarrow$ | **Policy: *Preparar Pacote*** | Política (Purple) |
| | $\rightarrow$ | **Package Order** | Comando (Blue) |
| | **Warehouse Staff** | Ator (Yellow) |
| | $\rightarrow$ | **Item Packaged** | Evento (Orange) |
| **8. Envio** | **Item Packaged** | Evento (Orange) |
| | $\rightarrow$ | **Policy: *Solicitar Envio*** | Política (Purple) |
| | $\rightarrow$ | **Ship Order** | Comando (Blue) |
| | **Shipping Partner** | Sistema Externo (Pink) |
| | $\rightarrow$ | **Order Shipped** | Evento (Orange) |
| **9. Conclusão** | **Shipping Partner** | Sistema Externo (Pink) |
| | $\rightarrow$ | **Order Delivered** | Evento (Orange) - *Fato final do ciclo* |

***

## 3. Fluxo de Falha Crítico e Hot Spots (Pontos Quentes)

Um Event Storming completo deve mapear os cenários de falha (*edge cases*) e identificar problemas, utilizando *Hot Spots* (Magenta/Vermelho).

### Exemplo de Fluxo de Falha (Pagamento)

O Event Storming permite modelar a **Consistência Eventual**, um princípio chave na arquitetura de microsserviços.

| Cenário | Fluxo Event Storming | Elemento |
| :--- | :--- | :--- |
| **Falha de Pagamento** | **Payment Gateway** (Pink) $\rightarrow$ **Payment Failed** | Evento (Orange) |
| | **Payment Failed** $\rightarrow$ **Policy: *Compensar Falha*** | Política (Purple) - *Saga para garantir consistência* |
| | $\rightarrow$ | **Cancel Order** | Comando (Blue) enviado ao *Order Aggregate* |
| | $\rightarrow$ | **Release Inventory** | Comando (Blue) enviado ao *Inventory Aggregate* |
| | **Order Aggregate** $\rightarrow$ **Order Cancelled** | Evento (Orange) |
| | **Inventory Aggregate** $\rightarrow$ **Inventory Released** | Evento (Orange) |

### Hot Spots e Complexidades (Magenta/Vermelho)

Esses pontos representam áreas de incerteza, gargalos ou alto risco:

1.  **"Tax Compliance/Compliance Fiscal":** A complexidade de aderir às diversas leis tributárias é um desafio significativo no e-commerce. A Garantia de **cálculos de impostos precisos** e **arquivamentos oportunos** é crucial.
2.  **"Prevenção de Fraude":** A detecção de padrões que podem levar a fraudes está sempre evoluindo, sendo necessário aprender com os "buracos" descobertos no passado.
3.  **"Inconsistência de Preço":** A necessidade de garantir **regras e taxas consistentes** em todos os canais de vendas (e-commerce, *marketplaces*, ERP) para evitar insatisfação do cliente.
4.  **"Gerenciamento de Inventário":** Inconsistências como itens declarados perdidos que reaparecem meses depois, ou a gestão de inventário em **múltiplos locais**.

## 4. Próximos Passos (Transição para Software Design)

A visualização acima, após a validação e ordenação de eventos, permite que a equipe avance para os níveis mais detalhados:

*   **Software Design Event Storming (DLES):** Neste nível, os **Agregados** (Tan/Yellow) são refinados. Por exemplo, o *Order Aggregate* seria isolado para garantir que todos os Comandos e Eventos que alteram o estado do pedido (ex: *Cancel Order*, *Order Placed*) sejam manipulados dentro de seus limites, garantindo a **consistência transacional** interna.
*   **Design de Microsserviços:** Os **Contextos Delimitados** (BCs) identificados (Order Management, Payment & Billing, Inventory) tornam-se os **limites naturais** para os microsserviços, garantindo que cada serviço seja fracamente acoplado e alinhado com a lógica de negócio.
*   **Design de API:** Os **Comandos** (Azul) servem como um ponto de partida para as operações da API, e os **Eventos** (Laranja) definem os contratos de comunicação entre os microsserviços na arquitetura orientada a eventos.