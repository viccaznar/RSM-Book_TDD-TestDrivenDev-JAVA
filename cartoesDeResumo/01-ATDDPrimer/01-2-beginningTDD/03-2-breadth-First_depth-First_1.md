# 📘 Capítulo 2.3: Amplitude vs Profundidade no TDD 🔍

## 📝 Tradução do Texto

O software que construímos hoje não é algo trivial que se resolve em poucas horas. Já trabalhei em sistemas com dezenas de milhares de linhas de código — um chegando a mais de um milhão. Assim como engolir um muffin inteiro vira bagunça, dar mordidas grandes demais em código acaba mal.  

No nosso motor de templates, chegamos a um trecho de complexidade que ainda não tratamos. O teste de renderização não funciona sem lidar com ele. Mas será que temos que resolver tudo de uma vez?  

Assim como em algoritmos há percursos em largura (breadth-first) ou profundidade (depth-first), no TDD podemos optar por:  
- Implementar funcionalidades de alto nível primeiro, fingindo internals (breadth-first).  
- Ou aprofundar num recurso específico antes de juntar tudo (depth-first).  

Com breadth-first, escrevemos testes de interface pública e “fingimos” parsing ou rendering até que a camada superior passe. Depois testamos e implementamos as camadas internas.  

Com depth-first, voltamos ao vermelho, criamos testes para a lógica de parsing, implementamos um pedaço vertical — parsing e rendering juntos — e só então escrevemos testes de alto nível.  

Podemos estender o truque de fingir internals: no exemplo “Hello, ${name}”, usamos `replaceAll("\\$\\{name\\}", variableValue)` no método `evaluate` para passar o teste sem um parser completo. Não é “trapaça”! São **baby steps** — todos testes verdes, ambiente estável — e partimos para refatorar e extrair lógica genérica.

---

## 🧠 Raciocínio Contido no Texto

- Sistemas grandes exigem abordagens passo a passo, não soluções gigantes de uma vez.  
- `Breadth-first` foca em funcionalidades externas, adiando detalhes internos com stubs.  
- `Depth-first` foca nos detalhes de parsing antes de compor funcionalidades de alto nível.  
- Faking internals (regex hard-coded) mantém testes verdes e impulsiona progresso.  
- Refatoração e baby steps asseguram evolução limpa e gerenciam complexidade incremental.

---

## 📚 Conceitos Explicativos

### 🍰 1. Mordidas Pequenas em Código

Dividir problemas grandes em pedaços pequenos previne confusão e mantém a direção clara.

  - **Exemplo Lúdico:** É como comer um bolo fatiado em pedaços: você aprecia cada fatia sem se engasgar, construindo satisfação passo a passo.

---

### ↔️ 2. Estratégia Breadth-First

Implementar primeiro a interface pública, fingindo (mockando) funções internas; depois desça para os detalhes.

  - **Exemplo Lúdico:** Imagine montar um quebra-cabeça começando pela borda: você contorna o quadro, deixando o centro para depois.

---

### ↕️ 3. Estratégia Depth-First

Focar num fatiamento vertical: implementar parsing e rendering juntos antes de expandir para casos de uso mais amplos.

  - **Exemplo Lúdico:** É como descer num tobogã aquático: você testa o percurso completo — altura, curva e splash — antes de convidar a turma.

---

### 🧪 4. Fingir Internals (Faking Details)

Usar soluções temporárias (hard-coded ou regex simples) para satisfazer testes iniciais.

  - **Exemplo Lúdico:** É como decorar uma cena de teatro com cartolina antes de construir cenários detalhados: o espetáculo continua até a hora da reforma.

---

### 🛠️ 5. Refatoração e Evolução

Após cada fase “verde”, extraia lógica repetida e generalize a solução, mantendo testes intactos.

  -  **Exemplo Lúdico:** Pense num jardineiro que poda galhos secos depois de cada florada: o jardim fica sempre saudável antes de plantar novas mudas.

---

## 💼 Capítulo 2.4: Boas Práticas & Cenários Reais 🌟

### ✅ Boas Práticas

- Escolha entre **breadth-first** ou **depth-first** conforme urgência de entrega e estabilidade.  

- Use **stubs** e **regex simples** para manter o fluxo de testes sem paralisar o projeto.

- Refatore **logo após** cada conjunto de testes verdes, extraindo parsing genérico e substituição.

- Documente nos testes o motivo de cada hack temporário e o próximo passo de refatoração.

- Mantenha sua suíte de testes **curta e rápida**, garantindo feedback contínuo.

- Revise periodicamente a abordagem escolhida: às vezes é melhor alternar entre breadth e depth.

### 🌐 Cenários Reais em Negócios

- **E-commerce**: breadth-first para validar carrinho (testes de checkout) e depois depth-first para parsing de cupons complexos.  
- **Fintech**: depth-first em regras fiscais (parsing de alíquotas) antes de compor relatórios gerenciais.  
- **SaaS B2B**: breadth-first ao expor API pública com mocks de backend; depois depth-first para integração real.  
- **IoT**: depth-first em protocolo de comunicação sensor-dispositivo antes de montar painel de monitoramento.

---

## 📝 Exercícios de Fixação

1. Em até três linhas, descreva a diferença entre abordagem `breadth-first` e `depth-first` no TDD.

2. Cite dois benefícios de fingir internals antes de implementar parsing completo.

3. Por que a refatoração imediata após o “verde” é fundamental em ambos os estilos?

---

## 🏆 Soluções

1. `Breadth-first`: testa e implementa interface pública primeiro, adiando detalhes; `depth-first`: implementa internals primeiro, depois a interface.

2.  
   - Mantém o fluxo de desenvolvimento sem paradas prolongadas.  
   - Fornece feedback rápido, permitindo identificar problemas de API desde cedo.  

3. Refatorar logo após o verde elimina hacks, evita dívidas técnicas e garante que a base se mantenha limpa antes de avançar.  

---

## 📜 Exemplo de Código

```java
public class Template {
    private String variableValue;
    private String templateText;

    public Template(String templateText) {
        this.templateText = templateText;
    }

    public void set(String variable, String value) {
        this.variableValue = value;
    }

    public String evaluate() {
        return templateText.replaceAll("\\$\\{" + variable + "\\}", variableValue);
    }
}
```