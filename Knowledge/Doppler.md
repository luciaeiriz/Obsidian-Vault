# Special Relativity and the Relativistic Doppler Effect

### Lorentz Transformations
When an event occurs at $(x,y,z)$ at time $t$ in $S$, there's a corresponding $(x',y',z')$ and time $t'$ in a second frame $S'$, where $S'$  moves at speed $u$ in the $+x$ direction relative to $S$. 
$$x' = \frac{x - ut}{\sqrt{1 - u^2 / c^2}}, \quad y' = y, \quad z' = z, \quad t' = \frac{t - (xu / c^2)}{\sqrt{1 - u^2/c^2}}$$ Useful to define the Lorentz factor:
$$\boxed{\gamma= \frac{1}{\sqrt{1-u^2/c^2}}}$$

So that: 
$$x' = \gamma(x-ut) \quad and \quad t' = \gamma\left(t-\frac{ux}{c^2}\right)$$

We can then have velocity transformations: 
$$v'_x = \frac{v_x - u}{1 - uv_x/c^2}, \quad v_x = \frac{v'_x + u}{1 +uv'_x/c^2}$$

### Proper Time and Time Dilation
The time interval between two events depends on the reference frame.

When the two events occur at the **same position** in a particular reference frame, the measured time interval is called the **proper time** $\Delta t_0$.

For a clock moving relative to an observer, the observer measures a longer time interval than the proper time:
$$\boxed{\Delta t=\gamma\Delta t_0} \quad or \quad \boxed{\Delta t=\frac{\Delta t_0}{\sqrt{1-u^2/c^2}}}$$
The important point for the Doppler effect is that **successive emission events occur at the same position in the source's rest frame**, so the time between emissions is a proper-time interval.

### Frequency and Period
Frequency is the number of cycles per unit time: $f=\frac{1}{T}$ where (T) is the period.

For a source emitting light at frequency $f_0$, the time between successive emissions in the source's rest frame is

$\boxed{\Delta t_0=\frac{1}{f_0}  }$

This will be the starting point for deriving the relativistic Doppler effect.

### Relative Motion and the Doppler Effect
The Doppler effect is the change in the observed frequency of a wave due to relative motion between the source and observer.

For electromagnetic waves, the situation is different from classical sound waves because there is no medium that defines a preferred reference frame.

Since the speed of light is invariant, $c=\text{constant in every inertial frame,}$ the Doppler effect must be derived using **special relativity**.

Consider a source and observer with relative speed $u$, and choose the observer's rest frame SS. The source therefore moves with speed $u$ relative to the observer.

We distinguish two cases:

1. **Source and observer approaching**
The observed frequency is greater than the emitted frequency:
$f>f_0.$

2. **Source and observer receding**
The observed frequency is lower than the emitted frequency:
$f<f_0.$

### Relativistic Doppler Effect
For motion directly along the line joining source and observer, the relativistic Doppler effect can be derived by considering the time between successive emission events and the time between the corresponding arrival events

- $S'$ : source's rest frame
- $S$ : observer's rest frame
- $u$ : relative speed between source and observer
- $f_0$ : frequency measured in the source's rest frame
- $f$ : frequency measured by the observer.

#### Approaching

The source emits two successive light pulses. Because the source is stationary in $S'$ we can say that $\Delta x' = 0$

Therefore the time between them is the proper time: $\Delta t' = \Delta t_0$

and so, $\Delta t_0 = 1 / f_0$

Using the inverse Lorentz transformation for time:
$$t = \gamma \left(t' + \frac{ux'}{c^2}\right) \quad \rightarrow \quad \Delta t = \gamma \left(\Delta t' + \frac{\Delta ux'}{c^2}\right)$$

Hence:
$$\Delta t = \gamma \Delta t' = \gamma \Delta t_0$$

In the observer's frame, the two emission events are separated by a longer time interval. This, however, is not the observed period because the observer doesn't measure the time between the two emission events. It measures the time between **receiving** the two light signals.

