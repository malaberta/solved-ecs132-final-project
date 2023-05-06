Download Link: https://assignmentchef.com/product/solved-ecs132-final-project
<br>
<h1>Problem A</h1>

Here you will analyze the Movie Lens data, 100K version.

Note that successive ratings by the same user are not independent, so our confidence intervals would not be correct if we were to use the data in this raw form. To cope with this problem, let Ai denote the average rating that user i gives to the various movies he/she rates. If for instance user 29 rated 3 movies, then A29 will be the average of those 3 ratings. Our data will now have the samplee size n equal to the number of users. Include in your report your R code for computing the Ai, and an outline of how it works. (I suggest you use <strong>tapply()</strong>, or just <strong>split()</strong>)

Note that we are treating the users here as a random sample from the (rather conceptual) population of all possible users, and the same for the movies.

<ol>

 <li>Find an approximate 95% confidence interval for the population mean rating by men.</li>

 <li>Find the same for women.</li>

 <li>Find an approximate 95% confidence interval for the difference between the two means.</li>

 <li>Do a significance test of the hypothesis that the male and female population means are equal.</li>

 <li>Plot histograms of the male and female ratings on the same graph.</li>

 <li>Find an approximate 95% confidence interval for the difference between the population mean number of ratings by men and women.</li>

 <li>Find an approximate 95% confidence interval for the population proportion of users who are men.</li>

 <li>Using a linear model, estimate the population regression function in which we predict rating from age and gender.

  <ul>

   <li>Form a confidence interval for <em>β<sub>age</sub></em>, and test the hypothesis that the coefficient is 0.</li>

   <li>Form a confidence interval for the mean population rating among women of age 28.</li>

  </ul></li>

</ol>

<h1>Problem B</h1>

This problem concerns some fascinating data sets at Stanford, <a href="http://wordbank.stanford.edu/">Wordbank</a><a href="http://wordbank.stanford.edu/">,</a> ”An open database of children’s vocabulary development.”

Note that the maintainers of the database have made things convenient for us, remarking,

Wordbank is open access! You can use the <a href="https://github.com/langcog/wordbankr">wordbankr</a> package to access Wordbank data from R.

Unfortunately, this in turn requires installing other packages, such as the very popular <strong>dplyr</strong>. You’d learn from this, but in this case it is probably not worth the trouble, especially since the functions the package provides don’t seem to be too relevant to what you’ll be doing in this problem.

Instead, to get the data directly, go to English vocabulary norms, and click on Download Raw Data, to acquire the file <strong>vocabulary norms data.csv</strong>.

By the way, there are some nice graphs, and the R code that generated them, throughout this Stanford Wordbank Web site, such as <a href="https://mikabr.github.io/vocab-comp/">this page</a><a href="https://mikabr.github.io/vocab-comp/">.</a> They rely on various R libraries, and thus the code is probably not worth trying to comprehend, but the graphs will give you an idea of what can be done.

This problem is quite open-ended. You will predict vocabulary size from age (in months), birth order, ethnicity, sex and mom’s education, using a linear regression model (more from a Description point of view than Prediction). Clearly you will need to form dummy variables from ethnicity and sex, but it will be up to you what to do with birth order and mom’s education. You are required to have some graphs, but it is up to you what to graph – univariate measures, bivariate relations and so on.

<h1>Some General Issues</h1>

<ul>

 <li>As you know, this Project counts both as a Homework assignment and as a substitute for an in-class Final Exam. All in all, it will require time similar to approximately 1.5 Homework assignments. <strong>START EARLY! </strong>A lot of things you think will be easy, postponable to the last minute, may prove to be much harder than you think.</li>

</ul>

A typical good-quality report will run, say, 6-7 pages, excluding code listings, graphs and figures. But there is no magic formula; a really excellent report might be shorter than this, and a mediocre one might be much longer.

<ul>

 <li><strong>Please note the open-ended nature of the Project. </strong>As you can see, these Project specs don’t take the form of ”Step 1, do this, Step 2, do that…”</li>

</ul>

<strong>Writeup:</strong>

