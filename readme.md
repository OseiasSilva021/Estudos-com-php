# 🚀 Fundamentos do PHP: Guia Completo para Iniciantes 🐘

## 🎯 Objetivo
Entender a linguagem PHP e suas bases fundamentais.

## 📜 História e Propósito do PHP

### 🕰️ História
- Criado em 1994 por Rasmus Lerdorf como scripts para monitorar visitas pessoais 🖥️
- Evoluiu rapidamente para uma linguagem de programação completa 📈
- Originalmente "Personal Home Page", hoje "PHP: Hypertext Preprocessor" 🌐

### 🎨 Propósito
- Focado no desenvolvimento web dinâmico 🌍
- Permite:
  - Integração com bancos de dados 💾
  - Manipulação de arquivos 📂
  - Geração de conteúdo dinâmico 🔧
- Popular pela facilidade de uso e grande comunidade 👥

## 💻 Ambiente de Desenvolvimento

### 🛠️ Configuração do Servidor Local

#### XAMPP 
- Multiplataforma 🖥️🍎🪟
- Inclui Apache, MySQL/MariaDB, PHP e Perl
- Ideal para iniciantes 🚀

#### WAMP
- Exclusivo para Windows 🪟
- Inclui Apache, MySQL e PHP
- Interface gráfica amigável 😊

#### Docker 
- Ideal para produção e times 🐳
- Cria ambientes isolados e replicáveis
- Exemplo de comando:
  ```bash
  docker run -d -p 8080:80 -v $(pwd):/var/www/html php:apache
  ```

## 🧩 Sintaxe Básica

### 📝 Variáveis e Constantes

#### Variáveis 
```php
$nome = "Oséias";    // 👤 Nome
$idade = 18;         // 🎂 Idade
```

#### Constantes
```php
define("PI", 3.14);      // 🔢 Valor fixo
const APP_NAME = "MeuApp"; // 🏷️ Nome da aplicação
```

### 📊 Tipos de Dados
- Primitivos: int, float, string, bool 🔢
- Compostos: array, object 📦
- Especiais: null, resource 🌈

```php
$numero = 42;            // 🔢 Inteiro
$preco = 19.99;          // 💰 Float
$ativo = true;           // ✅ Booleano
$cidades = ["SP", "RJ"]; // 🏙️ Array
```

### 🧮 Operadores
- Aritméticos: +, -, *, /, % 
- Lógicos: &&, ||, !
- Relacionais: ==, !=, <, >, <=, >=

```php
$resultado = ($idade > 18) && ($ativo); // 🤔 Verificação
```

## 🔀 Controle de Fluxo

### 🚦 Condicionais

#### if/else
```php
if ($idade >= 18) {
    echo "Maior de idade 🎉";
} else {
    echo "Menor de idade 👶";
}
```

#### switch
```php
switch ($dia) {
    case "segunda": echo "Começo da semana! 📅"; break;
    case "sexta": echo "Quase fim de semana! 🎊"; break;
    default: echo "Dia comum. 🕰️";
}
```

### 🔁 Loops

#### for
```php
for ($i = 0; $i < 5; $i++) {
    echo $i;  // 🔢 Contagem
}
```

#### foreach
```php
foreach ($cidades as $cidade) {
    echo $cidade;  // 🏘️ Iteração
}
```

## 🔧 Funções

### 📋 Declaração e Escopo
```php
function saudacao($nome) {
    return "Olá, $nome! 👋";
}
echo saudacao("Oséias");
```

### 🛠️ Funções Nativas Comuns
```php
// Strings 📝
echo strlen("Olá");        // Comprimento
echo strtoupper("olá");    // Maiúsculas

// Arrays 📦
$numeros = [1, 2, 3];
array_push($numeros, 4);   // Adicionar elemento

// Datas 📅
echo date("Y-m-d");        // Data atual
```

## 🎉 Conclusão
Este guia oferece uma base sólida para iniciar sua jornada com PHP! 🚀🐘

**Dica Extra**: Pratique, pratique, pratique! 💪📚
