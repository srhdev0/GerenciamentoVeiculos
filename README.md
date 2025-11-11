# UlbraProgramacaoObj
Estrutura de Classes
/src
 ├── Veiculo.java
 ├── Carro.java
 ├── Moto.java
 └── Main.java

Classe Abstrata
// Arquivo: Veiculo.java
public abstract class Veiculo {
    // Atributos
    public String marca;
    public String modelo;
    private int ano;

    // Construtor
    public Veiculo(String marca, String modelo, int ano) {
        this.marca = marca;
        this.modelo = modelo;
        this.ano = ano;
    }

    // Getter e Setter para o ano
    public int getAno() {
        return ano;
    }

    public void setAno(int ano) {
        this.ano = ano;
    }

    // Método abstrato (sem corpo)
    public abstract String informacoesVeiculo();
}
abstract  não pode ser instanciada diretamente.

public e private conforme pedido.

informacoesVeiculo() será implementado pelas subclasses.

Classe Carro
// Arquivo: Carro.java
public class Carro extends Veiculo {
    public int numeroPortas;

    public Carro(String marca, String modelo, int ano, int numeroPortas) {
        super(marca, modelo, ano); // chama o construtor da classe mãe (Veiculo)
        this.numeroPortas = numeroPortas;
    }

    @Override
    public String informacoesVeiculo() {
        return "Carro: " + marca + " " + modelo +
               " (" + getAno() + "), " +
               numeroPortas + " portas.";
    }
}
Usa super(...) para inicializar os atributos herdados.

Implementa informacoesVeiculo() retornando todos os dados.

Classe Moto
// Arquivo: Moto.java
public class Moto extends Veiculo {
    private int cilindrada;

    public Moto(String marca, String modelo, int ano, int cilindrada) {
        super(marca, modelo, ano);
        this.cilindrada = cilindrada;
    }

    public int getCilindrada() {
        return cilindrada;
    }

    public void setCilindrada(int cilindrada) {
        this.cilindrada = cilindrada;
    }

    @Override
    public String informacoesVeiculo() {
        return "Moto: " + marca + " " + modelo +
               " (" + getAno() + "), " +
               cilindrada + "cc.";
    }
}
cilindrada é privado, conforme solicitado.

Usa getCilindrada() e setCilindrada() para acesso seguro.

Classe Main
// Arquivo: Main.java
public class Main {
    public static void main(String[] args) {
        // Instanciando um Carro
        Carro carro = new Carro("Toyota", "Corolla", 2020, 4);

        // Instanciando uma Moto
        Moto moto = new Moto("Honda", "CB 500", 2022, 500);

        // Exibindo as informações
        System.out.println(carro.informacoesVeiculo());
        System.out.println(moto.informacoesVeiculo());
    }
}


Saída Esperada
Carro: Toyota Corolla (2020), 4 portas.
Moto: Honda CB 500 (2022), 500cc.
