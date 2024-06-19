
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






