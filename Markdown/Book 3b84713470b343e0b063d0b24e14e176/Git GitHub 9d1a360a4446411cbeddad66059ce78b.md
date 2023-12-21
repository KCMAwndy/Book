# Git/GitHub

## Introduction

**Version Control** : 

- System records all the change made to a file or set of files, so a specific version may be called later if needed
- The system makes sure that all the team members are working on the latest version of the file

**Git** : เป็น Version Control แบบ Distributed Version Control System (DVCS)

**GitHub** : (Git Repository/ Remote Repository) : คือ Web Server ที่เก็บ file ที่ upload โดย Git 

**Repository** : Database ที่เก็บ version ของ code

- ใน GitHub การสร้าง repository คือการสร้าง พื้นที่จัดเก็บ project (file code)
- การที่จะดึงข้อมูลจาก server มาไว้กับเครื่องโดยที่จะทำงานแบบ Offline โดยไม่ต้องพึ่ง Online ต้องอาศัยการ clone จาก server มาใช้งาน ซึ่งจะเรียกเครื่องที่ใช้ clone source code จากฐานข้อมูลมาไว้ที่เครื่องของตนเองว่า Local Repository
- เมื่อต้องการ upload เข้า server (GitHub) จะใช้การ Syn ด้วยวิธีการ Pull/ Merge/ Push

---

## การสร้างและลบ Repository (GitHub)

บน Web Browse

![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled.png)

---

## การเชื่อมต่อ Git กับ Email & Username

command line

การเชื่อม git กับ Email

<aside>
<img src="https://www.notion.so/icons/command-line_gray.svg" alt="https://www.notion.so/icons/command-line_gray.svg" width="40px" /> git config —global [user.email](http://user.email) “Email ของเรา”

</aside>

การเชื่อม git กับ Username 

<aside>
<img src="https://www.notion.so/icons/command-line_gray.svg" alt="https://www.notion.so/icons/command-line_gray.svg" width="40px" /> git config —global [user.](http://user.email)name “ชื่อ user ของเราบน git”

</aside>

การเเสดงการตั้งค่าทั่งหมด

<aside>
<img src="https://www.notion.so/icons/command-line_gray.svg" alt="https://www.notion.so/icons/command-line_gray.svg" width="40px" /> git config —list

</aside>

---

## วงจรการทำงานของ Git (Git WorkFlow)

![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%201.png)

Untracked : คือ file/folder ที่ยังไม่มีการตรวจสอบโดย git ว่ามีการเปลี่ยนแปลงอย่างไรบ้าง

- **git init** : เป็นการบอกว่าจะนำ file มาตรวจสอบ (tracked)
    - **Tracked Status (สถานะการติดตาม)**
        - **Modified** : มีการแก้ไขไฟล์แล้ว แต่ยังไม่เริ่มต้นจัดเก็บลงบน Repository
        - **Staged** : ได้ทำเครื่องหมาย File ที่ได้ถูกแก้ไขเพื่อบันทึกใน version หน้า
        - **Committed** : ข้อมูลถูกบันทึกลงใน Repository เรียบร้อยแล้ว

---

## Git Command เบื้องต้น

**การสร้าง Local Git Repository**

<aside>
<img src="https://www.notion.so/icons/command-line_gray.svg" alt="https://www.notion.so/icons/command-line_gray.svg" width="40px" /> git init

</aside>

การเชื่อม git กับ Email

<aside>
<img src="https://www.notion.so/icons/command-line_gray.svg" alt="https://www.notion.so/icons/command-line_gray.svg" width="40px" /> git config —global [user.email](http://user.email) “Email ของเรา”

</aside>

**การเพิ่ม file เข้าไปใน Staging Area(Check-in)**

- ระบุ file โดยตรง
    
    <aside>
    <img src="https://www.notion.so/icons/command-line_gray.svg" alt="https://www.notion.so/icons/command-line_gray.svg" width="40px" /> git add <file_name>
    
    </aside>
    
- เพิ่มหลายๆ file พร้อมกัน โดยระบุนามสกุล
    
    <aside>
    <img src="https://www.notion.so/icons/command-line_gray.svg" alt="https://www.notion.so/icons/command-line_gray.svg" width="40px" /> git add *.html
    
    </aside>
    
- เพิ่มทุก file ที่อยู่ภายใต้ Directory ปัจจุบัน
    
    <aside>
    <img src="https://www.notion.so/icons/command-line_gray.svg" alt="https://www.notion.so/icons/command-line_gray.svg" width="40px" /> git add .
    
    </aside>
    

**การลบ file หรือ folder ออกจาก Git Repository (Remove)**

- ลบทั้งหมด
    
    <aside>
    <img src="https://www.notion.so/icons/command-line_gray.svg" alt="https://www.notion.so/icons/command-line_gray.svg" width="40px" /> git rm -r —cached .
    
    </aside>
    
- ระบุ file โดยตรง
    
    <aside>
    <img src="https://www.notion.so/icons/command-line_gray.svg" alt="https://www.notion.so/icons/command-line_gray.svg" width="40px" /> git rm —cached <file_name>
    
    </aside>
    

**การตรวจสอบสถานะ (status)**

เป็นการดูสถานะการเปลี่ยนแหลงของ Repository บนเครื่องเรา (Local) เช่น การเพิ่ม, แก้ไข, ลบไฟล์ต่างๆ

<aside>
<img src="https://www.notion.so/icons/command-line_gray.svg" alt="https://www.notion.so/icons/command-line_gray.svg" width="40px" /> git status

</aside>

**ตัวอย่างการใช้งาน**

1. ใน folder ที่เราจะนำเข้าสู่ Git ให้กดคลิกขวา > เลือก Git Bash Here
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%202.png)
    
2. สร้าง file โดยใช้คำสั่ง touch / สร้างผ่าน text editor
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%203.png)
    
3. นำ Git มาตรวจสอบ file ว่ามีการเปลี่ยนแปลงกลุ่มคำสั่งตรงไหนบ้าง เริ่มจากการนำ Git มาทำงาน (สร้าง Git บนเครื่องเรา) โดยใช้คำสั่ง git init
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%204.png)
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%205.png)
    
