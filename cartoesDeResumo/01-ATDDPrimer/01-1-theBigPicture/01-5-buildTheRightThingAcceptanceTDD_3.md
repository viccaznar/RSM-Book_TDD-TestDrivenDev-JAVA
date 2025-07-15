# 📘 Capítulo 1.5: Testes como Linguagem Compartilhada 🗣️

## 📝 Tradução do Texto

Um dos maiores problemas de desenvolver software para terceiros é a ambiguidade prevalente nos requisitos. Não é tarefa fácil expressar e comunicar exigências sem perder informação e sem deturpar a ideia original. Alguns afirmam ser impossível: afinal, não podemos ler mentes.  

Esse problema se acentua quando usamos documentação escrita — um documento de requisitos, por exemplo — um formato longe de ser perfeito para transferir entendimento. Se transformássemos cada requisito em testes executáveis que verificam se o sistema atende cada aspecto da especificação, haveria muito menos ambiguidades e menos espaço para interpretações dos desenvolvedores. Eis o cerne da ideia de **testes como especificação**.

Com **testes como especificação**, olhamos aos testes como algo derivado dos requisitos; logo, um sistema que passa nesses testes deve, em teoria, atender à especificação. Claro, isso pressupõe cobertura perfeita de testes, algo que raramente ocorre em projetos “do mundo real”. Defeitos escapam porque deixamos passar um teste ou por preguiça de executá-los todos.  

Ainda assim, usar testes como especificação traz vantagens claras:
- Feedback mais rápido via automação  
- Execução de testes confiável (sem esquecer de rodá-los)  
- Um passo a menos na tradução de requisitos para código  

Mesmo errando ao converter requisitos em testes, quanto menos etapas de interpretação humana, menor o risco de algo “cair no vazio” depois.  

Além disso, a prática de **especificação por exemplo** faz com que testes expressem requisitos com casos concretos em vez de frases abstratas. Em vez de “o sistema deve calcular imposto”, escrevemos “para assinatura de $20 com taxa de 10%, o sistema cobra $22”. Essa abordagem encaixa-se melhor na nossa intuição e reduz riscos de mal-entendidos em regras complexas, como multiplos cálculos de tributos em diferentes localidades.

---

## 🧠 Raciocínio Contido no Texto

- Requisitos escritos sofrem ambiguidade; transformar em testes executáveis reduz interpretações errôneas.  
- Testes como especificação unificam design, requisitos e verificação em um único artefato.  
- Automação e execução forçada de testes combatem a preguiça humana e aceleram feedback.  
- Especificação por exemplo torna regras abstratas concretas, alinhando entendimento entre todos.

---

## 📚 Conceitos Explicativos

### 🌀 1. Ambiguidade nos Requisitos

Documentos escritos perdem nuances, geram leituras diferentes e demandam clarificações constantes.

  - **Exemplo Lúdico:** É como jogar “telefone sem fio”: cada pessoa repete a frase original e, ao final, a mensagem chega totalmente distorcida.

---

### 📜 2. Testes como Especificação

Transformar cada requisito em teste executável faz do conjunto de testes o contrato que define o que deve ser entregue.

  - **Exemplo Lúdico:** Imagine receber uma receita em vídeo: em vez de ler instruções vagas, você vê exatamente cada passo e só cozinha o prato quando todos os testes (provas de sabor, textura e cor) passam.

---

### ⚡ 3. Vantagens de Testes como Especificação

#### Feedback Rápido

Automação dispara testes ao menor sinal de mudança, revelando erros imediatamente.

  - **Exemplo Lúdico:** Como um detector de fumaça que soa o alarme ao primeiro sinal de fumaça, avisando antes que o incêndio alastre.

#### Execução Confiável

O computador não “esquece” de rodar testes; cada alteração é verificada sem falhas humanas.

  - **Exemplo Lúdico:** É como um robot de cozinha que segue a receita à risca toda vez, sem pular nenhuma etapa.

#### Um Passo a Menos

Elimina a tradução de “documento → teste → desenvolvedor”, pois o teste **é** a especificação.

  - **Exemplo Lúdico:** Pense num espelho mágico que reflete exatamente o que você quer: só precisa olhar para saber se está correto, sem intermediários.

---

### 🌟 4. Especificação por Exemplo

Requisitos são expressos por casos concretos, facilitando o entendimento de regras complexas.

  - **Exemplo Lúdico:** Como aprender matemática com problemas reais: em vez de fórmulas abstratas, você calcula o troco de uma compra de verdade e entende o conceito na prática.

---

## 🛠️ Capítulo 2: Boas Práticas & Cenários Reais 🌐

### ✅ Boas Práticas

- Defina cada requisito como um **teste executável**, não apenas como texto.  
- Automatize todos os testes em **CI/CD**, garantindo feedback em cada build.  
- Use **exemplos reais** nos testes de aceitação para cobrir cenários críticos e casos de borda.  
- Revise periodicamente a suíte de testes para cobrir lacunas de especificação.  
- Mantenha testes simples e rápidos, permitindo rodá-los toda vez que o código mudar.

### 🌍 Cenários Reais de Negócio

- Em **e-commerce**, testes de exemplo valem para calcular descontos, fretes e campanhas regionais.  
- Em **fintech**, regras de imposto e tarifas são validadas por exemplos de cálculos em diferentes cenários de conta.  
- Em **logística**, simulações de roteirização (peso, volume, prazos distintos) garantem que cada cenário seja coberto.  
- Em **telecom**, planos de assinatura com franquias de dados e descontos em roaming são especificados por exemplos de faturas.

---

## 📝 Exercícios de Fixação

1. Em até três linhas, explique como “testes como especificação” reduz a ambiguidade nos requisitos.  

2. Cite as três vantagens principais de usar testes executáveis como especificação.  

3. Crie um exemplo de “especificação por exemplo” para a regra de cálculo de frete gratuito acima de $100.

---

## 🏆 Soluções

1. Testes como especificação convertem requisitos em código automatizado, eliminando a interpretação individual de texto e tornando claras as condições de sucesso.  

2.  
   - Feedback mais rápido via automação.  
   - Execução confiável sem depender de memória humana.  
   - Um passo a menos na tradução do que deve ser desenvolvido.  

3. Exemplo de especificação por exemplo (frete gratuito):  
  Dado que o pedido totaliza $120 Quando o cliente finaliza a compra Então o sistema deve aplicar frete de $0 E exibir “Frete gratuito aplicado”