![image](https://github.com/user-attachments/assets/2d72b7c3-4ad8-4e39-b7c2-6bc69ede7ebb)Atividade 1 - We see three critical differences between programming and software engineering: time, scale, and the trade-offs at play. On a software engineering project, engineers need to be more concerned with the passage of time and the eventual need for change. In a software engineering organization, we need to be more concerned about scale and efficiency, both for the software we produce as well as for the organization that is producing it. Finally, as software engineers, we are asked to make more complex decisions with higher-stakes outcomes, often based on imprecise estimates of time and growth.

Comentário: A engenharia de software valoriza mais o tempo de trabalho e sua relação com a eficiência, e profissionais dessa área trabalham com valores mais significativos de resultados, quando comparados com profissionais de programação.

Within Google, we sometimes say, “Software engineering is programming integrated over time.” Programming is certainly a significant part of software engineering: after all, programming is how you generate new software in the first place. If you accept this distinction, it also becomes clear that we might need to delineate between programming tasks (development) and software engineering tasks (development, modification, maintenance). The addition of time adds an important new dimension to programming. Cubes aren’t squares, distance isn’t velocity. Software engineering isn’t programming.

Comentário: Programação é uma parte da engenharia de software, porém aliada com a manutenção e modificação do que foi produzido. Novamente, nesse ramo o tempo se torna um aspecto valioso do trabalho.

Atividade 2 - Exemplos de trade-offs: 
1 - Python x Java - Python é uma linguagem de programação mais fácil de entender, porém de processamento mais lento. É adequado no caso de aprendizagem e tarefas mais simples, porém com um leque de possibilidades menor.
2 - Windows x Linux - Windows é um SO mais conhecido e amigável ao usuário, porém apresenta uma menor estabilidade e confiabilidade quando comparado ao Linux em um contexto de servidores.
3 - MySQL x MongoDB - MySQL possui uma maior integridade e consistência dos dados, porém apresentar uma menor flexibidade quando comparado ao MongoDB.

Atividade 3 - Trade-offs da arquitetura da Netflix
![Arquitetura Netflix](./netflix.jpg_large)
A arquitetura geral da Netflix é separada em diferentes seções específicas para cada área. Dentro dessas seções são utilizadas diferentes linguagens de acordo com suas vantagens naquele contexto. Observa-se a divisão em: Frontend (API, mobile, web), Backend (serviços, banco de dados, comunicação/streaming), Streaming (video, transcodificador), Big Data (armazenamento de dados, processamento de dados) e CI/CD (desenvolvimento e operações). Para cada uma dessas vertentes menores, são escolhidas as linguagens que melhor se adequam à sua função. Vale ressaltar que nenhum dos serviços utilizados é isento de desvantagens/defeitos, mas são escolhidos pontualmente visando suas tarefas especializadas.

Atividade 4 - Classes UML
d
d
d
d
d
d
d


package Bertoti;
public class Produto{
    private String id;
    private String nome;
    public String getId(){
        return id;
    }
    public String getNome(){
        return nome;
    }
    public void setId(String i){
        id=i;
    }
    public void setNome(String n){
        nome=n;
    }
}

package Bertoti;
import java.util.List;
import java.util.LinkedList;

public class Loja {
    private List<Produto> produtos = new LinkedList<Produto>();
    public void adicionarProduto(Produto produto){
        produtos.add(produto);
    }
    public List<Produto> buscarProdutoPorID(String id){
        List<Produto> encontrados = new LinkedList<Produto>();
        for(Produto produto: produtos){
            if(produto.getId().equals(id))encontrados.add(produto);
        }
        return encontrados;
    }
}

import java.util.List;
import java.util.LinkedList;

public class Loja {
    private List<Produto> produtos = new LinkedList<>();
    public void adicionarProduto(Produto produto){
        if (produto != null) {
            produtos.add(produto);
        }
    }
    public List<Produto> buscarProdutoPorID(String id){
        List<Produto> encontrados = new LinkedList<>();
        if (id != null) {
            for (Produto produto : produtos) {
                if (id.equals(produto.getId())) {
                    encontrados.add(produto);
                }
            }
        }
        return encontrados;
    }
}
![Captura de tela 2024-08-23 082836](https://github.com/user-attachments/assets/86855392-2aab-4efb-8e52-6f179494aa7d)
