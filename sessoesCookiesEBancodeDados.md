# Gerenciamento de Sessões, Cookies e Banco de Dados (MySQL) em PHP 🚀

## 📋 Gerenciamento de Sessões e Cookies

### **Sessões** 🖥️

As sessões são usadas para armazenar informações do usuário enquanto ele navega entre as páginas de um site. As informações são armazenadas no servidor.

- **`session_start()`**: Inicia uma nova sessão ou retoma uma sessão existente.
  ```php
  session_start(); // Inicia a sessão
  ```

- **`$_SESSION`**: Superglobal usada para armazenar dados da sessão. Esses dados ficam disponíveis enquanto a sessão estiver ativa.
  ```php
  $_SESSION['user'] = 'João'; // Armazena o nome do usuário na sessão
  echo $_SESSION['user']; // Exibe o nome do usuário
  ```

- **`session_destroy()`**: Finaliza a sessão e apaga todos os dados associados a ela.
  ```php
  session_start(); // Inicia a sessão
  session_unset(); // Limpa todas as variáveis de sessão
  session_destroy(); // Finaliza a sessão
  ```

### **Cookies** 🍪

Cookies são pequenos arquivos armazenados no navegador, permitindo salvar informações entre as visitas do usuário.

- **`setcookie()`**: Define um cookie. Exemplo:
  ```php
  setcookie('user', 'João', time() + 3600); // Cria um cookie 'user' que expira em 1 hora
  ```

- **`$_COOKIE`**: Superglobal usada para acessar os valores armazenados nos cookies.
  ```php
  echo $_COOKIE['user']; // Exibe o valor do cookie 'user'
  ```

### **Gerenciamento de Autenticação e Controle de Acesso** 🔐

- **Login e Autenticação**: Após validar o login (usando dados do banco), você pode armazenar o estado de autenticação em uma variável de sessão.
  ```php
  session_start();
  $_SESSION['user_logged_in'] = true;
  $_SESSION['username'] = 'João';
  ```

- **Protegendo Páginas**: Verifique se o usuário está autenticado antes de acessar páginas restritas.
  ```php
  session_start();
  if (!isset($_SESSION['user_logged_in'])) {
      header('Location: login.php'); // Redireciona para login
      exit();
  }
  ```

- **Logout**: Para desconectar o usuário, destrua a sessão.
  ```php
  session_start();
  session_unset();
  session_destroy();
  header('Location: login.php');
  exit();
  ```

---

## 💻 Trabalhando com Banco de Dados (MySQL)

### **Conexão com MySQL** 🛠️

- **Usando `mysqli`**:
  Para conectar ao banco de dados com `mysqli`, utilize `mysqli_connect()`.
  ```php
  $conn = mysqli_connect('localhost', 'usuario', 'senha', 'banco_de_dados');
  if (!$conn) {
      die('Erro de conexão: ' . mysqli_connect_error());
  }
  ```

- **Usando `PDO`**:
  O `PDO` é uma interface mais flexível e segura.
  ```php
  try {
      $conn = new PDO('mysql:host=localhost;dbname=banco_de_dados', 'usuario', 'senha');
      $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
  } catch (PDOException $e) {
      echo 'Erro de conexão: ' . $e->getMessage();
  }
  ```

### **Realizando Consultas** 🔍

- **SELECT**: Consulta para buscar dados do banco.
  ```php
  $query = "SELECT * FROM usuarios";
  $result = mysqli_query($conn, $query);
  while ($row = mysqli_fetch_assoc($result)) {
      echo $row['nome'];
  }
  ```

- **INSERT**: Insere dados no banco.
  ```php
  $query = "INSERT INTO usuarios (nome, email) VALUES ('João', 'joao@email.com')";
  mysqli_query($conn, $query);
  ```

- **UPDATE**: Atualiza dados no banco.
  ```php
  $query = "UPDATE usuarios SET nome='Carlos' WHERE id=1";
  mysqli_query($conn, $query);
  ```

- **DELETE**: Deleta dados do banco.
  ```php
  $query = "DELETE FROM usuarios WHERE id=1";
  mysqli_query($conn, $query);
  ```

### **Prevenção contra SQL Injection** 🚫

Para prevenir SQL Injection, use consultas preparadas.

- **Com `mysqli`**:
  ```php
  $stmt = mysqli_prepare($conn, "SELECT * FROM usuarios WHERE email = ?");
  mysqli_stmt_bind_param($stmt, 's', $email);
  $email = 'joao@email.com';
  mysqli_stmt_execute($stmt);
  $result = mysqli_stmt_get_result($stmt);
  ```

- **Com `PDO`**:
  ```php
  $stmt = $conn->prepare("SELECT * FROM usuarios WHERE email = :email");
  $stmt->bindParam(':email', $email);
  $email = 'joao@email.com';
  $stmt->execute();
  $result = $stmt->fetchAll();
  ```

### **Manipulação de Erros no MySQL** ⚠️

- **Com `mysqli`**:
  Para capturar erros de conexão e execução de consulta:
  ```php
  if (!$conn) {
      die('Erro de conexão: ' . mysqli_connect_error());
  }

  if (!mysqli_query($conn, $query)) {
      die('Erro na consulta: ' . mysqli_error($conn));
  }
  ```

- **Com `PDO`**:
  Configure o modo de erro para lançar exceções:
  ```php
  try {
      $conn = new PDO('mysql:host=localhost;dbname=banco_de_dados', 'usuario', 'senha');
      $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
      $conn->exec($query);
  } catch (PDOException $e) {
      echo 'Erro: ' . $e->getMessage();
  }
  ```

---

## 📝 Conclusão

Com essas práticas, você pode gerenciar **sessões** e **cookies** de forma eficiente, além de interagir com bancos de dados **MySQL** com segurança e desempenho. Essas são técnicas fundamentais para a construção de aplicações web robustas e seguras. 👨‍💻👩‍💻

---

> **Dica:** Não se esqueça de sempre testar e validar seu código, além de seguir boas práticas de segurança! 🔒
