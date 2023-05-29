# MINI PROJECT 1

## Part 1

My best guess for parameters:
$$
\rho=1.2250(kg/m^3)\\
C_d = 0.35\\
C_r = 0.01\\
m = 1000(kg)\\
g = 9.8(m/s^2)\\
I_w = \frac{1}{2}m_w\cdot R^2 = 0.5\cdot 15\cdot 0.3^2 = 0.675(kg/m^2)\\
M_t = \frac{(mR^2+I_w)R_g}{R} = \frac{(1000\cdot 0.3^2+0.675)\cdot 3.5}{0.3} = 1057.875(kg/m)
$$

---

## Part 2

### a): Design a linear controller by linearizing the system

#### 1.

Total torque: $T = \frac{T_e}{M_t}-\frac{T_b R_b}{M_t}$

Speed error: $e(t) = \overline{v}-v(t)$

Then, the dynamical system becomes
$$
-\dot{e} = -ae^2+2a\overline{v}e+T-(a\overline{v}^2+c)\\
\dot{e} = ae^2-2a\overline{v}e-T+a\overline{v}^2+c
$$
where
$$
a = \frac{\rho C_d}{2 M_t} = 2.03E-04\\
c = \frac{C_r mg}{M_t} = 0.093
$$

#### 2.

In the neighborhood of the origin, $x^2 = \sum_{n=0}^\infty \frac{f^{(n)} (0)}{n!}(x)^n = 0+0+x^2+0+……$

Thus, the system can be linearized as:
$$
\dot{e} = -2a\overline{v}e-T+(a\overline{v}^2+c)
$$

#### 3.

Distance error: $y(t) = \overline{x}(t)-x(t)$

$$ T=k_1 y+k_2 e + a\overline{v}^2+c $$

#### 4.

Plug in
$$
\begin{align}
\dot{e} &= -2a\overline{v}e-k_1y-k_2e\\
&= -(2a\overline{v}+k_2)e-k_1y
\end{align}
$$
Reformulate ($e = \overline{v}-v$)
$$
\begin{align}
-\dot{v} &= -(2a\overline{v}+k_2)(\overline{v}-v)-k_1y\\
-\dot{v} &= -(2a\overline{v}+k_2)(-v)-k_1y-2a\overline{v}^2-k_2\overline{v}\\
\dot{v} &= -(2a\overline{v}+k_2)v+k_1y+2a\overline{v}^2+k_2\overline{v}
\end{align}
$$

#### 5.

$$
\begin{align}
v[t+1] &= v[t]+[-(2a\overline{v}+k_2)v[t]+k_1(\overline{x}[t]-x[t])+2a\overline{v}^2+k_2\overline{v}]\delta\\
&= v[t]+[-(2a\overline{v}+k_2)v[t]+k_1\overline{v}t-k_1x[t]+2a\overline{v}^2+k_2\overline{v}]\delta\\
&= v[t]+[-(2a\overline{v}+k_2)v[t]-k_1x[t]+2a\overline{v}^2+(k_2+k_1t)\overline{v}]\delta\\
\end{align}
$$

$$
\begin{align}
x[t+1] &= x[t]+v[t]\delta
\end{align}
$$

#### 6.

Take $\sigma = 0.05$, $\mu = 0$ for $w[t]$

### b): Directly design a controller for the nonlinear system

#### 1.

$T=ae^2+k_1 y+k_2 e + a\overline{v}^2+c$

#### 2.

Plug in
$$
\begin{align}
\dot{e} &= -(2a\overline{v}+k_2)e-k_1y
\end{align}
$$
Reformulate
$$
\begin{align}
-\dot{v} &= -(2a\overline{v}+k_2)(\overline{v}-v)-k_1y\\
\dot{v} &= -(2a\overline{v}+k_2)v+k_1y+2a\overline{v}^2+k_2\overline{v}
\end{align}
$$

#### 3.

$$
\begin{align}
v[t+1] &= v[t]+[-(2a\overline{v}+k_2)v[t]+k_1(\overline{x}[t]-x[t])+2a\overline{v}^2+k_2\overline{v}]\delta\\
&= v[t]+[-(2a\overline{v}+k_2)v[t]-k_1x[t]+2a\overline{v}^2+(k_2+k_1t)\overline{v}]\delta\\
\end{align}
$$

$$
\begin{align}
x[t+1] = x[t]+v[t]\delta
\end{align}
$$

#### 4.

Take $\sigma = 0.05$, $\mu = 0$ for $w[t]$

---

### ## Part 3