4. ตรวจสอบการติดตาม (track) ของไฟล์ ด้วย git status ว่ามีการจัดเก็บลงบน staging area (git repository ที่เราสร้างขึ้นมา แต่ยังไม่ยืนยันแบบถาวรบน local repository เนื่องจาก staging area คือพื้นที่ที่เราจัดเตียมขึ้นมาก่อนนำไป commit ถาวร) หรือไม่ ถ้า untracked ให้เก็บประวัติการแก้ไขบน staging area โดยใช้ git add
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%206.png)
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%207.png)
    
5. ลบ file ใน staging area นั้นคือ การยกเลิกการติดตาม file (untrack)
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%208.png)
    

---

## Git Commit ,Git Log

ใช้เพื่อเก็บประวัติถาวรบน Repository 

**การเก็บประวัติการอก้ไขถาวร (Commit)**

<aside>
<img src="https://www.notion.so/icons/command-line_gray.svg" alt="https://www.notion.so/icons/command-line_gray.svg" width="40px" /> git commit -m “Log Message”

</aside>

**Option**

- **m** : เป็น parameter สำหรับใส่ข้อความช่วยจำ (Log Message) เพอื่อธิบายการ commit แต่ละ version
- เมื่อ Commit ไปแล้ว ขะได้ SHA-1 Hash เป็น Commit ID (รหัสประจำ version), (โดยที่ SHA-1 Hash = 40 ตัวอักษร แต่ตอนอ้างอิงใช้แค่ 7 ตัวอักษรแรก)

**การดูประวัติการ Commit (Log)**

เป็นการแสดง Commit ID, Message, ชื่อผู้เขียน, email, และเวลาที่ Commit

- การแสดงผลทั้งหมดทีเดียว
    
    <aside>
    <img src="https://www.notion.so/icons/command-line_gray.svg" alt="https://www.notion.so/icons/command-line_gray.svg" width="40px" /> git log
    
    </aside>
    
