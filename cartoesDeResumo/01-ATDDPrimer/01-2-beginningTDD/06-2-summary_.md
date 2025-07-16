# 📓 Capítulo 2.7: Resumo do TDD ⏱️

## 📝 Tradução do Texto

O desenvolvimento guiado por testes (TDD) é uma técnica poderosa que nos ajuda a escrever software melhor e mais rápido. Isso ocorre ao focarmos no que é absolutamente necessário no momento, fazer essa pequena parte funcionar e, em seguida, limpar qualquer bagunça que tenhamos criado, mantendo a base de código saudável. Esse ciclo de primeiro escrever um teste, depois o código para fazê-lo passar e, por fim, refatorar o design faz uso intenso da programação por intenção — escrever o teste como se a implementação ideal já existisse — como ferramenta para criar designs usáveis e testáveis.  

Neste capítulo, vimos o TDD em ação, vivenciamos o ciclo de TDD e percebemos que nosso design atual do motor de templates ainda deixava a desejar. Partimos para construir o motor baseados em uma lista curta de testes que especificam o comportamento esperado e seguimos o ciclo teste-código-refatoração (ou vermelho-verde-refatorar) até o fim. O código já satisfaz a maioria dos nossos requisitos (temos testes que provam isso!) e seria útil em muitos contextos. Progredimos rapidamente com os testes nos protegendo e não tememos refatorar, sabendo que a rede de segurança dos testes nos ampara caso algo quebre.  

Agora, vamos virar a página para o próximo capítulo e ver como superar os pontos pendentes e transformar esse motor de templates em um produto completo, funcional e bem construído!

---

## 🧠 Raciocínio Contido no Texto

- TDD promove um ciclo disciplinado de criação de testes, implementação e refatoração.  
- Programação por intenção orienta a API ideal antes de escrever a implementação.  
- Testes atuam como rede de segurança, permitindo refatorações sem medo de regressões.  
- Focar no mínimo necessário acelera entregas e evita over-engineering.  
- O sucesso do motor de templates depende da cobertura de testes que confirmam cada requisito.

---

## 📚 Conceitos Explicativos

### 🔄 1. Ciclo Teste–Código–Refatoração  

- Escreva um teste que falhe (vermelho).  
- Implemente o mínimo para fazê-lo passar (verde).  
- Refatore o código para melhorar design mantendo testes verdes.  

  - **Exemplo Lúdico:** É como construir uma torre de blocos: primeiro você testa se uma peça encaixa, depois coloca a peça, e por fim ajusta a base para ficar estável antes de subir o próximo bloco.

---

### 🌱 2. Programação por Intenção  

- Imagine a interface ideal e escreva o teste como se ela já existisse.  
- Força a implementação a evoluir para a API desejada.  

  - **Exemplo Lúdico:** Pense num roteirista que traz um storyboard completo da cena antes que os atores gravem qualquer diálogo, garantindo que a filmagem siga exatamente a visão original.

---

### 🛡️ 3. Rede de Segurança de Testes  

- Uma suíte de testes abrangente detecta falhas imediatamente após mudanças.  
- Dá confiança para refatorar sem medo de quebrar funcionalidades existentes.  

  - **Exemplo Lúdico:** É como um trampolim de segurança sob um acrobata: ele se arrisca em manobras ousadas sabendo que, se errar, será amparado pela rede.

---

### ⚡ 4. Foco no Essencial  

- Priorize cada entrega em pequenos incrementos que agreguem valor real e verificável.  
- Evite gastar tempo com funcionalidades ainda não solicitadas.  

  - **Exemplo Lúdico:** Como um chef que prepara um amuse-bouche antes do jantar completo — serve algo saboroso e imediato enquanto planeja o prato principal.

---

## 💼 Capítulo de Boas Práticas & Cenários Reais 🌟

### ✅ Boas Práticas  
- Mantenha o ciclo TDD: teste-código-refatorar sem atalhos.  
- Escreva testes claros e focados em requisitos de negócio.  
- Refatore sempre após cada “verde”, mantendo métodos curtos e níveis de abstração consistentes.  
- Use programação por intenção para desenhar APIs limpas.  
- Organize testes em suítes: unitários, integração, aceitação e performance.  
- Integre TDD a CI/CD para feedback contínuo de qualidade.  

### 🌍 Cenários Reais em Negócios  
- **E-commerce:** desenvolver e testar fluxo de checkout passo a passo, refatorando cálculos de frete conforme surgem novos requisitos.  

- **Fintech:** escrever testes de cálculo de juros antes de implementar regras complexas de tributação e bilhetagem.  

- **SaaS B2B:** usar acceptance TDD para validar cada endpoint da API conforme user stories de clientes corporativos.  

- **IoT:** testar leitura e processamento de dados de sensores um a um, garantindo estabilidade antes de implementar a orquestração de múltiplos dispositivos.

---

## 📝 Exercícios de Fixação

1. Descreva em até três linhas o benefício do ciclo **vermelho-verde-refatorar** no TDD.  

2. Explique como **programação por intenção** influencia o design de APIs.  

3. Dê um exemplo (em linguagem natural) de um teste que deveria entrar na suite de **performance** de um motor de templates.

---

## 🏆 Soluções

1. O ciclo vermelho-verde-refatorar comprova que cada funcionalidade só entra quando testada e passa, e garante que o design seja continuamente aprimorado após cada entrega.  

2. Ao escrever testes que supõem a API ideal, o desenvolvedor cria uma implementação que se ajusta à intenção expressa, resultando em interfaces naturalmente simples e intuitivas.  

3. “Ao avaliar um template com 50 variáveis em um texto de 500 palavras, `evaluate()` deve executar em menos de 100 ms.”  

```java
@Test
public void performanceLargeTemplate() {
    // setup de template com 500 palavras e 50 variáveis
    long start = System.nanoTime();
    template.evaluate();
    long elapsedMs = (System.nanoTime() - start) / 1_000_000;
    assertTrue("Demorou " + elapsedMs + "ms, alvo 100ms", elapsedMs <= 100);
}
```
