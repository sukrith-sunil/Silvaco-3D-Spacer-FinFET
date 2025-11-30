
# DESIGN AND SIMULATION OF A 3D SPACER SOI-FINFET USING SILVACO ATLAS

# Abstract 

FinFET is a multi-gate transistor structure designed to overcome the
scaling limitations of traditional planar MOSFETS. The gate surrounds
the vertical silicon fin, providing improved electrostatic control and
reduced leakage current. FinFETs enable continued transistor scaling in
advanced nanometer technologies with better performance and lower power
consumption. In this work, a 3D single-fin FinFET is designed and
simulated using Silvaco ATLAS to analyze its $I_D-V_{GS}$ and
$I_D-V_{DS}$ characteristics. This report presents the design,
simulation methodology, and extraction of key device parameters.

# Introduction

## Background

As MOSFET dimensions scale below deep nanometer levels, planar
transistors suffer from short-channel effects and poor gate control.
This leads to higher leakage current, reduced drive current, and
performance degradation. A device structure is required that can enhance
gate control, reduce leakage, and maintain high performance at nanoscale
dimensions. The FinFET architecture, where the gate wraps around a
vertical \"fin\" channel, provides this improved electrostatic control.

## Problem Statement and Objectives

The primary goal of this project is to design and simulate a 3D
single-fin FinFET structure using Silvaco ATLAS to analyze and evaluate
its electrical characteristics.

-   Design a 3D FinFET on an SOI (Silicon-on-Insulator) substrate.

-   Define an appropriate simulation mesh, materials, and doping
    profiles.

-   Perform DC analysis to obtain the $I_D-V_{GS}$ (transfer) and
    $I_D-V_{DS}$ (output) curves.

-   Extract key performance parameters (DIBL, SS, $I_{ON}/I_{OFF}$
    ratio) to evaluate device performance.

# Literature Survey

A review of existing research highlights various approaches to FinFET
and related device design, focusing on different materials and
structural innovations to enhance performance. The following table summarizes key features from relevant
studies.


<table>
  <thead>
    <tr>
      <th>Feature</th>
      <th>High-k SOI GaN FinFET [1]</th>
      <th>Stepped-Spacer FinFET (S3-FinFET) [2]</th>
      <th>SONOS FLASH Memory [3]</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>Main Function</strong></td>
      <td>High-performance Logic/Analog/RF</td>
      <td>High-speed, Low-power Logic (FPGA)</td>
      <td>Non-Volatile Data Storage</td>
    </tr>
    <tr>
      <td><strong>Architecture</strong></td>
      <td>Multi-gate FinFET on SOI</td>
      <td>Junctionless SOI FinFET</td>
      <td>MOSFET (ONO Stack)</td>
    </tr>
    <tr>
      <td><strong>Channel Material</strong></td>
      <td>Gallium Nitride (GaN)</td>
      <td>Silicon</td>
      <td>Silicon Channel</td>
    </tr>
    <tr>
      <td><strong>Substrate</strong></td>
      <td>SOI</td>
      <td>SOI (80 nm Buried Oxide)</td>
      <td>Not specified</td>
    </tr>
    <tr>
      <td><strong>Gate Oxide</strong></td>
      <td>HfO2 (High-k)</td>
      <td>SiO2 (0.75 nm)</td>
      <td>Tunnel/Blocking Oxide</td>
    </tr>
    <tr>
      <td><strong>Gate Length</strong></td>
      <td>8 nm</td>
      <td>5 nm</td>
      <td>100 nm (Channel)</td>
    </tr>
    <tr>
      <td><strong>Fin Dimensions</strong></td>
      <td>H: 8 nm; W: 4 nm</td>
      <td>Thickness: 8 nm</td>
      <td>N/A</td>
    </tr>
    <tr>
      <td><strong>Key Innovation</strong></td>
      <td>GaN channel + SOI + HfO2</td>
      <td>Three-layer Stepped Spacer</td>
      <td>Storage/Tunneling layer optimization</td>
    </tr>
  </tbody>
</table>

Table 2.1: Literature Survey Summary

## Paper 1

This paper, titled \"Impact on DC and analog/RF performances of SOI
based GaN FinFET considering high-k gate oxide\" and authored by Vandana
et al , investigates a highly scaled transistor structure optimized for
performance. The primary goal is to suggest an analysis of a
Silicon-on-Insulator (SOI) based Gallium Nitride (GaN) FinFET that
incorporates a high-k gate oxide. The authors analyze and compare
various performance metrics---including DC, RF/analog, and
linearity---of this proposed structure against a bulk GaN FinFET and a
conventional Si FinFET. This comparison shows how the high-k oxide and
SOI substrate enhance the performance of the GaN FinFET.

