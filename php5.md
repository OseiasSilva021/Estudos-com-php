# 🚀 PHP Moderno e Frameworks

## 📌 Objetivo
Aprender boas práticas e adotar ferramentas modernas para desenvolvimento em PHP.

## 1. Composer: Gerenciador de Dependências 📦

### O que é Composer?
Gerenciador de dependências essencial para desenvolvedores PHP, facilitando:
- 🔗 Inclusão de bibliotecas externas
- 🔍 Controle de versões
- 🔁 Reutilização de código

### Instalação

#### Linux/Mac
```bash
# Baixe e instale via terminal
curl -sS https://getcomposer.org/installer | php
sudo mv composer.phar /usr/local/bin/composer
```

#### Windows
- Baixe o instalador oficial do Composer

### Verificação de Instalação
```bash
composer --version
```

### Comandos Principais
```bash
# Iniciar novo projeto
composer init

# Adicionar dependência
composer require vendor/package

# Atualizar dependências
composer update
```

## 2. PSR (PHP Standards Recommendations) 📋

### Principais Padrões
- **PSR-1**: Padrões básicos de codificação
- **PSR-4**: Carregamento automático de classes (autoload)

### Configuração de Autoload no composer.json
```json
{
    "autoload": {
        "psr-4": {
            "App\\": "src/"
        }
    }
}
```

### Atualizar Autoload
```bash
composer dump-autoload
```

## 3. Frameworks PHP 🌐

### Por que usar Frameworks?
- 🏗️ Organização de código
- 🛡️ Aplicação de boas práticas
- ⚡ Funcionalidades prontas

## 4. Laravel: Framework MVC Completo 🔥

### Padrão MVC
- **Model**: Dados e lógica de negócio
- **View**: Apresentação
- **Controller**: Interação entre Model e View

### Instalação
```bash
# Certifique-se de ter o Composer instalado
composer create-project laravel/laravel meu_projeto
```

### Conceitos-chave

#### Roteamento
```php
Route::get('/home', [HomeController::class, 'index']);
```

#### Migrations
```bash
php artisan make:migration create_users_table
```

#### Eloquent ORM
```php
// Buscar usuário
User::find(1);
```

#### Blade Templates
```php
<h1>{{ $title }}</h1>
```

## 5. Alternativas Leves 🌱

### CodeIgniter
- 🚀 Rápido e leve
- 👶 Ideal para iniciantes

#### Instalação
```bash
composer create-project codeigniter4/appstarter meu_projeto
```

### Slim Framework
- 🔬 Focado em APIs
- 🏃 Minimalista
- 📡 Ótimo para microservices

#### Instalação
```bash
composer require slim/slim
```

## 🌟 Boas Práticas

1. 📦 Use Composer para gerenciar dependências
2. 📏 Siga padrões PSR
3. 🧩 Aprenda Laravel (padrão MVC)
4. 🔍 Experimente frameworks leves para projetos menores

## 📚 Recursos Adicionais

- [Documentação Composer](https://getcomposer.org/doc/)
- [Laravel Documentation](https://laravel.com/docs/)
- [CodeIgniter Documentation](https://codeigniter.com/user_guide/)
- [Slim Framework Documentation](https://www.slimframework.com/docs/v4/)
- [PHP Standards Recommendations](https://www.php-fig.org/psr/)

## 🤝 Contribuições

Contribuições são bem-vindas! Abra issues ou envie pull requests.

## 📄 Licença

[Inserir informações da licença]

## 📧 Contato

Dúvidas? Entre em contato!
```

## 🚀 Próximos Passos

- Escolha um framework
- Pratique
- Desenvolva projetos
```