- การแสดงแต่ละ log ให้เหลือบรรทัดเดียว
    
    <aside>
    <img src="https://www.notion.so/icons/command-line_gray.svg" alt="https://www.notion.so/icons/command-line_gray.svg" width="40px" /> git log —oneline
    
    </aside>
    
- การแสดงเป็นเส้น Branch ให้ดูง่าย
    
    <aside>
    <img src="https://www.notion.so/icons/command-line_gray.svg" alt="https://www.notion.so/icons/command-line_gray.svg" width="40px" /> git log —graph
    
    </aside>
    

**ตัวอย่างการใช้งาน**

1. การเก็บประวัติ file version แรก บน repository โดยใช้ git commit -m “Log Message” ทำให้เมื่อดู git status จะไม่ขึ้นว่าไม่มีการเปลี่ยนแปลงของไฟล์แล้ว เนื่องจากมีการเก็บประวัตถาวร
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%209.png)
    
2. ดูประวัติการทำงานบน folder ในอดีต โดยใช้ git log 
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2010.png)
    
3. เมื่อเกิดการเปลี่ยนแปลงบน folder (แก้ไข file) ต้องการ check การแก้ไข file บน folder ใช้คำสั่ง git status โดยจะขึ้น status ว่า modified > ทำให้จะมี version ที่ 2 
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2011.png)
    
4. ทำการ update version ที่ 2 โดยการใช้ git add > git commit
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2012.png)
    
5. เมื่อ check ประวัติด้วย git log จะเห็นว่า มีทั้งหมด 2 version (version ที่ 1 ด้านล่าง, version ที่ 2 ด้านบน) โดยที่มี HEAD ชี้อยู่ว่า version นี้คือ version ปัจจุบัน (สามารถดู version ปัจจุบนโดยการใช้ **git show HEAD**)
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2013.png)
    
    - การแสดงผลแบบ oneline
        
        ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2014.png)
        
    - การแสดงผลแบบ Branch
        
        ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2015.png)
        

---

## การเปรียบเทียบ version (git diff)

ใช้สำหรับตรวจสอบแลเปรียบเทียบ file source code ว่ามีอะไรเปลี่ยนแปลง และต่างไปจากเดิมบ้างเมื่อเทียบกับ Commit (version )ที่ผ่านมา

- เปรียบเทียบโดยการระบุ Commit ID โดยตรง (เปรียบเทียบแค่ version เดียว)

<aside>
<img src="https://www.notion.so/icons/command-line_gray.svg" alt="https://www.notion.so/icons/command-line_gray.svg" width="40px" /> git diff <commit_id>

</aside>

- เปรียบเทียบระหว่าง 2 Commit

<aside>
<img src="https://www.notion.so/icons/command-line_gray.svg" alt="https://www.notion.so/icons/command-line_gray.svg" width="40px" /> git diff <commit_id> <commit_id>

</aside>

โดยที่ commit_id คือ รหัส version 7 ตัวแรก นำมาอ้างอิง

**สีสถานะ**

- **เครื่องหมาย - และตัวอักษรสีแดง** หมายถึง บรรทัดเดิมก่อนถูกแก้ไขและถูกลบ (version เดิม)
- **เครื่องหมาย + และตัวอักษรสีเขียว** หมายถึง โค้ดใหม่ที่ถูกแก้ไขและเพิ่มใหม่ (คำสั่งที่มีการแก้ไขบน version ใหม่)

**ตัวอย่างการใช้งาน**

1. แสดงการเปรียบเทียบระหว่าง 2 version ด้วย git diff <commit_id> <commit_id>
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2016.png)
    
    - เปรียบเทียบ 2 version จากที่มี 3 version
        
        ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2017.png)
        

---

## การกู้คืน version ของ file

**การยกเลิกการแก้ไข file (Check-Out)**

เป็นการย้อนกลับไปยัง Commit ล่าสุด หรือยกเลิกการแก้ไย file 

<aside>
<img src="https://www.notion.so/icons/command-line_gray.svg" alt="https://www.notion.so/icons/command-line_gray.svg" width="40px" /> git checkout <file-name>

