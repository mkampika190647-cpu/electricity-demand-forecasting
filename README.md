# Electricity Demand Forecasting in Southern Thailand

**Time Series Analysis & Forecasting | Microsoft Excel · Minitab · Statistical Analysis**

โปรเจกต์วิเคราะห์และพยากรณ์ความต้องการใช้ไฟฟ้าในภาคใต้ของประเทศไทย โดยใช้ข้อมูลรายชั่วโมงในช่วงเดือนมกราคม–สิงหาคม 2023 เพื่อศึกษารูปแบบของข้อมูลและเปรียบเทียบวิธีการพยากรณ์อนุกรมเวลา

## Project Overview

ข้อมูลที่ใช้ในโปรเจกต์เป็นข้อมูลความต้องการใช้ไฟฟ้าในภาคใต้แบบรายชั่วโมง โดยเลือกตัวแปร `south_demand` ซึ่งมีหน่วยเป็นเมกะวัตต์ (MW) มาใช้ในการวิเคราะห์แบบ Univariate Time Series

เนื่องจากข้อมูลเป็นรายชั่วโมง จึงกำหนด Seasonal Period เท่ากับ 24 ชั่วโมง เพื่อพิจารณารูปแบบการใช้ไฟฟ้าที่เกิดซ้ำในแต่ละวัน

ข้อมูลถูกแบ่งตามลำดับเวลาเป็น Training Data ช่วงเดือนมกราคม–มิถุนายน และ Test Data ช่วงเดือนกรกฎาคม–สิงหาคม โดยใช้ข้อมูล Training สำหรับสร้างและเปรียบเทียบแบบจำลอง ก่อนนำแบบจำลองที่เลือกไปทดสอบกับข้อมูล Test

## Dataset

- **Period:** January–August 2023
- **Frequency:** Hourly
- **Observations:** Approximately 5,831
- **Target Variable:** `south_demand`
- **Unit:** Megawatt (MW)
- **Seasonal Period:** 24 hours
- **Training Data:** January–June 2023
- **Test Data:** July–August 2023

ข้อมูลมาจากชุดข้อมูล **Thai Power System: Hourly Power Generation, Demand, and Cross-Border Flows** ที่เผยแพร่ผ่าน Zenodo โดยข้อมูลต้นทางรวบรวมจากการไฟฟ้าฝ่ายผลิตแห่งประเทศไทย (EGAT)

## Data Preparation

ก่อนสร้างแบบจำลอง มีการตรวจสอบและเตรียมข้อมูลเบื้องต้น ได้แก่

- ตรวจสอบ Missing Values
- ตรวจสอบข้อมูลซ้ำ
- จัดเรียงข้อมูลตามวันและเวลา
- ตรวจสอบความต่อเนื่องของข้อมูลรายชั่วโมง
- ตรวจสอบค่าผิดปกติด้วย Time Series Plot, Boxplot และ IQR
- กำหนด Datetime เป็นตัวแปรเวลา
- แบ่งข้อมูลออกเป็น Training และ Test Data ตามลำดับเวลา

จากการตรวจสอบไม่พบ Missing Values และข้อมูลมีความต่อเนื่องตามช่วงเวลาที่นำมาวิเคราะห์

## Exploratory Data Analysis

สำรวจลักษณะของข้อมูลด้วยสถิติเชิงพรรณนาและกราฟก่อนนำไปสร้างแบบจำลอง

ค่าความต้องการใช้ไฟฟ้าโดยเฉลี่ยอยู่ที่ประมาณ **2,105.88 MW** โดยมีค่าต่ำสุดประมาณ **1,363.20 MW** และค่าสูงสุดประมาณ **2,787.20 MW**

จาก Time Series Plot พบว่าความต้องการใช้ไฟฟ้ามีการเปลี่ยนแปลงตามเวลา และมีรูปแบบที่เกิดซ้ำในแต่ละวัน

### Daily Seasonality

