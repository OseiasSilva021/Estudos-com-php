# 🚀 PHP Orientado a Objetos (OOP)

## 📌 Introdução

Programação Orientada a Objetos (OOP) é um paradigma que organiza código em classes e objetos, promovendo:
- 🔁 Reutilização de código
- 🛠️ Manutenibilidade
- 📦 Organização estrutural

## 1. Classes e Objetos 📦

### Definição
- **Classe**: Molde para criar objetos
- **Objeto**: Instância de uma classe

### Exemplo Básico
```php
class Car {
    public $color; // Propriedade

    public function drive() { // Método
        echo "The car is driving.";
    }
}

$car = new Car(); // Criando um objeto
$car->color = "Red"; // Definindo valor da propriedade
echo $car->color; // Acessando a propriedade
$car->drive(); // Chamando o método
```

## 2. Propriedades e Métodos 🛠️

### Propriedades
Variáveis que armazenam dados relacionados ao objeto.

### Métodos
Funções que definem comportamentos do objeto.

### Exemplo
```php
class Person {
    public $name; // Propriedade
    public $age;

    public function greet() { // Método
        echo "Hello, my name is " . $this->name;
    }
}

$person = new Person();
$person->name = "John";
$person->greet(); // Hello, my name is John
```

## 3. Visibilidade 🔐

### Tipos de Visibilidade
- **public**: Acessível de qualquer lugar
- **private**: Acessível apenas dentro da classe
- **protected**: Acessível na classe e subclasses

### Exemplo
```php
class BankAccount {
    private $balance = 0; // Somente a classe pode acessar

    public function deposit($amount) {
        $this->balance += $amount;
    }

    public function getBalance() {
        return $this->balance;
    }
}

$account = new BankAccount();
$account->deposit(100);
echo $account->getBalance(); // 100
```

## 4. Herança 🌳

### Conceito
- Permite que uma classe herde propriedades e métodos de outra
- **Subclasse**: Classe que herda
- **Superclasse**: Classe herdada

### Exemplo
```php
class Animal {
    public function eat() {
        echo "Eating...";
    }
}

class Dog extends Animal {
    public function bark() {
        echo "Barking...";
    }
}

$dog = new Dog();
$dog->eat(); // Método herdado
$dog->bark(); // Método próprio
```

## 5. Interfaces e Classes Abstratas 📋

### Interface
Contrato que define métodos sem implementação.

```php
interface Logger {
    public function log($message);
}

class FileLogger implements Logger {
    public function log($message) {
        echo "Logging to a file: $message";
    }
}
```

### Classe Abstrata
Base para outras classes, pode conter métodos implementados ou abstratos.

```php
abstract class Shape {
    abstract public function calculateArea(); // Método abstrato

    public function describe() {
        echo "I am a shape.";
    }
}

class Circle extends Shape {
    public function calculateArea() {
        return 3.14 * 5 * 5;
    }
}
```

## 6. Namespaces e Autoloading (PSR-4) 🗂️

### Namespaces
Organizam classes em grupos lógicos.

```php
namespace App\Models;

class User {
    public function getName() {
        return "John Doe";
    }
}

// Uso
use App\Models\User;
$user = new User();
```

### Autoloading com Composer

#### 1. Estrutura de Diretórios
```
src/
├── Models/
│   └── User.php
└── Controllers/
    └── HomeController.php
```

#### 2. Configuração composer.json
```json
{
    "autoload": {
        "psr-4": {
            "App\\": "src/"
        }
    }
}
```

#### 3. Comandos Composer
```bash
# Gerar autoload
composer dump-autoload

# Usar no código
require 'vendor/autoload.php';

use App\Models\User;
$user = new User();
```

## 🌟 Boas Práticas

- 📦 Use classes para organizar código
- 🔒 Utilize visibilidade adequada
- 🔁 Aproveite herança e composição
- 🤝 Implemente interfaces quando apropriado
- 🧩 Mantenha classes coesas e com responsabilidades únicas

## 📚 Recursos Adicionais

- [Documentação Oficial PHP - OOP](https://www.php.net/manual/pt_BR/language.oop5.php)
- [PSR-4 Autoloader](https://www.php-fig.org/psr/psr-4/)
- [Composer Autoloading](https://getcomposer.org/doc/04-schema.md#autoload)

## 🤝 Contribuições

Contribuições são bem-vindas! Abra issues ou envie pull requests.

## 📄 Licença

[Inserir informações da licença]
