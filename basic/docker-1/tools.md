---
description: "อยากใช้เจ้าวาฬน้ำเงินแต่ขี้เกียจจำคำสั่งทำไงดี \U0001F914"
---

# 🛠️ Docker Tools

🤠 จาก [**บทความที่ 3**](https://www.saladpuk.com/basic/docker-1/exercise01) เราได้ลองใช้เจ้าวาฬน้ำเงิน 🐳 ครั้งแรกแล้วก็จะพบว่า **มีแต่ Command Line เต็มจอไปหมด** ซึ่งบางคนก็ขี้เกียจที่จะไปนั่งจำคำสั่งพวกนั้นทั้งหมด ดังนั้นในบทความนี้**เรามาลองเล่น Docker แบบไม่ใช้ CLI กันดีก่าาาา**

{% hint style="success" %}
**แนะนำให้อ่าน**  
บทความนี้เป็นส่วนหนึ่งของคอร์ส [🐳 **Docker**](https://www.saladpuk.com/basic/docker-1) ที่จะสอนตั้งแต่เรื่องพื้นฐานยันระดับ master กันไปเลย ซึ่งเนื้อหาทั้งหมดจะทำให้เพื่อนๆเข้าใจและใช้งาน **Docker** โดยใช้ **Kubernetes** เป็น และสามารถสร้าง **Cluster** เพื่อนำไปใช้งานบน **Cloud Providers** ต่างๆได้ และทั้งหมดที่พูดมานั้นอ่านได้ฟรีเลย ดังนั้นหากสนใจก็สามารถกดเจ้าวาฬสีน้ำเงินเพื่อไปอ่านตั้งแต่เริ่มต้นได้ครัช 🤠
{% endhint %}

## 🐳 Docker Desktop

### 🔥 Dashboard

ตอนที่เราติดตั้ง Docker นั้นเราจะได้โปรแกรม **`🐳 Docker Desktop`** มาด้วย ซึ่งเราสามารถใช้งานมันได้ง่ายๆโดยการดับเบิลคลิกตัว Icon พี่วาฬที่อยู่มุมจอของเรา หรือจะคลิกขวาเพื่อเปิด **Dashboard** ก็ได้เช่นกัลลล์

![](../../.gitbook/assets/image%20%281162%29.png)

ตัว 🐳 **Docker Desktop** เมื่อถูกเปิดขึ้นมา เราจะเห็นแถบอยู่ 2 อันคือ **`📦 Containers`** กับ **`🖼️ Images`** ตามรูปด้านล่าง \(เครื่องป๋มใช้ Dark theme มันเลยเป็นสีดำ\)

![&#x1F4E6; Containers](../../.gitbook/assets/image%20%281164%29.png)

![&#x1F5BC;&#xFE0F; Images](../../.gitbook/assets/image%20%281161%29.png)

### 🔥 Run an image

ในบทความนี้เครื่องผมไม่มี Containers หรือ Images อยู่เลย ดังนั้นทั้ง 2 แถบเลยว่างโล่งโจ้ง ดังนั้นเราก็จะลองเอา Image ตัวฝึกหัดมาลองใช้งานอีกครั้ง โดยการใช้คำสั่งด้านล่างใน `Command Prompt` \(ไหนบอกไม่ใช้ CLI 🤪\)

```bash
docker pull docker/getting-started
```

เมื่อเสร็จแล้วลองมาดูที่แถบ **`🖼️ Images`** ใหม่อีกครั้งก็จะเห็น Image ที่เราพึ่งดาวโหลดลงมา ตามรูปด้านล่าง

![](../../.gitbook/assets/image%20%281157%29.png)

คราวนี้ถ้าเราอยากเอา **`🖼️ Container Image`** ตัวนั้นไปสร้างเป็น **`📦 Container`** เราก็แค่เลื่อนเมาส์ไปที่ image ตัวนั้นๆ แล้วเลือกคำสั่ง **`RUN`** ตามรูปด้านล่าง

![](../../.gitbook/assets/image%20%281154%29.png)

หากเราต้องการ **Map PORT** หรือทำ **Volume** ก็ให้กดที่ **`Optional Settings`** ได้เบย \(Volume จะมีสอนในบทความถัดๆไป\)

![](../../.gitbook/assets/image%20%281163%29.png)

ที่รายการ setting ป๋มต้องการแค่จะ Map PORT 80 เหมือนใน [**บทความที่ 3**](https://www.saladpuk.com/basic/docker-1/exercise01) เท่านั้น ดังนั้นก็ใส่ค่าตามรูปด้านล่างแล้วกด **`RUN`**โลด

![](../../.gitbook/assets/image%20%281153%29.png)

เพียงแค่นี้เจ้า **`🐳 Docker`** ก็จะไปสร้าง Container ตัวใหม่ให้เรา แถมยังพาเรามาที่แถบ **`📦 Containers`** อีกด้วย ซึ่งเราก็จะเห็นตัว Container ตัวนั้นพร้อมสถานะของมันตามรูปด้านล่าง 

![](../../.gitbook/assets/image%20%281156%29.png)

### 🔥 Containers

รายการ **`📦 Containers`** เราสามารถเลือกตัวที่เราสนใจเพื่อทำรายการต่างๆกับมันได้ เช่น อยากเข้าไปดูเว็บตัวนั้น ก็สามารถกดที่ปุ่ม **`Open in browser`** เขาก็จะเปิดตัวเว็บที่ container ตัวนั้นๆทำงานอยู่ขั้นมาให้เรา ตามรูป

![](../../.gitbook/assets/image%20%281159%29.png)

![](../../.gitbook/assets/image%20%281133%29.png)

ส่วนคำสั่งอื่นๆก็น่าจะตรงตัว ดังนั้นเพื่อนๆลองเล่นได้เต็มที่เลย \(ถ้า container พังก็กดลบทิ้งแล้วสร้างใหม่ 🤣\)

![](../../.gitbook/assets/image%20%281190%29.png)

{% hint style="info" %}
คำสั่ง **CLI** จะเป็นการเข้าไปข้างใน Container แล้วทำงานกับมันด้วย CLI \(เหมือน remote เข้าเครื่อง ซึ่งเดี๋ยวจะอธิบายอีกทีในบทความถัดๆไป\)
{% endhint %}

### 🔥 Images

กลับมาที่แถบ **`🖼️ Images`** เมื่อเลื่อนเมาส์ไปใกล้ๆเราก็จะเห็นปุ่ม `...` แล้วเมื่อคลิกมันก็จะแสดงรายการคำสั่งขึ้นมาให้ใช้ ดังนั้นถ้าเราอยากจะจัดการอะไรกับมันก็มาที่ตรงนี้แหละ ส่วนคำสั่งแต่ละตัวเดี๋ยวไปดูรายละเอียดในบทความถัดๆไปละกันนะ แต่ที่แน่ๆตอนนี้เรารู้จักคำสั่ง Remove แน่นอน 🤣

![](../../.gitbook/assets/image%20%281165%29.png)

## 🛠️ Visual Studio Code

ตัวโปรแกรม [**VS Code**](https://code.visualstudio.com/) ที่ช่วยให้ขาเดฟเขียนงานกันก็มี Extensions ช่วยให้เราทำงานกับ **`🐳 Docker`** ด้วยนะ ส่วนใครที่ยังไม่รู้จักหรือยังไม่ได้ลงก็สามารถกดดาวโหลดได้จากลิงค์นี้เลยครัช [https://code.visualstudio.com](https://code.visualstudio.com/)

![](../../.gitbook/assets/image%20%281151%29.png)

เมื่อเปิดโปรแกรมขึ้นมาแล้วเลือก `Extension` ที่อยู่ด้านซ้ายมือ แล้วทำการค้นหาด้วยคำว่า `docker` ซึ่งน่าจะได้ผลลัพท์มาเป็นตัวแรก \(ที่มันติดดาว\) ให้คลิกมันไป 1 จึ๊ก แล้วจะเห็นปุ่ม Install ก็กดติดตั้งไปอย่ารอช้า

![](../../.gitbook/assets/image%20%281158%29.png)

หลังจากติดตั้งเสร็จเราก็จะเห็น Icon ปลาวาฬโผล่มาที่ด้านซ้ายมือ ให้ลองจิ้มอย่างแผ่วเบาไป 1 จึ๊ก แล้วเราก็จะเห็นรายการ  **`📦 Containers`** กับ **`🖼️ Images`** ที่เรามีอยู่ในเครื่อง ตามรูปด้านล่าง

![](../../.gitbook/assets/image%20%281167%29.png)

### 🔥 Run an image

ในบทความนี้เครื่องผมไม่มี Containers หรือ Images อยู่เลย ดังนั้นทั้ง 2 แถบเลยว่างโล่งโจ้ง ดังนั้นเราก็จะลองเอา Image ตัวฝึกหัดมาลองใช้งานอีกครั้ง โดยการใช้คำสั่งด้านล่างใน `Command Prompt` \(ไหนบอกไม่ใช้ CLI 🤪\)

```bash
docker pull docker/getting-started
```

เมื่อเสร็จแล้วลองมาดูที่แถบ **`🖼️ Images`** ใหม่อีกครั้งก็จะเห็น Image ที่เราพึ่งดาวโหลดลงมา ตามรูปด้านล่าง

![](../../.gitbook/assets/image%20%281160%29.png)

คราวนี้ถ้าเราอยากเอา **`🖼️ Container Image`** ตัวนั้นไปสร้างเป็น **`📦 Container`** เราก็แค่คลิกขวาแล้วเลือก `RUN` เท่านั้นเอง ซึ่งพอรอสักครู่เราก็จะเห็น Container ของเราโผล่มาละ ตามรูปด้านล่าง

![](../../.gitbook/assets/image%20%281166%29.png)

### 🔥 Containers

รายการ **`📦 Containers`** เราสามารถเลือกตัวที่เราสนใจเพื่อทำรายการต่างๆกับมันได้ เช่น อยาเข้าไปดูเว็บตัวนั้น ก็ให้คลิกขวาแล้วเลือกคำสั่ง **`Open in Browser`** เขาก็จะเปิดตัวเว็บที่ container ตัวนั้นๆทำงานอยู่ขั้นมาให้เรา ตามรูป

![](../../.gitbook/assets/image%20%281152%29.png)

![](../../.gitbook/assets/image%20%281133%29.png)

## 🎯 Summary

จากทั้งหมดที่พาเล่นไปก็น่าจะเห็นแล้วนะว่าการเล่นกับพี่วาฬ **`🐳 Docker`** นั้นไม่ยากอย่างที่คิดเลยชิมิ แถมจริงๆเครื่องมือที่จะช่วยให้เราทำงานกับพี่วาฬก็ไม่ได้มีแค่นี้นะลองไปหาดูก็จะพบอีกเพียบเบย

{% hint style="warning" %}
**คำเตือน**  
เครื่องมือมันช่วยให้เราทำงานได้โดยไม่ต้องไปนั่งจำ Commands ก็จริง แต่ถ้าเราจะใช้ Docker จริงๆจังๆที่เป็น Production grade แล้วล่ะก็ **สิ่งที่ดีที่สุดคือการใช้ Command Line ต่างหาก** เพราะตัว Commands จริงๆมันมี options & parameters ให้เยอะยั๊วเยี๊ยเต็มไปหมด จนตัว Tools ไม่สามารถเอามาแสดงได้หมดด้วยซ้ำ ไม่เชื่อลองใช้คำสั่ง **`docker --help`** ดูจิ แล้วลองใช้ **`--help`** กับคำสั่งแต่ละคำสั่งลงไปอีก ก็จะเจอ options ขึ้นมาเต็มไปหมดเบย 🤣
{% endhint %}

หลังจากที่ได้เห็นตัวอย่างการใช้งาน Docker ขั้นพื้นฐานละ เดี๋ยวในบทความถัดไปเราจะลงรายละเอียดเรื่อง **`🗃️ Docker Registry`** กันต่อ เพื่อเตรียมตัวสร้าง **`🖼️ Container Image`** เป็นของตัวเอง จะได้เอาไว้ใช้พัฒนาต่อกับคนในทีมนั่นเองกั๊ฟ

{% page-ref page="registry.md" %}

{% hint style="success" %}
อ่านแล้วชอบป๋มก็ขอฝากแชร์ หรือกดติดตามเพื่อจะได้ไม่พลาดบทความอื่นๆจาก **ดช.แมวน้ำ** ได้จากลิงค์นี้เบยครัช [**Saladpuk Fanclub**](https://www.facebook.com/mr.saladpuk/?modal=admin_todo_tour) **😍**
{% endhint %}

![&#xE0A;&#xE48;&#xE2D;&#xE07;&#xE17;&#xE32;&#xE07;&#xE2A;&#xE19;&#xE31;&#xE1A;&#xE2A;&#xE19;&#xE38;&#xE19;&#xE04;&#xE48;&#xE32;&#xE2D;&#xE32;&#xE2B;&#xE32;&#xE23;&#xE41;&#xE21;&#xE27;&#xE19;&#xE49;&#xE33;&#xE01;&#xE31;&#xE4A;&#xE1F; &#x1F618;](../../.gitbook/assets/promptpay.png)

