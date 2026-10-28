

Indonesian Journal of Electrical Engineering and Computer Science
Vol. 17, No. 1, January 2020, pp. 36~46
ISSN: 2502-4752, DOI: 10.11591/ijeecs.v17.i1.pp36-46      36

Journal homepage: http://ijeecs.iaescore.com/
Solar powered peltier cooling storage for vaccines in rural
areas


Henning Buitendach, Immanuel N. Jiya and Rupert Gouws
North-West University, Potchefstroom, South Africa


## Article Info

## ABSTRACT
Article history:
## Received Apr 20, 2019
## Revised Jun 15, 2019
## Accepted Jul 23, 2019


The  research  presented  in  this  paper proposes  a  new design  of  a  vaccine
cooling  and  storage  unit  that  can  keep  vaccines  in  the  cold  chain  (2°C  to
8°C).  This design  was done to  facilitate  effective  completion  of  the  African
vaccination week. The cooling and storage unit was designed to be compact,
portable,  well  isolated  and  to  make  use  of  a  PV  solar  energy  system  as  a
source  of  electricity.  The  cooling  unit  makes  use  of  a  Liquid  to  Air
thermoelectric cooling module connected to some tubing and a liquid pump
to  cool  the  inside  of  the  cooling  unit.  The  design  process  also  included
designing  a  control  system  that  controls  the  temperature  inside  the  cooling
holder and a monitoring system to monitor the battery  voltage and capacity.
The system also has a user interface that displays the temperatures inside and
outside  of  the  cooling  holder,  as  well  as  the  battery  voltage  and  capacity.
The  cooling  system  successfully  developed  was able  to keep  vaccines
in  the  cold  chain  for  up  to  three  days,  the  system  could control  the
temperature  of  the  vaccines  with  an  accuracy  of  1°C  and  was  small  and
portable, but still had enough room to house up to 250 vaccines.
## Keywords:
PV Energy
## Renewable Energy
## Vaccine Storage
Copyright © 2020 Institute of Advanced Engineering and Science.
All rights reserved.
## Corresponding Author:
## Jiya Immanuel Ninma,
North-West University, Potchefstroom, South Africa.
Email: immanueljiya@ieee.org


## 1. INTRODUCTION
The African vaccination week, organized by the World Health Organization (WHO) each year, has
the  potential  to  drastically  lower  the  amount  of  deaths  among  young  children  in  Africa.  According  to  the
latest  study  done by  the  WHO  (World  Health  Organization)  in  2013  around  2.9  million  children  under  the
age of 5 years died in the WHO’s African region[1].  People  living  in these  rural parts  of  Africa  do  not  get
necessary  medical  attention  and  most  of  the  time  are  not  informed  enough  either.  They  do  not  have  the
knowledge  to  know  when their  children  are  ill  and  even  if  they  do,  they  do  not  have  any  resources  like  a
clinic  or  doctor  to  support  them.  The  WHO  state  that  the  main  cause  of  these  deaths  are  pneumonia,
diarrhoea, malaria and HIV [1].
Immunization  is  one  of  the  most  cost-effective  and  successful  ways  that  some  of  these  infectious
diseases can be stopped to save millions of lives[2]. Each year during World Immunization Week, the WHO
Regional Office  for Africa coordinates the African Vaccination Week. The goal of this program, led by the
WHO, is to save lives and to raise awareness under the people in these parts of Africa. For this program to be
successful  the  vaccines  used  during  the  immunization  program  need  to  stay  in  the  cold  chain  system.  The
cold  chain  system  refers  to  the  temperature  controlled  storage  and  transport  of  vaccines  that  is  needed  for
these vaccines to arrive at the patient in a potent state. The health workers that should be concentrating on the
vaccination program spend a lot of time and energy  on trying to keep these  vaccines in the cold chain. The
required temperature that a vaccine should have to stay in the cold chain is 2°C up to 8°C [3].
Having  a  cooling  device  that  can  keep  the  vaccines  at  the  correct  temperature  will  give  the  health
workers the chance to do more vaccinations [4-8]. There is also the problem of the transport of these vaccines

Indonesian J Elec Eng & Comp Sci  ISSN: 2502-4752 