The device is an SOI-based FinFET, meaning it includes an oxide layer
(BOX) between the substrate and the fin, offering better segregation and
isolation compared to bulk FinFETs. The gate oxide layer is made of
HfO2, a high-k oxide, chosen to mitigate tunneling phenomena in thinner
gate oxides and suppress leakage current. The fin material is Gallium
Nitride (GaN), which is preferred over silicon for high-power,
high-frequency, and high-temperature applications due to its increased
velocity and large band gap. All simulations were conducted using the
Silvaco TCAD tool. For a fair comparison, structural parameters such as
gate length (Lg = 8 nm), fin height, fin width, and oxide thickness (tOX
= 1 nm) were kept uniform across all three devices. Models utilized
include the polarization model (for the GaN fin), the Albrecht model
(for low-field mobility), and the SRH model (for
generation-recombination).

Regarding key findings, the suggested structure exhibits superior DC
performance compared to the other two structures. The high mobility of
the GaN fin is the primary reason for the high ON current, which is
approximately 24.7 times higher than that of the Si FinFET. Furthermore,
the OFF current in the suggested device is approximately 8200 times
lower than that of the Si FinFET. This results in the highest current
ratio (ION/IOFF) for the proposed device, increasing it by roughly 2×10⁴
times compared to a traditional FinFET. The suggested device also
achieves a minimum Subthreshold Swing (SS) of 66 mV/dec, which is close
to the theoretical Boltzmann's Tyranny limit (60 mV/Dec) and is 35.9%
better than the Si FinFET. Electrochemically, the high-k oxide and BOX
layer contribute to reduced leakage current. A strong electric field in
the channel area improves carrier mobility and creates a potential
barrier in the off-state that is almost four times higher than the
barrier created by a Si device, resulting in much less leakage current.

In terms of analog/RF performance, the proposed structure displays an
enhanced cut-off frequency (fT), Transconductance Generation Factor
(TGF), and Transconductance Frequency Product (TFP). The combination of
SOI technology, high GaN carrier mobility, and HfO2 gate oxide results
in better high-frequency performance, achieving a maximum fT of
1.85×10¹³ Hz. The suggested device also has a very high transconductance
(gm), which is directly correlated with better switching speed.

In conclusion, the High-k SOI GaN FinFET is an effective choice for
high-frequency and high-power applications, offering significant
enhancements in DC, analog/RF, and linearity metrics compared to Bulk
GaN FinFET and Si FinFET

## Paper 2

This paper, titled \"Simulation of Optimum Stored Charge in SONOS FLASH
Memory using Silvaco TCAD,\" focuses on optimizing the charge storage
characteristics of SONOS memory cells using simulation tools. The
research presents simulations of SONOS
(Silicon-Oxide-Nitride-Oxide-Silicon) memory cells to investigate the
effect of varying the thickness of the nitride layer (NL) and tunnel
oxide layer (TL) on the net stored charge in the floating nitride gate.
SONOS memory, a non-volatile memory (NVM) valued for its straightforward
fabrication and scaling capability, operates by having charged electrons
tunnel through the tunnel oxide and get trapped in the nitride layer,
causing a threshold voltage shift that defines the memory window. The
study used the Silvaco ATLAS tool to model the SONOS memory device,
performing simulations in transient mode to replicate programming (via
channel hot electron injection) and erasing features, while varying the
NL thickness from 4 nm to 6 nm and the TL thickness from 1.5 nm to 3 nm.
The key findings on layer thickness optimization showed that as the NL
thickness increases from 4 nm to 6 nm, the net stored charge rises due
to a higher capture probability of electrons, leading to a larger
threshold voltage transition; a 6 nm NL thickness showed a maximum net
charge stored of 4.6×10-15 C. Regarding the tunnel oxide layer,
increasing the TL thickness from 1.5 nm to 3 nm results in a decrease in
the net stored charge. Decreasing the TL thickness enhances programming
speed due to the increased electric field across it. A 1.5 nm TL
thickness offered the shortest transition time with a max stored charge
of 4.4×10-15 C, while a 2 nm TL thickness offered the best consistency
and a maximum stored charge of 4.7×10-15 C. The simulation results
conclude that varying the nitride and tunnel oxide layer thicknesses
directly impacts the net charge stored and threshold voltage transition.
The study identified two optimized configurations: a nitride layer of 6
nm followed by a tunnel layer of 2 nm, and a nitride layer of 6 nm
followed by a tunnel layer of 1.5 nm, positioning SONOS-like
non-volatile memory as a promising option for high-density,
high-performance portable electronics.

