

# 🧩 Contexto da Modelagem de Domínio com Event Storming Big Picture

O diretor de TI de um supermercado deseja implantar um software que realize a **gestão de vendas, compras, estoques e informações gerenciais**. Porém, para que o sistema reflita fielmente a rotina operacional do supermercado, o diretor decidiu realizar uma **modelagem de domínio** antes da implementação.

Para essa atividade, foi escolhida a metodologia **Event Storming Big Picture**, que permite compreender de forma colaborativa todos os processos do negócio. Cada setor do supermercado cedeu um funcionário para participar da modelagem (conforme o layout do supermercado).

Sabe-se que o objetivo de todo negócio é **obter lucro**, e para isso todas as seções devem trabalhar **de forma sincronizada**, garantindo que:

* os produtos estejam **disponíveis para venda**;
* estejam dentro do **prazo de validade**;
* o fluxo de informações entre setores seja consistente e claro.

## Layout do Supermercado

[Layout do Supermercado](image/layout_supermercado.md)

Essa modelagem ajudará a identificar eventos de domínio, problemas, riscos e oportunidades de melhoria, fornecendo uma base sólida para que o novo software seja alinhado às necessidades reais do supermercado.

---

# 🟧 **Workshop Completo – Event Storming Big Picture (50 minutos)**

### **Modelagem do Domínio para Sistema de Gestão de Supermercado**

## 🎯 **Objetivo Geral**

Mapear o fluxo de valor do supermercado (vendas, compras, estoques e informações gerenciais) usando Event Storming Big Picture, identificando **Eventos de Domínio**, **Atores**, **Sistemas Externos** e **Hotspots**, para que o novo software reflita a operação real do supermercado.

---

# ⏱️ **Agenda de 50 Minutos (Estruturada e Prática)**

---

## **0 – 5 min | Abertura e Alinhamento**

### 🎙️ *Atividades*

* Apresentação do facilitador e dos objetivos do workshop.
* Explicação do propósito: compreender o funcionamento real do supermercado antes de desenvolver o software.
* Regras básicas da técnica:

  * Post-it **laranja** = Evento de Domínio.
  * Post-it **azul** = Atores / Sistemas.
  * Post-it **vermelho/rosa** = Hotspots (problemas, dúvidas, riscos).
  * Todos participam, ninguém discute agora.

### 🎯 *Resultados esperados*

* Participantes entendem o objetivo e a dinâmica.
* Todos sabem como contribuir.

---

## **5 – 10 min | Aquecimento (Warm-up)**

### 🎙️ *Atividades*

* Pergunta rápida ao grupo:
  **“Qual é a atividade mais importante do seu setor que não pode falhar?”**
* Responder em post-its (qualquer cor), sem ordem.
* Expor na parede para criar engajamento.

### 🎯 *Resultado*

* Quebra-gelo.
* Participantes começam a pensar em fluxo de valor.

---

## **10 – 20 min | Exploração Caótica (Geração de Eventos)**

### 🎙️ *Atividades*

* Cada participante escreve **eventos importantes do seu setor** em post-its laranjas.
* Todos postam **sem ordem** na parede.
* Exemplos sugeridos pelo facilitador:

  * *Produto Recebido no Depósito*
  * *Preço Atualizado na Gôndola*
  * *Item Selecionado pelo Cliente*
  * *Produto Pesado no Hortifrúti*
  * *Item Registrado no Caixa*
  * *Pagamento Aprovado*
  * *Estoque Mínimo Atingido*

### 🎯 *Resultado*

* Grande volume de eventos reais do dia a dia.
* Visão ampla de como o supermercado funciona.

---

## **20 – 30 min | Organização em Linha do Tempo**

### 🎙️ *Atividades*

* O grupo reorganiza todos os eventos **cronologicamente**, da esquerda (início do processo) para a direita (final).
* O facilitador ajuda perguntando:

  * “O que acontece antes disso?”
  * “O que depende desse evento?”
* Remover duplicações.
* Criar um esboço do fluxo:
  **Compras → Recebimento → Armazenagem → Reposição → Cliente Escolhe → Checkout → Pagamento**

### 🎯 *Resultado*

* Linha do tempo consistente representando o fluxo de valor do supermercado.

---

## **30 – 35 min | Identificação dos Atores e Sistemas**

### 🎙️ *Atividades*

* Participantes criam post-its **azuis** indicando:

  * Pessoas (Açougueiro, Repositor, Gerente de Estoque, Cliente, Caixa…)
  * Sistemas (API de Pagamento, Sistema do Fornecedor, Balança do Hortifrúti…)
* Posicionar ao redor dos eventos que eles influenciam.

### 🎯 *Resultado*

* Clareza sobre quem faz o quê.
* Integração entre setores fica visível.

---

## **35 – 40 min | Storytelling do Fluxo Completo**

### 🎙️ *Atividades*

* Um voluntário percorre a linha do tempo explicando o fluxo.
* Facilitador incentiva perguntas:

  * “Isso sempre acontece assim?”
  * “O que dá errado aqui?”
  * “E quando falta produto?”
* O processo ganha validação colaborativa.

### 🎯 *Resultado*

* Refinamento da linha do tempo.
* Compreensão compartilhada do processo completo.

---

## **40 – 45 min | Identificação de Hotspots (Problemas)**

### 🎙️ *Atividades*

* Participantes marcam eventos críticos com post-its vermelhos.
* Tipos de hotspots a considerar:

  * Falhas (ex: *Preço divergente no caixa*)
  * Incertezas (ex: *Validade do produto não registrada*)
  * Riscos (ex: *API de fornecedor lenta*)
  * Ambiguidades (ex: *Quem decide o preço final?*)

### 🎯 *Resultado*

* Mapa visual com pontos sensíveis para o software resolver.

---

## **45 – 50 min | Priorização e Encerramento**

### 🎙️ *Atividades*

* Votação rápida para escolher os **3 hotspots mais importantes**.
* Facilitador conclui com:

  1. O que foi aprendido.
  2. Próximos passos:

     * Digitalizar o mapa.
     * Preparar workshop de detalhamento (Event Storming de Processo).
     * Definir possíveis **Contextos Delimitados** (Vendas, Compras, Estoque…).

### 🎯 *Resultado*

* Entendimento claro do que deve ser resolvido primeiro.
* Entregável concreto para a equipe de desenvolvimento.

---

# 📌 **Saída Final do Workshop**

* Linha do tempo completa do fluxo do supermercado.
* Lista de eventos de domínio.
* Identificação dos atores e sistemas externos.
* Hotspots priorizados.
* Base inicial para definir contextos delimitados (módulos do software).


[Painel Ilustrativo do Event Storming Big Picture](./Painel_supermercado.md)

---

# 🛒 **Exemplos de Eventos por Área (para facilitar o workshop)**

### **📍 Compras**

* Pedido de Compra Emitido
* Cotação Recebida
* Mercadoria Despachada pelo Fornecedor

### **📍 Recebimento / Depósito**

* Caminhão Chegou
* Nota Fiscal Validada
* Produto Conferido
* Produto Armazenado

### **📍 Loja / Gôndolas**

* Produto Reposto
* Estoque Mínimo Atingido
* Produto Vencido

### **📍 Cliente**

* Cliente Procurou Setor
* Item Selecionado
* Item Colocado no Carrinho

### **📍 Checkout / Vendas**

* Item Registrado
* Desconto Aplicado
* Pagamento Aprovado
* Venda Finalizada

---


