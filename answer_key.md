# Invoice Inputs and Extracted JSON Outputs 

Compiled from the second invoice input onward. Each section contains the invoice content as provided and the corresponding JSON extraction. 

## **Invoice 1 – TechNova Solutions Pvt Ltd** 

### **Input – Invoice content provided** 

Subject: INV-778 | Monthly IT Maintenance Bill 

Dear Finance Department, 

Please process our service invoice. 

Vendor Name: TechNova Solutions Pvt Ltd Invoice Reference: TN-778/26 Date of Invoice: 18/10/2026 

GST Registration: 29AABCT7788K1Z2 

Description: Computer AMC and IT support services. 

Taxable Amount: 42,000 CGST: 3,780 SGST: 3,780 Total Payable: Rs. 49,560 

Payment due on: 05 November 2026. 

Thank you. **Output – Extracted JSON response** { "vendor": "TechNova Solutions Pvt Ltd", "invoice_no": "TN-778/26", "invoice_date": "2026-10-18", "gstin": "29AABCT7788K1Z2", "description": "Computer AMC and IT support services", "taxable_amount": 42000, "cgst": 3780, "sgst": 3780, "total_payable": 49560, "due_date": "2026-11-05" } 

Invoice extraction examples 

## **Invoice 2 – Venkateswara Electricals** 

### **Input – Invoice content provided** 

Subject: Payment Pending – Invoice Attached Details 

Hello Sir, 

Sharing the invoice details for the electrical materials delivered to your Hyderabad branch. 

Vendor: Venkateswara Electricals Bill No: VE/091/2026 GSTIN: 36AAEFV9988L1Z8 

Material value: 18,750 GST: 3,375 Net invoice amount: 22,125 

Please clear this bill by 12-11-2026. 

Thanks, Venkateswara Electricals 

**Output – Extracted JSON response** { "vendor": "Venkateswara Electricals", "invoice_no": "VE/091/2026", "invoice_date": null, "gstin": "36AAEFV9988L1Z8", "description": "Electrical materials delivered to Hyderabad branch", "material_value": 18750, "gst": 3375, "net_invoice_amount": 22125, "due_date": "2026-11-12" } 

## **Invoice 3 – Annapurna Corporate Caterers** 

**Input – Invoice content provided** 

Subject: Invoice for Corporate Catering Services 

Dear Accounts, 

Please find our billing information. 

Vendor: Annapurna Corporate Caterers Invoice No: ACC-2026-441 Invoice Date: 22 October 2026 

Invoice extraction examples 

###### GSTIN: 36AACCA4567M1Z3 

Service: Corporate lunch arrangements for 120 employees. 

Food and service charges: ₹36,000 CGST: ₹900 SGST: ₹900 

Total Amount: ₹37,800 

Payment deadline: 07 November 2026. 

Regards, Billing Department 

### **Output – Extracted JSON response** 

{ "vendor": "Annapurna Corporate Caterers", "invoice_no": "ACC-2026-441", "invoice_date": "2026-10-22", "gstin": "36AACCA4567M1Z3", "service_description": "Corporate lunch arrangements for 120 employees", "food_and_service_charges": 36000, "cgst": 900, "sgst": 900, "total_amount": 37800, "due_date": "2026-11-07" } 

## **Invoice 4 – Sri Durga Packaging Industries** 

### **Input – Invoice content provided** 

SRI DURGA PACKAGING INDUSTRIES 

TAX INVOICE 

Field 

Details 

Vendor Name 

Sri Durga Packaging Industries 

Invoice No 

SDPI/260/26 

Invoice extraction examples 

Invoice Date 

24/10/2026 GSTIN 

36AABFS1122C1Z6 

Due Date 08/11/2026 Description Amount Corrugated Boxes 15,000 Packing Material 7,500 GST (18%) 4,050 Total 26,550 Amount payable: INR 26,550 only. **Output – Extracted JSON response** { "vendor": "Sri Durga Packaging Industries", "invoice_no": "SDPI/260/26", "invoice_date": "2026-10-24", "gstin": "36AABFS1122C1Z6", "due_date": "2026-11-08", "items": [ { "description": "Corrugated Boxes", "amount": 15000 }, { "description": "Packing Material", "amount": 7500 

Invoice extraction examples 

} ], "gst_rate": 18, "gst_amount": 4050, "total": 26550, "amount_payable": 26550, "currency": "INR" } 

