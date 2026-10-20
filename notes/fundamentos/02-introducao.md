# Introdução ao Rust

Rust é uma linguagem de programação de sistemas, de código aberto, focada em **desempenho**, **confiabilidade** e **segurança de memória**. Começou em 2006 como um projeto pessoal de Graydon Hoare, passou a ser patrocinada pela Mozilla em 2009 e chegou à versão 1.0 em 2015. Hoje é mantida pela comunidade com apoio da Rust Foundation.

## Por que o Rust foi criado

Linguagens como C e C++ dão controle total sobre a memória e geram programas muito rápidos, mas deixam a responsabilidade de gerenciar essa memória com quem programa. Erros como acessar memória já liberada, ler fora dos limites de um array ou duas threads escrevendo no mesmo dado ao mesmo tempo causam travamentos e falhas de segurança graves.

Do outro lado, linguagens com **garbage collector** (Java, Go, Python) eliminam boa parte desses erros, mas cobram um preço em desempenho e previsibilidade.

O Rust propõe um terceiro caminho: **segurança de memória garantida em tempo de compilação, sem garbage collector**.

## Características principais

### Ownership: memória segura sem garbage collector

O coração do Rust é o sistema de **ownership** (posse). Cada valor tem um único dono, e quando o dono sai de escopo o valor é liberado automaticamente:

```rust
fn main() {
    let texto = String::from("Caramelo");
    let outro = texto; // a posse foi movida para `outro`

    // println!("{texto}"); // erro de compilação: `texto` não é mais válido
    println!("{outro}");
}
```

Para usar um valor sem tomar posse dele, você o **empresta** com uma referência (`&`). O compilador, por meio do **borrow checker**, garante que referências nunca apontam para dados que já foram liberados.

Você vai estudar ownership e borrowing com calma - é o conceito que mais exige no início e o que mais recompensa depois.

### Abstrações de custo zero

Iteradores, closures, generics e traits deixam o código expressivo, e o compilador transforma tudo isso em código de máquina tão eficiente quanto um laço escrito à mão:

```rust
let soma: i32 = (1..=10).filter(|n| n % 2 == 0).sum();
```

### Sem `null` e sem exceções

Em Rust não existe `null`. Um valor que pode estar ausente é representado pelo tipo `Option`, e uma operação que pode falhar retorna um `Result`. O compilador obriga você a tratar os dois casos:

```rust
let numero: Result<i32, _> = "42".parse();

match numero {
    Ok(n) => println!("Número: {n}"),
    Err(e) => println!("Não é um número: {e}"),
}
```

### Concorrência sem medo

As mesmas regras de ownership valem entre threads. Se um código tem risco de **data race**, ele simplesmente não compila. A comunidade chama isso de *fearless concurrency* - concorrência sem medo.

### Um compilador que ensina

As mensagens de erro do Rust são famosas por serem claras: mostram o trecho do código, explicam o problema e, muitas vezes, sugerem a correção. No começo você vai "brigar" com o compilador; com o tempo, ele vira seu melhor par de programação.

### Cargo e crates.io

O Cargo cuida de criar projetos, compilar, testar, gerar documentação e baixar dependências. As bibliotecas da comunidade se chamam **crates** e ficam publicadas no [crates.io](https://crates.io/).

## Onde o Rust é usado

- **Sistemas operacionais e baixo nível** - o kernel do Linux aceita código em Rust, e Microsoft e Google usam Rust em componentes do Windows e do Android
- **Infraestrutura e cloud** - o Firecracker (base do AWS Lambda) e diversos serviços da Cloudflare são escritos em Rust
- **Ferramentas de desenvolvimento** - ripgrep, uv e Ruff (Python), Biome e SWC (JavaScript) usam Rust para serem muito rápidas
- **WebAssembly** - Rust é uma das linguagens mais usadas para compilar para Wasm
- **Backend, CLIs, sistemas embarcados e jogos**

## Anatomia de um programa Rust

```rust
fn main() {
    let nome = "Caramelo Tech";
    println!("Olá, {nome}!");
}
```

- **`fn main()`** - a função `main` é o ponto de entrada de todo programa executável.
- **`let nome = ...`** - declara uma variável. Variáveis são **imutáveis por padrão**; para permitir alterações, use `let mut`.
- **`println!`** - o `!` indica que é uma **macro**, não uma função. Macros geram código em tempo de compilação; `println!` verifica a string de formatação antes de o programa rodar.
- **`{nome}`** - interpola a variável `nome` no texto.
- **`;`** - toda instrução termina com ponto e vírgula. Uma expressão sem `;` no fim de um bloco é o **valor de retorno** dele.

## `cargo run` vs `cargo build --release`

```bash
cargo run                # compila sem otimizações e executa (rápido de compilar)
cargo build --release    # compila com otimizações (mais lento de compilar, mais rápido de rodar)
./target/release/ola-rust
```

Use `cargo run` enquanto está desenvolvendo e `--release` para medir desempenho ou distribuir o programa.

## A curva de aprendizado

Rust tem fama de ser difícil, e é verdade que os primeiros dias exigem paciência. Algumas dicas:

- **Leia as mensagens de erro inteiras** - elas costumam dizer exatamente o que fazer
- **Não tente fugir do borrow checker** - quando ele reclama, quase sempre está apontando um problema real de design
- **Clone sem culpa no começo** - usar `.clone()` para destravar o aprendizado é aceitável; otimize depois
- **Estude com o livro oficial** - *The Rust Programming Language* é gratuito e muito didático

## Referências

- [Site oficial do Rust](https://www.rust-lang.org/)
- [The Rust Programming Language](https://doc.rust-lang.org/book/)
- [What is Ownership? - The Rust Programming Language](https://doc.rust-lang.org/book/ch04-01-what-is-ownership.html)
- [Rust by Example](https://doc.rust-lang.org/rust-by-example/)
- [Comprehensive Rust (Google) - em português](https://google.github.io/comprehensive-rust/pt-BR/)
