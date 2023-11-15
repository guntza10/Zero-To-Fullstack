# Zero-To-Fullstack

# Internet vs World wide web(www)

## Internet

- เป็น network ที่เชื่อม computer หรือ device
  ทั่วโลกให้สามารถส่งข้อมูลระหว่างกันได้
- ใช้ TCP/IP protocol ในการ transfer data ระหว่าง network

`Note :` protocol เป็น standard หรือ rule ที่ต้องมีในการทำงานร่วมกัน

## World wide web(www)

- ui ของ website ที่ user สามารถดู multimedia content ต่างๆ และ interact กับตัว website เองหรือ user คนอื่นๆได้

# Browsers and Servers

## Client

- device ของ user หรือ program ที่จะ make request for data ไปที่ server
- อาจจะเป็น browser, application ที่รันบน device ต่างๆของ user

## Server

- device หรือ program บน network
- ที่รอ request จาก client แล้ว send data กลับไปที่ client
- อาจจะเป็น in-house server,rented server at data center,cloud server
- ใช้ store resources พวก website files,datas,videos,images

## Process between client and server

- browser จะส่ง request ไปที่ server เพื่อขอ file สำหรับ render สร้างหน้าเว็บ
- server จะส่ง response neccessary file กลับมา
- browser เอา file ที่ได้มา render หน้า website
- browser communicate server ด้วย HTTP(`hypertext transfer protocol`) ที่ allow data transfer
- https มันคือ HTTP ที่เพิ่มความ secure ให้การ transfer data
- HTTP protocol จะมี HTTP method ที่เป็นการกำหนด type สำหรับ request
  - GET
  - POST
  - PUT
  - DELETE
- server จะ send response กลับมาพร้อม status code

## Summary

- browser send request ไปที่ server และ display or render website files
- server store website files และ send back กลับไปที่ web browser เมื่อเกิด request
- HTTP(`hypertext transfer protocol`) เป็น standard หรือ rule ที่ browser และ server transfer data ระหว่างกัน

## Status code

- เป็นสิ่งที่ server ส่งกลับมาพร้อม response เพื่อบอกให้ browser รู้ว่า request ที่ส่งไป successful หรือ error
- status code จะช่วยให้ browser รู้ว่าจะ handle กับ data ที่ถูกส่งกลับมากับ response นี้แบบไหน
- 200(ok) -> request succeed
- 301(moved permanently) -> resource ถูกย้ายแล้ว และ client กำลังถูกเปลี่ยนเส้นทาง
- 404(not found) -> the requested resource was not found
- 500(Internal server error) -> error ที่เกิดจาก server

## How Do Browsers Work?

- ทุกครั้งที่ browser โหลดหน้า webpage ขึ้นมา 1 ครั้ง จะมีการส่ง multiple request พร้อมๆกันไปที่ server
- หลังจากที่เราใส่ url แล้ว enter server จะ process และส่ง html file กลับมาที่ client
- ใน html file จะมี content ของ website ทั้งหมด
- browser จะ search element ใน html file แล้วก็เริ่ม request พวก external resources ทั้งหมดที่ถูกใช้ใน html file ดังนี้
  - `css` -> server ส่ง css กลับมา browser จะอ่าน css แล้ว apply style ให้กับ element content
  - `request-response cycle` -> server ส่งพวก assets(image,video) กลับมาที่ browser บางที่ถ้ามันมีขนาดใหญ่ ก็อาจจะใช้เวลาในการ render
  - `javascript` -> เป็นตัวทำให้ website มี interactive
- additional request พวกนี้ จะถูก request พร้อมกัน ทำงานเป็น parallel
- resource ทั้งหมดจะถูก render พร้อมกันแสดงออกมาเป็นหน้า website
- process ในการ render หน้า website จะเร็วหรือช้าขึ้นอยู่กับ
  - speed ของการ connection ของ user
  - size ของ website
  - ระยะทางระหว่าง browser กับ server

`Note :` webpage ที่ไม่ใช้ javascript จะเรียกว่า `static webpage`

## Web 2.0

### Web 1.0 (static website)

- เป็น website ที่ให้ user เข้ามาอ่าน content ได้อย่างเดียว
- user ไม่สามารถ interact อะไรกับตัว website ได้
- content ถูกสร้างจากทางเดียว
- เวลามีการเปลี่ยนแปลงหน้า website แค่บางส่วน จะต้อง re-load ทั้งหน้าใหม่

### Web 2.0

- user สามารถ interact กับ website ได้
- user สามารถสร้าง content เองได้บน website (blog,social media)
- สามารถเปลี่ยนแปลงบางส่วนของ website ได้โดยที่ไม่ต้อง re-load ทั้งหน้าใหม่

`Note :` เกิด technical ที่ advance

- jQuery เป็น js framework ตัวแรกที่สามารถ fetch data ได้ในขณะที่ web กำลังรัน
- เกิด web framework ที่ connect database เช่น Spring, Django, Ruby-on-Rails

# WEB DEVELOPMENT

- `HTML` — structures website content
- `CSS` — applies styling to websites
- `JavaScript` — adds interactivity to websites
- `SQL(structured query language)` — allows your web application to store and retrieve data (save, modify, and access data)