เมื่อพิจารณาค่าเฉลี่ยของความต้องการใช้ไฟฟ้าในแต่ละชั่วโมง พบรูปแบบฤดูกาลรายวัน (Daily Seasonality)

ความต้องการใช้ไฟฟ้าค่อนข้างต่ำในช่วงประมาณ **04.00–06.00 น.** จากนั้นเพิ่มขึ้นในช่วงกลางวัน และอยู่ในระดับสูงช่วงประมาณ **19.00–21.00 น.**

จึงกำหนด Seasonal Period เท่ากับ **24 ชั่วโมง** สำหรับการวิเคราะห์รูปแบบรายวัน

## Stationarity Test

ตรวจสอบความนิ่งของข้อมูล Training ด้วย **Augmented Dickey-Fuller (ADF) Test**

ผลการทดสอบได้

- **ADF Statistic:** -4.169
- **Critical Value (5%):** -2.862

ค่า ADF Statistic มีค่าน้อยกว่า Critical Value ที่ระดับนัยสำคัญ 0.05 จึงปฏิเสธสมมติฐานหลักของ ADF Test และสรุปว่าข้อมูล Training มีลักษณะ Stationary ที่ระดับนัยสำคัญ 0.05

## Forecasting Methods

แบบจำลองที่นำมาศึกษาและเปรียบเทียบ ได้แก่

- Naive Method
- Simple Exponential Smoothing (SES)
- Additive Decomposition
- Holt-Winters Additive

แบบจำลองทั้ง 4 วิธีถูกสร้างและเปรียบเทียบจากข้อมูล Training โดยพิจารณาค่าความคลาดเคลื่อนของแต่ละวิธี จากนั้นเลือกแบบจำลองที่ให้ผลดีที่สุดไปประเมินต่อกับข้อมูล Test

## Model Evaluation

ใช้ตัวชี้วัดความคลาดเคลื่อนในการเปรียบเทียบแบบจำลอง ได้แก่

- **MAE** — Mean Absolute Error
- **MSE** — Mean Squared Error
- **RMSE** — Root Mean Squared Error
- **MAPE** — Mean Absolute Percentage Error

แบบจำลองที่มีค่าความคลาดเคลื่อนต่ำกว่าจะถูกพิจารณาเปรียบเทียบกับแบบจำลองอื่นใน Training Set ก่อนเลือกไปทดสอบกับข้อมูลที่ไม่ได้ใช้สร้างแบบจำลอง

## Model Comparison — Training Set

ผลการเปรียบเทียบแบบจำลองจาก Training Set มีดังนี้

| Model | MAE | MSE | RMSE |
|---|---:|---:|---:|
| Naive | 82.1094 | 12,276.4993 | 110.7993 |
| SES | 152.0060 | 32,271.0400 | 179.6414 |
| Holt-Winters Additive | **39.9590** | **2,897.1670** | **53.8253** |
| Additive Decomposition | 173.3470 | 45,231.0636 | 212.6760 |

จากผลบน Training Set พบว่า **Holt-Winters Additive** มีค่า MAE, MSE และ RMSE ต่ำที่สุดในกลุ่มแบบจำลองที่นำมาเปรียบเทียบ จึงเลือกแบบจำลองนี้ไปประเมินต่อกับ Test Set

## Test Set Evaluation

เมื่อนำ Holt-Winters Additive ไปประเมินกับข้อมูล Test ได้ผลดังนี้

| Metric | Result |
|---|---:|
| MAE | 647.8491 |
| MSE | 547,074.105 |
| RMSE | 739.6446 |
| MAPE | 30.8287% |

ผลบน Test Set มีค่าความคลาดเคลื่อนสูงกว่าที่พบใน Training Set แสดงให้เห็นว่าแม้ Holt-Winters Additive จะให้ผลดีที่สุดในกลุ่มแบบจำลองที่นำมาเปรียบเทียบ แต่ความแม่นยำลดลงเมื่อนำไปพยากรณ์ข้อมูลช่วงที่ไม่ได้ใช้ในการสร้างแบบจำลอง

