# Roteiro Completo — Event Storming Big Picture (Domínio: Supermercado)

> Documento: roteiro prático, didático e orientado a ação para conduzir um Event Storming Big Picture aplicado a um supermercado. Use este roteiro como guia passo-a-passo, checklist e artefato para capturar os resultados do workshop.

---

## Sumário rápido

1. Objetivo do Workshop
2. Preparação (material, espaço, participantes)
3. Notação e cores (legend)
4. Agenda detalhada (tempo, atividades, transcripts)
5. Passo-a-passo do Event Storming (fases e como conduzir)
6. Identificação de Eventos Pivô e delimitação de contextos
7. Swimlanes (como organizar por setor)
8. Elementos adicionais: Comandos, Regras, Agregados, Políticas, Sistemas
9. Hot Spots e técnicas de priorização
10. Storytelling e Reverse Storytelling
11. Entregáveis ao final do workshop
12. Próximos passos técnicos (DDD, Context Mapping, arquiteturas)
13. Dicas do facilitador e armadilhas comuns

---

## 1 — Objetivo

Modelar, em colaboração com especialistas das áreas (vendas, compras, estoques, gerência, fornecedores), o fluxo de valor principal do supermercado para garantir: disponibilidade de produtos, controle de validade e fluxo de informações consistente — antes de iniciar a implementação do sistema de gestão.

## 2 — Preparação

**Participantes recomendados**
- Diretor de TI (sponsor)
- Facilitador(s) de Event Storming (1 principal + 1 assistente)
- Representantes de Vendas (caixa, front-store)
- Representantes de Compras
- Representantes de Estoque/Logística
- Representante(s) Gerencial/BI/Financeiro
- 1-2 pessoas de TI/arquitetura
- Opcional: fornecedor-chave, parceiro logístico

**Espaço & Materiais**
- Parede grande com rolo de papel kraft (linha do tempo)
- Post‑its: Laranja, Amarelo, Azul, Roxo/Pink, Verde, Cinza
- Fitas adesivas, canetas grossas, barbante
- Adesivos para votação (5 por participante)
- Câmera/telefone para fotografar o quadro no final

**Configuração da sala**
- Remover cadeiras (colaboração em pé)
- Desenhar uma linha do tempo da esquerda para a direita
- Preparar 4–6 raias horizontais (Vendas, Compras, Estoques, Gerencial, Fornecedores, Sistemas)

## 3 — Notação & cores (legend)

- **Eventos de Domínio — Laranja** (verbos no passado: "Venda Registrada")
- **Atores / Pessoas — Amarelo** (ex: "Operador de Caixa", "Cliente")
- **Comandos — Azul** (ações executadas: "Emitir Pedido de Compra")
- **Sistemas Externos / Legados — Salmão/Rosa** (ex: "Fornecedor", "ERP Legado")
- **Hot Spots / Problemas — Roxo/Vermelho** (onde existe incerteza/gargalo)
- **Políticas/Regras de Negócio — Cinza/Tan** (ex: prazo de validade mínimo aceito)
- **Informações / Documentos — Verde** (ex: Nota Fiscal Recebida)

> Dica: mantenha os eventos em verbos no passado — ajuda a tornar as consequências explícitas.

## 4 — Agenda detalhada (exemplo 90 minutos)

- 00:00–00:10 — Kick‑off: objetivo, escopo e regras de colaboração
- 00:10–00:30 — Exploração Caótica (geração massiva de eventos — post‑its laranja)
- 00:30–00:50 — Ordenação cronológica (colocar eventos da esquerda para a direita)
- 00:50–01:10 — Inserir atores, sistemas, comandos, regras; identificar Hot Spots
- 01:10–01:25 — Identificação de Eventos Pivô / delimitação de contextos
- 01:25–01:40 — Storytelling (narrativa) e Reverse Storytelling
- 01:40–01:50 — Votação de prioridades, captura de entregáveis e fechamento

> Se houver tempo: separação em sub‑workshops para aprofundar pivôs selecionados.

## 5 — Passo-a-passo prático (fases)

### Fase A — Exploração caótica
- Peça a todos escreverem eventos em LARANJA — sem discutir.
- Meta: muitos eventos (≥50) — quantidade expõe detalhes e exceções.

### Fase B — Ordenar cronologicamente
- Agrupe e mova eventos para formar uma linha lógica.
- Use setas para indicar dependências e sequência.

### Fase C — Enriquecer com atores, comandos, sistemas, regras
- Coloque ATORES (amarelo) próximos aos eventos onde atuam.
- Adicione COMANDOS (azul) que causaram eventos.
- Coloque sistemas externos (rosa) que interagem.
- Adicione regras/validações (cinza), por exemplo: "Prazo mínimo de validade = 15 dias".

### Fase D — Identificar Hot Spots e dúvidas
- Use roxo para marcar incertezas, riscos de negócio, exceções frequentes.
- Faça 1–2 rodadas de perguntas rápidas para explicar cada Hot Spot.

