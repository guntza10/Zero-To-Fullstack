# Zero-To-Fullstack

# Internet vs World wide web(www)

## Internet

- เป็น network ที่เชื่อม computer หรือ device
  ทั่วโลกให้สามารถส่งข้อมูลระหว่างกันได้
- ใช้ TCP/IP protocol ในการ transfer data ระหว่าง network

`Note : ` protocol เป็น standard หรือ rule

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
