# ASP.NET Core MVC (.NET7)

## **MVC**

- **Model(M) :** ส่วนที่เก็บข้อมูลของ Application (Back-End)
- **View(V) :** ส่วนที่ทำงานฝั่ง Front-End หรือหน้าตาแอพพริเคชั่น เป็นส่วนที่ไว้ใช้แสดงผลข้อมูลด้วย HTML ร่วมกับ Tag Helper
- **Controller(C) :** ส่วนประมวลผลคำสั่งต่างๆ ใน Application โดยควบคุมการทำงานระหว่าง Model และ View (Back-End)

## Getting Start

### Create new project

- เลือก templates : ASP.NET Core Web App(Model-View-Controller)
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled.png)
    
- ตั้งชื่อ Project, Location
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%201.png)
    
- ต่อมา เลือก Framework : .NET 7.0 (Standard Team Support)
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%202.png)
    
- create

## Introduce

- สามารถเลือกการ run projectได้
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%203.png)
    
- ออกจากการ run ด้วยการ ปิด prompt/ปิด web browser
- มี hot reload: สามารถกดเพื่อเป็นการ update คำสั่งอัตโนมัติ
- การตั้งค่าการ run ตัว project จะอยู่ใน Properties>launchSetting.json
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%204.png)
    
    - โดยที่ .NET 7.0 ต่างจาก .NET 6.0 ตรงที่ .NET 7.0 มี http, https แต่ .NET 6.0 จะเป็นชื่อ project แทน (ไม่มี profile: http/https)

---

## โครงสร้าง Project

### Folder

- **Controllers :** เป็น folder ที่เก็บกลุ่ม Controller สำหรับกำหนดการทำงานหรือการประมวลผลข้อมูลใน application
- **Models :** เป็น folder ที่เก็บกลุ่ม file : Model เพื่อใช้งานฐานข้อมูล
- **Views :** เป็น folder ที่เก็บ file สำหรับแสดงผลหน้าเว็บ (.cshtml)
- **wwwroot :** เป็น folder ที่ใช้จัดการ Static File (css, js), เก็บ file รูปภาพ, library
- **Properties :** เป็น folder ที่เก็บการตั้งค่ารูปแบบการ run : application ผ่าน file ที่ชื่อวา launchSetting.json

### Files

- **appsettings.json :** เป็น Configuration File หลักของระบบ เช่นการเพิ่ม Environment Variable ที่ใช้ใน project
- **Program.cs :**
    
    การทำงานเริ่มต้นของ project: ASP.NET Core MVC จะอยู่ใน file: Program.cs ซึ่งมีกลุ่มคำสั่งสำหรับจัดการ Request และ Response (Middleware) รวมถึงการตั้งค่า Service หรือบริการต่างๆ ที่ใช้งานใน project เช่น Routing, Database Service, Static File, Authentication เป็นต้น
    
    - File : Program.cs จะมีการตั้งค่าบริการเริ่มต้นสำหรับจัดการเส้นทาง(Route) และ Controller
        
        ผ่านคำสั่ง :
        
        <aside>
        <img src="https://www.notion.so/icons/snippet_gray.svg" alt="https://www.notion.so/icons/snippet_gray.svg" width="40px" /> app.UseRouting();
        
        app.MapControllerRoute(
        
        name: “default”,
        
        pattern: “{controller=Home}/{action=Index}/{id?}”
        
        );
        
        </aside>
        
        - name: “default” ; default คือชื่อ Route: เมื่อเปิด project จะไปค้นหาเส้นทางที่ชื่อ default โดยเส้นทางจะไปคุยกับ controller
        - controller=Home ; controller จะเป็นที่ทำงานเป็นอันดับแรกในตอนเริ่มต้นรัน Application
            - Home: เขียนแบบย่อ
            - HomeController: เขียนแบบเต็ม
        - action=Index ; action คือกระบวนการทำงาน function
            - Index(): ชื่อ method ที่ทำงานอยู่ใน Home(HomeController)
            - ดังนั้น ชื่อ controller กับ ชื่อ action ต้องสัมพันธ์กัน
        - id? ; parameter ที่ส่งเข้ามาทำงานใน method: Index, สามารถส่งค่าเข้าไปทำงานหรือไม่ส่งก็ได้ (? Optional Parameter)
    
    ตัวอย่างการใช้งาน:
    
    **Program.cs** : กระบวนการทำงานเริ่มต้นของตัว Project จะอยู่ใน file นี้
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%205.png)
    
    - Program จะสร้าง builder และ set Service: AddContollersWithViews():
        - นั้นคือ จะมี Contoller และ Views ทำงานอยู่ใน project
    - ตั้งค่า MiddleWare ผ่าน App
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%206.png)
    
    เช่น 
    
    การกำหนดการใช้ middleware ที่มีชื่อว่า HttpsRedirection() : กำหนดให้ตัว project run เป็นรูปแบบของ https
    
    - การกำหนดการใช้ middleware ที่มีชื่อว่า HttpsRedirection() : กำหนดให้ตัว project run เป็นรูปแบบของ https
    - มีการใช้ตัว static file ผ่าน app.UseStaticFiles()
    - มีการกำหนดเส้นทาง ผ่าน app.UseRouting()
    - มีการกำหนดสิทธิที่จะจัดการข้อมูลที่อยู่ในตัว project ผ่าน app.UseRouting()
    - app.MapContollerRoute : เป็นการจับคู่ระหว่างชื่อ controller กับชื่อ route
    
    **HomeContoller.cs :** 
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%207.png)
    
    - มี Action method ที่ทำงานอยู่ใน HomeController
        - Index() ; return View()
        - Privacy() ; return View()
        
        View ในที่นี้คือ View ที่บรรจุอยู่ใน HomeController โดยจะมีชื่อ View ตาม Action method (.cshtml)
        
        ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%208.png)
        

