---
SQL DML AND REPORTING EXERCISES - # BATCH 1 (Exercises 1-10)
---
Student Learning Project: University Management System Database
Difficulty Level: BEGINNER TO INTERMEDIATE
Last Updated: 25-Dec-2025

---
## EXERCISE 1: Basic SELECT - Count Total Students
---
Write a query to count the total number of students in the database.

### Expected Output:
A single row with one column showing the total count of students (should be 477).


---
## EXERCISE 2: Basic SELECT with WHERE - Students from Specific Department
---
Write a query to display all students from Department ID 1, showing their StudentID, 
Name, and Email.

### Expected Output:
Multiple rows showing StudentID, Name, and Email for all students in DeptID = 1.
(Should return approximately 48 students)


---
## EXERCISE 3: ORDER BY - Faculty Names Sorted Alphabetically
---
Write a query to display all faculty members sorted by their Name in ascending order.
Show FacultyID, Name, and Email.

### Expected Output:
Faculty records ordered alphabetically by Name (50 faculty members total).


---
## EXERCISE 4: Basic JOIN - Student Names with Department Names
---
Write a query to display each student's name along with their department name.
Show StudentID, Student Name, and Department Name.
Use INNER JOIN between Students and Departments tables.

### Expected Output:
Multiple rows with StudentID, student names, and their corresponding department names.


---
## EXERCISE 5: COUNT with GROUP BY - Students per Department
---
Write a query to count how many students are enrolled in each department.
Show DeptID, Department Name, and the count of students.
Order by the count in descending order.

### Expected Output:
10 rows (one for each department) showing:
DeptID | Department Name | Number of Students
For example:
1  | Computer Science | 48
2  | Electronics      | 47
...and so on


---
## EXERCISE 6: DISTINCT - Unique Departments with Faculty
---
Write a query to find all unique departments that have faculty members.
Show only the DeptID and DeptName.

### Expected Output:
10 rows showing departments that have faculty assigned.


---
## EXERCISE 7: Aggregate Functions - Average and Maximum
---
Write a query to find the average number of credits for all courses and also 
the maximum credits in any single course.

### Expected Output:
One row with two columns:
- Average Credits (for all courses)
- Maximum Credits (highest credit course)


---
## EXERCISE 8: Multiple JOINs - Student, Course, and Faculty Information
---
Write a query to display student enrollment information with course details and 
faculty information.
Show: StudentID, Student Name, Course Name, Faculty Name
Join: Students → StudentCourses → Courses → Classes → Faculty

### Expected Output:
Multiple rows showing which students are enrolled in which courses 
and which faculty teach those courses.
(Note: This will produce many rows as students take multiple courses)


---
## EXERCISE 9: WHERE Clause with Multiple Conditions - Advanced Filtering
---
Write a query to find all students from Department 1 OR Department 2 whose 
email addresses contain 'gmail.com'.
Show StudentID, Name, Email, and DeptID.

### Expected Output:
Students from dept 1 or 2 with gmail email addresses.


---
## EXERCISE 10: ORDER BY with LIMIT - Top 10 Courses by Credits
---
Write a query to display the top 10 courses with the highest number of credits.
Show CourseID, CourseName, and Credits.
Order by Credits in descending order, then by CourseName alphabetically.

### Expected Output:
10 rows showing the courses with the most credits.

---
END OF # BATCH 1 - Exercises 1 to 10
---


---
# BATCH 2 (Exercises 11-20)
Difficulty Level: INTERMEDIATE TO ADVANCED
---

---
## EXERCISE 11: HAVING Clause - Departments with Average Student Count Above Threshold
---
Write a query to find departments where the average number of students per course 
is greater than 5. Show DeptID, DeptName, and the average student count per course.
Use HAVING to filter groups after aggregation.

### Expected Output:
DeptID | DeptName              | Avg_Students_Per_Course
-------+----------------------+----------------------
Multiple rows showing only departments meeting the threshold.


---
## EXERCISE 12: Subquery in FROM - Course Statistics
---
Write a query using a subquery to find the total number of courses offered by 
each department. Use a subquery in the FROM clause.
Show: DeptName, Total_Courses

### Expected Output:
DeptName              | Total_Courses
----------------------+---------------
Computer Science     | 8
Electronics          | 7
...and so on


---
## EXERCISE 13: Subquery in WHERE - Students Enrolled in Multiple Courses
---
Write a query to find students enrolled in more than 5 courses.
Use a subquery in the WHERE clause with IN or comparison operators.
Show: StudentID, Name, Number_of_Courses

