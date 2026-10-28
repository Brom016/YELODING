

## INTERNATIONAL STUDENT ESSAY CHALLENGE  |  PARTICIPANT BRIEF
## SMART HEALTHCARE & COLD CHAIN LOGISTICS  •  1
## INTERNATIONAL STUDENT
## ESSAY CHALLENGE
## CASE STUDY 5  |  SMART HEALTHCARE & COLD CHAIN LOGISTICS
Smart IoT-Enabled Solar Cold Storage Unit
for Medical & Vaccine Supply Chains
THEME: Smart Healthcare and Resilient Cold-Chain Logistics

Universitas Wahid Hasyim (Unwahas), Indonesia
Universitas Muria Kudus (UMK), Indonesia
Cavite State University (CvSU), Philippines

Design a reliable, portable, and verifiable medical cold-chain system
Propose an IoT-enabled cold storage transport box that keeps temperature-sensitive medical supplies within 2–8°C,
supports at least 24 hours of passive holdover during power loss, and records trustworthy temperature and handover data
from dispatch to delivery.

## 1. Problem Narration
Vaccines,  biological  reagents,  and  other  temperature-sensitive  medical  supplies  must  be  transported  under
carefully controlled conditions. In island communities and rural areas—including coastal islands in the Philippines
and  remote  health  facilities  in  Central  Java—cold-chain  performance  can  be  undermined  by  grid  outages,  long
travel times, inadequate insulation, and limited access to continuous monitoring.
A  temperature  excursion  may  reduce  product  quality  even  when  a  shipment  looks  normal.  The  challenge  is
therefore  not  simply  to  build  a  cooler:  it  is  to  combine  thermal  engineering,  resilient  energy,  safe  handling,  route
planning, and credible digital records.
Design challenge
Develop a portable Smart Thermoelectric/Vapor-Compression Cold Chain Transport Box operating at 2–8°C. Integrate
thermal energy storage using phase-change materials (PCMs), automated temperature regulation, vibration mitigation, and
cryptographic IoT tracking for chain-of-custody verification.

The case uses a hypothetical spoilage figure of up to 25% as a scenario prompt, not as a universal or independently
verified rate. In your essay, explain how a real project would establish baseline spoilage and temperature-excursion
data for the target region.
## 2. System Concept
Use the following conceptual flow as a starting point. You may improve, simplify, or replace the architecture if your
proposal explains the trade-offs.
## SOLAR / POWER INPUT THERMAL MANAGEMENT 2–8°C STORAGE CHAMBER
PV + BATTERY / GRID BACKUP PCM + INSULATION + COOLER VACCINES / MEDICAL SUPPLIES

## INTERNATIONAL STUDENT ESSAY CHALLENGE  |  PARTICIPANT BRIEF
## SMART HEALTHCARE & COLD CHAIN LOGISTICS  •  2
## ROUTE & FLEET DISPATCH SECURE TELEMETRY PLATFORM IOT SENSOR ARRAY
Important: the solar panel may charge a battery or support stationary recharging; it does not necessarily need to be
mounted  on  the  transport  box.  Compare  thermoelectric  (Peltier)  and  vapor-compression  cooling  rather  than
assuming one technology is always superior.
## 3. Provided Benchmark Dataset
A. Thermal and Storage Specifications
Parameter Benchmark value Unit / note
Storage chamber volume 30.0 L
Required operating temperature 2.0–8.0 °C
Extreme ambient temperature baseline 38.0–42.0 °C
Target PCM latent heat capacity >220.0 kJ/kg
Target passive holdover time ≥24.0 hours without external power
B. Telemetry and Telecommunications Matrix
Parameter Benchmark Design implication
Sensor sampling interval 30 seconds
Continuous logging target; define buffering during
outages.
Cellular fallback LTE-M / NB-IoT
Availability depends on local operator coverage and
device support.
Maximum allowed temperature
excursion
15 minutes
Scenario requirement; actual acceptance criteria must
follow product-specific guidance.
GPS accuracy target 2.5 metres
Target under suitable signal conditions; actual accuracy
may vary.
## C. Additional Design Assumptions
- The 30 L figure refers to usable chamber volume unless your proposal explicitly defines it otherwise.
- The 24-hour holdover target must be demonstrated under a stated test profile, including ambient temperature,
payload, initial chamber temperature, door openings, and sensor placement.
- A 15-minute excursion limit is a case-study benchmark, not permission to ignore product-specific stability rules
or local cold-chain protocols.
- No  power  consumption,  battery  capacity,  vehicle  profile,  or  PCM  mass  is  prescribed.  Estimate  these  values
transparently and show sensitivity to key assumptions.
## 4. Main Essay Question
How can an IoT-enabled, solar-supported cold-chain transport system maintain vaccine and medical-
supply quality, remain operational during power and network disruptions, and provide trustworthy end-to-
end custody records at an affordable cost for remote communities?
Your essay should present a coherent system design, defend key technical choices with calculations or evidence, and
explain how performance would be tested in a realistic pilot.