---

## Routing & Controller

- **Routing :** ส่วนที่ใช้ระบุเส้นทางในการรับส่งข้อมูล
- **Controller :** ศูนย์กลางสำหรับส่งข้อมูล และการประมวลผลโยเชื่อมโยงการทำงานระหว่าง Model และ View

**โครงสร้าง URL**

![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%209.png)

- **Path :** จับคู่ระหว่าง Controller และ Action Method ใน Controller เอาไปสร้างเป็น View
    
    **ตัวอย่าง Path :**
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2010.png)
    
    - **ID :** Parameter ID ส่งมาให้ Action Method

---

## การสร้าง Controller

- คลิกขวา>Add>Controller>MVC Empty>Add>ตั้งชื่อ(xxxController.cs)>Add
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2011.png)
    
    - **IActionResult** Method : ส่งเป็นหน้า Web ออกไป
        
        <aside>
        <img src="https://www.notion.so/icons/snippet_gray.svg" alt="https://www.notion.so/icons/snippet_gray.svg" width="40px" /> public IActionResult Index()
        {
             return Content(”Index”)
        }
        
        </aside>
        
        - return Content(””) : จะเป็นการ return การแสดงผลในรูปแบบ String (ชุดข้อความ)
    - เพิ่ม **Parameter ID** :
        
        ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2012.png)
        
        ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2013.png)
        
    - สามารถเปลี่ยน Default Rout ได้ โดยเมื่อ run Web จะเปิด view ใน Action Method ของ Controller นั้นขึ้นมาทันที : ปรับที่ **pattern**
        
        ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2014.png)
        
        ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2015.png)
        

---

## View

- **View :** หน้าตา Application เป็นส่วนที่ไว้ใช้แสดงผลหรือผลลัพธ์จากการประมวลผลในหน้าเว็บเพจ โดยทำงานร่วมกับ HTML และ Tag Helper
- โดยจะต้องสร้าง file View(.cshtml) ตาม ชื่อ Action method และอยู่ใน folder ที่ตั้งชื่อตามชื่อ controller นั้นๆ
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2016.png)
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2017.png)
    

---

## การสร้าง View-Empty

