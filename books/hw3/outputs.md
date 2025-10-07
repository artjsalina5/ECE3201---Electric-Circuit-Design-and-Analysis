# ECE3201 HW 3

## Question 6.65

### Circuit Netlist

```spice
.model DIODE D(Vfwd=0.7, Roff=100M, Ron=.1u)
.model NPNQ NPN(Bf=100)
.model PNPQ PNP(Bf=100)
R1 N001 N006 80k
R3 N001 N002 2k
R4 N005 0 2k
R5 N007 0 100
R6 N001 N003 100
Q1 N004 N006 N005 0 NPNQ
Q2 PNPQ N007 N005 N003 0 PNP
V1 N001 0 9
D1 N002 N004 DIODE
R2 N008 0 80k
D2 N008 N006 DIODE
.op
.backanno
.end
````

### Operating Point

| Node / Device | Value         | Type              |
| ------------- | ------------- | ----------------- |
| V(n001)       | 9.00000 V     | voltage           |
| V(n002)       | 8.26664 V     | voltage           |
| V(n003)       | 4.35333 V     | voltage           |
| V(vb1)        | 4.35333 V     | voltage           |
| V(vc1)        | 8.26661 V     | voltage           |
| V(vc2)        | 4.37862 V     | voltage           |
| V(ve1)        | 3.60505 V     | voltage           |
| V(ve2)        | 4.47816 V     | voltage           |
| I(D1)         | 3.66678e-4 A  | current           |
| I(D2)         | -5.44166e-5 A | current           |
| I(R1)         | 5.80834e-5 A  | current           |
| I(R2)         | 5.44166e-5 A  | current           |
| I(R3)         | 3.66678e-4 A  | current           |
| I(R4)         | 1.80253e-3 A  | current           |
| I(R5)         | 4.37862e-2 A  | current           |
| I(R6)         | 4.52184e-2 A  | current           |
| I(V1)         | -4.56432e-2 A | current           |
| Ib(Q1)        | 3.66677e-6 A  | base current      |
| Ic(Q1)        | 3.66678e-4 A  | collector current |
| Ie(Q1)        | -3.70344e-4 A | emitter current   |
| Ib(PNPQ)      | -1.43218e-3 A | base current      |
| Ic(PNPQ)      | -4.37862e-2 A | collector current |
| Ie(PNPQ)      | 4.52184e-2 A  | emitter current   |

---

### Modified Circuit (With 2k Resistor)

```spice
.model DIODE D(Vfwd=0.7, Roff=100M, Ron=.1u)
.model NPNQ NPN(Bf=100)
.model PNPQ PNP(Bf=100)
R1 N001 VB1 80k
R3 N001 N002 2k
R4 VE1 0 2k
R5 VC2 0 100
R6 N001 VE2 100
Q1 VC1 VB1 VE1 0 NPNQ
Q2 PNPQ VC2 VE1 VE2 0 PNP
V1 N001 0 9
D1 N002 VC1 DIODE
R2 N003 0 80k
D2 N003 VB1 DIODE
R7 VC2 VE1 2k
.op
.backanno
.end
```

### Operating Point (With R7)

| Node / Device | Value         | Type              |
| ------------- | ------------- | ----------------- |
| V(n001)       | 9.00000 V     | voltage           |
| V(n002)       | 8.28960 V     | voltage           |
| V(n003)       | 4.35792 V     | voltage           |
| V(vb1)        | 4.35792 V     | voltage           |
| V(vc1)        | 8.28956 V     | voltage           |
| V(vc2)        | 4.37201 V     | voltage           |
| V(ve1)        | 3.61046 V     | voltage           |
| V(ve2)        | 4.48334 V     | voltage           |
| I(D1)         | 3.55202e-4 A  | current           |
| I(D2)         | -5.44740e-5 A | current           |
| I(R1)         | 5.80260e-5 A  | current           |
| I(R2)         | 5.44740e-5 A  | current           |
| I(R3)         | 3.55202e-4 A  | current           |
| I(R4)         | 1.80523e-3 A  | current           |
| I(R5)         | 4.37201e-2 A  | current           |
| I(R6)         | 4.51666e-2 A  | current           |
| I(R7)         | 3.80775e-4 A  | current           |
| I(V1)         | -4.55798e-2 A | current           |
| Ib(Q1)        | 3.55202e-6 A  | base current      |
| Ic(Q1)        | 3.55202e-4 A  | collector current |
| Ie(Q1)        | -3.58754e-4 A | emitter current   |
| Ib(PNPQ)      | -1.06570e-3 A | base current      |
| Ic(PNPQ)      | -4.41009e-2 A | collector current |
| Ie(PNPQ)      | 4.51666e-2 A  | emitter current   |

---

## Question 6.66

### Circuit Netlist

```spice
.model NPNQ NPN(Bf=100)
.model PNPQ PNP(Bf=100)
R1 N001 V2 9.1k
R3 N001 V5 5.1k
R4 V4 0 4.3k
Q1 V5 V3 V4 0 NPNQ
Q2 PNPQ V3 V1 V2 0 PNP
V1 N001 0 3
R2 V3 0 9.1k
R8 V1 0 100k
.op
.backanno
.end
```

### Operating Point

| Node / Device | Value         | Type              |
| ------------- | ------------- | ----------------- |
| V(n001)       | 3.00000 V     | voltage           |
| V(v1)         | 0.772487 V    | voltage           |
| V(v2)         | 1.50075 V     | voltage           |
| V(v3)         | 1.41454 V     | voltage           |
| V(v4)         | 0.687966 V    | voltage           |
| V(v5)         | 2.19212 V     | voltage           |
| I(R1)         | 1.64753e-4 A  | current           |
| I(R2)         | 1.55444e-4 A  | current           |
| I(R3)         | 1.58408e-4 A  | current           |
| I(R4)         | 1.59992e-4 A  | current           |
| I(R8)         | 7.72487e-6 A  | current           |
| I(V1)         | -3.23161e-4 A | current           |
| Ib(Q1)        | 1.58408e-6 A  | base current      |
| Ic(Q1)        | 1.58408e-4 A  | collector current |
| Ie(Q1)        | -1.59992e-4 A | emitter current   |
| Ib(PNPQ)      | -7.72487e-6 A | base current      |
| Ic(PNPQ)      | -1.57028e-4 A | collector current |
| Ie(PNPQ)      | 1.64753e-4 A  | emitter current   |
