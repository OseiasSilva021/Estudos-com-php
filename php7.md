
# 🌐 **APIs e Integrações: Criar e Consumir APIs RESTful com PHP** 🚀

## 1. 🛠️ **Criação de uma API RESTful** 🖥️

Criar uma **API RESTful** com **PHP** envolve estruturar endpoints que seguem os padrões **REST**. As **APIs RESTful** utilizam os métodos **HTTP** (**GET**, **POST**, **PUT**, **DELETE**) para realizar operações em recursos. Para isso, é necessário:

### 🗂️ **Estruturar o Projeto**:
Organize os arquivos em pastas para separação lógica. Exemplo:

```bash
/api
   /controllers
   /models
   /routes
   /public (index.php)
```

### 🔧 **Configurar o Roteamento**:
Use bibliotecas como **Slim Framework** ou **Laravel**, ou implemente manualmente um roteador. O roteador associa os endpoints às funções apropriadas.

### 🏗️ **Definir o Banco de Dados**:
Utilize **PDO** ou uma **ORM** como **Eloquent** para interagir com o banco de dados.

### 📡 **Exemplo de Endpoint Básico**:

```php
header('Content-Type: application/json');

if ($_SERVER['REQUEST_METHOD'] === 'GET') {
    echo json_encode(['message' => 'API funcionando!']);
}
```

---

## 2. 🔄 **Métodos HTTP: GET, POST, PUT, DELETE** ⚙️

### 📚 **Cada método é utilizado para uma ação específica**:

- **GET**: Recupera dados 📑
- **POST**: Cria novos dados ✍️
- **PUT**: Atualiza dados existentes 🔄
- **DELETE**: Remove dados ❌

### 🧑‍💻 **Exemplo com PHP puro para cada método**:

```php
header('Content-Type: application/json');

switch ($_SERVER['REQUEST_METHOD']) {
    case 'GET':
        echo json_encode(['message' => 'Recuperar dados']);
        break;
    case 'POST':
        echo json_encode(['message' => 'Criar dados']);
        break;
    case 'PUT':
        echo json_encode(['message' => 'Atualizar dados']);
        break;
    case 'DELETE':
        echo json_encode(['message' => 'Deletar dados']);
        break;
    default:
        http_response_code(405); // Método não permitido
        echo json_encode(['error' => 'Método não suportado']);
}
```

---

## 3. 🔄 **Serialização com JSON** 📦

A **serialização** transforma objetos ou arrays em um formato **JSON** para serem enviados pela **API**.

### 📝 **Para respostas**:

```php
$data = ['nome' => 'Oséias', 'idade' => 18];
echo json_encode($data);
```

### 📥 **Para requisições**:

```php
$json = file_get_contents('php://input');
$data = json_decode($json, true); // Decodifica em array
```

### ⚡ **Dicas**:
- Sempre use **json_encode()** para enviar respostas.
- Utilize **json_decode()** com o parâmetro **true** para **arrays** associativos.

---

## 4. 🔐 **Autenticação de APIs com JWT** 🔑

**JWT (JSON Web Token)** é um método comum de autenticação em **APIs**. Um token **JWT** contém informações codificadas que o servidor verifica para autenticar um usuário.

### 🛠️ **Passos para implementar JWT em PHP**:

#### 🔄 **Instalar a Biblioteca**:
Use **Firebase JWT**. Instale via **Composer**:

```bash
composer require firebase/php-jwt
```

#### 📝 **Gerar o Token**:

```php
use Firebase\JWT\JWT;

$payload = [
    'iss' => 'localhost',
    'iat' => time(),
    'exp' => time() + (60 * 60), // Expira em 1 hora
    'user_id' => 123
];
$secretKey = 'sua_chave_secreta';
$jwt = JWT::encode($payload, $secretKey, 'HS256');
echo $jwt;
```

#### 🛡️ **Validar o Token**:

```php
use Firebase\JWT\JWT;
use Firebase\JWT\Key;

$jwt = $_SERVER['HTTP_AUTHORIZATION']; // Token enviado no cabeçalho
try {
    $decoded = JWT::decode($jwt, new Key('sua_chave_secreta', 'HS256'));
    print_r($decoded);
} catch (Exception $e) {
    http_response_code(401);
    echo json_encode(['error' => 'Token inválido']);
}
```

---

## 5. 🌍 **Consumo de APIs Externas** 🔌

Para consumir **APIs** externas, use a biblioteca **cURL** ou **Guzzle**.

### 🌐 **cURL (Padrão do PHP)**:

```php
$url = "https://api.exemplo.com/dados";
$ch = curl_init($url);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
$response = curl_exec($ch);
curl_close($ch);

$data = json_decode($response, true);
print_r($data);
```

### ⚡ **Guzzle (Mais Moderno)**:

#### 🔧 **Instale via Composer**:

```bash
composer require guzzlehttp/guzzle
```

#### 📝 **Exemplo**:

```php
use GuzzleHttp\Client;

$client = new Client();
$response = $client->request('GET', 'https://api.exemplo.com/dados');
$data = json_decode($response->getBody(), true);
print_r($data);
```

---

## 6. 🛠️ **Boas Práticas** ✅

- **Organize os códigos**: Utilize **MVC** ou **frameworks** (**Laravel**).
- **Documentação**: Crie documentação com ferramentas como **Swagger**.
- **Validação**: Valide os dados de entrada 🛡️.
- **Erros**: Retorne códigos de status **HTTP** apropriados (200, 400, 401, 404, 500).

---

## 7. 🔒 **Segurança** ⚠️

- Use **HTTPS** 🔐.
- Não exponha informações sensíveis no token 🔑.
- Utilize limites de requisição (**rate-limiting**) ⏳.

---

Criar e consumir APIs RESTful com PHP é uma habilidade essencial para desenvolvedores que trabalham com integrações. Seguindo essas práticas e dicas, você estará mais preparado para construir APIs seguras e eficientes! 💪🚀