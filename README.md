🏥 Hospital Emergency Room Dashboard (Excel)

An end-to-end Hospital Emergency Room Analysis Dashboard built entirely in Microsoft Excel — starting from raw, messy patient data and ending in a fully interactive, slicer-driven monthly/yearly reporting dashboard.

📌 About This Project

Hospitals generate large volumes of Emergency Room (ER) visit data every single day. On their own, raw records are hard to act on. This project takes that raw data and turns it into a clean, interactive Excel dashboard that lets hospital staff and stakeholders quickly answer questions like:


How many patients came into the ER this month?
How long are patients waiting on average?
How satisfied are patients with the service?
What % of patients are being admitted vs. sent home?
Which age groups and departments see the most ER traffic?
Are patients being seen within an acceptable time window?


The goal was to practice the complete analytics workflow — not just building charts, but going through the real steps an analyst would: cleaning raw data, modeling it with pivot tables, and designing an interactive report on top of it.

🎯 Project Objective


Build a Hospital Emergency Room Analysis Dashboard that helps stakeholders monitor, analyze, and make better decisions around patient flow and service quality — filterable by year and month.




🧩 Dashboard Features

Filters


Year selector — 2023 / 2024
Month selector — Jan through Dec (12 individual month buttons)


Selecting a year and month filters every chart and KPI on the dashboard to that specific period.

KPI Cards

KPIWhat it showsNo. of PatientsTotal ER patients for the selected month/yearAvg. Wait Time (Min)Average number of minutes patients waited before being seenPatient Satisfaction ScoreAverage patient satisfaction rating

Each KPI card also includes a small sparkline trend showing the daily pattern across the selected month.

Admission Status Table

Shows Admitted vs. Not Admitted patients with:


Patient count
% of total
A visual "status in %" bar for quick comparison


Charts


Patient Age Distribution (Bar Chart) — patients grouped into age bands: 0-4, 05-14, 15-29, 30-44, 45-59, 60-69, 70-79
Patients Attended Within Time (Pie Chart) — split between Within Time (seen in under 30 minutes) and Delay (30+ minutes)
Patients by Gender (Donut Chart) — Female vs. Male patient count
Patients by Department Referral (Bar Chart) — None, General Practice, Orthopedics, Physiotherapy, Gastroenterology, Cardiology, Neurology, Renal



🧹 Data Cleaning Process

Before any dashboard work began, the raw CSV data was cleaned inside Excel:


Removed a duplicate column (the raw data had Patient Admission Flag listed twice)
Standardized inconsistent category labels — e.g. gender values appeared as both M and Male, so these were unified
Handled missing/blank values in Patient Satisfaction Score
Converted the Patient Admission Date text into a real date field so it could be filtered by year/month
Built a supporting date/calendar reference to power the Year and Month slicers



🧮 Key Formulas Used

Age Group bucketing (creates the age bands used in the age distribution chart):

excel=IF([Patient Age]>=70,"70-79",
 IF([Patient Age]>=60,"60-69",
 IF([Patient Age]>=45,"45-59",
 IF([Patient Age]>=30,"30-44",
 IF([Patient Age]>=15,"15-29",
 IF([Patient Age]>=5,"05-14","0-4"))))))

Patient Attend Status (flags whether a patient was seen within the target time):

excel=IF([Patient Waittime]<30,"Within Time","Delay")


🛠️ Tools & Techniques Used


Excel Pivot Tables — to aggregate patients by month, age group, gender, department, and admission status
Pivot Charts — Pie, Donut, and Bar charts built directly from pivot data
Slicers — connected Year and Month filters that control every chart at once
Sparklines — compact daily trend lines inside the KPI cards
Nested IF formulas — for age grouping and timeliness status
Data bars / conditional formatting — used in the "Status in %" admission visualization



📁 Repository Structure

├── Hospital_Emergency_Dashboard.xlsm      # Main Excel file (Pivot Tables + Dashboard)
├── Hospital_Emergency_Room_Data.csv       # Raw source dataset
├── Hospital_Dashboard_Final.jpg           # Dashboard preview image
├── Project_Steps.pptx                     # Project documentation/walkthrough slides
└── README.md


📄 Dataset Description

Source file: Hospital_Emergency_Room_Data.csv

ColumnDescriptionPatient IdUnique patient identifierPatient Admission DateDate & time the patient was registeredPatient First Initial / Last NamePatient name fieldsPatient GenderGender of the patientPatient AgeAge of the patientPatient RacePatient demographic fieldDepartment ReferralDepartment the patient was referred to, if anyPatient Admission FlagWhether the patient was admitted (True/False)Patient Satisfaction ScoreSatisfaction rating given by the patientPatient WaittimeWait time in minutes before being seen

I'm treating this as a sample/synthetic dataset used for learning and portfolio purposes rather than real patient records — I don't have a way to confirm its exact origin, so if you know where it originally came from, it'd be worth crediting the source here.


🚀 How to Use This Dashboard


Download Hospital_Emergency_Dashboard.xlsm
Open it in Microsoft Excel (enable macros/content if prompted)
Go to the Dashboard sheet
Click a Year and a Month to filter the report to that period
Open the Pivot Report sheet to see the underlying pivot tables that power each chart



📊 What the Dashboard Shows (Example: November, based on the preview above)

These figures are read directly from the dashboard screenshot in this repo for the specific month/year selected there. They'll change automatically for any other month/year you select:


464 total patients
35.19 min average wait time
5.09 average patient satisfaction score
Admissions were nearly split down the middle between Admitted and Not Admitted
A majority of patients were seen within time, with a meaningful share experiencing delays
The 30–44 age group had the highest patient count
Most patients had no department referral, meaning their case was handled directly in the ER


If you want to draw further conclusions (e.g., which age group has the longest wait times, or how 2023 compares to 2024), those would need to be checked directly in the dashboard by selecting the relevant filters, since I only have visibility into the one screenshot shared here.


🧠 Skills Demonstrated


Data cleaning & preparation (duplicates, blanks, inconsistent categories)
Pivot table design & aggregation
Pivot chart creation (Pie, Donut, Bar)
Interactive filtering with Slicers
Formula-based feature engineering (nested IF)
Dashboard layout & UX design in Excel
KPI card design with sparkline trends



🔮 Possible Future Enhancements


A Power BI version of this same dashboard for cloud-based sharing
Automated data refresh using Power Query
A side-by-side 2023 vs. 2024 comparison view
Department-level breakdown of wait time and satisfaction score



📝 License

This project is shared for learning and portfolio purposes. Feel free to fork, adapt, and reuse it.


🙋 About / Contact

Built as a hands-on Excel analytics project covering the full workflow: data cleaning → pivot table modeling → chart building → interactive dashboard design.

If you have feedback or spot something worth improving, feel free to open an issue on this repo.
