$
V_{g.abc} = 
\begin{bmatrix}
V_a \\
V_b \\
V_c
\end{bmatrix} = \sqrt{2} V_{rms} \cdot
\begin{bmatrix}
sin(\theta) \\
sin(\theta - \frac{2}{3} \pi) \\
sin(\theta + \frac{2}{3} \pi)
\end{bmatrix}
$

$
V_{g.dq} = 
\begin{bmatrix}
V_d \\
V_q
\end{bmatrix}=\frac{2}{3} \cdot
\begin{bmatrix}
cos(\theta) & cos(\theta+\frac{2}{3}\pi) & cos(\theta-\frac{2}{3}\pi) \\
-sin(\theta) & -sin(\theta+\frac{2}{3}\pi) & -sin(\theta-\frac{2}{3}\pi)
\end{bmatrix} \cdot
\begin{bmatrix}
V_a \\
V_b \\
V_c
\end{bmatrix}
$

$
\theta = \int \omega dt \\
\dot{\theta} = K_p V_q + \frac{1}{T_i}\int V_q dt + 60 \\
$

$
L \frac{d}{dt}I_{dq} = V_{i.dq} - V_{g.dq} \\
$

$
P_m = \frac{2}{3} (V_d I_d + V_q I_q) \\
Q_m = \frac{2}{3} (V_q I_d - V_d I_q)
$

$
P_{er} = P_r - P_m \\
I_{d.r} = K_p P_{er} + \frac{1}{T_i}\int P_{er} dt \\
$

$
Q_{er} = Q_r - Q_m \\
I_{q.r} = K_p Q_{er} + \frac{1}{T_i}\int Q_{er} dt \\
$

$
I_{d.er} = I_{d.r} - I_{d} \\
V_{i.d} = K_p I_{d.er} + \frac{1}{T_i}\int I_{d.er} dt
          + V_d - I_q \omega_{pu} L_{pu} \\
$

$
I_{q.er} = I_{q.r} - I_{q} \\
V_{i.q} = K_p I_{q.er} + \frac{1}{T_i}\int I_{q.er} dt
          + V_q + I_d \omega_{pu} L_{pu} \\
$

$
V_i=
\begin{bmatrix}
V_{i.a} \\
V_{i.b} \\
V_{i.c}
\end{bmatrix}=
\begin{bmatrix}
cos(\theta) & -sin(\theta) \\
cos(\theta+\frac{2}{3}\pi) & -sin(\theta+\frac{2}{3}\pi) \\
 cos(\theta-\frac{2}{3}\pi) & -sin(\theta-\frac{2}{3}\pi)
\end{bmatrix}\cdot
\begin{bmatrix}
V_{i.d} \\
V_{i.q}
\end{bmatrix}
$

<br>
<br>

선형화

$
\Delta V_{g.abc} = 
\begin{bmatrix}
\Delta V_a \\
\Delta V_b \\
\Delta V_c
\end{bmatrix} = \sqrt{2} \bigg( \Delta V_{rms} \cdot
\begin{bmatrix}
sin(\theta_0) \\
sin(\theta_0 - \frac{2}{3} \pi) \\
sin(\theta_0 + \frac{2}{3} \pi)
\end{bmatrix} + V_{rms0} \cdot \Delta \theta \cdot
\begin{bmatrix}
cos(\theta_0) \\
cos(\theta_0 - \frac{2}{3} \pi) \\
cos(\theta_0 + \frac{2}{3} \pi)
\end{bmatrix} \bigg)
$

$
\Delta P_m = \frac{2}{3} (\Delta V_d I_{d0} + V_{d0} \Delta I_d
                        + \Delta V_q I_{q0} + V_{q0} \Delta I_q) \\
\Delta Q_m = \frac{2}{3} (\Delta V_q I_{d0} + V_{q0} \Delta I_d
                        - \Delta V_d I_{q0} - V_{d0} \Delta I_q)
$

$
\Delta V_{g.dq} = 
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
\end{bmatrix} \biggr)
$

$
\theta = \int \omega dt \\
\Delta \dot{\theta} = K_p \Delta V_{g.q} + \frac{1}{T_i}\int \Delta V_{g.q} dt \\
$

$
L \frac{d}{dt}\Delta I_{d} = \Delta V_{i.d} - \Delta V_{g.d} \\
L \frac{d}{dt}\Delta I_{q} = \Delta V_{i.q} - \Delta V_{g.q}
$

$
\Delta P_{er} = \Delta P_r - \Delta P_m \\
\Delta I_{d.r} = K_p \Delta P_{er} + \frac{1}{T_i}\int \Delta P_{er} dt \\
$

$
\Delta Q_{er} = \Delta Q_r - \Delta Q_m \\
\Delta I_{q.r} = K_p \Delta Q_{er} + \frac{1}{T_i}\int \Delta Q_{er} dt \\
$

$
\Delta V_{i.d} = K_p (\Delta I_{d.r} - \Delta I_{d})
                + \frac{1}{T_i}\int (\Delta I_{d.r} - \Delta I_{d}) dt
                - \Delta I_q \omega_{pu} L_{pu} \\
\Delta V_{i.q} = K_p (\Delta I_{q.r} - \Delta I_{q})
                 + \frac{1}{T_i}\int (\Delta I_{q.r} - \Delta I_{q}) dt
                 + \Delta I_d \omega_{pu} L_{pu} \\
$

$
\Delta V_i =
\begin{bmatrix}
\Delta V_{i.a} \\
\Delta V_{i.b} \\
\Delta V_{i.c}
\end{bmatrix}=
\begin{bmatrix}
cos(\theta_0) & -sin(\theta_0) \\
cos(\theta_0+\frac{2}{3}\pi) & -sin(\theta_0+\frac{2}{3}\pi) \\
 cos(\theta_0-\frac{2}{3}\pi) & -sin(\theta_0-\frac{2}{3}\pi)
\end{bmatrix}\cdot
\begin{bmatrix}
\Delta V_{i.d} \\
\Delta V_{i.q}
\end{bmatrix}
$

<br>

$
x = \begin{bmatrix}
\Delta I_d \\ \Delta I_q \\ 
\int (\Delta I_{d,er}) dt \\ \int (\Delta I_{q,er}) dt \\
\int (\Delta P_{er}) dt \\ \int (\Delta Q_{er}) dt \\
\int (\Delta V_{g,q}) dt
\end{bmatrix}, \quad
u = \begin{bmatrix}
\Delta P_r \\ \Delta Q_r \\ \Delta V_{\text{rms}}
\end{bmatrix}
$


