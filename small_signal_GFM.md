입력  
$P_r, Q_r$  

<br>

출력  
$P_m, Q_m$  

<br>

계수  
$S_{base}, V_{base}, f_{base}, L_i, R_i$  

<br>

base 지정  
$I_{base} = \frac{V_{base}}{S_{base}} \\
\omega_{base} = \frac{f_{base}}{2\pi} \\
V_{pk.b} = \sqrt\frac{2}{3} \ V_{base} \\
I_{pk.b} = \sqrt\frac{2}{3} \ \frac{S_{base}}{V_{base}} \\
Z_{base} = \frac{{V_{base}}^2}{S_b} \\
L_{base} = \frac{Z_{base}}{\omega_{base}} \\
C_{base} = Z_{base} \cdot \omega_{base} \\
L_{pu} = \frac{L_i}{L_{base}} \\
R_{pu} = \frac{R_i}{Z_{base}}$

<br>

제어 식

DQ 변환  
$T(\theta) = \begin{bmatrix}
sin(\theta) & sin(\theta-\frac{2}{3}\pi) & sin(\theta+\frac{2}{3}\pi) \\
-cos(\theta) & -cos(\theta-\frac{2}{3}\pi) & -cos(\theta+\frac{2}{3}\pi)
\end{bmatrix}$

$V_{g.abc} = 
\begin{bmatrix}
V_a \\
V_b \\
V_c
\end{bmatrix} = \sqrt{2} \ V_{rms} \cdot
\begin{bmatrix}
sin(\delta) \\
sin(\delta - \frac{2}{3} \pi) \\
sin(\delta + \frac{2}{3} \pi)
\end{bmatrix} \\$

$V_{dq} = 
\begin{bmatrix}
V_d \\
V_q
\end{bmatrix}=\frac{2}{3} \cdot
T(\theta) \cdot V_{g.abc}\\$

$V_{dq.pu} = \frac{V_{dq}}{V_{pk.b}} \\ $

<br>

Droop Control (APC)  
$\omega_{pu} = D_p (P_{r.pu} - P_{m.pu}) + \omega_{r.pu} \\
\omega = \omega_{base} \cdot \omega_{pu} \\
\dot{\theta} = \omega \\$

<br>

Power Calculation  
$\begin{bmatrix}
P_{m} \\ Q_{m}
\end{bmatrix} =
\begin{bmatrix}
V_d & V_q \\
-V_q & V_d
\end{bmatrix} \cdot 
\begin{bmatrix}
I_d \\ I_q
\end{bmatrix} \\$

$\begin{bmatrix}
P_{m.pu} \\ Q_{m.pu}
\end{bmatrix} = \frac{1}{S_{base}}
\begin{bmatrix}
P_{m} \\ Q_{m}
\end{bmatrix} \\$

$\begin{bmatrix}
P_{r.pu} \\ Q_{r.pu}
\end{bmatrix} = \frac{1}{S_{base}}
\begin{bmatrix}
P_{r} \\ Q_{r}
\end{bmatrix} \\$

<br>

Power Control (RPC)  
$Q_{er} = Q_{r.pu} - Q_{m.pu} \\
V_{d.r.pu} = K_{p} Q_{er} + \frac{1}{T_{i}}\int Q_{er} dt \\$

<br>

Voltage Control  
$V_{d.er} = V_{d.r.pu} - V_{d.pu} \\
I_{d.r.pu} = K_{p} V_{d.er} + \frac{1}{T_{i}}\int V_{d.er} dt
          + I_{d.pu}FF - V_{q.pu} \omega_{pu} C_{pu}(=0) \\$

$V_{q.er} = V_{q.r.pu}(=0) - V_{q.pu} \\
I_{q.r.pu} = K_{p} V_{q.er} + \frac{1}{T_{i}}\int V_{q.er} dt
          + I_{q.pu}FF + V_{d.pu} \omega_{pu} C_{pu}(=0) \\$

$FF = Feed Forward$, 여기서는 0으로 간주

