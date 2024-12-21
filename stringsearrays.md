# Manipulação de Strings e Arrays em PHP 💻

## ✨ Manipulação de Strings:

### Funções para manipulação de strings 🔧

- **`strlen()`**: Retorna o comprimento de uma string (número de caracteres).
  ```php
  $str = "Olá, Mundo!";
  echo strlen($str); // Exibe 12
  ```

- **`substr()`**: Retorna uma parte (substring) de uma string, com base na posição inicial e no comprimento.
  ```php
  $str = "Olá, Mundo!";
  echo substr($str, 0, 3); // Exibe "Olá"
  ```

- **`strpos()`**: Encontra a posição da primeira ocorrência de uma substring em uma string. Retorna `false` se a substring não for encontrada.
  ```php
  $str = "Olá, Mundo!";
  echo strpos($str, "Mundo"); // Exibe 5
  ```

- **`str_replace()`**: Substitui todas as ocorrências de uma substring em uma string por outra substring.
  ```php
  $str = "Olá, Mundo!";
  echo str_replace("Mundo", "PHP", $str); // Exibe "Olá, PHP!"
  ```

### Concatação e Interpolação de Strings 🔗

- **Concatação**: Concatenar strings usando o operador `.` (ponto).
  ```php
  $str1 = "Olá";
  $str2 = "Mundo!";
  $resultado = $str1 . " " . $str2; // Exibe "Olá Mundo!"
  ```

- **Interpolação**: Você pode interpolar variáveis dentro de strings utilizando aspas duplas `""`. Isso não funciona com aspas simples `''`.
  ```php
  $nome = "Mundo";
  echo "Olá, $nome!"; // Exibe "Olá, Mundo!"
  ```

---

## 🌟 Manipulação de Arrays:

### Arrays Indexados e Associativos 🧮

- **Arrays indexados**: São arrays onde os índices são números inteiros, começando geralmente de 0.
  ```php
  $frutas = ["Maçã", "Banana", "Laranja"];
  echo $frutas[1]; // Exibe "Banana"
  ```

- **Arrays associativos**: São arrays onde os índices são strings (chaves associadas a valores).
  ```php
  $idades = ["João" => 25, "Maria" => 30, "Pedro" => 28];
  echo $idades["Maria"]; // Exibe 30
  ```

### Funções para Arrays ⚙️

- **`array_push()`**: Adiciona um ou mais elementos no final de um array.
  ```php
  $arr = [1, 2, 3];
  array_push($arr, 4, 5); // Exibe [1, 2, 3, 4, 5]
  ```

- **`array_pop()`**: Remove o último elemento de um array.
  ```php
  $arr = [1, 2, 3];
  array_pop($arr); // Exibe [1, 2]
  ```

- **`array_merge()`**: Mescla dois ou mais arrays.
  ```php
  $arr1 = [1, 2];
  $arr2 = [3, 4];
  $arr3 = array_merge($arr1, $arr2); // Exibe [1, 2, 3, 4]
  ```

- **`in_array()`**: Verifica se um valor existe em um array. Retorna `true` ou `false`.
  ```php
  $arr = [1, 2, 3];
  if (in_array(2, $arr)) {
      echo "Encontrado!"; // Exibe "Encontrado!"
  }
  ```

- **`array_map()`**: Aplica uma função em todos os elementos de um array e retorna um novo array.
  ```php
  $arr = [1, 2, 3];
  $novoArr = array_map(function($item) {
      return $item * 2;
  }, $arr); // Exibe [2, 4, 6]
  ```

- **`array_filter()`**: Filtra os elementos de um array com base em uma função de callback e retorna um novo array com os valores que passaram no filtro.
  ```php
  $arr = [1, 2, 3, 4, 5];
  $filtrado = array_filter($arr, function($item) {
      return $item % 2 == 0; // Filtra números pares
  }); // Exibe [2, 4]
  ```

---

### 🔥 Dicas Extras:

- As funções de manipulação de **strings** são úteis para validar e transformar dados antes de exibi-los ou armazená-los no banco de dados.
- **Arrays** são fundamentais para armazenar listas de dados, e as funções do PHP oferecem diversas maneiras de manipular essas listas de forma eficiente.
- Utilize **concatação** e **interpolação** para formar strings dinâmicas e dinâmicas que mudam conforme as variáveis.
- Não se esqueça de explorar as funções para arrays como **`array_map()`** e **`array_filter()`** para manipular os dados de forma funcional! 💡

---

🚀 **Explore mais sobre PHP e continue aprendendo!**