## Paper 3

This article, titled \"A Stepped-Spacer FinFET Design for Enhanced
Device Performance in FPGA Applications,\" by Meysam et al, addresses
the challenges of downscaling transistors below 10 nm using novel spacer
engineering. The paper proposes a novel FinFET architecture called the
Stepped-Spacer Structured FinFET (S3-FinFET), which utilizes a
three-layer spacer stack composed of HfO₂/Si₃N₄/HfO₂ arranged in a
stepped vertical configuration. The objective is to enhance
electrostatics, suppress parasitic effects, and achieve superior
performance, making it particularly well-suited for Field-Programmable
Gate Arrays (FPGAs), where power efficiency and speed are crucial. The
S3-FinFET is a junctionless SOI FinFET with a 5 nm gate length, and its
source, drain, and channel are uniformly doped, which simplifies
fabrication. The key innovation is the three-layer stepped spacer: an
inner HfO₂ layer (adjacent to the gate), a middle Si₃N₄ layer
(dielectric buffer), and an outer HfO₂ layer (near the source/drain
junctions), with the height gradually decreasing toward the source and
drain. This arrangement enhances fringe field coupling near the gate
while screening unwanted electric field penetration near the
source/drain. Rigorous 2D TCAD simulations (Silvaco Atlas) were
performed, incorporating advanced physical models like the quantum
density-gradient model. Compared to conventional FinFETs, the S3-FinFET
achieves significant performance enhancements. Provides superior leakage
control, with a high ION/IOFF ratio exceeding (peak value 1.41G ), and
an improved Subthreshold Swing (SS) of 66.3 mV/dec. Drain-Induced
Barrier Lowering (DIBL) is excellently suppressed (36.2 mV/V) due to the
serial capacitance effect of the spacer stack. The design also exhibits
low gate-to-drain capacitance (Cgd) and a high cut-off frequency (fT),
making it suitable for high-speed applications. Reliability simulations
for Negative Bias Temperature Instability (NBTI) show a gradual recovery
after stress. The paper concludes that the S3-FinFET structure
successfully addresses scaling challenges, and its superior
electrostatic control and low Miller capacitance make it a promising,
energy-efficient candidate for next-generation reconfigurable FPGA
systems.

# Device Design and Methodology

The FinFET was modelled in Silvaco ATLAS. The process involves defining
the 3D simulation mesh, specifying the device geometry (regions),
materials, electrodes, and doping profiles. Physics models are then
applied, and simulation (solve) statements are executed.

## Device Structure

The device is a 3D single-fin n-channel FinFET on an SOI substrate. The
silicon fin is divided into N+ Source, P-type Channel, and N+ Drain
sections. A polysilicon gate wraps the channel, separated by a thin SiO2
gate oxide. HfO2 spacers isolate the gate from the source/drain.

The structure is defined geometrically using coordinates in the ATLAS
input deck. The fin itself (regions 8, 9, 10) is defined to overwrite
the Buried Oxide (BOX, region 3) and gate oxide (region 7) layers,
creating a non-planar structure where the fin sits on the BOX and is
wrapped by the gate oxide. The polysilicon gate (region 4) then wraps
around this oxide. The key dimensions of the device, extracted from the
region definitions in the simulation code, are detailed in Table



<table>
<thead>
<tr>
<th>Parameter</th>
<th>Calculation (from code)</th>
<th>Value</th>
</tr>
</thead>
<tbody>
<tr>
<td>Gate Length ($L_g$)</td>
<td>0.0205 - 0.0105 μm</td>
<td>10 nm</td>
</tr>
<tr>
<td>Fin Height ($H_{fin}$)</td>
<td>0.013 - 0.008 μm</td>
<td>5 nm</td>
</tr>
<tr>
<td>Fin Width ($W_{fin}$)</td>
<td>0.016 - 0.008 μm</td>
<td>8 nm</td>
</tr>
<tr>
<td>Gate Oxide ($T_{ox}$)</td>
<td>0.008 - 0.00725 μm</td>
<td>0.75 nm</td>
</tr>
<tr>
<td>Spacer Length ($L_{spacer}$)</td>
<td>0.0105 - 0.0065 μm</td>
<td>4 nm</td>
</tr>
<tr>
<td colspan="3"><strong>Doping Concentrations</strong></td>
</tr>
<tr>
<td>Source/Drain (N+)</td>
<td>conc=1e19</td>
<td>$1 \times 10^{19}$ cm$^{-3}$</td>
</tr>
<tr>
<td>Channel (P)</td>
<td>conc=1e18</td>
<td>$1 \times 10^{18}$ cm$^{-3}$</td>
</tr>
<tr>
<td>Substrate (P+)</td>
<td>conc=1e20</td>
<td>$1 \times 10^{20}$ cm$^{-3}$</td>
</tr>
</tbody>
</table>

