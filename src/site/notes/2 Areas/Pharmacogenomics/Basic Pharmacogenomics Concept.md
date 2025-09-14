---
{"dg-publish":true,"permalink":"/2-areas/pharmacogenomics/basic-pharmacogenomics-concept/","created":"2023-12-17T15:57:36.055+07:00","updated":"2025-09-14T21:27:39.055+07:00"}
---

## Genome Variation
- Base Variation
	- SNPs
	- Short Indel
- Structural Variation (ส่องกล้อง)
	- CNV
	- Duplication
	- InDel
	- Translocation
	- Inversion

### Terminology
- SNP Loci - Coding Gene
	- Non-synonymous mutation (mutate แล้วได้ไม่เหมือนเดิม)
		- Nonsense mutation มี stop codon ออกมาก่อน
		- Missense mutation ลำดับ amino เปลี่ยน
- Mutation
	- polymorphism ที่พบ < 1% in population
- Variant Name (Reference SNPs) 
	- เป็น ref genome
- (c.4181 G>C)
	- หมายถึงใน coding region ลำดับที่ 4181 มีการเปลี่ยนจาก G เป็น C
- (p.S486T)
	- หมายถึงโปรตีนตำแหน่งที่ 486 จาก S เปลี่ยนเป็น T


## PGx (Pharmacogenomics)
![messageImage_1704945810937.jpg](/img/user/3%20Resources/Attachment/messageImage_1704945810937.jpg)
![634DD809-8D63-4FA4-A891-EFBD6CC4042C copy.jpg](/img/user/3%20Resources/Attachment/634DD809-8D63-4FA4-A891-EFBD6CC4042C%20copy.jpg)
- การตรวจเพื่อการแพทย์หมายถึง
	- เพื่อคัดกรอง hypersensitivity ของคนที่ยังไม่เคยรับยา หรือรับแต่ไม่เกิน 3 เดือน
		- **แพทย์สภาบอกว่า** 2565 ต้องเป็นหมอเฉพาะทาง **แต่ปัจจุบัน 2566 หมอ GP ก็ตรวจได้**
		- สปสช -> B1502, B5801, B5701
		- B1502 ตรวจได้กับทุก indication
		- A3101 ยังไม่รองรับ -> Caucasian, European, Japanese, Korean, African (CBZ: SJS/TEN + DRESS + MPE)
	- TDM
		- PGRN Hub
			- PharmVar
			- CPIC
			- PharmGKB
		- สปสช -> 
			- CYP2C19 - Clopidogrel, Amitriptyline, Nortriptyline, PPI
			- CYP2C9 - Warfarin, Phenytoin, Aspirin, NSAIDs (Celebrex, Piroxicam, Meloxicam)
			- TPMT (HPLC) - 6MP, AZA
	- ดูว่าจะ response ต่อการรักษามั้ย
		- Responder vs Non-Responder
		- ex. HER-2 Gene

A3201 -> vanconycin DRESS // but mostly found in europe

## Precision medicine
>[!note] Always consider other factor, not just genetics (germline genome) -> Pre-counseling สำคัญ
- Genetics
- Lifestyle
- Comedication
- PK PD
- Food, Herbal Supplements
- Gender, Age, Ethnic, Other Risk


## Common Drugs
- CBZ
	- B1502 (OR 137.69) for SJS/TEN
		- การตรวจ 1502 ยังบอก Phenytoin (SCARs)
		- และ Co-trimoxazole (SJS/TEN) *แต่ถ้าจะบอก (DRESS) ต้อง A3101*
	- A3101 จะรวมทั้ง SJS/TEN, Dress และ MPE (Caucasian, European, Japanese, Korean, African)
	- B1521 (Serotype B75) (OR 9.54) ก็เกิดได้ แต่ไม่ต้องเลี่ยง Ox-CBZ / B1508 1511 1521
- Allo
	- B5801 (SCARs) อยู่ในสปสช -> ถ้า pos ไปใช้ febuxostat ได้เลย
	- ไม่ต้องสนเชื้อชาติ
	- ถ้าไม่ตรวจให้ใช้ 100mg/day ก่อน (เพราะ 200mg/day OR = 30)
- ABC
	- B5701 อยู่ในสปสชแล้ว
- Dapsone (SCARs), Phenobarbital, Co-trimoxazole (DRESS)
	- B1301
- DPP-4i
	- DQB1\*03:01


long read sequencing แยกข้างได้
แต่ short read nope

allo conc dependent ถ้าไม่มากพอ มันอาจไม่ได้จับกับ HLA