### Expected Output:
StudentID | Name          | Number_of_Courses
-----------+---------------+------------------
Multiple rows showing students with >5 course enrollments.


---
## EXERCISE 14: UNION - Combine Faculty and Staff Names
---
Write a query to combine (union) faculty names and staff names into a single list.
Show Name and Role. 
Faculty rows should have Role = 'Faculty', Staff rows should show their actual role.

### Expected Output:
Name                  | Role
----------------------+---------------------------
Anil Deshmukh        | Faculty
Bhavana Iyer         | Faculty
Database Administrator| Staff
...combining faculty and staff


---
## EXERCISE 15: CASE Statement - Student Grade Classification
---
Write a query to classify students based on their grades in StudentCourses.
Use CASE statement to assign:
  - Grade A (90+) or Excellent
  - Grade B (80-89) or Good
  - Grade C (70-79) or Average
  - Grade F (<70) or Fail

Note: Assume grades are numeric (0-100). If not, convert letter grades to numbers.
Show: StudentID, CourseName, ActualGrade, GradeClassification

### Expected Output:
StudentID | CourseName       | ActualGrade | GradeClassification
-----------+------------------+-------------+--------------------
Multiple rows showing student grades with classifications.


---
## EXERCISE 16: Self JOIN - Faculty as Department Head and Regular Faculty
---
Write a query using a self-join to find which faculty members are department heads 
and show them alongside other faculty from the same department.
Show: DeptName, HeadFacultyName, OtherFacultyName

### Expected Output:
Multiple rows showing department structure with head and other faculty.


---
## EXERCISE 17: Complex Aggregation with Multiple Conditions
---
Write a query to find courses with enrollment between 20 and 50 students that are 
offered by specific departments (1, 2, or 3).
Show: CourseID, CourseName, DeptName, Student_Count
Filter using HAVING with multiple conditions.

### Expected Output:
CourseID | CourseName         | DeptName         | Student_Count
---------+--------------------+------------------+---------------
Multiple rows meeting the enrollment and department criteria.


---
## EXERCISE 18: LEFT JOIN with IS NULL - Find Unassigned Students
---
Write a query using LEFT JOIN to find students who are NOT assigned to any hostel.
Join Students with StudentHostel using LEFT JOIN.
Show: StudentID, Name, Email where StudentHostel assignment is NULL.

### Expected Output:
StudentID | Name          | Email
-----------+---------------+---------------------
Multiple rows showing students without hostel assignments.


---
## EXERCISE 19: Window Function - Student Rank by Attendance
---
Write a query to rank students within their department by attendance percentage 
(using data from Attendance table).
Use ROW_NUMBER() or RANK() window function.
Show: StudentID, Name, DeptName, Attendance_Percentage, Rank_Within_Dept

### Expected Output:
StudentID | Name          | DeptName         | Attendance_% | Rank
-----------+---------------+------------------+-------------+-----
Multiple rows with rank assigned within each department.


---
## EXERCISE 20: Complex JOIN with Aggregation - Student Course Performance
---
Write a query to show each student's overall performance:
- Total courses enrolled
- Average grade across all courses
- Highest grade obtained
- Lowest grade obtained
Join: Students → StudentCourses with Courses
Use multiple aggregate functions with GROUP BY.

Show: StudentID, Name, Total_Courses, Avg_Grade, Highest_Grade, Lowest_Grade
Order by Average Grade descending.

### Expected Output:
StudentID | Name          | Total_Courses | Avg_Grade | Highest | Lowest
-----------+---------------+---------------+-----------+-------+--------
Multiple rows showing each student's grade statistics.

---
END OF # BATCH 2 - Exercises 11 to 20
---


---
# BATCH 3 (Exercises 21-30)
Difficulty Level: ADVANCED
---

---
## EXERCISE 21: INSERT Statement - Adding New Student Records
---
Write an INSERT statement to add 3 new students to the Students table.
New students:
1. Rohit Sharma from Department 2, email: rohit.sharma@college.edu, phone: 9876543210
2. Priya Chopra from Department 5, email: priya.chopra@gmail.com, phone: 9876543211
3. Arjun Verma from Department 3, email: arjun.verma@college.edu (no phone)

### Requirements:
- Use appropriate StudentID (assume max current StudentID is 477, so start from 478)
- Handle NULL values for optional fields
- Show the INSERT syntax clearly

