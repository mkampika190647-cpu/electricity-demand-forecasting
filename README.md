Electricity Demand Forecasting in Southern Thailand
Short-term Hourly Load Forecasting using Advanced Time Series Analysis
โปรเจกต์วิเคราะห์และพยากรณ์ความต้องการใช้ไฟฟ้าในพื้นที่ภาคใต้ของประเทศไทย เพื่อสนับสนุนการวางแผนผลิตไฟฟ้าและการบริหารจัดการโหลดไฟฟ้าให้มีประสิทธิภาพสูงสุด 

📌 บทสรุปโครงการ (Project Overview)
วัตถุประสงค์ (Objective): เพื่อศึกษาลักษณะและรูปแบบการใช้ไฟฟ้า พร้อมพัฒนาแบบจำลองพยากรณ์ความต้องการใช้ไฟฟ้าล่วงหน้าในระยะสั้น 
ปัญหา (Problem): การจัดการพลังงานต้องการความแม่นยำสูง โดยเฉพาะในช่วงความต้องการใช้สูงสุด (Peak Load) เพื่อรักษาเสถียรภาพของระบบและลดความเสี่ยงจากการผลิตไฟฟ้าไม่เพียงพอ 
ข้อมูล (Data): ข้อมูลรายชั่วโมง (Hourly) จากการไฟฟ้าฝ่ายผลิตแห่งประเทศไทย (EGAT) ครอบคลุมช่วงเวลา 8 เดือน (มกราคม - สิงหาคม 2023) รวม 5,831 จุดข้อมูล 

🛠️ เทคนิคและเครื่องมือ (Tech Stack)Tools: Microsoft Excel, Minitab 
Statistical Methods: * Augmented Dickey-Fuller (ADF) Test สำหรับทดสอบความนิ่งของข้อมูล 
Naive
Decomposition Method (Additive) 
Exponential Smoothing (SES) 
Holt-Winters Additive Method (แบบจำลองหลัก) 
Parameters: Seasonal Period ($s$) = 24 ชั่วโมง เพื่อสะท้อนรูปแบบฤดูกาลรายวัน 

📊 ขั้นตอนการดำเนินงาน (Methodology)
Exploratory Data Analysis (EDA): วิเคราะห์ลักษณะข้อมูล พบแนวโน้ม (Trend) เพิ่มขึ้นเล็กน้อย และฤดูกาลรายวัน (Daily Seasonality) ที่ชัดเจน โดยมี Peak ในช่วง 19:00 - 21:00 น. 
Data Preprocessing: ตรวจสอบความครบถ้วน (Completeness 100%) และแบ่งข้อมูลเป็น Training Set (6 เดือน) และ Test Set (2 เดือนสุดท้าย) 
Model Development: เปรียบเทียบ 4 แบบจำลอง (Naive, SES, Additive Decomposition, Holt-Winters) 
Model Diagnostics: ตรวจสอบคุณสมบัติของ Residuals (White Noise, Normality, Autocorrelation) เพื่อยืนยันความเหมาะสมของแบบจำลอง 

🚀 ผลลัพธ์และการนำไปใช้ (Results & Business Impact)
Key Result: แบบจำลอง Holt-Winters Additive มีความแม่นยำสูงสุดในการอธิบายโครงสร้างข้อมูลที่มีทั้งแนวโน้มและฤดูกาล 
Impact: ช่วยลดความเสี่ยงในการจัดการพลังงานช่วง Peak Load และสนับสนุนการวางแผนสำรองไฟฟ้าล่วงหน้าได้อย่างเป็นระบบ 
Performance Metrics (Training Set): 
MAE: 39.9590
RMSE: 53.8253
MAPE: ~30.83% (ในชุดข้อมูลทดสอบ จัดอยู่ในระดับ Moderate Accuracy
