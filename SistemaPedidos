import java.time.LocalDate; //PACOTE NECESSÁRIO PARA USAR O LOCALDATE 
import java.io.FileWriter; // PACOTE NECESSÁRIO PARA ESCREVER EM ARQUIVOS
import java.io.BufferedWriter;
import java.io.IOException;

// CLASSE CLIENTE
class Cliente{
    
    private String nome;
    private double telefone;
    private String endereco;
    
    // CONSTRUTOR
    public Cliente(String nome, double telefone, String endereco){
        
        this.nome = nome;
        this.telefone = telefone;
        this.endereco = endereco;
        
    }

    public String getNome()
    {
      return this.nome;
    }

    public double getTelefone()
    {
      return this.telefone;   
    }

    public String getEndereco()
    {
      return this.endereco;
    }
  
    // MÉTODO TO STRING PARA IMPRIMIR OS DADOS DOS CLIENTES
    public String toString(){
        return nome;
    }
    
}

// CLASSE PEDIDO 
class Pedido{
    
    int numero;
    Cliente cliente;
    LocalDate dataR = LocalDate.now(); // DATA DA REALIZAÇÃO DO PEDIDO
    LocalDate dataE = LocalDate.now(); // DATA DA ENTREGA DO PEDIDO
    double preco;
    int tipo = 0;
    
    // CONSTRUTOR PEDIDO PADRÃO
    public Pedido(int numero, Cliente cliente, LocalDate hoje, int preco) throws IOException{ // IGNORA AS EXCEÇÕES 
        
        this.numero = numero;
        this.cliente = cliente;
        this.dataR = hoje;
        this.preco = preco;
        this.tipo = 1; // PARA IDENTIFICAR O TIPO DO PEDIDO COMO PADRÃO
      
        FileWriter arquivo = new FileWriter("pedido" + this.numero + ".txt");
        BufferedWriter buffer = new BufferedWriter(arquivo);
        buffer.append("Pedido: " + Integer.toString(this.numero) + "\n");
        buffer.append("Cliente: " + this.cliente.getNome() + "\n");
        buffer.append("Telefone: " + Integer.toString((int)(this.cliente.getTelefone())) + "\n");
        buffer.append("Endereço: " + this.cliente.getEndereco() + "\n");
        buffer.append("Data da realização: " + this.dataR.toString() + "\n");
        buffer.append("Preço: " + Double.toString(this.preco) + "\n");
        buffer.close();
    }
    
    // CONSTRUTOR PEDIDO EXPRESSO
    public Pedido(int numero, Cliente cliente, LocalDate dataReal, LocalDate dataEntre, double preco) throws IOException{
        
        this.numero = numero;
        this.cliente = cliente;
        this.dataR = dataReal;
        this.dataE = dataEntre;
        this.preco = preco + (preco * 0.2); // PREÇO COM ACRÉSCIMO DE 20% 
        this.tipo = 2; // PARA IDENTIFICAR O TIPO DO PEDIDO COMO EXPRESSO 

        // GRAVANDOS OS DADOS NUM ARQUIVO TXT
        FileWriter arquivo = new FileWriter("pedido" + this.numero + ".txt");
        BufferedWriter buffer = new BufferedWriter(arquivo);
        buffer.append("Pedido: " + Integer.toString(this.numero) + "\n");
        buffer.append("Cliente: " + this.cliente.getNome() + "\n");
        buffer.append("Telefone: " + Integer.toString((int)this.cliente.getTelefone()) + "\n");
        buffer.append("Endereço: " + this.cliente.getEndereco() + "\n");
        buffer.append("Data da realização: " + this.dataR.toString() + "\n");
        buffer.append("Data de entrega: " + this.dataE.toString() + "\n");
        buffer.append("Preço: " + Double.toString(this.preco) + "\n");
        buffer.close();
    }
    
    // MÉTODO TO STRING PARA IMPRIMIR OS DADOS DO PEDIDO
    public String toString(){
        
        String frase =  "Nome: " + cliente + "\nPreço: " + preco + "\n";
        
        if(this.tipo == 2){ // SE O PEDIDO FOR DO TIPO 2 = EXPRESSO
            if(Prazo.calcular(dataR, dataE)){ // SE O PEDIDO TIVER SIDO ENTREGUE NO PRAZO
                frase = frase + "Foi entregue no prazo!\n"; // FRASE RECEBE "FOI ENTREGUE NO PRAZO"
            }else{ // SE NÃO TIVER SIDO ENTREGUE NO PRAZO
                frase = frase + "Não foi entregue no prazo!\n"; // FRASE RECEBE "NÃO FOI ENTREGUE NO PRAZO"
            }
            
        }
        
        return frase;
    }
    
}

// MÉTODO PARA VERIFICAR SE OS PEDIDOS FORAM ENTREGUES NO PRAZO
class Prazo{
    
    public static boolean calcular(LocalDate dataReal, LocalDate dataEntre){
        
        if(dataReal == dataEntre){ // SE A DATA DA REALIZAÇÃO DO PEDIDO E A DATA DE ENTREGA FOREM IGUAIS:
            return true; // RETORNA VERDADEIRO
        }else{ // SE NÃO FOREM: 
            return false; //RETORNA FALSO
        }

    }
}

class Sistema
{
	public static void main (String[] args) throws java.lang.Exception
	{
	  // CRIANDO OS NOVOS CLIENTES 
		Cliente fulano = new Cliente("Fulano", 9999, "Rua A");
		Cliente ciclano = new Cliente("Ciclano", 8888, "Rua B");
        
    // DEFININDO DATAS
    LocalDate hoje = LocalDate.now(); // DATA DE HOJE
    LocalDate ontem = hoje.minusDays(1); // DATA DE ONTEM --> SUBTRAINDO UM DIA DA DATA "HOJE"
    
    // CRIANDO OS PEDIDOS 
    Pedido pedidoFulano = new Pedido(1, fulano, hoje, 500);
    Pedido pedidoCiclano = new Pedido(2, ciclano, hoje, hoje, 500);
    
    
    // IMPRIMINDO O CADASTRO DOS PEDIDOS 
    System.out.println(pedidoFulano); // System.out.println(pedidoFulano.toString()); 
    System.out.println(pedidoCiclano);
    
	}
}