## **Invoice 5 – BlueWave Office Furniture** 

**Input – Invoice content provided** 

BLUEWAVE OFFICE FURNITURE 

INVOICE / BILL 

Particulars 

Value Name 

BlueWave Office Furniture 

Bill Number BW-2026-092 

GSTIN 

27AAEFB6722R1Z4 

Invoice Date 25/10/2026 Payment Date 

10/11/2026 Item Qty Total 

Office Chairs 

Invoice extraction examples 

10 32,000 Work Desks 

4 28,000 GST 

- 10,800 Grand Total 70,800 

Please make payment within the mentioned period. 

**Output – Extracted JSON response** { "vendor": "BlueWave Office Furniture", "invoice_no": "BW-2026-092", "gstin": "27AAEFB6722R1Z4", "invoice_date": "2026-10-25", "payment_date": "2026-11-10", "items": [ { "description": "Office Chairs", "quantity": 10, "amount": 32000 }, { "description": "Work Desks", "quantity": 4, "amount": 28000 } ], "gst_amount": 10800, "grand_total": 70800, "currency": "INR" } 

Invoice extraction examples 

## **Invoice 6 – Rajesh Industrial Tools** 

### **Input – Invoice content provided** 

RAJESH INDUSTRIAL TOOLS 

SALES INVOICE 

Details Information Supplier Name Rajesh Industrial Tools Invoice Number RIT/556/2026 Invoice Date GSTIN 36AAGPR2233D1Z9 

Amount ₹15,340 Due Date Products supplied: Drill Machine, Safety Gloves, Cutting Discs. 

Total payable including taxes: Rs. 15,340. **Output – Extracted JSON response** { "vendor": "Rajesh Industrial Tools", "invoice_no": "RIT/556/2026", "invoice_date": null, "gstin": "36AAGPR2233D1Z9", "products": [ "Drill Machine", "Safety Gloves", "Cutting Discs" ], "amount": 15340, "total_payable_including_taxes": 15340, 

Invoice extraction examples 

"due_date": null, "currency": "INR" } 

## **Invoice 7 – Sri Sai Transport Services** 

### **Input – Invoice content provided** 

SRI SAI TRANSPORT SERVICES HYDERABAD TELANGANA 

tax invoice no SST/2026/319 

invoice date 26-10-2026 

GST No: 36AABSS5566P1Z1 

Transport charges for goods delivery Hyderabad to Vijayawada freight charges ......... 12000.00 loading/unloading ....... 2000.00 tax amount .............. 2520.00 

TOTAL AMOUNT PAYABLE = Rs. 16520/- 

DUE ON : 09-11-2026 

**Output – Extracted JSON response** { "vendor": "Sri Sai Transport Services", "address": "Hyderabad, Telangana", "invoice_no": "SST/2026/319", "invoice_date": "2026-10-26", "gstin": "36AABSS5566P1Z1", "description": "Transport charges for goods delivery", "transport_route": "Hyderabad to Vijayawada", "freight_charges": 12000, "loading_unloading_charges": 2000, "tax_amount": 2520, "total_amount_payable": 16520, "due_date": "2026-11-09", "currency": "INR" } 

Invoice extraction examples 

## **Invoice 8 – Mahalakshmi Hardware & Paints** 

### **Input – Invoice content provided** 

Mahalakshmi Hardware & Paints Kukatpally, Hyderabad 

BILL / TAX INVOICE 

Vendor : Mahalakshmi Hardware & Paints 

Inv No: MHP/2026/118 Date : 27 October 2026 

GSTIN : 36AAKFM8877H1Z4 

Description: Paint buckets, wall primer, brushes and rollers. 

Amount before tax: 9,500 CGST 9% : 855 SGST 9% : 855 

NET TOTAL : Rs. 11,210 

Payment should be completed on or before 15 November 2026. 

