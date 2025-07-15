# 🌱 Capítulo 1.4: Desenvolvendo em Pequenos Incrementos 🚀

## 📝 Tradução do Texto

Desenvolver em pequenos incrementos  
Um princípio comum dos métodos ágeis sugere produzir um produto potencialmente implantável o mais cedo possível — independentemente de quão poucas funcionalidades ele tenha — e continuar gerando essas versões implantáveis diariamente (alguns projetos relatam montar um pacote de release várias vezes ao dia) até o projeto ser concluído. Essa prática garante que, quando o prazo chegar, você tenha algo para entregar e que funcione. Talvez não tenha todas as funcionalidades que o cliente pediu, e talvez não cumpra todo o plano de iteração, mas pelo menos você tem algo — e algo que funciona.

A Figura 1.6 mostra a progressão incremental de funcionalidades testadas e funcionando, onde o inventário de trabalho não integrado e inacabado é muito pequeno a qualquer momento.

Muitos projetos adiam seus prazos repetidamente, acabam cancelados e não entregam uma única linha de código funcional. Ao construir seu produto em pequenos incrementos, iteração após iteração, você não precisa se preocupar em não cumprir o prazo, pois já conta com um sistema funcional (ainda que não completo) desde a primeira iteração. Da mesma forma, muitos projetos entregam código cheio de bugs devido ao aperto de última hora para cumprir o prazo.

O TDD elimina esse problema ao seguir em pequenos passos, cada um resultando em um produto funcional e mais próximo do comportamento desejado. Como esses passos são tão curtos (medidos em minutos, não em horas ou dias), não acabamos com um monte de código solto para juntar às pressas. Mantemos o software funcionando ao não deixá-lo se afastar demais desse estado. Da mesma forma, mantemos o software enxuto ao projetar para o momento presente em vez de olhar muito à frente.

---

Construir software em incrementos — especialmente ditados pelo custo-benefício percebido de funcionalidades de negócio — não é possível com a abordagem tradicional de “projetar tudo de antemão, considerando todas as possíveis variações, para que a arquitetura seja inabalável e suporte todas as funcionalidades”. Não conseguimos construir a arquitetura perfeita do produto final em uma única vez. Apenas projetos muito simples ou bem compreendidos permitem acertar a arquitetura logo no início.

Precisamos iterar, adicionando à nossa arquitetura um pequeno passo de cada vez. A Figura 1.7 mostra como esse processo iterativo e incremental oscila entre o pequeno passo de adicionar funcionalidade e o ajuste do design — e da arquitetura — para acomodar adequadamente essa funcionalidade.

Isso é design incremental e evolutivo. Em vez de projetar o máximo que conseguirmos de antemão, projetamos o necessário para avançar. Em vez de analisar exaustivamente todos os cenários antes de finalizar o design, optamos por tomar decisões baseadas em conhecimento — não em suposições — obtido durante a implementação.

O grau de design inicial necessário antes de mergulhar na implementação de uma funcionalidade varia de situação para situação, entre equipes, indivíduos e tecnologias. O importante é observar se você está indo na direção certa. Parte do seu design não funcionou? Reduza o design antecipado. O design não escalou o suficiente? Aumente o nível de design inicial.

---

Pequeno o suficiente para caber em nossas cabeças  
A lógica de dividir um objetivo maior em pequenos testes é dupla. Primeiro, muitas tarefas no campo são grandes, ambíguas ou complexas demais para serem gerenciáveis. Assim, precisamos fragmentá-las em partes menores para que caibam em nossas cabeças. Não sei a sua, mas a minha mente não lida bem com esses monstros, e já ouvi outros dizerem o mesmo (espero que não estivessem apenas sendo educados). A Figura 1.8 mostra como um problema complexo pode ser simplificado em problemas menores, mais simples, para serem resolvidos um de cada vez.

Vamos encarar: a maioria das pessoas consegue lidar com até cinco ou sete conceitos simultaneamente na memória de trabalho. Sobrecarregar seu cérebro além desse limite causa confusão e atrasos.

---

## 🧠 Raciocínio Contido no Texto

