# 📘 Capítulo 1.5.3: Cobertura de Código – Code Coverage 🕵️‍♀️

## 📝 Tradução do Texto

Muitos desenvolvedores conhecem ferramentas de análise estática como Lint e variantes. No mundo Java, é comum usar o PMD para detectar uso indevido de construções ou medir complexidade. O foco crescente em testes automatizados, especialmente unitários, gerou várias ferramentas para medir cobertura de código (ou cobertura de testes). Em resumo, cobertura de código é a métrica que indica o quanto nossos testes exercitam efetivamente o código de produção—suas instruções, ramos de decisão e expressões.

O principal benefício de incluir métricas de cobertura nos builds é manter sempre visível o quão completa é nossa suíte de testes. Isso ajuda muito equipes iniciando testes unitários ou adotando TDD, pois revela as áreas do código que ainda não estão sendo verificadas.

Como outras métricas técnicas, cobertura de código pode ser mal usada. Correr cegamente atrás de 100% é arriscado: às vezes, pelas APIs envolvidas, ir de 99% para 100% significa testar cenários impossíveis. Se decidir usar cobertura, tome cuidado para não “atirar no próprio pé”.

Qual meta de cobertura buscar? Depende de tecnologias, linguagens e contexto. Em Java/J2EE, 85% é comum—não por falta de testes em partes críticas, mas pelos detalhes e “esquisitices” das APIs. Nas palavras de J. B. Rainsberger: “Mire em 100% enquanto aprende—você vai entender por que 85% é mais agradável.”

Algumas ferramentas populares para Java são: Cenqua Clover, Cobertura e EMMA.

---

## 🧠 Raciocínio Contido no Texto

- Cobertura de código revela lacunas de testes, orientando onde focar novos casos de teste.  
- Métricas ajudam equipes iniciantes em TDD a priorizar áreas críticas.  
- Buscar cobertura perfeita pode levar a testes inúteis e retrabalho.  
- Meta de cobertura varia conforme linguagem, APIs e complexidade do projeto.

---

## 📚 Conceitos Explicativos

### 🛠️ 1. Ferramentas de Análise Estática x Cobertura de Código

Análise estática (Lint, PMD) detecta padrões problemáticos sem executar código. Cobertura de código mede o que **é** executado pelos testes.

  - **Exemplo Lúdico:** É como revisar uma receita apenas lendo os ingredientes (análise estática) versus realmente cozinhar o prato e ver quais etapas são executadas (cobertura de código).

---

### 📏 2. O Que é Cobertura de Código?

Percentual de comandos, ramos e expressões do código de produção tocados por testes automatizados.

  - **Exemplo Lúdico:** Imagine um **mapa do tesouro** onde cada pedaço escavado (testado) é colorido. A área não colorida mostra onde ainda não procuramos o tesouro.

---

### 🌟 3. Benefícios de Medir Cobertura

- Destaca trechos não testados.  
- Orienta a escrita de novos testes.  
- Dá visibilidade contínua da abrangência dos testes.

  - **Exemplo Lúdico:** É como usar um **detector de vazamentos** num cano: ele apita nos pontos não inspecionados, ajudando você a focar na área que realmente precisa de atenção.

---

### ⚠️ 4. Riscos de Cobertura Cega

Correr atrás de 100% a qualquer custo leva a testes irrelevantes e perda de tempo. Nem todas as linhas merecem ser cobertas.

  - **Exemplo Lúdico:** É como arrumar o armário classificando até as buchas de limpeza: você gasta horas organizando algo que nunca vai usar, enquanto a geladeira está sem comida.

---

### 🎯 5. Meta de Cobertura Ideal

Não há valor mágico; depende de contexto. Em Java/J2EE, 85% é um patamar saudável para equipes experientes.

  - **Exemplo Lúdico:** É como calibrar o volume de um sistema de som: 100% de volume distorce o áudio; 85% é o ponto em que a música soa clara sem estalos.

---

## 🛠️ Capítulo 2: Boas Práticas & Cenários Reais 💼

### ✅ Boas Práticas

- Monitore cobertura de código em cada build automático.  
- Priorize testes em áreas críticas, não em casos hipotéticos.  
- Combine cobertura de linhas, ramos e caminhos de decisão.  
- Ajuste a meta de cobertura conforme a disciplina e maturidade do time.  
- Revise periodicamente relatórios para identificar quedas na cobertura.

### 🌐 Cenários Reais em Negócios

- **E-commerce:** garantir teste de todos os cálculos de carrinho e checkout, mas não testar códigos de tributação obsoletos.  
- **Fintech:** medir cobertura de regras de cálculo de juros e tarifas, ignorando cenários de moedas não usadas.  
- **SaaS B2B:** focar cobertura em APIs críticas de autenticação, deixando de lado endpoints internos de debug.  
- **IoT:** cobrir lógica de processamento de dados de sensores, mas não simular falhas de hardware raras no nível de testes unitários.

---

## 📝 Exercícios de Fixação

1. Explique em até três linhas a diferença entre análise estática e cobertura de código. 

2. Cite dois benefícios e dois riscos de usar métricas de cobertura.  

3. Dê um exemplo de meta de cobertura adequada para um projeto em Python que lida com processamento de dados científicos.

---

## 🏆 Soluções

1. Análise estática examina o código sem executá-lo (detecta padrões e erros); cobertura de código mede quais partes foram realmente executadas pelos testes.  

2.  
   - Benefícios: destaca áreas não testadas; orienta novos testes.  
   - Riscos: testes inúteis para linhas irrelevantes; esforço desproporcional para atingir 100%.  

3. Em um projeto Python de processamento científico, 75–80% de cobertura pode ser adequado, focando em funções críticas de cálculo e deixando de lado scripts de experimentação ad-hoc.  
