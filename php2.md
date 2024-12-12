# 📦 Manipulação de Dados em PHP

## 🎯 Objetivo
Trabalhar com dados de forma eficiente e segura utilizando recursos do PHP.

## 1. Arrays 🔢

### 1.1 Arrays Associativos
Arrays com chaves personalizadas (strings) ao invés de índices numéricos.

```php
$usuario = [
    "nome" => "Oséias",
    "idade" => 18,
    "profissao" => "Programador"
];
echo $usuario["nome"]; // Oséias
```

### 1.2 Arrays Multidimensionais
Arrays dentro de arrays para estruturas complexas.

```php
$usuarios = [
    ["nome" => "João", "idade" => 25],
    ["nome" => "Maria", "idade" => 30],
    ["nome" => "Oséias", "idade" => 18]
];
echo $usuarios[2]["nome"]; // Oséias
```

### 1.3 Métodos Úteis

#### array_map()
Aplica uma função a cada elemento de um array.

```php
$numeros = [1, 2, 3];
$quadrados = array_map(fn($n) => $n ** 2, $numeros);
print_r($quadrados); // [1, 4, 9]
```

#### array_filter()
Filtra elementos de um array com base em uma condição.

```php
$numeros = [1, 2, 3, 4, 5];
$pares = array_filter($numeros, fn($n) => $n % 2 === 0);
print_r($pares); // [2, 4]
```

## 2. Strings 📝

### Funções Importantes

#### substr()
Extrai uma parte de uma string.

```php
echo substr("Oséias", 0, 3); // Osé
```

#### str_replace()
Substitui partes de uma string.

```php
echo str_replace("mundo", "Oséias", "Olá, mundo!"); // Olá, Oséias!
```

#### explode() e implode()
Divide e junta strings.

```php
$dados = "nome,idade,profissao";
print_r(explode(",", $dados)); // ["nome", "idade", "profissao"]

$array = ["PHP", "é", "incrível"];
echo implode(" ", $array); // PHP é incrível
```

## 3. Superglobais 🌐

### 3.1 $_GET
Dados enviados via URL.

```php
// URL: site.com?nome=Oséias
echo $_GET['nome']; // Oséias
```

### 3.2 $_POST
Dados enviados via formulário.

```php
if ($_SERVER['REQUEST_METHOD'] === 'POST') {
    echo $_POST['nome'];
}
```

### 3.3 $_SERVER
Informações do servidor e ambiente.

```php
echo $_SERVER['HTTP_USER_AGENT']; // Navegador do usuário
```

## 4. Formulários 📋

### 4.1 Validação de Dados

```php
if (empty($_POST['email'])) {
    echo "O campo email é obrigatório.";
} elseif (!filter_var($_POST['email'], FILTER_VALIDATE_EMAIL)) {
    echo "Formato de email inválido.";
}
```

### 4.2 Tratamento de Entradas

#### Prevenção de XSS
Sempre escape as saídas.

```php
echo htmlspecialchars($_POST['nome']);
```

#### Prevenção de SQL Injection
Use prepared statements.

```php
$stmt = $pdo->prepare("SELECT * FROM usuarios WHERE email = :email");
$stmt->execute(['email' => $_POST['email']]);
$usuario = $stmt->fetch();
```

## 🚀 Boas Práticas
- Sempre valide e filtre entradas de usuário
- Use prepared statements para consultas SQL
- Escape saídas HTML para prevenir XSS
- Utilize funções nativas do PHP para manipulação de dados

## 📚 Recursos Adicionais
- [Documentação Oficial do PHP](https://www.php.net/manual/pt_BR/)
- [Manual de Segurança PHP](https://www.php.net/manual/pt_BR/security.php)

## 👥 Contribuições
Sinta-se à vontade para propor melhorias ou adicionar exemplos!

## 📄 Licença
[Inserir informação de licença]
