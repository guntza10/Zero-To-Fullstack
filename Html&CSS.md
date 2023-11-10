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

## Structure HTML

### `<!DOCTYPE html>`

- ประกาศเพื่อบอก browser ว่าเป็น type html,version html(HTML 5)

### `<html>`

- code ที่อยู่ภายใต้ tag html จะถูกแปลงเป็น html code เพื่อให้ browser อ่านได้
- ถ้าไม่เขียน code html ภายใต้ tag html browser จะไม่สามารถอ่าน code html นั้นๆได้

### `<head>`

- จะ contain metadata ของ web
- metadata เป็น info เกี่ยวกับ web ที่ไม่ได้ display โดยตรงให้เห็นบน web

#### `metadata`

1. `<title>`

- ชื่อที่แสดงที่ tab bar
- ควรตั้งให้น้อยกว่า 64 characters

### `anchor tag`

- `<a href="url">...<a>`
- link to Other Web Pages with href attribute (`hyperlink reference`)
- attribute `target="_blank"` เอาไว้ navigate เปิด tab ใหม่
- สามารถใช้ href navigate ไปหน้าเดียวกันได้ เพื่อให้ scroll ไปที่ content ที่เราต้องการ

  - กำหนด id ให้ element ที่เราต้องการให้ navigate ในหน้าเดียวกันนี้
  - กำหนด anchor tag พร้อมด้วย href="#id"

### `comments`

- `<!-- ...content will be comment... -->`

```
<!-- This is a comment that the browser will not display.
-->
```

## Debugging HTML

- เกิดได้จาก 2 สาเหตุ
  - Syntax errors
  - Logic errors
- ถึงแม้จะเกิด error html browser ก็ยังสามารถแปลง html ได้ แล้ว render อยู่ดี
  - HTML is parsed permissively because when the web was first created, it was decided that allowing people to get their content published was more important than making sure the syntax was absolutely correct. The web would probably not be as popular as it is today, if it had been more strict from the very beginning.

`Note :` https://validator.w3.org/#validate_by_uri

## Table

### Table Rows

- ทุก table data จะต้องอยู่ภายใต้ table row

```
<table>
  <tr>
  </tr>
  <tr>
  </tr>
</table>
```

### Table Data

- display table data สำหรับแต่ละ cell(column)

```
<table>
  <tr>
    <td>73</td>
    <td>81</td>
  </tr>
</table>
```

### Table Headings

- มี attribute 2 ตัวสำหรับ table heading
- attribute scope row => เป็นการบอกว่าเป็น heading สำหรับ row
- attribute scope col => เป็นการบอกว่าเป็น heading สำหรับ column

```
<table>
  <tr>
    <th></th>
    <th scope="col">Saturday</th>
    <th scope="col">Sunday</th>
  </tr>
  <tr>
    <th scope="row">Temperature</th>
    <td>73</td>
    <td>81</td>
  </tr>
</table>
```

### Table Borders

- ใน html version เก่า attribute border ถูกใช้เพื่อกำหนดให้ border ของ table display โดยใส่เป็น integer (เป็นระดับความหนาของ border)
- ใน html version ใหม่ เลิกใช้ attribute border นี้แล้ว
- เราใช้ css ในการตกแต่ง border แทน

```
<table border="1">
  <tr>
    <td>73</td>
    <td>81</td>
  </tr>
</table>
```

### Spanning Columns

- attribute colspan กำหนดให้ table data นั้นๆ กินพื้นที่กี่ column heading (ต้องเป็น interger >= 1)
- จากตัวอย่าง table data "Out of Town" กินพื้นที่ table heading Monday,Tuesday

```
<table>
  <tr>
    <th>Monday</th>
    <th>Tuesday</th>
    <th>Wednesday</th>
  </tr>
  <tr>
    <td colspan="2">Out of Town</td>
    <td>Back in Town</td>
  </tr>
</table>
```

### Spanning Rows

- attribute rowspan กำหนดให้ table data นั้นๆ กินพื้นที่กี่ row (ต้องเป็น interger >= 1)

