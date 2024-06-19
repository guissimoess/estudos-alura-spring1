
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

# Datas
Para trabalhar com datas, podemos importar o pacote que possui diversas classes de data e hora, o java.time.
Os formatos de data e hora são especificados por strings padrão de data e hora
Exemplo:
```java
import java.text.SimpleDateFormat;
import java.util.Date;

public class Datas {

    public static void main(String[] args) {

        String pattern = "E, dd MMM yyyy HH:mm:ss z";
        SimpleDateFormat simpleDateFormat = new SimpleDateFormat(pattern);
        String date = simpleDateFormat.format(new Date());
        System.out.println(date);

    }
}
```

O output seria:  sáb., 19 nov. 2022 02:58:14 BRT”:

LocalDate: representa uma data sem fuso horário no sistema do calendário ISO 8601 tem como formato padrão yyyy-MM-dd. Essa classe não armazena 
ou representa uma hora ou fuso horário. Em vez disso, é uma descrição da data, normalmente usada para aniversários.

```java
import java.time.LocalDate;

public class Datas {

    public static void main(String[] args) {

        LocalDate hoje = LocalDate.now();
        System.out.println(hoje);

    }
}
```
O código acima cria um objeto LocalDate que representa a data atual e imprime a data no formato yyyy-MM-dd.



Criando datas:

Agora, vamos criar uma nova data para representar a data de um aniversário. Para isso, importaremos o pacote java.time.month;
```java
import java.time.LocalDate;
import java.time.Month;

public class Datas {
    
    public static void main(String[] args) {

        LocalDate hoje = LocalDate.now();
        System.out.println(hoje);

        LocalDate aniversarioAlice = LocalDate.of(2005, Month.SEPTEMBER, 15);
        System.out.println(aniversarioAlice);
    }
}
```
O código acima cria um objeto LocalDate que representa a data de aniversário de Alice e imprime a data no formato yyyy-MM-dd. (2005-09-15)



Também podemos brincar com esse código e calcular a idade atual da aniversariante. Uma forma de fazer isso na mão seria subtraindo o método getYear das datas, dessa forma:
```java
import java.time.LocalDate;
import java.time.Month;

public class Datas {
    public static void main(String[] args) {
        LocalDate hoje = LocalDate.now();
        System.out.println(hoje);

        LocalDate aniversarioAlice = LocalDate.of(2005, Month.SEPTEMBER, 15);
        System.out.println(aniversarioAlice);

        int idade =  hoje.getYear() - aniversarioAlice.getYear();
        System.out.println(idade);
    }

}
```

O resultado também será:
2022-11-19
2005-09-15
17


Período:
Ao executar esse código temos o resultado esperado, que neste caso é 17 anos. Mas e se quiséssemos descobrir a diferença de dias e meses também? 
Daria pra fazer da mesma forma utilizando o get, no entanto, existe algo pronto para nos ajudarmos. Nesse caso, podemos utilizar a classe Period.

Para saber a diferença entre duas datas podemos utilizar seu método between, da seguinte forma:
```java
import java.time.LocalDate;
import java.time.Month;
import java.time.Period;

public class Datas {
    public static void main(String[] args) {
        LocalDate hoje = LocalDate.now();
        System.out.println(hoje);

        LocalDate aniversarioAlice = LocalDate.of(2005, Month.SEPTEMBER, 15);
        System.out.println(aniversarioAlice);

        int idade = aniversarioAlice.getYear() - hoje.getYear();
        System.out.println(idade);

        Period periodo = Period.between(hoje, aniversarioAlice);
        System.out.println(periodo);

    }
}
```


LocalTime:
O local time representa um horário, seu formato padrão é hh:mm:ss.zzz.

Horário atual
Assim como fizemos com o LocalDate, dessa vez vamos imprimir o horário atual:
```java
import java.time.LocalTime;

public class Horarios {

    public static void main(String[] args) {
        LocalTime hoje = LocalTime.now();
        System.out.println(hoje);
    }
}
```

Criando horários:
Agora, vamos criar um novo horário para representar as horas em que Alice nasceu:
```java
import java.time.LocalTime;

public class Horarios {

    public static void main(String[] args) {
        LocalTime hoje = LocalTime.now();
        System.out.println(hoje);

        LocalTime aniversarioHoraAlice = LocalTime.of(22, 33, 15);
        System.out.println(aniversarioHoraAlice);
    }
}
```
22:33:15 


LocalDateTime

O LocalDateTime representa uma data com a hora, visto como ano-mês-dia-hora-minuto-segundo. O tempo é representado como yyyy-MM-dd-HH-mm-ss.zzz.
```java
import java.time.LocalDateTime;

public class DataHorario {

    public static void main(String[] args) {
        LocalDateTime hoje = LocalDateTime.now();
        System.out.println(hoje);
    }
}
```
2022-11-19T04:11:17.108565200


DateTimeFormatter
Você deve ter notado que os resultados estão em formatos que não estamos acostumados a trabalhar. Podemos então trabalhar com diversos formatadores de datas existentes!

``` java
DateTimeFormatter formatador = DateTimeFormatter.ofPattern("dd/MM/yyyy hh:mm:ss");

import java.time.LocalDateTime;
import java.time.format.DateTimeFormatter;

public class Formatando {

    public static void main(String[] args) {
        LocalDateTime hoje = LocalDateTime.now();
        System.out.println(hoje);

        DateTimeFormatter formatador = DateTimeFormatter.ofPattern("dd/MM/yyyy hh:mm:ss");
        LocalDateTime agora = LocalDateTime.now();
        System.out.println(hoje.format(formatador));

    }
}
```

19/11/2022 04:38:11













