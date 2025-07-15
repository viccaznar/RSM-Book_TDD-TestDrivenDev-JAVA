# 📒 Capítulo 2.3.2: Esgotando os Hacks Falsos 🧪

## 📝 Tradução do Texto

É hora de escrever um teste para múltiplas variáveis em um template. Este é o teste número 2 na nossa lista. Adicionando ao `TestTemplate`:

```java
@Test
public void multipleVariables() throws Exception {
   Template template = new Template("${one}, ${two}, ${three}");
   template.set("one", "1");
   template.set("two", "2");
   template.set("three", "3");
   assertEquals("1, 2, 3", template.evaluate());
}
```

Esse teste falha, pois a nossa expressão regular só busca ${name}. Para avançar rápido, podemos fazer um loop de busca-e-substituição para cada par (nome, valor) conhecido. Preocupações com valores que contenham padrões ${x} virão depois; por enquanto, anotamos essa limitação como novo teste:

Teste lembrança: avaliar "${one}, ${two}, ${three}" com valores "1", "${foo}", "3" deve resultar em "1, ${foo}, 3".

Depois, implementamos o mínimo para passar:

java
public class Template {
   private Map<String,String> variables;
   private String templateText;

   public Template(String templateText) {
      this.variables = new HashMap<>();
      this.templateText = templateText;
   }
   public void set(String name, String value) {
      this.variables.put(name, value);
   }
   public String evaluate() {
      String result = templateText;
      for (Map.Entry<String,String> entry : variables.entrySet()) {
         String regex = "\\$\\{" + entry.getKey() + "\\}";
         result = result.replaceAll(regex, entry.getValue());
      }
      return result;
   }
}
Com isso, voltamos ao verde sem refatorar ainda. Nos restam três testes na lista, e o próximo (unknownVariablesAreIgnored) já passa sem mudanças. Antes de avançar, é bom falhar intencionalmente para garantir que o teste realmente executa.

🧠 Raciocínio Contido no Texto
Para manter o fluxo, usamos hacks (regex hard-coded) até o próximo teste falhar.

Escrever testes que expõem deficiências (triangulação) guia a evolução do código.

Registrar limitações como novos testes mantém o foco num passo só de cada vez.

A busca-e-substituição por mapas de variáveis resolve múltiplos placeholders de forma rápida e simples.

📚 Conceitos Explicativos
🔢 1. Teste para Múltiplas Variáveis
Resumo Crie testes que validem templates com diversas variáveis, forçando a lógica a lidar com mais de um placeholder.

Exemplo Lúdico É como testar um misturador de cores: primeiro você mistura vermelho+azul, depois adiciona verde e espera uma nova cor. Cada adição é um teste que confirma que o misturador funciona.

🎯 2. Triangulação de Testes
Resumo Adicione novos testes que derrubem hacks anteriores, empurrando a implementação para a solução real.

Exemplo Lúdico Pense num marinheiro que navega por estrelas: traça duas referências (triangulação) para garantir a rota exata, ajustando sempre que uma estrela desaparece.

⚙️ 3. Hack Rápido com Regex e Map
Resumo Use replaceAll em loop sobre HashMap de variáveis para passar testes sem parser completo.

Exemplo Lúdico É como usar cola quente para juntar móveis provisórios: resolve rapidinho, mas depois você troca por parafusos para ficar firme.

📝 4. Documentar Limitações como Testes
Resumo Quando notar uma deficiência (por exemplo, valores contendo ${x}), crie um teste que espera o comportamento correto em vez de consertar tudo de uma vez.

Exemplo Lúdico É como anotar no roteiro de um filme: “na cena 5, preciso de um dublê para piruetas” antes de focar na cena inteira, garantindo que nada seja esquecido.

🌟 Capítulo 2.4: Boas Práticas & Cenários Reais 💼
✅ Boas Práticas
Mantenha uma lista viva de testes: cada nova deficiência vira um teste.

Aplique hacks localizados (hard-coded) até o teste correspondente falhar.

Use triangulação: para cada valor fake que passar, crie outro teste com valor diferente.

Refatore logo após o conjunto de testes verdes, extraindo parsing genérico.

Documente via comentário o próximo passo para remover o hack.

Insista em ver o vermelho antes do verde ao adicionar novos testes.

🌐 Cenários Reais em Negócios
E-commerce: templates de carrinho com várias variáveis (itens, quantidades, preços) e ignorar campos extras na API.

Fintech: geração de extratos com múltiplas linhas de transação, substituindo placeholders de data, valor e descrição.

SaaS B2B: notificações personalizadas para clientes, variando dados de contato, nome da empresa e assinatura.

IoT: dashboards que mostram leituras de diversos sensores, ignorando IDs não configurados.

📝 Exercícios de Fixação
Explique em até três linhas por que criar testes que expõem hacks (triangulação) é crucial no TDD.

Cite dois potenciais problemas de usar replaceAll com regex para parsing de templates.

Escreva um teste (linguagem natural) que force o motor a ignorar variáveis desconhecidas e preservar placeholders não preenchidos.

🏆 Soluções
A triangulação adiciona cenários que quebram implementações temporárias, forçando melhorias graduais e evitando soluções monolíticas.

Valores contendo {$...} podem ser substituídos indevidamente.

Regex complexas podem não capturar todos os formatos ou escapar caracteres especiais.

Cenário:

Dado o template "Valor: ${amount}, Desconto: ${discount}, Total: ${total}"  
Quando definir amount="100" e total="90" (sem definir discount)  
Então evaluate() deve retornar "Valor: 100, Desconto: ${discount}, Total: 90"  
java
@Test
public void unknownPlaceholdersRemain() throws Exception {
    Template tpl = new Template("Valor: ${amount}, Desconto: ${discount}, Total: ${total}");
    tpl.set("amount", "100");
    tpl.set("total", "90");
    assertEquals("Valor: 100, Desconto: ${discount}, Total: 90", tpl.evaluate());
}