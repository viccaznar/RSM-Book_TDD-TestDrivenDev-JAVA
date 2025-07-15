
# 🚀 Capítulo 1.2: Solução—Ser Guiado por Testes 🔍

## 📝 Tradução do Texto

Assim como o problema que enfrentamos tem duas faces—código mal escrito e falha em atender necessidades reais—a solução que exploraremos também é dupla. Por um lado, precisamos aprender a **construir direito**. Por outro, a **construir a coisa certa**. A solução descrita neste livro—ser guiado por testes—vale para ambas as frentes.

Na prática, usamos dois níveis de “test-drive”:

- **TDD** (Test-Driven Development) para guiar o código e melhorar a qualidade interna.
- **ATDD** (Acceptance TDD) para guiar recursos e funcionalidades, garantindo a qualidade externa percebida.

---

## 🧠 Raciocínio Contido no Texto

- Dois problemas:  
  1. Código mal escrito → alta taxa de defeitos e baixa manutenibilidade.  
  2. Falta de alinhamento com necessidades reais do cliente.  


- Duas soluções complementares:  
  1. **TDD** para qualidade interna.  
  2. **ATDD** para qualidade externa.  
  
- Testes servem como motor de design e garantia contínua de valor.

---

## 📚 Conceitos Explicativos

### 🛠️ 1. Test-Driven Development (TDD)

- Escreva um teste automatizado que falhe.  
- Implemente o mínimo de código para fazê-lo passar.  
- Refatore o design para a forma mais simples, mantendo todos os testes verdes.


  - **Exemplo Lúdico:** Imagine um construtor de Lego que só adiciona uma peça depois de certificar-se de que ela se encaixa perfeitamente. O “teste” é o encaixe: se falhar, troca-se a peça antes de seguir adiante.


  - **Exemplo de código:**  


> ```python  
> # Python  
> def test_multiplica_por_zero():  
>     assert multiplica(5, 0) == 0  
>  
> def multiplica(a, b):  
>     return a * b  
> ```

---

### 🎯 2. Acceptance Test-Driven Development (ATDD)

- Defina critérios de aceitação do ponto de vista do usuário.  
- Escreva um teste de aceitação que descreva o cenário real.  
- Desenvolva o recurso via TDD até passar no teste de aceitação.


  - **Exemplo Lúdico:** Pense em um roteiro de filme: primeiro, descreve-se a cena que o espectador deve ver. Só depois se monta o cenário e se filma, garantindo que o resultado corresponda ao script de aprovação.


---

### 🔄 3. Ciclo Red–Green–Refactor

1. **Red**: escreva um teste que falha (vermelho).  
2. **Green**: implemente o código mínimo para torná-lo verde.  
3. **Refactor**: limpe duplicações e simplifique o design, mantendo tudo verde.


  **Exemplo Lúdico:** Conduzir um carro com piloto automático:  

  - `Red`: configure a rota (teste falho).  
  - `Green`: ative o piloto e siga o caminho.  
  - `Refactor`: ajuste a velocidade e otimize a viagem.


---

### 🔍 4. Garantia de Qualidade via Cobertura e Design

- 100% de cobertura não é meta; sim testar casos normais, limites e erros de usuário.  
- Focar em **interfaces públicas** força pensar no uso real antes de detalhes internos.


  - **Exemplo Lúdico:** É como testar todos os botões de um videogame antes de lançar um console: não basta checar power on/off, precisa simular combinação de comandos, respostas erradas e pausas inesperadas.

---

### ⏱️ 5. Redução do Tempo de Correção de Defeitos

- Bugs encontrados no dia da introdução custam muito menos que os detectados meses depois. Passos pequenos e testes frequentes evitam sessões longas de debug.


  - **Exemplo Lúdico:** Consertar um vazamento em casa: é muito mais barato vedar o cano no momento em que começa a pingar do que reformar a cozinha inteira após a inundação.


---


# 📈 Capítulo 2: Boas Práticas & Cenários Reais 🏭

## ✅ Boas Práticas

- `Integração Contínua (CI)`: execute todos os testes a cada commit.  
- `Feedback Rápido`: falha no build = alerta imediato.  
- `Pair Programming`: dupla revê testes e código em tempo real.  
- `Critérios de Aceitação Vivos`: mantenha histórias de usuário e cenários sempre atualizados.

## 🌐 Cenários Reais de Negócio

- Exemplo de Uso TDD/ATDD

`E-commerce`: Fluxo de carrinho e pagamento (cenários de estoque, pagamento recusado, cupom inválido)

`Fintech`: Cálculo de juros, simulações de investimento e relatórios fiscais

`IoT`: Testes simulando falha de sensor, desconexão de rede e reinicialização automática

`Microserviços`: Mocks e stubs para isolar chamadas entre serviços, garantindo deploys independentes e seguros

---

# 📝 Exercícios de Fixação

1. Descreva em até três linhas o propósito duplo de “ser guiado por testes”.  
2. Cite três benefícios de usar TDD conforme o texto.  
3. Escreva um pequeno teste que falhe para uma função `divide(a, b)` em JavaScript, e depois a implementação mínima.

---

# 🏆 Soluções

1. Ser guiado por testes ajuda a **construir código de alta qualidade** (TDD) e a **entregar as funcionalidades certas** (ATDD), mantendo alinhamento com requisitos reais.  

2. Três benefícios de TDD:  

   - Feedback rápido sobre regressões.  
   - Design mais simples e modular.  
   - Menos tempo gasto em debug e correção de bugs.  

3. Teste e implementação mínima em JavaScript:  


```java
// Função que divide dois números
function testDivideByZero() {  
   try {  
     divide(10, 0);  
     throw new Error('Deveria ter lançado');  
   } catch (e) {  
     console.assert(e.message === 'Divisão por zero');  
   }  
}  


// Implementação mínima da função divide
@Test
function divide(a, b) {  
   if (b === 0) throw new Error('Divisão por zero');  
   return a / b;  
}  
```