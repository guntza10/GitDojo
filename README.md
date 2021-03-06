# GitDojo

## `Git`

=> เป็นเครื่องมือที่เอามาช่วยให้ dev ทำให้งานร่วมกันหลายคนได้สะดวกขึ้น

`problem`

- เวลาเราทำงานร่วมกันหลายคน แล้วเราต้องการจะแชร์ code กัน เราก็อาจจะให้คนนึงทำเสร็จแล้วส่ง zip ไฟล์มา แล้วเราก็เอามาแก้ต่อ ทำต่ออะไรแบบนี้
- เวลาที่เราทำงานที่ไฟล์เดียวกัน เราจะทำยังไง เราก็อาจจะต้องมานั่ง compare code กันว่าเอ้ยส่วนนี้เป็นของเรานะเอามา ส่วนนี้เป็นของเพื่อนก็ copy ส่วนที่เป็นของเพื่อนมาใส่ใน code เรา หลังจาก compare ปรับ code ให้เป็นล่าสุดที่มีส่วนของทั้งคู่เสร็จ เราก็อาจจะต้องมานั่ง zip ไฟล์ที่ถูก update เป็น code ตัวล่าสุดใหม่ เพื่อจะส่งไปให้เพื่อนทำต่อ
- เราทำงานไปได้แล้วซักพักปรากฏว่า code ดันพัง เราอยากจะย้อนกลับไปก่อนหน้าที่ code จะพัง เราจะทำยังไง เราอาจจะมานั่งไล่กด ctrl + z ย้อนกลับรัวๆก็ได้ แต่มันก็ไม่ควรทำถูกป่ะ เพราะมันต้องมานั่งไล่ย้อน code เรื่อยก็ปวดหัว ยุ่งยากซับซ้อน

## `การใช้งาน Git เบื้องต้น`

1. เริ่มต้นเราจะต้องสร้าง git repository (git repo) หรือก็คือเป็นที่เก็บงาน เก็บ project ที่เราจะทำร่วมกันนั่นเอง
2. เมื่อเรามี git repo แล้วเราต้องนำ git repo นั้นเอามาทำงานที่เครื่องด้วยคำสั่ง git clone
3. เมื่อเราทำงานของเราเรียบร้อย งานที่เราทำมันอยู่บนเครื่อง เราอยากจะ push งานขึ้นไปบน git เพื่อให้ git repo เรามัน update งานที่เราทำ มีขั้นตอนดังนี้
   - commit code ที่เราทำ (เป็นการ save state การเปลี่ยนแปลงที่เราทำ) git add . (เป็นการเลือกว่าเราจะเอาไฟล์ไหนที่มีการเปลี่ยนแปลงเข้าไปใน state บ้าง) git commit -m "message" (เป็น save state การเปลี่ยนแปลงของเรา)
   - หลังจากที่เรา save state เสร็จด้วยการ commit แล้วเราอยากจะการเปลี่ยนแปลงที่เราทำนี้อะ ขึ้นไป update บน git repo เราก็ใช้คำสั่ง push

## `การทำงานหลายคนร่วมกับ Git`

Note : ก่อนจะทำงานทุกครั้ง หรือ commit code เราควร git pull code ลงมาที่เครื่องเราก่อนเสมอเพื่อเป็นการ update code ตัวล่าสุดบน git repo มาที่เครื่อง

Note : การทำงานร่วมกันหลายคนแล้วเป็นการทำงานที่ไฟล์เดียวกัน แก้ไขที่ไฟล์เดียวกัน มันจะเกิด conflict เราต้องแก้ conflic ก่อน จากนั้น commit state ที่เราแก้ conflict ก่อนจะ push

## Git Branch

=> เป็นความสามารถหนึ่งของ Git ที่เอาช่วยจัดการการทำงานของ Project ให้จัดการง่ายขึ้น + best practice ที่เราควรทำเพื่อให้ทำงานร่วมกับคนอื่นได้สะดวกขึ้น

