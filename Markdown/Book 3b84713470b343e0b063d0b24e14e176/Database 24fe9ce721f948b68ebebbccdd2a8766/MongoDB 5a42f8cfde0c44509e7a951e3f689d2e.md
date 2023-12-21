# MongoDB

เป็นฐานข้อมูลเชิงเอกสาร (Document Store) สำหรับเก็บข้อมูลขนาดใหญ่ที่มีความยืดหยุ่นสูง ง่ายต่อการปรับขนาดและทำงานข้าม Platform ได้ การจัดเก็บข้อมูลไม่ได้อยู่ในรูปแบบตาราง แต่จะอยู่ในรูปแบบเอกสาร JSON แล้วเซฟเก็บไว้ในเอกสารรูปแบบไบนารี BSON (เพื่อให้ทำงานได้ไวมากกว่าเดิม)

JSON มีโครงสร้างการจัดเก็บข้อมูลอยู่ 3 ส่วนได้แก่

1. **Database** (ฐานข้อมูล) : เป็ยส่วนที่ใช้เก็บ collection หรือชุดข้อมูล
2. **Collection** (ชุดข้อมูล) : เทียบได้กับตารางในฐานข้อมูลเชิงสัมพันธ์
3. **Documents** (เอกสาร) : ที่จัดเก็บข้อมูลของคู่คี่ย์(Key) และค่า(Value)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%201.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%202.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%203.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%204.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%205.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%206.png)

**JSON & BSON**

JSON(JavaScript Object Notation) เป็นรูปแบบการเเลกเปลี่ยนหรือรับส่งข้อมูลในระบบคอมพิวเตอร์หรือแอพลิเคชั่น ในอดีตมีการแลกเปลี่ยนหรือรับส่งข้อมูลโดยใช้รูปแบบ xml แต่เนื่องจาก xml มีโครงสร้างข้อมูลที่มีความซับซ้อน และมีขนาดใหญ่จึงมีการเปลี่ยนมาใช้รูปแบบ JSON แทน เนื่องจากมีขนาดเบาและมีโครงสร้างข้อมูลที่มนุษย์สามารถอ่านและเขียนได้ง่าย โดยรูปแบบของ JSON จะอยู่ในรูปแบบข้อความธรรมดา

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%207.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%208.png)

**JSON รองรับการทำงานชนิดข้อมูลพื้นฐานทั้งหมด ได้แก่**

- **Number :** ตัวเลข
- **String :** สตริงหรือชุดข้อความโดยใช้เครื่องหมาย double-quote(”)
- **Boolean :** ค่าบูลีน (True or False)
- **Null :** ค่าว่าง
- **Array :** อาร์เรย์หรือชุดข้อมูลซึ่งจะเป็นชนิดข้อมูลใดก็ได้ใช้สัญลักษญ์ [] เป็นตัวแสดงและคั่นสมาชิกในอาร์เลย์แต่ละค่าด้วยคอมม่า (,) เช่น [var1,var2]
- **Object :** ชุดข้อมูลที่เป็นคู่ Key-Value แบบสตริงใช้สัญลักษณ์ปีกกา {key:value1,key2:value2} และคอมม่า(,) เป็นตัวแบ่งแต่ละคู่ และใช้โคลอน(:) เป็นตัวแบ่งฝั่งระหว่าง key และ value

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%209.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2010.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2011.png)

    ในฐานข้อมูล MongoDB จะทำการแปลงเอกสาร JSON โดยเข้ารหัสให้อยู่ในรูปแบบไบนารี่หรือเรียกว่า **BSON(Binary JSON)** เพื่อขยายความสามารถให้ JSON มีชนิดข้อมูลเพิ่มมากขึ้น มีการเข้าและถอดรหัสด้วยภาษาที่แตกต่างกันได้

    **BSON** จะมีขนากเบาและรับส่งข้อมูลได้เร็วเหมือนกับ JSON โดย MongoDB สามารถเข้าถึงข้อมูลหรือ Object ใน BSON เพื่อสร้าง Index ในการทำระบบสอบถามข้อมูล(Query) โดย BSON จะทำงานซ่อนอยู่เบื้องหลัง ส่วนการแสดงข้อมูลกับผู้ใช้จะเป็น JSON

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2012.png)

---

## การสร้างและลบฐานข้อมูล

ใช้ mongo shell

- การแสดงฐานข้อมูล
    
    <aside>
    💡 show dbs
    
    </aside>
    
    ![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2013.png)
    
