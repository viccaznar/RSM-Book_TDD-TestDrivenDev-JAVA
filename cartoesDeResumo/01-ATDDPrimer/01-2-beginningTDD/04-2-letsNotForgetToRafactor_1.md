# 🎨 Capítulo 2.4: Não Esqueça de Refatorar Testes 🛠️

## 📜 Tradução do Texto

Ainda não refatoramos nada, mesmo tendo escrito bastante código. A razão aparente é que não identificamos nada para refatorar. Mas refatoração não vale só para código de produção — vale também para nosso código de teste, que pode “apodrecer” e causar dor de cabeça depois.  

A listagem abaixo mostra nossa classe de testes até agora. Encontre duplicações, redundâncias semânticas ou qualquer “cheiro” de código que mereça limpeza:

```java
public class TestTemplate {
   @Test
   public void oneVariable() throws Exception {
       Template template = new Template("Hello, ${name}");
       template.set("name", "Reader");
       assertEquals("Hello, Reader", template.evaluate());
   }
   @Test
   public void differentTemplate() throws Exception {
       template = new Template("Hi, ${name}");
       template.set("name", "someone else");
       assertEquals("Hi, someone else", template.evaluate());
   }
   @Test
   public void multipleVariables() throws Exception {
       Template template = new Template("${one}, ${two}, ${three}");
       template.set("one", "1");
       template.set("two", "2");
       template.set("three", "3");
       assertEquals("1, 2, 3", template.evaluate());
   }
   @Test
   public void unknownVariablesAreIgnored() throws Exception {
       Template template = new Template("Hello, ${name}");
       template.set("name", "Reader");
       template.set("doesnotexist", "Hi");
       assertEquals("Hello, Reader", template.evaluate());
   }
}
```

Identificamos repetições ao instanciar Template e chamadas a evaluate(). Também usamos o mesmo texto de template em vários testes. Se separássemos fixtures (estados iniciais) em classes diferentes, teríamos duas classes de testes, mas existe outra refatoração possível.

## 🧠 Raciocínio Contido no Texto

- Código de teste é tão suscetível a “code rot” quanto o de produção e requer limpeza periódica.

- Duplicação e redundância em testes dificultam manutenção e evolução.

- Consolidar setup comum em fixtures evita repetição e destaca diferenças entre cenários.

- Refatoração de testes fortalece a confiança no ciclo TDD, tornando falhas e sucessos mais claros.

## 📚 Conceitos Explicativos

### 🔄 1. Testes Têm “Code Rot”

Testes envelhecem: duplicações e detalhes obsoletos atrapalham a clareza.

Manter testes limpos é tão importante quanto manter o código de produção em dia.

  - **Exemplo Lúdico:** É como uma horta: se não arrancar as ervas daninhas (duplicações), elas crescem e sufocam as plantas boas (casos de teste).

### 🔍 2. Duplicação de Setup

- Instanciar Template várias vezes e usar literais repetidos é sinal de fixture mal organizada.

- Extrair o setup para um método ou campo compartilhado elimina repetição.

  - **Exemplo Lúdico:** Imagine quatro cozinheiros preparando o mesmo bolo em fornos diferentes, cada um misturando ingredientes do zero. É muito mais eficiente reunir a massa pronta e distribuir em assadeiras separadas.

### 🎯 3. Redundância de Chamadas

- Invocar `evaluate()` em cada `assertEquals` repete lógica de verificação.

- Extrair em helper method clarifica o propósito de cada teste.

  - **Exemplo Lúdico:** Pense num árbitro de futebol que marca todos os gols no apito em vez de apitar a cada jogada — mais simples e focado no resultado.

### 📦 4. Fixtures Bem Definidas

- `Fixture`: estado inicial comum a vários testes (instâncias e configurações).

- Use anotações como `@Before` para preparar o cenário antes de cada teste.

  - **Exemplo Lúdico:** É como preparar kits de ferramentas para diferentes tarefas: cada kit vem pronto, sem que você precise montar cada parafuso na hora de usar.

## 💼 Capítulo 2.5: Boas Práticas & Cenários Reais 🌟

### ✅ Boas Práticas

- Extraia setup repetido para um campo de instância ou método `@Before`.

- Crie helper methods para chamadas frequentes a `evaluate()`.

- Use variáveis de classe para textos de template comuns, nomeando-as claramente.

- Mantenha testes pequenos, focados e sem dependências entre si.

- Periodicamente revise testes antigos para remover duplicações e atualizar fixtures.

- Considere `@ParameterizedTest` para cenários que variam apenas dados de entrada.

### 🌍 Cenários Reais em Negócios

- **E-commerce:** fixtures para “template de e-mail de boas-vindas” e “template de recuperação de senha”, evitando reescrever setup em cada teste.

- **Fintech:** testes de relatórios financeiros usam fixtures de dados pré-carregados com transações comuns.

- **SaaS B2B:** painéis de controle compartilham configuração de usuário e permissões em fixtures antes de cada caso de teste.

- **IoT:** simulações de rede criam fixtures com sensores ativos, reaproveitadas em diferentes testes de protocolo.

## 📝 Exercícios de Fixação

1. Em até três linhas, explique por que extrair fixtures melhora a legibilidade dos testes.

2. Identifique na listagem mostrada duas duplicações que podem ser refatoradas.

3. Proponha um helper method em pseudo-código para criar e configurar uma instância de Template com um dado texto.

## 🏆 Soluções

1. Extrair fixtures centraliza o setup, elimina repetição e torna claro o estado inicial de cada teste, facilitando manutenção.

2. Instância `new Template("Hello, ${name}")` aparece em `oneVariable` e `unknownVariablesAreIgnored`.

3. Chamadas repetidas a `template.evaluate()` dentro de `assertEquals`.

### Exemplo de helper (Java):

```java
private Template makeTemplate(String text, Map<String,String> vars) {
    Template tpl = new Template(text);
    for (Map.Entry<String,String> e : vars.entrySet()) {
        tpl.set(e.getKey(), e.getValue());
    }
    return tpl;
}
```

// Uso em teste
```java
@Test
public void oneVariableWithHelper() {
    Map<String,String> vars = Map.of("name", "Reader");
    Template tpl = makeTemplate("Hello, ${name}", vars);
    assertEquals("Hello, Reader", tpl.evaluate());
}