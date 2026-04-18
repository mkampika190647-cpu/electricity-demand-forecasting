# Electricity Demand Forecasting in Southern Thailand
> **Short-term Hourly Load Forecasting using Advanced Time Series Analysis**

[cite_start]โปรเจกต์วิเคราะห์และพยากรณ์ความต้องการใช้ไฟฟ้าในพื้นที่ภาคใต้ของประเทศไทย เพื่อสนับสนุนการวางแผนผลิตไฟฟ้าและการบริหารจัดการโหลดไฟฟ้าให้มีประสิทธิภาพสูงสุด [cite: 21, 29]

## 📌 บทสรุปโครงการ (Project Overview)
* [cite_start]**วัตถุประสงค์ (Objective):** เพื่อศึกษาลักษณะรูปแบบการใช้ไฟฟ้า และพัฒนาแบบจำลองพยากรณ์ความต้องการใช้ไฟฟ้าล่วงหน้าในระยะสั้น [cite: 31, 33]
* [cite_start]**ปัญหา (Problem):** ระบบไฟฟ้าจำเป็นต้องมีการวางแผนการผลิตให้เพียงพอกับความต้องการ เพื่อรักษาเสถียรภาพและลดความเสี่ยงจากการผลิตไฟฟ้าไม่เพียงพอในช่วง Peak Load [cite: 20]
* [cite_start]**ข้อมูล (Data):** ข้อมูลรายชั่วโมง (Hourly) จากการไฟฟ้าฝ่ายผลิตแห่งประเทศไทย (EGAT) ครอบคลุมช่วงเวลา 8 เดือน (มกราคม - สิงหาคม 2023) รวมทั้งสิ้น 5,831 จุดข้อมูล [cite: 26, 54]

## 🛠️ เทคนิคและเครื่องมือ (Tech Stack)
* [cite_start]**Tools:** `Microsoft Excel`, `Minitab` [cite: 36, 462]
* **Statistical Methods:**
    * [cite_start]**Augmented Dickey-Fuller (ADF) Test:** สำหรับทดสอบความนิ่งของข้อมูล (Stationarity) [cite: 210]
    * [cite_start]**Decomposition Method:** แยกองค์ประกอบ Trend และ Seasonality [cite: 231]
    * [cite_start]**Exponential Smoothing (SES):** สำหรับข้อมูลที่ไม่มีแนวโน้มและฤดูกาล [cite: 230]
    * [cite_start]**Holt-Winters Additive Method:** แบบจำลองหลักที่ใช้รองรับทั้งแนวโน้มและฤดูกาลรายวัน [cite: 232, 309]
* [cite_start]**Parameters:** กำหนด Seasonal Period ($s$) = 24 ชั่วโมง เพื่อสะท้อนพฤติกรรมการใช้ไฟฟ้าตามกิจกรรมประจำวัน [cite: 27]

## 📊 ขั้นตอนการดำเนินงาน (Methodology)
1. [cite_start]**Exploratory Data Analysis (EDA):** พบแนวโน้ม (Trend) เพิ่มขึ้นเล็กน้อย และฤดูกาลรายวัน (Daily Seasonality) ที่ชัดเจน โดยมีความต้องการใช้ไฟฟ้าสูงสุดในช่วงเวลา 19:00 - 21:00 น. [cite: 162, 175]
2. [cite_start]**Data Preprocessing:** ตรวจสอบความครบถ้วนของข้อมูล (Completeness 100%) และแบ่งข้อมูลเป็น Training Set (6 เดือน) และ Test Set (2 เดือน) เพื่อประเมินผล [cite: 103, 222, 223]
3. [cite_start]**Model Development:** เปรียบเทียบประสิทธิภาพ 4 แบบจำลอง ได้แก่ Naive, SES, Additive Decomposition และ Holt-Winters [cite: 258]
4. [cite_start]**Model Diagnostics:** ตรวจสอบค่า Residuals พบว่าแบบจำลอง Holt-Winters มีคุณสมบัติเป็น White Noise และมีการแจกแจงแบบปกติ (Normality) มากที่สุด [cite: 350, 361]

## 🚀 ผลลัพธ์และการนำไปใช้ (Results & Business Impact)
* [cite_start]**Key Result:** แบบจำลอง **Holt-Winters Additive** มีความเหมาะสมและแม่นยำที่สุดในการอธิบายโครงสร้างข้อมูลความต้องการใช้ไฟฟ้า [cite: 333, 431]
* [cite_start]**Impact:** ผลการพยากรณ์ช่วยสนับสนุนการตัดสินใจในการวางแผนสำรองไฟฟ้า (Load Management) และลดโอกาสเกิดไฟฟ้าตก/ดับในช่วงที่ความต้องการใช้ไฟฟ้าสูง [cite: 29, 433]
* [cite_start]**Performance Metrics (Training Set):** [cite: 324]
    * **MAE:** 39.9590
    * **RMSE:** 53.8253
    * [cite_start]**MAPE:** ~30.83% (ในชุดข้อมูลทดสอบ จัดอยู่ในระดับความแม่นยำปานกลาง) [cite: 379]
