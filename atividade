import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

class Quarto {
    private String tipo; // "Solteiro" ou "Casal"
    private double valorDiariaBase;
    private boolean temArCondicionado;
    private boolean temHidromassagem;
    private int numeroDeCamas; // Usado para "Solteiro"
    private boolean temBerco; // Usado para "Casal"

    // Construtor para quarto solteiro
    public Quarto(double valorDiariaBase, boolean temArCondicionado, boolean temHidromassagem, int numeroDeCamas) {
        this.tipo = "Solteiro";
        this.valorDiariaBase = valorDiariaBase;
        this.temArCondicionado = temArCondicionado;
        this.temHidromassagem = temHidromassagem;
        this.numeroDeCamas = numeroDeCamas;
        this.temBerco = false;
    }

    // Construtor para quarto casal
    public Quarto(double valorDiariaBase, boolean temArCondicionado, boolean temHidromassagem, boolean temBerco) {
        this.tipo = "Casal";
        this.valorDiariaBase = valorDiariaBase;
        this.temArCondicionado = temArCondicionado;
        this.temHidromassagem = temHidromassagem;
        this.temBerco = temBerco;
        this.numeroDeCamas = 1; // Um casal sempre terá uma cama
    }

    // Calcula o valor da diária com os adicionais
    public double calcularValorDiaria(double valorAdicionalAr, double valorAdicionalHidro) {
        double valor = valorDiariaBase;
        if (temArCondicionado) {
            valor += valorAdicionalAr;
        }
        if (temHidromassagem) {
            valor += valorAdicionalHidro;
        }
        return valor;
    }

    // Getters
    public String getTipo() {
        return tipo;
    }

    public boolean temArCondicionado() {
        return temArCondicionado;
    }

    public boolean temHidromassagem() {
        return temHidromassagem;
    }

    public int getNumeroDeCamas() {
        return numeroDeCamas;
    }

    public boolean temBerco() {
        return temBerco;
    }
}

class Residencia {
    private String endereco;
    private String numero;
    private String bairro;
    private String cep;
    private String telefone;
    private String email;
    private List<Quarto> quartos;
    private double valorDiariaCasal;
    private double valorDiariaSolteiro;
    private double valorAdicionalAr;
    private double valorAdicionalHidro;

    public Residencia(String endereco, String numero, String bairro, String cep, String telefone, String email,
                      double valorDiariaCasal, double valorDiariaSolteiro, double valorAdicionalAr, double valorAdicionalHidro) {
        this.endereco = endereco;
        this.numero = numero;
        this.bairro = bairro;
        this.cep = cep;
        this.telefone = telefone;
        this.email = email;
        this.quartos = new ArrayList<>();
        this.valorDiariaCasal = valorDiariaCasal;
        this.valorDiariaSolteiro = valorDiariaSolteiro;
        this.valorAdicionalAr = valorAdicionalAr;
        this.valorAdicionalHidro = valorAdicionalHidro;
    }

    public void adicionarQuarto(Quarto quarto) {
        quartos.add(quarto);
    }

    public double getValorDiariaCasal() {
        return valorDiariaCasal;
    }

    public double getValorDiariaSolteiro() {
        return valorDiariaSolteiro;
    }

    public double getValorAdicionalAr() {
        return valorAdicionalAr;
    }

    public double getValorAdicionalHidro() {
        return valorAdicionalHidro;
    }

    public List<Quarto> getQuartos() {
        return quartos;
    }
}

class Cliente {
    private String nome;
    private String cpf;
    private String endereco;
    private String telefone;
    private String email;

    public Cliente(String nome, String cpf, String endereco, String telefone, String email) {
        this.nome = nome;
        this.cpf = cpf;
        this.endereco = endereco;
        this.telefone = telefone;
        this.email = email;
    }

    // Getters
    public String getNome() {
        return nome;
    }

    public String getCpf() {
        return cpf;
    }
}

public class SistemaAluguel {
    public static void main(String[] args) {
        // Criando algumas residências
        Residencia residencia1 = new Residencia("Rua ", "123", "Bairro 1", "12345-678", "(11) 1234-5678", "residencia1@email.com", 100, 80, 20, 30);
        Residencia residencia2 = new Residencia("Rua B", "456", "Bairro 2", "23456-789", "(11) 2345-6789", "residencia2@email.com", 120, 90, 25, 35);
        Residencia residencia3 = new Residencia("Rua C", "789", "Bairro 3", "34567-890", "(11) 3456-7890", "residencia3@email.com", 110, 85, 22, 32);

        // Adicionando quartos às residências
        residencia1.adicionarQuarto(new Quarto(80, true, true, 1)); // Solteiro
        residencia1.adicionarQuarto(new Quarto(100, true, false, 1)); // Solteiro
        residencia2.adicionarQuarto(new Quarto(90, true, true, 1)); // Solteiro
        residencia2.adicionarQuarto(new Quarto(120, false, true, false)); // Casal
        residencia3.adicionarQuarto(new Quarto(85, true, true, 1)); // Solteiro
        residencia3.adicionarQuarto(new Quarto(110, false, false, true)); // Casal

        // Criando cliente
        Cliente cliente = new Cliente("Carlos Souza", "123.456.789-00", "Rua X", "(11) 4567-8901", "cliente@email.com");

        // Leitura dos dados de aluguel
        Scanner scanner = new Scanner(System.in);
        System.out.print("Escolha o número da residência (1-3): ");
        int escolhaResidencia = scanner.nextInt();
        Residencia residenciaEscolhida = (escolhaResidencia == 1) ? residencia1 : (escolhaResidencia == 2) ? residencia2 : residencia3;

        System.out.print("Escolha o número do quarto (1-" + residenciaEscolhida.getQuartos().size() + "): ");
        int escolhaQuarto = scanner.nextInt();

        Quarto quartoEscolhido = residenciaEscolhida.getQuartos().get(escolhaQuarto - 1);

        System.out.print("Data e horário de entrada (ex: 12/07/2024 13h42min): ");
        scanner.nextLine(); // Limpar o buffer
        String entrada = scanner.nextLine();

        System.out.print("Data e horário de saída (ex: 15/07/2024 11h50min): ");
        String saida = scanner.nextLine();

        System.out.print("Número de diárias: ");
        int numDiarias = scanner.nextInt();

        // Cálculo do valor total
        double valorDiaria = quartoEscolhido.calcularValorDiaria(residenciaEscolhida.getValorAdicionalAr(), residenciaEscolhida.getValorAdicionalHidro());
        double total = valorDiaria * numDiarias;

        // Exibindo recibo
        System.out.println("\nRecibo de Pagamento:");
        System.out.println("Data e horário de entrada: " + entrada);
        System.out.println("Data e horário de saída: " + saida);
        System.out.println("Número de diárias: " + numDiarias);
        System.out.println("Total a pagar: R$" + total);
    }
}
