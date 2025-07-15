# 🚀 Capítulo 2.2: Escolhendo o Primeiro Teste 🎯

## 📝 Tradução do Texto

Conforme prometido, vamos desenvolver um motor de templates usando desenvolvimento guiado por testes (TDD). Para não dar uma mordida grande demais, vamos focar apenas na lógica de negócios do motor de templates, sem nos preocupar com todo o sistema que o utiliza para gerar e-mails personalizados.

Dica: abra seu IDE favorito e acompanhe passo a passo. Nada substitui a experiência prática!

O motor de templates deve ler um texto estático que contém marcadores de variáveis (como `${name}`), receber valores para esses marcadores e, ao renderizar, substituir cada placeholder pelo valor correspondente.

Tudo certo? Vamos em frente! Primeiro, transformaremos a descrição do motor de templates em uma lista inicial de testes e escolheremos um deles para implementar.

---

## 🧠 Raciocínio Contido no Texto

- **Pequenos passos**: dividir a implementação em testes reduz complexidade e mantém o foco.  
- **Requisitos ≠ Testes**: requisitos descrevem comportamento genérico; testes descrevem cenários específicos e executáveis.  
- **Teste como critério de “feito”**: só sabemos que concluímos quando o teste associado passa.  
- **Lista viva de testes**: adicionamos novos testes à medida que surgem casos de uso ou bugs descobertos.  
- **Programação por intenção**: imaginamos a API ideal ao escrever o teste, guiando a implementação.

---

## 📚 Conceitos Explicativos

### 📝 1. Lista Inicial de Testes

Resumo  
- Transformar requisitos genéricos em testes concretos e executáveis.  
- Cada teste valida um cenário de uso específico.

Exemplo Lúdico  
É como desenhar um mapa do tesouro dividindo a rota em marcos: “na caverna, vire à esquerda e cave até encontrar um baú.” Cada marco é um teste que, quando passa, confirma que seguimos pelo caminho certo.

---

### 🔀 2. Requisitos vs. Testes

Resumo  
- Requisitos: “o sistema substitui placeholders `${firstname}` e `${lastname}`.”  
- Testes: “`'Olá, ${name}'` com `name='Maria'` resulta em `'Olá, Maria'`.”

Exemplo Lúdico  
Compare com dar instruções em abstrato (“vá até o lago”) versus definir passos claros (“andar 100 metros para norte, virar a leste e pegar a pedra verde”).

---

### 🔄 3. Transformando Requisitos em Testes

Resumo  
- Liste cenários detalhados: casos felizes, erros esperados e comportamentos ignorados.  
- Escreva frases que descrevem entrada, ação e resultado esperado.

Exemplo Lúdico  
É como escrever receitas: em vez de “cozinhe arroz”, descreva “para 1 xícara de arroz, adicione 2 xícaras d’água; após ferver, mantenha em fogo baixo por 15 minutos”.

---

### 🚧 4. Escrevendo o Primeiro Teste Falho

Resumo  
- Crie o esqueleto da classe de teste e o método de teste.  
- Compile e execute para confirmar a falha inicial (ver teste vermelho).

Exemplo Lúdico  
É como plantar uma semente: a primeira semente não brota de imediato — você confirma que o solo está pronto antes de regar.

---

### 💡 5. Programação por Intenção

Resumo  
- Imagine a API perfeita e escreva o teste como se o código já existisse.  
- A implementação deve se moldar à intenção desenhada no teste.

Exemplo Lúdico  
Pense num **arquiteto** que rabisca o prédio ideal no papel antes de erguer qualquer parede. Ele guia a construção conforme sua visão clara, não conforme limitações iniciais.

```java
// Java + JUnit
import org.junit.Test;
import static org.junit.Assert.*;

public class TestTemplate {
    @Test
    public void oneVariable() throws Exception {
        Template template = new Template("Hello, ${name}");
        template.set("name", "Reader");
        assertEquals("Hello, Reader", template.evaluate());
    }
}
```

💼 Capítulo 2.3: Boas Práticas & Cenários Reais 🌟
✅ Boas Práticas
Mantenha lista de testes derivada diretamente de requisitos.

Escolha sempre o teste de menor esforço ou maior valor para iniciar.

Compile e execute imediatamente para ver o teste falhar antes de codificar.

Use mocks e stubs para isolar dependências e manter testes rápidos.

Escreva comentários breves nos testes para explicar o cenário e a intenção.

Atualize a lista de testes continuamente com novos casos encontrados em produção.

🌐 Cenários Reais em Negócios
E-commerce: validar “Hello, ${customer}” antes de implementar todo fluxo de descontos.

Fintech: checar “${amount} + ${tax} com amount=100, tax=0.05 resulta em 105” antes de criar relatórios completos.

SaaS B2B: testar “setConfig(key, value) retorna sucesso” antes de desenvolver interface de administração.

IoT: verificar “readSensor('temp') retorna número dentro do intervalo” antes de processar rede de vários sensores.

📝 Exercícios de Fixação
Em até três linhas, explique por que test-first exige compilar e executar o teste antes de escrever código de produção.

Cite dois critérios para escolher qual teste implementar primeiro.

Escreva um teste atômico e isolado (em linguagem natural) para cenário de template com duas variáveis: saudação e nome.

🏆 Soluções
Compilar e rodar o teste inicialmente confirma que ele falha por falta de implementação, reforçando o ciclo Test-Red-Green e garantindo ambiente de teste configurado.

Facilidade de implementação (baixo esforço).

Valor de negócio (alto impacto nas funcionalidades principais).

Cenário “Duas Variáveis”:

Dado o template "Olá, ${greeting} ${name}!"  
Quando definir greeting="Bem-vindo" e name="Ana"  
Então evaluate() deve retornar "Olá, Bem-vindo Ana!"  