Table 3.1: Key Device Dimensions and Parameters

## ATLAS Simulation Code

The complete input deck defines the structure and simulation tasks. Key
corrections included moving the gate electrode from the oxide (region 7)
to the polysilicon (region 4) and re-aligning the mesh to all new
coordinates for stability.

``` {#list:atlascode caption="ATLAS Input Deck for 3D S3-FinFET" label="list:atlascode"}
go atlas
TITLE S3-FinFET 3D (single-fin) 

mesh three space.mult=2.5

# --------------- OPTIMIZED & ALIGNED MESH ---------------
# x-direction mesh (transport)
x.mesh loc=0.000   spac=0.001
x.mesh loc=0.001   spac=0.0005  
x.mesh loc=0.005   spac=0.0005  
x.mesh loc=0.0065  spac=0.0005  
x.mesh loc=0.0105  spac=0.0001  
x.mesh loc=0.0205  spac=0.0001  
x.mesh loc=0.0245  spac=0.0005  
x.mesh loc=0.0269  spac=0.0005  
x.mesh loc=0.0301  spac=0.0001  
x.mesh loc=0.0309  spac=0.0001  
x.mesh loc=0.035   spac=0.001   

y.mesh loc=0.000    spac=0.001
y.mesh loc=0.00625  spac=0.0001  
y.mesh loc=0.00725  spac=0.0001  
y.mesh loc=0.008    spac=0.0001  
y.mesh loc=0.009    spac=0.0001  
y.mesh loc=0.012    spac=0.0001  
y.mesh loc=0.013    spac=0.0001  
y.mesh loc=0.093    spac=0.01   
y.mesh loc=0.108    spac=0.005   
y.mesh loc=0.110    spac=0.005   

z.mesh loc=0.000   spac=0.001
z.mesh loc=0.005   spac=0.0005  
z.mesh loc=0.00625 spac=0.0005  
z.mesh loc=0.00725 spac=0.0005  
z.mesh loc=0.008   spac=0.0002  
z.mesh loc=0.009   spac=0.0002  
z.mesh loc=0.015   spac=0.0002  
z.mesh loc=0.016   spac=0.0002  
z.mesh loc=0.01675 spac=0.0005  
z.mesh loc=0.01775 spac=0.0005  
z.mesh loc=0.019   spac=0.0005  
z.mesh loc=0.024   spac=0.001   
z.mesh loc=0.030   spac=0.001

# --------------- regions/materials (Corrected Order) ---------------
region num=1 material=air x.min=0 x.max=0.035 y.min=0 y.max=0.110 z.min=0 z.max=0.03
region num=2 material=silicon x.min=0.001 x.max=0.0301 y.min=0.093 y.max=0.108 z.min=0.0 z.max=0.024
region num=3 material=SiO2 x.min=0.001 x.max=0.0301 y.min=0.013 y.max=0.093 z.min=0.0 z.max=0.024   
region num=4 material=polysilicon x.min=0.0105 x.max=0.0205 y.min=0.00625 y.max=0.013 z.min=0.00625 z.max=0.01775
region num=5 material=HfO2 x.min=0.0065 x.max=0.0105 y.min=0 y.max=0.013 z.min=0 z.max=0.024
region num=6 material=HfO2 x.min=0.0205 x.max=0.0245 y.min=0 y.max=0.013 z.min=0 z.max=0.024
region num=7 material=SiO2 x.min=0.0105 x.max=0.0205 y.min=0.00725 y.max=0.013 z.min=0.00725 z.max=0.01675
region num=8 material=silicon x.min=0.001 x.max=0.0105 y.min=0.008 y.max=0.013 z.min=0.008 z.max=0.016
region num=9 material=silicon x.min=0.0105 x.max=0.0205 y.min=0.008 y.max=0.013 z.min=0.008 z.max=0.016
region num=10 material=silicon x.min=0.0205 x.max=0.0309 y.min=0.008 y.max=0.013 z.min=0.008 z.max=0.016

# --------------- electrodes / contacts (Corrected) ---------------
electrode name=source x.min=0.001 x.max=0.005 y.min=0.009 y.max=0.012 z.min=0.009 z.max=0.015
electrode name=drain x.min=0.0269 x.max=0.0309 y.min=0.009 y.max=0.012 z.min=0.009 z.max=0.015
electrode name=gate region=4
electrode name=substrate x.min=0.005 x.max=0.0301 y.min=0.108 y.max=0.109 z.min=0.005 z.max=0.019

# --------------- doping (Renumbered) ---------------
doping uniform n.type conc=1e19 region=8  
doping uniform p.type conc=1e18 region=9  
doping uniform n.type conc=1e19 region=10 
doping uniform p.type conc=1e20 region=2

# --------------- save initial structure ---------------
contact name=source
contact name=drain
contact name=gate workfunction=4.6 
save outfile=S3FinFET_3D_init.str

# --------------- physics models & solve init ---------------
models conmob fermi bgn srh auger cvtmob bbt.nonlocal
solve init
method newton carriers=2 itlimit=100 maxtrap=10

# --------------- DC Bias points and sweeps ---------------
# 1) ID–VGS sweep for VDS = 1 V (transfer curve)
solve init
solve vsubstrate=0.0 
solve vdrain=1 vgate=0.0 vsource=0.0
log outfile=S3_idvgs_vds1.log master
solve name=gate vgate=0 vstep=0.1 vfinal=1.0 vdrain=1
log off
save outfile=S3_idvgs_vds1.str

# 2) ID–VGS for VDS = 0.05 V (for threshold extraction)
solve init
solve vsubstrate=0.0 
solve vdrain=0.05 vsource=0.0
log outfile=S3_idvgs_vds0p05.log master
solve name=gate vgate=0 vstep=0.02 vfinal=1.0 vdrain=0.05
log off
save outfile=S3_idvgs_vdsn1.str

# 3) ID-VGS for VDS = 0.8 V
solve init
solve vsubstrate=0.0 
solve vdrain=0.8 vsource=0.0
log outfile=S3_idvgs_vds0p8.log master
solve name=gate vgate=0 vstep=0.1 vfinal=1.0 vdrain=0.8
log off
save outfile=S3_idvgs_vds0p8.str

# 4) ID–VDS output curves
solve init
solve vsubstrate=0.0 
solve vgate=1.0 vsource=0.0
log outfile=S3_idvds_vgs1p0.log master
solve name=drain vdrain=0 vstep=0.02 vfinal=1.0 vgate=1.0
log off
save outfile=S3_idvds_vgs1p0.str

# --------------- Threshold & DIBL extraction ---------------
extract init infile="S3_idvgs_vds0p05.log"
extract name="vt_lowVd" x.val from curve ((v."gate"), log10(abs(i."drain"))) where y.val=-7

extract init infile="S3_idvgs_vds0p8.log"
extract name="vt_highVd" x.val from curve ((v."gate"), log10(abs(i."drain"))) where y.val=-7

extract name="dibl_mV_per_V" ($"vt_lowVd" - $"vt_highVd")/(0.8 - 0.05)

# --------------- ION / IOFF and SS ---------------
extract init infile="S3_idvgs_vds0p8.log"
extract name="Ioff" y.val from curve(v."gate",i."drain") where x.val=0.0
extract name="Ion"  y.val from curve(v."gate",i."drain") where x.val=1.0
extract name="Ion_Ioff" $Ion/$Ioff

extract name="subvt" 1.0/slope(maxslope(curve(v."gate",log10(abs(i."drain")))))

# --------------- visualization & plotting ---------------
tonyplot S3_idvgs_vds0p8.log
tonyplot S3_idvgs_vds0p05.log
tonyplot S3_idvds_vgs1p0.log

# --------------- save final device ---------------
save outfile=S3FinFET_3D_final.str
quit
```