- คลิกขวาที่ Action method ใน controller ที่ต้องการ>Add View>**Razor View-Empty**>Add>ตั้งชื่อ xxx.cshtml(auto: เอามาจาก ชื่อ Action method)>Add
    
    **ตัวอย่างการใช้งาน :**
    
    **StudentController.cs ;**
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2018.png)
    
    **Index.cshtml ;**
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2019.png)
    
    **การแสดงผล**
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2020.png)
    
    สิ่งที่ไม่ใช่ h1 ; คือ view-layout(BasicASPTutorial - 2566 Privacy)
    

---

## Layout & Tag Helper

- **Layout Views :** การกำหนดโครงสร้างหลักในหน้าเว็บที่ทุกๆหน้าใช้งานร่วมกัน เพื่อลดความซ้ำซ้อนของ code เช่น เมนู(Navbar), Footer เป็นต้น
- โดยการแทรก File เนื้อหสหลักเข้าไปทำงานในหน้า Webpage ใน project ASP.NET Core MVC จะตั้งค่าการทำงาน file ที่ชื่อว่า **“_Layouts.cshtml”** จะอยู่ใน View>Shared>_Layouts.cshtml
    
    **โครงสร้างของ _Layouts.cshtml**
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2021.png)
    

- **Tag Helper** : การเชื่อมโยง Element ของ HTML5 ให้สามารถทำงานร่วมกับ .NET ได้ (ขึ้นต้นด้วย asp-xxx; ชื่อ tag helper ที่เราจะเรียกใช้งาน)
    
    ตัวอย่างเช่น : link ต้องการเรียกใช้ controller และ action method
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2022.png)
    

---

## การสร้าง View-Layout

โครงสร้างที่ View ทุกๆ หน้าจะใช้ร่วมกัน

- คลิกขวาที่ Action method ใน controller ที่ต้องการ>Add View>**Razor View>**Add>ตั้งชื่อ xxx.cshtml(auto: เอามาจาก ชื่อ Action method)>Add
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2023.png)
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2024.png)
    
    - ViewData[”Tittle”] = “Index”; คือการกำหนดชื่อ ViewData ใหม่ ใน _Layouts.cshtml
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2025.png)
    

---

## Model

ส่วนที่เก็บข้อมูลของ Application โดยจะทำหน้าที่จัดการฐานข้อมูลแทนการใช้คำสั่ง SQL โดยตรง ผ่านการกำหนด Class และ Object ซึ่งจะเรียกส่วนนี้ว่า ORM (Object Relational Mapping)

![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2026.png)

---

## การสร้าง Model

โดยที่ 1 Model แทน 1 Table ในฐานข้อมูล

- ออกแบบตารางข้อมูลก่อน เก็บเป็น type อะไร, ชื่อตัวแปรอะไร
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2027.png)
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2028.png)
    
- สร้าง class ใน folder Model (Add) > ตั้งชื่อ class อะไรก็ได้
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2029.png)
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2030.png)
    

---

## สร้าง Object จาก Model

การทำ Model ไปใช้งานใน controller โดยการใช้ Object

- รูปแบบการสร้าง Object
    1. **คำสั่ง new** : เป็นวิธีการสร้าง Object แบบมาตรฐาน
    2. **Type Inference** : ตัวแปรภาษา C# จะกำหนดชนิดข้อมูลให้กับตัวแปรอัตโนมัติตามข้อมูลที่จัดเก็บ
    3. **ใช้ฟังก์ชั่น new()** : การกำหนดชนิดข้อมูลให้กับตัวแปรก่อน ข้อมูลที่อยู่ในตัวแปรนั้นๆก็จะมีชนิดข้อมูลเดียวกันอัตโนมัติ
        
        ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2031.png)
        
        - ใน Controller - StudentController.cs
            
            ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2032.png)
            

---

## การแสดงข้อมูล

การนำข้อมูลจาก controller ไปแสดงผลที่ view โดยข้อมูลนำมาจาก Model

