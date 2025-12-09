## EVENT STORMING BIG PICTURE

O Event Storming Big Picture (BPE) é o nível de abstração mais alto do Event Storming, projetado para explorar todo um domínio de negócio de forma colaborativa e rápida,.

As etapas do processo de Event Storming Big Picture são divididas em fases de preparação, execução e conclusão, visando à descoberta rápida e à construção de um entendimento compartilhado,.

### I. Fases de Preparação e Kick-Off

Antes de iniciar a sessão de modelagem, é essencial alinhar o escopo e preparar o ambiente para a colaboração,.

1.  **Preparação da Sala e Logística:** O facilitador deve remover cadeiras e mesas e preparar uma **superfície de modelagem ampla**, tipicamente com pelo menos 8 metros de papel ou plástico na parede,.
2.  **Energização e Briefing:** O workshop começa com uma introdução dos participantes (que devem incluir especialistas de domínio e desenvolvedores) e, opcionalmente, um **exercício físico coletivo** para aumentar o engajamento,,.
3.  **Apresentação da Agenda:** O facilitador apresenta o objetivo e o escopo do workshop e introduz a notação básica, como os **Eventos de Domínio** (post-its cor laranja),.

### II. Fases de Execução e Modelagem

As fases centrais do BPE focam na transição do caos (divergência de ideias) para a estrutura (convergência de um modelo).

1.  **Geração de Eventos de Domínio (Exploração Caótica):** Os participantes escrevem simultaneamente o máximo de **Eventos de Domínio** (fatos relevantes expressos no passado) que conseguirem imaginar, colando-os na superfície de modelagem sem preocupação inicial com a ordem ou a estrutura,,. Esta fase é propositalmente caótica e cronometrada (cerca de 25 a 30 minutos),.
2.  **Ordenação Cronológica (Enforce the Timeline):** A equipe colabora para organizar todos os Eventos de Domínio em uma **linha do tempo consistente**, dispostos horizontalmente da esquerda (início do processo) para a direita (fim),,. Durante este processo, duplicatas são removidas e lacunas ou eventos ausentes são adicionados,,. A ordenação pode ser guiada por **Eventos Pivôs** ou **Swimlanes** (raias verticais) para clarear atividades paralelas.
3.  **Adição de Atores e Sistemas Externos:** O modelo é enriquecido com notas para identificar **Atores/Funções** (quem inicia ou participa) e **Sistemas Externos** (dependências como APIs de pagamento ou serviços de terceiros),,.
4.  **Storytelling (Narrativa Explícita):** Voluntários narram o processo completo, percorrendo a linha do tempo cronologicamente. A audiência deve **desafiar incoerências** e levantar perguntas,.
5.  **Reverse Storytelling (Narrativa Reversa):** Uma etapa opcional, mas valiosa, onde o processo é narrado **de trás para frente** (do evento final para o inicial) para expor dependências e pré-condições que foram negligenciadas,.
6.  **Identificação de Hotspots e Oportunidades:** Problemas, ambiguidades, conflitos ou riscos (os **Hotspots**) são visualmente marcados (geralmente com post-its de cor rosa ou vermelha),. Ideias para melhoria (Oportunidades) também podem ser adicionadas,.

### III. Conclusão e Próximos Passos

1.  **Votação e Priorização:** O grupo pode usar votação (e.g., com flechas) para identificar os **problemas mais urgentes** ou as oportunidades que merecem foco imediato.
2.  **Agrupamento e Resultados Estratégicos:** Clusters de eventos são analisados para identificar as fronteiras lógicas do domínio, o que leva ao desenho dos **Contextos Delimitados** (Bounded Contexts),. Este mapeamento é fundamental para definir a arquitetura funcional.
3.  **Fechamento:** O workshop é encerrado com uma avaliação (retrospectiva) da sessão e a definição de responsáveis e planos para os próximos passos,.