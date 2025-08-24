<img width="733" height="460" alt="image" src="https://github.com/user-attachments/assets/3ae389a7-0266-4919-a9b8-143b10392312" />

<br>

      class GerenciadorDeLeiloes {
          private List<Produto> produtos = new ArrayList<>();
          private List<Licitante> licitantes = new ArrayList<>();
      
          public void adicionarProduto(Produto produto) {
              produtos.add(produto);
          }
      
          public void adicionarLicitante(Licitante licitante) {
              licitantes.add(licitante);
          }
      
          public void darLance(Produto produto, Licitante licitante, double valor) {
              // Lógica de validação do lance
              if (valor > produto.getLanceAtual()) {
                  produto.setLanceAtual(valor);
                  // Notifica todos os licitantes sobre o lance em um produto específico
                  notificarTodos("Novo lance de R$ " + valor + " para o produto " + produto.getNome() + " por " + licitante.getNome());
              }
          }
      
          private void notificarTodos(String mensagem) {
              for (Licitante licitante : licitantes) {
                  licitante.receberNotificacao(mensagem);
              }
          }
          
          // ... muitos outros métodos que controlam tudo sobre leilões
      }
      
      class Produto {
          private String nome;
          private double lanceAtual;
      
          public Produto(String nome, double lanceAtual) {
              this.nome = nome;
              this.lanceAtual = lanceAtual;
          }
      
          public String getNome() {
              return nome;
          }
      
          public double getLanceAtual() {
              return lanceAtual;
          }
      
          public void setLanceAtual(double lanceAtual) {
              this.lanceAtual = lanceAtual;
          }
      }
      
      class Licitante {
          private String nome;
      
          public Licitante(String nome) {
              this.nome = nome;
          }
      
          public String getNome() {
              return nome;
          }
      
          public void receberNotificacao(String mensagem) {
              System.out.println(nome + ", você recebeu uma notificação: " + mensagem);
          }
      }

  <br>

    public class LeilaoCentralizado {
      public static void main(String[] args) {
          GerenciadorDeLeiloes gerenciador = new GerenciadorDeLeiloes();
  
          Produto produto1 = new Produto("Notebook Gamer", 2500.00);
          Produto produto2 = new Produto("Smartphone", 1500.00);
  
          Licitante licitante1 = new Licitante("João");
          Licitante licitante2 = new Licitante("Maria");
  
          gerenciador.adicionarProduto(produto1);
          gerenciador.adicionarProduto(produto2);
          gerenciador.adicionarLicitante(licitante1);
          gerenciador.adicionarLicitante(licitante2);
  
          gerenciador.darLance(produto1, licitante1, 2600.00);
          gerenciador.darLance(produto2, licitante2, 1600.00);
      }
    }
