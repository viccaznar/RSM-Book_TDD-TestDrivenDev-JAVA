# 🚀 Capítulo 1.2: Solução—Ser Guiado por Testes 🔍

---

## 📝 Tradução do Texto

TDD ajuda a construir código com alta qualidade técnica—código que faz o que esperamos e que é fácil de entender e manter. Contudo, a correção do código desenvolvido via TDD é verificada em blocos isolados de lógica, não em recursos e capacidades do sistema. Além disso, até o melhor código escrito “test-first” pode implementar algo que o cliente não precisa. É aí que entra o desenvolvimento guiado por testes de aceitação (acceptance TDD).

O modo tradicional de adicionar funcionalidades é: escrever um documento de requisitos, implementar segundo ele, testar a feature internamente e só então submeter ao cliente. Acceptance TDD inverte essa ordem: traduzimos um requisito em testes executáveis e, só então, implementamos contra esses testes, em vez de confiar na interpretação verbal do desenvolvedor.  

Acceptance TDD preenche a lacuna entre programadores e clientes. Em vez de trabalhar com documentos arbitrários, colaboramos de perto para definir testes explícitos e sem ambiguidades que nos dizem exatamente quando uma funcionalidade está “pronta”. Ao definir o comportamento desejado em termos concretos—via testes que o próprio sistema executa—asseguramos que estamos entregando o que o cliente realmente precisa.

O processo é análogo ao ciclo TDD no nível de código, mas focado no comportamento do sistema como um todo. Por isso, falamos a uma “linguagem” que programadores e clientes entendem. TDD e acceptance TDD andam de mãos dadas: no nível de sistema, guiamos o desenvolvimento com ATDD; na implementação de cada feature, usamos TDD. Não são prescritivos um ao outro, mas combinam de forma poderosa.

Agora já temos uma ideia de como TDD e acceptance TDD se unem para solucionar o desafio de entregar software de alta qualidade que atende à necessidade certa. Nos próximos tópicos, veremos em detalhes como TDD ajuda a criar código de qualidade e, em seguida, como usar testes para “construir a coisa certa” com ATDD.

---

## 🧠 Raciocínio Contido no Texto

- Testes no nível de código (TDD) garantem qualidade interna; testes de aceitação (ATDD) garantem qualidade externa.  
- Mover a fase de testes antes da implementação alinha expectativas e reduz retrabalho.  
- Definir funcionalidades como testes executáveis elimina ambiguidades entre desenvolvedores e clientes.  
- A combinação TDD + ATDD forma um processo coeso para “construir direito” e “construir a coisa certa”.

---

## 📚 Conceitos Explicativos

### 🎯 1. Acceptance Test-Driven Development (ATDD)

- Traduzir requisitos em testes executáveis antes de codificar.  
- Colaborar com clientes para definir cenários claros de “pronto”.  
- Implementar cada funcionalidade até satisfazer os testes de aceitação.


  - **Exemplo Lúdico:** Pense em um diretor de cinema que escreve o roteiro completo da cena antes de montar o cenário. Cada diálogo é um “teste” sobre o que o público deve ver. Só quando o roteiro estiver aprovado é que se constroem os cenários e se inicia a filmagem.

---

### 🔄 2. Ciclo Invertido de Requisitos

- Requisitos → testes executáveis → implementação.  
- Evita interpretações errôneas de documentos estáticos.  
- Garante que cada passo do desenvolvimento agrega valor real.


  - **Exemplo Lúdico:** É como planejar uma viagem dizendo “temos que chegar ao ponto X às 15h”. Em vez de buscar mapas e estimativas, você programa o GPS para simular o trajeto inteiro antes de sair de casa, ajustando o plano conforme o GPS “falar” que algo não vai bater.

---

### 💡 3. Alinhamento Cliente–Desenvolvedor

- Definir linguagem comum (testes) compreendida por todos.  
- Eliminar suposições e ambiguidades.  
- Aumentar confiança mútua de que “feito” significa “útil”.


  - **Exemplo Lúdico:** Imagine um jogo de charadas onde cliente e desenvolvedor usam cartões com desenhos (os testes) em vez de descrições verbais. Assim, não há dúvidas sobre o que deve ser representado: o desenho fala por si só.

---

### 🎁 4. Motivação Pessoal para Adotar TDD/ATDD

- Só vale aprender algo novo se trouxer benefício real.  
- Técnicas de teste-first devem melhorar nossa produtividade e satisfação.  
- Identificar ganhos concretos torna a mudança sustentável.


  - **Exemplo Lúdico:** Quem troca de carro escolhe um modelo que ofereça economia de combustível, conforto e segurança—não só porque é “novo”. Do mesmo modo, adotar TDD/ATDD deve trazer vantagens palpáveis: menos bugs, código limpo e feedback rápido.

---

## 🛠️ Capítulo 2: Boas Práticas e Cenários Reais 📈

### ✅ Boas Práticas

- Garanta **colaboração contínua** com clientes durante a definição de testes de aceitação.  
- Mantenha **testes de aceitação legíveis**, usando linguagem próximo ao negócio.  
- No nível de código, siga rigidamente o ciclo **Red–Green–Refactor** do TDD.  
- Automatize toda a suíte de testes (unitários e de aceitação) em **CI/CD** para feedback imediato.

### 🌐 Cenários Frequentes em Negócios

- `E-commerce`: validar fluxo de compra, estoque e pagamentos recusados via ATDD.  
- `Fintech`: simular cenários de investimento e falhas de transação com testes de aceitação.  
- `SaaS B2B`: alinhar workflows complexos (criação de conta, permissões, relatórios) antes de codificar.  
- `IoT`: escrever cenários de desconexão e reconexão de dispositivos para validar robustez da plataforma.

---

## 📝 Exercícios de Fixação

1. Explique em até três linhas por que acceptance TDD reduz o retrabalho com clientes.  
2. Cite duas diferenças entre testes de unidade (TDD) e testes de aceitação (ATDD).  
3. Escreva um cenário de aceitação (em linguagem natural) para uma busca de produtos em um e-commerce.

---

## 🏆 Soluções

1. Acceptance TDD traduz requisitos diretamente em testes executáveis antes de codificar, alinhando expectativas e evitando que clientes rejeitem funcionalidades entregues.  

2. Diferenças:  
   - TDD foca em blocos lógicos e unidades de código; ATDD foca em comportamentos e fluxos de usuário.  
   - TDD é escrito em frameworks de unit test; ATDD usa ferramentas que suportam linguagem próxima ao negócio (ex.: Cucumber).  

3. Exemplo de cenário de aceitação:

  Dado que o catálogo contém produtos “Notebook” e “Tablet” Quando o usuário pesquisar por “Note” Então ele deve ver na lista pelo menos o “Notebook” E não deve ver o “Tablet”