
# 📖 Capítulo 1: Visão Geral 🖼️

## 📝 Tradução do Texto

Posso suportar a força bruta, mas raciocínio bruto é insuportável. — Oscar Wilde

“Só escreva código para corrigir um teste que falhou.” Isso é desenvolvimento guiado por testes, ou TDD, em uma frase. Primeiro escrevemos um teste, depois escrevemos código para fazê-lo passar. Em seguida, descobrimos o melhor design possível para o que criamos, apoiando-nos nos testes já existentes para não quebrar nada no caminho. Essa abordagem ao construir software incentiva um bom design, gera código testável e nos afasta do over-engineering baseado em suposições equivocadas. Tudo isso é alcançado pelo simples ato de guiar nosso design, passo a passo, com testes executáveis que nos conduzem à implementação final.

Este livro trata de aprender a dar esses pequenos passos. Ao longo dos capítulos, aprenderemos os princípios e as sutilezas do TDD, desenvolveremos aplicações Java e Java Enterprise usando TDD e conduziremos nosso processo de desenvolvimento geral com uma extensão da ideia central de TDD chamada desenvolvimento guiado por testes de aceitação (acceptance TDD ou ATDD). Conduziremos o desenvolvimento em nível de funcionalidade escrevendo testes de aceitação antes de implementar cada recurso com TDD.

Aplicar testes para mais do que mera verificação de correção do software não é exatamente uma invenção nova. Muitos veteranos contam histórias de como escreviam testes antes do código antigamente. Hoje, esse modo de desenvolver software tem nome: TDD. A maior parte deste livro é dedicada ao “o quê” e ao “como” do desenvolvimento guiado por testes, aplicado às várias tarefas de criação de software.

Em termos de adoção geral, entretanto, o TDD ainda é novidade. Assim como as comodities de hoje eram luxo ontem, uma técnica de programação e design começa como privilégio de poucos e só vira padrão quando os pioneiros comprovam seu valor. A prática deixa de ser nicho e torna-se rotina. Acredito que a adoção em massa do TDD está mais próxima a cada dia. Na verdade, já começou, e espero que este livro torne a transição menos turbulenta. Começaremos expondo o desafio de entregar software com o estado atual da prática em desenvolvimento. Depois de alinharmos nossos objetivos e obstáculos, traçaremos um roteiro de como TDD e ATDD podem resolver esses problemas, e analisaremos as ferramentas que podemos empregar nessa jornada rumo à maestria.

---

## 💡 Raciocínio Central

- O desenvolvimento deve ser guiado por testes falhos, não por especulações de design.
- Testes executáveis garantem feedback rápido e evitam regressões.
- Pequenos incrementos de código, amparados por testes, conduzem a um design mais simples e robusto.
- A adoção gradual transforma práticas de nicho em padrões corporativos.

---

## 📚 Conceitos Fundamentais

### 🐣 1. Test-Driven Development (TDD)

- Escreva primeiro um teste que falhe.
- Implemente o código mínimo para fazê-lo passar.
- Refatore o design, mantendo todos os testes verdes.


  - **Exemplo lúdico:** Imagine um chef que só prova a massa do bolo após escrever uma “receita-teste” dizendo: “A massa deve ser doce e fofa.” Ele ajusta os ingredientes até o teste (uma pequena mordida) ficar ótimo. Só então segue adiante, refinando a apresentação do bolo.


 ```javascript
 // JavaScript
 // Teste: somar dois números
 assertEquals(add(2, 3), 5);

 function add(a, b) {
 return a + b;
 }
```


### 🏁 2. Acceptance Test-Driven Development (ATDD)

- Defina cenários de uso do ponto de vista do usuário.
- Escreva testes de aceitação que cubram essas jornadas.
- Desenvolva cada recurso via TDD até atender aos critérios de aceitação.


  - **Exemplo lúdico:** Pense em uma peça de teatro: antes de montar o cenário, o diretor escreve “teste de aceitação” dizendo “o personagem X deve entrar no palco com a máscara Y.” Só então o cenógrafo constrói o palco e os adereços.


### 🐢 3. Passos Pequenos e Refatoração

- Pequenas alterações reduzem erros.      
- Refatore sempre que houver duplicação ou design confuso.
- Garanta que todos os testes continuem passando após cada refatoração.


  - **Exemplo lúdico:** Construa um castelo de cartas colocando uma carta de cada vez, garantindo que cada camada esteja estável antes de seguir em frente. Se algo balançar, remova e ajuste antes de continuar.


