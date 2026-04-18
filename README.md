# Electricity Demand Forecasting in Southern Thailand
> **Short-term Hourly Load Forecasting using Advanced Time Series Analysis**

โปรเจกต์วิเคราะห์และพยากรณ์ความต้องการใช้ไฟฟ้าในพื้นที่ภาคใต้ของประเทศไทย เพื่อสนับสนุนการวางแผนผลิตไฟฟ้าและการบริหารจัดการโหลดไฟฟ้าให้มีประสิทธิภาพสูงสุด

## 📌 บทสรุปโครงการ (Project Overview)
* **วัตถุประสงค์ (Objective):** เพื่อศึกษาลักษณะรูปแบบการใช้ไฟฟ้า และพัฒนาแบบจำลองพยากรณ์ความต้องการใช้ไฟฟ้าล่วงหน้าในระยะสั้น
* **ปัญหา (Problem):** ระบบไฟฟ้าจำเป็นต้องมีการวางแผนการผลิตให้เพียงพอกับความต้องการ เพื่อรักษาเสถียรภาพและลดความเสี่ยงจากการผลิตไฟฟ้าไม่เพียงพอในช่วง Peak Load
* **ข้อมูล (Data):** ข้อมูลรายชั่วโมง (Hourly) จากการไฟฟ้าฝ่ายผลิตแห่งประเทศไทย (EGAT) ครอบคลุมช่วงเวลา 8 เดือน (มกราคม - สิงหาคม 2023) รวมทั้งสิ้น 5,831 จุดข้อมูล

## 🛠️ เทคนิคและเครื่องมือ (Tech Stack)
* **Tools:** Microsoft Excel, Minitab
* **Statistical Methods:**
    * **Augmented Dickey-Fuller (ADF) Test:** สำหรับทดสอบความนิ่งของข้อมูล (Stationarity)
    * **Decomposition Method:** แยกองค์ประกอบ Trend และ Seasonality
    * **Exponential Smoothing (SES):** สำหรับข้อมูลที่ไม่มีแนวโน้มและฤดูกาล
    * **Holt-Winters Additive Method:** แบบจำลองหลักที่ใช้รองรับทั้งแนวโน้มและฤดูกาลรายวัน
* **Parameters:** กำหนด Seasonal Period (s) = 24 ชั่วโมง เพื่อสะท้อนพฤติกรรมการใช้ไฟฟ้าตามกิจกรรมประจำวัน

## 📊 ขั้นตอนการดำเนินงาน (Methodology)
1. **Exploratory Data Analysis (EDA):** พบแนวโน้ม (Trend) เพิ่มขึ้นเล็กน้อย และฤดูกาลรายวัน (Daily Seasonality) ที่ชัดเจน โดยมีความต้องการใช้ไฟฟ้าสูงสุดในช่วงเวลา 19:00 - 21:00 น.
2. **Data Preprocessing:** ตรวจสอบความครบถ้วนของข้อมูล (Completeness 100%) และแบ่งข้อมูลเป็น Training Set (6 เดือน) และ Test Set (2 เดือน) เพื่อประเมินผล
3. **Model Development:** เปรียบเทียบประสิทธิภาพ 4 แบบจำลอง ได้แก่ Naive, SES, Additive Decomposition และ Holt-Winters
4. **Model Diagnostics:** ตรวจสอบค่า Residuals พบว่าแบบจำลอง Holt-Winters มีคุณสมบัติสอดคล้องกับข้อสมมติทางสถิติและมีความเหมาะสมมากที่สุด

## 🚀 ผลลัพธ์และการนำไปใช้ (Results & Business Impact)
* **Key Result:** แบบจำลอง **Holt-Winters Additive** ให้ค่าความคลาดเคลื่อนต่ำที่สุดและสามารถอธิบายโครงสร้างข้อมูลได้ดีที่สุด
* **Impact:** ช่วยสนับสนุนการตัดสินใจในการวางแผนสำรองไฟฟ้า (Load Management) และลดโอกาสเกิดไฟฟ้าตก/ดับในช่วงที่ความต้องการใช้ไฟฟ้าสูง
* **Performance Metrics (Training Set):**
    * **MAE:** 39.9590
    * **RMSE:** 53.8253
    * **MAPE:** ~30.83% (ในชุดข้อมูลทดสอบ)

---
**Developed by:** Ampika Pratumtong  
**Contact:** Ampika.pratumtong47@gmail.com