```
 <table>
    <tr>
      <!-- Row 1 -->
      <th></th>
      <th>Saturday</th>
      <th>Sunday</th>
    </tr>
    <tr>
      <!-- Row 2 -->
      <th>Morning</th>
      <td rowspan="2">Work</td>
      <td rowspan="3">Relax</td>
    </tr>
    <tr>
      <!-- Row 3 -->
      <th>Afternoon</th>
    </tr>
    <tr>
      <!-- Row 4 -->
      <th>Evening</th>
      <td>Dinner</td>
    </tr>
  </table>
```

![rowspan](/images/rowspan.png "rowspan example")

### Table Body

- contain all table data ยกเว้น table heading
- เป็นการแบ่ง section ของ table data โดยการ group ให้เป็นอันเดียวกัน

```
  <table>
    <tbody>
      <tr>
        <td>Adam's Greenworks</td>
        <td>14</td>
        <td>Package Items</td>
      </tr>
      <tr>
        <td>Davie's Burgers</td>
        <td>2</td>
        <td>Send Invoice</td>
      </tr>
      <tr>
        <td>Baker's Bike Shop</td>
        <td>3</td>
        <td>Send Invoice</td>
      </tr>
      <tr>
        <td>Miss Sally's Southern</td>
        <td>4</td>
        <td>Ship</td>
      </tr>
      <tr>
        <td>Summit Resort Rentals</td>
        <td>4</td>
        <td>Ship</td>
      </tr>
      <tr>
        <td>Strike Fitness</td>
        <td>1</td>
        <td>Enter Order</td>
      </tr>
    </tbody>
  </table>
```

### Table Head

- contain all table heading
- เป็นการแบ่ง section ของ table heading โดย group ให้เป็นอันเดียวกัน
- thead ยัง require tr ในการ contain th
- จะมีแค่ column heading th ที่อยู่ใน thead เท่านั้น ที่จะใช้ attribute scope ได้(เพื่อบ่งบอกว่าเป็น row หรือ col heading)

```
  <table>
    <thead>
      <tr>
        <th scope="col">Company Name</th>
        <th scope="col">Number of Items to Ship</th>
        <th scope="col">Next Action</th>
      </tr>
    </thead>
  </table>
```

### Table Footer

- เป็นการแบ่ง section ของ table data ที่เกี่ยวกับ sums, differences, results โดย group ให้เป็นอันเดียวกัน

```
<tfoot>
  <tr>
    <th>Total</th>
    <td>$22M</td>
    <td>$12.5M</td>
  </tr>
</tfoot>
```

`Note : ` เราสามารถแต่ง style ให้ table ด้วย css

## Semantic HTML

### Why use Semantic HTML?

- Accessibility => Semantic HTML makes webpages accessible for mobile devices and for people with disabilities as well. This is because screen readers and browsers are able to interpret the code better.
- SEO => It improves the website SEO. search engines are better able to identify the content of your website and weight the most important content appropriately
- Easy to Understand => code easier to read for other web developers

### Header and Nav

1. Header(`<header>`) => container usually for either navigational links or introductory content containing `<h1>` to `<h6>` headings.
2. Nav(`<nav>`) => a block of navigation links such as menus and tables of contents

   - can be used inside of the `<header>` element but can also be used on its own.

```
<header>
  <nav>
    <ul>
      <li><a href="#home">Home</a></li>
      <li><a href="#about">About</a></li>
    </ul>
  </nav>
</header>
```

### Main and Footer

1. Main(`<main>`)

- contain main content of web

```
<main>
  <header>
    <h1>Types of Sports</h1>
  </header>
  <article>
    <h3>Baseball</h3>
    <p>
      The first game of baseball was played in Cooperstown, New York in the summer of 1839.
    </p>
  </article>
</main>
```

2. Footer(`<footer>`)

- contains information such as
  - Contact information
  - Copyright information
  - Terms of use
  - Site Map
  - Reference to top of page links
- อยู่ใต้สุดของ webpage