---

## 🛠️ Capítulo de Boas Práticas e Cenários Reais 📈

- Integre TDD/ATDD em pipelines de CI/CD para feedback imediato.
- Use cobertura de testes (coverage) como métrica de confiança, não como fim em si.
- Adote pair programming para revisão de testes e código em tempo real.
- Documente critérios de aceitação em linguagem compreensível por todos os stakeholders.

### Cenários frequentes em negócios:

- **E-commerce:** validando fluxos de pagamento e carrinho de compras via ATDD.
- **Fintech:** garantindo regras de juros e cálculos de investimento com TDD.
- **Aplicações IoT:** testando comunicação entre dispositivos antes do hardware final.
- **Microserviços:** simulando dependências com mocks e stubs para isolar unidades de serviço.

---

## ✅ Exercícios de Fixação

1. Descreva, em até três linhas, o ciclo “Red–Green–Refactor” do TDD.
2. Crie um cenário de aceitação simples para um login de usuário (ATDD).
3. Identifique em um código fictício (abaixo) onde inserir o primeiro teste e descreva qual seria o teste:

 ```python
 # Python

 def calcular_desconto(valor, percentual):
 # TODO: implementar
 pass

 ```

---

## 💡 Soluções

1. Ciclo Red–Green–Refactor:

   - `Red`: escreva um teste que falha.
   - `Green`: implemente o mínimo para fazê-lo passar.
   - `Refactor`: melhore o design mantendo todos os testes verdes.

2. Cenário de aceitação “Login Bem-Sucedido”:

   - Dado que um usuário existe com email “maria@ex.com” e senha “1234”
   - Quando ela submete o formulário de login com esses dados
   - Então ela deve ser redirecionada ao dashboard e ver “Bem-vinda, Maria!”

3. No código `calcular_desconto`, o primeiro teste poderia ser:

   - “assert calcular_desconto(100, 10) == 90”
   - Escreva esse teste antes de implementar a função, depois faça a função retornar `valor * (1 - percentual/100)` para passar no teste.


 ```java
    import org.junit.Test; import static org.junit.Assert.assertEquals;

    // Teste primeiro (TDD)

    public class DescontoTest 
    {
      @Test 
      public void deveCalcularDesconto() 
      { 
        assertEquals(90.0, Desconto.calcularDesconto(100, 10), 0.0001); 
      }
    }


    // Implementação mínima para passar no teste

    public class Desconto 
    { 
      public static double calcularDesconto(double valor, double percentual) 
        { 
        return valor * (1 - percentual / 100); 
      } 
    }
    ```


## Conceitos

- **Test-Driven Development (TDD)**: Escrever testes antes de implementar o código.
- **Acceptance Test-Driven Development (ATDD)**: Escrever testes de aceitação antes de implementar o código.
- **Pair Programming**: Dois programadores trabalhando juntos, um escrevendo o código e o outro revisando.
- **Refactoring**: Melhorar o design do código mantendo todos os testes verdes.

---

## 🧩 Integração Contínua (CI)

Prática de mesclar frequentemente mudanças de código em um repositório compartilhado, acionando automaticamente builds e testes que detectam erros precocemente.

**Exemplo lúdico:** Imagine um chef preparando um risoto. A cada colherada de arroz que ele adiciona, ele prova um grão para verificar o ponto e o tempero. Se estiver salgado demais ou sem sal, ele ajusta na hora antes de continuar. Esse “provar a cada colher” equivale aos testes rápidos que a CI dispara a cada nova linha de código.

---

## 📦 Entrega Contínua (CD)

Extensão da CI que automatiza a preparação do build validado para ambientes de homologação ou produção, deixando o artefato sempre pronto para entrega.

**Exemplo lúdico:** Depois do chef provar e ajustar cada grão de risoto, ele coloca porções em pequenas marmitas lacradas e etiquetadas para a equipe de degustação. As marmitas chegam prontas ao laboratório de testes do restaurante, sem necessidade de reembalagem manual — assim como um build validado e empacotado automaticamente pela CD.

---

## 🚀 Implantação Contínua

Vai além da entrega contínua e automatiza também o deploy em produção assim que todos os testes passam, sem intervenções humanas.

**Exemplo lúdico:** Assim que o laboratório de degustação aprova cada marmita, um robô de entrega autônomo sai imediatamente do restaurante e leva o prato quentinho até a casa do cliente, sem ninguém ter que tocar no pacote. É o deploy automático do seu software direto para os usuários finais.