# Results and Discussion

The simulation produced log files for device characteristics and
parameter extraction.

## Device Structure Visualization

The `save` command created `S3FinFET_3D_init.str`, which was visualized
in TonyPlot. Figure 4.1 shows the 3D rendering of the device,
including the silicon fin (orange/silicon), polysilicon gate (yellow),
HfO2 spacers (brown), and SiO2 BOX (blue).

<img width="4177" height="1936" alt="FinFET struct" src="https://github.com/user-attachments/assets/876bf50b-c332-445d-ae7a-ad9f79c0e437" />

Figure 4.1 The 3D rendering of the FinFET device.

## Electrical Characteristics

$I_D-V_{GS}$ and $I_D-V_{DS}$ curves were obtained from the logged
simulation data.

<img width="800" height="600" alt="idvgs" src="https://github.com/user-attachments/assets/4cd31308-dc63-4056-affa-9b21d48a0983" />

<img width="800" height="600" alt="idvds" src="https://github.com/user-attachments/assets/b6aff934-370c-472b-8e62-4717662c2b9f" />


## Extracted Device Parameters

Key performance metrics were extracted from the simulation logs. The
results are summarized in Table 4.1



<table>
<thead>
<tr>
<th>Parameter</th>
<th>Value</th>
</tr>
</thead>
<tbody>
<tr>
<td>$V_t$ (low $V_D$) @ $I_D = 10^{-7}$ A</td>
<td>0.3034 V</td>
</tr>
<tr>
<td>$V_t$ (high $V_D$) @ $I_D = 10^{-7}$ A</td>
<td>0.2795 V</td>
</tr>
<tr>
<td>DIBL</td>
<td>31.95 mV/V</td>
</tr>
<tr>
<td>$I_{OFF}$ (at $V_{GS} = 0.0V$)</td>
<td>$6.56 \times 10^{-12}$ A</td>
</tr>
<tr>
<td>$I_{ON}$ (at $V_{GS} = 1.0V$)</td>
<td>$1.05 \times 10^{-5}$ A</td>
</tr>
<tr>
<td>$I_{ON}/I_{OFF}$ Ratio</td>
<td>$1.60 \times 10^6$</td>
</tr>
<tr>
<td>Subthreshold Slope (SS)</td>
<td>65.26 mV/decade</td>
</tr>
</tbody>
</table>