- การสร้างหรือเลือกฐานข้อมูล
    
    <aside>
    💡 use ชื่อฐานข้อมูล
    
    </aside>
    
    - กรณีที่ยังไม่มีฐานข้อมูลนั้น : จะทำการสร้างฐานข้อมูลขึ้นมา
        
        จะทำงานคู่กับ db.createCollection() เพื่อเป็นการสร้างฐานข้อมูล และจะถูกเห็นได้จาก show dbs
        
        <aside>
        💡 db.createCollection(”ชื่อ collection”)
        
        </aside>
        
        ![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2014.png)
        
    
    **การสร้างฐานข้อมูลใน MongoDB Compass**
    
    ![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2015.png)
    
    ![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2016.png)
    
    - กรณีที่มีฐานข้อมูลอยู่แล้ว : จะเลือกฐานข้อมูลนั้นมาใช้
        
        ![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2017.png)
        
- การลบฐานข้อมูล
    
    <aside>
    💡 db.droupDatabase()
    
    </aside>
    
    - โดยที่ต้องเข้าไปทำงานในฐานข้อมูลก่อนถึงจะลบได้
        
        ![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2018.png)
        
    
    ![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2019.png)
    

---

## การจัดการ Collection

- การสร้าง Collection
    
    <aside>
    💡 use ชื่อฐานข้อมูล
    db.createCollection(”ชื่อ Collection”)
    
    </aside>
    
    ![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2020.png)
    
- การเปลี่ยนชื่อ Collection
    
    <aside>
    💡 db.ชื่อCollection.renameCollection(”ชื่อ Collection ใหม่”)
    
    </aside>
    
    ![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2021.png)
    
- การลบ Collection
    
    <aside>
    💡 db.ชื่อCollection.drop()
    
    </aside>
    
    - โดยที่ต้องเข้าไปทำงานในฐานข้อมูลก่อนถึงจะลบได้
        
        ![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2022.png)
        

---

## ชนิดข้อมูลใน MongoDB

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2023.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2024.png)

---

## การเพิ่ม Document (insert)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2025.png)

- **การเพิ่ม Document เดียว**
    
    <aside>
    💡 db.ชื่อCollection.insertOne(<Document>)
    
    </aside>
    
    ![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2026.png)
    
    ![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2027.png)
    
    - เพิ่ม/ลด field ใน document ได้
    
    ![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2028.png)
    
    **การเพิ่มใน MongoDB Compass**
    
    ADD DATA>Import Document
    
    ![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2029.png)
    
    - โดยที่แต่ละ field ต้องกำหนดชนิดข้อมูลด้วย
    
- **การเพิ่มหลาย Document**
    
    <aside>
    💡 db.ชื่อCollection.insertMany([<Document>])
    
    </aside>
    
    ![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2030.png)
    
- **การเพิ่ม Document ที่มี field เป็น array**
    
    ![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2031.png)
    
    ![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2032.png)
    
    ![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2033.png)
    
    **การเพิ่มใน MongoDB Compass**
    
    ![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2034.png)
    
- **การเพิ่ม Document ที่มี field เป็น Object**
    
    เข้าถึงข้อมูลได้ง่ายกว่า array (ไม่ต้องจำเลข index)
    
    ![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2035.png)
    
    ![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2036.png)
    
    ![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2037.png)
    
    **การเพิ่มใน MongoDB Compass**
    
    ![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2038.png)
    

---

## การส่งออกและนำเข้า Collection

- **การส่งออก Collection ใน MongoDB Compass**

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2039.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2040.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2041.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2042.png)

- **การนำเข้า Collection ใน MongoDB Compass**
    
    ADD DATA>Import file  
    
    ![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2043.png)
    

---

## การสอบถามข้อมูล

- **fineOne()**
    
    การสอบถามข้อมูล Document จาก Collection ตามเงื่อนไขที่กำหนดผลจากการวอบถามจะได้ผลลัพธ์เพียง Document เดียว หากเจอ Document หลายรายการจะเลือกเอารายการแรกมาใช้งาน ถ้าไม่เจอจะได้ค่า Null
    
- **fine()**
    
    สอบถามข้อมูล Document จาก Collection ถ้าไม่กำหนดเงื่อนไขจะเลือก Document ทั้งหมดมาใช้งาน แต่สามารถกรอง (Filter) หรือเลือกข้อมูลภายใน Document ได้โดยระบุเงื่อนไข หรือ Parameter เข้าไป ถ้าเงื่อนไขไม่ตรงจะได้ Document เป็นค่า Null
    

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2044.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2045.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2046.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2047.png)

