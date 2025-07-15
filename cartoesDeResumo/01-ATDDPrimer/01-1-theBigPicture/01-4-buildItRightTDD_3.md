# 📚 Capítulo 1.5: Desenvolvimento Evolutivo 🌱

## 📝 Tradução do Texto

A capacidade de nossa memória de trabalho é limitada e forçar dados entre ela e a memória de longo prazo (ou documentos escritos) tende a fazer com que algo seja esquecido. Ter uma sequência de passos pequenos rumo ao objetivo final nos permite medir o progresso de forma concreta, pois sabemos quando cada um desses passos é concluído — graças aos testes que dividem a tarefa em etapas mensuráveis.

O TDD incentiva naturalmente esses pequenos passos, promovendo design evolutivo. Estamos sempre aprimorando e ajustando o design em incrementos sutis. Na prática, construímos parte da arquitetura conforme avançamos — basta considerar isso ao estimar o trabalho.

### Design Evolutivo

Muitos programadores já viram aquele trecho de código que “grita” por melhorias, mas acaba intocado porque faz parte da interface entre dois componentes e é difícil de mudar. Design evolutivo é a mentalidade de cuidar desse código vivo, em vez de protegê-lo do “mundo cruel”, melhorando nossa arquitetura e, por consequência, a qualidade de todo o sistema.

Funciona em passos pequenos: só implementamos a arquitetura que sabemos ser necessária. Se, por exemplo, precisarmos de um servidor de e-mail, adicionamos justo o suficiente para fazê-lo funcionar. Normalmente, esse tipo de mudança arquitetural “just in time” é tranquila, mas algumas demandas — como transformar um app desktop mono-usuário em um cliente-servidor multi-usuário — podem exigir esforço significativo.

### Antecipado vs. Inesperado

Nem toda mudança antecipada acontece, e mudanças não previstas surgem conforme revelamos incógnitas. A Figura 1.9 mostra que o design emergente é influenciado tanto por mudanças previstas quanto pelas surpresas que descobrimos. Devemos usar bom senso e julgar o quanto de design antecipado vale a pena, equilibrando trabalho desnecessário e atalhos que podem nos prejudicar depois.

### Disciplina e Refatoração

Design evolutivo exige muitas mudanças constantes no código existente. Não podemos permitir que o código apodreça. Por isso, precisamos de disciplina para manter o software saudável — e a refatoração contínua é a prática central para isso. Sem refatorar, teríamos código funcional, mas feio e difícil de evoluir.

---

## 🧠 Raciocínio Contido no Texto

- A memória de trabalho humana é limitada; dividir tarefas em pequenos testes torna-as gerenciáveis.  
- TDD promove design evolutivo por incrementos, mantendo o sistema sempre funcional.  
- Devemos implementar arquitetura “just in time” com base no que sabemos, mas sem ignorar mudanças futuras.  
- Antecipar mudanças é útil, mas nem todas se concretizam; surpresas exigem ajustes ágeis.  
- Disciplina e refatoração contínua são essenciais para evitar degradação do código (“code rot”).

---

## 📚 Conceitos Explicativos

### 🧩 1. Passos Pequenos e Memória Limitada

- Divida tarefas grandes em testes curtos que cabem na mente.  
- Testes confirmam quando cada pedaço está pronto.

  - **Exemplo Lúdico:** É como desbravar um labirinto apagado com pedaços de giz: você marca um pouco de cada vez e confirma o caminho antes de avançar, em vez de tentar decorar o trajeto de uma vez só.

---

### 🔄 2. Design Evolutivo em Incrementos

- Implemente somente o que é necessário agora.  
- Ajuste a arquitetura conforme cada funcionalidade entra no sistema.

  - **Exemplo Lúdico:** Imagine construir um **castelo de areia** adicionando baldes de areia por vez e moldando as torres conforme aprende a hora certa de reforçar as paredes.

---

### 🎯 3. Antecipação vs. Mudança Inesperada

- Identifique mudanças previsíveis e prepare-se “just in time”.  
- Aja com bom senso: evite over-engineering e atalhos perigosos.

  - **Exemplo Lúdico:** É como planejar um piquenique: você leva uma tenda extra “caso chova” (antecipado), mas não carrega um kit de primeira ajuda de dez quilos “só para o caso” — demais não ajuda, e de menos pode custar caro.

---

### 💼 4. Trade-Off Entre Planejamento e Flexibilidade

- Equilibre esforço de design antecipado e trabalho emergente.  
- Ajuste o grau de planejamento conforme novas informações surgem.

  - **Exemplo Lúdico:** Pense num **capitão de navio** que traça a rota conforme o clima muda: às vezes planeja com horas de antecedência, às vezes desvia na hora por causa de nevoeiro inesperado.

---

### 🛡️ 5. Disciplina e Refatoração Contínua

- Refatore sempre que o código apresentar duplicações ou complexidade desnecessária.  
- Refatoração mantém o código saudável e pronto para mudanças.

  - **Exemplo Lúdico:** É como manter um **jardim**: você poda galhos mortos assim que aparecem, em vez de esperar que a planta fique doente, garantindo flores saudáveis o ano inteiro.

---

## 🛠️ Capítulo 2: Boas Práticas & Cenários Reais 📈

### ✅ Boas Práticas

- **Teste em pequenos passos**: crie um teste, faça-o passar, depois refatore.  
- **Implementação just-in-time**: adicione apenas a arquitetura necessária para o teste atual.  
- **Revisão contínua de design**: use sessões rápidas de refatoração após cada incremento.  
- **Backlog de ideias**: documente possíveis melhorias, mas só implemente quando necessário.  
- **Disciplina de testes e refatoração**: incorpore esses hábitos no dia a dia da equipe.  
- **CI/CD**: automatize builds e testes a cada commit para detectar regressões imediatamente.


---

## 📝 Exercícios de Fixação

1. Explique em até três linhas por que os passos pequenos ajudam a lidar com a memória limitada.  

2. Cite dois benefícios de implementar arquitetura “just in time”.  

3. Dê um exemplo de situação em que antecipar demais uma mudança poderia atrapalhar o projeto.

---

## 🏆 Soluções

1. Passos pequenos mantêm o foco em tarefas gerenciáveis; cada teste indica claramente quando uma parte está pronta, evitando sobrecarga cognitiva.  

2. Benefícios:  
   - Evita over-engineering e retrabalho de funcionalidades não usadas.  
   - Permite validar requisitos reais antes de investir em infraestrutura complexa.  

3. Exemplo: criar de antemão uma camada complexa de cache quando a aplicação ainda não tem volume de usuários, gerando complexidade desnecessária e atrasos iniciais.  
