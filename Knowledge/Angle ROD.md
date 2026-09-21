
# 1. Angle-Only Relative Orbit Determination

The aim of this notebook is to build a simple simulation of **angle-only relative orbit determination**

We have two spacecraft:

- **Satellite A** — the observer/chaser
- **Satellite B** — the target

Satellite A observes Satellite B using an idealised camera/sensor.

The sensor does **not** measure the distance between the spacecraft. Instead, it measures the **direction** from A towards B.

The overall process is:

```text
                 TRUE WORLD
                     │
          ┌──────────┴──────────┐
          │                     │
     Satellite A           Satellite B
      Observer                Target
          │                     │
          └──────────┬──────────┘
                     │
              Relative position
                     │
                     ▼
              Line-of-sight
                     │
                     ▼
              Azimuth + Elevation
                     │
                     ▼
                Add noise
                     │
                     ▼
             Sensor measurements
```

The first version of this notebook will **simulate the measurements**.

It will not yet perform orbit determination. That will be the next step.

---

# 2. The spacecraft state

An orbit can be described using a six-dimensional state vector:

	$\vec{X} = \begin{bmatrix} \vec{r} \\ \vec{v} \end{bmatrix} = \begin{bmatrix} x\\ y\\ z\\ v_x\\ v_y\\ v_z \end{bmatrix}$

The first three components describe position:

$\vec{r} = \begin{bmatrix} x\\ y\\ z \end{bmatrix}$

and the final three describe velocity:

$\vec{v} = \begin{bmatrix} v_x\\ v_y\\ v_z \end{bmatrix}$

The state contains everything we need to describe the spacecraft's position and velocity at a particular time.

---

# 3. Two-body orbital dynamics

For the first simulation, we assume that the only force acting on each spacecraft is Earth's gravity.

This is the **two-body problem**.

The gravitational acceleration is:

$\boxed{ \mathbf{a} = -\frac{\mu}{r^3}\mathbf{r} }$

where:

- $\mathbf{r}$ is the spacecraft's position relative to the centre of Earth
- $r = |\mathbf{r}|$ is the distance from Earth's centre
- $\mu$ is Earth's gravitational parameter

For Earth:
$\mu = 3.986004418\times10^{14}\ {\rm m^3\,s^{-2}}.$

---

# 4. Writing the dynamics as a first-order system

Velocity is the derivative of position:

$\frac{d\mathbf{r}}{dt} = \mathbf{v}.$

Acceleration is the derivative of velocity:

$\frac{d\mathbf{v}}{dt} = \mathbf{a}.$

Using the two-body gravitational acceleration:

$\frac{d\mathbf{v}}{dt} = -\frac{\mu}{r^3}\mathbf{r}.$

Therefore the complete state equation is:

$\boxed{ \frac{d}{dt} \begin{bmatrix} \mathbf{r}\\ \mathbf{v} \end{bmatrix} = \begin{bmatrix} \mathbf{v}\\ -\frac{\mu}{r^3}\mathbf{r} \end{bmatrix} }$

or more compactly:
$\boxed{ \dot{\mathbf{x}}=f(\mathbf{x},t) }$

This is the differential equation we need to solve.

---

# 5. Propagating the orbit

We start with an initial state:

$\mathbf{x}(t_0)=\mathbf{x}_0.$

For example:

$\mathbf{x}_0= \begin{bmatrix} x_0\\ y_0\\ z_0\\ v_{x0}\\ v_{y0}\\ v_{z0} \end{bmatrix}$

We then solve:

$\dot{\mathbf{x}}=f(\mathbf{x},t).$

Numerically, this produces:

$\mathbf{x}(t_1), \mathbf{x}(t_2), \mathbf{x}(t_3), ...$


Conceptually:

```text
Initial state
     │
     ▼
Calculate gravity
     │
     ▼
Calculate acceleration
     │
     ▼
Integrate equations
     │
     ▼
New position + velocity
     │
     ▼
Repeat
     │
     ▼
Complete orbit
```

We therefore obtain the position and velocity of the spacecraft at every time step.

If measurements are repeated we get an orbit: $\vec{r_1}(t)$, $\vec{r_2}(t)$

The relative position of B as seen from A is:

$\boxed{ \mathbf{r}_{rel} = \mathbf{r}_B-\mathbf{r}_A }$

This equation is fundamental to relative navigation.

---

# 6. Why is the LOS vector so important?

Consider two possible target positions:

```text
A ─────── B₁
```

and:

```text
A ───────────────────────── B₂
```

The targets are at different distances, but they are in exactly the same direction.

Therefore the unit LOS vector is identical. LOS direction does not contain direct range information

This is the fundamental difficulty of angle-only orbit determination.

---

# 7. From LOS vector to angles

A camera or optical sensor could represent the LOS direction using two angles:

- **Azimuth** $\alpha$
- **Elevation** $\beta$

We can write the LOS vector as:

$\mathbf{u} = \begin{bmatrix} u_x\\ u_y\\ u_z \end{bmatrix}.$

The azimuth is:

$\boxed{ \alpha= \tan^{-1}(u_y,u_x) }$

and the elevation is:

$\boxed{ \beta=\sin^{-1}(u_z) }$

because $\mathbf{u}$ has unit magnitude.


---

# 8. Noise

A real sensor is not perfect. To compensate we introduce a random Gaussian error when simulating, $\epsilon$

$\boxed{ \alpha_{\rm measured} = \alpha_{\rm true} + \epsilon_\alpha }$

and:

$\boxed{ \beta_{\rm measured} = \beta_{\rm true} + \epsilon_\beta }$

where $\epsilon$ represents measurement noise.

A common simple model is Gaussian noise:

$\epsilon \sim \mathcal{N}(0,\sigma^2).$

This means the errors have:

- mean = 0
- standard deviation (= noise sigma) = $\sigma$

---

# 9. The actual angle-only OD problem

From here we can make a guess of the initial relative state.  Suppose the unknown initial relative state is:

$\mathbf{X}_0= \begin{bmatrix} x\\ y\\ z\\ v_x\\ v_y\\ v_z \end{bmatrix}.$

We make an initial guess:

$\mathbf{X}_0^{guess}$

which would look something like:

$\mathbf{x}_0^{guess} = \begin{bmatrix} x+\Delta x\\ y+\Delta y\\ z+\Delta z\\ v_x+\Delta v_x\\ v_y+\Delta v_y\\ v_z+\Delta v_z \end{bmatrix}$

We propagate this guess using our orbital dynamics, which gives a predicted relative position:

$\hat{\mathbf{r}}_{rel}(t)$

from which we can calculate the predicted angles:

$\hat{\alpha}(t)$ and $\hat{\beta}(t)$

We compare these with the measurements:

$\alpha(t),\quad\beta(t)$

The residuals are:

$e_\alpha(t) = \alpha(t)-\hat{\alpha}(t)$ and $e_\beta(t) = \beta(t)-\hat{\beta}(t)$

To find the initial state which makes the residual as small as possible ($e_\alpha \rightarrow 0$ and $e_\beta \rightarrow 0$) we minimise something like:

$\boxed{ J = \sum_k \left[ e_{\alpha,k}^2 + e_{\beta,k}^2 \right] }$

The result should be an estimate of the initial orbital state.