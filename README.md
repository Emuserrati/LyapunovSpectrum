# LyapunovSpectrum
1. Calculation of the Lyapunov spectrum
If a dynamical system has a multidimensional phase space, for example, the Hénon map
and the Lorenz model, there is a set of Lyapunov exponents called the Lyapunov spectrum
that characterize the divergence of the trajectory. As an example, consider a set of initial
conditions that forms a filled sphere in phase space for the (three-dimensional) Lorenz
model. If we iterate the Lorenz equations, then the set of phase space points will deform
into another shape. If the system has a fixed point, this shape contracts to a single point.
If the system is chaotic, then the sphere will typically diverge in one direction but become
smaller in the other two directions. In this case we can define three Lyapunov exponents to
measure the deformation in three mutually perpendicular directions. These three directions
generally will not correspond to the axes of the original variables. Instead, we must use a
Gram–Schmidt orthogonalization procedure.
The algorithm for finding the Lyapunov spectrum is as follows:
1. Linearize the dynamical equations. If r is the f-component vector containing the
dynamical variables, then define ∆r as the linearized difference vector. For example,
the linearized Lorenz equations are
d∆x
dt
= −σ∆x + σ∆y
d∆y
dt
= −x∆z − z∆x + r∆x − ∆y
d∆z
dt
= x∆y + y∆x − b∆z.
2. Define f orthonormal initial values for ∆r. For example, ∆r1(0) = (1, 0, 0), ∆r2(0) =
(0, 1, 0) and ∆r3(0) = (0, 0, 1). Because these vectors appear in a linearized equation,
they do not have to be small in magnitude.
3. Iterate the original and linearized equations of motion. One iteration yields a new
vector from the original equation of motion and f new vectors ∆rα from the linearized
equations.
4. Find the orthonormal vectors ∆r
′
α
from the ∆rα using the Gram–Schmidt procedure.
That is,
∆r
′
1 =
∆r1
|∆r1|
∆r
′
2 =
∆r2−(∆r
′
1
· ∆r2)∆r
′
1
|∆r2−(∆r
′
1
· ∆r2)∆r
′
1
|
∆r
′
3 =
∆r3−(∆r
′
1
· ∆r3)∆r
′
1−(∆r
′
2
· ∆r3)∆r
′
2
|∆r3−(∆r
′
1
· ∆r3)∆r
′
1−(∆r
′
2
· ∆r3)∆r
′
2
|
.
5. Set the ∆rα(t) equal to the orthonormal vectors ∆r
′
α
(t).
6. Accumulate the running sum, Sα as Sα → Sα + log |∆rα(t)|.
7. Repeat steps 3.-6. and periodically output the approximate Lyapunov exponents
λα = (1/n)Sα, where n is the number of iterations.
To obtain a result for the Lyapunov spectrum that represents the steady state attractor,
include only data after the transient behavior has ended.
(a) Compute the Lyapunov spectrum for the Lorenz model for σ = 16, b = 4, and r = 45.92.
Try other values of the parameters and compare your results.
(b) Linearize the equations for the Hénon map,
xn+1 = yn + 1 − ax2
n
yn+1 = bxn,
and find the Lyapunov spectrum for a = 1.4 and b = 0.3.
