# การใช้งาน library จาก Composer ภาษา PHP เเละเเนะนำ library ตัวสำคัญที่ใช้กับ Project
### 1. โหลด ```composer.phar```
- ลิงก์ดาวน์โหลดไฟล์ composer.phar โดยตรงจากเว็บทางการ:
👉https://getcomposer.org/composer.phar
- เอาไฟล์ ```composer.phar``` ที่คุณโหลดมา
- ย้ายไปที่โฟลเดอร์ ```C:\xampp\php```
---
### 2. สร้างไฟล์ ```composer.bat```
- ไปที่ ```C:\xampp\php```
- คลิกขวา → New → Text Document → ตั้งชื่อ ```composer.bat```
- เปิดไฟล์ composer.bat ด้วย Notepad

__ใส่โค้ดนี้:__
```bat
bat

@php "%~dp0composer.phar" %*
```
- กด Save → ปิด
    - ไฟล์ ```.bat``` นี้ทำหน้าที่เป็น "ตัวลัด" เรียก ```composer.phar``` ผ่าน PHP

---
#### การใช้งานตัวของ ```composer.phar``` กับ ```composer.bat```
นำไฟล์ composer.phar ไปวางไว้ในโฟลเดอร์ project ของคุณ เช่น:
```makefile
makefile

C:\xampp\htdocs\Myproject\composer.phar
```

---
### เเนะนำ(วิธีใช้ถาวร)

ถ้าไม่อยากใช้ ```php composer.phar``` ทุกครั้ง ให้ติดตั้ง Composer แบบ global จะสะดวกกว่าเยอะ

- ดาวน์โหลด installer: https://getcomposer.org/Composer-Setup.exe


#### วิธีติดตั้ง __Composer-Setup.exe__
- ดับเบิลคลิกไฟล์ Composer-Setup.exe ที่โหลดมา
- ตอนติดตั้ง:
    - เลือก __PHP.exe__ ของ XAMPP (เช่น ```C:\xampp\php\php.exe```)
    - ติ๊กให้ __เพิ่ม Composer ลงใน PATH__ (สำคัญมาก จะได้ใช้ได้จากทุกที่)
    - กด Next → Install → Finish

- เปิด __Git Bash หรือ CMD ใหม่__ (ต้องเปิดใหม่หลังติดตั้ง)

ลองเช็คว่า Composer ใช้งานได้หรือยัง:
```bash
bash

composer -V
```

ถ้าได้ผลลัพธ์ประมาณนี้ แสดงว่าพร้อมใช้งานแล้ว 👇
```yaml
Composer version 2.x.x 2025-xx-xx ...
```
📂 ตำแหน่งที่เก็บ

- Installer จะจัดการเก็บไฟล์ Composer และตั้งค่า PATH ให้อัตโนมัติ
- คุณไม่ต้องวาง ```composer.phar``` เอง
- จากนั้นทุก project ที่อยู่ใน ```C:\xampp\htdocs\YourProject``` ก็ใช้ Composer ได้เลย

---
### 3. เพิ่ม Path ให้ Windows รู้จัก
- กด __Start__ → พิมพ์ env → เลือก __Edit the system environment variables__
- กดปุ่ม __Environment Variables...__
- ในช่อง __System variables__ → หา ```Path``` → กด __Edit__
- กด New → เพิ่มค่า:
```makefile
makefile

C:\xampp\php
```
- กด OK ปิดหน้าต่างทั้งหมด
---
### 4. รีสตาร์ท Git Bash หรือ CMD
- เพื่อให้ PATH ใหม่ทำงาน

---
### 5.ตรวจสอบ Path ว่ามี C:\xampp\php อยู่จริงหรือไม่
- เปิด ```cmd``` (ไม่ใช่ Git Bash)
- พิมพ์:
```cmd
cmd

echo %PATH%
```

ดูว่ามี ```C:\xampp\php``` อยู่ในนั้นหรือไม่

---

