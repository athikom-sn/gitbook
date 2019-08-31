# 15.Value type vs Reference type

💬 ในรอบนี้เราจะมาทำความรู้จักกับชนิดของข้อมูลของเราให้ลึกซึ้งยิ่งๆขึ้นไปอีกขั้นนะฮ๊าฟ ซึ่งเวลาที่เรากำหนดชนิดของข้อมูล int, double, string, bool อะไรพวกนี้ จริงๆในเบื้องลึกเขาแบ่งกลุ่มของพวกนี้ไว้ทั้ง 2 แบบนะครับนั่นคือ **Value type** กับ **Reference type** ส่วนมันคืออะไรและต่างกันยังไง ลองกดดูวีดีโอกันเบย

{% embed url="https://www.youtube.com/watch?v=ug2Sve3B03o&list=PLUjAn8nwWnijERZ3HpzBk7NfSrau74\_lQ&index=30" %}

## 🎯 สรุปสั้นๆ

### 👨‍🚀 Value type

ชนิดข้อมูลพื้นฐานที่เรานิยมใช้กันเช่น int, double, bool อะไรพวกนี้อยู่ในกลุ่มของ value type นะครับ ซึ่งลักษณะเฉพาะตัวของกลุ่มนี้คือ ตัวแปรแต่ละตัวเวลามันเก็บข้อมูลมันจะเก็บแยกของใครของมัน แยกขาดจากกันเลย ไม่เกี่ยวข้องกันเลย

### 👨‍🚀 Reference type

ชนิดข้อมูลส่วนใหญ่ที่อยู่ในกลุ่มนี้จะเป็นพวก class ต่างๆและรวมถึง string ด้วย ซึ่งลักษณะเฉพาะตัวของกลุ่มนี้คือ ตัวแปรแต่ละตัวมันจะไม่เก็บข้อมูลไว้ แต่มันใช้การชี้ไปยังข้อมูลแทน ซึ่งตัวแปรต่างกันก็สามารถชี้ไปที่ข้อมูลตัวเดียวกันได้ ดังนั้นเวลาเวลามีการแก้ไขข้อมูลมันก็จะทำให้ตัวแปรที่ชี้มาหาข้อมูลเดียวกันมีผลกระทบไปด้วย

{% hint style="info" %}
**Immutable of string**  
หลายคนพอได้ยินว่า string นั้นอยู่ในกลุ่มของ Reference type ก็เลยไปลองเล่นดู แต่พอลองดูจะพบว่าพฤติกรรมของมันจะเหมือนกับ value type มากกว่า เพราะเวลาให้ตัวแปรอื่นไปแก้ไขข้อมูลจะพบว่าอีกตัวแปรนึงไม่เปลี่ยนตาม นั่นก็เพราะ ตอนที่เราไปแก้ไขข้อมูลของ string จริงๆนั้นเราทำไม่ได้ เพราะ string มีลักษณะเฉพาะตัวอีกข้อคือสิ่งที่เรียกว่า **Immutable** ซึ่งความหมายของ immutable ผมขอยกไปอยู่ในบทของ string อีกทีละกันครับ
{% endhint %}