</aside>

**ตัวอย่างการใช้งาน**

1. เมื่อลบ code ทั้งหมดบน file แล้ว กด save
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2018.png)
    
2. ต้องการกู้คืนคำสั่งกลับมา(ยกเลิกการแก้ไข) โดยใช้ git checkout <file-name>
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2019.png)
    

---

## Git Reset

**Git Reset สำหรับการย้อนคืน file ที่ไม่ต้องการจาก Staging Area**

เป็นการย้อน version ให้กลับไปอยู่ในสภาพก่อนที่จะ add file เข้าสู่ Staging Area ซึ่งบางครั้ง มีการเพิ่ม file ลงใน Staging Area โดยไม่ได้ตั้งใจ ซึ่งสามมารถเอาออกได้ โดยใช้ git reset

<aside>
<img src="https://www.notion.so/icons/command-line_gray.svg" alt="https://www.notion.so/icons/command-line_gray.svg" width="40px" /> git reset <ชื่อ file ที่จะนำออกจาก staging area>

</aside>

**ตัวอย่างการใช้งาน**

1. ทดลองโดยการ เพิ่ม 2 file ด้วย touch
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2020.png)
    
2. check track file และเพิ่ม file บน staging area ด้วย git add
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2021.png)
    
3. นำ readme.txt ออกจาก staging area โดยการใช้ git reset
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2022.png)
    
4. ในการ commit นี้ หมายถึงการเก็บ style.css ลงประวัติอย่างเดียว
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2023.png)
    

**Git Reset สำหรับการย้อนคืน version** 

![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2024.png)

<aside>
<img src="https://www.notion.so/icons/command-line_gray.svg" alt="https://www.notion.so/icons/command-line_gray.svg" width="40px" /> git reset —option <commit_id>

</aside>

**Option**

- **soft** : ใช้เพื่อลบ Commit ทั้งหมดที่อยู่หลัง Commit ID แล้วนำไฟล์ที่เคยอยู่ใน Commit นั้นหลับมายัง **Staging Area**
- **mixed** : ใช้เพื่อลบ Commit ทั้งหมดที่อยู่หลัง Commit ID แล้วนำไฟล์ที่เคยอยู่ใน Commit นั้นหลับมายัง **Working Directory**
- **hard** : ใช้เพื่อลบ Commit ทั้งหมดที่อยู่หลัง Commit ID และจะทำลาย file ที่เคยอยู่ใน Commit เหล่านั้น

**ตัวอย่างการใช้งาน**

1. check version ที่มีด้วย git log
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2025.png)
    
2. จะเห็นว่าปัจจุบันอยู่ version ที่ 4 ต้องการย้อนกลับไปใช้ version ที่ 2 โดยที่ถัดไปจาก version ที่ 2 ทิ้งไปหมดเลย (version ที่ 3 และ 4) ด้วยการใช้ git reset —**hard** <commit_id> 
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2026.png)
    
3. เพิ่มข้อมูลบน index.html 
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2027.png)
    
4. ทำการ commit เป็น version ที่ 3 
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2028.png)
    

---

## Git Branching : การแตกกิ่ง

การแตกกิ่งคือการพัฒนา project ใหม่/เพิ่ม feature เข้าไปใน project เก่า โดยที่ยังสามารถใช้งาน version ล่าสุดได้โดยไม่ต้อง ใช้ git reset ย้อนกลับ version (ใช้เมื่อ version ล่าสุดเกิด Bug แต่ยังต้องการเพิ่ม feature เข้าไป ทำได้โดยการใช้ version ก่อนหน้าแตกกิ่งก้านออกมา หลังจากที่ version ล่าสุดแก้ Bug เสร็จแล้ว สามารถนำมา Merge รวมกันได้)

![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2029.png)

- Master เป็น Branch Default (กิ่งหลัก) ตอนใช้คำสั่ง git init
- project ที่ถูกแตกกิ่งออกมาจาก Master Branch เรียกว่า Feature Branch