**Output – Extracted JSON response** { "vendor": "Mahalakshmi Hardware & Paints", "address": "Kukatpally, Hyderabad", "invoice_no": "MHP/2026/118", "invoice_date": "2026-10-27", "gstin": "36AAKFM8877H1Z4", "description": "Paint buckets, wall primer, brushes and rollers", "amount_before_tax": 9500, "cgst_rate": 9, "cgst_amount": 855, "sgst_rate": 9, "sgst_amount": 855, "net_total": 11210, "due_date": "2026-11-15", "currency": "INR" } 

Invoice extraction examples 

## **Invoice 9 – Vardhan Digital Services** 

### **Input – Invoice content provided** 

VARDHAN DIGITAL SERVICES HYDERABAD 

INVOICE COPY 

Supplier name : Vardhan Digital Services GSTIN : 36AABCV7788N1Z5 

Invoice ref no : VDS/448/26 Software installation and configuration Annual software support charges 

Service charges = 28,000.00 CGST = 2,520.00 SGST = 2,520.00 

AMOUNT TOTAL : 33,040.00 Payment terms : Net 15 days Bank details partially visible Authorized signature present 

**Output – Extracted JSON response** { "vendor": "Vardhan Digital Services", "address": "Hyderabad", "gstin": "36AABCV7788N1Z5", "invoice_no": "VDS/448/26", "invoice_date": null, "description": [ "Software installation and configuration", "Annual software support charges" ], "service_charges": 28000, "cgst": 2520, "sgst": 2520, "total_amount": 33040, "payment_terms": "Net 15 days", "due_date": null, "bank_details": "Partially visible", "authorized_signature": true, 

Invoice extraction examples 

"currency": "INR" } 

## **Invoice 10 – Blue Frost Cooling Services** 

### **Input – Invoice content provided** 

From: accounts@bluefrostcooling.in To: ap@meridiancomponents.in Date: Tue, 6 Oct 2026 11:42 AM Subject: Invoice BFC/25-26/0418 - AMC Renewal HVAC - Plant 1100 

Dear Sir/Madam, 

Greetings from Blue Frost Cooling Services. 

Please find below our invoice for the renewal of Annual Maintenance Contract for 6 nos. HVAC units (Plant 1100) for the period 01-Oct-2026 to 30-Sep-2027. 

Invoice No   : BFC/25-26/0418 Invoice Date : 06-Oct-2026 AMC Charges  : Rs. 1,85,000.00 CGST @ 9%    : Rs.    16,650.00 SGST @ 9%    : Rs.    16,650.00 TOTAL        : Rs. 2,18,300.00 

SAC: 998719 Our GSTIN: 36AAKFB2290M1ZQ | PAN: AAKFB2290M Bank: HDFC Bank, A/c 50200012345678, IFSC HDFC0001234 

Kindly release payment within 30 days. 

Regards, Suresh Reddy Blue Frost Cooling Services, Kukatpally, Hyderabad 

### **Output – Extracted JSON response** 

{ "vendor": "Blue Frost Cooling Services", "address": "Kukatpally, Hyderabad", "invoice_no": "BFC/25-26/0418", "invoice_date": "2026-10-06", "gstin": "36AAKFB2290M1ZQ", "pan": "AAKFB2290M", "description": "Annual Maintenance Contract renewal for 6 HVAC units", "plant": "1100", "service_period": { "start_date": "2026-10-01", 

Invoice extraction examples 

"end_date": "2027-09-30" }, "amc_charges": 185000, "cgst_rate": 9, "cgst_amount": 16650, "sgst_rate": 9, "sgst_amount": 16650, "sac": "998719", "total_amount": 218300, "payment_terms": "Within 30 days", "due_date": null, "bank_details": { "bank_name": "HDFC Bank", "account_number": "50200012345678", "ifsc": "HDFC0001234" }, "currency": "INR" } 

**Invoice 11 – Sri Sai Transport Services (Repeat Invoice)** 

### **Input – Invoice content provided** 

SRI SAI TRANSPORT SERVICES HYDERABAD TELANGANA 

tax invoice no SST/2026/319 

invoice date 26-10-2026 

GST No: 36AABSS5566P1Z1 

Transport charges for goods delivery Hyderabad to Vijayawada 

freight charges ......... 12000.00 loading/unloading ....... 2000.00 tax amount .............. 2520.00 

TOTAL AMOUNT PAYABLE = Rs. 16520/- 

