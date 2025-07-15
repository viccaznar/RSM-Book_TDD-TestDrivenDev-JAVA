# 📗 Capítulo 2.1: De Requisitos a Testes 📝

## 📝 Tradução do Texto

Imagine que você está implementando um subsistema para uma suíte corporativa de colaboração responsável por fornecer funcionalidades de template de email, para que o assistente do CEO envie emails personalizados a todo o pessoal com alguns cliques. Como os testes vão guiar o desenvolvimento desse subsistema? A resposta sai ao final deste capítulo, mas tudo começa decompondo os requisitos em algo menor e mais concreto.

### 2.1.1 Decompondo Requisitos 🪓

Quando você visualiza os requisitos do subsistema, provavelmente já os dividiu em “tarefas” — itens como “escrever expressão regular para identificar variáveis” ou “implementar parser de template”. Agora apague essas tarefas da mente e faça tudo de novo, desta vez fragmentando os requisitos em **testes**. Pense em pequenos testes que, quando passam, provam que parte do requisito foi atendida.

Por exemplo:
- “Um template sem variáveis é enviado exatamente como está.”  
- “O marcador para nome do destinatário deve ser substituído pelo nome correto.”  

Esses testes, em conjunto, verificam comportamento e funcionalidade completos, enquanto tarefas soltas não garantem progresso real.

### 2.1.2 Do Que São Feitos Bons Testes? 🔍

Nem todo teste vale. Dois atributos são cruciais para um teste guiar bem o desenvolvimento:

- **Atomização:** o teste deve cobrir somente um aspecto pequeno e definido do comportamento.  
- **Isolamento:** o teste não pode depender de nenhum outro teste ou estado global.

Testes atômicos mantêm o foco num passo preciso rumo ao sistema completo. Testes isolados evitam efeitos colaterais e garantem que cada falha ou sucesso se deva apenas ao comportamento testado.

---

## 🧠 Raciocínio Contido no Texto

- Dividir requisitos em testes (e não tarefas) alinha o trabalho a resultados observáveis no software.  
- Testes atômicos e isolados estabelecem passos claros e confiáveis rumo ao sistema final.  
- A prática de “testes como passos concretos” mantém forte a conexão mental entre exigência e implementação.

---

## 📚 Conceitos Explicativos

### 🧩 1. Testes vs. Tarefas

- Tarefas descrevem trabalho a fazer; testes definem comportamento que deve funcionar.  
- Passar num teste é “feito”; concluir uma tarefa não garante sistema ativo.

- **Exemplo Lúdico:** Imagine construir um **quebra-cabeça**. Tarefas seriam “junte 50 peças azuis”; testes seriam “a ponta superior do castelo forma uma torre completa”. Você só sabe que concluiu quando vê o castelo, não ao juntar peças sem contexto.

---

### 💥 2. Teste Atômico

- Teste foca num único cenário ou regra de negócio.  
- Facilita diagnóstico de falhas.

- **Exemplo Lúdico:** É como atirar uma flecha num alvo numerado: cada flecha (teste) mira num círculo específico. Se a flecha atinge o círculo certo, você sabe exatamente o que funciona.

---

### 🛡️ 3. Teste Isolado

- Teste não deve depender de dados ou estados gerados por outros testes.  
- Garante resultados previsíveis e independentes.

- **Exemplo Lúdico:** Pense num **grampo de papel**: cada folha (teste) deve ser avaliada separadamente. Se você empilhar folhas antes de grampear, não saberá qual folha ficou solta por causa de outro grampo.

---

## 🛠️ Capítulo de Boas Práticas & Cenários Reais 💼

### ✅ Boas Práticas

- **Converta requisitos em testes** antes de listar tarefas de implementação.  
- Faça testes **pequenos e focados**: um teste — um comportamento.  
- Garanta que cada teste seja **independente**: limpe estado e use mocks se necessário.  
- Evolua a suíte de testes junto com os requisitos, mantendo-a sempre atualizada.  
- Revise periodicamente testes antigos para manter relevância e clareza.

### 🌐 Cenários Reais

- **E-commerce:** testar “cupom de desconto aplica 10%” antes de “processar pagamento”.  
- **Fintech:** validar “juros diários calculados corretamente” sem envolver transações completas.  
- **SaaS B2B:** testar “usuário com permissão X vê relatório Y” isoladamente, antes de montar dashboard completo.  
- **IoT:** verificar “leitura de sensor retorna valor numérico dentro de intervalo” antes de simular rede inteira.

---

## 📝 Exercícios de Fixação

1. Explique em até três linhas por que decompor requisitos em testes é melhor que em tarefas.  
2. Cite dois benefícios de escrever testes atômicos e isolados.  
3. Dê um exemplo de teste atômico e isolado para a funcionalidade de template de email (sem código).

---

## 🏆 Soluções

1. Testes vinculam diretamente o requisito ao comportamento observável no software, garantindo que “feito” signifique “funciona”, não apenas “foi implementado”.  
2.  
   - Localiza rapidamente a causa de uma falha.  
   - Evita dependências entre testes, proporcionando resultados previsíveis.  
3. Exemplo de teste:  
   - “Dado um template ‘Olá, {{nome}}!’ e valor ‘Maria’ para {{nome}}, quando renderizar, a saída deve ser ‘Olá, Maria!’.”  
