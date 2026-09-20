# E-Commerce-Customer-Analytics-RFM

โปรเจกต์วิเคราะห์ข้อมูลเชิงลึกลูกค้า e-Commerce แบบ End-to-End ตั้งแต่การบริหารจัดการฐานข้อมูลด้วย PostgreSQL, การประมวลผลและทำคำนวณแบ่งกลุ่มลูกค้า (RFM Segmentation) ด้วย Python ไปจนถึงการสร้าง Interactive Dashboard บน Power BI เพื่อสนับสนุนการตัดสินใจทางธุรกิจ

---

## ภาพรวมและวัตถุประสงค์ทางธุรกิจ 
การเข้าใจพฤติกรรมการซื้อซ้ำและการรักษาฐานลูกค้า  มีความสำคัญอย่างมากในธุรกิจ e-Commerce โปรเจกต์นี้จัดทำขึ้นเพื่อแก้ปัญหาการทำการตลาดแบบหว่านแห โดยนำข้อมูลการสั่งซื้อมาวิเคราะห์และจำแนกกลุ่มลูกค้าตามพฤติกรรมจริง

**วัตถุประสงค์หลัก**
* ทำความสะอาดและประมวลผลข้อมูลรายการสั่งซื้อขนาดใหญ่ (100k+ orders)
* จัดกลุ่มลูกค้าด้วยเทคนิค **RFM Analysis** (Recency, Frequency, Monetary) เพื่อจำแนกประเภทลูกค้าออกเป็นกลุ่มชัดเจน (เช่น VIP, At-Risk, Lost Customers)
* พัฒนา **Power BI Dashboard** ให้ผู้บริหารและทีมการตลาดติดตาม KPI ยอดขายและสัดส่วนกลุ่มลูกค้าได้แบบ Interactive
* เสนอแนะกลยุทธ์ทางการตลาดเชิงรุก เพื่อลดอัตราการเลิกใช้บริการ (Churn Rate)

---

## 🛠️ เครื่องมือและเทคโนโลยีที่ใช้ (Tech Stack)
* **Database:** PostgreSQL (การจัดเก็บและคิวรีข้อมูล)
* **Data Processing & Analytics:** Python (`pandas`, `numpy`, `sqlalchemy`)
* **Data Visualization:** Power BI Desktop
* **Dataset Source:** Brazilian E-Commerce Public Dataset by Olist (Kaggle)

---

## 🔄 สรุปขั้นตอนการทำ Data Pipeline (Workflow)
1. **Data Ingestion:** นำเข้าไฟล์ข้อมูล Raw Data เข้าสู่ฐานข้อมูล PostgreSQL
2. **Data Cleaning & Transformation (Python):** 
   * กรองออเดอร์ที่ยกเลิก (Cancelled Orders) ออก และจัดการข้อมูลที่เป็นค่าว่าง (Missing Values)
   * แปลงชนิดข้อมูลวันที่ (Datetime Formatting) เพื่อเตรียมคำนวณพฤติกรรมตามช่วงเวลา
3. **RFM Analytics Processing:**
   * คำนวณค่า **Recency** (จำนวนวันที่ไม่ได้ซื้อ), **Frequency** (ความถี่ในการสั่งซื้อ), และ **Monetary** (ยอดขายรวม) ของลูกค้าแต่ละราย (`customer_unique_id`)
   * ให้คะแนน RFM Score และจัดกลุ่มลูกค้าลงใน `Customer_Segment`
4. **Data Modeling & Visualization (Power BI):**
   * ออกแบบ Data Model แบบ Star Schema และเชื่อมความสัมพันธ์ (Relationships) ระหว่างตาราง
   * สร้าง Visualizations ได้แก่ KPI Cards, Donut Chart (สัดส่วนลูกค้า), และ Line Chart (แนวโน้มยอดขายรายเดือน)

---

## 📊 Insights ที่พบและข้อเสนอแนะทางธุรกิจ

### Insights:
* **กลุ่ม Champions / VIP (~10% ของลูกค้าทั้งหมด): เป็นกลุ่มที่ทำรายได้สูงถึง 30%+ ของยอดขายรวม มีความถี่ในการสั่งซื้อสูงและเพิ่งกลับมาซื้อไม่นาน
* **กลุ่ม At-Risk (~25% ของลูกค้าทั้งหมด): เป็นกลุ่มที่เคยซื้อบ่อยแต่ไม่มีการสั่งซื้อเพิ่มเติมในรอบ 90 วันที่ผ่านมา ถือเป็นสัญญาณเสี่ยงที่จะ Churn
* **แนวโน้มรายได้ (Revenue Seasonality): ยอดขายมีความพุ่งสูงขึ้นชัดเจนในบางช่วงเดือนของปี

### ข้อเสนอแนะเชิงกลยุทธ์ :
* **สำหรับกลุ่ม Champions / VIP: มอบสิทธิพิเศษเฉพาะกลุ่ม หรือสิทธิ์ซื้อสินค้าใหม่ก่อนใคร เพื่อรักษารายได้หลักของบริษัท
* **สำหรับกลุ่ม At-Risk: ทำแคมเปญ Re-engagement ส่งโค้ดส่วนลดแบบจำกัดเวลาผ่าน Email/SMS เพื่อดึงกลับมาก่อนจะกลายเป็น Lost Customers
* **สำหรับกลุ่ม New Customers: มอบคูปองส่วนลดสำหรับการซื้อครั้งที่ 2 ทันทีเพื่อกระตุ้นค่า Frequency ให้กลายมาเป็นลูกค้าประจำ

<img width="1167" height="703" alt="Screenshot 2026-09-20 170702" src="https://github.com/user-attachments/assets/6e312e77-40e6-43a2-9307-998395877881" />