Solar powered peltier cooling storage for vaccines in rural areas (Henning Buitendach)
## 37
to these parts in Africa as the journey can be quite long and the vaccines need to stay in the cold chain. These
parts  of  Africa  very  seldom  have  access  to  electricity;  thus,  they  cannot  use  a  standard  fridge [9–11].  The
numerous improvements to renewable energytechnology, particularly solar energy harnessing and conversion
into  electrical  energyby  means  of  PV panels [12-21],  brings  about  a  good  opportunity  to  arrst  the  grand
challenge of electrical energy in rural areas. This being opportunity to solve not only the challenge of vaccine
storage but extends to several other thermoelectric applications [22-28].
In previous  research [4-8,  10,  11,  22,  23, 29],  attempts  have  been  made  to  improve  the  storage
condition  of  vaccines  and  or  other  vital  medical  supplies.  However,  most  of  these  solutions  still  posses
certain  unique  shortcoings.  Some  of  the  issues  still  left  to  be  addressed  includes  the  size  of  the  cooling
compartment, the energy consumption of the system, the efficiency and the time within which the cold chain
temperature  requirements  can  be  maintained.  Summarily,  they  are either  too  large,  not  energy  efficient
enough or  not  able  to  maintain  the  cold  chain  for  the  time  required. There  is  also  the  fact  thatsome  of  the
systems  proposed  previously  are  fragile  and  hence  require  a  high  skilled  maintenance  to  keep  thesystem
running  effectively  and  efficiently.  This  level  of  skilled  maintecnance  is  often  not  available  in  rural
communities thus posing a crucial question to the economic feasibility of running such systems in rural areas.
Some of these systems are also unnesesarily “intelligent” which makes their adoption in rural Africa  more
difficult than it should due to the dearth of technical know-how [30].
The solution proposed in this research, is a robust vaccine cooling and storage unit that would keep
the  vaccines  in  the  cold  chain.  The  cooling  and  storage  unit would be kept compact  and  portable.  This
cooling holder should make use of a solar power system as a source of electricity. The solution proposed in
this research, seeks to improve the size and efficiency  of the system  while also making it robust but simple
enough for easy adoption and maintenance in rural areas.


## 2. PROPOSED SOLUTION
In  this  design,  some  of  the  main  technical  issues  during  any  vaccination  program  are  addressed.
These  issues  include  the  cold  chain  of  vaccines  during  the  vaccination  program,  as  well  as  the  energy
consumption  of  the  cooling  system  used [1-3]. The  proposed  solution  consists  out  of  a  compact  cooling
holder  that  is  well  isolated and has  enough room  for  several  vaccines. The  cooling holder  will make use  of
the most energy efficient and stable cooling method. The cooling holder will have control system that would
ensure that the temperature stays within the requirements of 2 and 8 °C and controls the energy supplied and
consumed. The cooling holder will be power by a solar power source. This, together with the energy efficient
cooling unit that will be used, will minimize the energy usage of the cooling holder. The functional units as
in  Figure  1  are  all  of  the  physical  units  that  are needed  to  build  this  cooling  system.  Each  of  these  units  is
described in detail in Table 1. A detailed flow diagram of how these units interact and work together as one
system is presented in Figure 2.


## Cooling Holder
ControllerUser Interface
Solar Power system
Cooling unit
## Temperature Probe
## Solar Panels
Charge controller
## Batteries
## Operator
## F/U:1F/U:2
## F/U:3
## F/U:4
## F/U:4.1
## F/U:4.2
## F/U:5
## F/U:5.1
## F/U:5.2
## F/U:5.3


Figure 1. Conceptual design diagram

##           ISSN: 2502-4752
## Indonesian J Elec Eng & Comp Sci, Vol. 17, No. 1, January 2020 :  36-46
## 38
The Figure 2 is an illustration of the functional flow of the cooling system. This figure indicates how
the  temperature  and  energy  control  and  monitoring  of  the  cooling  system  will  function.  When  the  cooling
system is powered on, the controller will start to receive information like the temperature inside the cooling
holder, the set temperature by the user, the battery power left, and the energy consumed by the system. This
information is then used for temperature and energy monitoring and control.


Table 1. Functional Unit description
Functional Unit Detail description
## 1: Operator
The  operator  will  interact  with  the  user  interface.  Information  like  the  desired  temperature  will  be
inserted into the user interface by the operator.
2: User interface
The temperature and energy consumption will be displayed on the user interface. The user will also be
able to set the temperature on this interface.
## 3: Controller
The   controller   will   receive   information   from   the   user   interface,   solar   power   system   and   the
temperature  probe.  This  information  will  be  used  to  control  the  temperature  by  controlling  the  status
of  the  cooling  unit.  The  controller  will  also  send  information  like  the  temperature  and  energy
consumption to the user interface.
4: Cooling holder
The  cooling  holder  will  isolate  the  vaccines  from  the  ambient  temperature.  The  cooling  unit,
temperature probe, controller and user interface will be mechanically connected to the cooling holder.
4.1: Temperature probe
The   temperature   probe   will   capture the   temperature   inside   the   cooling   holder   and   send   this
information to the controller.
4.2: Cooling unit
The  cooling  unit  will  be  responsible  for  maintaining  the  required  temperature  inside  the  cooling
holder. The cooling unit’s status will be determined and controlled by the controller.
5: Solar Power system The solar power system will supply the necessary power to the vaccine cooling holder.
5.1: Solar panels Solar panels will be used to capture renewable energy from the sun.
5.2: Charge controller
A charge controller will be used to determine the maximum power point of the electricity supplied by
the solar panels.
5.3: Batteries The energy supplied by the solar panels will be stored in the batteries


## Start
Power on
User set temperature
value on interface
Controller receive
set temperature
Controller receive
measu red
temperature
## AND
Probe measure
temperature inside
holder
Controller compare
values
## OR
Switch co olin g unit
on
Leave coolin g unit
off
Power off
Sho w measured
temperature on
interface
## End
Sho w set
temperature on
interface
Controller receive
battery power
Controller receive
energy consuemed
## AND
Controller calculate
coolin g time
remaining
Display cooling
time remaining
## OR
## OR


