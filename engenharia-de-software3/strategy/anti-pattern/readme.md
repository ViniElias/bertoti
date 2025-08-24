<img width="403" height="322" alt="image" src="https://github.com/user-attachments/assets/723e447e-7a6c-476a-9cb1-c2d74e160608" />

<br>

    public enum TipoFrete {
        SEDEX,
        PAC
    }

    // Classe com o Anti-Padrão
    public class Pedido {
        private double pesoTotal;
    
        public Pedido(double pesoTotal) {
            this.pesoTotal = pesoTotal;
        }
    
        // Método que concentra toda a lógica e viola o Princípio Aberto/Fechado
        public double calcularFrete(TipoFrete tipo) {
            double custoFrete = 0.0;
    
            switch (tipo) {
                case SEDEX:
                    // Lógica de cálculo para Sedex
                    custoFrete = 10.0 + (this.pesoTotal * 1.5);
                    break;
                case PAC:
                    // Lógica de cálculo para PAC
                    custoFrete = 5.0 + (this.pesoTotal * 1.1);
                    break;
                // Para adicionar um novo tipo (Ex: TRANSPORTADORA),
                // seria necessário adicionar um novo "case" aqui,
                // modificando a classe Pedido.
                default:
                    throw new IllegalArgumentException("Tipo de frete desconhecido.");
            }

<br>

    public class Loja {
        public static void main(String[] args) {
            Pedido pedido = new Pedido(5.5);
    
            // O cliente passa o tipo de frete como um parâmetro
            double custoSedex = pedido.calcularFrete(TipoFrete.SEDEX);
            System.out.println("Custo do frete com Sedex: R$ " + custoSedex);
    
            double custoPac = pedido.calcularFrete(TipoFrete.PAC);
            System.out.println("Custo do frete com PAC: R$ " + custoPac);
        }
    }
        return custoFrete;
    }
}