1. โดยปกติทุกครั้งที่เราสร้าง git repo ขึ้นมา branch เริ่มต้นเราจะเป็น master(main)
2. เวลาที่เราจะ develop(dev) front-end,back-end ซักอย่างตัวขึ้นมามันจะมี feature มากมายเลยถูกป่ะ ที่เราจะต้อง dev ใน 1 project สมมตินะ เราจะ dev ระบบการจัดเก็บข้อมูลนักเรียก feature ที่เราต้องมีคร่าวๆคืออะไรบ้าง ยกตัวอย่าง

- feature การเก็บข้อมูลนักเรียน
- feature การแสดงผลข้อมูลนักเรียน
- feature การคำนวณคะแนน คำนวณเกรดอะไรพวกนี้

สมมติว่ามีทั้งหมด 3 feature ที่เราจะต้อง dev

สิ่งแรกที่เราต้องทำและต้องรู้ก่อนเลยก็คือโดยปกติเราจะไม่ทำงานที่ branch master(main) เราจะแตกย่อย branch ออกไปทำเป็น featureๆ เมื่อเรา dev เสร็จ test เรียบร้อยแล้วว่า feature ที่เราทำมันเสร็จไม่มีปัญหา เราถึงจะเอา branch ของ feature นั้นๆอะ มา Merge(รวมเข้ากับ main)

มายกตัวอย่างวิธีการทำ

1. เราเลือกที่จะทำ feature การเก็บข้อมูลนักเรียน ก่อน
2. เราก็ทำการแตก branch จาก main ออกมาเป็น branch ของ feature การเก็บข้อมูลนักเรียก เราต้องตั้งชื่อ branch ก่อน สมมติชื่อ branch ว่า feature-keep-student-data
   git checkout -b "feature-keep-student-data"
3. พอเราแตก branch ไปที่ feature-keep-student-data เสร็จปุ๊ป เราก็ไม่ได้ทำงานที่ branch นี้นะ เราต้องแตกจาก branch feature-keep-student-data ออกไปเป็น branch ของตัวเองที่จะเอาไว้ทำงานอีกทีนึงเพื่ออะไรใช่มั้ย เพื่อป้องกันการ conflict กันที่ branch feature-keep-student-data ที่เป็น branch หลักในการทำงาน
4. เพราะโดยปกติแล้วถ้าเราทำงานที่ตัว branch หลัก ก่อนจะ commit push code เราต้อง pull code ลงมาก่อนถูกป่ะเพื่อ update code ตัวล่าสุดลงมาที่เครื่องตอนที่ pull ถ้า code ที่เราแก้มันเป็นไฟล์เดียวกันมันจะเกิด conflict แน่นอนเราต้องแก้ conflict ก่อน แล้วก็เพื่อหลีกเลี่ยง conflict ที่จะเกิดที่ branch หลักที่เราทำงาน การแยก branch ออกมาทำอีกทีจะเป็นเป็นการมาแก้ conflict ที่ branch ที่เราทำงานแทน ถ้าแก้ได้ค่อย merge กลับเข้าไปที่ branch หลักที่เราทำงาน เพราะถ้าเกิดเกิด conflict แล้วเราแก้ conflict แล้วมัน error หรือแก้ conflict ไม่ได้ branch หลักที่เราทำงานมันก็จะไม่มีผลกระทบถูกมะ มันก็จะกระทบแค่ branch ที่เราแตกออกมาทำงาน

# Git Command

## Basic

1. git add . => การ keep track file ที่มีการเปลี่ยนแปลงทั้งหมดเข้า commit
2. git commit -m "message for commit" => save state การเปลี่ยนแปลง ของ git repo
3. git push => push state การเปลี่ยนแปลงขึ้นมาบน git repo
4. git pull => pull state การเปลี่ยนแปลงลงมาที่เครื่อง

## Git Branch

1. git checkout -b "ชื่อ branch" => เป็น switch branch พร้อมทั้งสร้าง branch ให้ใหม่
2. git checkout "ชื่อ branch" => เป็นการ switch branch
3. git merge "ชื่อ branch" => merge branch
