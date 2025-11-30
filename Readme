<h1 align="center">Design and Simulation of a 3D Spacer <br> SOI-FinFET Using Silvaco ATLAS</h1>

<br>

## Overview

[cite_start]This research project investigates the design and simulation of a 3D single-fin FinFET on a Silicon-on-Insulator (SOI) substrate[cite: 38]. [cite_start]The primary objective is to address the scaling limitations inherent in traditional planar MOSFETs, such as short-channel effects and poor gate control[cite: 35, 44]. [cite_start]The study focuses on the use of the Silvaco ATLAS TCAD tool to model the multi-gate architecture, which surrounds a vertical silicon fin to provide improved electrostatic control and reduced leakage current[cite: 36].

[cite_start]The paper outlines the comprehensive device design methodology, encompassing the definition of 3D simulation meshes, specific device geometries, material assignment, and doping profiles[cite: 114]. [cite_start]The simulation performs a detailed DC analysis to obtain Transfer ($I_{D}-V_{GS}$) and Output ($I_{D}-V_{DS}$) characteristics[cite: 52]. [cite_start]The obtained results are rigorously analyzed to extract key performance metrics such as Threshold Voltage, Subthreshold Swing (SS), and DIBL, successfully validating the superiority of the FinFET design over planar structures[cite: 53, 388].

Moreover, the project explores the impact of spacer engineering and high-k dielectrics on device performance. [cite_start]The outcomes of this study contribute significantly to the understanding of nanoscale transistor design, offering valuable insights for low-power and high-performance VLSI applications[cite: 37].

<br>

## Key Objectives:

- [cite_start]Design a 3D single-fin FinFET structure on an SOI substrate using Silvaco ATLAS[cite: 50].

- [cite_start]Define appropriate simulation meshes, regions, materials (including HfO2 spacers), and doping profiles[cite: 51].

- [cite_start]Perform DC analysis to obtain $I_{D}-V_{GS}$ (transfer) and $I_{D}-V_{DS}$ (output) curves[cite: 52].

- [cite_start]Extract key performance parameters including Drain-Induced Barrier Lowering (DIBL), Subthreshold Swing (SS), and the $I_{ON}/I_{OFF}$ ratio to evaluate device performance[cite: 53].

- [cite_start]Visualize the 3D device structure and internal physical properties[cite: 49].

- [cite_start]The findings of this research validate the device's immunity to short-channel effects and its suitability for advanced nanometer technologies[cite: 376, 388].

<br>

## Abstract 

This research explores the design and simulation of a 3D Spacer SOI-FinFET using Silvaco ATLAS to analyze its electrical characteristics. [cite_start]The focus is on overcoming the scaling limitations of planar MOSFETs by utilizing a multi-gate structure that wraps around a vertical silicon fin[cite: 35]. [cite_start]The study employs a rigorous simulation methodology to define the mesh, geometry, and physics models[cite: 39]. [cite_start]Specific parameters guide the design, including a 10 nm gate length and 5 nm fin height[cite: 127]. [cite_start]DC analysis is performed to generate $I_{D}-V_{GS}$ and $I_{D}-V_{DS}$ characteristics[cite: 38]. [cite_start]Results are analyzed to extract parameters like Subthreshold Swing (65.26 mV/dec) and $I_{ON}/I_{OFF}$ ratio ($1.60 \times 10^6$), confirming the device's excellent electrostatic control and reduced leakage[cite: 371, 375]. [cite_start]This report presents the design, simulation methodology, and extraction of key device parameters[cite: 39].

<br>

## Source Code

