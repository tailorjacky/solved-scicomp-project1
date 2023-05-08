Download Link: https://assignmentchef.com/product/solved-scicomp-project1
<br>
Many of you will know the phenomenon that a prism refracts light, i.e. splits it up in different colors, because the refractive index of the prism varies with the frequency <em>ω </em>of light. The underlying property of the molecules forming the material is the frequency dependent polarizability, <em>α</em>(<em>ω</em>). The polarizability, like many other properties of molecules and materials, can be calculated from the basic laws of physics, here the the timedependent Schr¨odinger equation.

In the end, the polarizability for a given frequency <em>ω </em>of the incoming light is obtained as the following scalar product of two column vectors <strong>z </strong>and <strong>x</strong>:

<table width="417">

 <tbody>

  <tr>

   <td width="228"><em>α</em>(<em>ω</em>) = <strong>z</strong><em><sup>T</sup></em><strong>x                                               </strong>(1)</td>

   <td width="189">Figure 1: A dispersive prism slows light at different rates depending on the wave-length, causing refraction.</td>

  </tr>

 </tbody>

</table>

where <strong>z </strong>is a vector that can be calculated from the Schr¨odinger equation, and <strong>x </strong>is the solution to the following system of linear equations:

(<strong>E </strong>− <em>ω</em><strong>S</strong>)<strong>x </strong>= <strong>z                                                                              </strong>(2)

Here, <strong>E </strong>and <strong>S </strong>are two square matrices, and <em>ω </em>is the frequency of the incoming light. Like the column vector <strong>z</strong>, the matrices <strong>E </strong>and <strong>S </strong>are calculated from the Schr¨odinger equation, which we will not discuss further in this course.

<h1>2           Data</h1>

In this project we consider the water molecule, H<sub>2</sub>O, and its frequency dependent polarizability, <em>α</em>(<em>ω</em>). It turns out that the matrices <strong>E </strong>and <strong>S</strong>, and the column vector <strong>z</strong>, have a structure that lets us decompose the matrices into submatrices as follows:

<strong>A B</strong>

<strong>E </strong>=                    <em>,                         </em><strong>S</strong><em>,                                                                                  </em><strong>z</strong>(3)

<strong>B A</strong>

The Python-file <a href="http://www.nbi.dk/~avery/teaching/scicomp/2018/watermatrices.py">watermatrices.py</a> and the Matlab-file <a href="http://www.nbi.dk/~avery/teaching/scicomp/2018/watermatrices.mat">watermatrices.mat</a> contain the submatrices <strong>A </strong>and <strong>B</strong>, and the subvector <strong>y </strong>for a water molecule, obtained by an approximate solution to the Schr¨odinger equation.

<h1>3           Questions for Week 1</h1>

<ol>

 <li>(1) Write a small function that computes the condition number of a matrix under the max-norm:</li>

</ol>

cond

Use a library matrix inversion routine<a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a> for <strong>M</strong><sup>−1</sup>, but do program the max-norm yourself using sum, abs, and max. (2) For three frequencies, <em>ω </em>= {0<em>.</em>800<em>,</em>1<em>.</em>146<em>,</em>1<em>.</em>400}, calculate the condition number for the matrix <strong>E </strong>− <em>ω</em><strong>S</strong>. The right-hand-side <strong>z </strong>is given with 8 significant digits. How many digits in the solution <strong>x </strong>could we trust if everything else were exact? Why?

<ol>

 <li>(1) For each of the three <em>ω</em>, determine a bound on the relative forward error in the max-norm:</li>

</ol>

cond<sub>∞</sub>

for the perturbation that the frequency <em>ω </em>is changed byis given with

3 digits after the comma, how many digits in <strong>x </strong>could we be guarantee are valid if everything else were exact? Why?

<ol>

 <li>Implement three separate functions

  <ol>

   <li>L,U = lu factorize(A), which takes a square matrix <strong>M </strong>as input and returns two square matrices: A triangular matrix <strong>L </strong>and upper triangular matrix <strong>U </strong>such that</li>

  </ol></li>

</ol>

<strong>M </strong>= <strong>LU</strong>.

<ol start="2">

 <li>y = forward substitute(L,z), which takes a square lower triangular matrix <strong>L </strong>and a vector <strong>b </strong>as input, and returns the solution vector <strong>y </strong>to <strong>Ly </strong>= <strong>b</strong>.</li>

 <li>x = back substitute(U,y), which takes a square upper triangular matrix <strong>U </strong>and a vector <strong>y </strong>as input, and returns the solution vector <strong>x </strong>to <strong>Ux </strong>= <strong>y</strong>.</li>

</ol>

and test them with the linear equation

You can test your solution against a library routine.<a href="#_ftn2" name="_ftnref2"><sup>[2]</sup></a>

If you know how, try to use vector operations instead of for-loops where possible (orders of magnitude faster in Python and Matlab).

<ol>

 <li>Implement a function <em>α </em>= solve alpha(omega) for calculating the frequency-dependent polarizability <em>α</em>(<em>ω</em>) = <strong>z</strong><em><sup>T</sup></em><strong>x </strong>for water in the given approximation. This routine should solve Equation (2) by LU-factorization using your own three routines from (c). (1) Using your routine, make a table of the polarizabilities for the frequencies given in (a) and their perturbations, i.e. for <em>ω </em>= {0<em>.</em>800 ± <em>δω,</em>1<em>.</em>146 ± <em>δω,</em>1<em>.</em>400 ± <em>δω</em>}, with as before. (2)</li>

</ol>

Which error-bound is the correct one to understand the variation of the calculated polarizabilities due to the perturbation: (a) or (b) or both? Do your calculated values fall within the bounds you calculated above?

