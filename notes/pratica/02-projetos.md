# Projetos

Mini projetos para aplicar o que foi aprendido de forma integrada.

## Como usar

1. Leia o enunciado do projeto
2. Planeje antes de codificar - defina módulos, structs, enums e fluxo
3. Implemente incrementalmente, rodando `cargo check` com frequência
4. Escreva testes com `cargo test` para as partes principais antes de avançar

## Projeto 01 - Jogo de Adivinhação

**Nível:** iniciante

**Objetivo:** Construir um jogo interativo no terminal usando uma crate externa.

**Descrição:**
O programa sorteia um número entre 1 e 100 e pede palpites até a pessoa acertar, dizendo se o palpite foi alto ou baixo. É o primeiro projeto do livro oficial do Rust - tente fazer sem olhar e compare depois.

**Requisitos:**

- [ ] Usa a crate `rand` (adicionada com `cargo add rand`) para sortear o número
- [ ] Lê a entrada com `std::io::stdin().read_line`
- [ ] Converte o palpite com `parse` e ignora entradas inválidas sem encerrar o programa
- [ ] Compara com `match` e `std::cmp::Ordering`
- [ ] Mostra quantas tentativas foram necessárias

**Exemplo de uso:**

```
Adivinhe o número (1 a 100):
50
Muito alto!
25
Muito baixo!
37
Acertou em 3 tentativas!
```

## Projeto 02 - Lista de Tarefas (CLI)

**Nível:** intermediário

**Objetivo:** Criar uma ferramenta de linha de comando que persiste dados em arquivo.

**Descrição:**
Construa um gerenciador de tarefas que recebe subcomandos pela linha de comando e salva as tarefas em um arquivo JSON.

**Requisitos:**

- [ ] Subcomandos `add`, `list`, `done` e `remove`, definidos com a crate `clap`
- [ ] Tarefas representadas por uma `struct` com `id`, `titulo` e `concluida`
- [ ] Persistência em `tarefas.json` com `serde` e `serde_json`
- [ ] Erros propagados com o operador `?` e exibidos com mensagens claras
- [ ] Nenhum `unwrap()` em operações de arquivo

**Exemplo de uso:**

```
$ tarefas add "Estudar ownership"
Tarefa 1 adicionada.

$ tarefas list
[ ] 1 - Estudar ownership

$ tarefas done 1
Tarefa 1 concluída.
```

## Projeto 03 - mini grep

**Nível:** intermediário

**Objetivo:** Reproduzir uma versão simples do `grep`, organizando o código em biblioteca e binário.

**Descrição:**
O programa recebe um termo de busca e o caminho de um arquivo e imprime as linhas que contêm o termo.

**Requisitos:**

- [ ] Lógica de busca em `src/lib.rs` e leitura de argumentos em `src/main.rs`
- [ ] Função `buscar<'a>(termo: &str, conteudo: &'a str) -> Vec<&'a str>` com lifetime explícito
- [ ] Opção de busca sem diferenciar maiúsculas de minúsculas via variável de ambiente
- [ ] Mensagens de erro enviadas para `stderr` com `eprintln!`
- [ ] Testes unitários da função de busca

**Exemplo de entregável:**

```
$ minigrep caramelo poema.txt
o caramelo dormiu ao sol
e o caramelo sonhou com ossos
```

## Projeto 04 - API REST de Livros

**Nível:** avançado

**Objetivo:** Construir uma API HTTP assíncrona.

**Descrição:**
Crie uma API que permite cadastrar, listar, buscar e remover livros, guardando os dados em memória.

**Requisitos:**

- [ ] Servidor com `axum` sobre o runtime `tokio`
- [ ] Rotas `GET /livros`, `GET /livros/{id}`, `POST /livros` e `DELETE /livros/{id}`
- [ ] Entrada e saída em JSON com `serde`
- [ ] Estado compartilhado com `Arc<Mutex<...>>` (ou `RwLock`)
- [ ] Códigos de status corretos (`200`, `201`, `204`, `400`, `404`)
- [ ] Testes de integração das rotas

**Exemplo de entregável:**

```
$ curl -X POST localhost:3000/livros -H 'Content-Type: application/json' \
    -d '{"titulo":"A Linguagem Rust","autor":"Klabnik e Nichols"}'
{"id":1,"titulo":"A Linguagem Rust","autor":"Klabnik e Nichols"}
```
