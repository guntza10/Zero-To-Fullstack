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
<link href='https://www.codecademy.com/stylesheets/style.css' rel='stylesheet' type="text/css">
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
- 1 -> ไม่โปร่งใส(ทึบแสง ดำเลย)

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

## The Box Model in DevTools

- https://www.codecademy.com/journeys/full-stack-engineer/paths/fscj-22-web-development-foundations/tracks/fscj-22-fundamentals-of-css/modules/wdcp-22-learn-css-the-box-model-c8543ca0-92d4-4824-bb89-35a1fb0189d4/articles/f1-devtools-box-model

- https://www.youtube.com/watch?v=uQi8TK-GDO4

`Note:` CSS Reset

- https://meyerweb.com/eric/tools/css/reset/

## Display and Positioning

### Flow of HTML

- default ของ browser จะ render HTML แบบ no css จาก `ซ้ายไปขวา บนลงล่าง`
- Flow html => `ซ้ายไปขวา บนลงล่าง`
- property เกี่ยวกับ display,position
  - position
  - display
  - z-index
  - float
  - clear

### Position

- default position ของ element จะอยู่ชิดซ้ายของตำแหน่งปัจจุบันที่มันอยู่
- position มี 5 value
  - static (default) ตำแหน่งที่ element อยู่
  - relative
  - absolute
  - fixed
  - sticky

### Position: Relative

- relative กำหนด position element ให้ relative กับ default position ของตัวมัน
- การกำหนด position relative แล้วอยากให้ position `เปลี่ยนต้องมี offset properties ด้วย`
- offset properties มี 4 value
  - top -> move element จากบนลงล่าง
  - bottom -> move element จากล่างขึ้นบน
  - left -> move element จากซ้ายไปขวา
  - right -> move element จากขวาไปซ้าย
- offset properties กำหนดใน px,ems,percent ก็ได้
- offset properties ไม่ทำงานกับ position static (default)
- offset properties ไม่มีผลกับ position ของ element อื่น นอกจากตัวที่มันโดน set

```
.green-box {
  background-color: green;
  position: relative;
  top: 50px;
  left: 120px;
}
```

### Position: Absolute

- absolute กำหนด position element ให้เป็นอิสระต่อทุก element ไม่ relative กับใครนอกจาก parent
- ทุก element จะ ignore เหมือนกับว่ามันไม่มีอยู่ (`ถูก remove ออกจาก flow html`)
- position ของ absolute คือ position ที่ใกล้ที่สุดกับ parent (top:0,left:0)
- ใช้ offset properties ร่วมกันในการจัด position
- position absolute จะทำให้ width ของ element กว้างเท่าตัว content อาจจะต้องมีการกำหนด width 100% เพื่อให้มันกว้างเต็มพื้นที่

```
header {
  background-color: #466995;
  border-bottom: 1px solid #466995;
  position: absolute;
  width: 100%;
}
```

### Position: Fixed

- fixed เหมือน absolute แต่เป็น absolute ที่ fixed position ไว้ เวลาเลื่อนหน้าจอมันจะติด display มาด้วยทุกครั้ง
- ถูก remove ออกจาก flow html
- ปกติ absolute position อิสระต่อทุก element เวลาเลื่อนหน้าจอมันก็จะอยู่ที่ตำแหน่งอิสระของมัน ไม่ได้เลื่อนตามมาด้วย
- ใช้ offset properties ร่วมกันในการจัด position
- position fixed จะทำให้ width ของ element กว้างเท่าตัว content อาจจะต้องมีการกำหนด width 100% เพื่อให้มันกว้างเต็มพื้นที่

```
.title {
  position: fixed;
  top: 0px;
  left: 0px;
}
```

### Position: Sticky