Figure 2. Functional flow diagram

Indonesian J Elec Eng & Comp Sci  ISSN: 2502-4752 

Solar powered peltier cooling storage for vaccines in rural areas (Henning Buitendach)
## 39
## 3. DESIGN OVERVIEW
In this section the detail design for the efficient vaccine cooling system is presented. This includes
the wiring of the different components, the controlled and monitoring software, the solar power system and
how  all  of  the  cooling  components  like  the thermoelectric  cooling  module  (TECM),  tubing,  pump  and
cooling holder fits together. Simulation results are presented to demonstrate the functionality  of the cooling
system by using software like SolidWorks, PLC Siemens LOGO! Soft Comfort and PVSyst
## ®
## .
The Liquid to air TECM selected for this project is the LA-115-24-02-0710 by Laird Technologies.
This TECM consists of a warm side with a heatsink and a fan attached to it and a cold side with some tubing
running through a cold plate [31]. The RTD temperature probe selected for this project is a PT100 probe. One
of the reasons for that is the fact that a PLC is selected as the controller. An extension module can be used to
connect the PT100 directly to the PLC.
The PLC selected is the Siemens Logo 12/24RC as this is the PLC the university has available. In
addition to  the  Siemens  12/24  RC,  an  extension module  is  also  required  to  connect  the  temperature  probes
directly to the PLC. An AM2 RTD extension module is selected, with the capability of connecting two Pt100
temperature sensors to it. The condition for the input to the AM2 is a temperature input between -50°C and
200°C. Figure 3 shows the schematic for the detail design of the PLC’s control and monitoring. The cooling
holder selected for the efficient vaccine cooling system is the 10 litre cold box produced  by Eva Kool. The
cold box is shown in the Figure 4.


## START
## RECEIVE
## TEMP. T1
## AND T2
## FROM
## PT100
## T1  <= (T-1)
## SWITCH OFF
## TECM
## Q1
## &
## SWITCH OFF PUMP
## Q2
## &
## DISPLAY ROOM
## AND COOLER
## TEMP.
## SWITCH ON
## TECM
## Q1
## &
## SWITCH ON PUMP
## Q2
TECM and pump on
(Q1 and Q2 on)
## T1  >= (T+1)
## &
## &
## OR
## YES
## YES
## YES
## NO
## NO
## NO
## OR
## RECEIVE
## TEMP. T
## FROM
## USER
## DISPLAY BATTERY
## VOLTAGE AND
## CAPACITY
## USER SET
## TEMPERATURE
## SET TEMP.
## T=5
## SYSTEM
## STATUS
## OFF
## ON
## RECEIVE
## BATTERY
## VOLTAGE
## CALCULATE
## BATTERY CAPACITY
## OR


Figure 3. PLC logic flow diagram




Figure 4. Eva Kool 10 litre cold box


##           ISSN: 2502-4752
## Indonesian J Elec Eng & Comp Sci, Vol. 17, No. 1, January 2020 :  36-46
## 40
The main problem in rural areas where the system is to  be  potentially applied is that there will not
always be electricity available to use for the vaccine cooling system, thus a solar power system was designed
to  be  able  to  supply  the  vaccine  cooling  system  with  power.  Two  solar  power  systems  were  designed;  the
first was be for a worst-case scenario and the second a more realistic system with a size constrain. The worst-
case scenario is that the temperatures are extremely hot, and it is cloudy for up to 3 days. This first step is to
determine  the  maximum  energy  consumption  of  the  cooling  system.  The  energy  consumption  of  each
component is listed in Table 2 as well as the total energy consumption of the system. The maximum energy
consumption  in  watts  is  158  W  and  the  system  would  thus  consume  a  maximum  of  3792  Wh  per  24-hour
day. The TECM require a input power of 24 V while the rest of the components require 12 V. The total Watt
hours used per day by the cooling system is 3792 Wh. The watt hours are then divided by 0.85 to compensate
for the battery losses.

## Watt−hours=
## Watt−hours
## 0.85
## =
3792Wh
## 0.85
## =4461 Wh (1)


Table 2. Maximum energy consumption
Component Maximum energy consumption (W)
LA-115-24-02-0710 liquid to air TECM 139
Siemens Logo 12/24RC and AM2 Pt100 module 2
Pt100 temperature probes 2
## Pump 15
## Total  158


Watt hours is  then  converted to  amp hours  by  dividing  the watt hours  with  the nominal  voltage  of
the batteries.

## Amp−hours=
## Watt−hours
## 24V
## =
4461Wh
## 24V
## =185.9 Ah (2)

The solar power system should also be able to provide energy to the cooling system for up to 3 days
with no power provided by the PV panels. The amp hours should thus be multiplied by 3. This then gives a
total of 557.7 Ah.

Total battery capacity
## (
## Ah
## )
## =185.9 Ah ×3=557.7 Ah (3)