### 6. ทดสอบ
- เปิด Git Bash หรือ CMD แล้วลองพิมพ์:
```bash
bash

composer --version
```
- ถ้าเห็นเวอร์ชันของ Composer → แปลว่าติดตั้งถาวรเรียบร้อย ✅

---
## 🛠️ วิธีใช้งาน Composer กับโปรเจกต์
สมมติคุณมีโปรเจกต์อยู่ใน:
```makefile
makefile

C:\xampp\htdocs\Myproject
```

ให้เข้าไปโฟลเดอร์นั้นก่อน เปิด Git bash ใส่คำสั่ง:
```bash
bash

cd /c/xampp/htdocs/Myproject
```
หรือ:
```cmd
cmd

cd /c/xampp/htdocs/Myproject
```
#### *จำเป็นต้องใส่คำสั่ง ```cd /c/xampp/htdocs/Myproject``` ก่อนใช้งานกับ Project

**แล้วจึงใส่คำสั่งติดตั้ง library ที่ต้องการทำงาน เช่น:**
```bash
bash

composer init -n
composer require illuminate/support nesbot/carbon danielstjules/stringy
```
- __Library__ ->  ```(illuminate/support => มาจาก Laravel Framework → รวมพวก Helper functions และ Collection, nesbot/carbon => เป็น library จัดการ วัน เวลา แบบใช้ง่ายมาก, danielstjules/stringy => เอาไว้จัดการ String (ภาษาอังกฤษและ UTF-8 ได้ดี))``` คือ __library__ ที่ใช้บ่อย ใน __PHP__ ผ่าน __Composer__

__Composer__ จะสร้างไฟล์ ```composer.json``` และโฟลเดอร์ ```vendor``` ให้ → จากนั้นคุณก็ ```require "vendor/autoload.php";``` ใน __PHP__ ได้เลย 

---
## นอกจากนี้ขอเเนะนำ library ที่ใช้บ่อยๆ กับ Project จริง
#### 1. ```vlucas/phpdotenv```
**ใช้จัดการไฟล์ ```.env``` สำหรับเก็บค่าลับ (เช่น DB password, API key)**
```bash
bash

php composer.phar require vlucas/phpdotenv
```
__สร้างไฟล์ .env__

ให้สร้างไฟล์ชื่อ ```.env``` ไว้ใน root ของโปรเจกต์ (เช่นเดียวกับ ```index.php```, ```vendor/```)

📂 โครงสร้างตัวอย่าง
```bash
bash

/xampp/htdocs/MyProject/
│── index.php
│── .env
│── composer.json
│── vendor/
```

📄 ตัวอย่าง ```.env``` ใช้คำสั่งนี้ copy เเละวางใน file ได้เลย เเละเปลี่ยนค่าเองเพื่อความปลอดภัย
```ini
ini

DB_HOST=localhost
DB_PORT=3306
DB_NAME=mydb
DB_USER=root
DB_PASS=secret

APP_ENV=development
APP_DEBUG=true
```
#### โหลดค่า ```.env``` ในโค้ด PHP

สร้าง/แก้ไฟล์ ```index.php``` หรือไฟล์เชื่อมต่อฐานข้อมูลของคุณ
```php
php

<?php
require __DIR__ . '/vendor/autoload.php';

// โหลดไฟล์ .env
$dotenv = Dotenv\Dotenv::createImmutable(__DIR__);
$dotenv->load();

// ใช้งานค่าจาก .env
$host = $_ENV['DB_HOST'];
$user = $_ENV['DB_USER'];
$pass = $_ENV['DB_PASS'];
$db   = $_ENV['DB_NAME'];

$conn = new mysqli($host, $user, $pass, $db);

if ($conn->connect_error) {
    die("เชื่อมต่อฐานข้อมูลล้มเหลว: " . $conn->connect_error);
}

echo "เชื่อมต่อสำเร็จ!";

?>
```
#### ใช้ร่วมกับการตั้งค่าอื่น
- ในโค้ด PHP ให้ใช้ ```$_ENV['ชื่อคีย์']```
- ไม่ต้องแก้ ```php.ini``` เพราะ ```phpdotenv``` จะโหลดค่ามาเป็น __Environment Variables__
- เวลาย้ายเซิร์ฟเวอร์ → เปลี่ยนแค่ไฟล์ ```.env``` ไม่ต้องแก้โค้ด