```
<footer>
  <p>Email me at Codey@Codecademy.com</p>
</footer>
```

### Article and Section

1. Section(`<section>`) => defines elements in a document, such as chapters, headings, or any other area of the document with the same theme. (part group ของ content ที่เหมือนๆกัน)
2. Article(`<article>`) => can hold content such as articles, blogs, comments, magazines, etc. (that might contain a combination of text, images, audio, etc.)

`Note : ` Section,Article สามารถสลับ inside กันและกันได้ ขึ้นอยู่กับ context

```
<section>
  <h2>Fun Facts About Cricket</h2>
  <article>
    <p>A single match of cricket can last up to 5 days.</p>
  </article>
</section>
```

### The Aside Element

- เป็นส่วนเสริมของ content ที่มา enhance element อื่นๆ (ไม่ได้ required ว่าต้องใส่)
- ถูกใช้ใน
  - content เสริมให้ article,section
  - content เสริมด้านข้างๆ ซ้าย ขวา (additional sidebar)
- contain additional information next to a main piece of content

```
<article>
  <p>The first World Series was played between Pittsburgh and Boston in 1903 and was a nine-game series.</p>
</article>
<aside>
  <p>
   Babe Ruth once stated, “Heroes get remembered, but legends never die.”
  </p>
</aside>
```

### Figure and Figcaption

- figure => contain media content
- figcaption => contain description ของ media
- figure,figcaption ใช้ร่วมกันเพื่อ grouping ​media with a caption.

```
<figure>
  <img src="overwatch.jpg">
  <figcaption>This picture shows characters from Overwatch.</figcaption>
</figure>
```

### Audio and Attributes

- is used to embed audio content
- ref audio file with src attribute (ใน source tag)
- ref type audio with type attribute (ใน source tag) (มีหรือไม่มีก็ได้ it helps the browser identify it more easily and determine if that type of audio file is supported by the browser.)
- มีหลาย attribute ให้ใช้ มี 3 ตัวหลักที่ใช้
  - controls: display audio controls พวก play,pause,mute เป็นต้น
  - src: url audio file
  - autoplay: เล่น audio auto
- attribute ส่วนใหญ่จะใช้กับ audio tag (จะมีแค่ src,type ที่ใช้กับ source tag)

```
<audio>
  <source src="iAmAnAudioFile.mp3" type="audio/mp3">
</audio>
```

`Note: ` https://developer.mozilla.org/en-US/docs/Web/HTML/Element/audio#attributes

### Video and Embed

- video มี attribute ที่ใช้บ่อยๆ

  - controls: display video control พวก play,pause,volume control,fullscreen option.
  - autoplay: autoplay video เมื่อ load หน้าเว็บเสร็จ
  - loop: loop video

- content ที่อยู่ใน tag video จะ display ตอนที่เว็บไม่สามารถ display video ได้

```
<video src="coding.mp4" controls>
  Video not supported
</video>
```

- embed ใช้กับพวก media ต่างๆ (image,video,audio,gif)
- เลิกใช้แล้ว (มีพวก tag img,video,audio ให้ใช้แทน)

```
<embed src="download.gif"/>
```

### Summary

- ช่วย specific meaning element
- ช่วยให้ screen reader สามารถ access,translate webpage ได้ดีขึ้น
- ช่วย improve seo
- `<header>`, `<nav>` , `<main>` and `<footer>` create the basic structure of the webpage.
- `<section>` defines elements in a document, such as chapters, headings, or any other area of the document with the same theme.
- `<article>` contain content such as articles, blogs, comments, etc.
- `<aside>` contains information that is related to the main content, but not required in order to understand the dominant information.
- `<figure>` contain all types of media.
- `<figcaption>` is used to describe the media in `<figure>`.
- `<video>`, `<embed>`, and `<audio>` elements are used for media files.

## How to structure

# CSS

- applies styling to websites
- selector คือส่วนที่เราต้องการเขียน css ให้แบบ specific อาจจะเป็น element selector,class selector เป็นต้น