To determine the size of PV panels that are needed to supply enough energy to the cooling system
and sufficiently charge the batteries the peak watt (Wp) produced is needed. The Wp depends on the size of
the  PV  panels  as  well  as  the  climate  of  the  location  the  PV  panels  are  situated [32].    The  peak  watt  (Wp)
produced by the PV panels for this specific project is calculated by using simulation software PVSyst
## ®
## . This
software is used because of its ability to use any desired location to calculate the peak watt produced as well
as  the  battery  capacity  required.  Potchefstroom  was  chosen  as  the  location  to  simulate  the  available  solar
energy as this would most likely be to location where the solar system is tested. PVSyst
## ®
calculated the peak
watt  (Wp)  produced  to  be  779  Wp  and  a  battery  capacity  of  558  Ah. The  electrical  characteristics  of  the
ReneSola Virtus II 260 W solar panel that was used is presented in [33]. The charge controller is responsible
for  maximum  power  point  tracking  to  ensure  that  the  PV  panels  are  used  to  their  full  potential. The  short
circuit  current  of  the  PV  panels  that  are  selected  is  8.95A  each.  This  short  circuit  current  is  obtained  at
ambient temperature and can be up to 20% more in high temperatures.

Short circuit current total=8.95 A ×3 panels=26.85 A (4)

Short circuit current total=26.85 A+(26.85 A×20%)=32.22 A (5)

From this calculation, it is implied that a charge controller should have a rating of at least 32.22 A.
Due  to  standard  sizes  of  charge  controller,  a  40  A,  24  V  charge  controller  is  selected  for  this  solar  power
system.
The  second  scenario  is  a  system  that  will  be  mounted  to  an  automotive  vehicle,  thus  this  system
should  be  relatively  small. The  system  consists  of  only  one  solar panel that  will  be  fitted  to  the roof  of  the
automotive vehicle and a much smaller battery bank also fitted to the vehicle. The idea of this system is that
the  batteries  will  be  pre-charged  before  the  health  workers  sets off  for  the  vaccination  programs.  The

Indonesian J Elec Eng & Comp Sci  ISSN: 2502-4752 

Solar powered peltier cooling storage for vaccines in rural areas (Henning Buitendach)
## 41
batteries will also be charging using a PV panel while the health workers are busy with the vaccination week
in locations without electricity. The PV panel will be the ReneSola Virtus II 260 W panel, but only one rather
than three like in the system above. Two 45 Ah, 12 V batteries will be used, connected in series to form a 24
V battery  bank. The size of the charge controller needed for this system is calculated using the short circuit
current of the solar panel. The sort circuit current is 8.95 A at ambient temperature and can rise up to 20% in
higher temperatures.
Short circuit current total=8.95 A+
## (
## 8.95A× 20%
## )
## =10.74 A (6)

Due  to  the  standard  sizes  of  solar  charge  controllers,  this  system  will  use  a  15  A,  24  V  charge
controller.


## 4. IMPLEMENTATION AND RESULTS
The  integrated  system  consists  of  the  cooling  holder,  PLC  and  electronic  circuit.  Figure  5  shows
how the PLC and electronics, the cooling holder and the PT100 sensors are integrated together. The cooling
holder consists of the TECM, pump, liquid coolant and tubing.



## (a)

## (b)

Figure 5. Descriptive pictorial view of the implemented system (a) integrated system and (b) cross section
of the implemented cooling box


The Vaccine cooling system is evaluated and tested to ensure that the objectives  of this project are
achieved.  The  most  important  objective  of  this  project  is  to  ensure  that  the  vaccines  stay  in  the  cold  chain.
The equipment used to test the Vaccine cooling system included a DC power supply with a constant voltage
of 24 V, a multi-meter, a Fluke Thermal imager and the PT100 temperature sensors.
The  system  was  tested  to  evaluate  the  temperature  change  in the  cooling holder, the  time required
for  the  temperature  change  and  the  energy  usage  of  the system. The  PT-100  temperature  sensor  has  been
validated  in  previous  research [34–36],  therefore,  there  is  no  need  presenting  the  validation  results  in  this
paper once it was confirmed to be working effectively by verifying the temperature values using an external
equipment. Figure 6 represents  the  temperature  of  the  cooling  system  without  a  load  over  a  period  of  100
minutes. The figure shows the time that is required by the system to reach a temperature of 3 °C. At 3 °C the
system  was  switched  off  to  measure  the  time  the  system  will  keep  its  temperature  and  stay  in  the required
temperature range of 2 °C to 8 °C.
## Matlab
## ®
was used to fit a curve to the data obtained from this test. The curve fitted to the data points
has a R-square value of 0.9933 and can thus be used as an accurate representation of the air temperature over
time in  the  cooling  holder.  The  air  temperature  inside  the  cooling  holder  can  be  represented  with  the
polynomial function of T in °C,

## 푇
## (
## 푡
## )
## =푝
## 1
## 푡
## 3
## +푝
## 2
## 푡
## 2
## +푝
## 3
## 푡+푝
## 4
## (7)

## Where, 푝
## 1
## =1.179×10
## −5
## , 푝
## 2
## =0.001523, 푝
## 3
## =−0.4054, 푝
## 4
=20.62  and   t,   the   time   in
minutes. This can be used for further work on this project in the future to determine the air temperature after
a certain amount of time.


