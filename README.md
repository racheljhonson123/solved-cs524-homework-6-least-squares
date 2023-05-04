Download Link: https://assignmentchef.com/product/solved-cs524-homework-6-least-squares
<br>



<ol>

 <li><strong>Hovercraft rendezvous. </strong>Alice and Bob are cruising on Lake Mendota in their hovercrafts. Each hovercraft has the following dynamics:</li>

</ol>

Dynamics of each hovercraft:

At time <em>t </em>(in seconds), <em>x<sub>t </sub></em><sup>∈</sup>R<sup>2 </sup>is the position (in miles), <em>v<sub>t </sub></em><sup>∈</sup>R<sup>2 </sup>is the velocity (in miles per hour), and <em>u<sub>t </sub></em>∈ R<sup>2 </sup>is the thrust in normalized units. At <em>t </em>= 1, Alice has a speed of 20 mph going North, and Bob is located half a mile East of Alice, moving due East at 30 mph. Alice and Bob would like to rendezvous at exactly <em>t </em>= 60 seconds. The location where they meet is up to you.

<ol>

 <li>Find the sequence of thruster inputs for Alice (<em>u</em><sup>A</sup>) and Bob (<em>u</em><sup>B</sup>) that achieves a rendezvous at <em>t </em>= 60 while minimizing the total energy used by both hovercraft:</li>

</ol>

total energy =

Plot the trajectories of each hovercraft to verify that they do indeed rendezvous.

<ol>

 <li>In addition to arriving at the same place at the same time, Alice and Bob should also make sure their velocity vectors match when they rendezvous (otherwise, they might crash!) Solve the rendezvous problem again with the additional velocity matching constraint and plot the resulting trajectories. Is the optimal rendezvous location different from the one found in the first part?</li>

</ol>

<ol start="2">

 <li><strong>Quadratic form positivity. </strong>You’re presented with the constraint:</li>

</ol>

2<em>x</em><sup>2 </sup>+ 2<em>y</em><sup>2 </sup>+ 9<em>z</em><sup>2 </sup>+ 8<em>xy </em>− 6<em>xz </em>− 6<em>yz </em>≤ 1 (1) <strong>a) </strong>Write the constraint (1) in the standard form <em>v</em><sup>T</sup><em>Qv </em>≤ 1. Where <em>Q </em>is a symmetric matrix. What is <em>Q </em>and what is <em>v</em>?

<ol>

 <li><strong>b) </strong>It turns out the above constraint is <em>not </em> In other words, the set of (<em>x,y,z</em>) satisfying the constraint (1) is not an ellipsoid. Explain why this is the case.</li>

</ol>

<strong>Note: </strong>you can perform an orthogonal decomposition of a symmetric matrix <em>Q </em>in Julia like this:

(L,U) = eigen(Q)                            # L is the vector of eigenvalues and U is orthogonal

U * diagm(L) * U’                                                # this is equal to Q (as long as Q was symmetric to begin with)

<ol>

 <li>We can also write the constraint (1) using norms by putting it in the form:</li>

</ol>

k<em>Av</em>k<sup>2</sup>−k<em>Bv</em>k<sup>2 </sup>≤ 1

What is <em>v </em>and what are the matrices <em>A </em>and <em>B </em>that make the constraint above equivalent to (1)?

<ol>

 <li>Explain how to find a direction for vector (<em>x,y,z</em>) such that k(<em>x,y,z</em>)k<sub>2 </sub>(norm) is unbounded (can be made arbitrarily large) while satisfying the constraint (1).</li>

 <li><strong>Lasso regression. </strong>Consider the data (<em>x,y</em>) plotted below, available in csv.</li>

</ol>

In this problem, we will investigate different approaches for performing polynomial regression.

<ol start="15">

 <li>Perform ordinary polynomial regression. Make plots that show the data as well as the best fit to the data for polynomials of degree <em>d </em>= 5 and <em>d </em>= 15. Also comment on the magnitudes of the coefficients in the resulting polynomial fits. Are they small or large?</li>

 <li>In order to get smaller coefficients, we will use ridge regression (<em>L</em><sub>2 </sub>regularization). Re-solve the <em>d </em>= 15 version of the problem using a regularization parameter <em>λ </em>= 10<sup>−6 </sup>and plot the new fit. How does the fit change compared to the non-regularized case of part a? How do the magnitudes of the coefficients in the resulting polynomial fit change?</li>

 <li>Our model is still complicated because it has so many parameters. One way to simplify our model is to look for a sparse model (where many of the parameters are zero). Solve the <em>d </em>= 15 problem once more, but this time use the Lasso (<em>L</em><sub>1 </sub>regularization). Start with a large <em>λ </em>and progressively make <em>λ </em>smaller until you obtain a model with a small number of parameters that fits the data reasonably well. <strong>Note: </strong>due to numerical inaccuracy in the solver, you may need to round very small coefficients (say less than 10<sup>−5</sup>) down to zero. Plot the resulting fit.</li>

</ol>