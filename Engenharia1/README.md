1. Os termos engenharia de software e programação tem sido usados como se significassem as mesmas práticas, porém não é exatamente isso, na engenharia de software criam-se produtos reais e intangíveis quando comparados aos produtos de outras engenharias. 
A medida que a vida cotidiana tem cada vez mais e mais tecnologias integradas é preciso que os métodos sejam mais rigorosos. 

2. A engenharaia de software tem mais a ver com o desenvolvimento de um sistema do que apenas as linguagens de programação. Os rumos que um sistema pode tomar variam muito ao longo do tempo, desde as melhorias contínuas para os clientes quanto a escalabilidade que eventualmente pode ser necessária. Mesmo que o produto não seja tangível, o planejamento e desenvolvimento nessa etapa permitem que ele não seja vencido por adversidades, assim, se a necessidade seja alterar a tecnologia usada, novas funcionalidades, prover disponibilidade do programa para mais pessoas, etc, não trará uma dor de cabeça tão grande ao fazer as alterações.
Existem diversos métodos e técnicas para se fazer algo com programação, então, não quer dizer que uma seja melhor do que a outra, apenas que a necessidade de algo faz dela a melhor opção ou não de acordo com os recursos disponíveis e o contexto.

3. Exemplos:
Primeiro: Suporte técnico que é terceirizado por Software House. Ao invés de eles terem de investir em recursos e infraestrutura, é feito esse tipo de contrato de serviço para que a os resursos e infraestrutura do próprio Suporte sejam utilizados.

Segundo: Uso de armazenamento em nuvem e menos memória no dispositivo. Utilizando o armazenamento em nuvem não precisamos ter gastos muito grandes para ter memórias com capacidade e custos mais altos.

Terceiro: Escolhe entre Simplicidade no projeto ou melhor escalabilidade. Em determinados momentos do desenvolvimento de um sistema, precisa ser feita a escolha entre manter o sistema mais simples, porém com mais facilicade para escalabilidade. Assim, quando surgir a necessidade de escalabilidade o processo para fazê-la também será mais simples, e isso evita outros problemas como o tempo que o sistema precisa ficar offline para a atualização ou manutenção, por exemplo. 

4. Comentário do Slide 57: no slide vemos que a construção do produto ao longo das Sprints deve visar o valor definido pelo cliente. Nesse sentido, vemos que entregar partes do produto sem funcionalidade não se configura como entrega, mas se entregarmos protótipos levemente diferentes que resolvem o problema, conseguimos atingir o valor pedido pelo cliente e, ao fim, entregar o produto completo no molde original da ideia.  

5. Teste Java:

public class Morador {
    private String nome;
    private String apto;
    private String andar;
    
    public Morador(String nome, String apto, String andar) {
        this.nome = nome;
        this.apto = apto;
        this.andar = andar;
    }
    
    public String getNome() {
        return nome;
    }
    
    public String getApto() {
        return apto;
    }
    
    public String getAndar() {
        return andar;
    }
    
    public void setNome(String nome) {
        this.nome = nome;
    }
    
    public void setApto(String apto) {
        this.apto = apto;
    }
    
    public void setAndar(String andar) {
        this.andar = andar;
    }
}

public class Predio {
    
    private List<Morador> condominos = new LinkedList<Morador>();
    
    public void addMorador(Morador morador) {
        condominos.add(morador);
    }
    
    public Morador buscarApto(String apto) {
        for(Morador morador:condominos) {
            if(morador.getApto().equals(apto)) {
                return morador;
            }
        }
        return null;
    }
    
    public List<Morador> buscarAndar(String andar) {
        List<Morador> encontrados = new LinkedList<Morador>();
        for(Morador morador:condominos) {
            if(morador.getAndar().equals(andar)) {
                encontrados.add(morador);
            }
        }
        return null;
    }
    
    public List<Morador> getCondominos() {
        return condominos;
    }
    
}

public class NewJUnitTest {
    
    @Test
    void Teste() {
        Predio predio = new Predio();
        predio.addMorador(new Morador("João", "31", "Terceiro"));
        predio.addMorador(new Morador("Flora", "88", "Oitavo"));
        
        assertEquals(predio.getCondominos().size(), 2);
        
        Morador morador = predio.buscarApto("31");
        
        assertEquals(morador.getAndar(), "Terceiro");
    }
}