##           ISSN: 2502-4752
## Indonesian J Elec Eng & Comp Sci, Vol. 17, No. 1, January 2020 :  36-46
## 42


Figure 6. No-Load temperature test data plot


From  the  equation  calculated  making  use  of  Matlab
## ®
,  the  time  required  to  cool  the  system  down
from  any  starting  temperature  can  be  determined.  The  value  of 푝
## 4
is  the  starting  temperature  and  can  be
changed to the starting temperature of the cooling system. For instance, if the starting temperature is 35 °C
and the system needs to be cooled down to a desired temperature of 5 °C, the time required by the system is,

## 푇
## (
## 푡
## )
## =푝
## 1
## 푡
## 3
## +푝
## 2
## 푡
## 2
## +푝
## 3
## 푡+푝
## 4

## Where; 푝
## 1
## =1.179×10
## −5
## , 푝
## 2
## =0.001523, 푝
## 3
## =−0.4054, 푝
## 4
=35 thus, 푇
## (
## 푡
## )
## =5°퐶 (8)
## 5=
## (
## 1.179×10
## −5
## )
## 푡
## 3
## +
## (
## 0.001523
## )
## 푡
## 2
## −0.4054푡+35
## 푡=94 푚푖푛푢푡푒푠

Although  this might not  be  the  exact  time  as  there are  other  external  influences  like  humidity  and
the presence or absence of direct sunlight that will affect this time, this is a good starting point. In the case of
the loaded temperature test, the purpose of this test is to determine the temperature of the heat load inside the
cooling holder.  This  cooling  system  is  designed  to  keep  vaccines  in the  cold  chain  (2 °C  to  8 °C)  and  it is
thus important to firstly test to see if the system can do so and secondly to determine how efficient the system
is.
One litre of  water placed in a glass container is used to represent the heat load of the vaccines that
this system will be used for. One vaccine has the volume of 8 ml and one litre of water is thus equivalent to
about  125  vaccines.  Although  the  vaccines  that  will be  placed  inside  the  cooling  holder  will  already  be
between the temperatures of 2 and 8°C, the water temperature was 20 °C when it was placed in the cooling
holder.
The load test was done over a period of 3 hours. From this test the time required to reach a certain
temperature  is  obtained  as  well  as  the  system  capability  to  maintain  a  certain  decried  temperature.  The
temperature  is  measured  with  the  thermal  imager  every  two  to  five  minutes  in  this  3-hour  period.  For  this
specific  test  the  PLC  was  set  to  maintain  a  temperature  between  4  and  5 °C.  Although  the  cold  chain  is
between  2  and  8°C,  the  temperature  recommended  by  the WHO is  5 °C [3].  The  reason  the  PLC  is  set  to
control  the  temperature  precise  to  one  degree  Celsius  and not  lower,  at  for  instance  0.5  °C,  is  to  avoid  the
TECM from switching on and off too often. In Figure 7 the green line represents the ambient temperature and
the  blue  line  the  load  temperature.  The  red  dotted  lines  are  the  limits of  the  cold  chain  system.  The  figure
shows that when the load temperature reached 4 °C the system is switched off and when the load temperature
then again reached 5 °C the system is switched on again.
One of the objectives of this project  was to make use of an alternative power source as the parts of
Africa where a system like this will be used, do not always have access to electricity. The energy usage of the
system is thus very important. A test was done to measure the energy usage of the system for each hour of a
regular early summer day in Potchefstroom. This may not be the exact usage of the system in other parts of
Africa at different times of the  year, but it will give a close representation. If the TECM is switched on the
system will need a current of 5.42 A at a voltage of 24 V. This gives an energy usage of 130 W. If the TECM
is  switched  off,  only  the  PLC  will  consume  energy  which  is  only  2  W.    The  energy  consumption  of  the
system for each hour is thus calculated as follow. If the system is switched on for 40 min of the hour and off
for 20 min, the average usage for that hour is,

## 0
## 4
## 8
## 12
## 16
## 20
## 24
## 0102030405060708090100110
## Temperature (
## °
## C)
Time (Minutes)

Indonesian J Elec Eng & Comp Sci  ISSN: 2502-4752 

Solar powered peltier cooling storage for vaccines in rural areas (Henning Buitendach)
## 43
## 퐸푛푒푟푔푦 푐표푛푠푢푚푝푡푖표푛=130
## (
## 40
## 60
## )
## +2
## (
## 20
## 60
## )
## =87.33 푊 (9)





Figure 7. Load temperature test data plot


The average energy consumption of the vaccine cooling system for each hour can be seen in Figure
-  The  energy  consumption is  plotted  together  with  an  educated representation  of  the  energy  supply  of  one
260W PV panel over a period of 24 hours. The representation of the energy supply is constructed making use
of PVSyst
## ®
and the  Renesola  Virtus  II  260W  PV  panel  data  sheet. The  energy  consumption  shown  on  this
graph is thus measured data while the energy supply is only a representation of the size limit solar system.
The worst case solar power system is designed to keep the vaccine cooling system powered up for
as  long  as  necessary,  even  when  there  is  no  sun  light  for  three  days.  The  size  limit  solar  power  system
however  only  consists  of  one  260W  PV  panel  and  one  150 Ah  battery,  which  will  only  be  able  to  supply
power  to  the  vaccine  cooling  system  for  a  limited  time.  The  running  time  for  the  system,  when  using  the
second solar power system can be calculated making use of this data.




