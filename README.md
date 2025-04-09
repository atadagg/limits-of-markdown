# Advanced Markdown Examples

This project showcases advanced Markdown features and techniques, pushing the boundaries of what Markdown can do.

## Table of Contents

- [Advanced Text Formatting](#advanced-text-formatting)
- [Complex Tables](#complex-tables)
- [Nested Lists and Task Lists](#nested-lists-and-task-lists)
- [Code Blocks and Syntax Highlighting](#code-blocks-and-syntax-highlighting)
- [Advanced Links and Images](#advanced-links-and-images)
- [HTML Embedding](#html-embedding)
- [Mathematical Expressions](#mathematical-expressions)
- [Footnotes and References](#footnotes-and-references)
- [Advanced Blockquotes](#advanced-blockquotes)
- [Custom Styling with HTML](#custom-styling-with-html)

## Advanced Text Formatting

Markdown supports various text formatting options:

- **Bold** and *Italic* text.
- ***Bold and Italic*** combined.
- ~~Strikethrough~~ text.
- `Inline code` within text.
- <sup>Superscript</sup> and <sub>Subscript</sub> using HTML.
- Text with <mark>highlighting</mark> using HTML.

## Complex Tables

Markdown tables can be complex:

| Header 1 | Header 2 | Header 3 |
|----------|----------|----------|
| Cell 1   | Cell 2   | Cell 3   |
| Cell 4   | Cell 5   | Cell 6   |
| Cell 7   | Cell 8   | Cell 9   |

## Nested Lists and Task Lists

Markdown supports nested lists and task lists:

- Item 1
  - Sub-item 1.1
  - Sub-item 1.2
- Item 2
  - Sub-item 2.1
  - Sub-item 2.2

- [ ] Task 1
- [x] Task 2
- [ ] Task 3

## Code Blocks and Syntax Highlighting

Markdown supports code blocks with syntax highlighting:

```python
def hello_world():
    print("Hello, World!")
```

```javascript
function helloWorld() {
    console.log("Hello, World!");
}
```

## Advanced Links and Images

Markdown supports various link and image formats:

- [Basic Link](https://example.com)
- [Link with Title](https://example.com "Example Website")
- ![Basic Image](https://via.placeholder.com/150 "Placeholder Image")
- [![Image with Link](https://via.placeholder.com/150)](https://example.com)

## HTML Embedding

Markdown allows embedding HTML for advanced formatting:

<div style="text-align: center; color: blue; font-size: 24px;">
  This is centered, blue, and larger text using HTML.
</div>

## Mathematical Expressions

Some Markdown flavors support mathematical expressions using LaTeX syntax:

Inline math: \(E = mc^2\)

Block math:

\[
\frac{n!}{k!(n-k)!} = \binom{n}{k}
\]

## Footnotes and References

Markdown supports footnotes and references:

Here's a sentence with a footnote[^1].

[^1]: This is the footnote content.

## Advanced Blockquotes

Markdown supports nested blockquotes:

> This is a blockquote.
>> This is a nested blockquote.
>>> This is a deeply nested blockquote.

## Custom Styling with HTML

Markdown allows custom styling using HTML:

<span style="color: red; font-weight: bold;">This text is red and bold.</span>

<details>
<summary>Click to expand</summary>
This is hidden content that can be expanded.
</details>
