# **HR POLICY TASK 2** 

Act as an experienced Python developer and create a short, beginner-friendly policy-based question-answering program. The program should contain predefined company policy texts directly in the code, divided into clearly numbered sections. Use only existing Python built-in modules, without requiring external libraries or API keys. Allow users to enter their own questions through the input function instead of hardcoding questions. The program must identify relevant policy sections, provide answers strictly based on the available policy, and cite the corresponding section. If the requested information is not available, it must respond exactly with "Not in policy". Keep the code simple, properly structured, error-free, and runnable in a standard Python compiler and the code should not bee too long keep it moderate 

## **Python code generated using this prompt:** 

import re 

# Predefined company policy texts divided into numbered sections 

POLICIES = { 

"Section 1": "Remote Work Policy: Employees are allowed to work remotely up to 2 days per week with prior manager approval. Core working hours are from 10:00 AM to 4:00 PM.", 

"Section 2": "Leave and PTO Policy: Full-time employees receive 20 days of paid time off (PTO) per year. PTO requests must be submitted at least two weeks in advance.", 

"Section 3": "Expense Reimbursement: Business travel expenses, including meals up to $50 per day and standard lodging, are fully reimbursable when submitted with original receipts.", "Section 4": "Code of Conduct: All employees must treat colleagues with respect and professionalism. Harassment or discrimination of any kind will result in immediate disciplinary action." 

} 

def answer_question(user_query): 

# Clean and tokenize the user query into lowercase words 

query_words = set(re.findall(r'\b\w+\b', user_query.lower())) 

# Common stop words to ignore so matching focuses on meaningful keywords 

stop_words = { 

"i", "me", "my", "myself", "we", "our", "ours", "ourselves", "you", "your", 

"yours", "yourself", "yourselves", "he", "him", "his", "himself", "she", 

"her", "hers", "herself", "it", "its", "itself", "they", "them", "their", 

"theirs", "themselves", "what", "which", "who", "whom", "this", "that", 

"these", "those", "am", "is", "are", "was", "were", "be", "been", "being", "have", "has", "had", "having", "do", "does", "did", "doing", "a", "an", "the", "and", "but", "if", "or", "because", "as", "until", "while", "of", "at", "by", "for", "with", "about", "against", "between", "into", "through", "during", "before", "after", "above", "below", "to", "from", "up", "down", "in", "out", "on", "off", "over", "under", "again", "further", "then", "once", "here", "there", "when", "where", "why", "how", "all", "any", "both", "each", "few", "more", "most", "other", "some", "such", "no", "nor", "not", "only", "own", "same", "so", "than", "too", "very", "can", "will", "just" } filtered_query = query_words - stop_words if not filtered_query: return "Not in policy" best_match = None max_score = 0 # Find the policy section with the highest keyword overlap for section, text in POLICIES.items(): text_words = set(re.findall(r'\b\w+\b', text.lower())) score = len(filtered_query.intersection(text_words)) if score > max_score: 

max_score = score best_match = section # Require at least 1 meaningful keyword match to answer if max_score > 0 and best_match: return f"{POLICIES[best_match]} (Source: {best_match})" 

else: 

return "Not in policy" 

def main(): 

print("=== Company Policy Assistant ===") print("Ask a question about company policies (type 'exit' to quit).\n") 

while True: query = input("Your question: ").strip() if query.lower() in ["exit", "quit"]: print("Goodbye!") break if not query: continue result = answer_question(query) print(result) print("-" * 50) if __name__ == "__main__": main() 

## **Proof of the answers with the prompt and the code:** 

Only 7 are right with this and 3 are out of policy. 



