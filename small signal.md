입력  
$P_r, Q_r$  

<br>

출력  
$P_m, Q_m$  

<br>

계수  
$S_b, V_b, f_b, L_i$  

<br>

base 지정  
$\omega_b = \frac{f_b}{2\pi} \\
V_{pk.b} = \frac{V_b}{\sqrt{6}} \\
I_{pk.b} = \frac{S_b}{V_b \sqrt{6}} \\
Z_b = \frac{{V_b}^2}{S_b} \\
L_b = \frac{Z_b}{\omega_b} \\
C_b = Z_b \cdot \omega_b \\
L_{pu} = \frac{L_i}{L_b} \\$

<br>

제어 식  
$V_{g.abc} = 
\begin{bmatrix}
V_a \\
V_b \\
V_c
\end{bmatrix} = \sqrt{2} V_{b} \cdot
\begin{bmatrix}
sin(\theta) \\
sin(\theta - \frac{2}{3} \pi) \\
sin(\theta + \frac{2}{3} \pi)
\end{bmatrix} \\$

$\begin{bmatrix}
V_d \\
V_q
\end{bmatrix}=\frac{2}{3 } \cdot
\begin{bmatrix}
cos(\theta) & cos(\theta+\frac{2}{3}\pi) & cos(\theta-\frac{2}{3}\pi) \\
-sin(\theta) & -sin(\theta+\frac{2}{3}\pi) & -sin(\theta-\frac{2}{3}\pi)
\end{bmatrix} \cdot
\begin{bmatrix}
V_a \\
V_b \\
V_c
\end{bmatrix} \\$

$\begin{bmatrix}
V_{d.pu} \\
V_{q.pu}
\end{bmatrix} = \frac{1}{V_{pk.b}}
\begin{bmatrix}
V_{d} \\
V_{q}
\end{bmatrix} \\$

<br>

$\theta = \int \omega dt \\
\dot{\theta} = K_{p.pll} V_q + \frac{1}{T_{i.pll}}\int V_q dt + 60 \\
\omega_{pu} = \frac{\omega}{\omega_b} \\$

<br>

$\dot {\begin{bmatrix}
I_{d.pu} \\ I_{q.pu}
\end{bmatrix}} = \frac{\omega_b}{L_{pu}} \bigg(
\begin{bmatrix}
V_{i.d.pu} \\ V_{i.q.pu}
\end{bmatrix} - 
\begin{bmatrix}
V_{d.pu} \\ V_{q.pu}
\end{bmatrix} \bigg)
$

<br>

$\begin{bmatrix}
P_{m} \\ Q_{m}
\end{bmatrix} = \frac{2}{3} 
\begin{bmatrix}
V_d & V_q \\
V_q & -V_d
\end{bmatrix} \cdot 
\begin{bmatrix}
I_d \\ I_q
\end{bmatrix} \\$

$\begin{bmatrix}
P_{m.pu} \\ Q_{m.pu}
\end{bmatrix} = \frac{1}{S_b}
\begin{bmatrix}
P_{m} \\ Q_{m}
\end{bmatrix} \\$

$\begin{bmatrix}
P_{r.pu} \\ Q_{r.pu}
\end{bmatrix} = \frac{1}{S_b}
\begin{bmatrix}
P_{r} \\ Q_{r}
\end{bmatrix} \\$

<br>

$P_{er} = P_{r.pu} - P_{m.pu} \\
I_{d.r.pu} = K_{p.p} P_{er} + \frac{1}{T_{i.P}}\int P_{er} dt \\$

$Q_{er} = Q_{r.pu} - Q_{m.pu} \\
I_{q.r} = K_{p.q} Q_{er} + \frac{1}{T_{i.q}}\int Q_{er} dt \\$

<br>

$I_{d.er} = I_{d.r.pu} - I_{d.pu} \\
V_{i.d.pu} = K_{p.id} I_{d.er} + \frac{1}{T_{i.id}}\int I_{d.er} dt
          + V_{d.pu} - I_{q.pu} \omega_{pu} L_{pu} \\$

$I_{q.er} = I_{q.r.pu} - I_{q.pu} \\
V_{i.q.pu} = K_{p.iq} I_{q.er} + \frac{1}{T_{i.iq}}\int I_{q.er} dt
          + V_{q.pu} + I_{d.pu} \omega_{pu} L_{pu} \\$

<br>
<br>

선형화

$\Delta V_{g.abc} = 
\begin{bmatrix}
\Delta V_a \\
\Delta V_b \\
\Delta V_c
\end{bmatrix} = \sqrt{2} V_b \bigg(
\begin{bmatrix}
sin(\theta_0) \\
sin(\theta_0 - \frac{2}{3} \pi) \\
sin(\theta_0 + \frac{2}{3} \pi)
\end{bmatrix} + \Delta \theta \cdot
\begin{bmatrix}
cos(\theta_0) \\
cos(\theta_0 - \frac{2}{3} \pi) \\
cos(\theta_0 + \frac{2}{3} \pi)
\end{bmatrix} \bigg)$

