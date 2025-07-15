# 📘 Capítulo 2.5.3: Mantendo Métodos Equilibrados ⚖️

## 📝 Tradução do Texto

Uma propriedade que afeta muito a legibilidade é a consistência do nível de abstração dentro de um método. No nosso `evaluate`, temos:

```java
public String evaluate() {
   String result = templateText;
   for (Entry<String, String> entry : variables.entrySet()) {
       String regex = "\\$\\{" + entry.getKey() + "\\}";
       result = result.replaceAll(regex, entry.getValue());
   }
   checkForMissingValues(result);
   return result;
}
```

Aqui evaluate faz duas coisas em níveis diferentes: substituir placeholders (baixo nível) e checar valores faltantes (alto nível). Misturar ambos torna o método confuso.

A solução é aplicar Extract Method novamente, separando responsabilidades:

java
public String evaluate() {
   String result = replaceVariables();
   checkForMissingValues(result);
   return result;
}

private String replaceVariables() {
   String result = templateText;
   for (Entry<String, String> entry : variables.entrySet()) {
       String regex = "\\$\\{" + entry.getKey() + "\\}";
       result = result.replaceAll(regex, entry.getValue());
   }
   return result;
}

private void checkForMissingValues(String result) {
   if (result.matches(".*\\$\\{.+\\}.*")) {
       throw new MissingValueException();
   }
}
Nossos testes continuam verdes, garantindo que a refatoração não quebrou nada.

🧠 Raciocínio Contido no Texto
Métodos devem operar em um único nível de abstração para manter clareza.

Extrair partes do método em funções específicas melhora o equilíbrio e a legibilidade.

Refatorações são seguras com testes cobrindo o comportamento antes e depois.

Ferramentas de refatoração (Extract Method) agilizam a separação de responsabilidades.

📚 Conceitos Explicativos
🎯 1. Equilíbrio de Abstração
Resumo Métodos claros misturam poucos níveis de detalhe, mantendo coerência entre suas instruções.

Exemplo Lúdico É como ouvir música: um álbum temfaixas no mesmo estilo; misturar jazz, rock e funk na mesma música soa confuso. Cada método deve “tocar” um estilo só.

✂️ 2. Extract Method Revisitado
Resumo Extraia blocos logicamente agrupados em novos métodos com nomes descritivos (replaceVariables), organizando fluxos no método principal.

Exemplo Lúdico Pense num cineasta que grava cenas de ação e drama em sets diferentes e só depois edita o filme, unindo cenas de forma coesa.

🔄 3. Segurança pela Suíte de Testes
Resumo Testes garantem que refatorações não alterem o comportamento externo, permitindo ousar mudanças internas.

Exemplo Lúdico É como tunar um carro: você troca peças internas (motor, suspensão) sabendo que o teste de aceleração e frenagem ainda será executado para validar a performance.

💼 Capítulo 2.6: Boas Práticas & Cenários Reais 🌟
✅ Boas Práticas
Mantenha um nível de abstração por método.

Use Extract Method sempre que detectar saltos de abstração.

Verifique o funcionamento com testes antes e depois de cada refatoração.

Nomeie métodos extraídos de forma clara, revelando a responsabilidade de cada um.

Utilize IDEs para automatizar extrações e renomeações, minimizando erros.

🌐 Cenários Reais em Negócios
E-commerce: processOrder() chama validateOrder() e dispatchOrder(), sem misturar detalhes de estoque.

Fintech: generateReport() extrai fetchTransactions(), calculateTotals() e formatOutput() em métodos distintos.

SaaS B2B: authenticateUser() separa checkCredentials(), loadPermissions() e createSession().

IoT: readSensorData() extrai connectToSensor(), parseData() e validateReadings() para manter clareza.

📝 Exercícios de Fixação
Em até três linhas, explique por que manter um nível de abstração único por método é importante.

Descreva como a refatoração Extract Method melhora o equilíbrio de evaluate().

Cite uma parte do método evaluate() que, em outro contexto, poderia formar um método separado.

🏆 Soluções
Um método com nível de abstração consistente é mais fácil de entender, evitando misturar lógica de negócio e detalhes de implementação.

Extract Method remove o loop de substituição para replaceVariables(), deixando evaluate() focado no fluxo de alto nível: preencher e validar.

O trecho de validação de exceções (if (result.matches(...)) throw ...) poderia formar um método validateNoMissingPlaceholders(String).

java
private void validateNoMissingPlaceholders(String text) {
    if (text.matches(".*\\$\\{.+\\}.*")) {
        throw new MissingValueException();
    }
}