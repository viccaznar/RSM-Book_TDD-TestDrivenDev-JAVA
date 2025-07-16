# 📕 Capítulo 2.6: Pontas Soltas na Lista de Testes & Performance ⏱️

## 📝 Tradução do Texto

Já implementamos todos os casos de teste pensados no início. Contudo, percebemos limitações na nossa implementação: ela não trata valores de variável que contêm os delimitadores `${` ou `}`, e temos preocupações quanto ao desempenho do motor de templates. Por isso, incluímos na lista de testes:

- Avaliar template `"${one}, ${two}, ${three}"` com valores `"1"`, `"${foo}"` e `"3"`, garantindo `"1, ${foo}, 3"`.  
- Verificar que um template de 100 palavras e 20 variáveis (valores de ~15 caracteres) seja avaliado em até 200 ms.

Não queremos interromper nosso fluxo imediato: anotamos esses testes e continuamos. Neste caso, “continuar” significa escrever primeiro o teste de performance antes de retomar o problema da dupla-renderização.

### 2.6.1 Testando Performance 🚀

Para monitorar a latência de `evaluate()`, criamos um micro-teste:

```java
import org.junit.Test;
import static org.junit.Assert.*;

public class TestTemplatePerformance {
    // setup omitido: template de 100 palavras com 20 variáveis
    @Test
    public void templateWith100WordsAnd20Variables() throws Exception {
        long expected = 200L;
        long time = System.currentTimeMillis();
        template.evaluate();
        time = System.currentTimeMillis() - time;
        assertTrue("Renderização levou " + time
                + "ms, mas o alvo era " + expected + "ms",
                time <= expected);
    }
}
```

O motor passou em cerca de 100 ms. Agora, se algo o deixar lento demais, o teste sinalizará imediatamente.

Esse teste é não-determinístico: depende da carga da máquina e de processos concorrentes. Ele pode passar num computador e falhar em outro. A prática comum é ajustar o limite para falhar apenas em degradações reais de performance.

---

## 🧠 Raciocínio Contido no Texto

- Listas vivas de testes garantem que novos casos não se percam.
- Testes de performance atuam como “early warning system” de latência.
- `System.currentTimeMillis()` torna esses testes sensíveis a ruídos de sistema.
- Ajustar limites (tuning) equilibra sensibilidade e confiabilidade.
- Registrar novos testes sem interromper o fluxo preserva a produtividade.

---

## 📚 Conceitos Explicativos

### 📝 1. Lista Viva de Testes

Anote imediatamente cada cenário novo para não esquecer. Mantém cobertura alinhada às necessidades que surgem.

  - **Exemplo Lúdico:** Um chef anota imediatamente cada novo pedido de tempero: se não anotar, o prato sai sem o toque especial e o cliente reclama.

---

### ⏱️ 2. Teste de Performance

Mede tempo de execução de operações críticas. Detecta regressões de performance.

  - **Exemplo Lúdico:** Um entregador cronometra cada rota: se antes levava 10 min e passar a 20 min, ele sabe que deve ajustar o trajeto.

---

### 🔄 3. Não-Determinismo em Tempo

Testes baseados em relógio variam conforme outros processos no sistema. Podem falhar esporadicamente sem haver mudança no código.

  - **Exemplo Lúdico:** É como medir rendimento de corrida enquanto a rua é bloqueada por um caminhão ocasional — o percurso muda conforme obstáculos reais.

---

### ⚖️ 4. Tuning de Limites

Defina metas realistas para minimizar falsos positivos. Ajuste conforme o ambiente de execução.

  - **Exemplo Lúdico:** É como calibrar o alarme de incêndio para não disparar ao fritar um ovo, mas sim com fumaça de verdade.

---

### 🎯 5. Fluxo Produtivo

Anote novos testes sem implementá-los imediatamente para não distrações. Volte a eles no momento certo.

  - **Exemplo Lúdico:** Um maratonista marca cada obstáculo no percurso e só volta para removê-los depois de cruzar a linha de chegada, mantendo o ritmo.

---

### 💼 Capítulo 2.7: Boas Práticas & Cenários Reais 🌟

#### ✅ Boas Práticas

- Mantenha uma lista viva de testes que inclua cenários funcionais, de erro e de performance.
- Separe testes de performance em suíte própria para não atrasar builds regulares.
- Use frameworks de benchmarking (e.g., JMH) em vez de `System.currentTimeMillis()` para maior confiabilidade.
- Ajuste limites de tempo conforme hardware, JVM e carga esperada.
- Documente no teste o contexto e o motivo do limite de performance.

---

#### 🌍 Cenários Reais em Negócios

- **E-commerce:** garantir que a página de checkout renderize em até 300 ms com 50 itens no carrinho.

- **Fintech:** validar que relatórios de 10 000 transações sejam gerados em menos de 1 s.

- **SaaS B2B:** testar que dashboard com 100 widgets seja carregado em até 200 ms.

- **IoT:** assegurar que agregação de dados de 100 sensores ocorra em até 500 ms.

---

#### 📝 Exercícios de Fixação

1. Explique em até três linhas por que manter uma lista viva de testes é essencial.

2. Quais são duas limitações de usar `System.currentTimeMillis()` em testes de performance?

3. Proponha um teste que utilize paralelismo para validar uma meta de 200 ms de execução.

---

#### 🏆 Soluções

1. Registra novos cenários imediatamente, evitando esquecimentos.

2. Garante cobertura completa de casos que surgem durante o desenvolvimento.

3. Resultados variam com carga do sistema e processos concorrentes. Não garante repetibilidade em diferentes ambientes (dev, CI, produção).

```java
@Test
public void performanceUnderLoad() throws Exception {
    long start = System.nanoTime();
    IntStream.range(0,100).parallel().forEach(i -> template.evaluate());
    long elapsed = (System.nanoTime() - start) / 1_000_000;
    assertTrue("Meta de 200ms excedida: " + elapsed + "ms", elapsed <= 200);
}
```

```java
  // Versão em Java com JMH
@Benchmark
public void benchEvaluate() {
    template.evaluate();
}