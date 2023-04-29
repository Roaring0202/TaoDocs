# This is how you would write documentation within mdBook. These are some of the more common symbols used.

## First, how does one use mdBook? Why should one learn? 

[mdBook](https://rust-lang.github.io/mdBook/index.html) is a way to write documentation for a project and organize it into a clean, coherent fashion. Depending on the scribe responsible for writing the book, the format, style, and website integration is easy to write it, but requires a different approach and knowledge of commands. If you are interested in furthering Bittensors documentation with your own contributions, mdBook is the format you should use going forward. 

Keep in mind, you can find the actual symbols that make the text look this way in the .md file found within src.

**Without further ado,**
***here's how you write a .md document***
# Headers

# Header 1
## Header 2
### Header 3
#### Header 4
##### Header 5
###### Header 6

# Emphasis

*Italic text*
_Italic text_

**Bold text**
__Bold text__

***Bold and italic text***
___Bold and italic text___

# Lists

## Unordered Lists
* Item 1
* Item 2
  * Nested Item 2.1
  * Nested Item 2.2
* Item 3

## Ordered Lists
1. Item 1
2. Item 2
   1. Nested Item 2.1
   2. Nested Item 2.2
3. Item 3

# Links

[Link Text](https://www.example.com)

# Images

![Alt text for image](https://www.example.com/image.jpg)

# Code

Inline `code` example



# Blockquotes

> This is a blockquote

# Horizontal Rule

---

# Tables

| Header 1 | Header 2 | Header 3 |
| -------- | -------- | -------- |
| Cell 1   | Cell 2   | Cell 3   |
| Cell 4   | Cell 5   | Cell 6   |

# Strikethrough

~~Strikethrough text~~


I'm sure there's things I've missed. I want to expand upon the intricacies of structure later on, but the purpose of this is to get others started on the journey. 