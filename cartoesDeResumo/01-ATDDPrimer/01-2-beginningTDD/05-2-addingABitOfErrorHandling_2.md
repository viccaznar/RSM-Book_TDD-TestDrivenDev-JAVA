# 📘 Capítulo 2.5.2: Refatorando para Métodos Menores 🛠️

## 📝 Tradução do Texto

Há diferenças no tamanho de métodos e classes que as pessoas preferem. Eu? Sinto-me confortável com menos de 10 linhas de código Java por método. Acima disso, começo a suspeitar que posso extrair algo ou mover para outro lugar. Além disso, o método `evaluate` está quase fazendo duas coisas: substituir variáveis e checar valores faltantes. Acho que já passou do limite.

Vamos aplicar um pouco de mágica de refatoração em `evaluate` para deixá-lo mais limpo. Podemos, ao menos, extrair o bloco que checa valores faltantes para um método próprio. A listagem 2.16 mostra a versão refatorada:

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
  
private void checkForMissingValues(String result) {  
    if (result.matches(".*\\$\\{.+\\}.*")) {  
        throw new MissingValueException();  
    }  
}  
```

Muito melhor: tiramos um if inteiro de `evaluate`. Mas agora o método está menos equilibrado em nível de abstração. Vamos falar sobre **equilíbrio** antes de seguir.

---

## 🧠 Raciocínio Contido no Texto

- Métodos com muitas linhas ou responsabilidades misturadas tornam-se confusos e difíceis de manter.  
- Extrair funcionalidades em métodos auxiliares (Extract Method) melhora clareza e coesão.  
- Manter **níveis de abstração** consistentes num método evita saltos cognitivos.  
- Refatoração incremental (“baby steps”) preserva testes verdes e saúde do código.

---

## 📚 Conceitos Explicativos

### 🛡️ 1. Tamanho de Método Ideal  

Métodos curtos (≤ 10 linhas) são mais fáceis de entender e modificar; quando crescem demais, sinalizam oportunidade de decomposição.

  - **Exemplo Lúdico:** É como comer **docinhos**: porções pequenas são rápidas e satisfatórias. Um bolo inteiro de uma só vez acaba entupindo o estômago e gera desperdício.

---

### ✂️ 2. Extract Method (Extrair Método)  

Refatore blocos independentes de código em métodos com nomes claros, isolando responsabilidades.

  - **Exemplo Lúdico:** Pense num **chef** que primeiramente prepara o molho numa panela separada antes de adicioná-lo ao prato principal. Cada etapa é isolada e testada independentemente.

---

### ⚖️ 3. Níveis de Abstração Consistentes  

Dentro de um método, mantenha instruções no mesmo “andar” de detalhe: ou todas em alto nível (lógica de negócio) ou todas em baixo nível (detalhes de implementação).

  - **Exemplo Lúdico:** Imagine um **tradutor** que, numa frase, mistura palavras em três línguas diferentes. O leitor perde o fio. Um texto coeso fala uma só linguagem em cada parágrafo.

---

### 🔄 4. Ciclo Red–Green–Refactor  

Após cada teste “verde”, refatore imediatamente para melhorar estrutura, sem mudar comportamento.

  - **Exemplo Lúdico:** É como escalar montanha: a cada trecho vencido (teste verde), você ajusta equipamentos (refatoração) antes de avançar para o próximo degrau.

---

## 💼 Capítulo 2.6: Boas Práticas & Cenários Reais 🌟

### ✅ Boas Práticas

- Mantenha métodos com **menos de 10 linhas** ou até um nível de abstração único.  

- Use **Extract Method** para isolar lógicas diferenciadas (substituição vs validação).  

- Avalie a **coerência de abstração**: alto nível de negócio não deve misturar detalhes de regex.  

- Realize refatorações **curtas e frequentes**: um método por vez, preservando testes verdes.  

- Nomeie métodos auxiliares de forma **descritiva**, revelando intenção (`checkForMissingValues`).  

- Utilize ferramentas de **métricas de complexidade** (McCabe, Sonar) para detectar métodos grandes.

### 🌐 Cenários Reais em Negócios

- **E-commerce:** separar lógica de cálculo de frete e formatação de mensagem em métodos distintos para clareza.  

- **Fintech:** extrair regras de arredondamento e checagem de limites em métodos claros antes de compor relatório.  

- **SaaS B2B:** isolar autenticação e autorização em métodos especializados, mantendo controlador slim.  

- **IoT:** dividir parsing de protocolo e validação de dados de sensores em componentes menores e testáveis.

---

## 📝 Exercícios de Fixação

1. Explique em até três linhas por que métodos curtos e focados são mais fáceis de manter.  

2. Descreva o que é o refactoring **Extract Method** e cite um benefício.  

3. Considerando `evaluate()`, identifique um trecho que poderia formar um novo método de alto nível.

---

## 🏆 Soluções

1. Métodos curtos evitam sobrecarga cognitiva, facilitam compreensão e reduzem locais de erro, acelerando mudanças.  

2.  
   - **Extract Method**: isola um bloco de código em método próprio com nome claro.  
   - Benefício: melhora legibilidade, reutilização e facilita testes unitários de cada parte.  

3. Trecho sugerido para extração:  
```java


   // dentro de evaluate()
   String filled = replaceAllVariables(result);
   checkForMissingValues(filled);
   return filled;


// Exemplo de método extraído
private String replaceAllVariables(String text) {
    String result = text;
    for (Entry<String,String> entry : variables.entrySet()) {
        String regex = "\\$\\{" + entry.getKey() + "\\}";
        result = result.replaceAll(regex, entry.getValue());
    }
    return result;
}
``` 