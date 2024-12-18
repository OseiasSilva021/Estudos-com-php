# Composer e Gerenciamento de Dependências em PHP

#### **Instalação e Configuração do Composer**
O **Composer** é uma ferramenta de gerenciamento de dependências para PHP, que facilita a instalação de bibliotecas e pacotes e o gerenciamento das versões delas. Aqui está como você pode instalá-lo e configurá-lo:

1. **Instalação**:
   - **No Windows**: Baixe o instalador do Composer em [getcomposer.org](https://getcomposer.org/), e siga as instruções.
   - **No Linux/macOS**: Execute o seguinte comando no terminal:
     ```bash
     curl -sS https://getcomposer.org/installer | php
     ```
   - Para torná-lo globalmente acessível, mova o arquivo para uma pasta em seu PATH:
     ```bash
     mv composer.phar /usr/local/bin/composer
     ```

2. **Verificação da instalação**:
   Após a instalação, você pode verificar se o Composer está instalado corretamente com o comando:
   ```bash
   composer --version
   ```

#### **Gerenciamento de Pacotes e Dependências**
- O Composer permite que você instale, atualize e remova pacotes de maneira simples.
- Para instalar uma dependência, use:
  ```bash
  composer require nome/pacote
  ```
- Para atualizar todas as dependências para as versões mais recentes permitidas no `composer.json`:
  ```bash
  composer update
  ```
- Para remover uma dependência:
  ```bash
  composer remove nome/pacote
  ```

#### **Como Criar e Usar um Arquivo composer.json**
O arquivo `composer.json` é o coração do Composer, pois define as dependências e outras configurações de seu projeto. Exemplo básico:

```json
{
  "name": "seu/projeto",
  "description": "Descrição do seu projeto",
  "require": {
    "monolog/monolog": "^2.0"
  }
}
```

- `"name"`: Nome do projeto.
- `"description"`: Breve descrição do projeto.
- `"require"`: Define as dependências que seu projeto precisa. O Composer vai instalar automaticamente as versões que atendem aos requisitos definidos aqui.

#### **Trabalhando com Bibliotecas Externas**
Quando você adiciona uma dependência no arquivo `composer.json` (como mostrado acima), o Composer baixa e instala as bibliotecas para o diretório `vendor/`. Você pode usar essas bibliotecas em seu código com o autoload do Composer, assim:

```php
require 'vendor/autoload.php';

use Monolog\Logger;
use Monolog\Handler\StreamHandler;

$log = new Logger('nome_do_log');
$log->pushHandler(new StreamHandler('app.log', Logger::WARNING));
$log->warning('Foo');
```

Este exemplo usa a biblioteca Monolog para registrar logs.

---

### Testes em PHP

#### **Introdução a Testes Unitários com PHPUnit**
O **PHPUnit** é uma framework para testes unitários em PHP. Com ele, você pode escrever testes para garantir que seu código funcione como esperado.

1. **Instalação do PHPUnit**:
   Você pode instalar o PHPUnit via Composer:
   ```bash
   composer require --dev phpunit/phpunit
   ```

2. **Exemplo de Teste Unitário**:
   Crie um arquivo de teste em `tests/CalculatorTest.php`:
   ```php
   <?php
   use PHPUnit\Framework\TestCase;

   class CalculatorTest extends TestCase {
       public function testAddition() {
           $this->assertEquals(4, 2 + 2);
       }
   }
   ```

   Para rodar os testes, use o comando:
   ```bash
   vendor/bin/phpunit tests/CalculatorTest.php
   ```

#### **Criando Testes de Unidade, Testes de Integração e Testes de API**
- **Testes de Unidade**: Testam uma unidade específica de código (geralmente uma função ou classe isolada).
  - Exemplo: Testar se um método de soma retorna o valor correto.
  
- **Testes de Integração**: Testam a interação entre diferentes unidades de código, como interações com bancos de dados ou APIs externas.
  - Exemplo: Testar se o envio de um email funciona quando o banco de dados é atualizado.

- **Testes de API**: Testam se sua API está respondendo corretamente. Você pode usar PHPUnit para enviar requisições HTTP e verificar as respostas.
  ```php
  public function testApiReturnsJson() {
      $response = file_get_contents('http://api.exemplo.com/endpoint');
      $this->assertJson($response);
  }
  ```

#### **Testes de Comportamento com Behat**
O **Behat** é uma ferramenta para **testes de comportamento** (BDD - Behavior-Driven Development) em PHP. Ele permite escrever testes que descrevem o comportamento esperado de uma aplicação em uma linguagem mais próxima do natural.

1. **Instalação do Behat**:
   ```bash
   composer require --dev behat/behat
   ```

2. **Escrevendo um Teste de Comportamento**:
   Em `features/alguma_funcionalidade.feature`:
   ```gherkin
   Feature: Calculadora
     In order to avoid mistakes
     As a user
     I want to be able to add two numbers

   Scenario: Add two numbers
     Given I have entered 2
     And I have entered 3
     When I press add
     Then the result should be 5
   ```

   Em seguida, crie os contextos do Behat para mapear os passos, como no arquivo `features/bootstrap/FeatureContext.php`.

#### **Mocking e Stubbing**
- **Mocking**: Criação de objetos falsos (mocks) que simulam o comportamento de objetos reais, úteis para isolar partes do código durante os testes.
  - Exemplo com PHPUnit:
    ```php
    $mock = $this->createMock(ClasseDependente::class);
    $mock->method('metodo')->willReturn('valor');
    ```

- **Stubbing**: Semelhante ao mocking, mas mais simples. Você cria um stub para retornar um valor específico quando um método é chamado.
  - Exemplo com PHPUnit:
    ```php
    $stub = $this->createStub(ClasseDependente::class);
    $stub->method('metodo')->willReturn('valor');
    ```

Mocking e stubbing são especialmente úteis em testes unitários, quando você precisa isolar o código testado de suas dependências externas.

---

Esses são os fundamentos de **Composer** para gerenciamento de dependências e **testes em PHP** com PHPUnit, Behat, mocking e stubbing. Eles são essenciais para manter seu código modular, escalável e confiável, além de garantir que suas aplicações funcionem corretamente em todos os cenários.