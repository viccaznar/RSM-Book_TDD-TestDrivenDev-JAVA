# 📘 Capítulo 1.5: Desenvolvimento Evolutivo 🌱

## 📝 Tradução do Texto

A capacidade da nossa memória de trabalho é limitada. Tentar trocar informações constantemente entre a memória de curto prazo e documentos escritos faz com que algo seja esquecido. Ter uma sequência de passos pequenos rumo ao objetivo final nos permite medir o progresso de forma concreta — cada passo é um teste que comprova avanço.

O TDD naturalmente incentiva esses pequenos passos e promove um design evolutivo. Estamos sempre aprimorando o código em incrementos sutis. Na prática, adicionamos partes da arquitetura “just in time” conforme surgem necessidades reais, considerando esse esforço ao estimar o trabalho.

### Design Evolutivo

Muitas vezes um trecho de código “grita” por melhorias, mas fica sem atenção porque é parte de uma interface crítica e difícil de mudar. Design evolutivo é a mentalidade de cuidar desse código vivo, em vez de protegê-lo de mudanças. Assim, melhoramos a qualidade do design e, indiretamente, de todo o sistema, em pequenos passos.

Algumas mudanças arquiteturais são fáceis de aplicar “just in time” (ex.: adicionar um servidor de e-mail quando precisar enviar mensagens). Outras, como converter um app desktop mono-usuário em cliente-servidor, exigem mais esforço. A boa notícia é que podemos antecipar parte dessas necessidades e planejar o suficiente sem over-engineering.

#### Mudança Antecipada vs. Mudança Inesperada

- Nem toda mudança prevista acontece; muitas se transformam em surpresas.  
- Use bom senso: implemente o que você **sabe** que vai precisar, mas mantenha flexibilidade para o que ainda é incerto.

### Disciplina e Refatoração

Design evolutivo exige mudanças constantes no código existente. Para evitar que o software “apodreça”, precisamos de disciplina para manter o código limpo e saudável. A refatoração contínua é a prática central: é o que torna o TDD sustentável e garante uma base pronta para novas funcionalidades.

---

## 🧠 Raciocínio Contido no Texto

- Dividir tarefas em testes pequenos torna objetivos gerenciáveis.  
- Design evolutivo incrementa arquitetura conforme necessidades reais.  
- Antecipar mudanças evita retrabalho, mas sem criar funcionalidades desnecessárias.  
- Disciplina e refatoração contínua mantêm a qualidade do código.

---

## 📚 Conceitos Explicativos

### 🧩 1. Passos Pequenos e Memória Limitada

- Pequenos testes cabem na mente e confirmam progresso concreto.

  - **Exemplo Lúdico:** Imagine um **detetive de pistas** que marca cada indício no mapa antes de seguir adiante. Cada marca é um “teste” da rota correta pelo labirinto.

---

### 🏗️ 2. Design Evolutivo “Just in Time”

- Implemente só o que é necessário agora.  
- Adicione arquitetura conforme surgem requisitos reais.

  - **Exemplo Lúdico:** É como construir uma **ponte de lego**: você junta pilares e vigas conforme precisa atravessar cada rio, não antes de saber que o rio existe.

---

### 🔮 3. Mudança Antecipada vs. Inesperada

- Planeje o que você sabe que virá, mas adapte-se às surpresas.  
- Evite gastar esforço com funcionalidades que podem nunca ser usadas.

  - **Exemplo Lúdico:** Pense num **pescador** que leva iscas para peixes que já viu no lago (antecipado) mas troca de isca quando aparece um peixe diferente (inesperado).

---

### ⚖️ 4. Trade-Off Entre Planejamento e Flexibilidade

- Equilibre design antecipado e capacidade de agir rapidamente.  
- Ajuste seu nível de planejamento conforme revelações no desenvolvimento.

  - **Exemplo Lúdico:** É como navegar um **barco**: às vezes você traça a rota pela bússola, outras vezes desvia à vista ao encontrar recifes não mapeados.

---

### 🛡️ 5. Disciplina e Refatoração Contínua

- Refatore sempre que surgir duplicação ou complexidade.  
- A prática constante evita que o código fique “podre”.

  - **Exemplo Lúdico:** Imagine um **jardineiro** que poda galhos secos assim que aparecem, mantendo a planta saudável e pronta para florescer.

---

# 🔧 Capítulo 2: Boas Práticas & Cenários Reais 🏢

## ✅ Boas Práticas

- Divida grandes tarefas em **pequenos testes**.  
- Adote arquitetura **just in time**, só quando um teste exigir.  
- Execute **refatoração** logo após cada teste passar.  
- Documente ideias extras num **backlog**, mas implemente depois.  
- Use **CI/CD** para validar cada incremento automaticamente.  
- Cultive disciplina de **testar e refatorar** continuamente.

---

## 📝 Exercícios de Fixação

1. Explique em até três linhas por que passos pequenos ajudam a lidar com nossa memória limitada.  

2. Cite dois benefícios de uma arquitetura “just in time”.  

3. Descreva um exemplo (qualquer domínio) em que antecipar demais uma mudança seria prejudicial.

---

## 🏆 Soluções

1. Passos pequenos mantêm o foco em tarefas gerenciáveis; cada teste confirma conclusão parcial e evita sobrecarga cognitiva.  

2. Benefícios:  
   - Evita over-engineering e retrabalho.  
   - Permite validar requisitos reais antes de investir em infraestrutura complexa.  
   
3. Exemplo: implementar cache distribuído antes de ter usuários suficientes gera complexidade desnecessária e pode atrasar a entrega inicial.  
