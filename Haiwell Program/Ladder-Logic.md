## 🧠 **COMPLETE LADDER LOGIC CIRCUIT - HAIWELL AT12M0R PLC**


---


### 🔐 **Rung 1 - Active Emergency Indication**
```ladder
|---[ X21 ]---------------------------( Y18 ) ; Yellow Light ON when EMG is active
```


---


### 🔔 **Rung 2 – Danger Indications if EMG + Full Item**
```ladder
|---[ X21 ]----[ X20 ]----------------( Y17 ) ; Red Light ON
|---[ X21 ]----[ X20 ]----------------( Y20 ) ; Buzzer ON
```


---


### ▶️ **Rung 3 – Start/Stop Latching Logic**
```ladder
|---[ X2 ]----------------------------( SET M0 ) ; Start → Activate System
|---[ X3 ]----------------------------( RST M0 ) ; Stop
|---[ X20 ]---------------------------( RST M0 ) ; Sensor full → auto stop
```


---


### ⚙️ **Rung 4 – Conveyor Motor On if System On**
```ladder
|---[ M0 ]----------------------------( Y16 ) ; Motor Conveyor ON
```


---


### ✅ **Rung 5 – Green Indicator ON if System is On**
```ladder
|---[ M0 ]----------------------------( Y19 ) ; Green Light ON
```


---


### 🧮 **Rung 6 – Counter Detection 3 Items (SB1–SB3)**
```ladder
|---[ X17 ]--+ ; Item detection
| |
|---[ X18 ]--+
| |
|---[ X19 ]--+-------------[ CU C0 K3 ] ; Count to 3
```


---


### 🔁 **Rung 7 – Validation of Ready Goods**
```ladder
|---[ C0 >= K3 ]----------------------( SET M1 ) ; M1 → Goods Ready for Pickup
```


---


### 🔽 **Rung 8 – Step 1: Twinrod Down**
```ladder
|---[ M1 ]----[ NOT X15 ]-------------( Y15 )
|---[ M1 ]----[ X15 ]------------------( TON T0 K1000 )
|---[ T0 ]-----------------------------( SET M10 )
```


---


### 🧲 **Rung 9 – Step 2: Aktifkan Suction Cup**
```ladder
|---[ M10 ]---------------------------( Y12 )
|---[ M10 ]---------------------------( TON T1 K1000 )
|---[ T1 ]----------------------------( SET M11 )
---
