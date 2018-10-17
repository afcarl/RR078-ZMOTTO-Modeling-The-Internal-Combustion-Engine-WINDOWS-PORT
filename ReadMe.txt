
=============================================================
ZMOTTO Modeling the Internal Combustion Engine: WINDOWS-PORT
=============================================================


The computer ZMOTTO program is capable of multicycle calculations, with some parameters varying from cycle to cycle, and has restart capabilities that permit continuation of a sequence of cycle calculations or the recalculation of earlier cycles with altered assumptions. It can accommodate a broad spectrum of reactants, permits changes in physical properties, and offers a wide selection of alternative modeling functions without any reprogramming. It readily adapts to the amount of information available in a particular case because the model is actually a hierarchy of five models of differing complexity. The models range from a simple model requiring only thermodynamic properties to a very complex one demanding full combustion kinetics, transport properties, and poppet valve flow characteristics. These five models can be defined precisely only by the governing equations. However, they can still be classified approximately according to their treatment of several important features of the internal combustion engine. This classification is shown in the accompanying table, where level 1 represents the simplest model and level 5 the most complex. The calculations are based on the premise that heat transfer is expressible in terms of a heat transfer coefficient and that the cylinder average of kinetic plus potential energies remains constant. Furthermore, during combustion the pressures of the burned and unburned gases are assumed to be equal and their heat transfer areas are assumed to be proportional to their respective mass fractions. Although the model cannot resolve spatial gradients, it does not assume spatial uniformity.


