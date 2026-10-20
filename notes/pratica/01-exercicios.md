# Exercícios

Pratique o que aprendeu nos conteúdos e exemplos de código.

## Como usar

1. Leia o enunciado do exercício
2. Tente resolver por conta própria antes de buscar ajuda
3. Revise as notas de [Fundamentos](/labs/rust/fundamentos/01-ambiente/) se precisar relembrar algum conceito
4. Rode `cargo fmt` e `cargo clippy` na sua solução antes de considerar o exercício concluído
5. Compare sua solução com a de outras pessoas da comunidade

## Exercício 01 - Olá, Rust

**Nível:** iniciante

**Objetivo:** Criar um projeto com Cargo e executar o primeiro programa Rust.

**Instrução:**

1. Crie um projeto com `cargo new ola-rust`
2. Altere o `main.rs` para imprimir `Olá, Caramelo Tech!`
3. Execute com `cargo run` e depois gere o binário otimizado com `cargo build --release`

**Critérios de sucesso:**

- [ ] O projeto tem `Cargo.toml` e `src/main.rs`
- [ ] `cargo run` imprime a mensagem corretamente
- [ ] O binário em `target/release/` imprime a mesma mensagem

## Exercício 02 - Variáveis e Mutabilidade

**Nível:** iniciante

**Objetivo:** Entender variáveis imutáveis, `mut` e shadowing.

**Instrução:**

1. Declare uma variável com seu nome (`&str`) e outra com sua idade (`u32`)
2. Declare uma constante `ALTURA: f64` com sua altura em metros
3. Declare um contador com `let mut`, some 1 a ele e imprima o resultado
4. Use shadowing para converter a idade em texto: `let idade = idade.to_string();`
5. Imprima uma frase combinando nome, idade e altura

Saída esperada:

```
Meu nome é Ana, tenho 25 anos e meço 1.68m.
```

**Critérios de sucesso:**

- [ ] Usa `let`, `let mut` e `const` pelo menos uma vez cada
- [ ] Usa shadowing pelo menos uma vez
- [ ] Formata a altura com duas casas decimais (`{:.2}`)
- [ ] O programa compila sem avisos

## Exercício 03 - FizzBuzz

**Nível:** iniciante

**Objetivo:** Praticar laços e `match`.

**Instrução:**
Imprima os números de 1 a 100. Para múltiplos de 3, imprima `Fizz` no lugar do número; para múltiplos de 5, `Buzz`; para múltiplos de ambos, `FizzBuzz`.

**Critérios de sucesso:**

- [ ] Usa um laço `for` com range (`1..=100`)
- [ ] Usa `match` sobre a tupla `(n % 3, n % 5)` em vez de vários `if`
- [ ] A saída está correta para 3, 5, 15 e 100

## Exercício 04 - Divisão Segura

**Nível:** iniciante

**Objetivo:** Usar `Option` e `Result` para representar falhas.

**Instrução:**
Crie a função `dividir(a: f64, b: f64) -> Result<f64, String>` que retorna `Err` quando `b` for zero. No `main`, chame a função com valores válidos e inválidos e trate os dois casos com `match`.

**Critérios de sucesso:**

- [ ] A função retorna `Err` com uma mensagem clara quando `b == 0.0`
- [ ] O `main` trata `Ok` e `Err` com `match` ou `if let`
- [ ] O programa não usa `unwrap()` em valores que podem falhar

## Exercício 05 - Contador de Palavras

**Nível:** intermediário

**Objetivo:** Praticar `String`, `&str`, iteradores e `HashMap`.

**Instrução:**
Escreva a função `contar_palavras(texto: &str) -> HashMap<String, usize>` que conta quantas vezes cada palavra aparece (ignorando maiúsculas e minúsculas). Imprima as palavras em ordem alfabética com suas contagens.

**Critérios de sucesso:**

- [ ] Usa `split_whitespace` e `to_lowercase`
- [ ] Usa a API `entry` do `HashMap` (`*mapa.entry(palavra).or_insert(0) += 1`)
- [ ] Ordena as chaves antes de imprimir
- [ ] Tem ao menos um teste com `#[test]` validando a contagem
