Traduza o texto para o português. Identifique o raciocínio contido no texto. Organize os conceitos em tópicos explicativos, com resumo objetivo, robusto e simples. Para cada conceito, insira um exemplo lúdico rico e explicativo que ilustre a ideia dos conceitos mais difícieis. Insira um capítulo sobre boas práticas e cenários reais onde o que é explicado acontece com frequência em um negócio. Organize os tópicos em capítulos e subcapítulos decorados com emoticons que condizem com o que está sendo abordado. Inclua uma seção de exercícios para fixar o conteúdo, junto com a solução. Coloque o resultado em um único bloco no formato Markdown. Se houver exemplos de códigos, envolva-o entre quotes junto com o nome da linguagem de programação:

Breadth-first, depth-first
 The software we build today is not something trivial that can be built in a matter
 of a couple of hours. I’ve worked with systems with tens of thousands of lines of
 code. One system had over a million lines of code. And I know there are plenty of
 people out there who have developed and maintained systems that have had
 many more millions of lines of code than the one I had the privilege of being
 involved with. Just like it’ll get messy if we try to swallow a muffin as a whole, tak
ing too big a bite talking about code will surely backfire as well.
 In our template engine example, we just reached a point where we uncovered
 a muffin-size bit of complexity that we haven’t yet taken care of. At the same time,
 the test we were working on—evaluating a template—cannot work without that
 particular bit of complexity being tackled first. Or can it?
 As you may remember from the algorithms course in school, there is more
 than one way to traverse a tree. We can either traverse breadth-first or we can
 traverse depth-first. The same holds true for test-driven development. Well, sort
 of. Figures 2.3 and 2.4 compare these two alternatives side by side.
 We could decide to go breadth-first, writing tests against the public interface of
 the Template class; making them pass by faking the internals, the lower-level func
tionality; and only then proceed to writing tests for (and implementing) the layer
 beneath the original one. Figure 2.3 illustrates this approach.
 Template engine functionality
 Faked
 parsing
 Template engine functionality
 Faked
 rendering
 Parsing
 Faked
 rendering
 Template engine functionality
 Parsing
 Rendering
 Figure 2.3 With a breadth-first strategy, we implement the higher-level functionality first by 
faking the required lower-level functionality.
Breadth-first, depth-first
 59
 Template engine functionality
 Parsing
 Template engine functionality
 Rendering
 Template engine functionality
 Parsing
 Rendering
 Parsing
 Rendering
 Figure 2.4 With a depth-first strategy, we implement the lower-level functionality first and 
only compose the higher-level functionality once all the ingredients are present.
 The other option would be to back out to a working state and start writing tests for
 the template-parsing logic instead—and come back once we’ve got the template
parsing stuff in check. That is, traverse functionality depth-first and implement
 the details first for one small vertical slice before moving on with the next slice.
 Figure 2.4 shows what this approach might look like.
 In the case of our template engine having to deal with “Hello, ${name}”, we can
 fake the lower-level functionality—parsing the template—a little longer before we
 add more functionality (more tests, that is) and see where that’ll lead us.
 2.3.1 Faking details a little longer
 First, we’ll need to start storing the variable value and the template text some
where. We’ll also need to make evaluate replace the placeholder with the value.
 Listing 2.10 shows one way to get our test passing.
 Listing 2.10 Our first attempt at handling the variable for real
 public class Template {
    private String variableValue;
    private String templateText;
    public Template(String templateText) {
        this.templateText = templateText;
    }
    public void set(String variable, String value) {
        this.variableValue = value;
    }
    public String evaluate() {
 return templateText.replaceAll("\\$\\{name\\}", variableValue);
    }
 }
60
 CHAPTER 2
 Beginning TDD
 Some might say what we’re doing here is cheating—we’re still hard-coding the reg
ular expression to look for “${name}”. It’s not really cheating, however. We’re being
 disciplined and not giving in to the temptation of “just write the code and be done
 with it.” We’ll get there eventually. Baby steps, remember? All tests are passing,
 we’re on stable ground—with a green bar as evidence—and we know exactly where
 that ground is. What’s next?
 Refactoring is what’s next. Do you see anything to refactor? Spot any duplica
tion that’s bothering you? Any less-than-ideal code constructs? Nothing strikes my
 eye, so I’ll go on and proceed to enhancing our test. Specifically, I’d like to drive
 out that hard-coded variable name. What better way to do that than by introduc
ing multiple variables into the template?