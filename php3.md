# 🗃️ Introdução a Bancos de Dados com PHP

## 📌 Objetivos
Apresentar conceitos fundamentais de conexão, manipulação e segurança de dados em PHP utilizando bancos de dados MySQL.

## 1. Configuração e Conexão com MySQL 🔌

### 1.1 MySQLi (Orientado a Objetos)
Extensão nativa do PHP para interação com MySQL.

```php
$host = 'localhost';
$username = 'root';
$password = '';
$dbname = 'meu_banco';

// Conexão
$conn = new mysqli($host, $username, $password, $dbname);

// Verificar conexão
if ($conn->connect_error) {
    die("Falha na conexão: " . $conn->connect_error);
}
echo "Conexão bem-sucedida com MySQLi!";
```

### 1.2 PDO (PHP Data Objects)
Abordagem flexível que suporta múltiplos bancos de dados.

```php
$host = 'localhost';
$username = 'root';
$password = '';
$dbname = 'meu_banco';
$dsn = "mysql:host=$host;dbname=$dbname;charset=utf8mb4";

try {
    $pdo = new PDO($dsn, $username, $password);
    $pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
    echo "Conexão bem-sucedida com PDO!";
} catch (PDOException $e) {
    die("Falha na conexão: " . $e->getMessage());
}
```

## 2. Operações CRUD 📊

### 2.1 Inserir Dados (Create)
```php
$sql = "INSERT INTO usuarios (nome, email) VALUES (:nome, :email)";
$stmt = $pdo->prepare($sql);

$nome = 'Oséias';
$email = 'oseias@example.com';

$stmt->bindParam(':nome', $nome);
$stmt->bindParam(':email', $email);

$stmt->execute();
echo "Usuário inserido com sucesso!";
```

### 2.2 Buscar Dados (Read)
```php
$sql = "SELECT * FROM usuarios";
$stmt = $pdo->query($sql);

while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {
    echo "ID: " . $row['id'] . " - Nome: " . $row['nome'] . "<br>";
}
```

### 2.3 Atualizar Dados (Update)
```php
$sql = "UPDATE usuarios SET email = :email WHERE id = :id";
$stmt = $pdo->prepare($sql);

$id = 1;
$email = 'novoemail@example.com';

$stmt->bindParam(':email', $email);
$stmt->bindParam(':id', $id);

$stmt->execute();
echo "Usuário atualizado com sucesso!";
```

### 2.4 Deletar Dados (Delete)
```php
$sql = "DELETE FROM usuarios WHERE id = :id";
$stmt = $pdo->prepare($sql);

$id = 1;
$stmt->bindParam(':id', $id);

$stmt->execute();
echo "Usuário deletado com sucesso!";
```

## 3. Prevenção de SQL Injection 🛡️

### Consulta Insegura (Evite!)
```php
// NUNCA FAÇA ISSO
$sql = "SELECT * FROM usuarios WHERE nome = '$nome'";
```

### Consulta Segura
```php
$sql = "SELECT * FROM usuarios WHERE nome = :nome";
$stmt = $pdo->prepare($sql);
$stmt->bindParam(':nome', $nome);
$stmt->execute();
```

## 4. Transações 🔄

Garantir consistência em operações críticas com múltiplos passos.

```php
try {
    $pdo->beginTransaction();

    $sql1 = "INSERT INTO contas (usuario_id, saldo) VALUES (1, 1000)";
    $pdo->exec($sql1);

    $sql2 = "UPDATE usuarios SET ativo = 1 WHERE id = 1";
    $pdo->exec($sql2);

    $pdo->commit(); // Confirma todas as mudanças
    echo "Transação concluída com sucesso!";
} catch (Exception $e) {
    $pdo->rollBack(); // Reverte todas as mudanças
    echo "Transação falhou: " . $e->getMessage();
}
```

## 🌟 Boas Práticas

- 🔒 Sempre use declarações preparadas (prepared statements)
- 📡 Prefira PDO para maior flexibilidade
- 🚫 Evite concatenar valores diretamente em consultas SQL
- 🛡️ Trate exceções e erros de forma adequada
- 🔐 Configure corretamente os modos de erro do PDO

## 📚 Recursos Adicionais

- [Documentação Oficial do PDO](https://www.php.net/manual/pt_BR/book.pdo.php)
- [Guia de Segurança do PHP](https://www.php.net/manual/pt_BR/security.database.php)

## 🤝 Contribuições

Contribuições são bem-vindas! Sinta-se à vontade para abrir issues ou enviar pull requests.

## 📄 Licença

[Inserir informações da licença]