<ol>

 <li>(1) Compute a table of <em>α</em>(<em>ω</em>) for 1000 evenly spaced values in the interval [0<em>.</em>7<em>,</em>1<em>.</em>5]<a href="#_ftn3" name="_ftnref3"><sup>[3]</sup></a> using your routine from (d), and plot the values. (2) What happens to the linear system of Equation</li>

</ol>

(2) around the frequency <em>ω </em>= 1<em>.</em>146307999, and how is this reflected in <em>α</em>(<em>ω</em>)?

<h1>4           Questions for Week 2</h1>

<ol>

 <li>Implement two routines and test them with the matrix <strong>A</strong><sub>test </sub>and right-hand-side <strong>b</strong>:</li>

</ol>

<strong>A</strong>test  and <strong>b</strong>test

<ol>

 <li>Q,R = householder QR(A), which takes as input a rectangular matrix <strong>A</strong>: <em>m </em>× <em>n </em>and uses the Householder method to compute its QR decomposition. Check that <strong>Q</strong>: <em>m</em>×<em>m </em>is orthogonal, i.e., <strong>Q</strong><em><sup>T</sup></em><strong>Q </strong>= <strong>QQ</strong><em><sup>T </sup></em>= <strong>I</strong>, and that the upper triangular matrix <strong>R</strong>: <em>m </em>× <em>n </em>satisfies <strong>A </strong>= <strong>QR</strong>.</li>

 <li>A more efficient version of (f.1) that doesn’t compute the <em>m</em>×<em>m </em>matrix <strong>Q</strong>, but just stores the reflection vectors <strong>v</strong>. You can either give it the interface V,R = householder fast(A) or (as is done in practice) let the result be a combined (<em>m</em>+1)×<em>n </em>matrix VR, in which the upper <em>n </em>× <em>n </em>triangle contains R, and the <em>k</em>th column below the diagonal is <strong>v</strong><em><sub>k </sub></em>(of length <em>m </em>− <em>k</em>).</li>

 <li>˜x = least squares(A,b), which combines this routine with your back-substitution from (c.3) to compute a linear least squares fitting. It should take as input a rectangular <em>m</em>×<em>n </em>matrix <strong>A </strong>and an <em>m</em>×1 right-hand-side vector <strong>b</strong>, returning an <em>n</em>×1 approximate solution vector <strong>x</strong>˜ to <strong>A</strong><em>x</em>˜ ‘ <strong>b </strong>as output. If you did not get (f.2) to work, you can just use your solution to (f.1).</li>

</ol>

<ol>

 <li>We now want to approximate <em>α</em>(<em>ω</em>) in the interval [0<em>.</em>7<em>,ω<sub>p</sub></em>] using a polynomial</li>

</ol>

(4)

<ol>

 <li>Suggest a suitable value of <em>ω<sub>p </sub>&lt; </em>1<em>.</em> What makes this choice reasonable? (2) Find the coefficients of the polynomial using your linear least squares routine from (f)<a href="#_ftn4" name="_ftnref4"><sup>[4]</sup></a> , the table computed above, and <em>n </em>= 4. (3) Repeat the computation for <em>n </em>= 6 and compare the accuracies of the two polynomials: Plot the magnitude of the relative error (in a log<sub>10</sub>-scale) of the polynomial approximation as the difference between the <em>P</em>(<em>ω</em>) and <em>α</em>(<em>ω</em>) values. (4) How many correct digits does each approximation yield?</li>

</ol>

<ol>

 <li>We would now like to approximate <em>α</em>(<em>ω</em>) in the entire interval [0<em>.</em>7<em>,</em>1<em>.</em>5], and choose the <em>rational </em>approximating function, which is able to represent singularities:</li>

</ol>

(5)

<ol>

 <li>Why will this fail with the polynomial approximation of Problem (g)? And why can Eq. (5) do a better job? (2) Find the coefficients <em>a<sub>j </sub></em>and <em>b<sub>j </sub></em>using your linear least squares routine, the table of <em>α</em>-values computed above, and <em>n </em>= 2. You need to reformulate the expression as an linear approximation so that you can use a linear least squares fitting. Plot the error of the the rational-function approximation <em>Q</em>(<em>ω</em>) compared to <em>α</em>(<em>ω</em>) calculated by Equations (1) and (2).<a href="#_ftn5" name="_ftnref5"><sup>[5]</sup></a> (3) Repeat the computation for <em>n </em>= 4 and compare the accuracies of the two approximations quantitatively.</li>

</ol>

<a href="#_ftnref1" name="_ftn1">[1]</a> E.g. inv from numpy.linalg for Python, inv for Matlab. But only here.

<a href="#_ftnref2" name="_ftn2">[2]</a> E.g. <a href="https://docs.scipy.org/doc/numpy/reference/generated/numpy.linalg.solve.html">numpy.linalg.solve</a> in Python, or <a href="https://www.mathworks.com/help/matlab/ref/linsolve.html">linsolve</a> in Matlab.

<a href="#_ftnref3" name="_ftn3">[3]</a> Use <a href="https://docs.scipy.org/doc/numpy/reference/generated/numpy.linspace.html">linspace</a> in both Python and Matlab.

<a href="#_ftnref4" name="_ftn4">[4]</a> If you could not get your own least squares solver to work, you can use a library version for the remaining problms – but make sure to write clearly that you have done so.

<a href="#_ftnref5" name="_ftn5">[5]</a> Once you have computed the coefficients <strong>a </strong>and <strong>b</strong>, be sure to finish the construction of <em>Q</em>(<em>ω</em>) using Eq. (5), and to use this for the error. It is tempting (but wrong) to just use the linear approximation you used to find <strong>a </strong>and <strong>b</strong>, but that is linear and hence cannot represent singularities.