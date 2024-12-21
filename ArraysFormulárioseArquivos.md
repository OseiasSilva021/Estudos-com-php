# Manipulação de Arrays, Formulários e Arquivos em PHP 🚀

## Manipulação de Arrays 🧮

### 1. **Arrays Indexados e Associativos**
- **Arrays Indexados**: Arrays com índices numéricos (iniciando do 0).
  ```php
  $frutas = ["maçã", "banana", "laranja"];
  echo $frutas[0]; // saída: maçã
  ```

- **Arrays Associativos**: Arrays com índices como strings.
  ```php
  $idades = ["João" => 25, "Maria" => 30, "Pedro" => 22];
  echo $idades["João"]; // saída: 25
  ```

### 2. **Funções para Arrays 🔧**
- **`array_push()`**: Adiciona elementos no final de um array.
  ```php
  $frutas = ["maçã", "banana"];
  array_push($frutas, "laranja", "uva");
  print_r($frutas); // saída: Array ( [0] => maçã [1] => banana [2] => laranja [3] => uva )
  ```

- **`array_pop()`**: Remove o último elemento de um array.
  ```php
  $frutas = ["maçã", "banana", "laranja"];
  array_pop($frutas);
  print_r($frutas); // saída: Array ( [0] => maçã [1] => banana )
  ```

- **`array_merge()`**: Junta dois ou mais arrays.
  ```php
  $frutas1 = ["maçã", "banana"];
  $frutas2 = ["laranja", "uva"];
  $todasFrutas = array_merge($frutas1, $frutas2);
  print_r($todasFrutas); // saída: Array ( [0] => maçã [1] => banana [2] => laranja [3] => uva )
  ```

- **`in_array()`**: Verifica se um valor existe em um array.
  ```php
  $frutas = ["maçã", "banana", "laranja"];
  if (in_array("banana", $frutas)) {
    echo "Banana encontrada!";
  }
  ```

- **`array_map()`**: Aplica uma função a cada elemento de um array.
  ```php
  $numeros = [1, 2, 3, 4];
  $quadrados = array_map(fn($n) => $n ** 2, $numeros);
  print_r($quadrados); // saída: Array ( [0] => 1 [1] => 4 [2] => 9 [3] => 16 )
  ```

- **`array_filter()`**: Filtra os elementos de um array usando uma função de callback.
  ```php
  $numeros = [1, 2, 3, 4, 5];
  $pares = array_filter($numeros, fn($n) => $n % 2 === 0);
  print_r($pares); // saída: Array ( [1] => 2 [3] => 4 )
  ```

---

## Manipulação de Formulários e Entradas do Usuário 📝

### 1. **Recebendo Dados de Formulários com `$_POST` e `$_GET`**
- **`$_POST`**: Para dados de formulários com o método POST.
  ```php
  if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $nome = $_POST["nome"];
    echo "Olá, $nome!";
  }
  ```

- **`$_GET`**: Para dados de formulários com o método GET.
  ```php
  if (isset($_GET["nome"])) {
    $nome = $_GET["nome"];
    echo "Olá, $nome!";
  }
  ```

### 2. **Validação e Filtragem de Entradas 🛡️**
- **Validação**: Garantir que os dados sejam válidos.
  ```php
  if (empty($_POST["email"])) {
    echo "O campo email é obrigatório!";
  } else {
    if (!filter_var($_POST["email"], FILTER_VALIDATE_EMAIL)) {
      echo "Email inválido!";
    }
  }
  ```

- **Filtragem**: Limpar os dados recebidos.
  ```php
  $nome = filter_var($_POST["nome"], FILTER_SANITIZE_STRING);
  $email = filter_var($_POST["email"], FILTER_SANITIZE_EMAIL);
  ```

### 3. **CSRF e XSS 🛑**
- **CSRF (Cross-Site Request Forgery)**: Proteção contra requisições indesejadas.
  ```php
  $_SESSION['token'] = bin2hex(random_bytes(32));
  ```

  Adicionar o token ao formulário:
  ```php
  <input type="hidden" name="token" value="<?php echo $_SESSION['token']; ?>">
  ```

  Verificar o token no servidor:
  ```php
  if ($_POST['token'] !== $_SESSION['token']) {
    echo "Token inválido!";
    exit;
  }
  ```

- **XSS (Cross-Site Scripting)**: Proteção contra injeção de scripts maliciosos.
  ```php
  echo htmlspecialchars($nome, ENT_QUOTES, 'UTF-8');
  ```

---

## Trabalhando com Arquivos 📂

### 1. **Abertura, Leitura, Escrita e Manipulação de Arquivos**
- **`fopen()`**: Abre um arquivo.
  ```php
  $arquivo = fopen("arquivo.txt", "r"); // "r" para leitura
  ```

- **`fread()`**: Lê o conteúdo de um arquivo.
  ```php
  $conteudo = fread($arquivo, filesize("arquivo.txt"));
  echo $conteudo;
  fclose($arquivo);
  ```

- **`fwrite()`**: Escreve em um arquivo.
  ```php
  $arquivo = fopen("arquivo.txt", "w"); // "w" para escrita
  fwrite($arquivo, "Novo conteúdo");
  fclose($arquivo);
  ```

- **`file_get_contents()`**: Lê o conteúdo de um arquivo e retorna como string.
  ```php
  $conteudo = file_get_contents("arquivo.txt");
  echo $conteudo;
  ```

- **`file_put_contents()`**: Escreve em um arquivo (substituindo o conteúdo existente).
  ```php
  file_put_contents("arquivo.txt", "Novo conteúdo");
  ```

---

### 🚀 Conclusão
Com esses conceitos e funções, você pode manipular arrays, receber dados de formulários, proteger sua aplicação contra ataques e trabalhar com arquivos de forma eficiente e segura em PHP. 💻🔒
