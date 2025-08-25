$
P_m = \frac{2}{3} (V_d I_d + V_q I_q) \\
Q_m = \frac{2}{3} (V_q I_d - V_d I_q)
$

$
\begin{bmatrix}
d \\
q
\end{bmatrix}=\frac{2}{3} \cdot
\begin{bmatrix}
cos(\theta) & cos(\theta+\frac{2}{3}\pi) & cos(\theta-\frac{2}{3}\pi) \\
-sin(\theta) & -sin(\theta+\frac{2}{3}\pi) & -sin(\theta-\frac{2}{3}\pi)
\end{bmatrix} \cdot
\begin{bmatrix}
a \\
b \\
c
\end{bmatrix}
$

$
L \frac{dI}{dt} = V_i - V_g \\
$

$
\theta_{er} = \theta - \theta_{PLL} \\
\dot{\theta}_{PLL} = K_p \theta_{er} + \frac{1}{T_i}\int \theta_{er} dt + 60 \\
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
V_{d.vsc} = K_p I_{d.er} + \frac{1}{T_i}\int I_{d.er} dt
          + V_d - I_q \omega_{pu} L_{pu} \\
$

$
I_{q.er} = I_{q.r} - I_{q} \\
V_{q.vsc} = K_p I_{q.er} + \frac{1}{T_i}\int I_{q.er} dt
          + V_q + I_d \omega_{pu} L_{pu} \\
$

$
\vec{V_i}=
\begin{bmatrix}
a \\
b \\
c
\end{bmatrix}=
\begin{bmatrix}
cos(\theta) & -sin(\theta) \\
cos(\theta+\frac{2}{3}\pi) & -sin(\theta+\frac{2}{3}\pi) \\
 cos(\theta-\frac{2}{3}\pi) & -sin(\theta-\frac{2}{3}\pi)
\end{bmatrix}\cdot
\begin{bmatrix}
d \\
q
\end{bmatrix}
$
