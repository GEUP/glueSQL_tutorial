# glueSQL_tutorial

https://www.rust-lang.org/tools/install
rustup-init.exe 설치 후 실행

```
> rustc --version
> cargo new test_gluesql
> cargo new test_gluesql
> notepad Cargo.toml
```

```toml
[dependencies]
gluesql = "0.11"
```

```
> notepad .\src\main.rs
```

```rust
use gluesql::prelude::*;
fn main() {
    let storage = SledStorage::new("data/doc-db").unwrap();
    let mut glue = Glue::new(storage);
    let sqls = vec![
        "DROP TABLE IF EXISTS Glue;",
        "CREATE TABLE Glue (id INTEGER);",
        "INSERT INTO Glue VALUES (100);",
        "INSERT INTO Glue VALUES (200);",
        "SELECT * FROM Glue WHERE id > 100;",
    ];
    for sql in sqls {
        let output = glue.execute(sql).unwrap();
        println!("{:?}", output)
    }
}
```
```
> cargo build
>.\target\debug\test_gluesql.exe
```