- sticky เป็น relative ที่เวลาเลื่อนจอมาถึงและเกิน position sticky มันจะ stick position ติดกับหน้าจอมาด้วย จนกว่าจะเลื่อนถึงล่างสุดมันถึงจะหลุด
- ต้องใช้ร่วมกับ offset properties(ส่วนใหญ่ก็ใช้กับ top) เสมอ ไม่งั้น sticky จะไม่ทำงาน จะกลายเป็นแค่ relative ธรรมดา เพราะว่ามันไม่รู้ offset ว่าเมื่อเลื่อนมาถึงเท่าไรแล้วถึงจะต้อง stick ไว้
- ยกตัวอย่างข้างล่าง box-bottom ก็จะเป็น relative อยู่ที่ position ที่มันอยู่ แต่ถ้าเลื่อนจากบนลงล่างถึง 240px เมื่อไร (top: 240px) sticky ก็จะทำงาน ถ้าไม่มีการกำหนด offset มาให้ sticky ก็จะไม่รู้ และทำตัวเหมือน relative

```
.box-bottom {
  background-color: darkgreen;
  position: sticky;
  top: 240px;
}
```

`Note :` sticky จะคล้ายกับ fixed

- absolute -> อิสระ ถูก remove ออกจาก flow html
- fixed -> เป็น absolute ที่ fixed position เวลาเลื่อนจะติดกับหน้าจอมาด้วยเสมอ
- relative -> relative กับ default position ของมัน
- sticky -> เป็น relative ที่ stick position เวลาเลื่อนมาถึงและเกิน position จะติดกับหน้าจอมาด้วยเสมอจนกว่าจะเลื่อนถึงล่างสุดมันถึงจะหลุด (`ต้องใช้ร่วมกับ offset properties(ส่วนใหญ่ก็ใช้กับ top) เสมอ`)

### Z-Index

- z-index เป็นตัวกำหนดความตื้น,ลึก ของ element
- บางครั้งการจัด position อาจทำให้ element เกิดการ overlap เราใช้ z-index ในการแก้ปัญหาเรื่องเหล่านี้
- z-index รับค่าเป็น interger
- default z-index = 0
- z-index ไม่สามารถใช้กับ static ได้ ต้องกำหนดให้เป็น relative ก่อน (`หรือ position อะไรก็ได้ที่ไม่ใช่ static`)

```
.blue-box {
  background-color: blue;
  position: relative;
  z-index: 1;
}

.green-box {
  background-color: green;
  position: relative;
  top: -170px;
  left: 170px;
}
```

### Inline Display

- inline จะเรียงจากซ้ายไปขวา ไม่ขึ้นบรรทัดใหม่
- จะกว้างเท่ากับ content ไม่กางเต็มพื้นที่
- ไม่สามารถ set width,height ได้
- ยกตัวอย่าง element ที่เป็น inline เช่น `<em>`, `<strong>`, `<span>`, `<a>`
- สามารถกำหนดให้ element ที่ไม่ใช่ inline ให้เป็น inline ได้ ดังตัวอย่างข้างล่าง

```
h1 {
  display: inline;
}
```

`Note : `

- https://developer.mozilla.org/en-US/docs/Glossary/Inline-level_content

### Display: Block

- block จะเรียงจากบนลงล่าง ขึ้นบรรทัดใหม่เสมอ
- จะกว้างเต็มพื้นที่
- block element หรือ block-level element
- สามารถ set width,height ได้
- ยกตัวอย่าง element ที่เป็น block เช่น `<h1>` - `<h6>`, `<p>`, `<div>`, `<footer>`
- สามารถกำหนดให้ element ที่ไม่ใช่ block ให้เป็น block ได้ ดังตัวอย่างข้างล่าง

```
strong {
  display: block;
}
```

`Note : `

- https://developer.mozilla.org/en-US/docs/Glossary/Block-level_content

### Display: Inline-Block

- เป็นการรวม feature ของ inline กับ block
- จะเรียงจากซ้ายไปขวา ไม่ขึ้นบรรทัดใหม่
- จะกว้างเท่ากับ content ไม่กางเต็มพื้นที่
- set width,height ได้
- ยกตัวอย่าง element ที่เป็น inline-block เช่น `<img>`

```
.rectangle {
  display: inline-block;
  width: 200px;
  height: 300px;
}

<div class="rectangle">
  <p>I’m a rectangle!</p>
</div>
<div class="rectangle">
  <p>So am I!</p>
</div>
<div class="rectangle">
  <p>Me three!</p>
</div>
```