![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2030.png)

- โดยที่ถ้าเราอยากสลับไปทำงานที่ Feature Branch สามารถสลับกิ่งได้ด้วยการ Check Out

---

## การจัดการ Git Branch เบื้องต้น

- การแสดงชื่อ Branch

<aside>
<img src="https://www.notion.so/icons/command-line_gray.svg" alt="https://www.notion.so/icons/command-line_gray.svg" width="40px" /> git branch

</aside>

- การสลับและสร้าง Branch

<aside>
<img src="https://www.notion.so/icons/command-line_gray.svg" alt="https://www.notion.so/icons/command-line_gray.svg" width="40px" /> git checkout -b <ชื่อ_branch>

</aside>

- โดยที่ <ชื่อ_branch> ห้ามตั้งชื่อเว้นวรรค
- การลบ Branch

<aside>
<img src="https://www.notion.so/icons/command-line_gray.svg" alt="https://www.notion.so/icons/command-line_gray.svg" width="40px" /> git branch -d <ชื่อ_branch>

</aside>

- สลับไป Branch ที่ต้องการ

<aside>
<img src="https://www.notion.so/icons/command-line_gray.svg" alt="https://www.notion.so/icons/command-line_gray.svg" width="40px" /> git checkout <ชื่อ_branch>

</aside>

- สลับไป Branch หลัก

<aside>
<img src="https://www.notion.so/icons/command-line_gray.svg" alt="https://www.notion.so/icons/command-line_gray.svg" width="40px" /> git checkout master

</aside>

- การรวม Branch

<aside>
<img src="https://www.notion.so/icons/command-line_gray.svg" alt="https://www.notion.so/icons/command-line_gray.svg" width="40px" /> git merge <ชื่อ_branch>

</aside>

**ตัวอย่างการใช้งาน**

1. ทดสอบโดยการดูชื่อ branch โดยใช้คำสั่ง git branch
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2031.png)
    
    โดยที่เราจะเห็นว่า เครื่องหมาย “*” หมายถึง ตอนนี้เรากำลังทำงานอยู่ที่ branch นั้นๆ / หรือดูที่ “()” หลังชื่อ project
    
2. การสร้างและสลับไปใช้ branch ที่สร้างขึ้น โดยใช้คำสั่ง git checkout -b <ชื่อ_branch>
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2032.png)
    
3. การลบ branch โดยใช้คำสั่ง git branch -d <ชื่อ_branch>
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2033.png)
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2034.png)
    
4. เพิ่ม branch(feature) ใหม่ และแก้ไข source code ที่ branch นั้น
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2035.png)
    
5. ทำการ check status, add และ commit ของ file index.html บน branch ให้เรียบร้อย
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2036.png)
    
6. ทำการสลับไปใช้ branch master จะเห็นว่า source code ใน branch master ไม่เปลี่ยนแปลง
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2037.png)
    
7. นำ branch มารวมกัน โดยใช้ git merge <ชื่อ_branch> โดยที่ต้องอยู่ใน branch master ก่อน
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2038.png)
    

---

## Git Push (ผลัก)

คือคำสั่งที่ใช้สำหรับนำสื่งที่อยู่ในเครื่องของเรา (Local Repository) ไปอัพเดตให้กับ Remote Repository (Server) / GitHub

**โดยสามารถใช้งานได้ 2 เหตุการณ์นั้นคือ**

1. นำไฟล์เข้าสู่ GitHub ตั้งแต่แรกที่ยังไม่เคยนำเข้า
2. นำไฟล์เข้าไป update ไฟล์เดิมใน GitHub

**ทำได้โดย**

- สร้าง branch (main) หลักบน remote repository

<aside>
<img src="https://www.notion.so/icons/command-line_gray.svg" alt="https://www.notion.so/icons/command-line_gray.svg" width="40px" /> git branch -M main

</aside>

<aside>
<img src="https://www.notion.so/icons/command-line_gray.svg" alt="https://www.notion.so/icons/command-line_gray.svg" width="40px" /> git remote add origin <URL_ของ_repository_เรา>

