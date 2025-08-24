<img width="715" height="439" alt="image" src="https://github.com/user-attachments/assets/56e4060c-88e3-4a81-ad6c-cc970497bfb2" />

<br>

    // Strategy Interface
    public interface CalculadoraFrete {
        double calcular(double peso);
    }

<br>

    // ConcreteStrategy A
    public class FreteSedex implements CalculadoraFrete {
        @Override
        public double calcular(double peso) {
            // Lógica de cálculo para Sedex: taxa fixa + taxa por peso
            return 10.0 + (peso * 1.5);
        }
    }
    
    <br>
    
    // ConcreteStrategy B
    public class FretePAC implements CalculadoraFrete {
        @Override
        public double calcular(double peso) {
            // Lógica de cálculo para PAC: taxa fixa + taxa por peso (mais barata)
            return 5.0 + (peso * 1.1);
        }
    }

<br>

    // Context
    public class Pedido {
        private double pesoTotal;
        private CalculadoraFrete estrategiaFrete;
    
        public Pedido(double pesoTotal) {
            this.pesoTotal = pesoTotal;
        }
    
        // Permite ao cliente definir a estratégia em tempo de execução
        public void setEstrategiaFrete(CalculadoraFrete estrategiaFrete) {
            this.estrategiaFrete = estrategiaFrete;
        }
    
        public double calcularFrete() {
            if (estrategiaFrete == null) {
                throw new IllegalStateException("A estratégia de frete não foi definida.");
            }
            // Delega o cálculo para o objeto da estratégia
            return estrategiaFrete.calcular(this.pesoTotal);
        }
    }

<br>

    public class Loja {
        public static void main(String[] args) {
            Pedido pedido = new Pedido(5.5); // Pedido com 5.5 kg
    
            // Cliente escolhe a estratégia Sedex
            pedido.setEstrategiaFrete(new FreteSedex());
            System.out.println("Custo do frete com Sedex: R$ " + pedido.calcularFrete());
    
            // Cliente decide mudar a estratégia para PAC
            pedido.setEstrategiaFrete(new FretePAC());
            System.out.println("Custo do frete com PAC: R$ " + pedido.calcularFrete());
        }
    }
