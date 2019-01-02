Illustrates [TDEPS-74](https://dev.clojure.org/jira/browse/TDEPS-74)

```
჻ (cd foo && clj)
Error building classpath. Manifest type not detected when finding deps for bar/bat in coordinate #:local{:root "../bat"}
```

There are three subprojects `foo`, `baz` and `bat`, with dependencies:
```
foo -> bar/baz -> bar/bat
```

Project layout:
```
├── README.md
├── bar
│   ├── bat
│   │   └── deps.edn ({:deps {}})
│   └── baz
│       └── deps.edn ({:deps {bar/bat {:local/root "../bat"}}})
└── foo
    └── deps.edn ({:deps {bar/baz {:local/root "../bar/baz"}}})

4 directories, 4 files
```
