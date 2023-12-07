# CSS

- applies styling to websites
- modifying colors, font types, font sizes, images, element positioning, and more

## Syntax

- เขียนได้ 2 แบบ
  - ruleset
  - inline style

![css-syntax](/images/css-syntax.png "css-syntax")

### Inline style

- คือการเขียน css บน html ผ่าน attribute style
- เป็นวิธีที่ไม่ค่อยใช้กัน อาจจะใช้ในบางกรณี

```
<p style='color: red; font-size: 20px;'>I'm learning to code!</p>
```

### Internal Stylesheet

- คือการเขียน css ในไฟล์ html ผ่าน tag style ใน tag head

```
<head>
  <style>
    p {
      color: red;
      font-size: 20px;
    }
  </style>
</head>
```

### External Stylesheet

- โดยปกติเราจะเขียน css,html แยกคนละไฟล์กันเพื่อจัดการ code,อ่าน code ได้ง่ายขึ้น
- HTML files contain only HTML code, and CSS files contain only CSS code

### Linking the CSS File

- เราแยกไฟล์ html,css การที่จะทำให้ code css ที่อยู่คนละไฟล์กับ html ทำงานร่วมกันได้ เราต้อง link css file ที่ html ไฟล์ก่อน
- link ผ่าน `<link>` ใน `<head>`
  - href คือ path css file
  - rel คือ อธิบาย relationship ระหว่าง html file,css file (`stylesheet`)

```
<link href='https://www.codecademy.com/stylesheets/style.css' rel='stylesheet'>
```
