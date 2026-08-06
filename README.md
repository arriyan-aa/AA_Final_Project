# AI Assisted System for Prioritizing Government Contracts for
## Human Review
1. Entity
Government agencies award numerous contracts for technology, construction, consulting,
equipment, and other services. The Canadian Public Procurement Integrity Lab is a fictional
public sector analytics unit that assists federal procurement auditors. Due to time constraints,
auditors are unable to thoroughly examine each contract by hand. The lab is looking for a datadriven
system that enables auditors to concentrate on contracts that exhibit anomalous
spending and supplier description trends.
Contract Lens combines financial irregularity detection with AI assisted procurement
description analysis to assist government auditors in identifying the contracts that are most
worthwhile reviewing.

<br><br>

2. Problem Definition
The lab seeks to respond to the following query:
Which federal contracts that differ significantly from similar contracts should be given priority
for a more thorough human review?
Problem 1: Contract irregularity discovery
To find contracts with odd combinations of features, examine structured contract data such as
contract value, department, supplier, dates, procurement category, and amendments. A
contract should be compared with pertinent contracts, such as those from the same
department, supplier group, time, or purchasing category, rather than being viewed as
problematic just because it is costly. The product should be a manageable and ranked set of
contracts that auditors can review in greater detail.
Problem 2: Contract description analysis
Without depending solely on pre existing categories, examine the written contract descriptions
to identify recurrent spending themes.
• Which spending categories have the highest concentration of odd contracts?
• Do some contracts have descriptions that don't seem to fit the categories they were
assigned?
• Are comparable purchases being given out at significantly different prices?
The objective is not to report fraud, instead the system should find trends that call for more
human intervention

<br><br>

3. Stakeholder and Decision
The primary stakeholder is a federal procurement auditor who plans regular contract reviews.
Due to staffing and time constraints, auditors must choose which contracts to review. Contract
Lens should assist them in transitioning from evaluating contracts primarily based on intuition
or value to a more methodical, evidence-based prioritization process. An auditor may be able to
examine the top 1-5% of contracts with the highest irregularity scores thanks to a helpful
output.

<br><br>

4. Dataset
The complete dataset contains hundreds of thousands of federal contract records, a cleaned
subset of approximately 10,000 contracts from recent years will be provided to keep the
analysis computationally manageable while still preserving sufficient diversity for meaningful
exploration.
Datasets consist of publicly available Government of Canadas official Proactive Publication
Contracts dataset, published by the Treasury Board of Canada Secretariat:
• downloadable contracts over 10,000 CSV file
• legacy contracts CSV
• official data dictionary
• JSON data schema
• online contract search interface
• Quarterly updates
The official portal notes that the records are submitted by federal reporting organizations and
have not been independently audited
• Primary dataset source: Government of Canada, Proactive Publication - Contracts.
• Supporting documentation: Official contract data dictionary and JSON schema.
Open Canada
Identifiers, vendor names, total contract values, and other procurement information recorded
in the official dictionary are pertinent fields. For instance, the dataset specifies a unique
reference number, procurement identification number, vendor name, and total contract value.
The supplied dataset should be a cleaned subset of roughly 5,000-15,000 contracts, chosen
from a recent period and comprising only records with useful descriptions and essential
financial fields, in order to keep the assignment manageable.

<br><br>

5. Proposed Dataset Preparation
The Client will provide:
• Contract Lens _contracts.csv
• Contract Lens _column_dictionary.pdf or .md
• A short preparation script or notebook
The cleaned file should retain useful fields such as:
Field Purpose
Reference number Unique record identifier
Department Contracting government organization
Vendor name Supplier receiving the contract
Contract value Total reported value
Contract date Timing and trend analysis
Description Text-theme analysis
Commodity or category Comparison with discovered themes
Amendment information Identification of substantial changes
Procurement method Comparison of purchasing processes
Basic cleaning may include:
• converting contract values, dates
• removing duplicate or cancelled records where appropriate
• standardizing missing values
• keeping english descriptions or clearly documenting bilingual text
• removing records with unusable descriptions
• preserving supplier and department names for aggregation

<br><br>

6. Success Criteria
Instead of returning an overwhelming list of generic outliers, a successful solution should
generate a clear, ranked subset of contracts that auditors could review. For each highly ranked
contract, the solution should offer an intelligible explanation, such as:
When compared to contracts in the same department and purchasing the theme, the contract
value is abnormally high.
Instead of ambiguous clusters like 'Category 1' the text analysis should yield significant
spending themes that are specific enough to support research, such as cloud infrastructure,
building maintenance, professional consulting, and medical equipment.
The final results should help an auditor answer:
Where should we look first, and why?
7. Constraints and Ethical Considerations
• The dataset does not contain verified fraud labels
• An unusual contract is not necessarily improper
• High-value contracts may be legitimate because of scale or complexity
• Departments may report similar purchases differently
• Vendor names and descriptions may contain inconsistent formatting
• The source data is reported by federal entities and is officially described as unaudited
• The system must support human judgment rather than automatically accuse suppliers
or departments
• Results should use terms such as irregularity, anomaly, review priority, procurement
risk, not guilt or fraud