<ul>

 <li>You are required to use LATEX to write up your report, with the output being a PDF file. I have a <a href="http://heather.cs.ucdavis.edu/~matloff/latex.html">quick tutorial</a><a href="http://heather.cs.ucdavis.edu/~matloff/latex.html">.</a> Also, all the <strong>.tex </strong>files for our own ECS 132 textbook are in <strong>http://heather.cs.ucdavis.edu/ matloff/132/PLN</strong>; by comparing output to input, you can see how to do lots of things in LATEX .</li>

</ul>

Make sure that your graphs are in either <strong>.png</strong>, <strong>.jpg </strong>or <strong>.pdf </strong>format. You may find the following code useful:

# prints        the       currently               displayed graph to the

# f i l e filename ; suffix can be ”pdf ” , ”png” or ”jpg” pr2file <em>&lt;</em>− function ( filename )

{

origdev <em>&lt;</em>− dev . cur ()

parts <em>&lt;</em>− strsplit ( filename ,”.” , fixed=TRUE) nparts <em>&lt;</em>− length ( parts [ [ 1 ] ] )

suff <em>&lt;</em>− parts [ [ 1 ] ] [ nparts ] i f ( suff == ”pdf ”) { pdf ( filename )

}

else i f ( suff == ”png”) { png( filename )

}

else jpeg ( filename ) devnum <em>&lt;</em>− dev . cur ()

dev . set ( origdev ) dev . copy(which = devnum) dev . set (devnum) dev . off () dev . set ( origdev )

}

I recommend that you use R’s <strong>ggplot2 </strong>package to generate your graphs; see my tutorial at the end of my <a href="http://heather.cs.ucdavis.edu/~matloff/132/PLN/ProbStatBook.pdf">ECS 132 book</a><a href="http://heather.cs.ucdavis.edu/~matloff/132/PLN/ProbStatBook.pdf">.</a> Or you may wish to use <strong>lattice</strong>, another popular package (for which there are many tutorials on the Web). In any case, all graphs and figures must be input by your <strong>.tex </strong>file, and appear within your report itself. The code generating the graphs must be R.

<ul>

 <li>It is of the utmost importance that your report be of <strong>PROFESSIONAL QUALITY</strong>. This means:

  <ul>

   <li>Clarity! This is very difficult, but quite achievable if you work at it. Ask friends not in the class to read it and tell you if it makes sense. Keep in mind that if you do the writeup at the last minute, the biggest casualty will be clarity.</li>

   <li>Correct spelling, grammar and usage!</li>

   <li>Professional-quality presentation! It doesn’t necessarily have to be fancy, but should not look sloppy.</li>

   <li>To be avoided like the plague:</li>

  </ul></li>

</ul>

∗ Avoid vague use of the word ”it.” Example: ”It is embarrassingly parallel”–exactly WHAT is embarrassingly parallel?

∗ ”If you wouldn’t eat it, don’t serve it.” This used to be a sign to employees in fast food restaurants, admonishing them not to serve sloppily cooked food. In our case here, ”If you wouldn’t find the premise of an analysis credible, don’t present that analysis.”

<ul>

 <li>You must include an appendix (use the LATEX <strong>appendix </strong>command), with the following contents.</li>

</ul>

∗ Your code, clearly commented, using the LATEX <strong>listings </strong>package. Also include in a a text portion (i.e. NOT in your code) an explanation of the highlights of your code.

∗ Include a brief account of ”who did what” in this Project among the various group members. Not everybody need have done exactly equal work, but something of the nature ”Transported a USB key to campus” doesn’t count as a contribution. &#x1f642; (A group acftually said this in their report one time about the contribution of a certain member.)

<ul>

 <li>Interpret all of your results; don’t just say, ”The confidence interval is (1.68,1.88).” Assume that the reader has technical background, i.e. understands quantitative issues, but has little or no background in statistics.</li>

 <li>Adhere to the UCD Code of Ethics. Having persons outside your team do any of the work, including the writing, or engaging in paid help of any kind, is unacceptable, and is a serious violation that will be referred to Student Judicial Affairs. There are probably other analyses</li>

</ul>

of this data on the Web; if you draw any ideas from any of them, that is fine but be sure to cite them.