### Float

- float เอาไว้ position element ให้อยู่ซ้ายสุดหรือขวาสุดเท่าที่จะเป็นไปได้
- ไม่นิยมใช้กันแล้ว
- CSS grid, flexbox เป็นตัวเลือกที่ดีกว่าในการจัดการ
- float มี 4 value
  - left -> move ไปซ้ายสุดเท่าที่จะเป็นไปได้
  - right -> move ไปขวาสุดเท่าที่จะเป็นไปได้
  - none -> ไม่มีการ float (`default`)
  - inherit -> inherit ตาม parent
- สามารถใช้กับ static,relative ได้

### Clear

- การ float multiple element บางทีจะเกิดปัญหาเมื่อ แต่ละ element มี height ที่แตกต่างกัน ส่งผลทำให้ element สามารถชนกัน และไม่ยอมให้ element อื่นๆ move ไปซ้ายหรือขวาได้อย่างที่ควรจะเป็น
- clear เป็นตัวกำหนดว่ามันควรจะจัดการยังไงเมื่อเกิดการชนกันกับ float element มี 4 value (`ใช้กับ element ที่ชนกันกับ float element แล้วส่งผลทำให้ float element move ไปซ้าย ขวาเพี๊ยน`)
  - left -> push element ที่ชนให้ไปอยู่ด้านล่างของ left floated elements
  - right -> push element ที่ชนให้ไปอยู่ด้านล่างของ right floated elements
  - both -> push element ที่ชนให้ไปอยู่ด้านล่างของ leftหรือright floated elements
  - none -> ไม่ทำอะไร ​(`default`)
- float กับ clear ต้อง set value ให้ตรงกัน เพื่อให้มัน map การ push element ไปอยู่ด้านล่างของ ประเภท float element ได้ถูกต้องตรงกัน ถ้า set ไม่ตรงกันมันจะเพี๊ยนเหมือนเดิมมีค่าเท่ากับ none (`default`)

`Note : `

- https://www.w3schools.com/css/css_float_clear.asp

## Dev Tools for Develop

- Tab Elements จะมี source code html ของ page พร้อม style css (Tab Styles,Computed)
- ตอนที่เรา inspect tab Styles จะมี css rule บางตัวถูกขีดค่า แสดงว่า css rule ตัวนั้นถูก overwrite และไม่ใช้แล้ว(`การไปเปลี่ยนแปลงมันไม่มีผลอะไร`)
  ![horizontal-black-line](/images/horizontal-black-line.png "horizontal-black-line")
- tab Styles จะมี style css ทุก style ที่ถูกใช้กับ element นั้นๆ
- tab computed(computed style) คือ specific style ของ element นั้นๆ และก็มี box model ให้ดู (content widht,height,padding,border,margin)
  ![computed-tab](/images/computed-tab.png "horizontal-black-line")
- การ modify html & css บน dev tools ไม่มีผลต่อ source code จริง
- เราสามารถ modify เพิ่ม,ลบ,แก้ไข html ได้
- เราสามารถ modify เพิ่ม,ลบ,แก้ไข style css ได้ ที่ tab Styles
- สามารถเปลี่ยน property เกี่ยวกับ box model ได้ที่ tab Computed

## Color

