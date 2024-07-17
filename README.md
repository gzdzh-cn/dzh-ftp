# ftp



A FTP client package for Go

## Install

```
go get -u github.com/gzdzh-cn/dzh-ftp
```

## Documentation

https://pkg.go.dev/github.com/gzdzh-cn/dzh-ftp

## Example

```go
c, err := ftp.Dial("ftp.example.org:21", ftp.DialWithTimeout(5*time.Second))
if err != nil {
    log.Fatal(err)
}

err = c.Login("anonymous", "anonymous")
if err != nil {
    log.Fatal(err)
}

// Do something with the FTP conn

if err := c.Quit(); err != nil {
    log.Fatal(err)
}
```

## Store a file example

```go
data := bytes.NewBufferString("Hello World")
err = c.Stor("test-file.txt", data)
if err != nil {
	panic(err)
}
```

## Read a file example

```go
r, err := c.Retr("test-file.txt")
if err != nil {
	panic(err)
}
defer r.Close()

buf, err := ioutil.ReadAll(r)
println(string(buf))
```


# 更新日志

v1.1.1
- 修改文档

v1.0.0
- 修改上传模式，可以设置主动模式或被动模式