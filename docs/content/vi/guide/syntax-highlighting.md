---
title: "Tô sáng cú pháp"
weight: 5
---

Hugo dùng [Chroma](https://github.com/alecthomas/chroma), công cụ tô sáng cú pháp thuần Go, để tô sáng mã. Nên dùng dấu backtick cho khối mã trong nội dung Markdown. Ví dụ:

<!--more-->

````markdown {filename="Markdown"}
```python
def say_hello():
    print("Hello!")
```
````

sẽ được hiển thị thành:

```python
def say_hello():
    print("Hello!")
```

## Tính năng

### Tên file

Để thêm tên file hoặc tiêu đề cho khối mã, đặt thuộc tính `filename`:

````markdown {filename="Markdown"}
```python {filename="hello.py"}
def say_hello():
    print("Hello!")
```
````

```python {filename="hello.py"}
def say_hello():
    print("Hello!")
```

### Liên kết tới file

{{< new-feature version="v0.9.2" >}}

Bạn có thể dùng thuộc tính `base_url` để cung cấp URL gốc, kết hợp với tên file tạo thành liên kết. Tên file có thể chứa đường dẫn tương đối nếu cần chỉ vị trí file trong đường dẫn gốc.

````markdown {filename="Markdown"}
```go {base_url="https://github.com/example/repo/blob/main/",filename="docs/hugo.work"}
go 1.20
```
````

```go {base_url="https://github.com/example/repo/blob/main/",filename="docs/hugo.work"}
go 1.20
```

### Số dòng

Để bật số dòng, đặt thuộc tính `linenos` thành `table` và tùy chọn `linenostart` là số dòng bắt đầu:

````markdown {filename="Markdown"}
```python {linenos=table,linenostart=42}
def say_hello():
    print("Hello!")
```
````

```python {linenos=table,linenostart=42}
def say_hello():
    print("Hello!")
```

### Tô sáng dòng

Để tô sáng một số dòng, đặt thuộc tính `hl_lines` thành danh sách số dòng:

````markdown {filename="Markdown"}
```python {linenos=table,hl_lines=[2,4],linenostart=1,filename="hello.py"}
def say_hello():
    print("Hello!")

def main():
    say_hello()
```
````

```python {linenos=table,hl_lines=[2,4],linenostart=1,filename="hello.py"}
def say_hello():
    print("Hello!")

def main():
    say_hello()
```

### Nút sao chép

Mặc định nút sao chép được bật cho khối mã. Có thể thay đổi trong file cấu hình site:

```yaml {linenos=table,linenostart=42,filename="hugo.yaml"}
params:
  highlight:
    copy:
      enable: true
      # hover | always
      display: hover
```

## Ngôn ngữ hỗ trợ

Xem [tài liệu Chroma](https://github.com/alecthomas/chroma#supported-languages) để biết danh sách ngôn ngữ được hỗ trợ.
