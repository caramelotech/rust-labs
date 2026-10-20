# Rust Roadmap

Um guia prático e progressivo para aprender Rust e construir software rápido e confiável.

## 🧱 1. Fundamentos de Programação

### Lógica de Programação

- Algoritmos e resolução de problemas
- Pseudocódigo
- Linguagens compiladas vs interpretadas

### Conceitos básicos

- Variáveis e constantes
- Tipos de dados
- Comentários
- Entrada e saída no terminal

### Controle de fluxo

- Condicionais
- Estruturas de repetição
- Funções

### Noções de memória

- Stack vs heap
- Ponteiros e referências (conceitual)
- Por que gerenciamento de memória importa

## 🦀 2. Primeiros Passos com Rust

### Ambiente

- Instalação com `rustup`
- Cargo: `new`, `run`, `build`, `check`, `test`
- `rustfmt` e `clippy`
- Editor com `rust-analyzer`

### Sintaxe

- Variáveis, imutabilidade e `mut`
- Shadowing
- Constantes
- Tipos escalares: inteiros, ponto flutuante, `bool`, `char`
- Tipos compostos: tuplas e arrays
- Funções, instruções e expressões
- Comentários e comentários de documentação (`///`)

### Controle de fluxo em Rust

- `if` como expressão
- `loop`, `while` e `for`
- Ranges

## 🔑 3. Ownership e Borrowing

- Regras de ownership
- Move vs copy (`Copy` e `Clone`)
- Referências e borrowing (`&` e `&mut`)
- As regras do borrow checker
- Slices (`&str`, `&[T]`)
- `String` vs `&str`

## 🧩 4. Structs, Enums e Pattern Matching

- Structs, tuple structs e unit structs
- Métodos e funções associadas (`impl`)
- Enums com dados
- `Option<T>`
- `match` e exaustividade
- `if let`, `let else` e `while let`
- Padrões avançados e guards

## 📦 5. Organização de Código

- Pacotes, crates e módulos
- `mod`, `use` e `pub`
- Separação entre `lib.rs` e `main.rs`
- Workspaces do Cargo
- Dependências e crates.io
- Features do Cargo

## 📚 6. Coleções e Strings

- `Vec<T>`
- `HashMap` e `HashSet`
- `BTreeMap` e `VecDeque`
- Strings e UTF-8

## ⚠️ 7. Tratamento de Erros

- `panic!` vs erros recuperáveis
- `Result<T, E>`
- O operador `?`
- Tipos de erro customizados
- Crates `thiserror` (bibliotecas) e `anyhow` (aplicações)

## 🧬 8. Generics, Traits e Lifetimes

- Funções e tipos genéricos
- Traits e implementações
- Traits da biblioteca padrão (`Debug`, `Display`, `Clone`, `PartialEq`, `From`, `Default`)
- `derive`
- Trait bounds e `where`
- `impl Trait` e `dyn Trait`
- Lifetimes e elisão
- Associated types

## 🔁 9. Programação Funcional

- Closures (`Fn`, `FnMut`, `FnOnce`)
- Iteradores e o trait `Iterator`
- Adaptadores: `map`, `filter`, `fold`, `collect`
- Desempenho de iteradores vs laços

## 🧠 10. Smart Pointers

- `Box<T>`
- `Rc<T>` e `Arc<T>`
- `RefCell<T>` e mutabilidade interior
- `Weak<T>` e ciclos de referência
- Trait `Drop`

## ⚡ 11. Concorrência

- Threads com `std::thread`
- Troca de mensagens com channels
- Estado compartilhado com `Mutex` e `RwLock`
- `Send` e `Sync`
- Paralelismo de dados com `rayon`

## ⏳ 12. Programação Assíncrona

- `async` e `await`
- Futures
- Runtime `tokio`
- Tasks, `select!` e cancelamento
- Streams

## 🧪 13. Testes e Qualidade

- Testes unitários com `#[test]`
- Testes de integração (`tests/`)
- Doc tests
- Testes baseados em propriedades (`proptest`)
- Benchmarks com `criterion`
- `clippy` e `cargo audit`

## 🌐 14. Desenvolvimento Web e APIs

- `axum` e `actix-web`
- Serialização com `serde`
- Cliente HTTP com `reqwest`
- Middlewares com `tower`
- gRPC com `tonic`
- Validação de entrada

## 🗄️ 15. Banco de Dados

- `sqlx` (SQL verificado em tempo de compilação)
- `diesel` e `SeaORM`
- Migrações
- Redis

## 🛠️ 16. CLIs e Ferramentas

- Argumentos com `clap`
- Configuração e variáveis de ambiente
- Saída colorida e barras de progresso
- Distribuição de binários

## 📊 17. Observabilidade

- Logging e tracing com `tracing`
- Métricas com Prometheus
- OpenTelemetry

## ☁️ 18. Cloud, Containers e Deploy

- Build otimizado (`--release`, profiles, LTO)
- Compilação cruzada (targets)
- Imagens Docker multi-stage e mínimas
- CI/CD com GitHub Actions

## 🌍 19. Outras Áreas do Ecossistema

- WebAssembly (`wasm-bindgen`, `wasm-pack`)
- Sistemas embarcados (`no_std`)
- Desenvolvimento de jogos (Bevy)
- Interfaces gráficas (Tauri, egui)
- Interoperabilidade com C (FFI) e Python (PyO3)

## 🎯 20. Tópicos Avançados

- `unsafe` Rust e suas garantias
- Macros declarativas (`macro_rules!`)
- Macros procedurais
- Layout de memória e `repr`
- Pin e internals de async
- Otimização de desempenho e profiling

## 🚀 Próximos Passos - Da Sintaxe à Produção

1. Domine ownership, borrowing e as mensagens do compilador
2. Modele seus dados com structs, enums e pattern matching
3. Trate erros com `Result` e `?` desde o início
4. Construa uma CLI com `clap` e `serde` e depois uma API com `axum` e `tokio`
5. Empacote com Docker, publique com CI/CD e observe com `tracing`

## 🧠 Dica

> Foque em **projetos reais** ao invés de só teoria.

Sugestões:

- CLI útil para o seu dia a dia
- Reimplementar uma ferramenta Unix (`grep`, `wc`, `cat`)
- API REST com `axum`, `sqlx` e PostgreSQL
- Um módulo WebAssembly rodando no navegador

🔥 **Regra de ouro:**
Aprenda - Aplique - Ensine - Repita