**การสอบถามข้อมูลแบบเงื่อนไขเดียว**

- ใช้ **{}** เพื่อระบุเงื่อนไขข้างใน
- ใช้ **:** แทนเครื่องหมายเท่ากับ

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2048.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2049.png)

**การสอบถามข้อมูลแบบ 2 เงื่อนไข**

- ใช้ , แทน และ

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2050.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2051.png)

สามารถใช้ FILTERใน MongoDB Compass ได้ > กด FIND

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2052.png)

**การสอบถามข้อมูลแบบ Object**

สอบถามใน field ย่อยที่เป็นชนิดข้อมูลแบบ Object

**เข้าถึงด้วย**

<aside>
💡 **“**ชื่อ_field_หลัก**.**ชื่อ_field_ย่อย**”**

</aside>

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2053.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2054.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2055.png)

**การสอบถามข้อมูลแบบ Array**

- สอบถามข้อมูลที่ต้องการภายใน []
- สนใจลำดับภายใน [] (ลำดับไม่ตรง: ไม่นำมาแสดงผล)

**เข้าถึงด้วย**

<aside>
💡 **“**ชื่อ_field_array**”:[”**ข้อมูลที่จะสอบถาม**”]**

</aside>

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2056.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2057.png)

---

## ตัวดำเนินการเปรีบเทียบ

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2058.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2059.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2060.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2061.png)

---

## สอบถามข้อมูลด้วย In และ Not In

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2062.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2063.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2064.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2065.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2066.png)

---

## ตัวดำเนินการทางตรรกศาสตร์

เขียนเงื่อนไขใน [] และคั้นเงื่อนไขด้วย , (comma)

<aside>
💡 **$and**:[{เงื่อนไขที่_1},{เงื่อนไขที่_2}]

</aside>

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2067.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2068.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2069.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2070.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2071.png)

---

## การอัพเดต&ลบ Document

มี 2 รูปแบบ

- อัพเดตรายการเดียว
    - การอัพเดต
        
        <aside>
        💡 db.ชื่อCollection.updateOne({flieldที่ต้องการแก้ไข},{ข้อมูลที่ต้องการแก้ไข(แก้ไขหลายรายการใช้ , คั้น)},{ตัวเลือกเพิ่มเติม})
        
        </aside>
        
    
    ![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2072.png)
    
    - การลบ
        
        <aside>
        💡 db.ชื่อCollection.deleteOne({flieldที่ต้องการลบ})
        
        </aside>
        
        ![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2073.png)
        
- อัพเดตหลายรายการ
    - การอัพเดต
        
        <aside>
        💡 db.ชื่อCollection.updateMany({flieldที่ต้องการแก้ไข},{ข้อมูลที่ต้องการแก้ไข(แก้ไขหลายรายการใช้ , คั้น)},{ตัวเลือกเพิ่มเติม})
        
        </aside>
        
    
    ![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2074.png)
    
    - การลบ
        
        <aside>
        💡 db.ชื่อCollection.deleteMany({flieldที่ต้องการลบ})
        
        </aside>
        
        ![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2075.png)
        

---

## Aggregation & Pipeline

**Pipeline** : การนำเข้าข้อมูลขากฐานข้อมูลมารวมเข้าด้วยกันและวิเคราะห์หาผลลัพธ์ที่ต้องการ โดยจะนำเอา Document ต่างๆจาก Collection ไปเข้าสู่กระบวนการกลั่นกรอง (Stage) เพื่อวิเคราะห์หาผลลัพธ์ (Output)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2076.png)

Pipeline จะใช้ method/คำสั่ง : **aggregation()** สำหรับรวบรวม Document ภายใน Collection ซึ่งด้านในจะประกอบไปด้วย Array ของ Stage โดย Document ทั้งหมดก็จะถูกดำเนินการกลั่นกรองข้อมูลด้านในกลุ่มของ Stage ดังกล่าวนั้นเอง

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2077.png)

<aside>
💡 db.ชื่อCollection.aggregate([stage])

</aside>

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2078.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2079.png)

### การสอบถามข้อมูลด้วย $project (Projection)

เป็นรูปแบบการสอบถามข้อมูล และให้แสดงผลเฉพาะ field ที่ต้องการและส่งออกไปโดยการแสดง field จะกำหนดเป็นหมายเลย 1 ส่วนการซ่อน/ปิด field จะใช้หมายเลข 0

