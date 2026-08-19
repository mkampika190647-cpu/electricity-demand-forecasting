# Electricity Demand Forecasting in Southern Thailand

**Time Series Forecasting Project | Electricity Demand · Forecasting · Excel · Statistical Analysis**

## Project Overview

โครงงานนี้เป็นการวิเคราะห์และพยากรณ์ความต้องการใช้ไฟฟ้าในภาคใต้ของประเทศไทย
โดยใช้ข้อมูลความต้องการใช้ไฟฟ้าแบบรายชั่วโมงในช่วงเดือนมกราคม–สิงหาคม 2023

การวิเคราะห์มุ่งศึกษารูปแบบของข้อมูลอนุกรมเวลาและเปรียบเทียบวิธีการพยากรณ์หลายรูปแบบ
เพื่อหาแบบจำลองที่เหมาะสมสำหรับการพยากรณ์ความต้องการใช้ไฟฟ้าในระยะสั้น

ข้อมูลมีลักษณะเป็นรายชั่วโมง และกำหนด Seasonal Period เท่ากับ 24 ชั่วโมง
เพื่อสะท้อนรูปแบบการใช้ไฟฟ้าที่เกิดขึ้นซ้ำในแต่ละวัน

## Objectives

- ศึกษาลักษณะและรูปแบบของความต้องการใช้ไฟฟ้าในภาคใต้
- วิเคราะห์องค์ประกอบและฤดูกาลของข้อมูลอนุกรมเวลา
- เปรียบเทียบประสิทธิภาพของวิธีการพยากรณ์หลายรูปแบบ
- ประเมินความแม่นยำของแบบจำลองด้วยตัวชี้วัดความคลาดเคลื่อน
- เลือกแบบจำลองที่เหมาะสมสำหรับการพยากรณ์ความต้องการใช้ไฟฟ้า

## Dataset

ข้อมูลที่ใช้เป็นข้อมูลความต้องการใช้ไฟฟ้าในภาคใต้ของประเทศไทยแบบรายชั่วโมง

- **Period:** January–August 2023
- **Frequency:** Hourly
- **Observations:** Approximately 5,831 observations
- **Seasonal Period:** 24 hours

สำหรับการประเมินแบบจำลอง ข้อมูลถูกแบ่งออกเป็น

- **Training Data:** 6 months
- **Test Data:** 2 months

## Analysis Workflow

1. เตรียมและตรวจสอบข้อมูลอนุกรมเวลา
2. สำรวจรูปแบบของความต้องการใช้ไฟฟ้า
3. กำหนด Seasonal Period สำหรับข้อมูลรายชั่วโมง
4. แบ่งข้อมูลออกเป็น Training และ Test datasets
5. สร้างแบบจำลองพยากรณ์หลายวิธี
6. เปรียบเทียบค่าพยากรณ์กับข้อมูลจริง
7. ประเมินความแม่นยำของแต่ละแบบจำลอง
8. เลือกแบบจำลองที่เหมาะสมสำหรับการพยากรณ์

## Forecasting Methods

มีการศึกษาและเปรียบเทียบวิธีการพยากรณ์ ได้แก่

- Naive Method
- Simple Exponential Smoothing (SES)
- Additive Decomposition
- Holt-Winters Method

## Model Evaluation

ประเมินประสิทธิภาพของแบบจำลองด้วยตัวชี้วัดความคลาดเคลื่อน เช่น

- MAE — Mean Absolute Error
- RMSE — Root Mean Squared Error
- MAPE — Mean Absolute Percentage Error

การเปรียบเทียบค่าความคลาดเคลื่อนช่วยในการเลือกแบบจำลอง
ที่สามารถพยากรณ์ข้อมูล Test ได้เหมาะสมที่สุด

## Key Findings

จากการเปรียบเทียบแบบจำลอง พบว่า **Holt-Winters Additive**
เป็นวิธีที่เหมาะสมสำหรับการพยากรณ์ข้อมูลความต้องการใช้ไฟฟ้าในชุดข้อมูลที่ศึกษา

ผลการประเมินแบบจำลองประกอบด้วย

- **MAE:** 39.9590
- **RMSE:** 53.8253
- **Test MAPE:** approximately 30.83%

ผลการวิเคราะห์แสดงให้เห็นถึงความสำคัญของการพิจารณารูปแบบฤดูกาล
ในการพยากรณ์ข้อมูลความต้องการใช้ไฟฟ้าแบบรายชั่วโมง

## Skills Demonstrated

- Time Series Analysis
- Time Series Forecasting
- Data Preparation
- Seasonal Pattern Analysis
- Train/Test Data Splitting
- Forecast Model Comparison
- Forecast Accuracy Evaluation
- Statistical Interpretation

## Tools & Technologies

- Microsoft Excel
- Statistical Analysis
- Time Series Forecasting
- Data Visualization

## Project Activities

โปรเจกต์นี้เป็น **งานกลุ่มเชิงวิชาการ** โดยสมาชิกในกลุ่มร่วมกันดำเนินการวิเคราะห์
และจัดทำรายงาน ซึ่งครอบคลุมกิจกรรมดังนี้

- เตรียมและตรวจสอบข้อมูลความต้องการใช้ไฟฟ้า
- สำรวจลักษณะและรูปแบบของข้อมูลอนุกรมเวลา
- แบ่งข้อมูลสำหรับการสร้างและทดสอบแบบจำลอง
- ประยุกต์ใช้วิธีการพยากรณ์หลายรูปแบบ
- เปรียบเทียบประสิทธิภาพของแบบจำลอง
- ประเมินความแม่นยำด้วย MAE, RMSE และ MAPE
- ตีความและสรุปผลการพยากรณ์
- จัดทำรายงานโครงงาน

## Project Report

รายละเอียดเกี่ยวกับข้อมูล วิธีการพยากรณ์ การประเมินแบบจำลอง
และผลการวิเคราะห์สามารถดูได้จากรายงานฉบับเต็ม

[View Full Project Report](Electricity-Demand-Forecasting-Southern-Thailand.pdf)

## Project Structure

```text
electricity-demand-forecasting/
│
├── README.md
└── Electricity-Demand-Forecasting-Southern-Thailand.pdf
```

## Project Type

**Academic Team Project — Time Series Analysis & Forecasting**

โครงงานนี้จัดทำขึ้นเพื่อประยุกต์ใช้เทคนิคการวิเคราะห์อนุกรมเวลา
และการพยากรณ์กับข้อมูลความต้องการใช้ไฟฟ้าจริง
ตั้งแต่การเตรียมข้อมูล การสร้างแบบจำลอง การประเมินความแม่นยำ
จนถึงการตีความและนำเสนอผลการพยากรณ์

> **Note:** Repository นี้จัดทำขึ้นเพื่อการศึกษาและการนำเสนอผลงานใน Portfolio