<br>

Current Control  
$I_{d.er} = I_{d.r.pu} - I_{d.pu} \\
V_{i.d.pu} = K_{p} I_{d.er} + \frac{1}{T_{i}}\int I_{d.er} dt
          + V_{d.pu} - I_{q.pu} \omega_{pu} L_{pu} \\$

$I_{q.er} = I_{q.r.pu} - I_{q.pu} \\
V_{i.q.pu} = K_{p} I_{q.er} + \frac{1}{T_{i}}\int I_{q.er} dt
          + V_{q.pu} + I_{d.pu} \omega_{pu} L_{pu} \\$

<br>

Current Dynamic (Filter)  
$J = 
\begin{bmatrix}
0 & -1 \\
1 & 0
\end{bmatrix}, \quad
\frac{d}{dt}T(\theta) = \omega \ J \cdot T(\theta)$

$L_i \frac{d}{dt} I_{abc} = V_{i.abc} - V_{g.abc} - R_i \ I_{abc} \\
I_{dq} = \frac{2}{3} \ T(\theta) \cdot I_{abc}, \quad
V_{dq} = \frac{2}{3} \ T(\theta) \cdot V_{g.abc} \\
\frac{d}{dt} I_{dq} = \frac{2}{3} \ \frac{d}{dt} T(\theta) \cdot I_{abc} +  \frac{2}{3} \ T(\theta) \cdot \frac{d}{dt} I_{abc} \\
\qquad \ = \omega \ J \cdot \frac{2}{3} \ T(\theta) \cdot I_{abc} + \frac{1}{L_i} \frac{2}{3} \ T(\theta) \cdot (V_{i.abc} - V_{g.abc} - R_i \ I_{bac})\\
\qquad \ = \omega \ J \cdot I_{dq} + \frac{1}{L_i} (V_{i.dq} - V_{dq} - R_i \ I_{dq})
$

$\dot {\begin{bmatrix}
I_{d} \\ I_{q}
\end{bmatrix}} = 
\begin{bmatrix}
-\omega I_q + \frac{1}{L_i} (V_{i.d} - V_d - R_i I_d) \\ \omega I_d + \frac{1}{L_i} (V_{i.q} - V_q - R_i I_q)
\end{bmatrix}
$

$\dot I_{dq.pu} = \frac{1}{I_{pk.b}} \dot{I_{dq}}$

<br>
<br>

선형화

DQ 변환  
$\Delta V_{dq} =
\begin{bmatrix}
0 \\ V_{pk.b} \Delta \theta
\end{bmatrix}$

$\Delta V_{dq.pu} = \frac{\Delta V_{dq}}{V_{pk.b}} \\ $

<br>

Droop Control (APC)  
$\Delta \omega_{pu} = D_p (\Delta P_{r.pu} - \Delta P_{m.pu}) + \Delta \omega_{r.pu} \\
\Delta \omega = \omega_{base} \cdot \Delta \omega_{pu} \\
\dot{\Delta \theta} = \Delta \omega \\$

<br>

Power Calculation  
$\begin{bmatrix}
\Delta P_{m} \\ \Delta Q_{m}
\end{bmatrix} =
\begin{bmatrix}
V_{d0}& \Delta V_d & V_{q0} & \Delta V_q \\
-V_{q0} & -\Delta V_q & V_{d0} & \Delta V_d \\
\end{bmatrix} \cdot 
\begin{bmatrix}
\Delta I_d \\ I_{d0} \\ \Delta I_q \\ I_{q0}
\end{bmatrix} \\$

$\begin{bmatrix}
\Delta P_{m.pu} \\ \Delta Q_{m.pu}
\end{bmatrix} = \frac{1}{S_{base}}
\begin{bmatrix}
\Delta P_{m} \\ \Delta Q_{m}
\end{bmatrix} \\$

$\begin{bmatrix}
\Delta P_{r.pu} \\ \Delta Q_{r.pu}
\end{bmatrix} = \frac{1}{S_{base}}
\begin{bmatrix}
\Delta P_{r} \\ \Delta Q_{r}
\end{bmatrix} \\$

