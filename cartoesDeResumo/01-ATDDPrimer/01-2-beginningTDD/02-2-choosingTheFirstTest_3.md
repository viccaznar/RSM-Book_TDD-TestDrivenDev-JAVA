# 📒 Capítulo 2.2.4: Escrevendo Outro Teste & Triangulação 🔍

## 📝 Tradução do Texto

Para eliminar o hard-coding do valor da variável, adicionamos um segundo teste que usa outro valor. No `TestTemplate`, criamos o método `differentValue()` que configura `"name"` como `"someone else"` e espera o resultado `"Hello, someone else"`. Essa técnica se chama **triangulação**: usamos múltiplos “pontos de vista” para levar a implementação à forma correta.  

Em seguida, implementamos o mínimo para passar o novo teste: armazenamos `variableValue` em um campo e retornamos `"Hello, " + variableValue` no método `evaluate()`. Nosso teste volta a ficar verde sem realmente analisar o template.  

Para eliminar também o hard-coding do prefixo fixo, adicionamos outro teste `differentTemplate()` que usa `"Hi, ${name}"` e espera `"Hi, someone else"`. Agora o retorno hard-coded não é mais suficiente — é hora de discutir profundidade e amplitude da implementação.

---

## 🧠 Raciocínio Contido no Texto

- Um teste só passando por um caso pode mascarar hard-codings; múltiplos testes forçam generalização.  
- **Triangulação** adiciona novos cenários (valores e templates diferentes) para expor implementações simplistas.  
- Evoluir gradualmente testes e código evita over-engineering, extrapolando apenas o necessário a cada etapa.  
- A decisão de avançar para parsing real surge naturalmente quando os hacks deixam de funcionar.

---

## 📚 Conceitos Explicativos

### 🧭 1. Triangulação  

Adicionar testes com diferentes entradas para guiar a implementação do mínimo até a solução geral.

  - **Exemplo Lúdico:** Imagine definir a cor de um carro apenas testando “vermelho”. Se você pintar todo o carro de vermelho, vai funcionar só para esse teste. Ao testar também “azul” e “verde”, você força a instalação de uma tinta que aceite qualquer cor, não apenas vermelho.

---

### 🛠️ 2. Eliminar Hard-Coding  

Substituir retornos literais por lógica que use variáveis e templates dinamicamente.

  - **Exemplo Lúdico:** É como aprender a cozinhar um prato: primeiro você memoriza “sopa de legumes” inteira (hard-coding). Depois testando “sopa de frango” e “sopa de peixe”, você desenvolve a receita base que aceita qualquer ingrediente.

---

### 🔄 3. Expandir Cobertura de Testes  

Crie testes que variem não só o valor da variável, mas também o próprio template, garantindo flexibilidade total.

  - **Exemplo Lúdico:** É similar a um maestro que ensaia uma melodia em diferentes tonalidades e andamentos: só assim ela fica perfeita em qualquer instrumento e ritmo.

---

## 🛠️ Capítulo 2.3: Boas Práticas & Cenários Reais 🌟

### ✅ Boas Práticas  

- **Use triangulação**: a cada hack (hard-coding) que passar, adicione um teste que o derrube.  

- **Teste cenários variados**: valores diferentes, templates variados e erros esperados.  

- **Refatore imediatamente**: assim que o mínimo passar, extraia lógica para parsing e substituição.  

- **Evolua em pequenos passos**: implemente só o necessário para satisfazer o teste atual.  

- **Comente a intenção**: documente nos testes o motivo de cada cenário (ex.: “força nova template”).

### 🌐 Cenários Reais em Negócios  

- **E-commerce**: testes para `"Bem-vindo, ${user}"` e `"Olá, ${user}! Seu pedido #${id}"`.  
- **Fintech**: validar `"Saldo: ${amount} USD"` e `"Balance: ${amount} EUR"`.  
- **SaaS B2B**: templates de notificação com variáveis de cliente e data.  
- **IoT**: dashboards que exibem `"Sensor ${id}: ${value}°C"` em diferentes unidades de medida.

---

## 📝 Exercícios de Fixação

1. Em até três linhas, explique por que a **triangulação** é essencial após um teste passar com hard-coding.  

2. Cite dois sinais de que o código hackeado (hard-coded) precisa ser refatorado. 

3. Escreva um teste simples (em linguagem natural) que force a substituição de dois marcadores, saudação e nome.

---

## 🏆 Soluções

1. Triangulação adiciona novos cenários que quebram soluções específicas demais, forçando a generalização da lógica e evitando over-engineering. 

2. 
   - Um segundo teste com valor diferente falha.  
   - Um teste com template diferente retorna resultado incorreto.  

3. Cenário “Duas Variáveis": Dado o template "Good ${timeOfDay}, ${name}!" Quando definir timeOfDay="morning" e name="Bob" Então evaluate() deve retornar "Good morning, Bob!"

```java
// Java + JUnit
@Test
public void twoVariables() throws Exception {
 Template tpl = new Template("Good ${timeOfDay}, ${name}!");
 tpl.set("timeOfDay", "morning");
 tpl.set("name", "Bob");
 assertEquals("Good morning, Bob!", tpl.evaluate());
}