Figure 8. Energy consumption vs Energy usage


Working  with  this  measured  energy  consumption  of  the  vaccine  cooling  system  together  with  the
Size limit PV system as discussed above, the running time of the system can now be calculated using the data
as represented in Figure 8. The first step is to determine the available Watt-hours of the size limit PV system
pre- charged battery.

## Amp−hours=
## Watt−hours
## Battery Voltage
## =
## 150 Ah
## 12 V
=1.8 kWh (10)

The  260  W  PV  panel  used  for  this  system  will  produce  1.3  kWh  of  energy  per  day  if  situated  in
Potchefstroom. This is obtained from Figure 8 or more directly  from the simulation software PVSyst
## ®
## . The
cooling  system  requirement  is  1896  Wh  per  day  as  an  average  energy  consumption  of  78  W  per  hour  is
## 0
## 4
## 8
## 12
## 16
## 20
## 24
## 28
## 0306090120150180
## Temperature (
## °
## C)
Time (Minutes)
## Load Temperature
Ambient temperature
## 0
## 50
## 100
## 150
## 200
## 250
## 03691215182124
Energy supplyEnergy usage
## Energy (
## Watt
## )
Timeof Day (Hours)

##           ISSN: 2502-4752
## Indonesian J Elec Eng & Comp Sci, Vol. 17, No. 1, January 2020 :  36-46
## 44
obtained from this test. This gives a shortage of 596 Wh per day that will have to be supplied by the capacity
stored in the pre- charged battery. The system thus has a running time of, 3 days.
Thus, cooling system will be able to run for three days if the Size limit PV system, (one PV panel
and  one  battery),  is  used  and  the cooling  system  is  kept  at  an  average  temperature  of  23°C  over  the  three
days. The accuracy of the system monitoring was tested by comparing the values shown on the user interface
with values measured with external equipment.


## 5. CONCLUSION
The system presented in this work is a new and tailored cooling system for keeping vaccines in the
cold chain which was to be applicable for developing countries where availability of energy in the rural areas
is  still  a  huge  challenge. This research  hopes  to solve  the  problem  as  the  vaccines  will be  kept  in  the  cold
chain in a small and portable cooling system. The system was be able to control and monitor the temperature
of  the  storage  system. The  design  process  included  designing  an  innovative  way  of  using  a  liquid to  air
TECM  to  ensure  that  this  cooling  unit  uses  its  full  potential  with  as  little  as  possible  energy  loss.  When
working with vaccines, the temperature as well as the systems capability to maintain that temperature is very
important, therefore, a user interface  with the ability to show the temperature, battery  voltage as well as the
battery capacity remaining was implemented.
The objectives which were achieved by this research include, being able to keep vaccines in the cold
chain for upto 72 hours (3day), temperature control accuracy of 1°C, portability and capacity to house upto to
250 vials of vaccine. The system developed although being robust is very user-friendly and the maintenance
cost is also less since the system is robust enough not to need a high skilled personel to operate andmaintain.


