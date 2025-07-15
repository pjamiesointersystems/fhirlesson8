# 🔍 Lesson 8 – Searching and Filtering Data Using FHIR APIs

Welcome to **Lesson 8** of the InterSystems FHIR Course!  
This lesson introduces the fundamentals and advanced techniques of **FHIR Search**, highlighting how FHIR's RESTful API enables structured and flexible access to healthcare data.

---

## 🎯 Learning Objectives

By the end of this lesson, learners will be able to:

- Understand how FHIR search differs from traditional SQL queries
- Perform standard and advanced FHIR searches using query parameters
- Utilize chaining and reverse chaining for relational queries
- Apply token, range, and string-based searches
- Interpret paginated results using the FHIR `link` array

---

## 📂 Repository Contents

| File         | Description                                                |
|--------------|------------------------------------------------------------|
| `search.http` | VS Code-compatible file containing example HTTP FHIR queries |

Use `search.http` with the REST Client or Thunder Client extensions in VS Code to run pre-built FHIR queries interactively.

---

## ⚙️ Setup Instructions

1. **Clone the Repository**

```bash
git clone https://github.com/pjamiesointersystems/fhirlesson8.git
cd fhirlesson8

Open in VS Code

Ensure you have one of the following extensions installed:

REST Client

Thunder Client

Explore the search.http File

Open search.http to explore:

Simple patient queries:
GET /Patient?name=Smith

Token searches (e.g., using LOINC and SNOMED codes):
GET /Observation?code=http://loinc.org|85354-9

Chained searches:
GET /Observation?subject.name=John

Reverse chaining:
GET /Patient?_has:Condition:patient:code=http://snomed.info/sct|195967001

Date and numeric range searches:
GET /Procedure?date=ge2020-01-01&date=le2020-12-31

Key Concepts
🔄 FHIR vs SQL
FHIR Search	SQL Query
GET /Patient?name=Smith	SELECT * FROM Patient WHERE name='Smith'

FHIR uses HTTP GET with parameterized queries

Fields must be indexed in the FHIR spec to be searchable

✅ Searchable vs ❌ Non-Searchable Fields
Searchable	Not Searchable
Patient?name=Smith	Patient?address.line=Main St
Patient?birthdate=1985-06-15	Patient?communication.language=en

See the FHIR Search Parameter documentation for full lists.

🔗 Advanced Topics
🔗 Chaining

GET /Observation?subject.name=Smith
Allows querying related resources by traversing reference fields.

🔁 Reverse Chaining

GET /Patient?_has:Condition:patient:code=http://snomed.info/sct|195967001
Finds resources (e.g., Patients) based on conditions that refer to them.

🧪 Token Matching

GET /Patient?identifier=http://hospital.org/mrn|123456
⏱️ Range Queries

GET /Procedure?date=ge2023-01-01&date=le2023-12-31
🔤 String Matching Modifiers
:exact

:contains

:not

📖 References
📘 FHIR R4 Search Documentation

🛠️ REST Client Extension

🔗 FHIR Base Specification

🙌 Acknowledgments
Lesson created by:
Patrick W. Jamieson, M.D. – Technical Product Manager
Russ Leftwich, M.D. – Senior Clinical Advisor, Interoperability

