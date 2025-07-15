# 📗 Capítulo 2.2.3: Fazendo o Compilador Feliz & Primeiro Verde 🔄

## 📝 Tradução do Texto

### 🚧 Fazendo o Compilador Feliz  
O compilador avisa que a classe `Template` não existe, que não há construtor recebendo `String`, e que os métodos `set` e `evaluate` estão faltando. Para satisfazer o compilador, criamos um esqueleto mínimo:

> "```java
> public class Template {
>     public Template(String templateText) {
>     }
>     public void set(String variable, String value) {
>     }
>     public String evaluate() {
>         return null;
>     }
> }
> ```"

Agora o código compila. O próximo passo é rodar o teste.

### ⏯️ Executando o Teste  
Ao executar o teste, ele falha — como esperado — porque nada foi implementado. Ver o teste falhar confirma que estamos de fato trabalhando no teste certo e que ainda não existe funcionalidade. Um inesperado “verde” significaria que nossa suposição estava errada.

### 🔴 O Teste Falho é Progresso  
Um teste que falha dá a métrica exata de quando a tarefa está completa: ele só passa quando o comportamento desejado existir. Nada de “90% concluído” ou “faltam cinco minutos”. O vermelho do JUnit diz: “ainda falta código”.

### 🟢 Fazendo o Primeiro Teste Passar  
Para sair rápido do vermelho, implementamos o mínimo necessário. A forma mais simples de passar o teste “Hello, ${name}” com `name="Reader"` é devolver a string fixa:

> "```java
> public class Template {
>     public Template(String templateText) {
>     }
>     public void set(String variable, String value) {
>     }
>     public String evaluate() {
>         return "Hello, Reader";
>     }
> }
> ```"

É um “hack” intencional: não usamos o texto ou a variável, mas ganhamos o “verde” imediato. Isso revela dois eixos de evolução: usar o template e aplicar o valor dinâmico.

---

## 🧠 Raciocínio Contido no Texto

- Stub de classe e métodos permite focar em testes antes de implementar lógica.  
- Falhar primeiro confirma que o teste é executado e que a funcionalidade não existe.  
- Red–Green: vermelho (teste falho), verde (teste passa) define o ritmo TDD.  
- Implementação minimalista garante feedback rápido antes de evoluir para solução geral.

---

## 📚 Conceitos Explicativos

### 🛠️ 1. Stub para Compilação  
**Resumo**  
Crie construtores e métodos vazios para satisfazer o compilador e poder executar testes.

**Exemplo Lúdico**  
É como montar uma casinha de boneca sem móveis: a estrutura existe para a visita, mesmo vazia, antes de mobiliar.

---

### 🎯 2. Teste Falho como Progresso  
**Resumo**  
Testes que falham comprovam que ausência de funcionalidade é detectada; o progresso só existe quando passam.

**Exemplo Lúdico**  
Pense num **farol de trânsito**: vermelho mostra que algo precisa mudar; só quando virar verde é seguro seguir.

---

### ⏱️ 3. Implementação “Quick Win”  
**Resumo**  
Use a solução mais simples (hard-coded) para passar o teste o mais rápido possível e manter o ciclo ágil.

**Exemplo Lúdico**  
É como fazer um **rascunho** de texto escrevendo “Lorem ipsum” para estruturar um artigo antes de desenvolver o conteúdo real.

---

### 🔄 4. Evoluindo a Solução  
**Resumo**  
Após o “verde” fácil, refine o código para usar dados e lógica reais, ampliando testes conforme necessário.

**Exemplo Lúdico**  
Como um escultor que primeiro faz um bloco bruto de mármore (rascunho) e depois esculpe os detalhes finos.

---

## 💼 Capítulo 2.3: Boas Práticas & Cenários Reais 🌟

### ✅ Boas Práticas  
- Gere **stubs** automaticamente com IDE para poupar digitação.  
- Sempre **execute** o teste após o stub para ver o vermelho.  
- Aplique o **hard-coded** apenas para salvar tempo; remova-o assim que possível.  
- **Evolua** testes gradualmente, cobrindo entradas, erros e múltiplos cenários.  
- Documente em comentário o **próximo passo** após cada “verde”.

### 🌐 Cenários Reais de Negócio  
- **E-commerce:** stub de cálculo de frete para passar teste de fluxo de compra inicial.  
- **Fintech:** hard-code de valor de juros em teste antes de conectar cálculo real.  
- **SaaS B2B:** simular retorno “OK” em endpoint de configuração antes de integrar serviço externo.  
- **IoT:** retornar valor fixo de sensor no stub antes de conectar hardware real.

---

## 📝 Exercícios de Fixação

1. Em até três linhas, explique por que criamos stubs vazios antes de implementar lógica.  
2. Qual a vantagem de passar um teste com código “hard-coded” antes de refinar a solução?  
3. Descreva em linguagem natural o próximo teste que você escreveria para forçar a substituição dinâmica de `${name}`.

---

## 🏆 Soluções

1. Stubs garantem compilação e permitem executar o teste falho, confirmando que o ambiente de teste está correto.  
2. Hard-code dá feedback instantâneo (“verde”), mantendo o ciclo ágil e indicando com clareza onde avançar.  
3. Próximo teste:  
Dado o template "Hello, ${name}" Quando definir name="Alice" Então evaluate() deve retornar "Hello, Alice"