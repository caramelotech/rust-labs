# Configurando o Ambiente

Antes de escrever qualquer código Rust, você precisa de três coisas:

1. **rustup** - o instalador e gerenciador de versões oficial do Rust
2. **Toolchain** - o compilador `rustc`, a biblioteca padrão e o **Cargo**, gerenciador de projetos e dependências
3. **Editor com suporte a Rust** - para ter autocompletar, erros em tempo real e formatação automática

Na prática, você instala só o `rustup`, e ele cuida do resto.

## Instalando o Rust

### macOS e Linux

Abra o terminal e execute o script oficial:

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

Escolha a instalação padrão (opção `1`). Ao terminar, feche e reabra o terminal, ou carregue o ambiente na sessão atual:

```bash
source "$HOME/.cargo/env"
```

O Rust precisa de um **linker** para gerar executáveis. No Linux, instale as ferramentas de build da sua distribuição (por exemplo, `sudo apt install build-essential` no Ubuntu). No macOS, rode `xcode-select --install`.

### Windows

1. Baixe e execute o `rustup-init.exe` em [rustup.rs](https://rustup.rs/)
2. O instalador verifica se as **Visual Studio C++ Build Tools** estão presentes. Se não estiverem, ele oferece instalá-las - aceite, porque o Rust usa o linker da Microsoft no Windows
3. Escolha a instalação padrão e reabra o terminal ao final

Também é possível instalar com:

```bash
winget install Rustlang.Rustup
```

## Verificando a instalação

```bash
rustc --version
cargo --version
rustup --version
```

A saída deve ser algo como:

```
rustc 1.X.Y (abcdef123 AAAA-MM-DD)
cargo 1.X.Y (abcdef123 AAAA-MM-DD)
rustup 1.X.Y (abcdef123 AAAA-MM-DD)
```

## Mantendo o Rust atualizado

O Rust lança uma versão estável nova a cada seis semanas. Para atualizar:

```bash
rustup update
```

O `rustup` também gerencia **canais** (`stable`, `beta`, `nightly`) e **componentes** extras. Os dois componentes que você vai usar desde o início já vêm na instalação padrão:

- **`rustfmt`** - formatador oficial (`cargo fmt`)
- **`clippy`** - linter com centenas de sugestões para deixar o código mais idiomático (`cargo clippy`)

Se algum estiver faltando:

```bash
rustup component add rustfmt clippy
```

A documentação completa (incluindo o livro oficial) também é instalada localmente e funciona offline:

```bash
rustup doc --book
```

## Escolhendo um editor

| Editor           | Como configurar                                                                                                   |
| ---------------- | ----------------------------------------------------------------------------------------------------------------- |
| **VS Code**      | Instale a extensão [rust-analyzer](https://marketplace.visualstudio.com/items?itemName=rust-lang.rust-analyzer)   |
| **RustRover**    | IDE da JetBrains dedicada ao Rust                                                                                 |
| **Zed**          | Editor com suporte nativo a Rust via rust-analyzer                                                                |
| **Neovim / Vim** | Configure o `rust-analyzer` pelo cliente LSP de sua preferência                                                   |

O **rust-analyzer** é o language server oficial do Rust. Ele mostra os tipos inferidos direto no editor - uma ajuda enorme enquanto você aprende ownership e borrowing.

Ative a opção de **formatar ao salvar** para o `rustfmt` cuidar do estilo do código.

## Criando o primeiro projeto com Cargo

```bash
cargo new ola-rust
cd ola-rust
```

O Cargo cria esta estrutura (e já inicializa um repositório Git):

```text
ola-rust/
├── Cargo.toml   -> manifesto: nome, versão, edition e dependências
└── src/
    └── main.rs  -> ponto de entrada do programa
```

O `Cargo.toml` gerado:

```toml
[package]
name = "ola-rust"
version = "0.1.0"
edition = "2024"

[dependencies]
```

A **edition** define o conjunto de regras da linguagem usado pelo projeto. Projetos de editions diferentes funcionam juntos sem problemas.

O `src/main.rs` já vem com um Hello World:

```rust
fn main() {
    println!("Hello, world!");
}
```

Execute:

```bash
cargo run
```

```
   Compiling ola-rust v0.1.0 (/caminho/ola-rust)
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 0.50s
     Running `target/debug/ola-rust`
Hello, world!
```

## Comandos essenciais do Cargo

| Comando                | O que faz                                                             |
| ---------------------- | --------------------------------------------------------------------- |
| `cargo new nome`       | Cria um projeto executável (use `--lib` para uma biblioteca)          |
| `cargo run`            | Compila e executa o projeto                                           |
| `cargo build`          | Compila em modo de desenvolvimento (`target/debug/`)                  |
| `cargo build --release`| Compila com otimizações (`target/release/`)                           |
| `cargo check`          | Verifica se o código compila, sem gerar binário - bem mais rápido     |
| `cargo test`           | Executa os testes                                                     |
| `cargo fmt`            | Formata o código                                                      |
| `cargo clippy`         | Roda o linter                                                         |
| `cargo add crate`      | Adiciona uma dependência ao `Cargo.toml`                              |
| `cargo doc --open`     | Gera e abre a documentação do projeto e das dependências              |

Dica: enquanto estiver programando, use `cargo check` com frequência. Ele dá o mesmo retorno do compilador em uma fração do tempo.

## Sem instalar nada: Rust Playground

Para testar um trecho rápido, use o [Rust Playground](https://play.rust-lang.org/) no navegador. Ele roda o código, aplica `rustfmt` e `clippy` e permite compartilhar o resultado por link.

## Problemas comuns

### `cargo: command not found` ou `'cargo' não é reconhecido`

O diretório `~/.cargo/bin` (no Windows, `%USERPROFILE%\.cargo\bin`) não está no `PATH`. Reabra o terminal depois da instalação; se continuar, adicione o diretório manualmente.

### `linker 'link.exe' not found` (Windows)

As Visual Studio C++ Build Tools não estão instaladas. Instale-as pelo [Visual Studio Installer](https://visualstudio.microsoft.com/visual-cpp-build-tools/) com a carga de trabalho "Desenvolvimento para desktop com C++".

### `linker 'cc' not found` (Linux)

Falta um compilador C no sistema. Instale `build-essential` (Debian/Ubuntu) ou o pacote equivalente da sua distribuição.

## Referências

- [Install Rust - site oficial](https://www.rust-lang.org/tools/install)
- [The Rust Programming Language - Instalação](https://doc.rust-lang.org/book/ch01-01-installation.html)
- [The Cargo Book](https://doc.rust-lang.org/cargo/)
- [The rustup book](https://rust-lang.github.io/rustup/)
- [rust-analyzer](https://rust-analyzer.github.io/)
