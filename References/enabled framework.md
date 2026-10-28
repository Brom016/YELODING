

Heliyon 10 (2024) e28910
Available online 28 March 2024
2405-8440/©  2024  The  Authors.Published  by  Elsevier  Ltd.This  is  an  open  access  article  under  the  CC  BY  license
## (http://creativecommons.org/licenses/by/4.0/).
Review article
Internet of Things (IoT)-enabled framework for a sustainable
Vaccine cold chain management system
## Shaojun Jiang
## *
## , Sumei Jia , Hongjun Guo
Hebei Key Laboratory of Optical Fiber Biosensing and Communication Devices (SZX2022010), Institute of Information Technology, Handan
## University, Handan, 056005, China
## ARTICLE INFO
## Keywords:
Vaccine cold chain
Vaccine cold chain management
Temperature monitoring
Internet of Things
Vaccine cold chain equipment
## ABSTRACT
Vaccines are  a  unique category of  drugs sensitive to  temperature and humidity and whose
effectiveness directly impacts public health. There has been an increase in vaccine-related adverse
events worldwide, particularly in developing countries, attributed to suboptimal temperatures
during transport and storage. At the same time, the Internet of Things (IoT) has ushered in a
paradigm shift in  vaccine information and storage monitoring, enabling continuous 24/7
tracking. This further reduces the dependence on limited human resources and significantly re-
duces the associated errors and losses. This paper presents an IoT-driven framework that aims to
improve the sustainability of medical cold chain management. The framework promotes trust and
transparency in vaccine surveillance data by accessing and authenticating IoT devices. The pro-
posed system aims to improve the safety and sustainability of vaccine management. Moreover, we
provide detailed insights into the design and hardware components of the proposed framework.
In addition, the specific use of the framework in a particular province is highlighted, covering the
design of the software platform and the analysis of the hardware equipment.
## 1. Introduction
Vaccines and a certain category of drugs are among the most cost-effective tools for preventing infectious diseases [1,2]. The World
Health Organization (WHO) found vaccinations can prevent two to three million deaths yearly [3]. Vaccination is estimated to have
reduced mortality rates for nine diseases by an average of 97.8% [4]. The ongoing COVID-19 outbreak over the past three years has
profoundly impacted our lives and the global landscape [5]. This virus has claimed millions of lives worldwide [6]. Vaccination is a
crucial solution to combat the pandemic [7,8]. Nevertheless, it is crucial to strictly control the temperature of vaccines from production
to administration by healthcare professionals [9]. At extreme temperatures, whether too hot or too cold, vaccines can quickly lose their
effectiveness, especially during transport and storage [10]. Currently, the recommended storage conditions for vaccines in China are a
temperature range of 2–8
## ◦
C. This ensures that the vaccine retains maximum effectiveness from production through the cold chain to
storage and vaccination. The cold chain is a term used to refer to the supply chain in which goods, such as vaccines, are maintained in a
temperature-controlled environment [11].
Therefore, the question arises: Is storing vaccines in freezers safe? To find the answer, we describe various incidents related to
vaccine refrigeration and examine global cases where COVID-19 vaccines were not stored properly. There are numerous reports of
vaccine wastage due to temperature fluctuations. For example, on January 20, 2021, Michigan authorities announced that nearly
- Corresponding author.
E-mail address: jiangshaojun@hdc.edu.cn (S. Jiang).
Contents lists available at ScienceDirect
## Heliyon
journal homepage: www.cell.com/heliyon
https://doi.org/10.1016/j.heliyon.2024.e28910
Received 7 January 2024; Received in revised form 25 March 2024; Accepted 26 March 2024

Heliyon 10 (2024) e28910
## 2
12,000 doses of Moderna’s COVID-19 vaccine were at risk due to a failure in temperature control during transportation [12]. In Maine,
over 16,000 doses were wasted, while in Milwaukee, an employee intentionally removed and destroyed over 500 doses [13]. In
January 2021, approximately 2000 doses of  the Moderna vaccine were damaged at a Boston hospital. Additionally, ABC News
attributed this to a cleaner turning off a refrigerator containing the vaccines. According to the Centers for Disease Control and Pre-
vention, the Moderna vaccine can be stored at 36–46
## ◦
## F (2–8
## ◦
C) for up to 30 days [14]. That same month, over 1100 Pfizer vaccine
doses were lost in Florida when a healthcare worker accidently closed a specialized refrigerator. The Pfizer vaccine has strict storage
requirements: 21
## ◦
## C (