### Expected Output:
Confirmation that 3 rows were inserted successfully.


---
## EXERCISE 22: UPDATE Statement - Modify Student Records
---
Write UPDATE statements to:
1. Change the phone number of student ID 100 to 9999888877
2. Update the email of student ID 250 to newemail.student@college.edu
3. Assume multiple students from Dept 4 need their department changed to Dept 6
   (Update 5 students: IDs 101, 102, 103, 104, 105)

### Requirements:
- Write separate UPDATE statements
- Show WHERE clause for each
- Include a SELECT statement to verify the changes

### Expected Output:
Number of rows affected for each update operation.


---
## EXERCISE 23: DELETE Statement - Remove Course Enrollment
---
Write DELETE statements to:
1. Delete all enrollment records for Course ID 10 where student has not graded yet
2. Delete fee records for students from Department 8 where PaidDate is NULL and DueDate has passed

### Requirements:
- Use subqueries where appropriate
- Include WHERE conditions for safe deletion
- Show a COUNT before deletion to confirm affected rows

### Expected Output:
Number of rows deleted, with verification of what was removed.


---
## EXERCISE 24: CREATE VIEW - Student Enrollment Summary
---
Create a VIEW named StudentEnrollmentSummary that shows:
- StudentID
- Student Name
- Department Name
- Total Courses Enrolled
- Total Clubs Joined
- Average Grade
- Attendance Percentage

Join multiple tables: Students, Departments, StudentCourses, StudentClubs, 
Attendance, Clubs

### Requirements:
- Use CREATE OR REPLACE VIEW syntax
- Include all necessary JOINs
- Use aggregate functions with GROUP BY
- Then write a SELECT query to retrieve from this view

### Expected Output:
Sample rows from the view showing student summary information.