- Entregar **versões implantáveis** cedo e com frequência reduz riscos de não cumprir prazos e evita acúmulo de código quebrado.  
- **Design incremental e evolutivo** permite ajustar arquitetura com base em conhecimento real, e não em suposições.  
- Dividir grandes tarefas em **pequenos passos** torna os objetivos gerenciáveis e evita sobrecarga cognitiva.  
- Manter um **estoque mínimo de trabalho não integrado** diminui o inventário de pendências e aumenta a previsibilidade.  
- Focar no **momento presente** evita over-engineering e usabilidade futura não necessária.

---

## 📚 Conceitos Fundamentais

### 🍰 1. Versões Implantáveis Diárias

- Gere builds diários ou frequentes com funcionalidades mínimas.  
- Garante sempre ter algo funcional para entregar.


  - **Exemplo Lúdico:** Pense numa **padaria** que, em vez de esperar o pão especial ficar pronto em uma semana, entrega mini-pães todos os dias. Se a fornada falhar, o padeiro ajusta a receita na hora — nunca fica sem produto.

---

### 📦 2. Estoque Mínimo de Trabalho Não Integrado

- Mantenha o backlog de código inacabado e não integrado sempre pequeno.  
- Reduz riscos de conflitos e retrabalho.


  - **Exemplo Lúdico:** Imagine um **mercado** que repõe suas prateleiras várias vezes ao dia, em vez de estocar tudo de uma vez. O corredor nunca fica vazio nem abarrotado, facilitando a visualização e o reabastecimento.

---

### 🏗️ 3. Design Incremental e Evolutivo

- Adicione pequenas funcionalidades e depois ajuste o design para acomodá-las.  
- Evolua a arquitetura passo a passo, validando cada mudança.


  - **Exemplo Lúdico:** Construa um **castelo de areia** adicionando um balde de terra de cada vez e ajustando a forma conforme o vento e as marés. Você aprende na prática o que funciona melhor.

---

### 🔍 4. Decisões Baseadas em Conhecimento

- Tome decisões de design com base no que você já implementou e testou.  
- Evite especulações: só planeje o que é necessário agora.


  - **Exemplo Lúdico:** É como preparar uma **receita de sopa**: você prova a cada adição de tempero em vez de jogar todos os ingredientes de uma vez. Ajusta o sal conforme o paladar — não antes de cozinhar tudo.

---

### 🧩 5. Pequenos Passos, Grandes Conquistas

- Divida problemas complexos em tarefas que levem minutos, não dias.  
- Facilita o foco mental e acelera o feedback.


  - **Exemplo Lúdico:** Imagine resolver um **quebra-cabeça** gigantesco: você separa as peças por cor e monta pequenos grupos antes de juntar tudo. Cada mini-puzzle concluído dá motivação para seguir em frente.

---

## 🛠️ Capítulo 2: Boas Práticas & Cenários Reais 🏭

### ✅ Boas Práticas

- Defina **itens de trabalho** curtos e priorizados por valor de negócio.  
- Planeje **iterações diárias ou semanais** com entregas mínimas mas funcionais.  
- Use **CI/CD** para validar cada incremento automaticamente.  
- Revise o **design** a cada entrega para corrigir rumos rápidos.  
- Mantenha um **backlog** de ideias extras para não sobrecarregar o código atual.  
- Envolva **stakeholders** em demos frequentes para ajustar expectativas.

---

## 📝 Exercícios de Fixação

1. Explique em até três linhas como versões implantáveis diárias reduzem riscos.  
2. Cite dois benefícios do design incremental e evolutivo.  
3. Divida a funcionalidade “carrinho de compras” em três incrementos gerenciáveis.

---

## 🏆 Soluções

1. Builds frequentes permitem mostrar software funcional desde cedo, detectar falhas rapidamente e evitar acúmulo de código quebrado antes do prazo.  


2. Benefícios:  
   - Arquitetura adaptada ao que foi testado e implementado, não a suposições.  
   - Risco menor de over-engineering e retrabalho, pois cada ajuste é validado logo após entrar no sistema.  


3. Incrementos para “carrinho de compras”:  
   - Incremento 1: adicionar itens e calcular total.  
     - Incremento 2: persistir carrinho no servidor e recarregar sessão.  
       - Incremento 3: aplicar cupom de desconto e exibir subtotal atualizado.  
