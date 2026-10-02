# Doppler signal 
Notes from the paper shared to me by Agatha and Astrid *"Coupled time synchronization and relative ranging system trade-off"*

**1. Start with the two satellite positions**

$\mathbf r_B, \quad \mathbf r_B$

With the vector from one satellite to the other is

$\Delta\mathbf r = \mathbf r_i-\mathbf r_j.$

The distance between the satellites is just the magnitude of this vector:

$\rho=\|\Delta\mathbf r\|.$

Therefore,

$\rho = \sqrt{ (x_i-x_j)^2+ (y_i-y_j)^2+ (z_i-z_j)^2 }.$

Or, using the dot product,

$\boxed{ \rho^2 = \Delta\mathbf r^T\Delta\mathbf r }$


**2. Now we want range-rate**

Doppler doesn't directly tell us $\rho$. It is associated with **how quickly $\rho$ changes**:

$\dot\rho=\frac{d\rho}{dt}$

Deriving it:

We have

$$\rho^2 = \Delta\mathbf r^T\Delta\mathbf r \quad \rightarrow \quad \frac{d}{dt}(\rho^2) = \frac{d}{dt} \left( \Delta\mathbf r^T\Delta\mathbf r \right) \quad \rightarrow \quad 2\rho\dot\rho = 2\Delta\mathbf r^T\Delta\dot{\mathbf r} \quad \rightarrow \quad \dot\rho = \frac{\Delta\mathbf r^T} {\rho} \Delta\dot{\mathbf r} $$

Note that $\frac{\Delta\mathbf r}{\rho}$ is simply a **unit vector along the line joining the satellites**. Let's call it

$\hat{\boldsymbol\rho} = \frac{\Delta\mathbf r}{\|\Delta\mathbf r\|}.$

And

$\Delta\dot{\mathbf r}=\Delta\mathbf v.$

Hence,

$\boxed{ \dot\rho = \hat{\boldsymbol\rho}^{T}\Delta\mathbf v }$


**3. From range-rate to Doppler**

Now we need to connect $\dot\rho$ to frequency.

The transmitted carrier has frequency $f_c.$ 

Its wavelength is $\lambda=\frac{c}{f_c}$

Now imagine the satellites separate by one wavelength:

$\Delta\rho=\lambda.$

That corresponds to one additional cycle of phase.

The Doppler shift is

$\boxed{ D=-\frac{\dot\rho}{\lambda} }$

Substituting with the carrier wavelength we get:

$$\boxed{D = - \frac{f_c}{\lambda} \dot \rho = - \frac{f_c}{\lambda} \hat \rho^T \Delta \mathbf v}$$

Note we are ignoring clock difference and measurement error. 

**4. Received frequency**

Simple transmitted carrier:      

$s_T(t) = A\cos(2\pi f_ct)$

The received frequency is

$f_r=f_c+D.$

Therefore the receiver sees,

$S_R = A\cos(2\pi (f_R +D)t)$

**5. Sampling the received signal**

Suppose the sampling frequency is: $f_s$

Then the sampling interval is: $T_s=\frac{1}{f_s}.$

The sample times are therefore: $t_n=nT_s=\frac{n}{f_s}.$

Substitute this into our received waveform:

$\boxed{ s_R[n] = A\cos \left( 2\pi\frac{f_r}{f_s}n \right) }$

**5. Fourier transform**

$\boxed{ X[k] = \sum_{n=0}^{N-1} s_R[n] e^{-j2\pi kn/N} }$

The FFT is essentially asking:  "How much of frequency $f_k$ exists in my received samples?" for lots of candidate frequencies.

Each index $k$ corresponds to

$\boxed{ f_k=\frac{k f_s}{N} }$.

If $f_s = N$ then, $f_k=k.$

Relevant spectral peak: $\hat f_r.$

Finally,

$\boxed{ D_{\mathrm{meas}} = \hat f_r-f_c }$

 **6. Where does their $\Delta f=f_s/N$ come from?**

We established that FFT bin $k$ corresponds to

$f_k=\frac{k f_s}{N}.$

The next bin is

$f_{k+1} = \frac{(k+1)f_s}{N}.$

Subtract them:
$$\Delta f = f_{k+1}-f_k = \frac{f_s}{N}(k+1-1)$$

Therefore,

$\boxed{ \Delta f=\frac{f_s}{N}. }$

We collected $N$ samples at $f_s$ samples per second.

Therefore the total observation duration is

$T=\frac{N}{f_s}.$

Rearrange:

$\Delta f = \frac{f_s}{N} = f_s \div Tf_s = \frac{1}{T}$

This equation proves that: {longer observation $\Longrightarrow$ finer nominal FFT frequency spacing

**7. But orbital dynamics causes the problem**

Everything above quietly assumed that $D$ is constant. But we already know that 

$r(t)=f_c+D(t)$

This means we can't properly describe the received signal over a long interval as simply

$A\cos(2\pi f_rt)$

because $f_r$ isn't constant.

Instead, frequency is the **rate of change of phase**:

$$f(t) = \frac{1}{2\pi}\frac{d\phi}{dt} \quad \rightarrow \quad d\phi = 2\pi f(t)\,dt \quad \rightarrow \quad \phi(t) = 2\pi\int_0^t f(\tau)\,d\tau$$

Since

$f(\tau)=f_c+D(\tau),$

the received signal becomes

$$\boxed{ s_R(t) = A\cos \left[ 2\pi \int_0^t \left(f_c+D(\tau)\right)d\tau +\phi_0 \right]}$$
