# 📘 Capítulo 2.4.2: Removendo Teste Redundante 🗑️

## 📝 Tradução do Texto

Há um tipo mais fundamental de duplicação em nossos testes `oneVariable`, `differentTemplate` e `multipleVariables`. Pensando bem, o teste de múltiplas variáveis cobre o de variável única, então podemos remover `oneVariable` se adicionarmos um teste que verifique a reavaliação após mudar o valor de uma variável. Além disso, podemos usar o mesmo template de `multipleVariables` em `unknownVariablesAreIgnored` e talvez eliminar `differentTemplate` também. A listagem 2.13 mostra os testes refatorados:

> "```java  
> import org.junit.Test;  
> import org.junit.Before;  
> import static org.junit.Assert.*;  
> public class TestTemplate {  
>    private Template template;  
>    @Before  
>    public void setUp() throws Exception {  
>        template = new Template("${one}, ${two}, ${three}");  
>        template.set("one", "1");                             
>        template.set("two", "2");                             
>        template.set("three", "3");                           
>    }  
>    @Test  
>    public void multipleVariables() throws Exception {  
>        assertTemplateEvaluatesTo("1, 2, 3");        
>    }  
>    @Test  
>    public void unknownVariablesAreIgnored() throws Exception {  
>        template.set("doesnotexist", "whatever");  
>        assertTemplateEvaluatesTo("1, 2, 3");       
>    }  
>    private void assertTemplateEvaluatesTo(String expected) {  
>        assertEquals(expected, template.evaluate());  
>    }  
> }  
> ```"

Agora todos os testes usam o mesmo fixture e focam apenas no essencial.

---

## 🧠 Raciocínio Contido no Texto

- Remover testes redundantes reduz manutenção e clarifica a suíte de testes.  
- Unificar fixtures com `@Before` centraliza setup, eliminando duplicações.  
- Helpers como `assertTemplateEvaluatesTo` extraem lógica de verificação repetida.  
- Testes minimalistas focam só no aspecto único de cada caso, facilitando evolução.

---

## 📚 Conceitos Explicativos

### 🔍 1. Identificando Testes Redundantes  
Resumo  
- Quando um teste abrange totalmente outro, o segundo torna-se dispensável.  
- Remover testes duplicados simplifica a suite sem perder cobertura.

Exemplo Lúdico  
É como ter duas lâmpadas acendendo a mesma sala; apagar uma não deixará a sala escura, apenas economiza energia.

---

### 🧩 2. Unificação de Fixture  
Resumo  
- Extrair setup comum para `@Before` reduz cópia-cola de instâncias e dados.  
- Testes passam a herdar o mesmo estado inicial, facilitando alterações no futuro.

Exemplo Lúdico  
Imagine quatro pintores começando do mesmo esboço de tela em vez de desenharem cada um uma cópia completa do esboço — ganha-se rapidez e consistência.

---

### 🛠️ 3. Uso de Helpers nos Testes  
Resumo  
- Criar métodos auxiliares para chamadas repetidas (`assertTemplateEvaluatesTo`) limpa os testes.  
- Helpers documentam intenção e encapsulam detalhes de verificação.

Exemplo Lúdico  
É como usar um atalho de teclado em vez de vários cliques: a tarefa se torna mais rápida e menos propensa a erros.

---

## 💼 Capítulo 2.5: Boas Práticas & Cenários Reais 🌟

### ✅ Boas Práticas

- Revise sua suite de testes em busca de **redundâncias** após adicionar novos casos.  
- Extraia **fixtures** comuns com `@Before` para centralizar configuração.  
- Utilize **métodos auxiliares** para asserções frequentes, mantendo testes enxutos.  
- Garanta que cada teste cubra um **aspecto único** do comportamento.  
- Periodicamente rode ferramentas de **detecção de duplicação** em testes.  
- Considere **Parameterized Tests** para cenários que variam apenas dados de entrada.

### 🌐 Cenários Reais em Negócios

- **E-commerce:** unificar fixtures de templates de email de confirmação, evitando reescrever setup em cada teste.  
- **Fintech:** remover testes redundantes de cálculo de juros, mantendo só casos extremos e representativos.  
- **SaaS B2B:** usar helpers para verificar resultados de geração de relatórios, em vez de repetir `assertEquals` com payloads grandes.  
- **IoT:** centralizar simulação de leituras de sensores em fixture comum, removendo duplicações em testes de processamento.

---

## 📝 Exercícios de Fixação

1. Explique em até três linhas por que remover testes redundantes é importante para a manutenção.  
2. Cite dois benefícios de unificar o setup de testes usando `@Before`.  
3. Escreva em pseudocódigo um helper method que crie e configure um `Template` para testes com três variáveis.

---

## 🏆 Soluções

1. Eliminar redundâncias reduz o esforço de atualização quando requisitos mudam e torna a suite mais legível e rápida de executar.  
2.  
   - Centraliza alterações no estado inicial em um único ponto.  
   - Reduz cópia e colagem, diminuindo o risco de inconsistências.  
3.  
```java
// Uso em Java
private Template makeTemplate(Map<String,String> vars) {
    Template tpl = new Template("${one}, ${two}, ${three}");
    vars.forEach((k,v) -> tpl.set(k, v));
    return tpl;
}