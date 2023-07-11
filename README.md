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
วิธีในการแยกชั้น (Naming Domain Layer)
- Define ชั้นของ Domain layer ก่อนเป็นอันดับแรก
  มีการตั้งชื่อชั้นนี้ได้หลากหลายชื่อมาก เช่น handler, controllers, usecases, businesslogic, app, pkg, domain, ตั้งชื่อตามสิ่งที่จะทำ(todo)  etc.
- Coupling ของชั้นนี้ต้องเป็นแบบ low coupling และ high cohesion
  - หา dependency แล้วหาทางแยกออกมาจาก domain เช่น การเชื่อมต่อฐานข้อมูล การเชื่อมต่อกับภายนอก การเชื่อมต่อกับ framework ต่าง ๆ (gorm, gin, echo, etc.)
  - ถ้าเราจะเอา gorm ออก ต้องคิดว่าจะเอาอะไรเข้ามาแทน ให้ใช้จินตนาการ แล้วสร้าง interface ขึ้นมา เช่น type storer interface { New(*Domain) error }
  - เปลี่ยน handler ให้ใช้ interface storer เช่น type Handler struct { store storer }
  - สร้าง storer ที่ทำงานกับ gorm.DB ไว้อีกชุดนึง เช่น TodoStore แยกออกมาเป็นอิสระ เช่น type TodoStore struct { db *gorm.DB }
  - ตัว Domain จะต้องมองไม่เห็นคนอื่น แต่คนอื่นมองเห็น Domain ได้
  - เปลี่ยนวิธีการสร้าง router ใหม่ เช่น
    ginrouter := router.New(protected)
    todoStore := store.NewTodoStore(db)
    todoHandler := todo.NewTodoHandler(todoStore)
```

## Reference

- [Clean Architecture](https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html)
- [Clean Architecture in Go](https://medium.com/@eminetto/clean-architecture-in-go-4030f11ec1b1)
- [golang-standards project-layout](https://github.com/golang-standards/project-layout)

```

```
