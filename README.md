# Project-U.S-Education

Context

This dataset is designed to bring together multiple facets of U.S. education data into one convenient CSV (states_all.csv).
Contents

    states_all.csv: The primary data file. Contains aggregates from all state-level sources in one CSV.

    states_all_extended.csv: An extended version of states_all.csv; contains detailed enrollment data for race and gender.

    aggregates.zip

        naep_states.csv: Aggregated results from the National Assessment of Educational Progress (NAEP) for states.

        finance_states.csv: Aggregated financial data for states.

        finance_districts.csv: Aggregated financial data for school districts.

        enroll_states.csv: Aggregated enrollment data for states.

    elsect.zip, NDE.zip, nces_enroll.zip: Source files used to create the aggregates.

    sanity_check.txt: An auto-generated file that reports on nulls found in states_all.csv.

    enroll_sanity_check.txt: An auto-generated file that reports on nulls found in enrollment data.

Column Breakdown
Identification

    PRIMARY_KEY: A combination of the year and state name.
    YEAR
    STATE

Enrollment

A breakdown of students enrolled in schools by school year.

    GRADES_PK: Number of students in Pre-Kindergarten education.

    GRADES_4: Number of students in fourth grade.

    GRADES_8: Number of students in eighth grade.

    GRADES_12: Number of students in twelfth grade.

    GRADES_1_8: Number of students in the first through eighth grades.

    GRADES 9_12: Number of students in the ninth through twelfth grades.

    GRADES_KG_12: Number of students in Kindergarten through twelfth grade.

    GRADES_ALL: The count of all students in the state. Comparable to ENROLL in the financial data (which is the U.S. Census Bureau's estimate for students in the state).

The extended version of states_all contains additional columns that breakdown enrollment by race and gender. For example:

    Grades_ALL_AS: Number of students whose ethnicity was classified as "Asian".

    Grades_ALL_ASM: Number of male students whose ethnicity was classified as "Asian".

    Grades_ALL_ASF: Number of female students whose ethnicity was classified as "Asian".

The represented races include AM (American Indian or Alaska Native), AS (Asian), HI (Hispanic/Latino), BL (Black or African American), WH (White), HP (Hawaiian Native/Pacific Islander), and TR (Two or More Races). The represented genders include M (Male) and F (Female).
Financials

A breakdown of states by revenue and expenditure.

    ENROLL: The U.S. Census Bureau's count for students in the state. Should be comparable to GRADES_ALL (which is the NCES's estimate for students in the state).

    TOTAL REVENUE: The total amount of revenue for the state.
        FEDERAL_REVENUE
        STATE_REVENUE
        LOCAL_REVENUE

    TOTAL_EXPENDITURE: The total expenditure for the state.
        INSTRUCTION_EXPENDITURE
        SUPPORT_SERVICES_EXPENDITURE
        CAPITAL_OUTLAY_EXPENDITURE
        OTHER_EXPENDITURE

Academic Achievement

A breakdown of student performance as assessed by the corresponding exams (math and reading, grades 4 and 8).

    AVG_MATH_4_SCORE: The state's average score for fourth graders taking the NAEP math exam.

    AVG_MATH_8_SCORE: The state's average score for eight graders taking the NAEP math exam.

    AVG_READING_4_SCORE: The state's average score for fourth graders taking the NAEP reading exam.

    AVG_READING_8_SCORE: The state's average score for eighth graders taking the NAEP reading exam.

Data Processing

The original sources can be found here:

# Enrollment
https://nces.ed.gov/ccd/stnfis.asp
# Financials
https://www.census.gov/programs-surveys/school-finances/data/tables.html
# Academic Achievement
https://www.nationsreportcard.gov/ndecore/xplore/NDE

Data was aggregated using a Python program I wrote. The code (and an explanation of how it works) can be found here.
Methodology Notes

    Spreadsheets for NCES enrollment data for 2014, 2011, 2010, and 2009 were modified to place key data on the same sheet, making scripting easier.

    The column 'ENROLL' represents the U.S. Census Bureau data value (financial data), while the column 'GRADES_ALL' represents the NCES data value (demographic data). Though the two organizations correspond on this matter, these values (which are ostensibly the same) do vary. Their documentation chalks this up to differences in membership (i.e. what is and is not a fourth grade student).

    Enrollment data from NCES has seen a number of changes across survey years. One of the more notable is that data on student gender does not appear to have been collected until 2009. The information in states_all_extended.csv reflects this.

    NAEP test score data is only available for certain years

    The current version of this data is concerned with state-level patterns. It is the author's hope that future versions will allow for school district-level granularity.

Acknowledgements

Data is sourced from the U.S. Census Bureau and the National Center for Education Statistics (NCES).
Licensing Notes

The licensing of these datasets state that it must not be used to identify specific students or schools. So don't do that.
Future Goals

    Expand the assessment data processing to include race and gender.
    Expand all data sources to work at the district level, in addition to the state level.
    Create a version of the financial data that accounts for inflation.
    Add college data from my other Kaggle datasets.
    Build a validation tool that can check for incorrect data.