- รายการเดียว (Object เดียว)
    
    **ใน controller** 
    
    - กำหนดข้อมูลด้วยการใช้ตัวแปร object กำหนดค่า
        - ex. s1.Id = 1;
    - ส่งข้อมูลจาก controller ไปแสดงผลที่ view ด้วยการ return object นั้นไปให้ view
        - ex. return View(s1)
        
        ใน controller - StudentController.cs
        
        ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2033.png)
        
    
    **ใน View**
    
    - ต้องมีการ import Model ที่จะใช้งานเข้ามาจาก Model นั้นๆที่มีส่งมาจาก controller
        - ex. @model **BasicASPTutorial**.Models.**Student**;
    - การใช้งานตัวแปรใน Model ต้องระบุ @Model.**ตัวแปร**
        - ex. @Model.Id
        
        ใน view - Index.cshtml
        
        ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2034.png)
        
- หลายรายการ (หลาย Object)
    
    **ใน Controller**
    
    - ต้องมีการรวบรวม Object โดยการใช้ List โดยระบุ Object นั้นๆที่สามารถเก็บได้เท่านั้น
        - ex. List<**Student**> **allStudent** = new List<**Student**>();
            
            >นั้นคือ เก็บเฉพาะ object student เท่านั้น โดยเก็บอยู่ใน list ของตัวแปร allStudent
            
    - เก็บ object เข้า list โดยการใช้ method : Add
        - ex. allStudent**.Add**(s1)
    - ทำการส่ง List ของ Object ไปยัง View
        
        ใน controller - StudentController.cs
        
        ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2035.png)
        
    
    **ใน View**
    
    - เนื่องจากมีหลาย Object การแค่ import Model เข้ามานั้นหมายถึงแค่ 1 Object ดังนั้นจึงเปลี่ยนมา import ด้วย IEnumerable<> แทน เพื่อเป็นการแจกแจง Object
        - ex. @model **IEnumerable<**BasicASPTutorial.Models.Student**>**;
    - ทำให้เมื่อวนการแสดงผลจึงต้องมีการแจกแจง object ด้วย จึงใช้ **@foreach(**var xxx **in** ObjectList**)** มาวนการแสดงผลแทนของเดิม
    - ทำให้เมื่อวน foreach จึงต้องใช้ตัวแปร var xxx แทน Model นั้นคือ ตัวแปร xxx แทน object แต่ละตัวใน ObjectList นั้นๆ
        - ex. xxx.Id แทน Model.Id
        
        ใน View - Index.cshtml
        
        ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2036.png)
        
- เพิ่มเติม
    - สามารถเพิ่มเงื่อนไขใน View เพื่อเลือกข้อมูลได้ - แสดงผลข้อมูลแบบมีเงื่อนไข
        - โดยใช้ @if{} else{}
            
            ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2037.png)
            

---

## SQL Server

ใช้ SQL Server 2022 - Microsoft

เป็นระบบจัดการฐานข้อมูลเชิงสัมพันธ์ (RDBMS: Relational Database Management System) หรือ การเก็บข้อมูลในรูปแบบตารางและใช้ภาษา SQL เข้ามาจัดการข้อมูลในฐานข้อมูล

- ทำให้เครื่องคอมพิวเตอร์ให้เป็นเครื่อง server โดยมี fileๆ นี้เป็นตัวเก็บ database
- ใช้ **Instance name** และ Connection String ในการเชื่อมต่อกับตัวจัดการฐานข้อมูล
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2038.png)
    

## SQL Server Management Studio (SSMS)

โปรแกรมสำหรับจัดการฐานข้อมูล สำหรับกำหนดการเข้าถึง, จัดการฐานข้อมูล และการตั้งค่าฐานข้อมูล เป็นต้น

**การเชื่อมต่อฐานข้อมูลด้วย SSMS**

