---
title: "LaTeX"
weight: 6
---

Biểu thức toán LaTeX được hiển thị bằng \(\KaTeX\) ([katex.org](https://katex.org/)) mặc định. Chỉ cần thêm vào nội dung Markdown mà không cần cấu hình thêm.

## Cách dùng

Bạn có thể dùng LaTeX cho biểu thức nội dòng và cho khối công thức lớn hơn.

### Toán nội dòng

Để đưa biểu thức vào trong dòng chữ, đặt giữa cặp `\(` và `\)`.

```markdown {filename="page.md"}
Biểu thức nội dòng: \(\sigma(z) = \frac{1}{1 + e^{-z}}\).
```

Biểu thức nội dòng: \( \sigma(z) = \frac{1}{1 + e^{-z}} \).

### Toán hiển thị riêng

Với công thức cần đứng riêng một đoạn, dùng cặp `$$`.

```markdown {filename="page.md"}
$$F(\omega) = \int_{-\infty}^{\infty} f(t)\, e^{-j \omega t} \, dt$$
```

sẽ hiển thị thành:

$$F(\omega) = \int_{-\infty}^{\infty} f(t)\, e^{-j \omega t} \, dt$$

Bạn cũng có thể dùng môi trường LaTeX như `aligned` cho biểu thức nhiều dòng.

```latex {filename="page.md"}
$$
\begin{aligned}
  \nabla \cdot \mathbf{E} &= \frac{\rho}{\varepsilon_0} \\
  \nabla \cdot \mathbf{B} &= 0 \\
  \nabla \times \mathbf{E} &= -\frac{\partial \mathbf{B}}{\partial t} \\
  \nabla \times \mathbf{B} &= \mu_0 \left( \mathbf{J} + \varepsilon_0 \frac{\partial \mathbf{E}}{\partial t} \right)
\end{aligned}
$$
```

sẽ hiển thị thành:

$$
\begin{aligned}
  \nabla \cdot \mathbf{E} &= \frac{\rho}{\varepsilon_0} \\
  \nabla \cdot \mathbf{B} &= 0 \\
  \nabla \times \mathbf{E} &= -\frac{\partial \mathbf{B}}{\partial t} \\
  \nabla \times \mathbf{B} &= \mu_0 \left( \mathbf{J} + \varepsilon_0 \frac{\partial \mathbf{E}}{\partial t} \right)
\end{aligned}
$$

Danh sách hàm hỗ trợ: [KaTeX supported functions](https://katex.org/docs/supported.html).

### Công thức hóa học

Extension [mhchem][mhchem] được bật mặc định, cho phép hiển thị phương trình và công thức hóa học.

Nội dòng: \(\ce{H2O}\) là nước.

Đoạn riêng:

```markdown {filename="page.md"}
$$\ce{Hg^2+ ->[I-] HgI2 ->[I-] [Hg^{II}I4]^2-}$$
```

sẽ hiển thị thành:

$$\ce{Hg^2+ ->[I-] HgI2 ->[I-] [Hg^{II}I4]^2-}$$

## Cấu hình

> [!IMPORTANT]
> Cần bật và cấu hình [extension passthrough](https://gohugo.io/content-management/mathematics/) trong file cấu hình Hugo để Hugo nhận diện biểu thức LaTeX trong nội dung Markdown.

```yaml {filename="hugo.yaml"}
markup:
  goldmark:
    extensions:
      passthrough:
        delimiters:
          block: [['\[', '\]'], ["$$", "$$"]]
          inline: [['\(', '\)']]
        enable: true
```

### Công cụ toán

[KaTeX][katex] là công cụ mặc định dùng để hiển thị biểu thức LaTeX khi build, được [Hugo][hugo-transform-tomath] hỗ trợ. Mặc định là KaTeX; bạn cũng có thể chuyển sang [MathJax][mathjax] nếu cần tính năng chỉ có ở MathJax.

#### KaTeX

Cấu hình mặc định không cần chỉnh. Hugo lấy CSS KaTeX từ CDN. Nếu cần cố định phiên bản KaTeX hoặc dùng file local, cấu hình trong `hugo.yaml`.

##### Ghi đè URL CDN

```yaml {filename="hugo.yaml"}
params:
  math:
    engine: katex
    katex:
      base: "https://cdn.jsdelivr.net/npm/katex@0.16.22/dist"
```

##### Dùng file local

Có thể đặt file css trong `assets` và xuất bản thêm font KaTeX cần dùng.

```yaml {filename="hugo.yaml"}
params:
  math:
    engine: katex
    katex:
      css: "css/katex.min.css"
      assets:
        - "fonts/KaTeX_Main-Regular.woff2"
```

Khi đó CSS KaTeX sẽ được tải từ `assets/css/katex.min.css` thay vì từ CDN.

#### MathJax

Có thể dùng [MathJax][mathjax] để hiển thị công thức:

```yaml {filename="hugo.yaml"}
params:
  math:
    engine: mathjax
```

> [!NOTE]
> Bạn có thể tùy biến thêm MathJax (ví dụ loader, đổi CDN/nguồn) bằng cách ghi đè template `layouts/_partials/scripts/mathjax.html` trong dự án. Hugo sẽ dùng bản của bạn thay cho mặc định của theme.

[katex]: https://katex.org/
[mathjax]: https://www.mathjax.org/
[mhchem]: https://mhchem.github.io/MathJax-mhchem/
[hugo-transform-tomath]: https://gohugo.io/functions/transform/tomath/