$\Delta V_{g.dq} = 
\begin{bmatrix}
\Delta V_d \\
\Delta V_q
\end{bmatrix} = \frac{2}{3} \biggr(
\begin{bmatrix}
cos(\theta_0) & cos(\theta_0+\frac{2}{3}\pi) & cos(\theta_0-\frac{2}{3}\pi) \\
-sin(\theta_0) & -sin(\theta_0+\frac{2}{3}\pi) & -sin(\theta_0-\frac{2}{3}\pi)
\end{bmatrix} \cdot
\begin{bmatrix}
\Delta V_a \\
\Delta V_b \\
\Delta V_c 
\end{bmatrix} + \Delta \theta \cdot
\begin{bmatrix}
-sin(\theta_0) & -sin(\theta_0+\frac{2}{3}\pi) & -sin(\theta_0-\frac{2}{3}\pi) \\
-cos(\theta_0) & -cos(\theta_0+\frac{2}{3}\pi) & -cos(\theta_0-\frac{2}{3}\pi)
\end{bmatrix} \cdot
\begin{bmatrix}
\Delta V_a \\
\Delta V_b \\
\Delta V_c 
\end{bmatrix} \biggr)$

$\Delta V_{g.dq.pu} = 
\begin{bmatrix}
\Delta V_{d.pu} \\
\Delta V_{q.pu}
\end{bmatrix} = \frac{1}{V_{pk.b}}
\begin{bmatrix}
\Delta V_d \\
\Delta V_q
\end{bmatrix}$

<br>

$\begin{bmatrix}
\Delta P_{m} \\ \Delta Q_{m}
\end{bmatrix} = \frac{2}{3} 
\begin{bmatrix}
\Delta V_d & V_{d0} & \Delta V_q & V_{q0} \\
\Delta V_q & V_{q0} & -\Delta V_d & -V_{d0}
\end{bmatrix} \cdot 
\begin{bmatrix}
I_{d0} \\ \Delta I_d \\ I_{q0} \\ \Delta I_q
\end{bmatrix} \\$

$\begin{bmatrix}
\Delta P_{m.pu} \\ \Delta Q_{m.pu}
\end{bmatrix} = \frac{1}{S_b}
\begin{bmatrix}
\Delta P_{m} \\ \Delta Q_{m}
\end{bmatrix} \\$

$\begin{bmatrix}
\Delta P_{r.pu} \\ \Delta Q_{r.pu}
\end{bmatrix} = \frac{1}{S_b}
\begin{bmatrix}
\Delta P_{r} \\ \Delta Q_{r}
\end{bmatrix} \\$

<br>

$\Delta \theta = \int (\omega_0 + \Delta \omega) dt \\
\dot{\Delta \theta} = K_{p.pll} \Delta V_{q}
                    + \frac{1}{T_{i.pll}}\int \Delta V_{q} dt \\
\Delta \omega_{pu} = \frac{\omega}{\omega_b}$

$\theta = \int \omega dt \\
\dot{\theta} = K_{p.pll} V_q + \frac{1}{T_{i.pll}}\int V_q dt + 60 \\
\omega_{pu} = \frac{\omega}{\omega_b} \\$

<br>

$\dot {\begin{bmatrix}
\Delta I_{d.pu} \\ \Delta I_{q.pu}
\end{bmatrix}} = \frac{\omega_b}{L_{pu}} \bigg(
\begin{bmatrix}
\Delta V_{i.d.pu} \\ \Delta V_{i.q.pu}
\end{bmatrix} - 
\begin{bmatrix}
\Delta V_{d.pu} \\ \Delta V_{q.pu}
\end{bmatrix} \bigg)$

<br>

$\Delta P_{er} = \Delta P_{r.pu} - \Delta P_{m.pu} \\
\Delta I_{d.r.pu} = K_p \Delta P_{er} + \frac{1}{T_i}\int \Delta P_{er} dt \\$

$\Delta Q_{er} = \Delta Q_{r.pu} - \Delta Q_{m.pu} \\
\Delta I_{q.r.pu} = K_p \Delta Q_{er} + \frac{1}{T_i}\int \Delta Q_{er} dt \\$

$\Delta V_{i.d.pu} = K_p (\Delta I_{d.r.pu} - \Delta I_{d.pu})
                + \frac{1}{T_i}\int (\Delta I_{d.r.pu} - \Delta I_{d.pu}) dt
                - \Delta I_{q.pu} \cdot \omega_{pu} \cdot L_{pu} \\
\Delta V_{i.q.pu} = K_p (\Delta I_{q.r.pu} - \Delta I_{q.pu})
                 + \frac{1}{T_i}\int (\Delta I_{q.r.pu} - \Delta I_{q.pu}) dt
                 + \Delta I_{d.pu} \cdot \omega_{pu} \cdot L_{pu} \\$

<br>

$\Delta x = \begin{bmatrix}
\Delta I_d \\ \Delta I_q \\ \Delta \theta \\
\int (\Delta I_{d,er}) dt \\ \int (\Delta I_{q,er}) dt \\
\int (\Delta P_{er}) dt \\ \int (\Delta Q_{er}) dt \\
\int (\Delta V_{g,q}) dt
\end{bmatrix}$

$\Delta  = \begin{bmatrix}
\Delta P_r & \Delta Q_r \\
\end{bmatrix}
$

$y = \begin{bmatrix}
\Delta P_m \\ \Delta Q_m \\
\end{bmatrix}
$