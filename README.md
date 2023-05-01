Download Link: https://assignmentchef.com/product/solved-ele888-lab2-linear-discriminant-functions
<br>
To classify Iris datasets using linear discriminant functions.

Background

Linear discriminant functions are those functions which are either linear in the components of feature vector <em>x </em>or linear in some given set of functions of <em>x</em>. Linear classifiers can be easily built using discriminant functions and does not need the knowledge on the underlying probability densities of the given data. Linear classifiers are attractive due to their simplicity and ideal for initial, trial classifiers. The classifier parameters can be computed using a set of training samples and minimizing a criterion function.

A discriminant function <em>g</em>(<strong>x</strong>) that is linear in the component of the feature vector <strong>x </strong>can be written as:

<em>g</em>(<strong>x</strong>) = <strong>w</strong><em><sup>T</sup></em><strong>x </strong>+ <em>w</em><sub>0                                                                                                                       </sub>(1)

where <strong>w </strong>is the weight vector and <em>w</em><sub>0 </sub>is the bias or threshold. In general for a two category class problem we decide on <em>ω</em><sub>1 </sub>(class 1) by observing the feature vector <strong>x </strong>if <em>g</em>(<strong>x</strong>) <em>&gt; </em>0 and <em>ω</em><sub>2 </sub>(class 2) if <em>g</em>(<strong>x</strong>) <em>&lt; </em>0.

A generalized form of linear discriminant functions can be given as:

<em>g</em>(<strong>x</strong>) = <strong>a</strong><em><sup>T</sup></em><strong>y                                                                </strong>(2)

<table width="624">

 <tbody>

  <tr>

   <td colspan="2" width="604">where the <em>augmented feature vector y </em>and <em>augmented weight vector a </em>are given by:</td>

   <td width="20"> </td>

  </tr>

  <tr>

   <td width="318"> 1  <em>x</em>1  <em>x</em>2   <strong>y </strong>= <sub> </sub><em>. </em><sub></sub> <em>. </em>  <em>. </em> <em>x<sub>d</sub></em></td>

   <td width="286"> <em>w</em><sub>0 </sub> <em>w</em>1  <em>w</em>2  <strong>a </strong>= <sub> </sub><em>. </em><sub></sub>  <em>. </em>  <em>. </em> <em>w<sub>d</sub></em></td>

   <td width="20">(3)</td>

  </tr>

  <tr>

   <td width="317"></td>

   <td width="286"></td>

   <td width="21"></td>

  </tr>

 </tbody>

</table>

The goal is to compute the weight vector using training data samples. Gradient descent procedures are commonly used to achieve this by iteratively updating the weight vector while minimizing some criterion function. The following pseudo code outlines the basic gradient descent algorithm:

<ol>

 <li><strong>begin initialise: a</strong>, criterion <em>θ</em>, <em>η </em>(<em>.</em>), <em>k </em>= 0</li>

 <li><strong><u>do </u></strong><em>k </em>← <em>k </em>+ 1</li>

 <li><strong>a </strong>← <strong>a </strong>− <em>η</em>(<em>k</em>)∇<em>J</em>(<strong>a</strong>)</li>

 <li><strong><u>until </u></strong>|<em>η</em>(<em>k</em>)∇<em>J</em>(<strong>a</strong>)| <em>&lt; θ</em></li>

 <li><strong><u>return </u>a</strong></li>

 <li><strong><u>end</u></strong></li>

</ol>

<h2>Laboratory Exercises</h2>

Let’s first consider the following test cases from the Iris dataset investigated in Lab 1:

<ul>

 <li><strong>data set A</strong>: a 50×2 matrix (50 rows, 2 columns) of the samples from the <em>Iris Setosa </em>class, with columns as the features <em>x</em><sub>2 </sub>and <em>x</em><sub>3 </sub></li>

 <li><strong>data set B</strong>: a 50×2 matrix of the samples from the <em>Iris Vericolour </em>class, with columns as the features <em>x</em><sub>2 </sub>and <em>x</em><sub>3 </sub></li>

 <li><strong>data set C</strong>: a 50×2 matrix (50 rows, 2 columns) of the samples from the <em>Iris Virginia </em>class, with columns as the features <em>x</em><sub>2 </sub>and <em>x</em><sub>3 </sub></li>

</ul>

Using the gradient descent approach and the <em>perceptron criterion </em>compute the weight vectors and classify the given data for the conditions given below. The perceptron criterion function <em>J<sub>p</sub></em>(<strong>a</strong>) and its gradient ∇<em>J<sub>p </sub></em>are given as:

<table width="384">

 <tbody>

  <tr>

   <td width="364"><em>J<sub>p</sub></em>(<strong>a</strong>) = <sup>X</sup>(−<strong>a</strong><em><sup>T </sup></em>· <em>y</em>)<strong>y</strong>∈<em>Y</em></td>

   <td width="20">(4)</td>

  </tr>

  <tr>

   <td width="364">∇<em>J<sub>p </sub></em>= <sup>X</sup>(−<strong>y</strong>)</td>

   <td width="20">(5)</td>

  </tr>

 </tbody>

</table>

<strong>y</strong>∈<em>Y</em>

where <em>Y </em>(<strong>a</strong>) are the set of samples misclassified by <strong>a</strong>.

<ol>

 <li>Construct a new data set from A and B by setting aside 30% of the samples from these original sets (this will be used for <em>training </em>purposes). Construct a second set from the remaining 70% of data (this will be used for <em>testing</em>). Use the 30% set (training samples) to compute the weight vector for <em>η</em>(<em>k</em>) = <em>η</em>(·) = 0<em>.</em>01, <em>θ </em>= 0, and an initial value of <strong>a</strong>(0) = [001]. Limit your maximum iterations to 300 (i.e even if you cannot achieve <em>θ </em>= 0).</li>

 <li>Use the 70% set (test samples) and the weight vector computed in the previous step to calculate the classification accuracy of the classifier.</li>

 <li>Repeat the above steps by changing the data split to 70%(training) and 30%(testing).</li>

 <li>Repeat all the above for test and training sets constructed from the combination of data sets B and C (i.e. <em>Iris Vericolour </em> <em>Iris Virginia</em>)</li>

 <li>Compute the weight vectors and study the gradient descent algorithms for two different values of <em>η</em>(<em>k</em>), and the initial values of <strong>a</strong>.</li>

 <li>In each of the above steps, plot the training data on the feature space, the decision boundary for training set, the perception criterion function over the iterations and the number of iterations required for convergence.</li>

 <li>Discuss in your report the following: (i) the effect of using different sizes for training and testing data, (ii) the effect of different learning rates, threshold, initial weight values, (iii) the criterion function over the iterations, and (iv) comment on the achieved classification accuracy for the given data.</li>

</ol>