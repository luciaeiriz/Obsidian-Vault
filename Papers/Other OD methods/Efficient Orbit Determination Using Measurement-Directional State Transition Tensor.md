---
Title: Efficient Orbit Determination Using Measurement-Directional State Transition Tensor
Year: 2025
Authors: Xingyu Zhou, Dong Qiao, Macdonald Malcolm, Xiangyu Li
Tags:
  - Estimation
  - Observability
---
Zotero PDF Link: [Full Text PDF](zotero://select/library/items/Q8NFG3RZ)
Related: OD, Estimation methodology

### Persistent Notes
The paper is fundamentally about improving the **estimator used for orbit determination**, rather than about a particular measurement such as Doppler. The authors propose a **Measurement-Directional State Transition Tensor (MDSTT)** and incorporate it into a high-order Extended Kalman Filter (HEKF). Their motivation is that ordinary EKFs can perform poorly when orbital dynamics are highly nonlinear, while higher-order filters are computationally expensive.

The generic OD formulation is:

$\dot{\mathbf{x}} = f(\mathbf{x},t)+\omega z=h(x)+ν\mathbf{z}=h(\mathbf{x})+\nu$

where $\mathbf{x}\in\mathbb{R}^6$ is the orbital state, $f$ is the dynamics model, and importantly for us,

$\boxed{\mathbf z=h(\mathbf x)+\nu}$

is the **measurement model**.

That is where Doppler _could_ enter. For Doppler OD, $h(\mathbf x)$ could be your Doppler/range-rate measurement model. But **this paper does not develop a Doppler measurement model**.

Their numerical experiments concern **cislunar orbit determination**, where nonlinear dynamics are particularly important.

#### Relevance to RODINN
The authors divide state-space directions according to how strongly the **measurement constrains them**. They use the gradient of the measurement model,

$\frac{\partial h(\mathbf x)}{\partial \mathbf x},$

to identify directions where the measurement strongly constrains the orbital state and directions where uncertainty remains large.

That connects conceptually to the question you've been asking throughout our Doppler discussion:

The introduction mentions previous work where DNNs have been used to improve high-order orbit-estimation algorithms

### In-text annotations



%% Import Date: 2026-09-15T14:39:37.366+01:00 %%