#### ✅ ข้อดี
- เก็บ ข้อมูลลับ (เช่น DB password, API key, secret token) ไว้นอกไฟล์โค้ด
- ย้ายโปรเจกต์ไปเซิร์ฟเวอร์จริงได้ง่ายมาก
- ใช้ได้กับทุก library ที่รองรับ Environment

---
#### 2. ```phpmailer/phpmailer```

**สำหรับส่งอีเมลผ่าน SMTP**
```bash
bash

php composer.phar require phpmailer/phpmailer
```

__ตัวอย่าง:__
```php
<?php
use PHPMailer\PHPMailer\PHPMailer;

require 'vendor/autoload.php';

$mail = new PHPMailer(true);
$mail->isSMTP();
$mail->Host = 'smtp.gmail.com';
$mail->SMTPAuth = true;
$mail->Username = 'your@gmail.com';
$mail->Password = 'yourpassword';
$mail->SMTPSecure = 'tls';
$mail->Port = 587;

$mail->setFrom('your@gmail.com', 'MyApp');
$mail->addAddress('to@example.com');
$mail->Subject = 'ทดสอบส่งอีเมล';
$mail->Body    = 'Hello from PHPMailer!';

$mail->send();

?>
```

---
#### 3. ```firebase/php-jwt```

**ใช้สร้าง/ตรวจสอบ Token สำหรับ API Authentication**
```bash
bash

php composer.phar require firebase/php-jwt
```

__ตัวอย่าง:__
```php
php

<?php
use Firebase\JWT\JWT;
use Firebase\JWT\Key;

require 'vendor/autoload.php';

$key = "secretkey";
$payload = [
    'iss' => "http://localhost",
    'iat' => time(),
    'exp' => time() + 3600,
    'user_id' => 123
];

// สร้าง Token
$jwt = JWT::encode($payload, $key, 'HS256');
echo "JWT: " . $jwt . "<br>";

// ตรวจสอบ Token
$decoded = JWT::decode($jwt, new Key($key, 'HS256'));
print_r($decoded);

?>
```

---
#### 4. ```guzzlehttp/guzzle```

**HTTP Client สำหรับเรียก API อื่น ๆ**
```bash
bash

php composer.phar require guzzlehttp/guzzle
```

__ตัวอย่าง:__
```php
php

<?php
require 'vendor/autoload.php';

$client = new \GuzzleHttp\Client();
$response = $client->get('https://jsonplaceholder.typicode.com/posts/1');
$data = json_decode($response->getBody(), true);

print_r($data);

?>
```

---
#### 5. ```monolog/monolog```

**ใช้เก็บ Log แทนการ echo → เหมาะกับโปรเจกต์จริง**
```bash
bash

php composer.phar require monolog/monolog
```

__ตัวอย่าง:__
```php
php

<?php
use Monolog\Logger;
use Monolog\Handler\StreamHandler;

require 'vendor/autoload.php';

$log = new Logger('myapp');
$log->pushHandler(new StreamHandler(__DIR__.'/app.log', Logger::WARNING));

$log->warning('มี Warning เกิดขึ้น!');
$log->error('มี Error เกิดขึ้น!');

?>
```

---
## *สรุปแนวทาง

 -  ```illuminate/support```, ```carbon```, ```stringy``` → **ใช้ง่ายกับ string/collection/date**
 -  **เพิ่มเติมที่ควรมีสำหรับโปรเจกต์จริง:**
    - ```.env``` =>  (```vlucas/phpdotenv```)
    - ส่งเมล => (```phpmailer/phpmailer```)
    - Authentication => (```firebase/php-jwt```)
    - API Client =. (```guzzlehttp/guzzle```)
    - Logging => (```monolog/monolog```)