# 🎯 Capítulo 2.6.2: Um Impasse de Design se Aproxima ⚠️

## 📝 Tradução do Texto

Em relação ao teste restante para valores de variáveis que contêm “${” e “}”, as coisas começam a ficar mais difíceis. Primeiro, não podemos continuar fazendo busca-e-substituição várias vezes, pois valores de variável renderizados primeiro poderiam ser reprocessados em rodadas posteriores. Além disso, não podemos mais confiar em detectar variáveis faltantes apenas procurando “${…}” no resultado.

Antes de especularmos demais, vamos escrever um teste que comprove nossas suposições sobre o comportamento atual. Adicione ao `TestTemplate`:

```java
@Test
public void variablesGetProcessedJustOnce() throws Exception {
   template.set("one", "${one}");
   template.set("two", "${three}");
   template.set("three", "${two}");
   assertTemplateEvaluatesTo("${one}, ${three}, ${two}");
}
```

# 🎯 Capítulo 2.6.2: Um Impasse de Design se Aproxima ⚠️

## 📝 Tradução do Texto

Em relação ao teste restante para valores de variáveis que contêm “${” e “}”, as coisas começam a ficar mais difíceis. Primeiro, não podemos continuar fazendo busca-e-substituição várias vezes, pois valores de variável renderizados primeiro poderiam ser reprocessados em rodadas posteriores. Além disso, não podemos mais confiar em detectar variáveis faltantes apenas procurando “${…}” no resultado.

Antes de especularmos demais, vamos escrever um teste que comprove nossas suposições sobre o comportamento atual. Adicione ao `TestTemplate`:

```java
@Test
public void variablesGetProcessedJustOnce() throws Exception {
   template.set("one", "${one}");
   template.set("two", "${three}");
   template.set("three", "${two}");
   assertTemplateEvaluatesTo("${one}, ${three}, ${two}");
}
