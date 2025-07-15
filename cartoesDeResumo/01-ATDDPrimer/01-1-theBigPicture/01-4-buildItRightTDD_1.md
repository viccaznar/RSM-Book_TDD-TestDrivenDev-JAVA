 # 📦 Capítulo 1.3: Construir Certo — TDD 🛠️

## 📝 Tradução do Texto

Test-driven development (TDD) é uma técnica de desenvolvimento e design que nos ajuda a construir o sistema incrementalmente, sabendo que nunca estamos longe de uma base funcional. Um teste é nosso próximo pequeno passo.

Nesta seção, aprenderemos o que faz o TDD funcionar, por que ele traz benefícios e como seu ciclo — teste, código e refatoração — é o coração do nosso trabalho. Veremos também o valor de ter software em funcionamento desde o primeiro dia, a importância de projetar para o presente e como manter o sistema saudável o tempo todo. Próxima parada: o ciclo Teste–Código–Refatorar.

### 1.3.1 Teste–Código–Refatorar: o Coração do TDD

Como vimos, a regra simples do TDD é:
> “Só escreva código para corrigir um teste que falhou.”

Em vez de primeiro projetar tudo, depois implementar e só então testar, o TDD inverte o fluxo: escrevemos o teste, fazemos o código passar e, por fim, ajustamos o design. Essa “refatoração” é um design pós-código com o objetivo de melhorar a estrutura sem alterar o comportamento.

#### Red–Green–Refactor

- **Red**: escreva um teste que falhe (barra vermelha).  
- **Green**: implemente o mínimo para fazê-lo passar (barra verde).  
- **Refactor**: limpe duplicações e simplifique o design, mantendo todos os testes verdes.

---

## 🧠 Raciocínio Contido no Texto

- Construção incremental reduz riscos e permite entregas contínuas.  
- Inverter o ciclo tradicional (design → código → teste) fortalece o design emergente.  
- Testes guiam a API e o comportamento desejado antes de detalhar a implementação.  
- Refatoração constante garante código limpo sem sacrificar funcionalidade.

---

## 📚 Conceitos Explicativos

### 🏗️ 1. Desenvolvimento Incremental com Base Funcional

- A cada passo, o sistema permanece executável.  
- Pequenas adições mantêm o progresso visível e seguro.

  - **Exemplo Lúdico:** Imagine um **arquiteto de LEGO** que só cola um bloco depois de testar se a estrutura aguentou o empilhamento anterior. Assim, a torre nunca desmorona enquanto cresce.

---

### 🔄 2. Ciclo Teste–Código–Refatorar

- Teste primeiro (falha) → Código depois (passa) → Refatorar design.  
- Repetir constantemente mantém o foco em qualidade e simplicidade.

  - **Exemplo Lúdico:** É como **pedalar uma bicicleta**: primeiro você solta o freio (teste falha), depois começa a pedalar (faz o teste passar) e só então ajusta o selim e o guidão para o melhor conforto (refatoração).

---

### 🌈 3. Red–Green–Refactor

- Red: ver o teste falhar reforça o que falta.  
- Green: passar no teste confirma o comportamento.  
- Refactor: melhorar sem mudar o “verde”.

  - **Exemplo Lúdico:** Pense num **semáforo** que fica vermelho quando há um pedestre esperando (teste falha), vira verde quando o carro passa (teste passa) e depois ajusta o tempo de sinal para otimizar o trânsito (refatoração).

---

### ✍️ 4. Escrever o Teste Primeiro como Decisão de Design

- Definir a interface e o comportamento desejado antes da implementação.  
- Força pensar no uso real da funcionalidade.

  - **Exemplo Lúdico:** É como desenhar o **molde de um biscoito** antes de abrir a massa: você já sabe o formato final que quer, e tudo que vier depois vai se encaixar perfeitamente.

---

## 🛠️ Capítulo 2: Boas Práticas & Cenários Reais 📈

### ✅ Boas Práticas

