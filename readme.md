# 🚀 Fase 1: Fundamentos de PHP (Básico) 💻

Este guia aborda os **fundamentos essenciais** de PHP para iniciantes. Aqui, você aprenderá o que é PHP, como configurá-lo e entenderá as estruturas básicas de código para começar a programar. 

## 1. 📝 Introdução ao PHP

### O que é PHP? 🤔
PHP (Hypertext Preprocessor) é uma linguagem de programação amplamente usada para **desenvolvimento web**. Ela é executada no servidor, gerando conteúdo dinâmico para o navegador. Ideal para sites interativos como blogs, lojas virtuais e sistemas de gerenciamento de conteúdo.

### Configuração do Ambiente de Desenvolvimento 🛠️
Para rodar PHP no seu computador, você precisa de um **servidor local**. Algumas opções populares são:

- **XAMPP**: Apache, MySQL e PHP.
- **WAMP**: Similar ao XAMPP, mas exclusivo para Windows.
- **MAMP**: Versão para Mac.
- **Docker**: Ambiente isolado para criação de containers (Apache, PHP, MySQL).

### Como Criar e Executar Scripts PHP 🖥️
1. Crie um arquivo com a extensão `.php` (por exemplo, `index.php`).
2. Escreva o código PHP:
   ```php
   <?php
   echo "Olá, mundo!";
   ?>
   ```
3. Coloque o arquivo na pasta do servidor (geralmente `htdocs` ou `www`).
4. Acesse via navegador: `http://localhost/nomedoarquivo.php`.

## 2. 🛠️ Sintaxe Básica

### Variáveis, Tipos de Dados e Operadores 🔢
- **Variáveis**: Usadas para armazenar dados. Exemplo:
  ```php
  $nome = "João";
  $idade = 25;
  ```

- **Tipos de Dados**:
  - **String**: "Olá"
  - **Inteiro**: 10
  - **Float**: 10.5
  - **Booleano**: `true` ou `false`
  - **Array**: `[1, 2, 3]`
  - **Objeto**: Instâncias de classes.

- **Operadores**:
  - **Aritméticos**: `+`, `-`, `*`, `/`, `%`
  - **Relacionais**: `==`, `!=`, `>`, `<`, `>=`, `<=`
  - **Lógicos**: `&&` (E), `||` (OU), `!` (NÃO)

### Estruturas Condicionais 🧠

- **if, else, else if**: Controle de fluxo.
  ```php
  if ($idade >= 18) {
      echo "Maior de idade";
  } else {
      echo "Menor de idade";
  }
  ```

- **switch**: Alternativa ao `if-else` para múltiplas condições.
  ```php
  switch ($idade) {
      case 18:
          echo "Adulto";
          break;
      case 17:
          echo "Menor";
          break;
      default:
          echo "Idade desconhecida";
          break;
  }
  ```

### Estruturas de Repetição 🔁

- **for**: Repete um bloco de código por um número fixo de vezes.
  ```php
  for ($i = 0; $i < 5; $i++) {
      echo $i;
  }
  ```

- **while**: Repete enquanto a condição for verdadeira.
  ```php
  $i = 0;
  while ($i < 5) {
      echo $i;
      $i++;
  }
  ```

- **foreach**: Usado para percorrer arrays.
  ```php
  $numeros = [1, 2, 3, 4, 5];
  foreach ($numeros as $numero) {
      echo $numero;
  }
  ```

### Funções e Parâmetros 🔧

- **Funções**: Blocos de código reutilizáveis.
  ```php
  function saudacao($nome) {
      return "Olá, " . $nome;
  }
  echo saudacao("Maria");
  ```

- **Funções Anônimas (Closures)**: Funções sem nome, frequentemente usadas como callback ou em arrays.
  ```php
  $soma = function($a, $b) {
      return $a + $b;
  };
  echo $soma(2, 3);  // Saída: 5
  ```

---

## 📚 Resumo dos Fundamentos de PHP (Básico)

- **Configuração do Ambiente**: Instale XAMPP, WAMP, MAMP ou Docker para configurar o PHP.
- **Sintaxe Básica**: Conheça as variáveis, tipos de dados e operadores essenciais.
- **Estruturas Condicionais e de Repetição**: Controle o fluxo do programa com `if`, `else`, `switch`, `for`, `while`, e `foreach`.
- **Funções**: Organize e reutilize seu código com funções.

Com esses **fundamentos**, você está pronto para avançar no aprendizado do PHP e começar a criar aplicações dinâmicas e interativas! 🚀
