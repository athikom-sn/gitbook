---
description: "\U0001F433 Docker ตอนที่ 2 กับสิ่งที่เรียกว่า คอนเทนเนอร์"
---

# 📦 Docker Containers

🤠 จาก [**บทความที่ 1**](https://www.saladpuk.com/basic/docker-1) เราน่าจะรู้แล้วว่าเจ้าวาฬสีน้ำเงิน 🐳 **Docker** มันช่วยให้ขาเดฟทำงานสะดวกขึ้นได้ยังไง ดังนั้นบทความนี้เรามาลองซูมดูเบื้องหลังการทำงานที่ว่านั้นกันดีก่าาา

## 🚨 เท้าความเดิม

จาก [**บทความที่ 1**](https://www.saladpuk.com/basic/docker-1) เราอยากได้ Environments แบบไหน \(เช่น ลง .NET 4.8, PHP 8.0 Angular 9.0 เอาไว้\) เราก็จะสร้างสิ่งที่เรียกว่า 🖼️ **Docker Image** ขึ้นมา แล้วเครื่องคอมพิวเตอร์เครื่องไหนก็ตามที่เอา Docker Image นั้นไปใช้ มันก็จะถูกจัด Environments ตามที่ Docker Image นั้นระบุไว้ ตามรูปด้านล่างเบย

![](../../.gitbook/assets/image%20%281125%29.png)

แต่เราเคยสงสัยกันป่ะว่าเจ้า 🐳 **Docker** มันทำให้ Environments ของคอมพวกนั้นเหมือนกันได้ยังไง? 🤔 ... ดังนั้นเรามาดูหัวใจของมันที่ชื่อว่า **Docker Engine** กันดีก่า

## 💝 Docker Engine

**`Docker Engine`** คือตัวทำงานอยู่เบื้องหลังของ Docker โดยมันสามารถทำงานได้หลากหลาย **OS** _\(CentOS, Debian, Fedora, Oracle Linux, RHEL, SUSE, Ubuntu, Windows Server\)_ หรือพูดง่ายๆคือ **Windows** กับ **Linux** นั่นเอง ซึ่งต้นตระกูลของ **macOS** มันก็คือ Linux ดังนั้น Docker Engine ก็เลยทำได้ด้วยได้ และเมื่อรองรับทุกระบบปฎิบัติการหลักอยู่แล้วเลยทำให้ตัวมันเองก็สามารถไปทำงานบน **Cloud Providers** ได้ด้วยนั่นเอง

![](../../.gitbook/assets/image%20%281128%29.png)

โดยเจ้า Docker Engine มีหน้าที่ **`สร้างระบบจำลอง`** ให้มี Environments ตามที่ Docker Image ระบุไว้นั่นเอง

😳 หลายคนพออ่านถึงจุดนี้ก็อาจเอะใจคำว่า **ระบบจำลอง** ที่เจ้า Docker สร้างละว่ามันคือ **Virtual Machine** หรือ **VM** ที่เราชอบใช้กันหรือเปล่า? ดังนั้นเราจะลองซูมดูรายละเอียดกันอีกนิสสสนุง

## 🔥 Virtual Machine

รู้กันป่ะว่าคอมพิวเตอร์ที่เราใช้ๆกันอยู่นั้น เราสามารถสร้างคอมพิวเตอร์จำลองให้มันทำงานอยู่ภายในเครื่องคอมเราอีกทีได้ด้วยนะ ตามรูปด้านล่าง

![](../../.gitbook/assets/image%20%281120%29.png)

ซึ่งการที่เราทำแบบนี้ได้ เราจะต้องใช้ **Hypervisor \(**อีกชื่อคือ **Hyper-V**\) เข้ามาช่วยสร้างเครื่องคอมจำลองขึ้นมา และเนื่องจากมันเป็นการจำลองเครื่องคอม ดังนั้นมันก็จะต้องมีการลง OS ให้กับเครื่องจำลองพวกนั้นด้วย \(OS ที่เราลงให้คอมจำลองพวกนั้นเราเรียกมันว่า **Guest OS**\) ตามรูปด้านล่าง

![](../../.gitbook/assets/image%20%281127%29.png)

{% hint style="success" %}
**Virtual Machine**  
👍ข้อดีของการทำ Virtual Machine แบบนี้คือ **มันเป็นเครื่องจำลองแบบเหมือนเครื่องคอมจริงๆ** เราต้องลง Windows ให้มันจริงๆ จะเปิดก็ต้องรอมันบูต จะปิดก็ต้องรอมัน shutdown จริงๆ และการแบ่ง RAM แบ่ง Storage ให้มันเท่าไหร่ มันก็จะใช้ได้เท่านั้นจริงๆ   
👎ส่วนข้อเสียคือ **มันเปลืองทรัพยากรของเครื่องที่ใช้สร้าง VM มาก** เพราะเราต้องสละ RAM สละ CPU สละ Storage ส่วนหนึ่งไปให้มันจริงๆ เพราะตัวมันก็ถูกดูแลเสมือนเป็นคอมพิวเตอร์จริงๆอีกเครื่องเลย
{% endhint %}

แต่ในทางกลับกันบริษัทที่ทำ Docker กลับมองว่าเราไม่ต้องทำแบบนั้นก็ได้นิ และเสนอแนวคิดที่เรียกว่า **`Container`** มาจัดการสร้างระบบจำลองขึ้นมา

## 🔥 Docker Container

บริษัทที่สร้าง Docker นั้นมองว่า ถ้าเราสามารถควบคุม Environment ของระบบจำลองนั้นๆได้ การสร้าง Guest OS ก็ไม่จำเป็นต้องทำอีกต่อไป ... ดังนั้น **Docker เลยสร้าง📦 กล่องขึ้นมา เราเรียกมันว่า `📦 Container` แล้วยัดของที่เราอยากจะควบคุมให้อยู่แค่ภายในกล่องใบนั้น** ตามรูปด้านล่าง

![](../../.gitbook/assets/image%20%281124%29.png)

{% hint style="success" %}
**Docker Container**  
👍ข้อดีของการทำ Docker Container คือ **มันไม่หนักเครื่อง** และ **เร็วม๊ากกกกก** เพราะไม่ต้องไปสร้าง Guest OS โดยเครื่องนั้นใช้ OS อะไรก็ใช้ไป ตัว Docker แค่ไปสร้าง Container ให้มี Environments ตามแบบที่เราอยากได้ก็จบ ส่วนพวก RAM, CPU, Storage อะไรพวกนั้นก็แชร์ๆกันไปเลยไม่ต้องไปกันอะไรเยอะ \(Config ได้\)   
👎ส่วนข้อเสียคือ **มันเป็นแค่การจำลอง environment เท่านั้น** ทำให้เราไม่สามารถทำงานมันได้เหมือนเป็น VM จริงๆในบางเรื่อง และ ก็เคยเกิดเหตุการณ์ที่ Java สามารถมองเห็นและเข้าถึงตัว OS หลักได้จากภายใน Container \(bug นี้โดนแก้แล้ว\) จะเกิดอะไรขึ้นถ้าสิ่งที่หลุดออกมาสามารถโจมตี OS หลักได้?
{% endhint %}

## ⚔️ VM vs Container

ตัว VM กับ Container เป็นแนวคิดในการสร้าง Environment จำลองเหมือนกัน ซึ่งแต่ตัวก็มีข้อดีข้อเสียที่ไม่เหมือนกัน แต่สำหรับการพัฒนาซอฟต์แวร์นั้น **สิ่งที่เราต้องการจริงๆคือ Environment เท่านั้น** เราไม่ค่อยได้ไปยุ่งกับพวก OS หรือ Hardware มากนัก ดังนั้นเจ้า **`📦 Docker Container` เลยเหมาะสมกับการสร้างซอฟต์แวร์มากกว่า** อีกทั้งมันไม่หนักเครื่องเลยทำให้ เวลาจะสร้าง เวลาจะลบก็เร็ว ดุจสายฟ้า แถมยังทำงานในลักษณะ [**Infrastructure as code**](https://www.saladpuk.com/basic/devops#infrastructure-as-code-iac) หรือ [**IaC** ](https://www.saladpuk.com/basic/devops#infrastructure-as-code-iac)ซึ่งเป็นที่นิยมในการทำ [**DevOps** ](https://www.saladpuk.com/basic/devops)อีกด้วย เลยไม่น่าแปลกเลยที่เจ้าวาฬน้ำเงิน 🐳 **Docker** จะเป็นที่ถูกใจของขาเดฟทั่วโลก

![](../../.gitbook/assets/image%20%281126%29.png)

## 🐳 Container Image

เมื่อเราเข้าใจละว่า Docker มันสร้าง Environments ให้กับเครื่องคอมพิวเตอร์ต่างๆ โดยการสร้าง Container ขึ้นมา ดังนั้นเพื่อที่จะเข้าใจให้ถูก เลยต้องย้อนกลับไปว่า **สิ่งที่ทีมสร้างมันคือ Image ของ Container นั่นเอง** ซึ่งเราเรียกมันว่า **`Container Image`** ตามรูปด้าน

![](../../.gitbook/assets/image%20%281122%29.png)

และเมื่อเราเอา **Container Image** มาทำงานที่คอมพิวเตอร์เครื่องไหนก็ตาม มันก็จะถูก Docker Engine เอาไปสร้างเป็น **`📦 Container`** โดยภายใน container ก็จะมี Environments ตรงตามที่ Container Image ระบุไว้ ตามรูปด้านล่างเบย

![](../../.gitbook/assets/image%20%281123%29.png)

และถ้าเราเอา Container Image หลายๆอันมาใช้ภายในคอมพิวเตอร์เครื่องเดียวกัน เจ้า Docker Engine ก็จะทำการสร้าง Container ตามที่ถูกกำหนดไว้ใน Container Image แต่ละตัวนั่นเอง ตามรูปด้านล่าง

![](../../.gitbook/assets/image%20%281121%29.png)

🤠 เอาละ **ดช.แมวน้ำ** คิดว่าอธิบายทฤษฎีมาเยอะพอสมควรละ และหลายๆคนก็น่าจะเริ่มคันมืออยากลองเล่น Docker กันละ ดังนั้นในบทความถัดไปเราจะมาลองติดตั้งและใช้งาน Docker ตามทฤษฎีทั้งหมดที่ว่ามากันดีกว่า

{% hint style="success" %}
อ่านแล้วชอบป๋มก็ขอฝากแชร์ หรือกดติดตามเพื่อจะได้ไม่พลาดบทความอื่นๆจาก **ดช.แมวน้ำ** ได้จากลิงค์นี้เบยครัช [**Saladpuk Fanclub**](https://www.facebook.com/mr.saladpuk/?modal=admin_todo_tour) **😍**
{% endhint %}

![&#xE0A;&#xE48;&#xE2D;&#xE07;&#xE17;&#xE32;&#xE07;&#xE2A;&#xE19;&#xE31;&#xE1A;&#xE2A;&#xE19;&#xE38;&#xE19;&#xE04;&#xE48;&#xE32;&#xE2D;&#xE32;&#xE2B;&#xE32;&#xE23;&#xE41;&#xE21;&#xE27;&#xE19;&#xE49;&#xE33;&#xE01;&#xE31;&#xE4A;&#xE1F; &#x1F618;](../../.gitbook/assets/promptpay.png)