## Key Findings

จากการวิเคราะห์พบว่าข้อมูลความต้องการใช้ไฟฟ้ามีรูปแบบรายวันที่เห็นได้ชัด โดยความต้องการใช้ไฟฟ้าต่ำในช่วงเช้ามืดและเพิ่มขึ้นในช่วงกลางวันจนถึงช่วงค่ำ

ในการเปรียบเทียบแบบจำลองบน Training Set พบว่า **Holt-Winters Additive** ให้ค่าความคลาดเคลื่อนต่ำที่สุด จึงถูกเลือกไปทดสอบกับข้อมูล Test

อย่างไรก็ตาม เมื่อทดสอบกับข้อมูล Test ได้ค่า MAPE ประมาณ **30.83%** ซึ่งแสดงว่าแบบจำลองยังมีข้อจำกัดในการพยากรณ์ข้อมูลนอกช่วงที่ใช้สร้างโมเดล

## Limitations

โปรเจกต์นี้เป็นการวิเคราะห์แบบ **Univariate Time Series** โดยใช้ `south_demand` เป็นตัวแปรหลักเพียงตัวเดียว จึงยังไม่ได้รวมปัจจัยภายนอกที่อาจเกี่ยวข้องกับความต้องการใช้ไฟฟ้า เช่น

- อุณหภูมิและสภาพอากาศ
- วันหยุด
- กิจกรรมทางเศรษฐกิจ
- เหตุการณ์พิเศษในแต่ละช่วงเวลา

นอกจากนี้ ข้อมูลที่ใช้ครอบคลุมระยะเวลา 8 เดือน จึงสามารถศึกษารูปแบบรายวันและใช้สำหรับการพยากรณ์ระยะสั้นในขอบเขตของข้อมูลชุดนี้ แต่ยังไม่ครอบคลุมรูปแบบฤดูกาลในระดับรายปี

## Skills Demonstrated

- Time Series Analysis
- Time Series Forecasting
- Exploratory Data Analysis
- Data Preparation
- Stationarity Testing
- Seasonal Pattern Analysis
- Train/Test Data Splitting
- Forecast Model Comparison
- Forecast Accuracy Evaluation
- Statistical Interpretation
- Data Visualization

## Tools & Technologies

- Microsoft Excel
- Minitab

## Project Activities

โปรเจกต์นี้เป็น **Academic Team Project** โดยสมาชิกในกลุ่มร่วมกันวิเคราะห์ข้อมูลและจัดทำรายงาน ตั้งแต่การเตรียมและสำรวจข้อมูล การสร้างแบบจำลอง การเปรียบเทียบผล ไปจนถึงการประเมินและสรุปผลการพยากรณ์

## Project Report

รายละเอียดของข้อมูล ขั้นตอนการวิเคราะห์ วิธีการพยากรณ์ และผลการประเมินแบบจำลองสามารถดูได้จากรายงานฉบับเต็ม

[View Full Project Report](Electricity-Demand-Forecasting-Southern-Thailand.pdf)

## Project Structure

```text
electricity-demand-forecasting/
│
├── README.md
└── Electricity-Demand-Forecasting-Southern-Thailand.pdf




## Project Type
**Academic Team Project — Time Series Analysis & Forecasting**

โปรเจกต์นี้จัดทำขึ้นเพื่อประยุกต์ใช้การวิเคราะห์อนุกรมเวลากับข้อมูลความต้องการใช้ไฟฟ้า ตั้งแต่การเตรียมและสำรวจข้อมูล การสร้างและเปรียบเทียบแบบจำลอง ไปจนถึงการประเมินผลด้วย Training Set และ Test Set

> **Note:** Repository นี้จัดทำขึ้นเพื่อการศึกษาและการนำเสนอผลงานใน Portfolio