</aside>

- เป็นการบอกว่า เราจะอัพ ตัว project ของเราขึ้นไปเก็บบน remote repository (GitHub) โดยมีที่อยู่ดังนี้

<aside>
<img src="https://www.notion.so/icons/command-line_gray.svg" alt="https://www.notion.so/icons/command-line_gray.svg" width="40px" /> git push -u origin main

</aside>

- เป็นการบอกว่าให้นำตัว project บนไปทำงาน/จัดเก็บบน branch (main) นั้นๆ

![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2039.png)

**ตัวอย่างการใช้งาน**

1. สร้าง repository ใหม่ บน GitHub
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2040.png)
    
    โดยเราจะ push แค่ file .js และ .html จึงต้องลบ file readme.txt จากนั้น git add และ commit ตามลำดับ
    
2. ทำการ Git Push ทั้ง 3 ขั้นตามลำดับ
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2041.png)
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2042.png)
    
3. จะเห็นว่ามีการ update ที่ branch หลักบน repository
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2043.png)
    

---

## Git Pull (ดึง+รวม)

คือคำสั่งที่ใช้สำหรับนำสิ่งที่อยู่ยน Remote Repository (Sever)/GitHub มาอัพเดตในเครื่องของเรา (Local Repository) ให้เป็น code ชุดเดียวกัน 

**ทำได้โดย**

<aside>
<img src="https://www.notion.so/icons/command-line_gray.svg" alt="https://www.notion.so/icons/command-line_gray.svg" width="40px" /> git pull

</aside>

**ตัวอย่างการใช้งาน**

1. ทำการแก้ไข file app.js บน GitHub และทำการ commit
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2044.png)
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2045.png)
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2046.png)
    
2. ใช้คำสั่ง git pull เพื่อดึง code จาก GitHub มา update บนเครื่องเรา
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2047.png)
    

---

## README

คือเอกสาร documentary ประกอบ กับ repository (คู่มือประกอบ project ว่า project เกี่ยวกับอะไร การทำงานเป็นอย่างไร ใช้งานอย่างไร)

**สามารถสร้างได้ 2 วิธี**

1. จากหน้า repository บน GitHub

![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2048.png)

1. บน git bash

<aside>
<img src="https://www.notion.so/icons/command-line_gray.svg" alt="https://www.notion.so/icons/command-line_gray.svg" width="40px" /> touch README.md

</aside>

**การใช้งาน**

- **#** : แสดงถึงหัวข้อ project (header)
- ระบุลายละเอียดด้วย text เฉยๆ

**ตัวอย่างการใช้งาน**

1. สร้าง file README.md บน project
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2049.png)
    
2. กำหนดหัวข้อ และลายละเอียดใน README.md และกด save
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2050.png)
    
3. ทำการ git add, commit และ push ตัว README.md
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2051.png)
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2052.png)
    
4. กลับไปดู README.md บน GitHub
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2053.png)
    

---

## Git Clone

คือคำสั่งที่ใช้สำหรับนำเอา project ใน Remote Repository (Server)/GitHub มาไว้ในเครื่องของเราหรือคนในทีม (Local Repository) โดยไม่สงผลกระทบต่อตัว project ที่ clone มา

**ทำได้โดย**

- หาตำแหน่งที่ project ที่จะ clone (URL) บน GitHub
- ระบุตำแหน่งนั้นบน folder ที่จะใส่ โดยใช้ git bash

<aside>
<img src="https://www.notion.so/icons/command-line_gray.svg" alt="https://www.notion.so/icons/command-line_gray.svg" width="40px" /> git clone <URL_project ที่จะ clone>

</aside>

**ตัวอย่างการใช้งาน**

1. หาตำแหน่งที่ project ที่จะ clone (URL) บน GitHub
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2054.png)
    
2. สร้าง folder ใหม่เพื่อจัดเก็บ และใช้คำสั่ง git clone <URL_project ที่จะ clone>
    
    ![Untitled](Git%20GitHub%209d1a360a4446411cbeddad66059ce78b/Untitled%2055.png)
    

---