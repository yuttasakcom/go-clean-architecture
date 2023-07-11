# Go Clean Architecture

## How to write a clean architecture in Go

```
Go มีแนวคิดที่เรียบง่าย และ มีความยืดหยุ่นสูง สามารถเขียนโค้ดได้หลากหลายรูปแบบ
ไม่มีการออกแบบที่เป็นมาตราฐาน แต่มีแนวคิดที่เรียกว่า Clean Architecture ที่เป็นแนวทางในการออกแบบโค้ด และ โครงสร้างโปรเจค ให้มีความยืดหยุ่นสูง สามารถทำงานได้ดีในระยะยาว โดยไม่ต้องเปลี่ยนแปลงโครงสร้างโปรเจคใหม่

โดยมีการแยกส่วนของโค้ดออกเป็น 3 ส่วน คือ
- Presentation
- Business Logic
- Data Access

โดยแต่ละส่วนจะมีความเชื่อมโยงกันเพียงเล็กน้อย และ สามารถแยกออกจากกันได้ โดยไม่มีผลกระทบกับส่วนอื่น ๆ ของโค้ด และ สามารถทำงานได้แยกกัน โดยไม่ต้องรู้จักกัน

การออกแบบโครงสร้างโปรเจคแบบนี้เพื่อ
- Easy to Test
- Easy to Change
- Easy to Read

Hexagonal Architecture หรือ Ports and Adapters
แบ่งออกเป็น 2 ฝั่ง
- API
- SPI

Framwork(inbound) --> API --> Domain <-- SPI <-- Infrastructure/External(outbound)

                    | Bisiness Logic Domain Object |

```

```

## Reference

- [Clean Architecture](https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html)
- [Clean Architecture in Go](https://medium.com/@eminetto/clean-architecture-in-go-4030f11ec1b1)
- [golang-standards project-layout](https://github.com/golang-standards/project-layout)
```