## REFERENCES
[1] World Health Organization, Global Vaccine Action Plan 2011-2020. World Health Organization, 2013.
[2] World Health Organization, “World Immunization Week 2017,” World Health Organization, 2017.
[3] World  Health  Organization, Immunization  in  practice:  a  practical  guide  for  health  staff – 2015  update.  China:
## World Health Organization, 2015.
[4] S. Monteleone, M. Sampaio, and R. F. Maia, “A novel deployment of smart Cold Chain system using 2G-RFID-
Sys temperature monitoring in medicine Cold Chain based on Internet of Things,” in 2017  IEEE  International
Conference on Service Operations and Logistics, and Informatics (SOLI), 2017, pp. 205–210.
[5] S. Jones, “Sure Chill Refrigeration Technology: Improving the Cold Chain in the Developing World,” in 2011
IEEE Global Humanitarian Technology Conference, 2011, pp. 205–207.
[6] R. Anderson et al., “Supporting immunization programs with improved vaccine cold chain information systems,”
in IEEE Global Humanitarian Technology Conference (GHTC 2014), 2014, pp. 215–222.
[7] J. M. Li, M. Friend, A. Miller, and S. Stone, “A SDD and PCM solution for vaccine storage and outreach,” in 2016
IEEE Global Humanitarian Technology Conference (GHTC), 2016, pp. 555–562.
[8] M. Friend and S. Stone, “Challenging requirements in resource challenged environment on a time challenged
schedule: A technical solution to support the cold chain for the VSV-Zebov (Merck) Ebola vaccine in Sierra Leone
Guinea,” in 2015 IEEE Global Humanitarian Technology Conference (GHTC), 2015, pp. 372–376.
[9] A.  S.  Talhar  and  S.  B.  Bodkhe,  “The  global  survey  of  the  electrical  energy  distribution  system :  a  review,”
International Journal of Electrical and Computer Engineering (IJECE), vol. 9, no. 4, pp. 2247–2255, 2019.
[10] J.  A.  Gastelo-Roque  and  A.  Morales-Acevedo, “Design of a photovoltaic system using thermoelectric Peltier
cooling for vaccines refrigeration,” in 2017 IEEE MIT Undergraduate Research Technology Conference (URTC),
2017, pp. 1–4.
[11] K.  Srinivasan  and  T.  A.  Kattakayam,  “Robust  controller  for  an  autonomous  small  refrigeration  unit,” IEE
Proceedings - Science, Measurement and Technology, vol. 146, no. 3, pp. 159–163, May 1999.
[12] A.  Pradhan and B. Panda, “Experimental Analysis of Factors Affecting the Power Output of the PV Module,”
International Journal of Electrical and Computer Engineering (IJECE), vol. 7, no. 6, p. 3190, Dec. 2017.
[13] A. Y. Al-Rawashdeh, O. Albarbarawi, and G. Qaryouti, “Response of Polycrystalline Solar Cell Outputs to Visible
Spectrum  and  other  Light  Sources-a Case Study,” International Journal of  Electrical and  Computer  Engineering
(IJECE), vol. 8, no. 6, p. 4096, Dec. 2018.
[14] A. A. Abdulrazzaq and A. Hussein Ali, “Efficiency Performances of Two MPPT Algorithms for PV System With
Different Solar Panels Irradiancess,” International Journal of Power Electronics and Drive Systems (IJPEDS), vol.
9, no. 4, p. 1755, Dec. 2018.
[15] M.  H.  Alomari,  J.  Adeeb,  and  O.  Younis, “PVPF tool: an automatedWeb application for real-time  photovoltaic
power forecasting,” International Journal  of  Electrical  and  Computer  Engineering  (IJECE),  vol.  9,  no.  1, p.  34,
## Feb. 2019.
[16] S.  Hadisaputra,  M.  Zohri,  H.  Hardani,  and  A.  Fudholi,  “Improvement  Potential  and  Exergy  Analyses  of
Photovoltaic  Thermal  with  and  without ∇-absorber Collector,” International  Journal  of  Power  Electronics  and
Drive Systems (IJPEDS), vol. 9, no. 4, p. 1792, Dec. 2018.
[17] A. T, I. Jagadeesh, and I. V, “Design and  implementation  of  modified  multilevel  sepic  converter  for  PV  based

Indonesian J Elec Eng & Comp Sci  ISSN: 2502-4752 

