
# Jackson Annotations
Utilizamos a anotação @JsonProperty no Jackson quando queremos utilizar um nome diferente para o atributo na serialização e deserialização de objetos JSON.
por exemplo:
```java
public class Pessoa {
    @JsonProperty("nome")
    private String nomeCompleto;
}
```
Neste caso, o atributo nomeCompleto será serializado e deserializado como "nome" no JSON.



Utilizamos a anotação @JsonAlias para definir um ou mais apelidos para o nome da propriedade JSON associada ao campo Java.
Por exemplo, se você tiver uma classe Java com a propriedade "nomeCompleto" e o JSON usa "nome" em vez disso, você pode usar o @JsonAlias("nome")
para mapear corretamente a propriedade. Dessa forma, tanto "nomeCompleto" quanto "nome" serão aceitos ao fazer o mapeamento.
```java
public class Pessoa {
    @JsonAlias({"nome", "nomeCompleto"})
    private String nomeCompleto;
}
```

# Generics
Generics é um recurso da linguagem Java que permite criar classes, interfaces e métodos que operam com tipos genéricos.
O principal objetivo de usar Generics é fornecer um tipo de parâmetro para classes, interfaces e métodos, permitindo que eles sejam reutilizados com diferentes tipos de dados.
Para criar um método ou classe genérico em Java, você deve usar a notação de tipo de parâmetro angular (<>) e especificar o tipo de parâmetro entre os sinais de menor e maior.
```java
public class Caixa<T> {
    private T conteudo;

    public T getConteudo() {
        return conteudo;
    }

    public void setConteudo(T conteudo) {
        this.conteudo = conteudo;
    }
}
```
No exemplo acima, podemos criar um objeto do tipo Caixa e armazenar qualquer tipo de valor no mesmo, veja um exemplo:
```java
public class TestaCaixa {
    public static void main(String[] args) {
        Caixa<String> caixaDeTexto = new Caixa<>();
        caixaDeTexto.setConteudo("Guardando texto na minha caixa!");

        Caixa<Integer> caixaDeIdade = new Caixa<>();
        caixaDeIdade.setConteudo(30);

        Caixa<Double> caixaDeValor = new Caixa<>();
        caixaDeValor.setConteudo(150.50);
    }
}
```

# Funções Lambda
Simplificam o código para torná-lo mais legível e conciso. As funções lambda são usadas principalmente para definir implementações de interfaces funcionais, 
que são interfaces com um único método abstrato.
Exemplo de uso de função lambda:
``` java
    List<Integer> lista = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9);

    for(Integer i: lista) {
      if(i % 2 == 0) {
        System.out.println(i);
      }
}
```
Utilizando uma função lambda:
``` java
    List<Integer> lista = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9);
    
    lista.stream().filter(i -> i % 2 == 0).forEach(System.out::println);
```
No código acima, criamos um stream da nossa lista, filtramos esse stream para incluir apenas os números pares (isso é feito pela função lambda i -> i % 2 == 0), 
e finalmente usamos o método forEach para printar cada elemento do stream filtrado.

Outros exemplos de funções lambda:
``` java
List<Integer> numeros = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);

List<Integer> numerosPares = numeros.stream()
                                   .filter(n -> n % 2 == 0)
                                   .collect(Collectors.toList());

System.out.println(numerosPares); // Output: [2, 4, 6, 8, 10]
```
``` java
List<String> palavras = Arrays.asList("Java", "Stream", "Operações", "Intermediárias");

List<Integer> tamanhos = palavras.stream()
                                .map(s -> s.length())
                                .collect(Collectors.toList());

System.out.println(tamanhos); // Output: [4, 6, 11, 17]
```
``` java
List<String> nomes = Arrays.asList("João", "Maria", "Pedro", "Ana");

nomes.stream()
     .forEach(nome -> System.out.println("Olá, " + nome + "!"));

// Output:
// Olá, João!
// Olá, Maria!
// Olá, Pedro!
// Olá, Ana!
```
``` java
List<Integer> numeros = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);

Set<Integer> numerosPares = numeros.stream()
                                   .filter(n -> n % 2 == 0)
                                   .collect(Collectors.toSet());

System.out.println(numerosPares); // Output: [2, 4, 6, 8, 10]
```

Uso > 
Você trabalha desenvolvendo aplicações em um banco digital e uma de suas tarefas é gerenciar e analisar de maneira eficiente uma enorme quantidade de dados referentes aos investimentos e saldos dos clientes, a fim de que se possa oferecer a eles linhas de crédito apropriadas ao saldo que possuem em conta.
Neste contexto, você deve filtrar os clientes com conta-corrente e ordená-los considerando o saldo, ordenando do maior para o menor, e, então, exibir os cinco clientes com maior saldo em conta.
Considerando que a variável dadosClientes já está populada com a lista completa de clientes e que os métodos para obter o tipo da conta e o saldo são o getTipoConta() e getSaldo(), respectivamente, qual dos seguintes códigos fará a funcionalidade corretamente?

``` java
dadosClientes.stream()
.filter(c -> c.getTipoConta().equalsIgnoreCase("corrente"))
.sorted(Comparator.comparingDouble(Conta::getSaldo).reversed())
.limit(5);
```