```atlas
go atlas
TITLE S3-FinFET 3D (single-fin)

mesh three space.mult=2.5

# OPTIMIZED & ALIGNED MESH
# x-direction mesh (transport)
x.mesh loc=0.000 spac=0.001
x.mesh loc=0.001 spac=0.0005
x.mesh loc=0.005 spac=0.0005
x.mesh loc=0.0065 spac=0.0005
x.mesh loc=0.0105 spac=0.0001
x.mesh loc=0.0205 spac=0.0001
x.mesh loc=0.0245 spac=0.0005
x.mesh loc=0.0269 spac=0.0005
x.mesh loc=0.0301 spac=0.0001
x.mesh loc=0.0309 spac=0.0001
x.mesh loc=0.035 spac=0.001

# y-direction mesh
y.mesh loc=0.000 spac=0.001
y.mesh loc=0.00625 spac=0.0001
y.mesh loc=0.00725 spac=0.0001
y.mesh loc=0.008 spac=0.0001
y.mesh loc=0.009 spac=0.0001
y.mesh loc=0.012 spac=0.0001
y.mesh loc=0.013 spac=0.0001
y.mesh loc=0.093 spac=0.01
y.mesh loc=0.108 spac=0.005
y.mesh loc=0.110 spac=0.005

# z-direction mesh
z.mesh loc=0.000 spac=0.001
z.mesh loc=0.005 spac=0.0005
z.mesh loc=0.00625 spac=0.0005
z.mesh loc=0.00725 spac=0.0005
z.mesh loc=0.008 spac=0.0002
z.mesh loc=0.009 spac=0.0002
z.mesh loc=0.015 spac=0.0002
z.mesh loc=0.016 spac=0.0002
z.mesh loc=0.01675 spac=0.0005
z.mesh loc=0.01775 spac=0.0005
z.mesh loc=0.019 spac=0.0005
z.mesh loc=0.024 spac=0.001
z.mesh loc=0.030 spac=0.001

# Regions/Materials (Corrected Order)
region num=1 material=air x.min=0 x.max=0.035 y.min=0 y.max=0.110 z.min=0 z.max=0.03
region num=2 material=silicon x.min=0.005 x.max=0.0301 y.min=0.093 y.max=0.108 z.min=0.0 z.max=0.024
region num=3 material=SiO2 x.min=0.001 x.max=0.0301 y.min=0.013 y.max=0.093 z.min=0.0 z.max=0.024
region num=4 material=polysilicon x.min=0.0105 x.max=0.0205 y.min=0.00625 y.max=0.013 z.min=0.00625 z.max=0.01775
region num=5 material=HfO2 x.min=0.0065 x.max=0.0105 y.min=0 y.max=0.013 z.min=0 z.max=0.024
region num=6 material=HfO2 x.min=0.0205 x.max=0.0245 y.min=0 y.max=0.013 z.min=0 z.max=0.024
region num=7 material=SiO2 x.min=0.0105 x.max=0.0205 y.min=0.00725 y.max=0.013 z.min=0.00725 z.max=0.01675
region num=8 material=silicon x.min=0.001 x.max=0.0105 y.min=0.008 y.max=0.013 z.min=0.008 z.max=0.016
region num=9 material=silicon x.min=0.0105 x.max=0.0205 y.min=0.008 y.max=0.013 z.min=0.008 z.max=0.016
region num=10 material=silicon x.min=0.0205 x.max=0.0309 y.min=0.008 y.max=0.013 z.min=0.008 z.max=0.016

# Electrodes / Contacts
electrode name=source x.min=0.001 x.max=0.005 y.min=0.009 y.max=0.012 z.min=0.009 z.max=0.015
electrode name=drain x.min=0.0269 x.max=0.0309 y.min=0.009 y.max=0.012 z.min=0.009 z.max=0.015
electrode name=gate region=4
electrode name=substrate x.min=0.005 x.max=0.0301 y.min=0.108 y.max=0.109 z.min=0.005 z.max=0.019

# Doping
doping uniform n.type conc=1e19 region=8
doping uniform p.type conc=1e18 region=9
doping uniform n.type conc=1e19 region=10
doping uniform p.type conc=1e20 region=2

# Save initial structure
contact name=source
contact name=drain
contact name=gate workfunction=4.6
save outfile=S3FinFET_3D_init.str

# Physics models & solve init
models conmob fermi bgn srh auger cvtmob bbt.nonlocal
solve init
method newton carriers=2 itlimit=100 maxtrap=10

# DC Bias points and sweeps
# 1) ID VGS sweep for VDS 1 V (transfer curve)
solve init
solve vsubstrate=0.0
solve vdrain=1 vgate=0.0 vsource=0.0
log outfile=S3_idvgs_vds1.log master
solve name=gate vgate=0 vstep=0.1 vfinal=1.0 vdrain=1
log off
save outfile=S3_idvgs_vds1.str

# 2) ID VGS for VDS = 0.05 V (for threshold extraction)
solve init
solve vsubstrate=0.0
solve vdrain=0.05 vsource=0.0
log outfile=S3_idvgs_vds0p05.log master
solve name=gate vgate=0 vstep=0.02 vfinal=1.0 vdrain=0.05
log off
save outfile=S3_idvgs_vds0p05.str

# 3) ID-VGS for VDS = 0.8 V
solve init
solve vsubstrate=0.0
solve vdrain=0.8 vsource=0.0
log outfile=S3_idvgs_vds0p8.log master
solve name=gate vgate=0 vstep=0.1 vfinal=1.0 vdrain=0.8
log off
save outfile=S3_idvgs_vds0p8.str

# 4) ID VDS output curves
solve init
solve vsubstrate=0.0
solve vgate=1.0 vsource=0.0
log outfile=S3_idvds_vgs1p0.log master
solve name=drain vdrain=0 vstep=0.02 vfinal=1.0 vgate=1.0
log off
save outfile=S3_idvds_vgs1p0.str

# Threshold & DIBL extraction
extract init infile="S3_idvgs_vds0p05.log"
extract name="vt_lowVd" x.val from curve ((v."gate"), log10(abs(i."drain"))) where y.val=-7

extract init infile="S3_idvgs_vds0p8.log"
extract name="vt_highVd" x.val from curve ((v."gate"), log10(abs(i."drain"))) where y.val=-7

extract name="dibl_mV_per_V" ($"vt_lowVd" - $"vt_highVd")/(0.8 - 0.05)

# ION/IOFF and SS
extract init infile="S3_idvgs_vds0p8.log"
extract name="Ioff" y.val from curve (v."gate",i."drain") where x.val=0.0
extract name="Ion" y.val from curve (v."gate",i."drain") where x.val=1.0
extract name="Ion_Ioff" $Ion/$Ioff

extract name="subvt" 1.0/slope (maxslope (curve (v."gate", log10(abs(i."drain")))))

# Visualization & plotting
tonyplot S3_idvgs_vds0p8.log
tonyplot S3_idvgs_vds0p05.log
tonyplot S3_idvds_vgs1p0.log

# Save final device
save outfile=S3FinFET_3D_final.str
quit
