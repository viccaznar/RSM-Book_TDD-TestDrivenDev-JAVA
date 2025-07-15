# 📗 Capítulo 2.1.3: Trabalhando a Partir de uma Lista de Testes 📝

## 📝 Tradução do Texto

Armados com um conjunto inicial de testes, podemos fazer cada um passar, um a um. Primeiro, escolhemos um teste — geralmente o mais fácil ou o que traz maior progresso com menor esforço — e ignoramos todos os outros por enquanto. Voltaremos várias vezes à questão “qual teste executar a seguir” nos próximos capítulos da parte 1, pois a cada minuto nessa abordagem test-first precisamos tomar essa decisão.

O próximo passo é escrever o código do teste. Vamos até compilar e executar o teste antes de pensar em implementar o código de produção que ele vai cobrir. “Não posso escrever o teste porque não compila?” “Não posso testar código que ainda não existe?” — Ah, mas podemos sim. Vamos descobrir como fazer isso.

Incluindo princípios como “testes devem ser isolados e independentes de ordem”, “testes devem rodar rápido” e “testes não exigem configuração manual”, mantemos nossos testes ágeis e confiáveis.

---

## 🧠 Raciocínio Contido no Texto

- Focar num teste de cada vez mantém o esforço concentrado e evita dispersão.  
- Escrever e compilar o teste antes do código de produção reforça a meta de “test-first”.  
- Decidir o próximo teste a cada passo é parte essencial do TDD de pequenos incrementos.  
- Propriedades de bons testes (isolamento, rapidez e independência) sustentam o ritmo de desenvolvimento.

---

## 📚 Conceitos Explicativos

### 🔢 1. Escolhendo o Próximo Teste

**Resumo**  
Selecione o teste que você acredita poder passar com mais facilidade ou que represente maior avanço. Ignore os demais até concluí-lo.

**Exemplo Lúdico**  
Imagine **escalar uma montanha**: você foca no próximo passo seguro, sem olhar o pico inteiro de uma vez. Cada pedra firmada é uma vitória antes de seguir em frente.

---

### ✍️ 2. Escrevendo o Teste Antes do Código

**Resumo**  
Crie o esqueleto do teste, compile e execute-o para confirmar que ele falha — antes mesmo de ter o código de produção.

**Exemplo Lúdico**  
É como escrever **a letra de uma música** antes de ter os acordes do violão. Você já sabe a melodia e testa o ritmo, mesmo sem as notas definidas.

---

### 🎯 3. Programação por Intenção

**Resumo**  
Imagine a forma ideal do código de produção ao escrever o teste. Descreva o uso perfeito antes de implementá-lo.

**Exemplo Lúdico**  
Pense num **designer de LEGO** que primeiro imagina o castelo completo e coloca o bloco de torre final antes de criar a base. Ele foca na visão ideal para guiar toda a construção.

---

## 🛠️ Capítulo 2.2: Boas Práticas & Cenários Reais 🌟

### ✅ Boas Práticas

- Mantenha uma **lista de testes** derivados diretamente dos requisitos.  
- Escolha sempre o teste com **maior retorno** (fácil de passar, alto valor).  
- Compile e execute o teste imediatamente para confirmar a falha inicial.  
- Utilize **mocks** e **stubs** para isolar dependências e manter testes rápidos.  
- Documente breves comentários no teste para explicar a intenção do comportamento.  
- Revise periodicamente a lista de testes para incluir novos cenários ou retirar casos obsoletos.

### 🌐 Cenários Reais

- **E-commerce**: testar “produto sem variação envia alerta” antes de construir o fluxo completo de promoções.  
- **Fintech**: validar “taxa de juros zero retorna valor igual ao principal” como teste inicial.  
- **SaaS B2B**: criar teste “salvar configurações de usuário retorna OK” antes de tratar credenciais avançadas.  
- **IoT**: checar “sensor emite valor dentro do intervalo esperado” antes de montar rede de múltiplos dispositivos.

---

## 📝 Exercícios de Fixação

1. Explique em até três linhas por que devemos “escrever e compilar o teste antes do código de produção”.  
2. Cite dois benefícios de escolher o teste mais fácil ou de maior valor primeiro.  
3. Descreva um teste atômico e isolado para um engine de template que substitua `{{nome}}` por “Carlos”.

---

## 🏆 Soluções

1. Escrever e compilar o teste primeiro garante que ele falhe por falta de código, reforçando o ciclo test-first e validando o ambiente de teste.  
2.  
   - Feedback imediato sobre o ponto de partida.  
   - Progresso tangível e motivador, pois um teste concluído reflete funcionalidade real.  
3.  
Dado um template "Olá, {{nome}}!" Quando renderizar com nome="Carlos" Então o resultado deve ser "Olá, Carlos!"