In the observer's frame, the source moves towards the observer between the two emission events. Therefore, the second pulse has a shorter distance to travel than the first pulse.

Time between arrivals at the observer is $\Delta t_{obs}$, during this time interval between emission $\Delta t$, the source moves a distance $u \Delta t$. Light travels at $c$, so the time interval is reduced by $u \Delta t / c$, and so:

$$\Delta t_{obs} = \Delta t - \frac{u \Delta t}{c} = \Delta t \left(1 - \frac{u}{c}\right)$$

remember that $\Delta t = \gamma \Delta t_0$
$$\Delta t_{obs} = \gamma \Delta_t0 \left(1 - \frac{u}{c} \right) $$
Converting into frequency:
$$f = \frac{1}{\Delta t_{obs}} = \frac{1}{\gamma \Delta t_0 (1 - u/c)}$$
since $f_0 = 1 / \Delta t_0$,
$$f = \frac{f_0}{\gamma (1 - u/c)},$$substituting for $\gamma$ we get:
$$\boxed{f=f_0 \sqrt{ \frac{c+u}{c-u}}} \quad or \quad \boxed{f=f_0\sqrt{\frac{1+u/c}{1-u/c}}}$$
#### Receding
Receding is the same except $\Delta t_{obs} = \Delta  t + \frac{u \Delta t}{c}$

and so $\Delta t_{obs} = \gamma \Delta t_0 (1 + \frac{u}{c})$

Putting it together we get
$$\boxed{f=f_0 \sqrt{ \frac{c-u}{c+u}}} \quad or \quad \boxed{f=f_0\sqrt{\frac{1-u/c}{1+u/c}}}$$


### Low-Velocity Limit
When $u\ll c,$ the relativistic Doppler equation reduces approximately to

$$\boxed{\frac{\Delta f}{f_0}\approx\frac{u}{c}}$$
for approaching motion, where

$$\Delta f=f-f_0.$$
Thus, the familiar first-order Doppler result is recovered in the low-velocity limit.


### Connection to Relative Velocity
The one-dimensional equation above assumes that the relative motion is directly along the line connecting the source and observer.

For arbitrary relative motion, only the component of the relative velocity along the line of sight contributes to the first-order Doppler shift.

This component is called the radial velocity.

If $\mathbf v_{\mathrm{rel}}$ is the relative velocity and $\hat{\mathbf r}$ is a unit vector along the line joining source and observer, then

$$\boxed{v_r=\mathbf v_{\mathrm{rel}}\cdot\hat{\mathbf r}}$$

This provides the starting point for extending the Doppler effect to relative motion in three dimensions.

### Source and Observer Both Moving
Suppose that the source has velocity $v_s$ and the observer has velocity $v_o$ along the same line, both measured in the original inertial frame $S$. 

Instead of applying the Doppler formula separately to each velocity, we can transform into the observer's rest frame $S'$. 

In that frame ($S'$), $v'_o = 0$

The source velocity measured in this frame is obtained using the relativistic velocity transformation:
$$v'_s = \frac{v_s - v_o}{1 - v_ov_s/c^2}$$Relative velocity is therefore: $u = v'_s - v'_o \quad \text{and so} \quad u = v'_s$

Hence,
$$u - \frac{v_s - v_o}{1 - v_sv_o/c^2}$$
Therefore, when both source and observer are moving, the relativistic Doppler equation can still be written in terms of a single relative velocity:
$$f = f_0 \sqrt{\frac{1 + u/c}{1-u/c}} \quad \rightarrow \quad f = f_0 \sqrt{\frac{1 + \frac{1}{c}(\frac{v_s - v_o}{1 - v_sv_oo/c^2})}{1-\frac{1}{c}(\frac{v_s - v_o}{1 - v_sv_o/c^2})}}$$
Simplifying:
$$\boxed{f = f_0 \sqrt{\frac{1+ v_s/c}{1 - v_s/c} * \frac{1-v_o/c}{1 + v_o/c}}}$$
where $u$ is the velocity of the source measured in the observer's rest frame, rather than simply $v_s - v_o$.