<!-- Start of picture text -->
moinpy Visco RIAN) output i<br>spery oe ern (Source: Section 1)<br>- CEOs Galise Eoigecs coalsoe ea api aco<br>bmi with prior manager approval. Core working hours are from 10:00 AM to 4:00 PM.<br>result It tonqwery) Your question: How many paid time-off days do full-time employees receive annually’<br>(oer) , Leaveyear. PTOand PTOrequestsPolicy: mustFull-timebe submittedemployeesat leastreceivetwo weeks20 days inofadvance.paid time(Source:off (PTO)Sectionper<br><!-- End of picture text -->





<!-- Start of picture text -->
‘ Expense Reimbursement:Business travel expenses, including meals up to $50per day<br><!-- End of picture text -->



<!-- Start of picture text -->
, Company Policy Assistant<br>‘‘ * ™ RemoteYour question:Work Policy:Does Employeesthe companyareprovideallowedfreeto worktransportationremotely upfacilitiesto 2 days forper employees:week<br>ery. with(So i priorSectiomanager yeapproval. Core working hours are from 10:00 AM to 4:00 PM.<br><!-- End of picture text -->

# **The corrected prompt for getting the code to work for all questions:** 

Act as an expert Python developer and modify the existing company policy questionanswering program to handle all 10 questions provided, ensuring that each question can retrieve the correct answer from the predefined policy sections. Improve the keywordmatching logic so that questions using different wording but referring to the same policy information are correctly understood. Preserve all four existing policy sections and ensure every answer includes its corresponding section citation. Keep the "Not in policy" response as a fallback for any new question whose answer is not supported by the predefined policies. Do not hardcode the 10 questions or their answers; users must be able to enter questions dynamically through the input function. Use only Python built-in modules, keep the code short, readable, and runnable in a standard Python compiler. Keep at least 6 sections of rules and if any question is not in policy give the related policy with a message. 

**The updated code after using the prompt:** import re 

# Expanded predefined company policy texts (6 sections) 

POLICIES = { 

"Section 1": "Remote Work Policy: Employees are allowed to work remotely up to 2 days per week with prior manager approval. Core working hours are from 10:00 AM to 4:00 PM.", 

"Section 2": "Leave and PTO Policy: Full-time employees receive 20 days of paid time off (PTO) per year. PTO requests must be submitted at least two weeks in advance.", 

"Section 3": "Expense Reimbursement: Business travel expenses, including meals up to $50 per day and standard lodging, are fully reimbursable when submitted with original receipts.", 

"Section 4": "Code of Conduct: All employees must treat colleagues with respect and professionalism. Harassment or discrimination of any kind will result in immediate disciplinary action.", 

"Section 5": "Equipment and Device Policy: The company provides laptops and secure accessories to all staff. Equipment must be returned immediately upon employment separation.", 

"Section 6": "Professional Development: Full-time staff members are eligible for up to $1,000 annually for approved conferences, online courses, or skill certifications." } 

# Synonym mapping to handle different wordings for the same concepts 

SYNONYMS = { 

"home": "remote", "house": "remote", "telecommute": "remote", "hours": "working", "schedule": "working", 

"vacation": "pto", "holiday": "leave", "timeoff": "pto", "days": "pto", "request": "submitted", "travel": "expenses", "food": "meals", "hotel": "lodging", "receipts": "reimbursement", "cost": "expenses", 

"behavior": "conduct", "harass": "harassment", "respect": "professionalism", "colleagues": 

"respect", 

"laptop": "equipment", "computer": "equipment", "device": "equipment", "return": "separation", 

"learning": "development", "courses": "development", "training": "development", "budget": "annually" 

} 

def answer_question(user_query): 

# Normalize user query and extract words 

query_words = set(re.findall(r'\b\w+\b', user_query.lower())) 

# Expand query tokens using the synonym dictionary 

expanded_query = set(query_words) 

for word in query_words: 

if word in SYNONYMS: 

expanded_query.add(SYNONYMS[word]) # Stop words to filter out 

stop_words = { 

- "i", "me", "my", "myself", "we", "our", "ours", "ourselves", "you", "your", 

"yours", "yourself", "yourselves", "he", "him", "his", "himself", "she", 

"her", "hers", "herself", "it", "its", "itself", "they", "them", "their", 

- "theirs", "themselves", "what", "which", "who", "whom", "this", "that", 

"these", "those", "am", "is", "are", "was", "were", "be", "been", "being", 

"have", "has", "had", "having", "do", "does", "did", "doing", "a", "an", 

"the", "and", "but", "if", "or", "because", "as", "until", "while", "of", 

- "at", "by", "for", "with", "about", "against", "between", "into", "through", 

- "during", "before", "after", "above", "below", "to", "from", "up", "down", 

"in", "out", "on", "off", "over", "under", "again", "further", "then", 

"once", "here", "there", "when", "where", "why", "how", "all", "any", 

"both", "each", "few", "more", "most", "other", "some", "such", "no", 

"nor", "not", "only", "own", "same", "so", "than", "too", "very", "can", "will", "just" 

} 

filtered_query = expanded_query - stop_words 

if not filtered_query: 

return "Not in policy. Please ask a specific question related to our company guidelines." best_match = None 

max_score = 0 

- # Calculate keyword matches against each policy text 

for section, text in POLICIES.items(): 

text_words = set(re.findall(r'\b\w+\b', text.lower())) score = len(filtered_query.intersection(text_words)) 

if score > max_score: 

max_score = score 

best_match = section 

- # Threshold check to ensure relevance 

if max_score > 0 and best_match: 

return f"{POLICIES[best_match]} (Source: {best_match})" 

else: 

return "Not in policy. The requested information is not covered by our current company guidelines." 

def main(): 

print("=== Advanced Company Policy Assistant ===") 

print("Ask any question regarding remote work, PTO, expenses, conduct, equipment, or development.") 

print("Type 'exit' or 'quit' to end the session.\n") 

while True: 

query = input("Your question: ").strip() 

if query.lower() in ["exit", "quit"]: 

print("Goodbye!") break if not query: continue 

result = answer_question(query) 

print(result) 

print("-" * 60) if __name__ == "__main__": main() 

## **The output for this updated one:** 

All are getting correct as the questions that has been asked are in the policy. 



<!-- Start of picture text -->
Pacis . Leave and PTO Policy: Full-time employees receive 20 days of paid time off (PTO)<br><!-- End of picture text -->



<!-- Start of picture text -->
auery.tover() in [<br>meinpy Vavolce (Rin) Oupst <i<br><!-- End of picture text -->