## INTERNATIONAL STUDENT ESSAY CHALLENGE  |  PARTICIPANT BRIEF
## SMART HEALTHCARE & COLD CHAIN LOGISTICS  •  3
- Questions to Consider
- What is the dominant heat load under the specified ambient conditions, and which design choices most reduce
it?
- How much PCM is needed to support the 24-hour holdover target, and what safety margin is appropriate?
- Under  what  conditions  is  thermoelectric  cooling  suitable,  and  when  is  vapor  compression  likely  to  be  more
efficient?
- How  will  the  system  respond  to  a  sensor  fault,  door  left  open,  depleted  battery,  lost  cellular  signal,  or  route
delay?
- What evidence is required to decide whether a batch is still usable after a temperature excursion?
- How  will  you  validate  sensor  calibration,  alarm  latency,  temperature  uniformity,  holdover  time,  and  data
integrity?
- How can the design protect patient and shipment information while enabling authorized audits?
- What  are  the  full  costs  over  the  equipment  life,  including  replacement  batteries,  calibration,  connectivity,
maintenance, and training?
- Scope, Safety, and Assumptions
- This is a conceptual engineering and logistics case study, not a validated medical-device specification.
- Vaccine  storage  and  excursion  decisions  must  follow  the  product  label,  national  immunization  programme
requirements,  and  applicable  WHO/national  guidance.  Do  not  assume  all  vaccines  respond  identically  to
temperature excursions.
- The  2–8°C  range  is  the  case  target  for  the  scenario;  some  medical  products require  different  conditions.  State
the intended product class and design boundaries.
- Any  prototype  should  be  tested  using  calibrated  reference  sensors  and  a  documented  temperature-mapping
protocol before carrying real vaccines or biological materials.
- Cryptographic  or  blockchain  records  can  make  logged  data  more  tamper-evident,  but  cannot  by  themselves
guarantee sensor accuracy, correct handling, or truthfulness of data entered at source.
- Use  privacy-preserving  design  and  role-based  access.  Avoid  storing  patient-identifiable  information  unless
strictly necessary and lawfully authorized.
## 7. Recommended Essay Structure
- Title and executive summary
- Introduction and problem definition
- Design requirements and assumptions
- Proposed system architecture and technical justification
- Key calculations, benchmark comparison, or model
- Operational plan, risk analysis, and validation strategy
- Economic, environmental, and social impact
- Limitations and recommendations
## • Conclusion
- References and optional appendices
## 8. Submission Guidelines
## • Language: English.
- Paper size: A4; font: Times New Roman, 12 pt; line spacing: 1.5; margins: 2.54 cm.
- Submit as a PDF using the submission channel and deadline announced by the organizers.
- Use  APA  7th  edition referencing or  the  organizer's  final citation  instructions.  Cite  sources  for  technical  claims,
data, figures, and standards.

## INTERNATIONAL STUDENT ESSAY CHALLENGE  |  PARTICIPANT BRIEF
## SMART HEALTHCARE & COLD CHAIN LOGISTICS  •  4
- Label  all  figures,  tables,  assumptions,  units,  and  calculations  clearly.  Distinguish  supplied  benchmark  values
from values you estimate.
## 9. Academic Integrity
All submissions must represent the participant’s own analysis. Properly cite sources and disclose any permitted
use of AI tools in accordance with the organizers’ rules. Fabricated experimental results, uncredited copying, and
unsupported claims may affect eligibility or scoring.
Final Message to Participants
Design for reliability when conditions are not ideal.
The strongest proposal will connect thermal science, resilient energy, trustworthy data, logistics, and human decision-
making. Explain not only how the box is designed, but how a health worker can trust it when power, connectivity, time, and
resources are limited.
