# Highsociety Shop Online

หน้าร้านออนไลน์ (storefront) สำหรับ HIGHSOCIETY เขียนเป็นไฟล์ HTML/CSS/JS ล้วน ไม่มี build step หรือ framework — เปิดไฟล์ตรงๆ หรือเสิร์ฟผ่าน static file server ได้ทันที

## โครงสร้างไฟล์

| ไฟล์ | หน้าที่ |
|---|---|
| `index.html` | หน้าร้านหลัก — แคตตาล็อกสินค้า (สายพันธุ์/อุปกรณ์), ตะกร้า, checkout, ผูก LINE LIFF |
| `admin.html` | แดชบอร์ดแอดมิน — ยอดขาย, จัดการออเดอร์/สถานะ, ตรวจสลิปโอนเงิน, จัดการสินค้า/สต็อก |
| `profile.html` | หน้าดูประวัติคำสั่งซื้อของลูกค้า (ค้นด้วย LINE userId) |
| `Receipt.html` | เทมเพลตใบเสร็จ — เป็น Google Apps Script HTML template (`<?= ... ?>` scriptlet) ไม่ใช่หน้าเว็บที่เปิดตรงได้ |

## Backend

เว็บนี้ไม่มี backend/database อยู่ในโปรเจกต์นี้ ทุกหน้าเรียก API ผ่าน `APP_URL` ที่ชี้ไปยัง **Google Apps Script Web App** ซึ่งอ่าน/เขียนข้อมูลลง **Google Sheet** — โค้ดฝั่งนั้นไม่ได้ถูก version control ไว้ในที่นี้ การแก้ไข logic ฝั่ง backend (เช่น การตรวจสลิป, การคำนวณสต็อก) ต้องไปแก้ที่ Apps Script project โดยตรง

## หมายเหตุ

- เนื้อหาเป็นภาษาไทยทั้งหมด ยังไม่รองรับหลายภาษา
- ต้องรัน HTTPS/host จริงเพื่อให้ LINE LIFF login ทำงานได้ (LIFF ไม่ทำงานบน `file://`)