เชื่อมต่อ SSMS กับ SQL Server โดยระบุ ชื่อเครื่อง/**ชื่อฐานข้อมูล**

- ex. KONGRUKSIAM\**SQLEXPRESS**
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2039.png)
    

---

## Data Annotation

เป็นการกำหนดกฎเกณเฑ์หรือรูปแบบการทำงานในระดับโมเดล

- ex.
- โดยต้องมีกรกำหนด **using System.ComponentModel.DataAnnotation;** ที่ header
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2040.png)
    
    ตัวอย่างการใช้งาน : 
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2041.png)
    
    การกำหนดตัวแปร property Id เป็น [Key] หรือ primary key นั้นคือ ข้อมูลห้ามซ้ำกันและห้ามเป็น null นั้นเอง และ property String ระบุเป็น [Required] นั้นคือจำเป็นต้องมีข้อมูลในส่วนนี้ ห้ามเป็นค่าว่าง
    

---

## Connection String

ชุดข้อความสำหรับระบุตำแหน่งฐานข้อมูลที่จะใช้งานร่วมกับ Project : ASP.NET Core MVC โดยระบุใน file : appsetting.json

- **DefaultConnection** : ชื่อ Connection (อะไรก็ได้)
- **ชื่อ Server** : **Instance name**
- **ชื่อ Database** : ชื่อฐานข้อมูล (อะไรก็ได้)
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2042.png)
    

เป็นการเชื่อมฐานข้อมูล > แต่ยังทำงานไม่ได้ต้องมีตัวแทนฐานข้อมูล : Application DB context เนื่องจากฐานข้อมูลมีหลายประเภท/เจ้า ex. mySQL, mongoDB

---

## Entity Framework Core (EF Core)

- library สำหรับจัดการฐานข้อมูล โดยทำงานร่วมกับ Model
- EF Core ทำหน้าที่จัดการฐานข้อมูลแทนการใช้คำสั่ง SQL โดยตรง
- กระบวนการทำงาน : จะทำการ Mapping หรือจับคู่ Model กับตาราง (Table) ที่อยู่ในฐานข้อมูลและให้ Model นั้นๆ เป็นตัวแทนของตาราง (ORM : Object Relational Mapping)
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2043.png)
    

**ติดตั้ง :**

Project > Manage NuGet Packages… > ค้นหา > install

สามารถ check package ที่ download มา : ชื่อ Project > Dependencies > Packages

---

## Application DbContext

การสร้าง class ที่รับบทบาทเป็นตัวแทนของฐานข้อมูลที่ใช้งานใน Project รวมถึง Model ที่จะนำไปสร้างเป็นตารางเก็บในฐานข้อมูลดังกล่าวต้องมาระบุใน Application DbContext นี้

วิธีทำ : 

1. สร้าง folder จัดเก็บ 
    1. ชื่อ Project > Add > New folder : ตั้งชื่อว่า Data
    2. Data > Add > Class : ตั้งชื่อว่า ApplicationDBContext
2. ให้ class : ApplicationDBContext สืบทอดคุณสมบัติมาจาก class : DbCintext
    1. import class : DbCintext : มาจาก Microsoft.EntityFrameworkCore
        1. พิมพ์คำสั่ง : using Microsoft.EntityFrameworkCore;
3. สร้าง constructure : ระบุ Option (ระบุว่าเชื่อมต่อ ฐานข้อมูลแบบใด)
    1. โดยระบุใน <> 
        1. DbContextOptions<**ApplicationDBContext**> options
            
            -options แทนฐานข้อมูล
            
        2. โยน options ไปทำงานใน class แม่ โดยการเรียกใช้ comstructure class แม่ : โดยใช้คำสั่ง base()
            - base(options)
        
        ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2044.png)
        
4. นำ Model ไปสร้างฐาข้อมูล โดยใช้คำสั้ง DbSet<Model> ชื่อแทนฐานข้อมูล {get; set;}
    1. DbSet<Student> Students {get; set;}
        - Model : Student นำไปสร้างตารางฐานข้อมูล โดยจะใช้ชื่อ Students แทนตารางที่ Student ไปสร้างมา
        
        ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2045.png)
        

---

## ตั้งค่า DbContext

ตั้งค่า service (ที่เกี่ยวกับฐานข้อมูล) ที่จะใช้งาน

- ไปที่ Program.cs
    - เพิ่ม service : เชื่อมต่อฐานข้อมูลผ่าน Application DbContext
        - builder.Services.AddDBContext<**class ที่เชื่อมต่อ**>(**ตัวที่จะตั้งค่า service** ⇒ **ตัวที่จะตั้งค่า service**.**ใช้ฐานข้อมูลประเภทใด**(builder.Configuration.GetConnectionString(”**ชื่อ Connection String**”)))
            - builder.Services.AddDBContext<**ApplicationDbContext**>(**options** ⇒ **options**.**UseSqlServer**(builder.Configuration.GetConnectionString(”DefaultConnection”)))
                - **import :** using BasicASPTutorial.Data
        
        ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2046.png)
        

---

## การสร้างฐานข้อมูล (Database)

ดำเนินการผ่าน package manager console : การป้อนคำสั่ง

อยู่ใน Tools > NuGet Package Manager > Package Manager Console

- **จะมี terminal ขึ้น :** PM>
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2047.png)
    

**ขั้นตอนการสร้างข้อมูล**

1. **add-migration <migration-name>**
    1. สร้างไฟล์ migration ที่เก็บโครงสร้างตารางจาก Model ⇒ แปลง Model เป็นตาราง
        
        ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2048.png)
        
    2. folder : **Migration** จะสร้างขึ้น โดยจะมี file : xxx_addStudentDB.cs ถูกสร้างขึ้น > file นี้บรรจุโครงสร้างของตารางที่ถูกแปลงจาก Model เป็นตารางในฐานข้อมูลผ่าน DbSet โดยจะสร้างตารางใน ApplicationDBContext.cs 
    3. ใน file : ApplicationDBContext.cs 
        
        ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2049.png)
        
    4. **update-database**
    5. นำไฟล์ migration ไปใช้งาน
        
        ใน SqlServer สร้างฐานข้อมูลมาแล้ว > ยังไม่มีข้อมูล
        
        ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2050.png)
        
        - ดูข้อมูล dbo.student > คลิกขวา >Select Top 1000 Rows
    
    ---
    
    ## ตัวอย่าง : แบบฟอร์มบันทึกข้อมูล
    
    - **tag form**
        - **asp-controller :** ปลายทางที่ข้อมูลจะส่งมา
        - **asp-action :** method ที่จะรับค่าที่ส่งมามาทำงาน
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2051.png)
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2052.png)
    
    - **get :** เหมาะกับการดึงข้อมูล
    - **post :** เหมาะกับการส่งข้อมูล/บันทึกข้อมูล
    
    **ตัวอย่างการใช้งาน :**
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2053.png)
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2054.png)
    
    - import Model เข้ามาใช้งาน
    - ผูกค่า form กับ model ด้วย tag helper : **asp-for=””**
        - <Label asp-for=”Name”></Label> : นำชื่อ property Name มาแสดงผล
        - <input type=”text” asp-for=”Name”></Label> : ผูกค่า
        - ค่า defult ของ method เป็น GET Method เนื่องจากไม่ได้รับค่ามา แค่ส่งไปแสดงผลที่ view
        
        ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2055.png)
        

---

## DisplayName & Range

**DisplatName :** เป็นการใช้ data anotation แทนที่ <Label **asp-for=”Name”**> ทำให้สามารถตั้งชื่อ property อื่นได้ โดยตั้งใน Model

**Range :** เป็นการใช้ data anotation เพื่อกำหนดช่วงของตัวเลข ถึงเก็บลงในฐานข้อมูลได้ 

![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2056.png)

---

## Dependency Injection

การกำหนดให้ controller สามารถเรียกใช้งานฐานข้อมูลได้ ผ่านตัวแทนของฐานข้อมูลที่ระบุใน DbContext

- โดยการสร้าง object จาก ApplicationDbContext ในพื้นที่ของ controller ที่เราสนใจ
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2057.png)
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2058.png)
    

---

## การบันทึกข้อมูล (Insert)

![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2059.png)

**ตัวอย่างการใช้งาน :**

ใน file : StudentController.cs

![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2060.png)

- Post Method : รับ parameter เป็น Model : Student มาทำงาน เนื่องจาก form มีการผูกค่ากับ Model : Student (Name, Score)
- เรียกใช้ฐานข้อมูลจาก **DbSet ที่เข้าถึงฐานข้อมูล Students** ผ่านตัวแปร _db
    - _db.**Students**.**Add**(obj) : เพิ่มข้อมูลที่ส่งมาลงตาราง
    - _db.SaveChanges() : บันทึกข้อมูล
- return RedirectToAction(”Index”) : กลับไปเรียกใช้ Method : Index ใน  file : StudentController.cs เดียวกัน
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2061.png)
    

---

## การดึงข้อมูล (Select)

- IEnumerable <ชื่อ Model> ชื่อที่จะเรียกใช้ = ตัวที่เข้าถึงฐานข้อมูล.ตัวแทนฐานข้อมูล
    - IEnumerable <Student> allStudent = _db.Students
    - เนื่องจากในตารางมีหลาย object > ใช้ IEnumerable
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2062.png)
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2063.png)
    

---

## การตรวจสอบความถูกต้อง (Validation)

ระบุเพื่อให้ตรวจสอบ data anotation ที่ระบุ

ex. การตรวจสอบค่าว่าง (Required), อยู่ในช่วงไหม (Range)

- โดยใช้ if(**ModelState.IsValid**){}
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2064.png)
    
    - ถ้าข้อมูลถูก > Redirect
    - ถ้าข้อมูลผิด > คงอยู่หน้านี้ต่อ, คงสภาพข้อมูลต่อไป

**ตัวอย่างการใช้งาน :**

- เมื่อป้อนข้อมูลไม่ถูกต้อง > แจ้งข้อความตอบกลับ
    - ใช้ tag-helper : **asp-validation-for=”ชื่อ poperty”**
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2065.png)
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2066.png)
    

---

## การปรับแต่งข้อความ (Custom Validation)

แปลงภาษาอังกฤษเป็นภาษาไทย/แสดงข้อความตอบกลับเอง

- ระบุ Attribue : **ErrorMassage : “”** ใน data anotation

**ตัวอย่างการใช้งาน :**

![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2067.png)

![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2068.png)

---

## การแสดงข้อมูลแบบตาราง

**ตัวอย่างการใช้งาน :** 

![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2069.png)

![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2070.png)

![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2071.png)

---

## การแก้ไขข้อมูล (Edit)

**ตัวอย่างการใช้งาน :**

ใน Index.cshtml

![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2072.png)

- ส่ง Id นักเรียน ที่จะไปแก้ไข โดยระบุ tag-helper : **asp-route-id=””**

ใน StudentController.cs

![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2073.png)

- สร้าง Edit.cshtml (View)
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2074.png)
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2075.png)
    

---

## การอัพเดตข้อมูล (Update)

- ตัวที่เข้าถึงฐานข้อมูล.ตัวแทนฐานข้อมูล.**Update**(Obj ที่จะอัพเดต)
    - _db.Students.**Update**(Obj)
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2076.png)
    

---

## **การลบข้อมูล (Delete)**

- ตัวที่เข้าถึงฐานข้อมูล.ตัวแทนฐานข้อมูล.**Remove**(Obj ที่จะลบ)
    - _db.Students.**Remove**(Obj)

**ตัวอย่างการใช้งาน :**

ใน Index.cshtml

![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2077.png)

- หลังจากลบต้องมีการ update ตารางด้วย
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2078.png)
    

---

## การยืนยันการลบ (Confirm)

ถามกับผู้ใช้ว่า ต้องการลบออกจาฐานข้อมูงจริงใช่ไหม

- ใช้ event : **onclick=”return confirm(’ข้อความ’)”**
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2079.png)
    
    - กด OK = ลบ, Cancel = ไม่ลบ
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2080.png)
    

---

## การปรับการแสดงผล

ถ้าไม่มีข้อมูลอยู่ในฐานข้อมูล > ไม่ต้องแสดงผลตาราง

- นับจำนวน Object ที่ทำงานอยู่ในตัว Model (นับจำนวนแถวของฐานข้อมูล) ด้วยคำสั่ง : **Model.Count()** ใส่ใน if-else เพื่อเช็ค
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2081.png)
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2082.png)
    
    ![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2083.png)
    

![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2084.png)

- กดบันทึกข้อมูลถึงมีตารางแสดงผลออกมา

![Untitled](ASP%20NET%20Core%20MVC%20(%20NET7)%200ed4345ed0fd487c9c4523e69c2bc1f9/Untitled%2085.png)

---