Markdown
# 📑 文献: {{title}}

## 📌 基本信息
- **标题:** {{title}}
- **作者:** {{authors}}
- **期刊/出版物:** {{publicationTitle}}
- **发表年份:** {{date | format("YYYY")}}
- **DOI/链接:** {% if DOI %} https://doi.org/{{DOI}} {% else %} {{url}} {% endif %}
- **Zotero 链接:** [点击在 Zotero 中打开]({{desktopURI}})

---

## 💡 我的核心释义 (Abstract / Summary)
> {{abstractNote}}

---

## ✍️ 划线高亮与批注 (Annotations)

{% persist "annotations" %}
{% set annotations = annotations | filterAnnotations %}
{% if annotations.length > 0 %}

### 🟥 核心论点与重要结论
{% for annotation in annotations | filterByColor("red") %}
- **{{annotation.annotatedText}}** [↗]({{annotation.desktopURI}}) {% if annotation.comment %}\n  - 💭 *我的想法: {{annotation.comment}}*{% endif %}
{% endfor %}

### 🟨 关键定义、数据与概念
{% for annotation in annotations | filterByColor("yellow") %}
- {{annotation.annotatedText}} [↗]({{annotation.desktopURI}}) {% if annotation.comment %}\n  - 💭 *我的想法: {{annotation.comment}}*{% endif %}
{% endfor %}

### 🟩 优秀论据与可引用文献
{% for annotation in annotations | filterByColor("green") %}
- *{{annotation.annotatedText}}* [↗]({{annotation.desktopURI}}) {% if annotation.comment %}\n  - 💭 *我的想法: {{annotation.comment}}*{% endif %}
{% endfor %}

### 📘 其他泛读记录
{% for annotation in annotations | filterByGroup([ "blue", "purple", "gray" ]) %}
- {{annotation.annotatedText}} [↗]({{annotation.desktopURI}})
{% endfor %}

{% endif %}
{% endpersist %}

---
## 🧠 本地思考连线
- **关联项目/论文章节:** 
- **衍生想法:**
