---
description: รูปแบบในการทำงานกับคลาว์
---

# Cloud Native

ในบทความนี้เราจะมาเคลียความเข้าใจเรื่องการใช้งานคลาว์กันนะครับ ว่าที่เราใช้ๆคลาว์กันอยู่นี่มันอยู่ในรูปแบบไหน แล้วมันเหมาะสมหรือยัง

## 🤔 โปรเจคที่มีอยู่เอาขึ้นคลาว์ได้เลยป่ะ ?

สมมุติว่าเราทำเว็บด้วย ASP.NET, Php, Angular หรืออะไรก็แล้วแต่ เราสามารถเอางานพวกนั้นมาขึ้นบนคลาว์แล้วใช้เลยได้ป่ะ ขอบตอบเลยว่า**ส่วนใหญ่จะเอาขึ้นได้เลยครับ** และที่เอาขึ้นมาก็ทำงานแบบ Production ที่ทำๆแบบปรกติได้เลยเช่นกันครับ **แต่การเอาขึ้นมาแบบดิบๆเลยมันจะไม่ได้ใช้ความสามารถของคลาว์แบบเต็มที่เท่าไหร่** พูดให้เห็นภาพคือ เราเอารถปอร์เช่มาขับบนถนนลูกรังไรงี้ ดังนั้นเราควรจะเรียนรู้ลักษณะการทำงานบนคลาว์ด้วย ซึ่งเราเรียกการเขียนแอพที่ออกแบบมาสำหรับคลาว์โดยเฉพาะว่า **Cloud Native** ครับ

## 🤔 ระดับของงานบนคลาว์มีไรบ้าง ?

คราวนี้เราจะมาดูกันว่าทาง Microsoft มี Guideline ในการทำงานบนคลาวเป็นยังไงบ้างจากรูปด้านล่างนี้เลย

![](../../.gitbook/assets/image%20%2855%29.png)

ทาง Microsoft เขาได้แบ่งรูปแบบออกเป็น 4 กลุ่มใหญ่ๆตามนี้ครับ

### 1.Existing apps

\(จากภาพซ้ายสุด\) คือแอพที่เรามีอยู่แล้วอาจจะตั้งอยู่บนเครื่องเซิฟเวอร์ที่บริษัทหรือไปเช่าใน web hosting อะไรก็แล้วแต่จะจัดอยู่ในกลุ่มนี้นะครับ ซึ่งกลุ่มนี้จะถือว่ายังไม่ได้ใช้งานอะไรกับคลาว์เลย

### 2.Cloud Infrastructure-Ready

ในกลุ่มนี้เราก็จะเริ่มเอาของบางอย่างที่เคยอยู่ในเซิฟเวอร์ของตัวเองย้ายมาทำงานบนคลาว์บ้างแล้ว เช่นใช้ VM หรือใช้  Database ที่อยู่บนคลาว์ไรงี้ ซึ่งข้อดีของกลุ่มนี้คือเราก็จะสามารถใช้ความสามารถของคลาว์ได้แล้ว เช่นการทำ Scaling เพื่อรองรับคนปริมาณมากๆไรงี้ แต่นี่ก็เป็นเพียงกลุ่ม 2 ที่ยังไม่ได้ใช้ความสามารถของคลาว์ได้เต็มสูบเท่าไหร่

### 3.Cloud-Optimized

กลุ่มนี้เราเริ่มที่จะถอดของที่เคยใช้เทคโนโลยีที่ทำงานบน On-premise เปลี่ยนมาใช้เทคโนโลยีของคลาว์บ้างแล้ว เช่นตัวเว็บก็มี Application Insight คอยตรวจ มีการทำ CI/CD ต่างๆ เพื่อทำให้ระบบมัน Automation มากขึ้น ซึ่งก็จะทำให้งานลดลงมหาศาลแล้วครับ ซึ่งการที่จะเปลี่ยนจากกลุ่มที่ 2 มาเป็นกลุ่มนี้ได้ เราจะต้องมีความรู้ความเข้าใจใน services ต่างๆที่อยู่บนคลาว์เพื่อเรียกใช้งานมันได้อย่างเหมาะสมด้วย

### 4.Cloud Native

กลุ่มสุดท้ายคือการที่เราออกแบบตัว Architecture ทุกอย่างโดยใช้คลาว์เป็นที่ตั้งเลย เช่น database จะใช้ตัวไหนบนคลาว์ Cosmos DB ไหม? ตัวทำ Microservice เป็น Service Fabric ไหม ใช้ API Management เป็นตัวจัดการเรื่อง API ให้ลูกค้าไปเลย บลาๆ พูดง่ายๆทุกอย่างที่ใช้เป็นคลาว์ทุกตัวเลย นี่ถึงจะเป็นการรีดความสามารถทุกอย่างบนคลาว์ออกมาอย่างแท้จริง

**Guideline** การเลือกว่าจะเปลี่ยน Database แบบเดิมมาเป็น Cloud Native ควรเลือกตัวไหนดี

![](../../.gitbook/assets/image%20%2838%29.png)

## 🤔 ทำไมต้องทำ Cloud Native ?

จะไม่ทำก็ได้นะตำรวจไม่จับหรอก เพียงแค่เวลาเกิดปัญหาต่างๆขึ้น เราเคยแก้ปัญหาแบบไหนก็อาจจะต้องแก้แบบเดิมและช้าแบบเดิม แต่ถ้าเราใช้ Cloud Native ปัญหาจะลดลงเยอะมากเพราะของที่อยู่บนคลาว์เราสามารถปรับ configuration นิดหน่อยมันก็จะ Automate ให้เราหลายเรื่องได้เลย ทำให้ลดค่าใช้จ่ายในตัวเงินและเวลาไปได้มากโขเลย

## 🎥 วีดีโออธิบายบทความนี้แบบละเอียด

{% embed url="https://www.youtube.com/watch?v=bkKkY82dafo&list=PLUjAn8nwWniiReiOqUqYwxG7ny2bhENMg&index=14" %}

{% hint style="success" %}
ลิงค์ของบทความนี้กดจิ้มลิงค์ข้างๆนี้โลด [Microsoft Architecture](https://docs.microsoft.com/en-us/dotnet/architecture/modernize-with-azure-containers/)
{% endhint %}