- set value color ได้ 3 แบบ
  - named color -> keyword color (https://developer.mozilla.org/en-US/docs/Web/CSS/named-color)
  - RGB -> เป็นตัวเลขที่แสดงถึงการ mix กันของ red,green,blue
  - HSL -> เป็นตัวเลขที่แสดงถึงการ mix กันของ hue,saturation,lightness

### Foreground vs Background

- การ set color มี 2 แบบ
  - Foreground: สี element (color)
  - Background: สี background element (background-color)

```
h1 {
  color: red;
  background-color: blue;
}
```

### Hexadecimal(Hex colors)

- Hex color เป็น format value ของค่าสีในเลขฐานสิบหก
- จะต้องเริ่มต้นด้วย (`#`) เสมอ
- มี 3 หรือ 6 digits
- hex color แสดงถึงค่าของ red,green,blue
- ถ้า hex มันมีตัวซ้ำกัน2ตัว สามารถยุบเป็น 1 ตัวได้ เช่น
  - #00 00 00 => #000
  - #FF FF FF => #FFF
  - #00 FF FF => #0FF
- Hexadecimal จะมี 16 ตัว คือ 0-9 , A-F (10-15)
- hex color จะเป็น uppercae หรือ lowercase ก็ได้

```
darkseagreen: #8FBC8F
sienna:       #A0522D
saddlebrown:  #8B4513
brown:        #A52A2A
black:        #000000 or #000
white:        #FFFFFF or #FFF
aqua:         #00FFFF or #0FF

background-color: #9932cc;
```

### RGB Colors

- RGB Color เป็น format value ของค่าสีใน RGB system
- rgb(red, green, blue);
- ค่าสีแต่ละตัวเป็นได้ตั้งแต่ 0-255 (decimal)

```
h1 {
  color: rgb(23, 45, 23);
}
```

### HSL (Hue, Saturation, and Lightness)

- HSL(`hue-saturation-lightness color`) เป็น format value ของค่าที่แสดงถึง hue(สี),saturation(ความอิ่มตัว),lightness(ความสว่าง)
- hsl(hue,saturation,lightness)
  - hue -> ค่าสี ตั้งแต่ 0-360
  - saturation -> ค่าความอิ่มสี เป็น percent
  - lightness -> ค่าความสว่าง เป็น percent

```
color: hsl(120, 60%, 70%);
```

- hue แสดงถึง angle ของ color wheel

  - Red 0 , Green 120 , Blue 240 และกลับมาที่ Red 360

  ![color-wheel](/images/color_wheel_4_background.svg "color wheel")

- saturation แสดงถึงค่าความอิ่มตัวของสี (ความเข้ม,ความใส)
  - increase toward 100% -> สีจะเข้มข้นขึ้น
  - decrease toward 0% -> สีจะกลายเป็นสีเทา
- lightness แสดงถึงค่าความสว่าง
  - 50% -> normal lightness
  - increase toward 100% -> สีจะสว่างขึ้น
  - decrease toward 0% -> สีจะมืดลงจนเป็นสีดำ

### Opacity and Alpha

- Opacity,Alpha คือความทึบแสง,ความโปร่งใส
- เราสามารถ set opacity(alpha) ให้ rgb,hsl ได้
- opacity(alpha) 0-1 (decimal)
  - 0 -> หายไปเลย ไม่แสดง
  - 1 -> ไม่โปร่งใส(ทึบแสง ดำเลย)
- hsla(hue, saturation, lightness, `alpha/opacity`)
- rgba(red, green, blue,`alpha/opacity`)

  ```
  color: hsla(34, 100%, 50%, 0.1);
  color: rgba(234, 45, 98, 0.33);
  ```

- hex color สามารถ set opacity(alpha) ได้เหมือนกัน
  - add 2 digit ต่อท้าย hex 6 digits (#52BC82`80`)
  - add 1 digit ต่อท้าย hex 3 digits (#F00`3`)
  - range opacity ของ hex color คือ 00 (โปร่งใส) - FF (ทึบแสง).
- named color set opacity(alpha) ไม่ได้
- named color มี keyword สำหรับ zero-opacity -> transparent

  - มันจะเท่ากับ rgba(0, 0, 0, 0)

  ```
  color: transparent;
  ```

## Typography

### Font Family

- กำหนด style รูปแบบของ font

  ```
  h1 {
    font-family: Arial;
  }
  ```

- Multi-Word Values -> ถ้าเป็นชื่อ font ที่มีหลายคำใช้ `' '` ครอบ

  ```
  h1 {
    font-family: 'Times New Roman';
  }
  ```

- Web Safe Fonts
  - เป็น font ที่ support ทุก browser,OS(operating systems)
  - บาง font อาจะไม่ support กับบาง browser
  - list web safe font: https://www.cssfontstack.com/
- Fallback Fonts and Font Stacks
  - font stack -> group ของ font ที่เหมือนกัน
  - fallback font -> browser จะเลือกใช้ font ใน font stack ไล่จากซ้ายไปขวา ถ้า font ที่เจอไม่ support ก็จะขยับไปใช้ font ตัวต่อไปใน font stack
  - จากตัวอย่างข้างล่าง browser จะพยายามใช้่ font Caslon ก่อน ถ้าไม่มี ก็จะไปใช้ Georgia,Times New Roman ต่อตามลำดับ
  ```
  h1 {
  // font stack
  font-family: Caslon, Georgia, 'Times New Roman';
  }
  ```
- Serif and Sans-Serif

  - font จะแบ่งออกเป็น 2 group ใหญ่ๆ คือ Serif, Sans-Serif
  - ยกตัวอย่าง Caslon, Georgia, Times New Roman เป็น serif fonts
  - Serif จะมี extra detail ที่ส่วนท้ายของตัวอักษรแต่ละตัว
  - Sans-Serif จะปกติ ไม่มี extra detail ที่ส่วนท้ายของตัวอักษรแต่ละตัว

  ![serif-san-serif](/images/htmlcss1-diagram__fontanatomy.svg)

  - serif, sans-serif จะถูกใช้เพิ่มเข้าไปเป็นตัวสุดท้ายของ fallback font ถ้าไม่มี font ไหนเลยใน font stack มันก็จะใช้ font อะไรก็ได้ที่เป็น serif หรือ sans-serif ที่อยู่ในระบบ

  ```
  h1 {
  font-family: Caslon, Georgia, 'Times New Roman', serif;
  }
  ```

### Font Weight

- กำหนด style ความหนา,บาง font
- กำหนดด้วยตัวเลขหรือ keyword
- Keyword Values
  - bold: font หนา
  - normal: normal font weight เป็น default value
  - lighter: ค่า font weight จะบางกว่าของ parent
  - bolder: ค่า font weight จะหนากว่าของ parent
- Numerical Values

  - เป็นตัวเลขตั้งแต่ 1-1000 (บางสุด-หนาสุด)
  - 400 = normal
  - 700 = bold

  ```
  .left-section {
    font-weight: 700;
  }

  .right-section {
    font-weight: bold;
  }
  ```

`Note : `

- การกำหนด font-weight เป็นตัวเลขไม่ได้มีในทุก font
- ต้องเช็ค font ที่ใช้ด้วยว่า สามารถกำหนด font-weight เป็นตัวเลขได้มั้ย

### Font Style

- กำหนด font style
  - normal -> ตัวปกติ default
  - italic -> ตัวเอียง

```
h3 {
  font-style: italic;
}
```

### Text Transformation

- เป็นการกำหนดรูปแบบ text
  - uppercase -> ตัวพิมพ์ใหญ่หมด
  - lowercase -> ตัวพิมพ์เล็กหมด

```
h1 {
  text-transform: uppercase;
}
```

### Text Layout

- Letter Spacing
  - set space ระหว่างตัวอักษร
  - ใช้หน่วย unit (px,em)
  ```
  p {
    letter-spacing: 2px;
  }
  ```
- Word Spacing
  - set space ระหว่างคำ
  - ใช้หน่วย unit (px,em)
  - แนะนำว่าใช้ em ดีกว่า px เพราะ space จะถูก set base ตาม size ของ font
  ```
  h1 {
    word-spacing: 0.3em;
  }
  ```
- Line Height
  - set ความสูงให้บรรทัดของ text
  - ความสูงของ text จะขึ้นอยู่กับ font size
  - การ set line-height จะไปเพิ่มความสูงให้บรรทัดของ text นั้นๆ
  - ใช้หน่วย unit (px,em,%) หรือเป็นตัวเลขก็ได้(`unitless`)
    ![line height](/images/htmlcss1-diagram__leading_updated_1-01.svg)
  ```
  p {
    line-height: 1.4;
  }
  ```
  - ถ้า set เป็น unitless การเปลี่ยนแปลง font size จะ auto ปรับ line height ให้ (`unitless มันจะ responsive base on current font size)`
- Text Alignment ([Go to Text Align](#text-align))

  - กำหนดการวางตำแหน่งของ text โดยอิงกับ parent ของมัน

### Web Fonts