Table 4.1: Extracted Device Parameters

## Discussion

The results confirm the excellent electrostatic control of the FinFET.
The Subthreshold Slope (SS) of 65.26 mV/decade is very close to the
ideal limit of 60 mV/decade, indicating a sharp turn-on. The
Drain-Induced Barrier Lowering (DIBL) is low at 31.95 mV/V,
demonstrating high immunity to short-channel effects. The
$I_{ON}/I_{OFF}$ ratio of $1.6 \times 10^6$ shows low static power
leakage and high drive current.

# Conclusion and Future Work

## Challenges

The major challenge faced was the optimization of the 3D mesh. Achieving
a mesh fine enough for numerical convergence in critical areas (like the
fin/gate interface) without causing excessive simulation times was
difficult. Ensuring precise alignment of the mesh with all region
boundaries was critical to avoid simulation failures.

## Conclusion

A 3D Spacer SOI-FinFET was successfully designed and simulated in
Silvaco ATLAS. The simulation results, including a near-ideal SS, low
DIBL, and high $I_{ON}/I_{OFF}$ ratio, validate the device design and
its superiority over planar MOSFETs in suppressing short-channel
effects.

## Future Enhancement

-   **Spacer Engineering**: Build more complex spacers (e.g.,
    Tri-symmetric Step spacer) to further reduce the DIBL effect.

-   **Advanced Models**: Extend the simulation to include temperature
    effects, advanced mobility models, and quantum confinement models
    for more realistic behavior analysis.

-   **AC/RF Analysis**: Perform AC simulations to extract RF parameters
    ($f_T$, $f_{max}$) to evaluate the device for high-speed
    applications.

## References


1. V. S. Rajawat, A. Kumar, and B. Choudhary, "Impact on DC and analog/RF
performances of SOI based GaN FinFET considering high-k gate oxide,"
*Memories - Materials, Devices, Circuits and Systems*, vol. 5,
p. 100079, 2023, doi: 10.1016/j.memori.2023.100079.

2. Zareiee, Meysam, Mahsa Mehrad, and Abdulkarim Tawfik. \"A stepped-spacer
FinFET design for enhanced device performance in FPGA applications.\"
*Micromachines* 16.8 (2025): 867.

3. S. Singh, A. K. Sunaniya, O. P. Das, and S. K. Pandey, \"Simulation of
Optimum Stored Charge in SONOS FLASH Memory using Silvaco TCAD,\" in
*2022 6th International Conference on Devices, Circuits and Systems
(ICDCS)*, 2022, pp. 174-177.

