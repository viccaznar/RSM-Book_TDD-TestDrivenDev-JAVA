# 🤝 Capítulo 1.4.2: Colaboração Próxima — Acceptance TDD

## 📝 Tradução do Texto

A colaboração próxima é essencial em qualquer empreendimento complexo com pessoas, e o desenvolvimento de software com acceptance TDD não é exceção. Na prática, queremos um time integrado, em vez de equipes separadas de desenvolvimento, análise de negócio e teste — sem falar em um departamento de QA distante.

A ideia fundamental é que a melhor produtividade surge ao fomentar feedback rápido e comunicação face a face em torno de software funcionando e concreto, em vez de trocar planos de teste, especificações e relatórios de bugs entre cliente, testadores, analistas de negócio e desenvolvedores. Com acceptance TDD, colaboramos efetivamente reunindo conhecimentos e habilidades necessárias para fazer um trabalho de qualidade.

### Ver Software Funcional na Prática 👀

Muito poucos clientes ficam satisfeitos após meses de silêncio. Ao entregar funcionalidades concluídas continuamente, descobrimos imediatamente se algo está errado ou falta. Esse feedback precoce reduz riscos e custos. Sem manter um estoque de itens “supostamente concluídos” que o cliente não viu, evitamos a ilusão de progresso apoiada em métodos documentais e frases vazias como “90% pronto”.

### Construir Confiança e Segurança 🔨

Outro benefício de entregar software funcionando cedo e com frequência é ganhar confiança — tanto do cliente quanto dentro da equipe. Mostrar, a cada iteração, que podemos cumprir promessas torna a vida mais fácil para todos no projeto.

### Cliente no Comando 🎛️

Na abordagem incremental, o cliente decide quais funcionalidades vêm primeiro e quais podem ser deixadas de fora, caso o tempo ou orçamento acabem. As escolhas do cliente consideram custo de cada feature, custo de adiar ou de mudar a ordem de implementação. Essa capacidade de direcionar investimentos faz o cliente se sentir realmente no controle do projeto.

### Evolução de uma Linguagem Compartilhada 🗣️

Ao promover colaboração estreita entre testadores, desenvolvedores e clientes, garantimos que a informação fluísse rápido em todas as direções. Com o convívio diário, evolui-se uma linguagem comum baseada em testes de aceitação, facilitando entendimento e reduzindo mal-entendidos. Afinal, desenvolvimento de software é um negócio de pessoas.

---

## 🧠 Raciocínio Contido no Texto

- Integração de perfis (cliente, dev, teste) gera comunicação direta e ágil.  
- Entregar software funcional cedo fornece feedback imediato, reduzindo riscos.  
- Demonstrações frequentes constroem confiança e transparência.  
- Cliente toma decisões de prioridade com base em valor e custo real.  
- Testes de aceitação servem de base para um vocabulário comum, alinhando expectativas.

---

## 📚 Conceitos Explicativos

### 👥 Colaboração Próxima

- Equipes multifuncionais trabalham lado a lado.  
- Troca de conhecimento em tempo real.

**Exemplo Lúdico:** Imagine um **quarteto de jazz**: músico, compositor, técnico de som e público improvisam juntos. Se alguém errar a nota, o outro ajusta na hora, criando harmonia instantânea.

---

### 👀 Feedback com Software Real

- Entregas contínuas mostram funcionalidades funcionando.  
- Detectar falhas no instante em que surgem.

**Exemplo Lúdico:** É como um **chefe de cozinha** que prova cada garfada no momento em que o prato sai da frigideira, ajustando temperos antes de servir ao cliente.

---

### 🔨 Construir Confiança

- Demonstrações frequentes validam progresso.  
- Transparência gera segurança mútua.

**Exemplo Lúdico:** Pense num **escoteiro** mostrando a barraca montada passo a passo ao monitor. Cada estaca fincada aprovada fortalece a confiança de que o acampamento vai ficar firme.

---

### 🎛️ Cliente no Comando

- Cliente escolhe prioridades conforme valor e custo.  
- Permite ajustes de escopo sem surpresas.

**Exemplo Lúdico:** É como um **capitão de navio** que define qual porto visitar primeiro. Se o tempo apertar, ele decide pular o segundo destino e seguir direto ao último.

---

### 🗣️ Linguagem Compartilhada

- Testes de aceitação viram “dicionário” comum.  
- Facilita entendimento entre todos os envolvidos.

**Exemplo Lúdico:** Imagine um **cartógrafo** que desenha um mapa colaborativo com clientes e guias locais. Cada símbolo aprovado vira parte do mapa oficial, evitando confusões sobre o terreno.

---

## 🛠️ Capítulo 2: Boas Práticas & Cenários Reais 🌟

### ✅ Boas Práticas

- Formule testes de aceitação em **linguagem de negócio** clara.  
- Agende **demos diárias** ou semanais para validar funcionalidades.  
- Mantenha **feedback loops curtos**: cliente e time side by side.  
- Use testes de aceitação como **contrato vivo**: atualize quando requisitos mudarem.  
- Combine acceptance TDD com TDD de unidade para **sinergia** de qualidade.

### 🌍 Cenários Reais

- Em e-commerce, o cliente revisa na hora o fluxo de checkout e libera ajustes imediatos.  
- Em fintech, simulações de empréstimos são apresentadas para aprovação antes da liberação.  
- Em SaaS B2B, o cliente valida cada relatório customizado assim que está gerado.  
- Em IoT, o time e o usuário testam juntos a interface do painel de controle em tempo real.

---

## 📝 Exercícios de Fixação

1. Em até três linhas, explique por que entregar software funcional cedo melhora a colaboração.  

2. Cite dois ganhos de ter o cliente no controle das prioridades.

3. Sugira um teste de aceitação (em linguagem natural) para o fluxo de “adicionar um produto ao carrinho”.

---

## 💡 Soluções

1. Entregar software funcional cedo fornece um ponto de conversa concreto, reduz mal-entendidos e gera feedback imediato para correções rápidas.  

2.  
   - Permite o cliente ajustar escopo conforme valor percebido.  
   - Evita desperdício de tempo e recursos em funcionalidades de baixo impacto.  

3. Cenário de aceitação “Adicionar Produto ao Carrinho”:  
    Dado que o produto “Caneca Azul” está disponível em estoque Quando o usuário clicar em “Adicionar ao Carrinho” Então o carrinho deve conter a “Caneca Azul” com quantidade 1 E o total da compra deve ser atualizado corretamente