
# 🚀 Fase 3: Tópicos Avançados

Na **Fase 3**, exploramos tópicos mais avançados em PHP que são essenciais para criar sistemas robustos, escaláveis e flexíveis. Vamos abordar conceitos cruciais como **Padrões de Projeto** (Design Patterns), **Autoloading** e **PSR-4**, que ajudarão a organizar e melhorar o seu código! 😎

## 🛠️ Padrões de Projeto (Design Patterns)

**Padrões de Projeto** são soluções comprovadas para problemas recorrentes no desenvolvimento de software. Eles tornam o código mais modular, reutilizável e fácil de entender. Vamos ver alguns padrões populares no PHP:

### 1. **Singleton** 🏠
- **Objetivo**: Garantir que uma classe tenha **apenas uma instância** e fornecer um ponto global de acesso a ela.
- **Exemplo**: Gerenciar a conexão com o banco de dados.

```php
class Database {
    private static $instance = null;

    private function __construct() {
        // Inicializa a conexão com o banco de dados
    }

    public static function getInstance() {
        if (self::$instance === null) {
            self::$instance = new Database();
        }
        return self::$instance;
    }
}
```

### 2. **Factory** 🏭
- **Objetivo**: Criar objetos **sem precisar especificar a classe exata**.
- **Exemplo**: Criar diferentes tipos de produtos em um e-commerce.

```php
interface Product {
    public function create();
}

class ConcreteProductA implements Product {
    public function create() {
        return "Produto A criado!";
    }
}

class ConcreteProductB implements Product {
    public function create() {
        return "Produto B criado!";
    }
}

class ProductFactory {
    public static function createProduct($type) {
        if ($type == 'A') {
            return new ConcreteProductA();
        } else {
            return new ConcreteProductB();
        }
    }
}
```

### 3. **Strategy** 🎯
- **Objetivo**: Permitir a seleção de um **algoritmo em tempo de execução**.
- **Exemplo**: Calcular diferentes formas de **desconto** em um sistema de vendas.

```php
interface DiscountStrategy {
    public function calculate($amount);
}

class NoDiscount implements DiscountStrategy {
    public function calculate($amount) {
        return $amount;
    }
}

class PercentageDiscount implements DiscountStrategy {
    public function calculate($amount) {
        return $amount * 0.9; // 10% de desconto
    }
}

class DiscountContext {
    private $strategy;

    public function __construct(DiscountStrategy $strategy) {
        $this->strategy = $strategy;
    }

    public function applyDiscount($amount) {
        return $this->strategy->calculate($amount);
    }
}
```

### 4. **Observer** 👀
- **Objetivo**: Permitir que **objetos sejam notificados** quando o estado de outro objeto mudar.
- **Exemplo**: Sistemas de **notificações**.

```php
interface Observer {
    public function update($message);
}

class ConcreteObserver implements Observer {
    public function update($message) {
        echo "Notificação recebida: $message";
    }
}

class Subject {
    private $observers = [];

    public function addObserver(Observer $observer) {
        $this->observers[] = $observer;
    }

    public function notify($message) {
        foreach ($this->observers as $observer) {
            $observer->update($message);
        }
    }
}
```

### 5. **MVC (Model-View-Controller)** 🖥️
- **Objetivo**: Separar a lógica de **negócio**, **interface do usuário** e **controle**.
- **Exemplo**: Uma das arquiteturas mais populares para desenvolvimento de **aplicativos web**.

- **Modelo**: Representa os **dados** e a lógica de **negócios**.
- **Visão**: Exibe os **dados** para o **usuário**.
- **Controlador**: Gerencia as interações entre **visão** e **modelo**.

---

## 🔧 Autoloading e PSR-4

### **Autoloading** no PHP
O **autoloading** permite carregar classes automaticamente quando necessário, sem a necessidade de usar `require` ou `include` manualmente. Isso facilita a organização e a performance do código.

### **Usando `spl_autoload_register()`** 🔄
A função `spl_autoload_register()` permite registrar uma função de autoload personalizada. Quando o PHP encontra uma classe que ainda não foi carregada, ele chama essa função para carregá-la automaticamente.

```php
function myAutoloader($class) {
    include 'classes/' . $class . '.class.php';
}

spl_autoload_register('myAutoloader');
```

### **Implementando PSR-4 para Autoloading** 📦
O PSR-4 define uma abordagem para organizar e carregar classes de forma padronizada, utilizando **namespaces** e **diretórios**.

#### Estrutura de Diretórios:
```
src/
    Acme/
        Foo.php
        Bar.php
```

#### Exemplo de Código PHP:
```php
namespace Acme;

class Foo {
    public function __construct() {
        echo "Classe Foo!";
    }
}
```

#### Arquivo `composer.json`:
```json
{
    "autoload": {
        "psr-4": {
            "Acme\\": "src/Acme/"
        }
    }
}
```

Após rodar o comando `composer dump-autoload`, o Composer cuidará do autoloading automaticamente!

---

## 📝 Resumo

- **Padrões de Projeto (Design Patterns)** são soluções estruturadas para problemas comuns, ajudando na manutenção e flexibilidade do código.
- **Autoloading** facilita o carregamento automático de classes, melhorando a organização e performance.
- **PSR-4** define como as classes devem ser organizadas em diretórios e como o autoloading funciona de maneira eficiente com o Composer.

Esses conceitos são essenciais para se tornar um **desenvolvedor PHP** mais eficiente e profissional. 🙌

---

🔗 **Links Úteis**:
- [PHP Design Patterns](https://refactoring.guru/design-patterns/php)
- [PSR-4 Autoloading Standard](https://www.php-fig.org/psr/psr-4/)
