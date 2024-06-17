
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