### Fase E — Selecionar Eventos Pivô
- Vote (pontos) nos eventos mais importantes. Escolha 3–6 pivôs.
- Exemplos práticos: "Pedido de Compra Emitido", "Produto Recebido e Aceito no Estoque", "Venda Registrada na Loja", "Produto Vencido Identificado".

## 6 — Eventos Pivô e delimitação de Contextos

**Como escolher**
- Evento que marca transição entre responsabilidades.
- Evento que envolve integração com sistemas externos.

**Exemplos (supermercado)**
- **Pedido de Compra Emitido** — fronteira entre Compras e Fornecedores (pode mapear contexto "Compras/Procurement").
- **Produto Recebido e Aceito no Estoque** — delimita "Logística/Recebimento" vs "Gestão de Estoque".
- **Produto Disponibilizado para Venda** — fronteira entre Estoque e Vendas.
- **Venda Registrada** — delimita contexto de "Ponto de Venda (POS)".

**Resultado esperado**
- Uma sugestão inicial de Bounded Contexts para DDD, alinhada aos pivôs.

## 7 — Swimlanes / Raia horizontal (organização por setor)

Crie raias para: Vendas, Compras, Estoques, Gerência, Fornecedores e Sistemas. Coloque eventos e atores na raia apropriada. Use isso para identificar handoffs: por exemplo, evento "Estoque Baixo Detectado" (Vendas) → "Pedido de Reposição Gerado" (Compras).

## 8 — Elementos adicionais e como registrá-los

- **Comandos (Azul):** escreva quem emitiu. Relacione com setas até o evento resultante.
- **Regras/Políticas (Cinza):** capture restrições. Ex.: política de validade, lote mínimo, lead time padrão.
- **Documentos/Informaçõs (Verde):** Nota Fiscal, Romaneio, Etiqueta de Validade.
- **Agregados / Entidades (post-it branco opcional):** quando já for claro, marque itens importantes (Produto, Lote, Fornecedor).

## 9 — Hot Spots e priorização

- Cada participante tem 5 adesivos para votar nos Hot Spots mais críticos.
- Ordene por votos — esses itens viram ações ou spikes técnicos.
- Para cada Hot Spot de topo, defina um responsável e um prazo de investigação (ação pós‑workshop).

## 10 — Storytelling e Reverse Storytelling

- Peça 2 voluntários para narrar a história inteira (ida e volta). Interrompa para corrigir termos e registrar linguagem ubíqua.
- Use o Reverse Storytelling para explodir requisitos atrás de um evento pivô ("O que precisava acontecer para que ‘Produto Disponibilizado para Venda’ ocorresse?").

## 11 — Entregáveis (ao final do workshop)

1. Foto(s) do quadro (alta resolução).
2. Lista de Eventos (ordenada cronologicamente).
3. Glossário / Linguagem Ubíqua (termos e definições).
4. Hot Spots priorizados com responsáveis.
5. Proposta inicial de Bounded Contexts e pontos de integração.
6. Backlog sugerido para spikes (investigações técnicas) e histórias de usuário.

## 12 — Próximos passos (técnico)

- Conduzir Event Storming de nível Projeto para cada Event Pivô selecionado — explorar fluxos detalhados, comandos, políticas e modelos de dados.
- Criar Context Map (mapa de integrações entre bounded contexts).
- Prototipar contratos de integração (events/messages) entre contextos.
- Preparar backlog para MVP (por exemplo: MVP POS + Estoque mínimo + Recebimento)

## 13 — Dicas do Facilitador & armadilhas

**Dicas**
- Promova escrita em silêncio na fase inicial (evita discussão prematura).
- Fotografe etapas importantes (antes/ depois da ordenação).
- Mantenha foco no fluxo de valor — não mergulhe cedo em UI/UX.
- Use tempo-box para cada etapa.

**Armadilhas**
- Permitir que 1 pessoa domine a conversa.
- Debater soluções técnicas na fase de exploração (planeje spikes para isso).
- Tentar cobrir todo o supermercado em um único workshop muito curto — prefira focar nos pivôs.

---

## Exemplo resumido de fluxo (ilustrativo)

1. **Estoque Baixo Detectado** (Evento) — Sistema de Estoque monitora vendas.
2. **Sinal de Reposição Emitido** (Comando) — Gerado por regra de reorder point.
3. **Pedido de Compra Emitido** (Evento Pivô) — Compras envia ao Fornecedor.
4. **Nota Fiscal Recebida** (Documento) — Fornecedor envia.
5. **Produto Recebido e Validado** (Evento Pivô) — Validade e Lote verificados.
6. **Produto Armazenado** (Evento) — Quantidade atualizada.
7. **Produto Disponibilizado para Venda** (Evento Pivô) — Prateleira abastecida.
8. **Venda Registrada** (Evento Pivô) — POS registra venda, decrementa estoque.
9. **Relatório Gerencial Atualizado** (Evento) — Métricas de disponibilidade e perda por validade.

---

## Observação sobre este roteiro

Este roteiro foi elaborado para ser operacional e adaptável: use como baseline e ajuste tempos, participantes e nível de detalhe conforme a maturidade do domínio e disponibilidade da equipe.

---

*Fim do roteiro.*