---
## EXERCISE 25: VIEW with INSTEAD OF Trigger Logic - Fee Payment View
---
Create a VIEW named PendingFeePayments that shows:
- StudentID
- Student Name
- Course Name
- Fee Amount
- Due Date
- Days Overdue (using TODAY's date minus DueDate)
- Payment Status (Paid/Overdue/Pending)

### Requirements:
- Join Fees, Students, StudentCourses, Courses
- Calculate Days Overdue as: TRUNC(SYSDATE) - DueDate
- Use CASE for Payment Status
- Filter for records where PaidDate is NULL (unpaid)
- Order by Days Overdue descending

### Expected Output:
List of pending payments sorted by overdue days.


---
## EXERCISE 26: Complex Data Analysis - Student Performance by Department
---
Write a comprehensive query to analyze student performance by department:

Show:
- Department Name
- Total Students in Department
- Average GPA (from StudentCourses.Grade)
- Number of Students with >80% Attendance
- Number of Students with <75% Attendance
- Average Fee Payment Delay (days late)

### Requirements:
- Use multiple JOINs: Students, Departments, StudentCourses, Attendance, Fees
- Use GROUP BY on Department
- Calculate multiple aggregate metrics
- Use CASE for conditional counts
- Order by Average GPA descending

### Expected Output:
10 rows (one per department) with comprehensive statistics.


---
## EXERCISE 27: Recursive Query or Hierarchical Data - Faculty Reporting Chain
---
Write a query to find the reporting hierarchy:
- Show each faculty member with their department head
- Format: Faculty Name -> Department Head -> Department Name

Use a self-join or subquery to create a hierarchy.

### Requirements:
- Show direct reporting relationships
- Include FacultyID, Faculty Name, HeadID, Head Name
- Order by Department, then Faculty Name
- Show clear hierarchy (Faculty is under Head)

### Expected Output:
Multiple rows showing the chain of command in each department.


---
## EXERCISE 28: Data Validation Query - Find Data Anomalies
---
Write queries to find data quality issues:

1. Find students with multiple email addresses (unlikely but check StudentID duplicate emails)
2. Find courses with no enrolled students
3. Find faculty members not assigned to any department
4. Find students in multiple hostels simultaneously
5. Find duplicate course enrollments for same student

For each anomaly, show:
- The problematic record(s)
- A count of how many exist
- Explanation of why it's anomalous

### Expected Output:
Lists of data quality issues that need correction.


---
## EXERCISE 29: Report Generation - Monthly Attendance Report
---
Generate a monthly attendance report for the month of March 2024:

Show per Student:
- StudentID
- Student Name
- Department Name
- Days Present in March
- Days Absent in March  
- Total Class Days in March
- Attendance Percentage for March
- Performance Flag: (Good if >85%, Average if 70-85%, Poor if <70%)

### Requirements:
- Filter attendance records for March 2024 only
- Use EXTRACT(MONTH FROM date) or date range filtering
- Use CASE for performance flags
- Use COUNT with conditions
- Order by Attendance Percentage descending

### Expected Output:
List of students with their March attendance details.


---
## EXERCISE 30: Advanced Analytics - Student Scholarship Eligibility
---
Create a comprehensive query to determine scholarship eligibility based on criteria:

A student is eligible for scholarship if:
- Average Grade >= 85 (Excellent Scholar)
- Average Grade 75-84 (Merit Scholar)
- Attendance >= 90% (Attendance Scholar)
- Average Grade >= 80 AND no outstanding fees (Full Merit)

Show:
- StudentID
- Student Name
- Average Grade
- Attendance Percentage
- Outstanding Fees Amount (NULL if paid)
- Scholarship Category
- Scholarship Amount (Excellent: 50000, Merit: 30000, Attendance: 20000, Full: 40000)

### Requirements:
- Use multiple CASE statements for complex logic
- Calculate outstanding fees using SUM(Amount - (case payment status))
- Join: Students, StudentCourses, Attendance, Fees
- GROUP BY Student
- Order by Scholarship Amount descending, then by StudentID
- ONLY show students with at least one scholarship category

### Expected Output:
Scholarship-eligible students with their category and amount.

---
END OF # BATCH 3 - Exercises 21 to 30
---


---
# BATCH 4 (Exercises 31-40)
Difficulty Level: EXPERT
---

---
## EXERCISE 31: Transaction Control - COMMIT and ROLLBACK
---
Write a transaction script to:
1. Begin a transaction
2. Insert 5 new student records
3. Update 10 existing student emails
4. Delete obsolete course enrollments
5. Commit if all successful, or ROLLBACK if any error occurs

### Requirements:
- Use BEGIN TRANSACTION / START TRANSACTION
- Show COMMIT and ROLLBACK statements
- Include error handling logic (WHEN clause)
- Write SAVEPOINT for intermediate rollback points
- Show verification queries before and after transaction

### Expected Output:
Transaction log showing successful commit or rollback with record counts.


---
## EXERCISE 32: Stored Procedure Basics - Student Registration
---
Create a STORED PROCEDURE named RegisterStudent that:
- Takes input parameters: p_name, p_deptid, p_email, p_phone
- Validates that DeptID exists in Departments table
- Checks if email is already registered
- Inserts new student if validation passes
- Returns output: student_id and success_message

### Requirements:
- Use CREATE PROCEDURE syntax
- Include IF/ELSE for validation
- Use DECLARE for variables
- Handle exceptions with exception blocks
- Test the procedure with sample data

### Expected Output:
Successfully registered student IDs and error messages for invalid inputs.


---
## EXERCISE 33: Stored Function - Calculate Student GPA
---
Create a STORED FUNCTION named CalculateStudentGPA that:
- Takes input: StudentID
- Calculates GPA from StudentCourses grades
- Returns DECIMAL value between 0-4.0
- Handles division by zero (no courses taken)
- Converts letter grades or numeric marks to GPA scale

Conversion scale:
- 90-100: 4.0
- 80-89: 3.0
- 70-79: 2.0
- 60-69: 1.0
- <60: 0.0

### Requirements:
- Use CREATE FUNCTION syntax
- Include error handling
- Test with multiple students
- Use in SELECT query: SELECT StudentID, Name, CalculateStudentGPA(StudentID) AS GPA

### Expected Output:
Student IDs with calculated GPA values.


---
## EXERCISE 34: Database Trigger - Audit Trail
---
Create a TRIGGER to maintain an audit trail:
- Trigger Name: StudentAuditLog
- Fires on: INSERT, UPDATE, DELETE on Students table
- Creates audit record with: old_value, new_value, action, timestamp, user

### Requirements:
- Create an AuditLog table first
- Use BEFORE or AFTER trigger
- Capture column changes
- Record operation type (INSERT/UPDATE/DELETE)
- Use SYSDATE for timestamp
- Use USER for who made change

### Expected Output:
Audit trail showing all changes to student records with timestamps.


---
## EXERCISE 35: Complex JOIN with Subquery - Multi-Level Reporting
---
Write a query to generate a comprehensive dashboard showing:
- Department performance metrics
- Top 5 students per department by GPA
- Enrollment trends
- Faculty workload (# of classes per faculty)
- Budget utilization (fees vs scholarship)

### Requirements:
- Use multiple nested subqueries
- Use window functions for ranking
- Complex multi-table JOINs
- Aggregate functions with multiple conditions
- Format results for executive reporting

### Expected Output:
Dashboard-style report with multiple sections and summary metrics.


---
## EXERCISE 36: Index Creation and Performance Analysis
---
Write statements to:
1. Create indexes on frequently queried columns:
   - Students(Email)
   - StudentCourses(StudentID, CourseID)
   - Attendance(StudentID, attendencedate)
   - Fees(StudentID, PaidDate)

2. Analyze query performance with and without indexes
3. Show execution plans
4. Identify slow queries
5. Recommend index optimization

### Requirements:
- Use CREATE INDEX syntax
- Write EXPLAIN PLAN or similar
- Test query performance
- Drop and recreate indexes
- Document impact on INSERT/UPDATE performance

### Expected Output:
Index creation statements and performance comparison metrics.


---
## EXERCISE 37: Data Migration - Merge Two Course Sections
---
Scenario: Two course sections (CourseID 50 and 51) are being merged.
Write a transaction to:
1. Copy all students from Course 51 to Course 50
2. Update attendance records for Course 51 students to Course 50
3. Merge fees for duplicate enrollments
4. Handle duplicate enrollments (avoid duplicates)
5. Archive old records in history table

### Requirements:
- Use INSERT...SELECT for bulk copy
- Handle primary key and unique constraint violations
- Use transactions for consistency
- Verify data before and after
- Keep audit trail of changes

### Expected Output:
Migration report showing records moved, duplicates handled, and verification.


---
## EXERCISE 38: Batch Processing - Monthly Fee Generation
---
Write a batch process to:
1. Generate fees for all students for the next month
2. Calculate amount based on department and enrollment
3. Set due date as 15th of next month
4. Skip students who already have fees for that month
5. Log the batch process with counts

### Requirements:
- Use INSERT...SELECT for bulk insert
- Include status logging
- Handle errors and rollback
- Generate summary report
- Track failed records

### Expected Output:
Batch processing log showing fees created, skipped, and any errors.


---
## EXERCISE 39: Recursive Query - Course Prerequisites
---
Write a recursive query to:
1. Find all prerequisites for a given course (assume Courses has PrerequisiteCourseID)
2. Build chain: Course -> Prerequisite -> Prerequisite of Prerequisite -> ...
3. Find students who have NOT taken all prerequisites for a course
4. Suggest which prerequisites students are missing

### Requirements:
- Use WITH RECURSIVE or equivalent
- Limit recursion depth
- Handle circular dependencies
- Order prerequisites by level
- Join with StudentCourses to find missing prerequisites

### Expected Output:
Prerequisite chains and list of students missing prerequisites.


---
## EXERCISE 40: Advanced Analytics - Predictive Insights
---
Create queries for predictive analytics:
1. Students at risk of failing (GPA trending down, low attendance)
2. Students likely to drop out (pattern analysis)
3. Courses with highest failure rates
4. Faculty with most struggling students
5. Department performance trend analysis

### Requirements:
- Use window functions for trend analysis
- Calculate percentage changes month-over-month
- Use CASE for risk categorization
- Aggregate multiple metrics
- Order by risk score descending

### Expected Output:
Risk analysis reports with students/courses flagged for intervention.

---
END OF # BATCH 4 - Exercises 31 to 40
---


---
# BATCH 5 (Exercises 41-50) - FINAL BATCH
Difficulty Level: EXPERT
Focus: Advanced Reporting, SELECT Optimization, Data Visualization Metrics
---

---
## EXERCISE 41: Advanced Reporting - Cohort Analysis
---
Create a cohort analysis report showing student performance by enrollment year:
- Group students by year they enrolled
- Track attendance rate, GPA, and dropout rate per cohort
- Compare retention across cohorts
- Show year-over-year trends

### Requirements:
- Use YEAR() function on enrollment dates
- Create cohort identifiers (Cohort_2024, Cohort_2023, etc.)
- Calculate retention rate: Students still enrolled / Total enrolled
- Calculate average GPA per cohort with percentile ranking
- Show month-wise progress within each cohort
- Create quarterly performance metrics

### Expected Output:
Cohort analysis table with retention, GPA, and performance trends by enrollment year.

### Example:
Cohort  | Total_Students | Retention_% | Avg_GPA | Percentile_Rank | Status
--------|-----------------|-------------|---------|-----------------|--------
2024    | 125             | 95.2%       | 3.45    | 85th            | EXCELLENT
2023    | 118             | 88.1%       | 3.12    | 65th            | GOOD


---
## EXERCISE 42: Funnel Analysis - Student Success Pipeline
---
Create a funnel analysis showing student progression through key stages:
1. Application Stage (Total applicants)
2. Enrollment Stage (Enrolled students)
3. Active Stage (Currently taking courses)
4. Completion Stage (Completed courses)
5. Excellence Stage (GPA >= 3.5)

### Requirements:
- Calculate count at each stage
- Calculate drop-off rate between stages: (Stage_N - Stage_N+1) / Stage_N * 100
- Identify bottleneck stages
- Compare funnel across departments
- Show conversion rates with percentages
- Create visualization-ready output

### Expected Output:
Funnel metrics showing students at each stage and drop-off percentages.

### Example:
Stage            | Department       | Count | Drop_off_% | Conversion_Rate
-----------------|-----------------|-------|------------|----------------
Application      | Computer Science | 500   | 15.0%      | 85.0%
Enrollment       | Computer Science | 425   | 8.2%       | 91.8%
Active           | Computer Science | 390   | 12.5%      | 87.5%
Completion       | Computer Science | 341   | 22.5%      | 77.5%
Excellence       | Computer Science | 264   | N/A        | 77.4%


---
## EXERCISE 43: Segment Analysis - Student Performance Segments
---
Create student segmentation report:
- Segment 1: Top Performers (GPA >= 3.5, Attendance >= 90%)
- Segment 2: Good Performers (GPA 3.0-3.5, Attendance >= 80%)
- Segment 3: Average (GPA 2.0-3.0, Attendance >= 70%)
- Segment 4: At Risk (GPA < 2.0 OR Attendance < 70%)
- Segment 5: Dropout Risk (Haven't attended in 30 days)

### Requirements:
- Calculate metrics per segment
- Show segment size and percentage of total
- Calculate average metrics per segment
- Identify action items per segment
- Track segment migration (how many moved from one to another)
- Show segment trends over time

### Expected Output:
Student segments with counts, percentages, and recommended actions.

### Example:
Segment        | Count | Percent | Avg_GPA | Avg_Attendance | Action
---------------|-------|---------|---------|----------------|-----------------------------------
Top Performers | 95    | 19.9%   | 3.78    | 94.2%          | Encourage leadership roles
Good Performers| 142   | 29.8%   | 3.25    | 85.3%          | Maintain current pace
Average        | 168   | 35.2%   | 2.51    | 75.1%          | Offer tutoring support
At Risk        | 65    | 13.6%   | 1.42    | 62.3%          | Immediate intervention
Dropout Risk   | 7     | 1.5%    | 0.89    | 15.2%          | Emergency outreach


---
## EXERCISE 44: Dashboard Metrics - KPI Reporting
---
Create comprehensive KPI (Key Performance Indicator) dashboard:
- Total Students, Active Students, New Enrollments
- Overall GPA, Class Average Attendance, Fee Collection Rate
- Courses Offered, Faculty Utilization, Class Sizes
- Student Satisfaction Score (if available), Graduation Rate
- YTD Progress vs Budget/Target

### Requirements:
- Calculate 12+ key metrics
- Show comparison to previous period (Month-over-Month, YoY)
- Calculate variance % from target
- Status indicator (Red/Amber/Green) based on thresholds
- Show trend direction (↑ ↓ →)
- Format as dashboard-ready output

### Expected Output:
KPI dashboard with current values, targets, variance, and trends.

### Example:
KPI                        | Current | Target | Variance | Status | Trend
---------------------------|---------|--------|----------|--------|-------
Total Students             | 477     | 450    | +6.0%    | GREEN  | ↑
Active Enrollment Rate     | 92.5%   | 90.0%  | +2.5%    | GREEN  | ↑
Average GPA                | 2.89    | 3.00   | -3.8%    | AMBER  | ↓
Attendance Rate            | 81.3%   | 85.0%  | -4.4%    | AMBER  | ↓
Fee Collection Rate        | 87.2%   | 95.0%  | -8.2%    | RED    | ↓


---
## EXERCISE 45: Comparative Analysis - Department Benchmarking
---
Create department benchmarking report:
- Compare 5+ metrics across all departments
- Metrics: Average GPA, Attendance Rate, Enrollment Count, Faculty Count, etc.
- Rank departments 1-N for each metric
- Show Department vs College Average for each metric
- Calculate Variance Index (Department - College Average) / College Average

### Requirements:
- Multi-dimensional comparison
- Identify top and bottom performers per metric
- Show department rankings
- Create heatmap-ready data (value, color code)
- Calculate composite score across all metrics
- Identify strengths and weaknesses per department

### Expected Output:
Benchmarking table with departments ranked across multiple dimensions.

### Example:
Department           | Avg_GPA | GPA_Rank | Attendance | Att_Rank | Enrollment | Enr_Rank | Composite_Score
---------------------|---------|----------|------------|----------|------------|----------|----------------
Computer Science     | 3.24    | 1st      | 87.5%      | 2nd      | 48         | 3rd      | 85/100
Electronics          | 2.98    | 3rd      | 84.2%      | 4th      | 47         | 4th      | 72/100
Information Tech     | 3.15    | 2nd      | 89.2%      | 1st      | 50         | 1st      | 89/100


---
## EXERCISE 46: Time Series Analysis - Trend Visualization Data
---
Create time series data for attendance and performance trends:
- Generate daily attendance rates for 12 months
- Calculate rolling 7-day and 30-day averages
- Show seasonal patterns (month-over-month trends)
- Identify peaks and valleys in attendance
- Calculate growth rate month-over-month and year-over-year

### Requirements:
- Use DATEDIFF or similar for daily tracking
- Calculate moving averages with window functions
- Identify trend direction: Uptrend, Downtrend, Stable
- Show percentage change from previous period
- Generate output suitable for line chart visualization
- Include confidence intervals or variance

### Expected Output:
Time series data with dates, values, moving averages, and trend indicators.

### Example:
Date       | Daily_Attendance | MA_7Day | MA_30Day | Trend      | MoM_Change | YoY_Change
-----------|------------------|---------|----------|------------|------------|----------
2024-01-15 | 85.2%            | 84.1%   | 82.5%    | Uptrend    | +2.3%      | +5.1%
2024-01-16 | 86.1%            | 84.8%   | 82.8%    | Uptrend    | +2.8%      | +5.4%
2024-01-17 | 83.5%            | 84.3%   | 82.6%    | Downtrend  | -1.2%      | +4.2%


---
## EXERCISE 47: Distribution Analysis - Grade Distribution Report
---
Create grade distribution analysis:
- Show grade ranges: A (90-100), B (80-89), C (70-79), D (60-69), F (<60)
- Calculate count and percentage for each grade range per course
- Show distribution across all courses
- Identify courses with skewed distributions
- Compare expected vs actual distribution
- Show percentile bands: Top 25%, 25-50%, 50-75%, Bottom 25%

### Requirements:
- Use CASE statements for grade ranges
- Calculate cumulative percentages
- Show distribution by department
- Identify outlier courses
- Create histogram-ready data
- Calculate standard deviation from expected distribution

### Expected Output:
Grade distribution with counts, percentages, and percentile rankings.

### Example:
Course          | Grade_A | Grade_B | Grade_C | Grade_D | Grade_F | Mode | Std_Dev | Normal_Distribution
-----------------|---------|---------|---------|---------|---------|------|---------|-------------------
Database Systems | 12.5%   | 28.3%   | 35.2%   | 18.5%   | 5.5%    | C    | 1.12    | Yes
Data Structures  | 8.2%    | 22.1%   | 40.3%   | 22.5%   | 6.9%    | C    | 1.24    | Yes
Programming II   | 5.1%    | 15.3%   | 35.8%   | 32.4%   | 11.4%   | D    | 1.45    | Skewed


---
## EXERCISE 48: Revenue & Financial Analysis - Fee Collection Metrics
---
Create financial reporting dashboard:
- Total fees charged, collected, pending, overdue
- Calculate collection rate per student, department, month
- Project annual revenue based on current collection rate
- Identify students with payment issues (>30 days overdue)
- Calculate average collection time (days from due to paid)
- Show payment trend by payment method (if available)

### Requirements:
- Complex financial calculations
- Time-based analysis (current, 30, 60, 90+ days overdue)
- Revenue forecasting
- Cash flow projections
- Student credit scoring (payment reliability)
- Departmental revenue analysis

### Expected Output:
Financial dashboard with collection metrics, trends, and projections.

### Example:
Metric                    | Amount      | Percentage | Trend
--------------------------|-------------|------------|-------
Total Fees Charged        | 28,620,000  | 100.0%     | -
Fees Collected            | 24,954,240  | 87.2%      | ↑
Fees Pending (<30 days)   | 2,288,240   | 8.0%       | ↓
Fees Overdue (30-60 days) | 1,145,120   | 4.0%       | ↑
Fees Overdue (>60 days)   | 232,400     | 0.8%       | ↓
Projected Annual Revenue  | 99,816,960  | N/A        | ↑


---
## EXERCISE 49: Correlation Analysis - Performance Metrics Relationships
---
Create correlation analysis between key metrics:
- Attendance Rate vs GPA (correlation coefficient)
- Class Size vs Average GPA (does larger class = lower GPA?)
- Faculty Experience vs Student Performance
- Study Hours (if tracked) vs Final Grade
- Previous GPA vs Current GPA (progression)
- Days Since Last Login vs Dropout Probability

### Requirements:
- Calculate Pearson correlation coefficients (-1 to +1)
- Identify strong correlations (r > 0.7 or r < -0.3)
- Show statistical significance (p-value)
- Create scatter plot ready data
- Identify causation vs correlation
- Suggest actionable insights

### Expected Output:
Correlation matrix showing relationships between variables.

### Example:
Variables                      | Correlation | Strength      | P_Value | Significant | Insight
-------------------------------|-------------|---------------|---------|-------------|--------------------------------
Attendance vs GPA              | 0.78        | Strong Pos    | <0.001  | Yes         | Higher attendance = Higher GPA
Class Size vs Avg GPA          | -0.65       | Moderate Neg  | <0.001  | Yes         | Smaller classes perform better
Faculty Exp vs Student GPA     | 0.52        | Moderate Pos  | <0.05   | Yes         | Experience matters
Study_Hours vs Final_Grade     | 0.85        | Strong Pos    | <0.001  | Yes         | Direct relationship


---
## EXERCISE 50: Custom Visualization Metrics - Data Mart for BI Tools
---
Create a comprehensive data mart table optimized for BI visualization tools:
- Fact table structure: (StudentID, CourseID, DepartmentID, Term, Metrics...)
- Key metrics: GPA, Attendance, Grade, Status, Engagement_Score
- Dimensions: Student_Profile, Course_Profile, Faculty_Profile, Term_Profile
- Pre-aggregated metrics for fast dashboard loading
- Time dimensions: Year, Quarter, Month, Week
- Status flags: At_Risk, Honors, Probation, Active, Inactive

### Requirements:
- Denormalized structure for reporting
- Pre-calculated metrics and KPIs
- Support for drill-down analysis
- Optimized for aggregation queries
- Include confidence scores and data quality flags
- Enable multi-dimensional reporting

### Expected Output:
Data mart table structure with sample data suitable for BI tools.

### Example:
StudentID | Student_Name | CourseID | Course_Name | DeptID | Dept_Name | Term | Year | Quarter | 
-----------|--------------|----------|-------------|--------|-----------|------|------|---------|
1          | Aarav Kumar  | 101      | Database    | 1      | CS        | 1    | 2024 | Q1      |

Metrics:
GPA | Attendance | Grade | Final_Score | Status | At_Risk_Flag | Honors_Flag | Engagement_Score | Confidence
----|-----------|-------|-------------|--------|--------------|------------|-----------------|------------
3.8 | 92%       | A     | 95          | Active | 0            | 1          | 0.92            | 0.98

---
KEY FEATURES FOR # BATCH 5:
---
1. Cohort Analysis - Track student groups over time
2. Funnel Analysis - Multi-stage student progression
3. Segmentation - Behavioral and performance grouping
4. KPI Dashboard - Executive summary metrics
5. Benchmarking - Cross-departmental comparison
6. Time Series - Trend analysis and forecasting
7. Distribution - Probability and frequency analysis
8. Financial - Revenue and collection metrics
9. Correlation - Relationship analysis and insights
10. Data Mart - BI-ready dimensional structure

Expected Learning Outcomes:
- Advanced SELECT query optimization
- Multi-dimensional reporting
- Window functions for complex calculations
- Data aggregation and summarization
- Visualization metric preparation
- Business intelligence data structures
- Performance metrics and KPIs
- Trend and pattern analysis
- Financial and operational reporting
- Executive dashboard creation

---
END OF # BATCH 5 - Exercises 41 to 50
FINAL # BATCH - Comprehensive SQL Reporting and Analytics
---