<br>

Power Control (RPC)  
$\Delta Q_{er} = \Delta Q_{r.pu} - \Delta Q_{m.pu} \\
\Delta V_{d.r.pu} = K_p \Delta Q_{er} + \frac{1}{T_i}\int \Delta Q_{er} dt \\
\Delta \xi_Q = \int \Delta Q_{er} dt$

<br>

Voltage Control  
$\Delta V_{d.er} = \Delta V_{d.r.pu} - \Delta V_{d.pu} \\
\Delta I_{d.r.pu} = K_p \Delta V_{d.er} + \frac{1}{T_i}\int \Delta V_{d.er} dt
                + \Delta I_{d.pu}FF
                - C_{pu}(=0) (V_{q.pu0} \Delta \omega_{pu} + \Delta V_{q.pu} \omega_{pu0})  \\
\Delta \xi_{Vd} = \int \Delta V_{d.er} dt$

$\Delta V_{q.er} = \Delta V_{q.r.pu}(=0) - \Delta V_{q.pu} \\
\Delta I_{q.r.pu} = K_p \Delta V_{q.er} + \frac{1}{T_i}\int \Delta V_{q.er} dt
                + \Delta I_{q.pu}FF
                + C_{pu}(=0) (V_{d.pu0} \Delta \omega_{pu} + \Delta V_{d.pu} \omega_{pu0}) \\
\Delta \xi_{Vq} = \int \Delta V_{q.er} dt$

$FF = Feed Forward$, 여기서는 0으로 간주

<br>

Current Controller  
$\Delta I_{d.er} = \Delta I_{d.r.pu} - \Delta I_{d.pu} \\
\Delta V_{i.d.pu} = K_p \Delta I_{d.er} + \frac{1}{T_i}\int \Delta I_{d.er} dt
                + \Delta V_{d.pu}
                - L_{pu}\ (I_{q.pu0} \Delta \omega_{pu} + \omega_{pu0} \Delta I_{q.pu}) \\
\Delta \xi_{Id} = \int \Delta I_{d.er} dt$

$\Delta I_{q.er} = \Delta I_{q.r.pu} - \Delta I_{q.pu} \\
\Delta V_{i.q.pu} = K_p \Delta I_{q.er} + \frac{1}{T_i}\int \Delta I_{q.er} dt
                + \Delta V_{q.pu}
                + L_{pu} \ (I_{d.pu0} \Delta \omega_{pu} + \omega_{pu0} \Delta I_{d.pu}) \\
\Delta \xi_{Iq} = \int \Delta I_{q.er} dt$

<br>

$\dot {\begin{bmatrix}
\Delta I_{d} \\ \Delta I_{q}
\end{bmatrix}} = 
\begin{bmatrix}
-(\omega_0 \Delta I_q + I_{q0} \Delta \omega) + \frac{1}{L_i} (\Delta V_{i.d} - \Delta V_{d} - R_i \Delta I_{d}) \\
\omega_0 \Delta I_d + I_{d0} \Delta \omega + \frac{1}{L_i} (\Delta V_{i.q} - \Delta V_{q} - R_i \Delta I_{q})
\end{bmatrix}
$

$\dot I_{dq.pu} = \frac{1}{I_{pk.b}} \dot{I_{dq}}$

<br>

$\Delta x = \begin{bmatrix}
\Delta \theta \\ \Delta I_d \\ \Delta I_q \\
\Delta \xi_Q \\ \Delta \xi_{Vd} \\ \Delta \xi_{Vq} \\
\Delta \xi_{Id} \\ \Delta \xi_{Iq} 
\end{bmatrix}$

$\Delta u = \begin{bmatrix}
\Delta P_r & \Delta Q_r \\
\end{bmatrix}
$

$y = \begin{bmatrix}
\Delta P_m \\ \Delta Q_m \\
\end{bmatrix}
$