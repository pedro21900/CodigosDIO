# CodigosDIO

```
import java.util.function.Consumer;
import java.util.function.Function;
import java.util.function.Predicate;
import java.util.function.Supplier;
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class GitHookApplication {

    public static void main(String[] args) {
        String[] nomes = {"Pedro", "Marcos", "João", "Victor"};

        //não retorna nada interface funcional
        Consumer<String> imprimaUmaFrase = System.out::println;
        imprimaUmaFrase.accept("Oi");

        // retorna value , interface funcional
        Function<String, String> retornarNomeAoContrario = text -> new StringBuilder(text).reverse().toString();
        System.out.println(retornarNomeAoContrario.apply("Ada Wong"));

        Function<String, Integer> retornaNumeroInteiro = numero -> Integer.valueOf(numero);
        System.out.println(retornaNumeroInteiro.apply("15"));

        //retornar true or false
        Predicate<String> estaVazio = valor -> valor.isEmpty();
        System.out.println(estaVazio.test(""));
        System.out.println(estaVazio.test("Ada Wong"));

        Predicate<String> estaVazioReferencia = String::isEmpty;
        System.out.println(estaVazio.test(""));
        System.out.println(estaVazio.test("Ada Wong"));

        //Spridor não recebem parametro ,mais retorna algo
        //Supplier<Pessoa> sipplies = () -> new Pessoa();
        Supplier<Pessoa> sipplies = Pessoa::new;
        System.out.println(sipplies.get());

        //iterações entre funções
        System.out.println(Stream.of(nomes).filter(nome -> nome.equals("Pedro"))
                .collect(Collectors.joining()));
        //Foreach por stream
        Stream.of(nomes).forEach(System.out::println);

    }

}

class Pessoa {
    private String nome;
    private Integer idade;

    public Pessoa() {
        nome = "Ada Wong";
        idade = 19;
    }

    @Override
    public String toString() {
        return String.format("nome : %s, idade : %d", nome, idade);
    }
}
```
