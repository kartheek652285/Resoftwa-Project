# **FIVE TRUST RULES FOR WHEN TO TRUST AI** 

1. Trust AI for standard facts, but verify important answers. 

Example: AI identifies EKKO as the SAP purchase order header table and EKPO as the item table. These are standard facts, but verify them with SAP documentation when accuracy is critical. 

2. Trust AI more when multiple sources agree. 

Example: ChatGPT, Gemini, and Claude all identify BAPI_GOODSMVT_CREATE as the BAPI used to post goods movements. Agreement increases confidence, but it does not guarantee correctness. 

3. Never trust AI blindly for complex technical explanations. 

Example: AI explains the difference between COMMIT WORK and COMMIT WORK AND WAIT. Before using the explanation in a real ABAP program, verify how update processing and sy-subrc behave. 

4. Test AI-generated solutions before using them in production. 

Example: AI recommends checking IF lt_vbak IS NOT INITIAL before using FOR ALL ENTRIES. Test this logic with empty and populated internal tables to ensure it works correctly and avoids retrieving unintended records. 

5. Be cautious when AI gives confident answers without sufficient evidence. Example: When answering questions about SAP Notes, release dates, or system-specific errors, AI may provide incorrect or incomplete information. If it cannot provide reliable evidence, treat the answer as unverified rather than assuming it is true. 

