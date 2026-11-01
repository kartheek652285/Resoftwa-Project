# **VALIDATION** 

## The prompt: 

You are an expert Python developer specializing in JSON validation and data quality checking. Develop a Python script that accepts a JSON input provided by the user and validates its structure and required fields. The script must check whether the input follows valid JSON syntax and display an appropriate error message if the JSON format is incorrect. Identify all required fields that are missing from the JSON and report each missing field separately. Check whether any existing field contains an empty value and report it as an empty required field. If any field contains null, explicitly display a message stating that the particular field is null. Also identify any unexpected or invalid fields that are not included in the predefined list of allowed fields. Display clear, field-specific validation messages so the user can easily understand the issues. If the JSON is valid and all required fields are present, display a success message. The complete Python code must not exceed 15 lines, use simple Python logic, and handle invalid JSON without terminating unexpectedly. 

The code as output in claude: 

import json 

REQUIRED = ["name", "email", "age"] 

ALLOWED = REQUIRED + ["phone", "address"] 

try: 

data = json.loads(input("Enter JSON: ")) 

if not isinstance(data, dict): raise ValueError("top-level JSON must be an object") 

errors = [] 

for f in REQUIRED: 

if f not in data: errors.append(f"Missing required field: '{f}'") 

elif data[f] is None: errors.append(f"Field '{f}' is null") 

elif str(data[f]).strip() in ("", "[]", "{}"): errors.append(f"Required field '{f}' is empty") errors += [f"Unexpected field: '{k}'" for k in data if k not in ALLOWED] 

print("\n".join(errors) if errors else "Success: JSON is valid and all required fields are present.") 

except ValueError as e: print(f"Invalid JSON: {e}") 



<!-- Start of picture text -->
‘QO%' Be one of the first 100 customers to get<br>"SH this offer in Programiz PRO. Cole ane x<br>Programiz 1C Amplify YourForex Trades Sx mogonizPeo><br>le Enter JSOW: {<br>I< REQUIREDAtoveo == nequtnen + ( f 1 stin':Seount": 18500“S6AABSSSSE<br>£ ese data, dict : ¢ Invalid 50 Expecting property name enclosed in double quotes: Line 1 column<br>fey (eatalf).str errors, append( FRequi<br><!-- End of picture text -->



<!-- Start of picture text -->
‘AO%" Be one of the first 100 customers to get<br>[68 this offer in Programiz PRO. On x<br>Programiz Amplify Your Forex Trades b —s 7)<br>Bn Vewctce RNB ouput <i<br>< me ei ame": “ABC Technologies Pvt Ltd”<br>© Atoveo = negate + castwer we": "Global Solutions Ltd<br>ic)icy ‘rror t (data).2 strip (k ( k in dataJ: errorsif k append(fRequALLOWED<br><!-- End of picture text -->

The proofs: 



<!-- Start of picture text -->
‘40%’ Be one of the first 100 customers to get .<br>HH this offer in ProgramizPRO. Coin oS<br>ProgramizPython Online Comper . A  —— peerGetreative PhotoshopCloud Prosensin [tem nore ‘Adobe Program PRO?<br>ony Vnctze RRB onpt < |<br>Q svendornae": “Lakshmi Electrical Work<br>| ovoREQUIRED =~ nequinen's[ 1 1 seeunt™:ie date", 12750"2026-11-15<br>e f oot in dita: erro ws<br>rc) a datatt1)-strip0) in ¢ Y: errors. op quired<br>hed ValueError as ‘ Ai fey<br><!-- End of picture text -->