1. Pre-Requisits/Reference: (https://ntrs.nasa.gov/search.jsp?R=19940002904)

2. Documentation: (https://ntrs.nasa.gov/archive/nasa/casi.ntrs.nasa.gov/19850011423.pdf)

3. Example problem located in "./example/":

4. Example problem: "Supercharged 488 cubic inch Chysler Hemi Drag Racing Engine using Methanol as Fuel" located:  "./example/"
4a. INPUT FILE #1: "TRANSPORT.INP".

==================================
START: Input File: "TRANSPORT.INP"
==================================
TRANSPORT
AIR                               V2C2   CALCULATED FROM N2, O2, AR, AND CO2    
 V   300.00  1000.00 0.60895375E 00-0.42843219E 02-0.11325133E 04 0.19053012E 01
 C   300.00  1000.00 0.87626176E 00 0.51636889E 02-0.46371351E 04 0.43274754E 00
 V  1000.00  5000.00 0.64804837E 00 0.22433407E 02-0.18264803E 05 0.15871360E 01
 C  1000.00  5000.00 0.68643241E 00-0.89154091E 02-0.21012637E 05 0.19004375E 01
AR                                V2C2  GORDON; NASA TM86885, OCT 1984          
 V  300.000 1000.000 0.57067551E 00-0.95117331E 02 0.20896403E 04 0.24718808E 01
 V 1000.000 5000.000 0.65601183E 00 0.51780497E 02-0.33046713E 05 0.17711406E 01
 C  300.000 1000.000 0.56758528E 00-0.10015251E 03 0.25736598E 04 0.22537407E 01
 C 1000.000 5000.000 0.64275516E 00 0.14112909E 02-0.20639082E 05 0.16440096E 01

... <content removed> ...

 OH                                V2C2  GORDON; NASA TM86885, OCT 1984          
 V  300.000 1000.000 0.78530133E 00-0.16524903E 03 0.12621544E 05 0.69788972E 00
 V 1000.000 5000.000 0.58936635E 00-0.36223418E 03 0.23355306E 05 0.22363455E 01
 C  300.000 1000.000 0.10657500E 01 0.45300526E 02-0.37257802E 04-0.49894757E 00
 C 1000.000 5000.000 0.58415552E 00-0.87533541E 03 0.20830503E 06 0.35371017E 01
O2                                V2C2  GORDON; NASA TM86885, OCT 1984          
 V  300.000 1000.000 0.61936357E 00-0.44608607E 02-0.13460714E 04 0.19597562E 01
 V 1000.000 5000.000 0.63839563E 00-0.12344438E 01-0.22885810E 05 0.18056937E 01
 C  300.000 1000.000 0.81595343E 00-0.34366856E 02 0.22785080E 04 0.10050999E 01
 C 1000.000 5000.000 0.80805788E 00 0.11982181E 03-0.47335931E 05 0.95189193E 00
LAST                                                                            
==================================
END: Input File: "TRANSPORT.INP"
==================================


4b. INPUT FILE #2: "THERMO.INP".

==================================
START: Input File: "THERMO.INP"
==================================
   300.000  1000.000  5000.000
AR                L 5/66AR 1.00 0.00 0.00 0.G   300.000  5000.000     39.94800 1
 0.25000000E 01     0.00000000     0.00000000     0.00000000     0.00000000    2
-0.74537502E 03 0.43660006E 01 0.25000000E 01     0.00000000     0.00000000    3
     0.00000000     0.00000000-0.74537498E 03 0.43660006E 01     0.00000000    4
C                 J 3/78C  1.   0.   0.   0.G   300.000  5000.000     12.01100 1
 0.25769424E 01-0.13903944E-03 0.69481807E-07-0.67414021E-11-0.43389004E-16    2
 0.85425220E 05 0.43358122E 01 0.25279476E 01-0.12519400E-03 0.22544496E-06    3
-0.18489024E-09 0.57291741E-13 0.85448374E 05 0.46274790E 01     0.00000000    4

... <content removed> ...

N2                J 3/77N  2.   0.   0.   0.G   300.000  5000.000     28.01340 1
 0.28532899E 01 0.16022128E-02-0.62936893E-06 0.11441022E-09-0.78057465E-14    2
-0.89008093E 03 0.63964897E 01 0.37044177E 01-0.14218753E-02 0.28670392E-05    3
-0.12028885E-08-0.13954677E-13-0.10640795E 04 0.22336285E 01     0.00000000    4
O2                J 3/77O  2.   0.   0.   0.G   300.000  5000.000     31.99879 1
 0.36122139E 01 0.74853166E-03-0.19820647E-06 0.33749008E-10-0.23907374E-14    2
-0.11978151E 04 0.36703307E 01 0.37837135E 01-0.30233634E-02 0.99492751E-05    3
-0.98189101E-08 0.33031825E-11-0.10638107E 04 0.36416345E 01     0.00000000    4
END2
==================================
END: Input File: "THERMO.INP"
==================================


4c. INPUT FILE #3: "CHEM.INP".

==================================
START: Input File: "CHEM.INP"
==================================
   M       +   CH3OH    =   CH3     +   OH           3.2E+18   0.        80000. 
   O2      +   CH3OH    =   CH2OH   +   HO2          4.0E+13   0.        50900. 
   OH      +   CH3OH    =   CH2OH   +   H2O          4.0E+12   0.        2000.  
   O       +   CH3OH    =   CH2OH   +   OH           1.6E+12   0.        2300.  
   H       +   CH3OH    =   CH2OH   +   H2           3.2E+13   0.        7000.  
   H       +   CH3OH    =   CH3     +   H2O          5.0E+12   0.        5300.  
   CH3     +   CH3OH    =   CH2OH   +   CH4          2.0E+11   0.        9800.  
   HO2     +   CH3OH    =   CH2OH   +   H2O2         6.3E+12   0.        19400. 
   M       +   CH2OH    =   CH2O    +   H            2.5E+13   0.        29000. 
   O2      +   CH2OH    =   CH2O    +   HO2          1.0E+12   0.        6000.  

... <content removed> ...

   H       +   O2       =   HO2     +   M       O2        2.0    N2        2.0 
   H       +   O2       =   HO2     +   M       H2O       32.5   CO2       7.5 
   H       +   O2       =   HO2     +   M       CO        2.0                   
   H       +   OH       =   H2O     +   M       O2        1.6    H2O       20.  
   H       +   OH       =   H2O     +   M       N2        1.6    CO2       7.5  
   H       +   OH       =   H2O     +   M       CO        1.6                   
==================================
END: Input File: "CHEM.INP"
==================================


4d. INPUT FILE #4: "ZMOTTO.INP".

==================================
START: Input File: "ZMOTTO.INP"
==================================
REAC
C 1.     H 4.     O 1.                       1.00             G298.15  F        
                                                                                
NAME                                                                            
 &OTTINP FREQ=9500,BORE=10.922,STROKE=10.312,ROD=17.145,TW=360.,                
 CA=129.03,CR=11.5,CSBURN=T,KASE=1359, PEXH=1.,PMFOLD=4.75,                     
  HC3=0,HA=0,HB=0,HC2=0,                                                        
   &END                                                                         
 &AFINP EQRAT=1.0,SPARK=40.,EGR=.0,THBURN=100.,VARAF=F,                         
  IFLOW=7,KINET=4,KFLAME=10,NCYCLE=12,DEBUG=F&END                                                  
 &FLOWIN DIN=5.08,DEX=5.08,BETAIN=45,BETAEX=45,LIN=2.2,LINR=2.2,          
  LEX=1.8,LEXR=1.8,AIN(1)=.95,AINR(1)=1.,AEXR(1)=.95,ALFAIN=0,ALFAEX=0,         
  EIN(2)=-20,EINR(2)=-20,EEXR(2)=-15,EEX(2)=-15,EIN(3)=2,EINR(3)=2,             
  EEXR(3)=2,EEX(3)=2,BIN(1)=.05,BINR(1)=.05,AEX(1)=1.,                          
  RIN=-1.2848969079444,-50.187346074604,1096.8283706756,-8957.6765334312,       
  39006.948871083, -100238.56274839, 156517.07679742,-145707.72737296,          
  74242.533537645,-15911.602212327,                                             
  REX= -1.7570429627131, -29.707017135839, 740.07743781757,                     
   -5709.7197760822, 22840.404174765, -53412.129620218, 75446.092321360,        
   -63124.319964495, 28632.585430403, -5383.9560171224,                         
  IVOPEN=699,IVSHUT=265,EVOPEN=465,EVSHUT=45&END                                
==================================
END: Input File: "ZMOTTO.INP"
==================================


5. Operation: Run "./bin/ZMOTTO.exe"


6. OUTPUT FILE: "zmotto.out".


==================================
START: Output File: "zmotto.out"
==================================

... <removed content> ...

1INTERNAL COMBUSTION ENGINE MODEL ZMOTTO                                    CYCLE  12    LEVEL 5    CASE NO.     1359
     REF:  ZELEZNIK, FRANK J.; AND MCBRIDE, BONNIE J.:  MODELING THE INTERNAL COMBUSTION ENGINE. NASA RP-1094, 1985.
0COMPRESSION RATIO =  11.5     RPM = 9500.0     EGR = 0.000     T(EGR) =  298.1 K     SPARK ADVANCE =  40.00 DEG
 FUEL PRESSURE = 1.00000 ATM     MANIFOLD PRESSURE = 4.75000 ATM     EXHAUST PRESSURE = 1.00000 ATM
 FLOWS ARE ISENTROPIC
 BORE = 10.922 CM     STROKE = 10.312 CM     ROD = 17.145 CM     CHAMBER AREA =129.030 SQ CM     WALL TEMP =  360.0 K
 TOTAL VOLUME = 1058.15 CC     DISPLACEMENT VOLUME =  966.13 CC
0IVOPEN = 699.00 DEG     IVSHUT = 265.00 DEG                         EVOPEN = 465.00 DEG     EVSHUT =  45.00 DEG

 EICHELBERG HEAT TRANSFER COEFICIENT
0    KINETIC FLAME    FINITE BURNING INTERVAL = 99.4 DEG    COSINE  COMBUSTION    TAU =0.0000E+00 SEC    BETA =   0.000
          AN =   0.500000  -0.500000
0                                                                            WT FRACTION   ENERGY   STATE   TEMP
          CHEMICAL FORMULA                                                                 CAL/MOL          DEG K
 FUEL    C  1.00000   H  4.00000   O  1.00000                                   1.000000   -48064.793  G    298.15
 AIR     N  1.56168   O  0.41959   AR 0.00936   C  0.00032                      1.000000      -29.791  G    298.15
0                  A/F=  6.4731   PERCENT FUEL=  13.3813   EQUIVALENCE RATIO= 1.0000   PHI=   1.0000
0                                      PERFORMANCE PARAMETERS FOR ONE CYLINDER
0      MASS PER CYCLE (G)                 MEAN INTAKE MASS FLOW RATE (G/SEC)       MEAN EXHAUST MASS FLOW RATE (G/SEC)
0     TOTAL        1.37181                      CHARGE       98.6586                      EXHAUST      99.1556
      FUEL         0.16677                      FUEL         13.2018                      CO           0.16429
      AIR          1.07953                      AIR          85.4568                      NOX          0.25544
                                                NET          98.6585                      NET          99.1556
0   ENERGY PER CYCLE (JOULES)              AVERAGE ENERGY RATE - POWER (KW)                CYCLE EFFICIENCIES

  INDICATED WORK       1420.808             INDICATED POWER       112.481                NET WORK      0.286254
  INDICATED PUMP WORK  -283.481             INDICATED PUMP POWER  -22.442                HEAT LOSS     0.076520
  HEAT LOSS             304.023             HEAT LOSS RATE         24.069                EXHAUST       0.440166
  CHEM. ENERGY         3973.145             EXHAUST POWER         138.450
0                                                    MISCELLANEOUS
0                              INDICATED MEAN EFFECTIVE PRESSURE (ATM)            14.5138
                               PUMP MEAN EFFECTIVE PRESSURE (ATM)                 -2.8958
                               MEAN TORQUE (NEWTON-METERS)                        90.5056
0COMPOSITE EXHAUST GAS MOLE FRACTIONS AT 1125.47 K  AND  1.0000 ATM      MOLECULAR WEIGHT =  27.610
      AR       0.007732      CH3OH    0.000025      CO       0.001633      CO2      0.113917      H        0.000010
      H2       0.001065      H2O      0.229456      NO       0.002370      NO2      0.000001      N2       0.643532
      O        0.000001      OH       0.000084      O2       0.000175
0FRESH CHARGE MOLE FRACTIONS AT  448.48 K  AND  4.7500 ATM      MOLECULAR WEIGHT =  29.342
      CH3OH    0.122538      AIR      0.877462
0NOTE:  INTAKE AND EXHAUST VALUES CALCULATED WHEN THE VALVES CLOSE.
0COMPUTER CYCLE TIME=   0.000 SEC
1EXHAUST GAS PROPERTIES AVERAGED FOR   6 CYCLES
0     NET EXHAUST FLOW RATE (G/SEC) = 134.1196
0     MOLECULAR WEIGHT =  27.5987
0     ENTHALPY (J/G) =  -2662.10
0     MASS AVERAGED COMPOSITION (MOLE FRACTIONS)
          AR           0.007729
          CH3OH        0.000011
          CO           0.002225
          CO2          0.113281
          H            0.000008
          H2           0.001305
          H2O          0.229137
          NO           0.003354
          N2           0.642731
          N2O          0.000002
          OH           0.000074
          O2           0.000084
          CH3OH        0.000009
          AIR          0.000049
==================================
END: Output File: "zmotto.out"
==================================

