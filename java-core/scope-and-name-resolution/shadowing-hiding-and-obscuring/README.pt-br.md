
# Hiding, Shadowing e Obscuring em Java: você sabe a diferença?

Muitas vezes usamos esses conceitos sem perceber, mas enternder a mecânica por trás deles evita bugs silenciosos e te ajuda a dominar o escopo da linguagem.

  ## Shadowing
  Ocorre quando uma variável em um escopo mais interno (como um método) tem o mesmo nome de uma variável em um escopo mais externo(como um campo da classe). A variável interna "esconde" a externa.

  - **Como resolver**: Use o prefixo ``` this ```
  
  ```java
  public class Exemplo {
    String nome = "Global";

    void setNome(String nome) {
        // O parâmetro 'nome' faz shadow no campo 'nome' da classe
        this.nome = nome; 
    }
   }
  ```

  ## Hiding
  Quando um método estático em uma subclasse tem o mesmo nome e assinatura de um método estático na superclasse. Não há overrride, mas sim *hiding*.

  ```java
  class Pai {
    static void mostrar() { System.out.println("Pai"); }
    }
    class Filho extends Pai {
        static void mostrar() { System.out.println("Filho"); } // hiding
    }

  ```
  ### Diferença entre ocultação e sobrescrita
  **Sobrescrita** (override)
  * só métodos de **instância**
  * resilvido em tempo de execução
  * Depende de **objeto real**

  **Ocultação** (hiding)
  * só métodos **static**
  * resolvido em tempo de compilação
  * depende do tipo de **referência**

  ## Obscuring
  É o caso mais raro e ocorre quando um nome pode ser interpretado de várias formas (como uma classe e um pacote, ou uma variável e uma classe com o mesmon nome). Java segue regras de precedência para decidir quem ganha.

  - Siga as convenções de nomenclatura (CamelCase para classes, lowerCase para variáveis) e você quase nunca rerá esse problema!

## Veja mais

[Java documentação JLS - 6.4. Shadowing and Obscuring](https://download.java.net/java/early_access/jdk27/docs/specs/jls/jls-6.html#jls-6.4)

[Java documentação JSL - 8.4.8.2. Hiding (by Class Methods)](https://download.java.net/java/early_access/jdk27/docs/specs/jls/jls-8.html#jls-8.4.8)

---

>by *Thiago Pompeu*


