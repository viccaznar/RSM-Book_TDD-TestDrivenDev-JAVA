
# 📗 Capítulo 1: O Desafio de Resolver o Problema Certo 🧐

## 📝 Tradução do Texto

A função do desenvolvimento de software é apoiar as operações e negócios de uma organização. Nosso foco como desenvolvedores profissionais deve ser entregar sistemas que ajudem a melhorar a eficácia e a produtividade, reduzir custos operacionais etc.

Olhando para meus anos como desenvolvedor e para as décadas de experiência documentadas na literatura e em histórias de artesãos ao redor do mundo, só podemos concluir que a maioria das organizações poderia melhorar muito na tarefa de entregar sistemas que apoiem seu negócio. Em resumo, estamos construindo sistemas que não funcionam direito; mesmo quando funcionam sem falhas, tendem a resolver o problema errado. Em essência, escrevemos código que não atende às necessidades reais.

Em seguida, vamos ver como criar código mal escrito e errar o alvo móvel das reais necessidades do cliente fazem parte do desafio de entregar a solução certa.

---

### 1.1.1 Criando Código Mal Escrito 🏗️

Mesmo após várias décadas de avanços, a qualidade do software continua um problema. O foco em tempo de entrega, o volume crescente de projetos e o fluxo constante de novas tecnologias tornam quase inevitáveis os desafios de qualidade.

Existem dois lados nesses problemas:

- Alta taxa de defeitos
- Falta de manutenibilidade

**Alta taxa de defeitos** gera custos extras, torna o sistema instável, imprevisível ou até inutilizável. Corrigir um bug na fase de testes costuma custar 10× ou 100× mais do que corrigi-lo assim que foi introduzido no código. Quanto mais caro e lento o conserto, menos entregamos.

**Falta de manutenibilidade** significa código de difícil compreensão e alteração. Uma mudança quase sempre quebra outra área do sistema, duplicações multiplicam bugs e ninguém quer “tocar” nesse emaranhado. Software precisa evoluir, e sem manutenibilidade ficamos travados num ciclo vicioso de atrasos e mais código problemático.

---

### 1.1.2 Falhando em Atender Necessidades Reais 🎯

Ninguém gosta de comprar gato por lebre, mas muitos clientes de TI fazem isso o tempo todo. Seguem uma especificação e só descobrem 12 meses depois que ela não representa o que realmente precisam. Sem falar que, num mercado ágil, a necessidade muda antes de o software ficar pronto.

Tentar “engrossar” a especificação antes de codificar costuma piorar: mais detalhes cedo criam um castelo de cartas de suposições que desaba ao primeiro imprevisto. Por isso surgiram métodos ágeis como Extreme Programming (XP) e Scrum, com um ingrediente-chave: ser guiado por testes.

---

## 🔍 Raciocínio Contido no Texto

- O software existe para atender operações e negócios; falhar nisso significa entregar valor abaixo do esperado.
- Código mal escrito (muitas falhas, baixa manutenibilidade) encarece e atrasa entregas.
- Especificações longas e estáticas não acompanham a mudança constante das necessidades do cliente.
- Métodos ágeis e Test-Driven Development (TDD) são as “curas” para alinhar entrega ao que realmente importa.

---

## 📚 Conceitos Explicativos

### 🐞 1. Alta Taxa de Defeitos

- Bugs geram instabilidade e custos altíssimos.
- Detectar cedo vale 10×–100× menos que consertar depois.


- **Exemplo Lúdico:** Imagine um labirinto cheio de armadilhas escondidas. Cada armadilha (bug) só aparece quando você passa lá, e consertá-la depois de todo mundo ter sido pego é muito mais caro do que remover o obstáculo antes de construir o labirinto.

---

### 🛠️ 2. Falta de Manutenibilidade

- Código confuso trava a equipe.
- Cada mudança é um risco de quebrar outra funcionalidade.


- **Exemplo Lúdico:** É como um castelo de cartas: você quer adicionar uma nova torre, mas só de encostar ele já pode desmoronar. É impossível construir mais alto sem refazer toda a base.

---

### 🎯 3. Falhar em Atender Necessidades Reais

- Especificações rígidas ficam obsoletas em meses.
- Entregas tardias não resolvem o problema que o cliente tem hoje.


- **Exemplo Lúdico:** Pense num pedido de pizza: você escolhe a cobertura antes de sair de casa, mas quando chega à pizzaria descobre que acabou o ingrediente principal. Seu pedido não atende mais ao que você precisa — e seu apetite mudou!

---

## ⚙️ Capítulo 2: Boas Práticas e Cenários Reais 📈

- Adote ciclos curtos de feedback com integração contínua (CI).
- Escreva testes automatizados que validem cada comportamento crítico.
- Priorize TDD para capturar defeitos na fonte e manter o design limpo.
- Mantenha documentação viva: critérios de aceitação claros para todos.

**Cenários frequentes em negócios**

- `E-commerce`: testes de fluxo de pagamento e carrinho evitam transações falhas.
- `Fintech`: validações de cálculo de juros e impostos garantem conformidade.
- `IoT`: simulações de hardware em testes evitam surpresas no campo.
- `Microserviços`: mocks e stubs isolam dependências e aceleram entregas.

---

## 📝 Exercícios de Fixação

1. Explique, em até três linhas, por que detectar defeitos cedo é mais barato.
2. Descreva um exemplo de manutenibilidade ruim em seu dia a dia (real ou imaginário).
3. Crie um cenário de aceitação para um sistema de reserva de ingressos (ATDD).

---

## 🏆 Soluções

1. Detectar defeitos cedo evita retrabalho em funcionalidades que já estão integradas. Corrigir antes de multiplicar o bug reduz custos e riscos.

2. Resposta pessoal, e.g.: “Um script de deploy que ninguém entende travou toda a produção.”

3. Cenário de aceitação “Reserva de Ingressos”:
   - Dado que o evento “Concerto X” tem 100 ingressos disponíveis
   - Quando o usuário selecionar 2 ingressos e confirmar o pagamento válido
   - Então o sistema deve registrar a reserva e diminuir o estoque para 98
