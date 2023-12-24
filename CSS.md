# CSS

- applies styling to websites
- modifying colors, font types, font sizes, images, element positioning, and more

## Basic Syntax

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

## Selectors

### Type

- selector css ที่เป็น type element เช่น h1,p,a,ul,li เป็นต้น

```
p {
  color: green;
}

h1 {
  color: maroon;
}
```

### Universal

- เป็น selector ที่ selects all elements of any type.
- selecting all children of a parent element

```
* {
  font-family: Verdana;
}
```

### Class

- เป็น selector ที่ select class css
- ต้องมี (`.`) หน้าชื่อ class

```
.title {
  color: teal;
}
```

### Multiple Classes

- สามารถใช้ multiple class css ใน element เดียวกันได้

```
.green {
  color: green;
}

.bold {
  font-weight: bold;
}

<h1 class='green bold'> ... </h1>
```

### ID

- selector ของ id attribute
- จะมี (`#`) ตามด้วยชื่อ id
- ใช้กำหนด style css ให้กับ element ที่ต้องการ unique style

```
#large-title {
  ...
}

<h1 id='large-title'> ... </h1>
```

### Attribute

- selector ที่ select element ที่มี attribute
- สามารถใช้ร่วมกับ type selector ได้

```
[href]{
   color: magenta;
}

<img src='/images/seasons/cold/winter.jpg'>
<img src='/images/seasons/warm/summer.jpg'>

img[src*='winter'] {
  height: 50px;
}

img[src*='summer'] {
  height: 100px;
}
```

`Note :`

- https://developer.mozilla.org/en-US/docs/Web/CSS/Attribute_selectors#syntax [`Attribute selectors`]

### Pseudo-class

- เป็น feature เสริมของ selector
- จะถูก select เพื่อ apply style เมื่อ element เกิดการ action,interact อะไรซักอย่าง (hover,focus,visited,disabled,active)
- ใช้ร่วมกับ selector อื่นๆ จะต้องมี (`:`) ตามด้วยชื่อ `action/interaction`
- :hover, :focus, :visited, :disabled, :active

```
p:hover {
  background-color: lime;
}

a:hover {
  color: darkorange;
}
```

### Classes and IDs

1. Class selector

- เหมาะกับการนำไปใช้ reuse style, ใช้มากกว่า 1 ครั้ง

2.  ID selector

- เหมาะกับการนำไปใช้ unique style กับ element เพียงอันเดียวเท่านั้น

### Specificity

- Specificity คือลำดับ priority ของการ apply style
- ID > Class > Type
- ID มีความ specific ที่สุด ทำให้สามารถ override all style ทุก selector ได้

```
<h1 class='headline'>Breaking News</h1>

h1 {
  color: red;
}
.headline {
  color: firebrick;
}
```

- จากตัวอย่างข้างบน class มีความ specific กว่า type ทำให้ style `color: firebrick;` override `color: red;` นั่นเอง

`Note : ` To make styles easy to edit, it’s best to style with a type selector, if possible. If not, add a class selector. If that is not specific enough, then consider using an ID selector

### Chaining

- คือการ style css ให้กับ element ที่มี multiple selector (`ใน element เดียวกัน`)

```
h2.destination {
  font-family: Tahoma;
}
```

- จากตัวอย่างข้างบน style css จะทำงานก็ต่อเมื่อเป็น h2 ที่มี class destination เท่านั้น

### Descendant Combinator (Specificity)

- มันคือการ style css แบบ specific ให้กับ nested selector

```
<ul class='main-list'>
  <li> ... </li>
  <li> ... </li>
  <li> ... </li>
</ul>

.main-list li {
  color: blueviolet;
}
```

- จากตัวอย่างข้างบน style css จะทำงานก็ต่อเมื่อเป็น li ที่ nested อยู่ใน class main-list เท่านั้น

### Chaining and Specificity

- การเพิ่ม และ chain selector มากกว่า 1 จะทำให้เพิ่ม specificity ให้กับ selector
- จากตัวอย่างข้างล่าง จะเห็นว่าทุก p จะเป็นสี blue จะมีแค่ p ที่ nested ใน class main เท่านั้นที่จะเป็นสี red (เนื่องจาก `Descendant Combinator` หรือ `Chaining` หรือ `specificity` มี priority ในการ apply style มากกว่า selector ปกติ)

```
p {
  color: blue;
}

.main p {
  color: red;
}
```

### Multiple Selectors

- เราสามารถ group การเขียน style css ให้กับ multiple selectors ได้ เพื่อลดความซ้ำซ้อนในการเขียน style
- จากตัวอย่างข้างล่างจะเห็นว่า `h1` และ `.menu` มี `font-family: Georgia` เหมือนกัน เพื่อลดความซ้ำซ้อนของการเขียน style เราสามารถ group การเขียนให้เป็นอันเดียวกันได้

```
h1 {
  font-family: Georgia;
}
.menu {
  font-family: Georgia;
}
// group multiple selector
h1,
.menu {
  font-family: Georgia;
}
```

## Visual rules

### Font Family

- กำหนด style รูปแบบของ font

```
h1 {
  font-family: Garamond;
}
```

### Font Size

- กำหนด style ขนาดของ font

```
p {
  font-size: 18px;
}
```

### Font Weight

- กำหนด style ความหนา,บาง font

```
p {
  font-weight: bold;
}
```

### Text Align

- กำหนดการวางตำแหน่งของ text โดยอิงกับ parent ของมัน
- left,center,right,justify
- left: เป็น default อยู่ด้านซ้าย (อิงกับ parent)
- center: อยู่ตรงกลาง (อิงกับ parent)
- right: อยู่ด้านขวา (อิงกับ parent)
- justify: จัด text ให้เว้นวรรรค เพื่อให้ text ชิดติดซ้าย,ขวา (อิงกับ parent) ตัวอย่าง justify ตามภาพข้างล่าง

  ![text-align-justify](/images/text-align-justify.png "text-align-justify")

```
h1 {
  text-align: right; // left,center,right,justify
}
```

### Color and Background Color

- กำหนดสีมี 2 แบบ สี font (`color`), สี background (`background-color`)

```
h1 {
  color: red; // สี font
  background-color: blue; // สี background
}
```

### Opacity

- กำหนดความโปร่งใส ความทึบแสง
- มีค่าตั้งแต่ 0(`0%`) - 1(`100%`)
- 0 -> หายไปเลย ไม่แสดง
- 1 -> แสดงเต็มไม่โปร่งใส

```
.overlay {
  opacity: 0.5;
}
```

### Background Image

- กำหนด background จาก image (path url => `relative path(internal)`,`public url(external)`)

- public url(external)

  ```
  .main-banner {
    background-image: url('https://www.example.com/image.jpg');
  }
  ```

- relative path(internal)

  ```
  .main-banner {
    background-image: url('images/mountains.jpg');
  }
  ```

### Important

- กำหนด hard override style (`It will override any style no matter how specific it is`)
- `!important` override all style ไม่สน specificity
- จากตัวอย่างข้างล่าง ถึงแม้ว่า .main p จะมีความ specific มากกว่า p แต่ p มีการกำหนด `!important` hard override style ทำให้ไม่ว่า p จะเป็นอะไร nested อยู่ที่ไหน ก็จะเป็นสี blue เสมอ

```
p {
  color: blue !important;
}

.main p {
  color: red;
}
```