<aside>
💡 {**$project**:{ชื่อfield : หมายเลข,ชื่อfield : หมายเลข}}

</aside>

- ถ้าไม่ระบุ field : _id จะเปิดทุกครั้ง (มีค่าเป็น 1) เนื่องมาจากเป็นค่าที่ไม่ซ้ำกันในแต่ละ document)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2080.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2081.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2082.png)

### การสอบถามข้อมูลด้วย $match

เป็นรูปแบบการสอบถามข้อมูลโดยเลือกเอาเฉพาะ Document ที่ผ่านเงื่อนไขที่ระบุแล้วส่งออกไป

<aside>
💡 {**$match**:{ชื่อfield : เงื่อนไข}}

</aside>

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2083.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2084.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2085.png)

### นับจำนวนด้วย $count

เป็นการนับจำนวน Document ใน Collection และส่งออกเป็นจำนวน Document ที่นับได้

<aside>
💡 {**$count**:ชื่อfieldที่แสดงการนับจำนวน<string>}

</aside>

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2086.png)

### เรียงลำดับด้วย $count

การดึงข้อมูลใน Collection จะมีลำดับในการจัดเก็บข้อมูล ถ้าเราต้องการอยากเรียงลำดับข้อมูลใหม่จะใช้ $sort โดยกำหนดค่าเป็นหมายเลข ดังนี้

- **1**  : เรียงจากน้อยไปมาก/พยัญชนะ (ก-ฮ) - สระ
- **-1** : เรียงจากมากไปน้อย/สระ - พยัญชนะ (ก-ฮ)

<aside>
💡 {**$sort**:{ชื่อfield:หมายเลข,ชื่อfield:หมายเลข}}

</aside>

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2087.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2088.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2089.png)

### จำกัดข้อมูลด้วย $limit

การจำกัดการแสดงจำนวน Document 

<aside>
💡 {**$limit**:จำนวนDocumentที่ต้องการจะแสดง<integer>}

</aside>

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2090.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2091.png)

### ข้าม Document ด้วย $skip

ข้าม Document ที่ไม่ต้องการจะเเสดง 

<aside>
💡 {**$skip**:จำนวนDocumentที่จะข้ามการแสดงผล<integer>}

</aside>

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2092.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2093.png)

### การจัดกลุ่มข้อมูลด้วย $group

การจัดกลุ่มข้อมูลของ Document ไว้เป็นกลุ่มเดียวกันโดยมี _id เก็บรายการข้อมูลแต่ละกลุ่มที่ไม่ซ้ำกัน และยังสามารถเพิ่มฟิลด์ในการคำนวณหาผลลัพธ์ภายในกลุ่มข้อมูลที่สร้างขึ้นได้ โดยใช้งานกลุ่มร่วมกับฟังก์ชั่นทางสถิติ

<aside>
💡 {**$group**:{ชื่อfieldสำหรับจัดกลุ่ม:ตัวดำเนินการทางสถิติ}}

</aside>

**ex.** {**$group**:{_id:”$address”}}, {**$group**:{_id:null}}

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2094.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2095.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2096.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2097.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2098.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%2099.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%20100.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%20101.png)

### เพิ่มข้อมูลกลุ่มด้วย $push และ $addToSet

การเพิ่มลายละเอียดข้อมูล

- $push : แสดงผลเป็น object
- $addToSet : แสดงผลเป็น array

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%20102.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%20103.png)

### เชื่อม Collection ด้วย $lookup

เป็นการสอบถามข้อมูล Document ที่เก็บข้อมูลใน Collection ที่แตกต่างกันโดยกำหนดให้ Collection หลักเชื่อมกับ Collection ด้านนอก ซึ่ง Collection ดังกล่าวต้องอยู่ในฐานข้อมูลเดียวกัน ผลลัพธ์ที่ได้คือ กลุ่ม Document ที่เชื่อมโยงช้อมูลระหว่าง Collection นั้นเอง

<aside>
💡 {**$lookup:**{
     **from:**”ชื่อCollectionด้านนอกที่เชื่อมโยง”,
     **localField:**”FieldจากCollectionหลัก”,
     **foreignField:**”FieldCollectionที่จะเชื่อมโยง”,
     **as:**”ชื่อFieldที่เก็บผลลัพธ์”
     }
}

</aside>

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%20104.png)

![Untitled](MongoDB%205a42f8cfde0c44509e7a951e3f689d2e/Untitled%20105.png)

---