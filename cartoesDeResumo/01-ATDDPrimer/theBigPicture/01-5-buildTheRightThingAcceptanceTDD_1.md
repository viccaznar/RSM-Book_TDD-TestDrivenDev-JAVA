# 📘 Capítulo 1.4: Construir a Coisa Certa — Acceptance TDD 🔨

## 📝 Tradução do Texto

Testar sempre fez parte integrante do desenvolvimento de software. No entanto, a forma como testamos evoluiu muito ao longo das décadas. Como programadores, sempre quisemos saber se nosso software funciona antes de entregá-lo aos usuários. Os meios para obter esse conhecimento mudaram bastante com o surgimento de processos ágeis, como o Extreme Programming.

Além disso, o papel dos testes deixou de ser apenas verificar a conformidade com a especificação. A solução para a segunda metade do nosso problema — código que não atende às necessidades reais — é permitir que os testes conduzam o desenvolvimento de **funcionalidades** do sistema. É disso que se trata o acceptance test-driven development: só iniciamos o desenvolvimento de uma funcionalidade quando existe um **teste de aceitação** que exige essa funcionalidade.

Em essência, os testes deixam de ser meras ferramentas de verificação e passam a fazer parte das **regras de negócio**, da especificação e do **meio de colaboração com o cliente**. Nesta seção, veremos o papel dos testes na colaboração entre desenvolvedores, testadores e clientes e como eles se tornam uma linguagem comum para todos.

Antes de abordar a colaboração, vamos entender a relação entre acceptance TDD e o TDD “tradicional”. Afinal, os nomes são quase idênticos, então deve haver uma razão para isso.

### 1.4.1 O que Há num Nome? 🤔

O nome “acceptance test-driven development” sugere semelhança com o TDD normal. O sufixo vem do TDD, mas o que significa “acceptance test”? Em resumo, testes de aceitação são **indicadores de conclusão** de um requisito ou funcionalidade. Quando todos os testes de aceitação de uma feature passam, você sabe que ela está **pronta**.

Acceptance TDD não depende de um formato específico de requisitos. As mesmas ideias funcionam com casos de uso, user stories ou qualquer meio equivalente de documentar o que deve ser feito. Equipes que usam user stories costumam chamar a técnica de “story-driven development”, outro nome para o mesmo processo. Algumas preferem dizer “customer test-driven development”, destacando que os testes pertencem ao cliente.

> **Nota:** TDD e acceptance TDD compartilham muito em comum e podem ser adotados separadamente. Desenvolvedores sem user stories podem usar TDD no nível de código; equipes que não programam test-first podem ainda criar features test-first. Mas a combinação de ambos traz melhorias multiplicadas.

Independentemente da ferramenta de requisitos, o objetivo principal do acceptance TDD é **aproximar cliente e equipe**, usando testes como contrato e linguagem compartilhada. Vamos ver como a abordagem test-driven facilita isso.

---

## 🧠 Raciocínio Contido no Texto

- Testes de aceitação garantem que **só se entrega** o que o cliente realmente quer.  
- Acceptance TDD faz dos testes parte integrante dos requisitos e da especificação.  
- A técnica promove **colaboração** contínua entre cliente e time, evitando mal-entendidos.  
- Embora TDD e acceptance TDD sejam independentes, juntos formam um processo coeso de qualidade interna e externa.

---

## 📚 Conceitos Explicativos

### 🎯 1. Testes de Aceitação
 
- Definem critérios que indicam quando uma feature está completa.  
- Executáveis, servem como contrato entre time e cliente.

  - **Exemplo Lúdico:** Imagine um **garçom** que só traz o prato quando o cliente marcar “Aprovado” em um cartão. O prato só sai da cozinha quando o cliente atesta via teste que o sal, a apresentação e a temperatura estão corretos.

---

### 🔀 2. Acceptance TDD vs. TDD

- **TDD** foca em testar unidades e APIs até chegar a um design limpo.  
- **Acceptance TDD** foca em testar **fluxos de usuário** e funcionalidades de ponta a ponta.

  - **Exemplo Lúdico:** É como um **arquiteto** que primeiro projeta a fundação (TDD) e depois valida com o cliente que cada cômodo atende ao uso (ATDD) antes de erguer as paredes.

---

### 📜 3. Formatos de Requisitos e Propriedade do Cliente

- Testes de aceitação não exigem um padrão: podem ser user stories, casos de uso ou tabelas.  
- Os testes são **“posse” do cliente**: quem melhor conhece o que precisa ser entregue?

  - **Exemplo Lúdico:** Pense num **cardápio personalizável**: o cliente escreve o teste em forma de receita, e a cozinha só prepara o prato de acordo com essa receita — nada de interpretações.

---

## 🛠️ Capítulo 2: Boas Práticas & Cenários Reais 🏭

### ✅ Boas Práticas

- Defina critérios de aceitação em **linguagem de negócio**, compreensível por todos.  
- Mantenha os testes de aceitação **automatizados** e executáveis em CI/CD.  
- Integre o cliente em **demos frequentes**, validando cada teste antes da próxima iteração.  
- Documente e atualize **requisitos** como testes vivos, não em documentos estáticos.  
- Combine acceptance TDD com TDD no nível de código para máxima sinergia.

### 🌐 Cenários Reais

- `E-commerce`: testes que simulam finalização de compra com cartão válido, cupom e frete grátis.  
- `Fintech`: cenários de simulação de empréstimo com diferentes perfis de cliente.  
- `SaaS B2B`: fluxo de criação de conta corporativa, aprovações e notificações por e-mail.  
- `IoT`: testes de comportamento de dashboard após envio de dados de sensores.

---

## 📝 Exercícios de Fixação

1. Explique em até três linhas o papel dos testes de aceitação como **contrato** entre cliente e time.  

2. Diferencie TDD e acceptance TDD em dois pontos principais.  

3. Escreva um cenário de aceitação simples (em linguagem natural) para um recurso de “recuperar senha”.

---

## 🏆 Soluções

1. Testes de aceitação documentam critérios claros de “pronto”, garantem alinhamento com o cliente e servem de guia para o desenvolvimento, eliminando ambiguidades.  

2.  
   - TDD testa unidades e APIs internamente; ATDD testa fluxos de usuário externamente.  
   - TDD melhora design de código; ATDD valida funcionalidades esperadas pelo cliente.  

3. Cenário de aceitação “Recuperar Senha”:  
