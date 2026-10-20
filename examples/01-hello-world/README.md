# 01 - Hello World

Este é o programa mais básico em Rust - o famoso "Olá, Mundo!"

## 📝 Sobre

Todo programador começa sua jornada com um programa Hello World. É uma tradição na computação e serve para:

- Verificar se o ambiente de desenvolvimento está configurado
- Entender a estrutura básica de um programa
- Fazer seu primeiro código funcionar!

## 📂 Arquivos

- `Cargo.toml` - manifesto do projeto: nome, versão e edition
- `src/main.rs` - código fonte do programa

## 🚀 Como Executar

Dentro desta pasta:

### 1. Execute com o Cargo

```bash
cargo run
```

O Cargo compila o projeto em `target/debug/` e executa o binário.

### 2. Ou compile a versão otimizada

```bash
cargo build --release
./target/release/hello-world        # no Windows: .\target\release\hello-world.exe
```

### 3. Saída Esperada

```
Olá, Mundo!
Bem-vindo ao Rust!
Este é meu primeiro programa.
```

## 🔍 Entendendo o Código

```rust
fn main() {
```

- `fn` - palavra-chave para declarar uma função
- `main` - ponto de entrada do programa; a execução começa aqui

```rust
println!("Olá, Mundo!");
```

- `println!` - imprime o texto e pula linha
- O `!` indica que `println!` é uma **macro**, não uma função comum
- `;` - toda instrução termina com ponto e vírgula

## 💡 Conceitos Importantes

### 1. Macros terminam com `!`

`println!`, `vec!` e `format!` são macros: geram código em tempo de compilação e verificam a formatação antes de o programa rodar.

### 2. Indentação com 4 espaços

É o padrão do `rustfmt`. Rode `cargo fmt` e o código fica no formato da comunidade.

### 3. `target/` não vai para o Git

A pasta `target/` guarda os artefatos de compilação e é recriada a cada build.

## 🎯 Experimente

1. **Mude a mensagem:**

   ```rust
   println!("Seu nome aqui!");
   ```

2. **Interpole uma variável:**

   ```rust
   let nome = "Caramelo";
   println!("Olá, {nome}!");
   ```

3. **Use `print!` em vez de `println!`:**

   ```rust
   print!("Não pula linha ");
   print!("fica na mesma linha\n");
   ```

## 🔗 Conceitos Relacionados

- [📖 Configurando o Ambiente](../../notes/fundamentos/01-ambiente.md)
- [📖 Introdução ao Rust](../../notes/fundamentos/02-introducao.md)

## ❓ Problemas Comuns

### Erro: "cargo: command not found" / "'cargo' não é reconhecido"

**Solução:** o Rust não está instalado ou `~/.cargo/bin` não está no `PATH`.
Veja: [Configurando o Ambiente](../../notes/fundamentos/01-ambiente.md)

### Erro: "linker `link.exe` not found" (Windows)

**Solução:** instale as Visual Studio C++ Build Tools, como explicado na nota de ambiente.

### Erro: "cannot find macro `printn` in this scope"

**Solução:** confira o nome da macro - o correto é `println!`, com o `!` no final.

**[⬅️ Voltar aos Exemplos](../README.md)**
