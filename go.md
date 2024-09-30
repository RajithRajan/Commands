# mod
Create a module
```bash
go mod init github.com/RajithRjan/<name>
```

# run
Execute the main.go
```bash
go run main.go
```

# test
Test a project
```bash
go test
# print verbose
go test -v
# print coverage
go test -cover
# display the coverage report in the browser
go test -coverprofile=coverage.out && go tool cover -html=coverage.out
```
