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

## The Box Model

- ทุก element เป็น box model
- box model จะประกอบไปด้วย 4 ส่วน
  - dimenstion(`width,height`)
  - border(`border`)
  - padding(`padding`)
  - margin(`margin`)

### The Box Model Property

1. width, height => width,height ของ content area
2. padding => space ระหว่าง content กับ border
3. border => เป็นขอบของ content อยู่รอบ padding,content
4. margin => space ระหว่าง border กับ element's outside

![the box model](/images/the-box-model.png "the-box-model")

### Height and Width

- width,height ของ content area
- การกำหนด width,height เป็น px เป็นการฟิก dimension ทำให้ทุก device จะมี dimension เท่ากันหมด ส่งผลทำให้บางที element ที่ display เต็มจอของ laptop/pc screen อาจจะเกิด overflow บน mobile screen ได้
- หน่วยเป็น px,percent ได้

```
p {
  height: 80px;
  width: 240px;
}
```

### Border

- เป็นขอบที่ล้อมรอบ padding,content
- border จะ set ได้ 3 value
  - width -> ความหนาของ border (`px,thin,medium,thick`)
  - style -> style ของ border (`none, dotted, and solid etc.`) [https://developer.mozilla.org/en-US/docs/Web/CSS/border-style#values]
  - color -> สีของ border
- default border คือ `medium none color`
- ถ้า value ตัวใดตัวนึงไม่ได้ set ไว้ มันจะใช้ default

```
p {
  border: 3px solid coral;
}

// width ไม่ได้ set จะถูก set เป็น default คือ medium
p.content-header {
  height: 80px;
  width: 240px;
  border: solid coral;
}
```

### Border Radius

- ความโค้งของ border (ความโค้งทั้ง 4 มุมของ border)
- default จะเป็นสี่เหลี่ยม
- สามารถปรับ border radius ได้เมื่อต้องการให้ขอบโค้ง
- border-radius: 50%; จะทำให้มันเป็นวงกลม

```
div.container {
  border: 3px solid blue;
  border-radius: 5px;
}
// circle style
div.container {
  height: 60px;
  width: 60px;
  border: 3px solid blue;
  border-radius: 50%;
}
```

### Padding

- space ระหว่าง content กับ border
- padding มี specific 4 แบบ
  - padding-top
  - padding-right
  - padding-bottom
  - padding-left
- หน่วยเป็น px,percent

```
p.content-header {
  border: 3px solid coral;
  padding: 10px;
}
// padding bottom
p.content-header {
  border: 3px solid fuchsia;
  padding-bottom: 10px;
}
```

### Padding Shorthand

- เป็นการเขียน padding แบบย่อ โดยการ specific แต่ละแบบ(`padding-top,padding-right,padding-left,padding-bottom`)ในบรรทัดเดียว
- specific ได้ 3 แบบ

  - 4 Values: ไล่ตามเข็มนาฬิกา (`top,right,bottom,left`)

  ```
  p.content-header {
    padding: 6px 11px 4px 9px;
  }
  ```

  - 3 Values: ไล่ตามเข็มนาฬิกา และ ซ้าย,ขวาเท่ากัน (`top,left-right,bottom`)

  ```
  p.content-header {
    padding: 5px 10px 20px;
  }
  ```

  - 2 Values: ไล่ตามเข็มนาฬิกา บน-ล่างเท่ากัน,ซ้าย-ขวาเท่ากัน (`top-bottom,left-right`)

  ```
  p.content-header {
    padding: 5px 10px;
  }
  ```

### Margin

- space ระหว่าง border กับ element's outside
- margin มี specific 4 แบบ
  - margin-top
  - margin-right
  - margin-bottom
  - margin-left

```
p {
  border: 1px solid aquamarine;
  margin: 20px;
}
// margin-right
p {
  border: 3px solid DarkSlateGrey;
  margin-right: 15px;
}
```

### Margin Shorthand

- เป็นการเขียน margin แบบย่อ โดยการ specific แต่ละแบบ(`margin-top,margin-right,margin-left,margin-bottom`)ในบรรทัดเดียว
- specific ได้ 3 แบบ

  - 4 Values: ไล่ตามเข็มนาฬิกา (`top,right,bottom,left`)

    ```
    p {
      margin: 6px 11px 4px 9px;
    }
    ```

    - 3 Values: ไล่ตามเข็มนาฬิกา และ ซ้าย,ขวาเท่ากัน (`top,left-right,bottom`)

    ```
    p {
      margin: 5px 10px 20px;
    }
    ```

    - 2 Values: ไล่ตามเข็มนาฬิกา บน-ล่างเท่ากัน,ซ้าย-ขวาเท่ากัน (`top-bottom,left-right`)

    ```
    p {
      margin: 5px 10px;
    }
    ```

### Auto

- margin สามารถทำให้ content อยู่ตรงกลางได้โดยการกำหนด auto (`ต้อง set width ด้วย`)
- จากตัวอย่างข้างล่าง element
  - จะอยู่ตรงกลางของ container ของมัน
  - margin top,bottom เป็น 0 px
  - auto จะทำให้ browser ปรับ left,right margin จนกว่า element จะอยู่ตรงกลางของ container ของมัน
  - จะใช้วิธีนี้ได้ต้อง set width ให้ element ด้วย
  - ถ้าไม่ set width width มันจะ auto full width ทำให้ browser ไม่สามารถปรับ left,right margin เพราะ width สามารถเปลี่ยนแปลง ตามขนาดจอและwindow size ได้ตลอด มันไม่มี constant width ให้ ref ในการปรับ margin
  - การ set width คือการ set minimum width ที่ browser จะ ref เพื่อใช้ในการปรับ left,right margin
  - จากตัวอย่างข้างล่าง width ตัั้งแต่ 400px ขึ้นไป browser จะ ref ปรับ left,right margin เพื่อให้ element อยู่ตรงกลางได้ (ถ้า width น้อยกว่า 400px ไม่มีผล)

```
div.headline {
  width: 400px;
  margin: 0 auto;
}
```

### Margin Collapse

- vertical margins(`margin-top,margin-bottom`) จะยุบตาม margin ที่เยอะสุด โดยไม่เอามาคำนวณ space รวม margin ถ้ามันชนกันหรือติดกัน
- horizon-margins(`margin-left,margin-right`),padding(`padding-left,padding-right,padding-top,padding-bottom`) จะเอา space มาคำนวณรวมกัน ถ้ามันชนกันหรือติดกัน

![margin collapse](/images/margin-collapse.png "margin-collapse")

### Minimum and Maximum Height and Width

- min-width -> กำหนด min width ให้ element (width น้อยสุดเท่านี้ และจะไม่หด width น้อยกว่านี้)
- max-width -> กำหนด max width ให้ element (width มากสุดเท่านี้ และจะไม่กาง width มากกว่านี้)
- จากตัวอย่างข้างล่าง
  - paragraph จะไม่หด width ต่ำกว่า 300px
  - paragraph จะไม่กาง width เกิน 600px

```
p {
  min-width: 300px;
  max-width: 600px;
}
```

- min-height -> กำหนด min height ให้ element (height น้อยสุดเท่านี้ และจะไม่หด height น้อยกว่านี้)
- max-height -> กำหนด max height ให้ element (height มากสุดเท่านี้ และจะไม่กาง height มากกว่านี้)
- จากตัวอย่างข้างล่าง
  - paragraph จะไม่หด height ต่ำกว่า 150px
  - paragraph จะไม่กาง height เกิน 300px

```
p {
  min-height: 150px;
  max-height: 300px;
}
```

`Note : ` ถ้า max-height มีค่าที่น้อยๆ อาจทำให้ content มันเกินออกมานอก box model (`เกิด overflow`)

### Overflow

- overflow คือ content เกินออกมานอก box model
- control content ที่มันเกินออกมานอก box model
- overflow มี 3 value
  - hidden -> hide content ส่วนที่เกินออกมา
  - scroll -> จะเกิด scroll bar ในส่วนที่ content เกิน
  - visible -> เป็น default display content ส่วนที่เกินออกมา
- overflow จะ set ให้ parent element ทำให้ all children element ที่เกิน จะแสดงตาม overflow value ที่เรา set
- overflow มี specific 2 แบบ
  - overflow-x -> horizon overflow
  - overflow-y -> vertical overflow

```
p {
  overflow: scroll;
}
```

`Note : ` https://developer.mozilla.org/en-US/docs/Web/CSS/overflow

### Resetting Defaults

- ปกติทุก web browser จะมี default stylesheet(`user agent stylesheets`) ของตัวเอง
- ยกตัวอย่างเช่น มี default padding, margin ซึ่งบางทีพวก default stylesheet พวกนี้ส่งผลต่อการ display html ของ browser ทำให้ developer design หรือ style web page ได้ยาก
- อาจมี default stylesheet บางตัว ทำให้การ display html ออกมาได้ไม่ตรงตามที่เราเขียน เช่น padding,margin ที่เราไม่ได้ต้องการจาก default stylesheet
- ซึ่งเราต้องทำการ reset default พวกนี้เอง ยกตัวอย่างการ reset default ตามข้างล่าง

```
* {
  margin: 0;
  padding: 0;
}
```

`Note : ` การกำหนดเป็น 0 ไม่จำเป็นต้องมีหน่วย

### Visibility

- control การ display element
- set ได้ 3 value
  - hidden -> hide element (hide แค่ content ของ element ไม่ได้ remove element ออกจาก web ทำให้มันจะ display empty space แทน)
  - visible -> display element (default)
  - collapse -> ยุบ element
- visibility: hidden ถึงแม้จะไม่แสดง แต่เวลา inspect ก็จะเจอใน source code อยู่

```
<ul>
  <li>Explore</li>
  <li>Connect</li>
  <li class="future">Donate</li>
</ul>

.future {
  visibility: hidden;
}
```

`Note : ` display: none กับ visibility: hidden แตกต่างกันยังไง?

- display: none -> remove element ออกจาก web
- visibility: hidden -> hide แค่ content แต่ element ยังอยู่ เลยทำให้มัน display empty space แทน

## Changing the box model

- โดย default ของ box model พวก box dimensions, borders, padding, margin จะส่งผลต่อการคำนวณ dimension ของ box
- จากตัวอย่างข้างล่าง
  - padding 10 px -> จะเพิ่ม height เป็น 220px(200+10+10), width เป็น 320px(300+10+10) ให้ box
  - border 1 px -> ความหนาจะเพิ่ม height เป็น 222px (220+1+1),width เป็น 322px(320+1+1) ให้ box
- การ set border,padding ทำให้มันถูกคำนวณ dimension รวมกัน
- ทำให้ dimension จริงไม่ตรงกับ dimension ที่เราต้องการจริงๆ

```
h1 {
  border: 1px solid black;
  height: 200px;
  width: 300px;
  padding: 10px;
}
```

### Box Model: Content-Box

- box-sizing -> property control type ของ box model
- box-sizing: content-box -> default ตัว border,padding มีผลต่อการคำนวณ dimension รวมกัน
- ทำให้ actual dimension ไม่ตรงกับที่เราต้องการ

![content box](/images/content-box.png "content-box")

### Box Model: Border-Box

- box-sizing: border-box
- dimension(height,width) จะถูกฟิกไว้
- border,padding จะถูกรวมใน box
- ทำให้ dimension ทั้งหมดจะไม่เปลี่ยน (width,height ไม่เปลี่ยน)
- border,padding จะไม่ถูกคำนวณ dimension รวมกันกับ content โดยจะปรับ dimension ของ content area auto + padding + border แล้วไม่เกิน actual width,height ที่เรา set ไว้
- ทำให้ actual dimension ตรงกับที่เราต้องการ

![border box](/images/border-box.png "border-box")

### The New Box Model

- set all element box เป็น border box

```
* {
  box-sizing: border-box;
}
```
