# Software Quality Quiz 2 Notes


[Week 4 - Automatic & Manual Techniques for Generating & Validating Test Data & Testing Process](#Lecture4)
<br>
[Week 5 - Test Driven Development, Static & Dynamic Analysis, Functional Testing](#Lecture5)
<br>

<a name="Lecture4"></a>
## Week 4 - Automatic & Manual Techniques for Generating & Validating Test Data & Testing Process

### Types of Data
- Discrete
  - Whole numbers (discrete variables)
- Continuous
  - Decimal numbers (continuous variables)

### Test Data Management (TDM)
- Well defined TDM strategy can
  - rapidly reduce inefficiencies
  - help extract greater value from expensive data
  - make validated test data available in an organized secured consistent and controlled manner
- **Domain Values**: The full range of valid and meaningful values for a data field
- **Data Ranges & Limits**: Especially those that define our equivalence classes
- **Data Relationships**: Data characteristics including cross-system data mappings and sources for derived or calculated data
- **Upstream & Downstream**: Data dependencies from upstream and downstream systems

- TDM Activities
  - **Initial Setup of Test Data**: This is a one time job which requires initial setup and synchronization of test data
  - **Service Projects for Test Data Requirements**: Provide test data to projects based on the requests received
  - **Continuous Support to Projects for Data Requirements**: Data creation request for change in data requirements
  - **Maintenance of Data**: Scheduled maintenance of test data in defined frequencies (weekly, monthly, quarterly or annually)

### Automatic Test Data Generation
- **Random Test Data Generation**
  - Develops test data at random until useful input is found
  - Easy to implement
  - Also ineffective on realistic program

- **Symbolic Execution-Based Test Data Generation**
  - Allow numeric values to take on symbolic values
  - Basically dont use real values
  - Hard to do for strings

- **Dynamic Test Data Generation**
  - For a condition `y <= 38`
    - Dynamic generation tries to make `y` hold a value smaller than or equal to 38 when it gets to that condition
  - If desired test requirement not met, use the generated data to see how close you were
    - Use the feedback to improve the generation
  - Do not generate test data for strings

### Manual Test Data Generation
- Data generation happens manually
- Time consuming (-)
- Data sets can be created using skills & judgments (+)
  - Ex: Better for Augmented Virtual Reality Testing

### Testing Process
- Planning
- Specification
- Execution
- Recording
- Checking for Test Completion


---

<a name="Lecture5"></a>
## Week 5 - Test Driven Development, Static & Dynamic Analysis, Functional Testing

### 


---


![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/CMM.png)
