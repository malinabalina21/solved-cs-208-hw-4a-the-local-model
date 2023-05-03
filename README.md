Download Link: https://assignmentchef.com/product/solved-cs-208-hw-4a-the-local-model
<br>
<ol>

 <li><strong>Learning Conjunctions in the SQ Model: </strong>In this problem, you will see a simple example of a machine learning algorithm that works in the statistical query (SQ) model, and will evaluate how it performs under both local and centralized DP.</li>

</ol>

The set-up is that we are given a data set <em>D </em>= ((<em>x</em><sub>1</sub><em>,y</em><sub>1</sub>)<em>,…,</em>(<em>x<sub>n</sub>,y<sub>n</sub></em>)) where <em>x<sub>i </sub></em>∈ {0<em>,</em>1}<em><sup>d </sup></em>and <em>y<sub>i </sub></em>∈ {0<em>,</em>1}. We want a (local or centralized) differentially private algorithm <em>M</em>(<em>D</em>) that outputs a subset <em>S</em>ˆ ⊆ {1<em>,…,d</em>} of the variables such that the conjunction of the <em>x</em>-variables in <em>S</em>ˆ predicts the <em>y </em>variable well.

Specifically, following Valiant’s PAC model, we will measure utility as follows. Suppose that <em>D </em>consists of <em>n </em>iid draws from an (unknown) distribution P on {0<em>,</em>1}<em><sup>d </sup></em>× {0<em>,</em>1}. Furthermore, suppose that there is an (unknown) set <em>S </em>⊆ {1<em>,…,d</em>} such that

<em>.</em>

That is, <em>y </em>can be <em>perfectly </em>predicted by some conjunction.<a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a> (Note that here and below, the notation (<em>x,y</em>) refers to a <em>single </em>labelled example drawn from P, not a dataset of <em>n </em>such values. We will use <em>D </em>= ((<em>x</em><sub>1</sub><em>,y</em><sub>1</sub>)<em>,…,</em>(<em>x<sub>n</sub>,y<sub>n</sub></em>)) for the dataset.)

Then the goal of <em>M </em>is to output <em>S</em>ˆ that minimizes the expected classification error:

<em> .</em>

(This is an instantiation of the “risk minimization” problem described in the April 8 lecture, though you will not need anything from that lecture for this homework problem.)

The SQ algorithm is based on estimating the following quantity for each variable <em>j </em>= 1<em>,…,d</em>: [<em>x</em>[<em>j</em>] = 0 ∧ <em>y </em>= 1]<em>.</em>

P

As shown in section, we have:

<ul>

 <li>For each <em>j </em>∈ <em>S</em>, we have <em>p<sub>j </sub></em>= 0.</li>

</ul>

1

<ul>

 <li>If <em>S</em>ˆ ⊇ <em>S</em>, then the false positive rate of <em>S</em>ˆ is 0.</li>

 <li>The false negative rate of <em>S</em><sup>ˆ </sup>is at most <sup>P</sup><em><sub>j</sub></em><sub>∈<em>S</em></sub>ˆ <em>p<sub>j</sub>.</em></li>

</ul>

Based on these observations, an SQ algorithm <em>M </em>for learning conjunctions works as follows:

<ul>

 <li>Using the dataset <em>D</em>, obtain an estimate ˆ<em>p<sub>j </sub></em>of <em>p<sub>j </sub></em>for <em>j </em>= 1<em>,…,d</em>.</li>

 <li>Output <em>S</em>ˆ = {<em>j </em>∈ [<em>d</em>] : <em>p</em>ˆ<em><sub>j </sub></em>≤ <em>t</em>} for an appropriate (small) threshold <em>t</em>.</li>

</ul>

You should do the following:

<ul>

 <li>Describe and implement centralized and local DP versions of the above SQ algorithm, dividing the privacy budget equally among each of the <em>d </em>estimates ˆ<em>p<sub>j</sub></em>. Keep the threshold <em>t </em>as a free parameter that you can choose.</li>

 <li>For both the centralized and local DP algorithms you give in Part 1a, analytically estimate Pr[<em>S</em>ˆ + <em>S</em>] as a function of <em>t</em>, <em>n</em>, <em>ε</em>, and |<em>S</em>|. Feel free to use a normal approximation for the binomial distribution, and to describe your estimate in terms of the CDF of a standard normal distribution. Use this as a guide to determine a setting of <em>t </em>to ensure that Pr[<em>S</em>ˆ + <em>S</em>] ≤ <em>.</em>1 as a function of <em>n</em>, <em>d</em>, and <em>ε </em>in each of the two settings, using the fact that |<em>S</em>| ≤ <em>d</em>.</li>

 <li>An interest group targets a particular online political advertisement to users of a social media platform based on a conjunction of demographic characteristics. The users who are targeted with the advertisement are recorded. You get differentially private access (at to the user data and attempt to learn what demographic combination was being focused on.</li>

</ul>

In the dataset CaPUMS5Full.csv are a number of potential demographic characteristics that might have been used for targeting: (sex, married, black, asian, collegedegree, employed, militaryservice, uscitizen, disability, englishability). The variable targeted records those individuals who received the ad. Use your DP algorithms to learn a classifier to predict targeted=1 (which we have artificially created) from these variables. Demonstrate whether your centralized and local algorithms would succeed. Also, use a bootstrap to compare the false positive rates and false negative rates of the two methods as a function of <em>n</em>.

If useful, also included in this dataset is the variable blackfemale that you can use to test if your implementation correctly picks up black and female as the constituent parts. There is also a test dataset, hw4testdata.csv, that contains x1 ··· x10, and y=x1∧x2∧x3.

2

<a href="#_ftnref1" name="_ftn1">[1]</a> This is known as the “realizable” case of learning, as opposed to the “agnostic” case, where no conjunction classifies perfectly, but the goal is to find one that does as well as possible.