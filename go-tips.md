## F1: Test Previous, Debug Previous

![image](https://github.com/voedger/kb/assets/11589750/e1e224b9-71e6-4583-a8b7-78e65c2031dd)

## Find All References

![image](https://github.com/voedger/kb/assets/11589750/8896bf42-c5ec-424e-8509-19e999f1e3f9)

## Emoji

- 📂apps
  - 📁app1
    - 📁image // unzipped app image
    - descriptor.json

⊞ Win + `.` 

![image](https://github.com/voedger/kb/assets/11589750/c7f23c60-998f-40a7-8bbe-3306da1b6f98)


![image](https://github.com/voedger/kb/assets/11589750/55e399cc-9d99-49d2-925d-2b203b63c89e)

## Ensure a type implements an interface

```go
// Let we have an interface...
type SomeInterface interface {
    Method()
}

// Let we have a type...
type Implementation struct{}

func (*Implementation) Method() { fmt.Println("Hello, World!") }

// We want to ensure that the type implements the interface...
var _ SomeInterface = (*Implementation)(nil) // ← this does the job
```

-  [Playground](https://go.dev/play/p/8cAxiaY8KEj)
-  Spotted in: [medium.com: Write Go like a senior engineer](https://levelup.gitconnected.com/write-go-like-a-senior-engineer-eee7f03a1883)

## Configuraion

- [Configuration](https://github.com/voedger/kb/issues/51)