DUE ON : 09-11-2026 

### **Output – Extracted JSON response** 

{ "vendor": "Sri Sai Transport Services", "address": "Hyderabad, Telangana", "invoice_no": "SST/2026/319", "invoice_date": "2026-10-26", 

Invoice extraction examples 

"gstin": "36AABSS5566P1Z1", "description": "Transport charges for goods delivery", "transport_route": "Hyderabad to Vijayawada", "freight_charges": 12000, "loading_unloading_charges": 2000, "tax_amount": 2520, "total_amount_payable": 16520, "due_date": "2026-11-09", "currency": "INR" } 

## THE PROMPTS I TRIED FOR FINALLY GETTING THIS: 

#### Prompt-1 

You are an expert Invoice Data Extraction and JSON Conversion Assistant. Your task is to convert any invoice provided in normal, unstructured, messy, email, scanned-text, or table format into clean, structured JSON. Automatically identify and extract the following fields: vendor, invoice_no, gstin, amount, and due_date. Follow the exact JSON structure shown in the example. Ensure that the amount is a numeric value without currency symbols or commas, and dates follow the YYYY-MM-DD format. If a field is missing, unclear, or unavailable, assign its value as null. Never guess, assume, or generate missing information. If multiple dates appear, identify the correct invoice due date rather than confusing it with the invoice date or other dates. Ignore irrelevant invoice content. **Output Rules:** Return valid JSON only, without explanations, introductory text, Markdown code blocks, or additional fields. If multiple invoices are provided, return a separate JSON object for each invoice inside a JSON array. 

##### **Expected Output Format:** 

{ 

"vendor": "Sri Lakshmi Traders", "invoice_no": "INV-2291", "gstin": "36ABCDE1234F1Z5", "amount": 48500, "due_date": "2026-11-11" } 

#### Prompt-2: 

You are an expert Invoice Data Extraction and JSON Conversion Assistant. Your task is to convert any invoice provided in normal, unstructured, messy, email, scanned-text, or table format into clean, structured JSON. Automatically identify and extract the fields from the invoice provided into JSON. Take the JSON structure shown in the example as reference doesnt mean only those fields in example if there are any in invoice provide them. Ensure that the amount is a numeric value without currency symbols or commas, and dates follow the YYYY-MM-DD format. If a field is missing, unclear, or unavailable, assign its value as null and give in the JSON and never miss any fields. Never guess, assume, or generate missing information. If multiple dates appear, identify the correct invoice due date rather than confusing it with the invoice date or other dates. if there are any fields with any values provide them in json. **Output Rules:** Return valid JSON only, without 

Invoice extraction examples 

explanations, introductory text, Markdown code blocks, or additional fields. If multiple invoices are provided, return a separate JSON object for each invoice inside a JSON array. 

**Expected Output Format:** { 

"vendor": "Sri Lakshmi Traders", "invoice_no": "INV-2291", "gstin": "36ABCDE1234F1Z5", "amount": 48500, "due_date": "2026-11-11" } 

#### Prompt-3(Final Prompt): 

You are an expert Invoice Data Extraction Assistant. Convert the invoice content provided by the user into structured JSON, regardless of whether it is in normal, messy, email, scanned-text, or table format. Extract all available fields and their values directly from the actual invoice content, including vendor name, invoice number, invoice date, GSTIN, amount, due date, tax details, address, and any other invoice-related information. Do not restrict extraction to the example fields. **Ignore email subjects, sender details, recipient details, email headers, greetings, and unrelated email content.** Only extract information that belongs to the actual invoice. Do not treat an email subject as an invoice field unless the same information is confirmed within the invoice content. Preserve all available invoice fields without missing any. If a field is missing or unclear, use null. Never guess or assume values. Keep amounts numeric without currency symbols or commas, and format dates as YYYY-MM-DD. Return valid JSON only, with no explanations, comments, or Markdown formatting. If multiple invoices are provided, return each as a separate JSON object inside an array. 

Example format: { "vendor": "Sri Lakshmi Traders", "invoice_no": "INV-2291", "gstin": "36ABCDE1234F1Z5", "amount": 48500, "due_date": "2026-11-11" } 

Invoice extraction examples 

