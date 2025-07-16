# 📘 Capítulo 2.5.4: Esperando Detalhes de uma Exceção 🤔

## 📝 Tradução do Texto

Ao escrever o teste para valor faltante, apenas capturamos uma `MissingValueException` sem verificar detalhes. Não há nada mais frustrante que uma mensagem de exceção sem significado — quem nunca encarou um “java.lang.NullPointerException: null”? Neste caso, devemos incluir o nome da variável ausente na mensagem da exceção. Primeiro, ajustamos o teste:

```java
@Test
public void missingValueRaisesException() throws Exception {
    try {
        new Template("${foo}").evaluate();
        fail("evaluate() deveria lançar uma exceção se faltar valor para variável!");
    } catch (MissingValueException expected) {
        assertEquals("No value for ${foo}", expected.getMessage());
    }
}
```
Para satisfazer isso, mudamos checkForMissingValues para usar java.util.regex e capturar o placeholder faltante:

```java
import java.util.regex.Pattern;
import java.util.regex.Matcher;

private void checkForMissingValues(String result) {
    Matcher m = Pattern.compile("\\$\\{.+\\}").matcher(result);
    if (m.find()) {
        throw new MissingValueException("No value for " + m.group());
    }
}
```
E adicionamos um construtor em `MissingValueException` para receber a mensagem:

```java
public class MissingValueException extends RuntimeException {
    public MissingValueException(String message) {
        super(message);
    }
}
```
Assim, em poucos minutos criamos um teste mais rico em contexto e atendemos ao critério “verde”.

---

## 🧠 Raciocínio Contido no Texto

- Exceções devem fornecer informação útil para diagnóstico.
- Testar não só o tipo, mas também a mensagem da exceção aumenta a confiabilidade.
- Usar regex para extrair padrões remanescentes de placeholder é um hack rápido para detectar erros.
- Extender a classe de exceção com construtor que aceita mensagem personaliza o feedback.

---

## 📚 Conceitos Explicativos

### 🛡️ 1. Mensagens de Exceção Significativas

Exceções com mensagens claras agilizam a identificação de problemas em produção.

  - **Exemplo Lúdico:** É como um alarme de carro que toca “Porta traseira aberta” em vez de apenas “Alarme disparado”: você sabe exatamente onde corrigir antes de sair dirigindo.

---

### 🎯 2. Testando Detalhes de Exceção

Capturar a exceção em try/catch e verificar getMessage() valida o contexto do erro.

  - **Exemplo Lúdico:** Imagine um detetive que, ao prender um suspeito, não só confirma o crime, mas também registra a arma usada — informação vital para a investigação.

---

### 🔍 3. Regex para Detecção de Placeholders

Use Pattern e Matcher para encontrar padrões ${...} que sobraram após substituições.

  - **Exemplo Lúdico:** É como usar um detector de metais na praia: ele apita exatamente onde há algo enterrado, mesmo que outras áreas pareçam limpas.

---

### ⚙️ 4. Construtor Customizado na Exceção
    
Adicionar construtor que recebe String message capacita a exceção a transportar detalhes específicos.

  - **Exemplo Lúdico:** Pense num carta de reclamação que, em vez de “Pedido não entregue”, diz “Pedido #1234 não entregue” — informação direta e útil.

---

## 💼 Capítulo 2.6: Boas Práticas & Cenários Reais 🌟

### ✅ Boas Práticas

- Sempre adicione mensagem significativa a exceções esperadas.
- Use `@Test(expected=...)` só para checar tipo; para mensagem, use try/catch.
- Extraia placeholder faltante via regex ou parser adequado, não só hard-code.
- Inclua o nome da variável ou contexto relevante na mensagem.
- Documente testes de exceção com comentários explicando o motivo da verificação.
- Mantenha testes que validam tanto tipo quanto conteúdo da exceção para cobertura completa.

---

### 🌐 Cenários Reais em Negócios

- **E-commerce:** lançar `MissingValueException("No value for ${orderId}")` se o ID do pedido faltar em emails de confirmação.

- **Fintech:** gerar erro “No value for `${accountBalance}`” ao preparar extrato bancário sem saldo definido.

- **SaaS B2B:** disparar “No value for `${customerName}`” em notificações de renovação de contrato sem nome do cliente.

- **IoT:** indicar “No value for `${sensorId}`” quando configurar dashboards sem identificar o sensor.

### 📝 Exercícios de Fixação
  
1. Em até três linhas, explique por que testar também a mensagem da exceção é importante.

2. Escreva em linguagem natural um cenário de exceção que inclua o nome do campo faltante.

3. Em Java, crie um teste usando try/catch para verificar que ${date} faltante gera a mensagem “No value for ${date}”.

---

### 🏆 Soluções

1.  Mensagens claras aceleram a compreensão do erro, permitindo localizar rapidamente o ponto de falha e contexto específico.

2. Cenário: “Ao gerar relatório ‘Relatório de Vendas de ` ${month}`’, sem definir month, deve lançar MissingValueException com mensagem ‘No value for `${month}`’.”

3. 
```java
@Test
public void missingDateThrowsWithMessage() throws Exception {
    try {
        new Template("Date: ${date}").evaluate();
        fail("Esperava MissingValueException para `${date}` sem valor");
    } catch (MissingValueException ex) {
        assertEquals("No value for ${date}", ex.getMessage());
    }
}
```
