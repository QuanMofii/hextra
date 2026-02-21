---
title: Markdown
weight: 4
---

Hugo hỗ trợ cú pháp [Markdown](https://en.wikipedia.org/wiki/Markdown) để định dạng văn bản, tạo danh sách và hơn nữa. Trang này trình bày một số ví dụ cú pháp Markdown thường dùng.

<!--more-->

## Ví dụ Markdown

### Định dạng chữ

| Kiểu          | Cú pháp                   | Ví dụ                                 | Kết quả                                |
| :------------ | :------------------------ | :------------------------------------ | :------------------------------------- |
| Đậm          | `**chữ đậm**`             | `**chữ đậm**`                         | **chữ đậm**                            |
| Nghiêng      | `*chữ nghiêng*`           | `*chữ nghiêng*`                       | _chữ nghiêng_                          |
| Gạch ngang   | `~~chữ gạch ngang~~`      | `~~chữ gạch ngang~~`                  | ~~chữ gạch ngang~~                     |
| Chỉ số dưới  | `<sub></sub>`             | `Đây là <sub>chỉ số dưới</sub>`       | Đây là <sub>chỉ số dưới</sub>          |
| Chỉ số trên  | `<sup></sup>`             | `Đây là <sup>chỉ số trên</sup>`       | Đây là <sup>chỉ số trên</sup>          |

### Trích dẫn

Trích dẫn có ghi nguồn

> Đừng giao tiếp bằng cách chia sẻ bộ nhớ, hãy chia sẻ bộ nhớ bằng cách giao tiếp.<br>
> — <cite>Rob Pike[^1]</cite>

[^1]: Trích từ [bài nói](https://www.youtube.com/watch?v=PAAkCSZUG1c) của Rob Pike tại Gopherfest, 18/11/2015.

```markdown {filename=Markdown}
> Đừng giao tiếp bằng cách chia sẻ bộ nhớ, hãy chia sẻ bộ nhớ bằng cách giao tiếp.<br>
> — <cite>Rob Pike[^1]</cite>

[^1]: Trích từ bài nói của Rob Pike tại Gopherfest, 18/11/2015.
```

### Cảnh báo (Alerts)

{{< new-feature version="v0.9.0" >}}

Alerts là mở rộng Markdown dựa trên cú pháp blockquote để nhấn mạnh thông tin quan trọng. Hỗ trợ [cảnh báo kiểu GitHub](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax#alerts). Cần dùng theme mới nhất và [Hugo v0.146.0](https://github.com/gohugoio/hugo/releases/tag/v0.146.0) trở lên.

> [!NOTE]
> Thông tin hữu ích người dùng nên biết, kể cả khi chỉ lướt nội dung.

> [!TIP]
> Gợi ý giúp làm việc tốt hơn hoặc dễ hơn.

> [!IMPORTANT]
> Thông tin then chốt để đạt mục tiêu.

> [!WARNING]
> Thông tin cần chú ý ngay để tránh sự cố.

> [!CAUTION]
> Cảnh báo rủi ro hoặc hậu quả tiêu cực của một số hành động.

```markdown {filename=Markdown}
> [!NOTE]
> Thông tin hữu ích người dùng nên biết.

> [!TIP]
> Gợi ý giúp làm việc tốt hơn.

> [!IMPORTANT]
> Thông tin then chốt để đạt mục tiêu.

> [!WARNING]
> Thông tin cần chú ý ngay.

> [!CAUTION]
> Cảnh báo rủi ro hoặc hậu quả tiêu cực.
```

### Bảng

Bảng không nằm trong spec Markdown cốt lõi nhưng Hugo hỗ trợ sẵn.

| Tên   | Tuổi |
| :---- | :-- |
| Bob   | 27  |
| Alice | 23  |

```markdown {filename=Markdown}
| Tên   | Tuổi |
| :---- | :-- |
| Bob   | 27  |
| Alice | 23  |
```

#### Markdown nội dòng trong bảng

| Nghiêng   | Đậm     | Mã     |
| :-------- | :------ | :----- |
| _nghiêng_ | **đậm** | `code` |

### Khối mã

{{< cards >}}
  {{< card link="../../guide/syntax-highlighting" title="Tô sáng cú pháp" icon="sparkles" >}}
{{< /cards >}}

### Danh sách

#### Danh sách có thứ tự

1. Mục đầu
2. Mục hai
3. Mục ba

```markdown {filename=Markdown}
1. Mục đầu
2. Mục hai
3. Mục ba
```

#### Danh sách không thứ tự

* Mục
* Mục khác
* Và một mục nữa

```markdown {filename=Markdown}
* Mục
* Mục khác
* Và một mục nữa
```

#### Danh sách lồng nhau

- Trái cây
  - Táo
  - Cam
  - Chuối
- Sữa
  - Sữa tươi
  - Phô mai

#### Danh sách công việc

- [x] Viết tài liệu
- [ ] Rà soát mã
- [ ] Triển khai thay đổi

```markdown {filename=Markdown}
- [x] Viết tài liệu
- [ ] Rà soát mã
- [ ] Triển khai thay đổi
```

### Hình ảnh

![phong cảnh](https://picsum.photos/800/600)

Với chú thích:

![phong cảnh](https://picsum.photos/800/600 "Lorem Picsum")

Để dùng tính năng nâng cao hơn, dùng [shortcode Figure](https://gohugo.io/shortcodes/figure/) tích hợp của Hugo.

## Cấu hình

Hugo dùng [Goldmark](https://github.com/yuin/goldmark) để phân tích Markdown. Có thể cấu hình trong `hugo.yaml` tại `markup.goldmark`. Dưới đây là cấu hình mặc định của theme:

```yaml {filename="hugo.yaml"}
markup:
  goldmark:
    renderer:
      unsafe: true
  highlight:
    noClasses: false
```

Tham khảo tài liệu Hugo [Configure Markup](https://gohugo.io/getting-started/configuration-markup/) để biết thêm tùy chọn.

## Tài liệu tham khảo

- [Markdown Guide](https://www.markdownguide.org/)
- [Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
- [Markdown Tutorial](https://www.markdowntutorial.com/)
- [Markdown Reference](https://commonmark.org/help/)