Solar powered peltier cooling storage for vaccines in rural areas (Henning Buitendach)
## 45
apllications,” Indonesian Journal of Elec. Eng. and Comp. Sci. (IJEECS), vol. 14, no. 3, p. 1125, Jun. 2019.
[18] N. Farhana Mohd Razali, A. Fudholi, M. Hafidz Ruslan, and K. Sopian, “Electrical characteristic of photovoltaic
thermal  collector  with  water-multiwalled  carbon  nanotube  nanofluid  flow,” Indonesian  Journal  of  Electrical
Engineering and Computer Science (IJEECS), vol. 13, no. 1, p. 324, Jan. 2019.
[19] G. A. Mani and A. K. Parvathy, “High gain boost converter with modified voltage multiplier for stand alone PV
system,” Indonesian Journal of Elec. Eng. and Comp. Sci. (IJEECS), vol. 14, no. 1, p. 185, Apr. 2019.
[20] N.  Shahirah  Binti  Rukman et  al., “Electrical  and  thermal  efficiency  of  air-based  photovoltaic  thermal  (PVT)
systems: an overview,” Indonesian  Journal  of  Elec.  Eng. and  Comp. Sci.  (IJEECS), vol.  14,  no.  3,  p.  1134,  Jun.
## 2019.
[21] E.  Roslan  and  A.  Razak,  “Performance  effect  of  applying  paraffin wax  on  solar  photovoltaic  backplate,”
Indonesian Journal of Elec. Eng. and Comp. Sci. (IJEECS), vol. 14, no. 1, p. 375, Apr. 2019.
[22] P. Attavane, G. B. Arjun, R. Radhakrishna, and S. R. Jadav, “Solar powered portable food warmer and cooler
based on peltier effect,” in 2017 2nd IEEE International Conference on Recent Trends in Electronics, Information
& Communication Technology (RTEICT), 2017, pp. 1975–1978.
[23] Shuwang Chen, Jun Zuo, and Dan Xie, “Design of solar power semiconductor refrigerator,” in 2010  8th  World
Congress on Intelligent Control and Automation, 2010, pp. 419–423.
[24] A. H. M. Alamwgani, A. T. Hindi, M. Irfan, H. Alghamidi, and S. Rahman, “Design and development of mobile
charging system using thermoelectricity,” Indonesian Journal of Elec. Eng. and Comp. Sci. (IJEECS), vol. 14, no.
2, p. 972, May 2019.
[25] S. K. A. Khalid, N. S. Che Dan, N. A. Samsudin, M. S. Aripin, and N. A. A. Nordin, “Autonomous coop cooling
system using renewable energy and water recycling,” Indonesian Journal of Elec. Eng. and Comp. Sci. (IJEECS),
vol. 13, no. 3, p. 1303, Mar. 2019.
[26] E. Roslan and I. Hassim, “Solar pv system with pulsating heat pipe cooling,” Indonesian Journal of Elec. Eng. and
Comp. Sci. (IJEECS), vol. 14, no. 1, p. 311, Apr. 2019.
[27] M.  I.  A.  Arafa  and  E.-S. S. A. Said, “A Different Visions for Uninterruptible Load using Hybrid Solar-Grid
Energy,” International  Journal  of  Power  Electronics  and  Drive  Systems  (IJPEDS),  vol.  10,  no.  1,  p.  381,  Mar.
## 2019.
[28] A.  Fudholi et  al.,  “Solar  Drying  Technology  in  Indonesia:  an  Overview,” International  Journal  of  Power
Electronics and Drive Systems (IJPEDS), vol. 9, no. 4, p. 1804, Dec. 2018.
[29] K. G. B. Arjun, B. G. Pruthviraj, K. Y. K. Chethan, and P. Rashmi, “Design and implementation of peltier based
solar  powered  portable  refrigeration  unit,”  in 2017  2nd  IEEE  International  Conference  on  Recent  Trends  in
Electronics, Information & Communication Technology (RTEICT), 2017, pp. 1971–1974.
[30] I. Saritas and M. Okay, “Design of portable medical cooler with artificial intelligent control,” in International
Conference on challenges in IT, Engineering and Technology (ICCIET’2014), 2014, pp. 39–44.
[31] Laird-Technologies, “LA PowerCool Series, LA-115-24-02 Thermoelectric Assembly,” 2010.
[32] Leonics, “How to Design Solar PV System - Guide for sizing your solar photovoltaic system.” [Online]. Available:
http://www.leonics.com/support/article2_12j/articles2_12j_en.php. [Accessed: 13-May-2019].
[33] Renesola, “Virtus®II Module Datasheet.”
[34] H. Eilers, “Thermoelectric (TECM) Cooling Holder,” North West University, Potchefstroom, 2012.
[35] C.  Svelto,  G.  Galzerano,  G.  Suardi,  and  E.  Bava,  “Compact  and  accurate  digital  thermometer  based  on  an
Anderson’s  loop  and  a  Pt-100  sensor,”  in IMTC/99.  Proceedings  of  the  16th  IEEE  Instrumentation  and
Measurement Technology Conference (Cat. No.99CH36309), vol. 3, pp. 1619–1623.
[36] N. Zabihi and R. Gouws, “Verifying the cooling capacity and power consumption of thermoelectric cooling holders
for vaccine storage,” in 2015 International Conference on the Domestic Use of Energy (DUE), 2015, pp. 115–119.


## BIOGRAPHIES OF AUTHORS


Henning  Buitendach holds a Bachelor’s degree in Electrical and Electronic Engineering from the
North-West  University  (Potchefstroom  campus).  He is  currently  registered  as  a  postgraduate  student
pursuing his Master’s degree in Electrical and Electronic Engineering at the North-West  University.
His  research  is  focused  on  the  hypothesis  that  the  efficiency  of  a  PEM  electrolysis  system  can  be
improved  by  applying  a  ripple  wave,  rather  than  the  conventional  steady  DC,  to  the  system.  After
graduation  he  worked  as  an  engineer  in  training  at  Iritron.  He  is  currently  registered  as  a  candidate
engineer with the Engineering Council of South Africa (ECSA).



Immanuel Ninma. Jiya was born in Bida, Niger State, Nigeria in 1993. He received the B.Eng. degree
in Electrical and Electronic Engineering from the Federal University of Technology, Minna, in 2016.
And   completed  the  M.  Eng.  degree  in  Electrical  and  Electronics  Engineering  at  North-West
University, Potchefstroom 2520, South Africa in 2018.
He  is  currently  continuing  his  research  career  with  a  PhD  degree  in  Electrical  and  Electronics
Engineering  at  North-West  University,  Potchefstroom  2520,  South  Africa.  His  research  current
research  area  is  Power  Electronics  with  a  special  interest  for  energy  storages,  economics  and
management.



##           ISSN: 2502-4752
## Indonesian J Elec Eng & Comp Sci, Vol. 17, No. 1, January 2020 :  36-46
## 46

Rupert  Gouws holds  a  Ph.D.  degree  in  Electrical  and  Electronic  Engineering  from  the  North-West
University (Potchefstroom campus).  He consulted to a variety of industry and public sectors in South
Africa and other countries in the fields of energy engineering and energy management. He is currently
appointed  as  an  Associate  Professor  specializing  in  energy  engineering,  electrical  machines  and
control  at  the  North-West  University.  The  Engineering  Council  of  South  Africa  (ECSA)  registered
him  as  a  Professional  Engineer  and  the  Association  of  Energy  Engineers  (AEE)  certified  him  as  a
Certified Measurement and Verification Professional (CMVP).
