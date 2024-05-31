Software engineering Risk model

- It is applicable for small and medium sized organisations
- primarily qualitative and quantitative
- Applicable to full life-cycle including maintenance phase
- Maintainable during project development

- Compatible with any development model, such as spiral, waterfall, joint application design, recent application design, incremental or prototyping
- SERIM uses risk questions to derive numerical probabilities for a set of risk factors and analyses them using a simple spreadsheet

## Terminology
##### Risk Elements:
Technical, cost scheduling problems
#####  Technical Risks

Technical risks involve potential issues related to the technology and technical aspects of the project. These risks can significantly impact the project's success and quality of the final product. Key technical risk factors include:

- **Complexity of Technology:** Use of new or untested technologies can introduce uncertainties and challenges.
- **Integration Issues:** Problems can arise when integrating different systems or components.
- **Performance Constraints:** Meeting performance requirements, such as speed and efficiency, can be challenging.
- **Technical Debt:** Accumulated technical debt due to quick fixes or poor design decisions can hinder future development.
- **Reliability and Correctness:** Ensuring the software works correctly and consistently under various conditions.

##### 2. Cost Risks

Cost risks pertain to potential financial issues that can affect the project's budget and overall financial health. These risks can lead to budget overruns or financial losses. Key cost risk factors include:

- **Budget Overruns:** The actual cost exceeding the planned budget due to various unforeseen expenses.
- **Underestimation of Costs:** Initial cost estimates being too low, leading to funding shortfalls.
- **Resource Availability:** Lack of access to necessary resources, such as skilled personnel or equipment, which can increase costs.
- **Economic Changes:** Changes in the economic environment that can impact costs, such as inflation or changes in currency exchange rates.

##### 3. Scheduling Risks

Scheduling risks involve potential delays or issues related to the project's timeline. These risks can cause delays in project completion and affect the overall schedule. Key scheduling risk factors include:

- **Unrealistic Deadlines:** Setting deadlines that are too tight and difficult to achieve.
- **Project Scope Changes:** Changes in project requirements or scope leading to delays.
- **Resource Allocation:** Inadequate allocation of resources, leading to delays in task completion.
- **Dependency Delays:** Delays caused by dependencies on other projects, teams, or external factors.
- **Time Estimation Errors:** Incorrect estimation of the time required to complete tasks or phases of the project.
#### Risk Factors:

- More specific subcategories of the general risk elements.
- Can relate to one or more risk elements.
- SERIM identifies ten primary risk factors:
    - **Organization**: Issues related to the project’s organizational structure.
    - **Estimation**: Accuracy of time and cost estimates.
    - **Monitoring**: How project progress is tracked and controlled.
    - **Development**: Challenges in the development process.
    - **Tools**: Software and hardware tools used in the project.
    - **Risk Culture**: The organization’s approach to risk management.
    - **Usability**: User-friendliness of the final product.
    - **Correctness**: Accuracy and correctness of the software.
    - **Reliability**: Dependability and stability of the software.
    - **Personnel**: Skills and performance of the project team.

Each software risk factor can influence each risk element, with the influence categorized as low, medium, or high.

They are ordered in a tree like pattern, so Risk elements are at the top, while the risk factors connect to these elements, changes in risk factors will influece the risk elements
![[Pasted image 20240530135557.png]]

![[Pasted image 20240520232235.png|300]]

One approach to assessing risk is asking questions to measure risk factors

- answers can be binary, yes,no (0,1)
	- Or they can range using any numberical values between 0 and 1. For example, a response range could be defined as none = 0, little = 0.2, some = 0.5, most = 0.8, and all = 1.0

![[Pasted image 20240520233120.png]]


![[Pasted image 20240520233204.png]]
![[Pasted image 20240521102909.png]]
$P(A)=\frac{[\sum_{n=1}^{n}{P(A_n)]}}{E}$
Basiically just the average with P(An​) is the probability of success for the n-th risk element.

![[Pasted image 20240521102941.png]]


Answering pastpaper questions on SERIM
![[Pasted image 20240527155413.png]]### a) How can SERIM help with risk management? [5 marks]

**Answer:** SERIM (Software Engineering Risk Index Model) helps with risk management by identifying, analyzing, and prioritizing potential risks in software projects. It provides a structured approach to quantify and manage risks, enabling project managers to implement effective mitigation strategies.

**Justification:**

1. **Identification of Risks:** SERIM helps in identifying various types of risks associated with software projects, such as technical, financial, and operational risks.
2. **Risk Analysis:** It allows for the analysis of the potential impact and likelihood of identified risks, giving a clear picture of their severity.
3. **Prioritization:** By quantifying risks, SERIM helps in prioritizing them based on their potential impact on the project.
4. **Mitigation Strategies:** It aids in developing appropriate mitigation strategies for high-priority risks, ensuring that they are managed proactively.
5. **Monitoring:** SERIM provides a framework for continuous monitoring and review of risks throughout the project lifecycle, facilitating timely responses to emerging threats.

### d) What is the difference between quantitative risks and qualitative risks for a typical project? [5 marks]

**Answer:** Quantitative risks involve numerical measures and statistical analysis, whereas qualitative risks involve descriptive assessments.

**Differences:**

1. **Measurement:**
    
    - **Quantitative Risks:** Measured using numerical data and statistical methods (e.g., probability distributions, Monte Carlo simulations).
    - **Qualitative Risks:** Assessed using descriptive methods (e.g., risk matrices, expert judgment).
2. **Analysis Techniques:**
    
    - **Quantitative Risks:** Techniques include cost-benefit analysis, decision trees, and sensitivity analysis.
    - **Qualitative Risks:** Techniques include SWOT analysis, brainstorming sessions, and scenario analysis.
3. **Data Requirements:**
    
    - **Quantitative Risks:** Requires precise data and historical information.
    - **Qualitative Risks:** Relies on subjective assessments and expert opinions.
4. **Application:**
    
    - **Quantitative Risks:** Used for detailed financial and schedule impact analysis.
    - **Qualitative Risks:** Used for initial risk identification and prioritization.
5. **Output:**
    
    - **Quantitative Risks:** Produces numeric estimates of risk impact and likelihood.
    - **Qualitative Risks:** Produces ranked lists of risks based on severity and impact.