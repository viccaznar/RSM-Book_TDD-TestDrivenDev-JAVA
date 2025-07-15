# 📗 Capítulo 2.5: Adicionando Tratamento de Erros 🛡️

## 📝 Tradução do Texto

Chegou a hora de adicionar um novo teste: aquele que verifica se o motor de templates dispara um erro quando sobra variável sem valor. Primeiro escrevemos o teste, depois fazemos passar, e por fim refatoramos.

### 2.5.1 Esperando uma Exceção 💣

Como testar com JUnit se um método lança uma exceção? Usamos `try/catch` para capturar o comportamento esperado:

```java
@Test
public void missingValueRaisesException() throws Exception {
    try {
        new Template("${foo}").evaluate();
        fail("evaluate() deve lançar MissingValueException se faltar valor para variável!");
    } catch (MissingValueException expected) {
    }
}
```

Chamamos fail(...) logo após evaluate() para garantir que, se chegarmos lá, falhamos o teste. Se evaluate() lançar MissingValueException, o catch intercepta e o teste passa.

Com JUnit 4 podemos usar a sintaxe de anotação, simplificando:

java
@Test(expected = MissingValueException.class)
public void missingValueRaisesException() throws Exception {
    new Template("${foo}").evaluate();
}
A anotação valida apenas o tipo da exceção. Para checar mensagem ou detalhes, use try/catch; para verificar só o tipo, a anotação é mais sucinta.

2.5.2 Fazendo o Teste Passar Rapidamente ✅
Precisamos fazer evaluate() detectar variáveis não definidas. Um hack rápido é verificar, ao final do replaceAll, se ainda há padrões ${...} na string e lançar a exceção:

java
public String evaluate() {
    String result = templateText;
    for (Map.Entry<String,String> entry : variables.entrySet()) {
        String regex = "\\$\\{" + entry.getKey() + "\\}";
        result = result.replaceAll(regex, entry.getValue());
    }
    if (result.matches(".*\\$\\{.+\\}.*")) {
        throw new MissingValueException();
    }
    return result;
}
Esse código retorna ao “verde” rapidamente, embora ainda precise de refatoração para melhorar clareza e robustez.

🧠 Raciocínio Contido no Texto
Testar exceções é tão importante quanto testar comportamentos “verdes”.

try/catch versus anotação: escolha a abordagem certa para seu nível de inspeção.

Hack de regex detecta placeholders restantes e garante feedback imediato.

Ciclo Red–Green–Refactor mantém progresso ágil antes de refinamentos.

📚 Conceitos Explicativos
🎯 1. Testando Exceções
Resumo Verificar se comportamento anômalo (variável sem valor) dispara a exceção esperada.

Exemplo Lúdico Imagine um detetive que entra numa sala trancada. Se a porta não girar, ele lança um alarme (exceção). Se a porta girar normalmente, algo deu errado no teste — ele esperava o alarme.

⚡ 2. Anotação expected vs try/catch
Resumo

@Test(expected=Excecao.class): válido para checar só o tipo.

try/catch: permite inspeção detalhada da mensagem e propriedades da exceção.

Exemplo Lúdico É como usar um sinalizador automático (anotação) que dispara sirene só por tipo de emergência, versus ter um policial (try/catch) que verifica armamento e voz do suspeito antes de prender.

🔍 3. Hack de Detecção de Placeholders
Resumo Após substituir variáveis conhecidas, detecte padrões remanescentes ${...} e lance erro.

Exemplo Lúdico É como um inspetor de bagagens que, depois de remover itens suspeitos, faz um raio-x final. Se ainda vê algo estranho, toca o alarme.

🛠️ 4. Refatoração Pós-Hack
Resumo Depois do primeiro “verde”, quebre evaluate() em métodos menores: parsing, substituição e validação de leftovers.

Exemplo Lúdico Pense num chef que, após provar a sopa pronta (hack), separa as tarefas: cortar legumes, cozinhar e ajustar tempero—tudo em etapas claras.

💼 Capítulo 2.6: Boas Práticas & Cenários Reais 🌟
✅ Boas Práticas
Escolha @Test(expected=...) para checar só o tipo; use try/catch quando precisar inspecionar detalhes da exceção.

Sempre rode o teste novo e veja o vermelho antes do verde para confirmar a execução.

Anote como novos testes os casos de valores inválidos ou placeholders especiais.

Após a entrega rápida, extraia métodos de parsing, substituição e validação em evaluate().

Documente no teste a razão da exceção e contexto do erro para facilitar manutenção.

🌐 Cenários Reais em Negócios
E-commerce: disparar MissingValueException se o email de confirmação usar ${orderId} sem definir o pedido, evitando envios incompletos.

Fintech: lançar erro ao gerar extrato com ${accountNumber} indefinido, prevenindo relatórios incorretos.

SaaS B2B: bloquear envio de alertas com ${userEmail} ausente, garantindo dados de contato.

IoT: sinalizar erro se ${sensorId} não for configurado, evitando leituras inválidas.

📝 Exercícios de Fixação
Explique em até três linhas a diferença entre usar anotação expected e try/catch para testar exceções.

Descreva um cenário (em linguagem natural) em que é crucial lançar MissingValueException.

Em Java, escreva um teste usando anotação para verificar que ${date} sem valor dispara a exceção.

🏆 Soluções
A anotação expected verifica apenas o tipo de exceção; try/catch permite inspeção adicional da instância lançada (mensagem, causa etc.).

Cenário: “Ao enviar e-mail de redefinição de senha com template ‘Temporário: ${tempPass}’, sem definir tempPass, deve lançar MissingValueException para impedir envio de mensagem incompleta.”

Código de teste em Java:

java
@Test(expected = MissingValueException.class)
public void datePlaceholderMissingThrows() throws Exception {
    new Template("Data: ${date}").evaluate();
}
```