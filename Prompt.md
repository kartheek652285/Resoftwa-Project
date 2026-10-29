**BAD PROMPTS TO IMPROVED VERSIONS AND RESPONSES**

**Prompt1:**  
write email tell your manager your transport will be 1 day late.

**Response:**

**R-1**

Subject: Transport Delayed by One Day

Hi \[Manager's Name\],

I wanted to let you know that the transport for \[shipment/order/item\] will arrive one day later than planned. The new expected arrival is \[new date\].

I'm keeping in touch with the transport team and will update you right away if anything else changes. Please let me know if this delay affects any of your plans and I'll help work out a solution.

Thanks for your understanding.

Best regards,

\[Your Name\]

**R-2**

Subject: Update: Transport Will Be 1 Day Late

Hi \[Manager's Name\],

I'm writing to flag a delay with the transport for \[shipment/order/item\]. It is now expected to arrive on \[new date\], one day later than the original date of \[original date\].

The delay is due to \[reason, e.g., a vehicle issue / weather / customs / carrier scheduling\]. I've already \[action taken, e.g., confirmed the revised schedule with the carrier\], and I'll keep following up to make sure there are no further slips.

If this impacts any downstream work or commitments, I can coordinate with the relevant teams to adjust. Happy to discuss whenever suits you.

Regards,

\[Your Name\]

I've drafted two versions: a short, direct one, and a longer one that includes the reason for the delay and what you're doing about it. Fill in the bracketed details (manager's name, shipment, dates, reason) before sending. If you tell me the specifics, I can finalize it for you.

**Improved Version prompt:**

You are an experienced business communication writer. Write a short, professional email from me to my manager informing them that our transport shipment will arrive one day later than planned. The shipment was originally due on 29/10/2026 and will now arrive on 05/11/2026 because of a delay at the carrier's end. Briefly mention any impact on our work and what I'm doing to manage it, and offer to share updates as I get them. Keep the tone polite, calm, and confident, similar to this: "Hi Priya, a quick heads-up that the delivery scheduled for Monday will now arrive on Tuesday due to a carrier delay. I'll keep you posted and make sure the team is ready." Give me a subject line followed by a body of no more than 100 words. Don't over-apologize, don't blame anyone, and don't invent details I haven't provided; use placeholders for anything missing.

**Response:**

Subject: Heads-up: Shipment Now Arriving 05/11/2026

Hi \[Manager's Name\],

A quick heads-up that our transport shipment, originally due on 29/10/2026, will now arrive on 05/11/2026 due to a delay at the carrier's end.

The main impact is \[brief impact, e.g., on a specific task, deadline, or team schedule\]. To manage this, I'm \[action, e.g., adjusting the schedule / confirming the revised arrival with the carrier / preparing the team\].

I'll share updates as soon as I receive them. Please let me know if you'd like me to cover anything else.

Best regards,

\[Your Name\]

**The improvements I made are:**

The bad prompt is “write email tell your manager your transport will be 1 day late,” only had a rough task and nothing else. In the new version, I added a role by telling Claude to act as an experienced business communication writer, so the email sounds professional. The task was made clearer: a short email from me to my manager about a shipment arriving one day later than planned. Context was added through the original date, new date and reason placeholders, plus the impact on the work and what I am doing about it, so the email reads as complete instead of generic. The example is the sample message to “Priya,” which shows the tone and length I needed. For the format, I asked for a subject line followed by a body of no more than 100 words. The constraints are to stay polite and confident, not over-apologize, not blame anyone, and not invent details that isn’t given, using placeholders instead.

**Prompt 2:**

explain this code  
REPORT zkn\_flight\_alv\_demo.

TABLES: sflight.

SELECT-OPTIONS: s\_carrid FOR sflight-carrid.

DATA: gt\_flights TYPE STANDARD TABLE OF sflight,  
go\_alv TYPE REF TO cl\_salv\_table.

START-OF-SELECTION.  
SELECT \* FROM sflight  
INTO TABLE gt\_flights  
WHERE carrid IN s\_carrid  
ORDER BY carrid, connid, fldate.

IF sy-subrc <> 0.  
MESSAGE 'No flights found for the selection' TYPE 'S' DISPLAY LIKE 'E'.  
RETURN.  
ENDIF.

cl\_salv\_table=>factory( IMPORTING r\_salv\_table = go\_alv  
CHANGING t\_table = gt\_flights ).  
go\_alv->get\_functions( )->set\_all( abap\_true ).  
go\_alv->display( ).

**Response:**

This is a small ABAP report that lets the user filter flights by airline and shows the results in a standard interactive grid (ALV).

**Declarations**

*   REPORT zkn\_flight\_alv\_demo. names the program. The Z prefix marks it as a custom program.
*   TABLES: sflight. creates a work area with the structure of the SAP demo table SFLIGHT (flight data). It's mainly needed here so SELECT-OPTIONS can refer to a table field.
*   SELECT-OPTIONS: s\_carrid FOR sflight-carrid. creates a selection screen field where the user can enter airline codes as single values, ranges, or exclusions. Internally, s\_carrid is a range table.
*   gt\_flights is an internal table with the same row structure as SFLIGHT. It holds the data read from the database.
*   go\_alv is a reference to the ALV class CL\_SALV\_TABLE.

**Processing, under START-OF-SELECTION**

1.  The SELECT reads all columns of SFLIGHT into gt\_flights. WHERE carrid IN s\_carrid applies whatever the user entered on the selection screen, and ORDER BY sorts by airline, connection number, then flight date.
2.  IF sy-subrc <> 0 checks whether anything was found. If not, it shows a status message ("No flights found..."). TYPE 'S' DISPLAY LIKE 'E' makes it a success-type message that looks like an error, so the user sees it in red without being kicked out of the selection screen. RETURN then ends the program.
3.  cl\_salv\_table=>factory(...) builds the ALV object go\_alv from the data in gt\_flights.
4.  go\_alv->get\_functions( )->set\_all( abap\_true ) switches on the standard toolbar functions, such as sort, filter, and export.
5.  go\_alv->display( ) shows the grid.

**Things worth knowing**

*   SELECT \* fetches every column. In real programs it's better to select only the columns you need.
*   The TABLES statement is considered obsolete in modern ABAP. Declaring s\_carrid with a DATA variable of the right type and FOR would be cleaner.
*   The CHANGING t\_table parameter passes the table by reference, so the ALV displays the same data in gt\_flights. The factory call also isn't wrapped in TRY ... CATCH cx\_salv\_msg, which production code would normally do.

I can also rewrite it in a more modern style (inline declarations, a column list, error handling) if you'd like.

**Improved Version:**

This program lets the user pick one or more airlines, reads their flights from the SFLIGHT table, and shows them in an interactive ALV grid. If nothing matches, it shows a short message and stops.

1.  **Selection screen:** SELECT-OPTIONS s\_carrid FOR sflight-carrid creates a selection field where the user can enter one or more airline codes, or ranges. TABLES: sflight is needed so this statement can refer to the table’s field.
2.  **Data declarations:** gt\_flights is an internal table (like a list of rows) shaped like SFLIGHT. go\_alv is an object reference that will hold the ALV grid.
3.  **SELECT:** After START-OF-SELECTION, the program reads matching rows from SFLIGHT into gt\_flights. WHERE carrid IN s\_carrid applies the user’s entries, and ORDER BY sorts the result by airline, connection, and date.
4.  **Error handling:** sy-subrc is the system’s return code, and anything other than 0 means no rows were found. The program then shows the message “No flights found for the selection” in red, and RETURN ends it.
5.  **ALV setup:** cl\_salv\_table=>factory builds the grid from gt\_flights. set\_all( abap\_true ) turns on the standard toolbar buttons (sort, filter, export), and display( ) shows it.

**What the user sees:** a selection screen first, then a sortable, filterable grid of flights.

One real improvement: SELECT \* pulls every column, so selecting only what you need is better on large tables.

**The improvements I made are:**

The bad prompt, “explain this code” with the code pasted, left Claude guessing who the explanation was for and how deep to go. In the new version, the role is a senior SAP ABAP developer mentoring a junior colleague, which sets the expertise and teaching style. The task is to explain the report that reads flight data from SFLIGHT and shows it in an ALV grid. Context comes from describing the reader as someone who knows basic programming but is new to ABAP, and from stating what the program does. The example is the sentence about SELECT-OPTIONS, which shows the simple, plain-language style for each part. For the format, I asked for a two-sentence summary first, then a short-numbered walkthrough of each block, and finally one line on what the user sees when the report runs. The constraints are to keep the answer under 300 words, not rewrite or change the code, and mention improvements like avoiding SELECT \* only if they really matter.

**Prompt 3:**

give test data for table ZEMPLOYEE

**Response:**

I don’t know the structure of your ZEMPLOYEE table, so I’ve assumed common fields. If yours differ, send me the field list and I’ll adjust it.

**Assumed fields:** EMP\_ID, FIRST\_NAME, LAST\_NAME, DEPARTMENT, DESIGNATION, JOIN\_DATE, SALARY, CURRENCY (plus MANDT, which ABAP fills in automatically).

| EMP_ID | FIRST_NAME | LAST_NAME | DEPARTMENT | DESIGNATION | JOIN_DATE | SALARY | CURRENCY |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1001 | Arjun | Reddy | IT | Developer | 2021-06-14 | 850000.00 | INR |
| 1002 | Priya | Sharma | HR | HR Manager | 2019-03-01 | 1200000.00 | INR |
| 1003 | Rahul | Verma | Finance | Accountant | 2020-09-21 | 720000.00 | INR |
| 1004 | Sneha | Iyer | IT | Senior Developer | 2018-01-15 | 1500000.00 | INR |
| 1005 | Kiran | Patel | Logistics | Coordinator | 2022-11-07 | 540000.00 | INR |
| 1006 | Ananya | Nair | Finance | Finance Manager | 2017-07-10 | 1650000.00 | INR |
| 1007 | Vikram | Singh | Sales | Sales Executive | 2023-02-27 | 600000.00 | INR |
| 1008 | Meera | Das | IT | Tester | 2022-05-16 | 650000.00 | INR |

Here is ABAP code to load it into the table:

abap

DATA lt\_emp TYPE STANDARD TABLE OF zemployee.

lt\_emp = VALUE #(

( emp\_id = '1001' first\_name = 'Arjun' last\_name = 'Reddy' department = 'IT' designation = 'Developer' join\_date = '20210614' salary = '850000.00' currency = 'INR' )

( emp\_id = '1002' first\_name = 'Priya' last\_name = 'Sharma' department = 'HR' designation = 'HR Manager' join\_date = '20190301' salary = '1200000.00' currency = 'INR' )

( emp\_id = '1003' first\_name = 'Rahul' last\_name = 'Verma' department = 'Finance' designation = 'Accountant' join\_date = '20200921' salary = '720000.00' currency = 'INR' )

( emp\_id = '1004' first\_name = 'Sneha' last\_name = 'Iyer' department = 'IT' designation = 'Senior Developer' join\_date = '20180115' salary = '1500000.00' currency = 'INR' )

( emp\_id = '1005' first\_name = 'Kiran' last\_name = 'Patel' department = 'Logistics' designation = 'Coordinator' join\_date = '20221107' salary = '540000.00' currency = 'INR' )

( emp\_id = '1006' first\_name = 'Ananya' last\_name = 'Nair' department = 'Finance' designation = 'Finance Manager' join\_date = '20170710' salary = '1650000.00' currency = 'INR' )

( emp\_id = '1007' first\_name = 'Vikram' last\_name = 'Singh' department = 'Sales' designation = 'Sales Executive' join\_date = '20230227' salary = '600000.00' currency = 'INR' )

( emp\_id = '1008' first\_name = 'Meera' last\_name = 'Das' department = 'IT' designation = 'Tester' join\_date = '20220516' salary = '650000.00' currency = 'INR' ) ).

MODIFY zemployee FROM TABLE lt\_emp.

IF sy-subrc = 0.

COMMIT WORK.

ENDIF.

MODIFY inserts new rows and updates any that already exist with the same key, so you can rerun it safely.

**Improved Version:**

You are an experienced SAP ABAP developer who sets up test data for custom tables. Generate realistic sample data for the custom table ZEMPLOYEE so I can test a report and an ALV display. Since I haven't shared the table structure, assume these fields: MANDT, EMP\_ID, EMP\_NAME, DEPARTMENT, DESIGNATION, JOIN\_DATE, SALARY and CURRENCY. Create 10 records with a mix of departments such as HR, IT, Finance and Sales, Indian names, joining dates between 2015 and 2025, and salaries in INR, in the style of this example: "00001 | Ravi Kumar | IT | Developer | 20190415 | 850000 | INR". Give the output as a simple pipe-separated table first, followed by a short ABAP snippet that inserts the same records into ZEMPLOYEE using an internal table. Keep the data fictional, don't use real people's details, use unique employee IDs, and keep the whole answer short.

**Response:**

Pipe-separated data (MANDT is filled automatically by the system):

EMP\_ID | EMP\_NAME | DEPARTMENT | DESIGNATION | JOIN\_DATE | SALARY | CURRENCY

00001 | Ravi Kumar | IT | Developer | 20190415 | 850000 | INR

00002 | Lakshmi Narayanan | HR | HR Executive | 20160822 | 620000 | INR

00003 | Amit Deshmukh | Finance | Accountant | 20180305 | 710000 | INR

00004 | Divya Menon | Sales | Sales Manager | 20150610 | 1350000 | INR

00005 | Suresh Babu | IT | Senior Developer | 20170119 | 1480000 | INR

00006 | Pooja Gupta | Finance | Finance Manager | 20150928 | 1720000 | INR

00007 | Harish Chandra | Sales | Sales Executive | 20230214 | 560000 | INR

00008 | Neha Kulkarni | HR | HR Manager | 20171103 | 1250000 | INR

00009 | Farhan Sheikh | IT | Tester | 20210731 | 640000 | INR

00010 | Swathi Rao | IT | Business Analyst | 20250102 | 780000 | INR

ABAP snippet:

abap

DATA lt\_emp TYPE STANDARD TABLE OF zemployee.

lt\_emp = VALUE #(

( emp\_id = '00001' emp\_name = 'Ravi Kumar' department = 'IT' designation = 'Developer' join\_date = '20190415' salary = '850000' currency = 'INR' )

( emp\_id = '00002' emp\_name = 'Lakshmi Narayanan' department = 'HR' designation = 'HR Executive' join\_date = '20160822' salary = '620000' currency = 'INR' )

( emp\_id = '00003' emp\_name = 'Amit Deshmukh' department = 'Finance' designation = 'Accountant' join\_date = '20180305' salary = '710000' currency = 'INR' )

( emp\_id = '00004' emp\_name = 'Divya Menon' department = 'Sales' designation = 'Sales Manager' join\_date = '20150610' salary = '1350000' currency = 'INR' )

( emp\_id = '00005' emp\_name = 'Suresh Babu' department = 'IT' designation = 'Senior Developer' join\_date = '20170119' salary = '1480000' currency = 'INR' )

( emp\_id = '00006' emp\_name = 'Pooja Gupta' department = 'Finance' designation = 'Finance Manager' join\_date = '20150928' salary = '1720000' currency = 'INR' )

( emp\_id = '00007' emp\_name = 'Harish Chandra' department = 'Sales' designation = 'Sales Executive' join\_date = '20230214' salary = '560000' currency = 'INR' )

( emp\_id = '00008' emp\_name = 'Neha Kulkarni' department = 'HR' designation = 'HR Manager' join\_date = '20171103' salary = '1250000' currency = 'INR' )

( emp\_id = '00009' emp\_name = 'Farhan Sheikh' department = 'IT' designation = 'Tester' join\_date = '20210731' salary = '640000' currency = 'INR' )

( emp\_id = '00010' emp\_name = 'Swathi Rao' department = 'IT' designation = 'Business Analyst' join\_date = '20250102' salary = '780000' currency = 'INR' ) ).

INSERT zemployee FROM TABLE lt\_emp.

IF sy-subrc = 0.

COMMIT WORK.

ELSE.

ROLLBACK WORK.

WRITE / 'Insert failed: duplicate keys already exist.'.

ENDIF.

INSERT fails if any key already exists. Use MODIFY instead if you want to rerun it safely. All names and values are fictional.

**The improvements I made are:**

The bad Prompt is “give test data for table ZEMPLOYEE,” only had a bare task and left out who the data is for, which fields exist, how many records you need, and what form the output should take. In the new version, the role is an experienced SAP ABAP developer who sets up test data for custom tables, which keeps the answer technically sound and suited to SAP. The task is now specific: generate realistic sample data for ZEMPLOYEE so you can test a report and an ALV display. Context comes from the assumed field structure (MANDT, EMP\_ID, EMP\_NAME, DEPARTMENT, DESIGNATION, JOIN\_DATE, SALARY and CURRENCY), since I hadn’t shared the real one, along with the details of 10 records, mixed departments like HR, IT, Finance and Sales, Indian names, joining dates between 2015 and 2025, and salaries in INR. The example is the sample row for Ravi Kumar, which shows the exact style each record should follow. For the format, the output is a simple pipe-separated table first, followed by a short ABAP snippet that inserts the same records into ZEMPLOYEE using an internal table. The constraints are to keep the data fictional, avoid real people’s details, use unique employee IDs, and keep the whole answer short.

**Prompt 4:**

fix this error in the code:  
REPORT z\_error\_demo.

START-OF-SELECTION.  
SELECT \* FROM sflight  
INTO TABLE gt\_flights.

Field "GT\_FLIGHTS" is unknown. It is neither in one of the specified tables nor defined by a "DATA" statement.

**Response:**

The error means gt\_flights is used in the SELECT but never declared. ABAP needs the internal table defined first, before START-OF-SELECTION.

abap

REPORT z\_error\_demo.

DATA gt\_flights TYPE STANDARD TABLE OF sflight.

START-OF-SELECTION.

SELECT \* FROM sflight

INTO TABLE gt\_flights.

The DATA line creates an internal table with the same row structure as SFLIGHT, so the SELECT has somewhere to put the rows.

If your system is on ABAP 7.40 or later, you can skip the separate declaration and declare the table inline:

abap

REPORT z\_error\_demo.

START-OF-SELECTION.

SELECT \* FROM sflight

INTO TABLE @DATA(gt\_flights).

With inline declarations, the @ escape is required before the host variable, and the column list must come before INTO in strict mode. If you get a syntax error with this version, use SELECT \* FROM sflight INTO TABLE @DATA(gt\_flights). exactly as written above, or fall back to the first version.

**Improved Version:**

You are a senior SAP ABAP developer who is good at debugging syntax errors for beginners. Fix the error in the ABAP report below, where the compiler says field "GT\_FLIGHTS" is unknown because it is neither in one of the specified tables nor defined by a DATA statement. Give me the corrected code with the missing declaration added and the SELECT kept as it is, then explain in two or three simple sentences what caused the error and why the fix works. Use a style like this: "The variable lv\_total was used in the calculation but never declared, so ABAP didn't know what it was. Adding a DATA statement for it tells ABAP its name and type, which removes the error." Show the corrected code in one code block, followed by the short explanation. Don't change the report name or the logic, don't add extra features like ALV or selection screens, and keep the whole answer short.  
REPORT z\_error\_demo.  
START-OF-SELECTION.  
SELECT \* FROM sflight  
INTO TABLE gt\_flights.

**Response:**

REPORT z\_error\_demo.

DATA gt\_flights TYPE STANDARD TABLE OF sflight.

START-OF-SELECTION.

SELECT \* FROM sflight

INTO TABLE gt\_flights.

The internal table gt\_flights was used in the SELECT but never declared, so ABAP didn’t know what it was. Adding a DATA statement tells ABAP its name and type (a table shaped like SFLIGHT), which gives the SELECT a place to store the rows and removes the error.

**The improvements I made are:**

The prompt “fix this error in the code,” had the code and the error message but gave no direction on who is fixing it, how much to change, or how to present the answer. In the new version, the role is a senior SAP ABAP developer who is good at debugging syntax errors for beginners, which sets both the expertise and a simple teaching tone. The task is now specific: fix the unknown field GT\_FLIGHTS error by adding the missing declaration while keeping the SELECT as it is, and then explain the cause and the fix. Context comes from stating exactly what the compiler complained about, namely that GT\_FLIGHTS is neither in one of the specified tables nor defined by a DATA statement, so Claude understands the real problem and doesn’t guess at a different cause. The example is the sentence about the variable lv\_total that was used but never declared, which shows the short, plain-language style I want for the explanation without giving away the actual answer. For the format, the corrected code goes in one code block, followed by a two or three sentence explanation. The constraints are to leave the report name and logic unchanged, not add extra features like ALV or selection screens, and keep the whole answer short.

**Prompt 5:**

make a report on sales order

**Response:**

I’ve made z\_sales\_order\_report.abap, an ABAP report that lists sales orders with their line items in an ALV grid. I assumed you meant an SAP report, since that’s what we’ve been working on. If you wanted something else, like a sales report in Excel, tell me.

*   **Selection screen:** filter by sales order number, customer, creation date, and sales organization.
*   **Data:** reads headers from VBAK and items from VBAP, joined on the order number.
*   **Display:** shows a sortable, filterable grid, with net value shown in the order currency.
*   **Empty results:** shows a message and stops if no orders match.

Before you run it, create it in SE38 and give the selection block a text element (TEXT-001) such as “Selection criteria”. It uses inline declarations, so it needs ABAP 7.40 or later. I can add totals per customer or a column for the customer name if you want.

REPORT z\_sales\_order\_report.

TABLES: vbak.

SELECTION-SCREEN BEGIN OF BLOCK b1 WITH FRAME TITLE TEXT-001.

SELECT-OPTIONS: s\_vbeln FOR vbak-vbeln,

s\_kunnr FOR vbak-kunnr,

s\_erdat FOR vbak-erdat,

s\_vkorg FOR vbak-vkorg.

SELECTION-SCREEN END OF BLOCK b1.

TYPES: BEGIN OF ty\_order,

vbeln TYPE vbak-vbeln,

erdat TYPE vbak-erdat,

auart TYPE vbak-auart,

vkorg TYPE vbak-vkorg,

kunnr TYPE vbak-kunnr,

waerk TYPE vbak-waerk,

posnr TYPE vbap-posnr,

matnr TYPE vbap-matnr,

arktx TYPE vbap-arktx,

kwmeng TYPE vbap-kwmeng,

vrkme TYPE vbap-vrkme,

netwr TYPE vbap-netwr,

END OF ty\_order.

DATA: gt\_orders TYPE STANDARD TABLE OF ty\_order,

go\_alv TYPE REF TO cl\_salv\_table.

START-OF-SELECTION.

" Read sales order headers (VBAK) with their items (VBAP)

SELECT a~vbeln, a~erdat, a~auart, a~vkorg, a~kunnr, a~waerk,

b~posnr, b~matnr, b~arktx, b~kwmeng, b~vrkme, b~netwr

FROM vbak AS a

INNER JOIN vbap AS b ON b~vbeln = a~vbeln

WHERE a~vbeln IN @s\_vbeln

AND a~kunnr IN @s\_kunnr

AND a~erdat IN @s\_erdat

AND a~vkorg IN @s\_vkorg

ORDER BY a~vbeln, b~posnr

INTO TABLE @gt\_orders.

IF sy-subrc <> 0.

MESSAGE 'No sales orders found for the selection' TYPE 'S' DISPLAY LIKE 'E'.

RETURN.

ENDIF.

TRY.

cl\_salv\_table=>factory( IMPORTING r\_salv\_table = go\_alv

CHANGING t\_table = gt\_orders ).

go\_alv->get\_functions( )->set\_all( abap\_true ).

go\_alv->get\_display\_settings( )->set\_list\_header( 'Sales Order Report' ).

go\_alv->get\_display\_settings( )->set\_striped\_pattern( abap\_true ).

DATA(lo\_columns) = go\_alv->get\_columns( ).

lo\_columns->set\_optimize( abap\_true ).

" Show net value with the order currency

DATA(lo\_netwr) = CAST cl\_salv\_column\_table( lo\_columns->get\_column( 'NETWR' ) ).

lo\_netwr->set\_currency\_column( 'WAERK' ).

go\_alv->display( ).

CATCH cx\_salv\_msg cx\_salv\_not\_found INTO DATA(lx\_salv).

MESSAGE lx\_salv->get\_text( ) TYPE 'E'.

ENDTRY.

**Improved Version:**

You are a senior SAP ABAP developer who writes clean, beginner-friendly reports. Create an ABAP report that reads sales order data from tables VBAK (header) and VBAP (items) and displays it in an ALV grid using CL\_SALV\_TABLE. I'm building this for a training project in an SAP S4 HANA system, so keep the code simple and easy to follow. The selection screen should let the user filter by sales organization, customer number and order creation date range. Show these columns: sales order number, order date, customer, item number, material, quantity and net value. Add short comments in the style of this example: "\* Read open invoices for the selected company code". Give me the complete code in one code block, followed by a three-line summary of how it works. Use an inner join instead of nested SELECTs, avoid SELECT \*, don't use obsolete statements like HEADER LINE, and keep the program under 80 lines.

**Response:**

REPORT z\_sales\_order\_alv.

\* Fields used only to define the selection criteria

DATA: gv\_vkorg TYPE vbak-vkorg,

gv\_kunnr TYPE vbak-kunnr,

gv\_erdat TYPE vbak-erdat.

SELECT-OPTIONS: s\_vkorg FOR gv\_vkorg,

s\_kunnr FOR gv\_kunnr,

s\_erdat FOR gv\_erdat.

\* Structure holding the columns shown in the ALV grid

TYPES: BEGIN OF ty\_order,

vbeln TYPE vbak-vbeln,

erdat TYPE vbak-erdat,

kunnr TYPE vbak-kunnr,

posnr TYPE vbap-posnr,

matnr TYPE vbap-matnr,

kwmeng TYPE vbap-kwmeng,

netwr TYPE vbap-netwr,

END OF ty\_order.

DATA: gt\_orders TYPE STANDARD TABLE OF ty\_order,

go\_alv TYPE REF TO cl\_salv\_table.

START-OF-SELECTION.

\* Read sales order headers with their items for the selected criteria

SELECT a~vbeln, a~erdat, a~kunnr,

b~posnr, b~matnr, b~kwmeng, b~netwr

FROM vbak AS a

INNER JOIN vbap AS b ON b~vbeln = a~vbeln

WHERE a~vkorg IN @s\_vkorg

AND a~kunnr IN @s\_kunnr

AND a~erdat IN @s\_erdat

ORDER BY a~vbeln, b~posnr

INTO TABLE @gt\_orders.

\* Stop if nothing matches the selection

IF sy-subrc <> 0.

MESSAGE 'No sales orders found' TYPE 'S' DISPLAY LIKE 'E'.

RETURN.

ENDIF.

\* Build the ALV grid and show it

TRY.

cl\_salv\_table=>factory( IMPORTING r\_salv\_table = go\_alv

CHANGING t\_table = gt\_orders ).

go\_alv->get\_functions( )->set\_all( abap\_true ).

go\_alv->get\_columns( )->set\_optimize( abap\_true ).

go\_alv->display( ).

CATCH cx\_salv\_msg INTO DATA(lx\_msg).

MESSAGE lx\_msg->get\_text( ) TYPE 'E'.

ENDTRY.

**The improvements I made are:**

The prompt “make a report on sales orders,” only had a vague task and left out the technology, the data source, the columns, the filters, and the output style. In the new version, the role is a senior SAP ABAP developer who writes clean, beginner-friendly reports, which sets the expertise and keeps the code readable. The task is now specific: build an ABAP report that reads sales orders from VBAK and VBAP and shows them in an ALV grid. Context comes from the training project setting in SAP HANA, the selection screen filters (sales organization, customer number and order date range), and the list of columns to display, so AI doesn’t have to guess what “report” means. The example is the sample comment about invoices, which shows the short, plain comment style I want in the code. For the format, the complete code goes in one code block, followed by a three-line summary of how it works. The constraints are to use an inner join, avoid SELECT \*, avoid obsolete statements like HEADER LINE, and keep the program under 80 lines.