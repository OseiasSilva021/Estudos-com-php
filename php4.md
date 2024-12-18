# 📚 Fase 2: Conceitos Intermediários de Programação

## 💡 Funções e Escopos

### 🔥 Funções Anônimas e Closures

- **Funções Anônimas**: São funções sem nome, normalmente usadas como parâmetros ou atribuídas a variáveis. Útil para comportamentos temporários.
  ```php
  $soma = function($a, $b) {
      return $a + $b;
  };
  echo $soma(2, 3); // Saída: 5
  ```

- **Closures**: São funções que capturam variáveis do escopo onde foram definidas. Elas podem acessar e modificar essas variáveis.
  ```php
  $valor = 10;
  $multiplicar = function($a) use ($valor) {
      return $a * $valor;
  };
  echo $multiplicar(2); // Saída: 20
  ```

### 🔄 Passagem por Valor e Referência

- **Passagem por Valor**: A função recebe uma cópia do valor da variável. Alterações dentro da função não afetam a variável original.
  ```php
  function dobrar($num) {
      $num = $num * 2;
  }
  $x = 5;
  dobrar($x);
  echo $x; // Saída: 5
  ```

- **Passagem por Referência**: A função recebe uma referência da variável, permitindo modificar seu valor original.
  ```php
  function dobrar(&$num) {
      $num = $num * 2;
  }
  $x = 5;
  dobrar($x);
  echo $x; // Saída: 10
  ```

### 🔄 Funções Recursivas

Funções recursivas chamam a si mesmas. Elas são úteis para problemas que podem ser divididos em subproblemas similares, como o cálculo do fatorial.
  ```php
  function fatorial($n) {
      if ($n <= 1) {
          return 1;
      }
      return $n * fatorial($n - 1);
  }
  echo fatorial(5); // Saída: 120
  ```

---

## 🧩 Orientação a Objetos (OOP)

### 🏗️ Definição de Classes e Objetos

- **Classe**: Modelo ou estrutura que define propriedades e comportamentos dos objetos.
  ```php
  class Carro {
      public $cor;
      public $modelo;
  
      public function ligar() {
          echo "Carro ligado!";
      }
  }
  $carro = new Carro();
  $carro->cor = 'azul';
  $carro->modelo = 'Fusca';
  $carro->ligar(); // Saída: Carro ligado!
  ```

- **Objeto**: Instância de uma classe. No exemplo, `$carro` é um objeto da classe `Carro`.

### 🛠️ Construtores e Destruidores

- **Construtores**: Inicializam o objeto no momento de sua criação.
  ```php
  class Carro {
      public $modelo;
  
      public function __construct($modelo) {
          $this->modelo = $modelo;
      }
  }
  $carro = new Carro("Fusca");
  echo $carro->modelo; // Saída: Fusca
  ```

- **Destruidores**: São chamados quando o objeto é destruído, frequentemente usados para liberar recursos.
  ```php
  class Carro {
      public function __destruct() {
          echo "Carro destruído!";
      }
  }
  $carro = new Carro();
  unset($carro); // Saída: Carro destruído!
  ```

### 🔑 Propriedades e Métodos

- **Propriedades**: Variáveis dentro de uma classe que guardam o estado do objeto.
- **Métodos**: Funções que definem os comportamentos dos objetos.
  ```php
  class Carro {
      public $cor;
  
      public function pintar($cor) {
          $this->cor = $cor;
      }
  }
  $carro = new Carro();
  $carro->pintar('vermelho');
  echo $carro->cor; // Saída: vermelho
  ```

### 🔓 Visibilidade (Público, Privado, Protegido)

- **Público** (`public`): Pode ser acessado de qualquer lugar.
- **Privado** (`private`): Só pode ser acessado dentro da classe.
- **Protegido** (`protected`): Acessível dentro da classe e por classes filhas.
  ```php
  class Carro {
      private $modelo;
  
      public function setModelo($modelo) {
          $this->modelo = $modelo;
      }
  
      public function getModelo() {
          return $this->modelo;
      }
  }
  ```

### 🧬 Herança, Polimorfismo e Encapsulamento

- **Herança**: Permite que uma classe herde as propriedades e métodos de outra.
  ```php
  class Carro {
      public $modelo;
      public function ligar() {
          echo "Carro ligado!";
      }
  }
  class CarroEsportivo extends Carro {
      public function acelerar() {
          echo "Acelerando!";
      }
  }
  ```

- **Polimorfismo**: Permite que a mesma ação tenha comportamentos diferentes em classes distintas.
  ```php
  class Animal {
      public function falar() {
          echo "Animal falando";
      }
  }
  class Cachorro extends Animal {
      public function falar() {
          echo "Au Au!";
      }
  }
  ```

- **Encapsulamento**: Controla o acesso a propriedades e métodos da classe, protegendo o estado interno.
  ```php
  class ContaBancaria {
      private $saldo;
  
      public function depositar($valor) {
          $this->saldo += $valor;
      }
  
      public function getSaldo() {
          return $this->saldo;
      }
  }
  ```

### 📝 Interfaces e Classes Abstratas

- **Interface**: Define um contrato para classes implementarem, ou seja, uma lista de métodos obrigatórios.
  ```php
  interface Veiculo {
      public function mover();
  }
  class Carro implements Veiculo {
      public function mover() {
          echo "Carro em movimento";
      }
  }
  ```

- **Classe Abstrata**: Não pode ser instanciada diretamente e pode conter métodos abstratos.
  ```php
  abstract class Forma {
      abstract public function desenhar();
  }
  
  class Circulo extends Forma {
      public function desenhar() {
          echo "Desenhando círculo";
      }
  }
  ```

### ⚙️ Traits

- **Traits**: Permitem que métodos sejam compartilhados entre várias classes sem a necessidade de herança.
  ```php
  trait Aceleracao {
      public function acelerar() {
          echo "Acelerando!";
      }
  }
  
  class Carro {
      use Aceleracao;
  }
  
  $carro = new Carro();
  $carro->acelerar(); // Saída: Acelerando!
  ```

---

## 🚀 Conclusão

Esses conceitos são essenciais para dominar a programação orientada a objetos e criar soluções robustas e reutilizáveis! Aprofundar-se nesses tópicos ajudará a transformar você em um programador mais completo e eficiente. Continue praticando e explorando novas possibilidades! 💻✨
