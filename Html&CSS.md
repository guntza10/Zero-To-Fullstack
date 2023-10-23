# HTML

- hypertext markup language (เป็น raw text)
- structures website content like layout,text,images,videos,elements
- มี element tag ของ element นั้นๆ
- มี attribute เอาไว้กำหนดคุณสมบัติต่างๆให้ element tag
- `<link rel="stylesheet" href="style.css">` เป็นการเรียกใช้ css file ใน html
  - rel เป็น attribute ที่ระบุ relation ระหว่าง current document กับ link resource

## Common Elements

### Body

- จะมีแค่ content ใน body เท่านั้นที่จะถูก display to screen

```
<body>
    ...content...
</body>
```

### Heading

- สำหรับ text ที่เป็น title
- การกำหนด heading ต้องกำหนดเป็นลำดับขั้น อย่า skip heading เช่น ใช้ h1 แล้วข้าม h2 ไปเป็น h3 เลย ไม่ได้ เพราะ (`ภายใต้ parent element เดียวกัน`)
  - screen reader ใช้ heading tag ในการช่วย user navigate ผ่าน page
  - ถ้าเรา skip heading มันจะทำให้ตัว screen reader สับสนได้ เพราะ heading hierarchy มีความสำคัญต่อการ read ของ screen reader
  - ควรหลีกเลี่ยงการ skip heading hierarchy
  - อีกเหตุผลคือบางทีมันไม่ใช่ heading เป็นแค่ content แต่เราไปกำหนด heading มันผิดความหมาย (incorrect semantic)

```
<h1> </h1>
<h2> </h2>
<h3> </h3>
<h4> </h4>
<h5> </h5>
<h6> </h6>
```

### Div

- เป็น element ที่เอาไว้ grouping elements ที่ต้องการ apply same style

### Paragraph and Span

- เอาไว้ display text
- paragraph => เป็น block element (block text)
- span => เป็น inline element (inline text)

```
<p></p>
<span></span>
```

### Styling Text

- strong => highlight คำ
- em => highlight คำ ด้วยการทำให้เป็นตัวเอียง

```
<strong></strong>
<em></em>
```

### Line Breaks

```
<br>
```

### Unordered Lists

- display list แต่ละตัวเป็น bullet point

```
<ul>
  <li>Limes</li>
  <li>Tortillas</li>
  <li>Chicken</li>
</ul>
```

### Ordered Lists

- display list แต่ละตัวเป็นเลขลำดับ

```
<ol>
  <li>Preheat the oven to 350 degrees.</li>
  <li>Mix whole wheat flour, baking soda, and salt.</li>
  <li>Cream the butter, sugar in separate bowl.</li>
  <li>Add eggs and vanilla extract to bowl.</li>
</ol>
```

### Image

- เป็น image content
- attribute src เอาไว้ ref image ที่เราต้องการเอามา display อาจจะเป็น url หรือ local address ก็ได้
- เป็น Self-closing tag
- attribute alt(alternative text) เป็น attribute ที่เอาไว้อธิบาย image
  - load image fail มันจะแสดง (ถ้า load image fail เราสามารถเอา mouse ไป hover มันจะโชว์ alt ของเรา)
  - เอาไว้ให้ screen reader อ่าน (screen reader สามารถอ่านแล้วก็พูดเสียงออกมาเพื่อให้ผู้พิการทางสายตาเข้าใจว่าคือรูปอะไร)
  - มีผลต่อการทำ SEO(Search Engine Optimization) เพราะ search engine ไม่สามารถมองเห็น image ได้ การมี alt สามารถช่วย improve ranking ของ website ได้
  - การกำหนด alt ควรให้กระชับ สั้นๆ ได้ใจความ ไม่ควรตั้งเป็นประโยคยาว

```
<img src="image-location.jpg" />
```

`Note :`

- URL(uniform resource locator) => จะเป็น web address หรือ local address ที่เก็บไฟล์ก็ได้.
- Pair tag/Container tag -> คือมี opening tag กับ closing tag ครอบ content
- Self-closing tag -> คือไม่ต้องมี opening tag กับ closing tag ครอบ content มันเปิด ปิดตัวเองเพราะไม่ต้องครอบ content ใดๆ

### Video

- video content
- attribute width,height เอาไว้กำหนด width,height ให้ video
- attribute controls เป็นการกำหนด basic video controls เพื่อให้ browser รู้จักการใช้งานพวก play,pause
- ไม่ได้เป็น Self-closing tag เหมือน image จะมี content ข้างใน มี opening tag,closing tag ครอบ
  - content จะแสดงก็ต่อเมื่อ browser load video ไม่ได้

```
<video src="myVideo.mp4" width="320" height="240" controls>
  Video not supported
</video>
```

## How to structure

# CSS

- applies styling to websites
- selector คือส่วนที่เราต้องการเขียน css ให้แบบ specific อาจจะเป็น element selector,class selector เป็นต้น