- Adote **passos pequenos**: um teste, um código, uma refatoração.  
- Mantenha **suíte de testes rápida** (ideal: <1 minuto).  
- Garanta **cobertura equilibrada**: primeiros cenários críticos, depois casos de borda.  
- Use **integração contínua (CI/CD)** para rodar todos os testes a cada commit.  
- Integre **code review** focado em qualidade de testes e clareza de refatorações.

### 🌐 Cenários Frequentes em Negócios

Exemplos de Uso TDD:

- `E-commerce`: Validar fluxo de checkout e cálculos de frete antes de disponibilizar no site              
- `Fintech`: Cobrar juros e tarifas corretamente em simulações instantâneas                            
- `SaaS B2B`: Garantir que APIs de integração não quebrem contratos com clientes externos               
- `IoT`: Testar emuladores de sensores e redes antes do deployment em equipamentos de campo         

---

## 📝 Exercícios de Fixação

1. Descreva em até três linhas por que o “Refactor” vem depois do “Green” no ciclo TDD.  
2. Explique a vantagem de manter sempre uma base funcional ao longo do desenvolvimento.  
3. Dê um exemplo simples de um teste que falha (Red) para uma função `somar(a, b)` em Java, e depois a implementação mínima.

---

## 🏆 Soluções

1. O “Refactor” ocorre após o “Green” para garantir que o código funcional não seja quebrado; só então melhoramos o design mantendo todos os testes passando. 

2. Manter a base executável reduz riscos de regressão, facilita demonstrações rápidas e permite correções contínuas.  

3. Teste e implementação mínima em Java:  
```java  
// Java  
import static org.junit.Assert.*;  
import org.junit.Test;  
  
public class SomaTest {  
   @Test  
   public void deveFalharPrimeiro() {  
     // Este teste falha porque ainda não implementamos o método  
     assertEquals(5, Calculadora.somar(2, 3));  
   }  
}  

public class Calculadora {  
   public static int somar(int a, int b) {  
     return a + b;  
   }  
}  
```

### 1.3.1 Escrever o Teste Primeiro para Guiar o Design 🎯

- Definir a interface e o comportamento desejado antes da implementação.  
- Testes antecipam o uso e revelam necessidades reais de API.  


  - **Exemplo Lúdico:** Imagine um **designer de quebra-cabeça** que primeiro desenha a última peça e só então cria as bordas do tabuleiro. Assim, cada peça se encaixa perfeitamente no todo.

---

### 1.3.2 Escrever Código Mínimo — Apenas o Necessário ✍️

- Fechar a “lacuna” identificada pelo teste em poucos minutos.  
- Focar em satisfazer o requisito explícito sem otimizações antecipadas.  


  - **Exemplo Lúdico:** Pense num **culinário de receitas rápidas**: o chef segue uma receita de 3 passos, prepara o prato em 5 minutos “do jeito mais simples” e só depois melhora a apresentação.

---

### 1.3.3 Refatorar — Aprimorar o Design 🔄

- Analisar o código funcional e melhorar sua estrutura sem alterar o comportamento.  
- Evitar acumular “feiúras” que reduzam produtividade futura.  


  - **Exemplo Lúdico:** É como um **jardinheiro** que poda galhos secos depois de colher os frutos. A poda não muda o rendimento imediato, mas mantém a planta saudável para próximas colheitas.

---

## 🧠 Raciocínio Contido no Texto

- Testes conduzem o design de APIs utilizáveis.  
- Passos pequenos evitam grandes quebras e longas depurações.  
- Refatoração é essencial para manter o código sustentável.  
- Focar no presente (só no que é necessário agora) evita over-engineering.

---

### ✅ Boas Práticas

- Escreva testes **pequenos** e **focados** (falha rápida).  
- Implemente o **mínimo** para passar no teste.  
- Refatore **imediatamente** após verde.  
- Mantenha a suíte de testes **rápida** (< 1 min).  
- Anote ideias extras num **backlog**, não no código.  
- Use **CI/CD** para validar automações a cada commit.