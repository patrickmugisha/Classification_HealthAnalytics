# Classification_HealthAnalytics

Scenario:<br>
I has access to the company's medical claims database. With this access, i am able to generate two data sets. The first is a list of people who have suffered heart attacks, with an attribute indicating whether or not they have had more than one; and the second is a list of those who have had a first heart attack, but not a second. The former data set, comprised of 138 observations, will serve as our training data; while the latter, comprised of 690 peoples' data, will be for scoring. my responsibility is to help this latter group of people avoid becoming second heart attack victims.

<h1>Table of Contents<span class="tocSkip"></span></h1>
<div class="toc"><ul class="toc-item"><li><span><a href="#Classification" data-toc-modified-id="Classification-1">Classification</a></span><ul class="toc-item"><li><ul class="toc-item"><li><span><a href="#Classification-vs-Regression" data-toc-modified-id="Classification-vs-Regression-1.0.1">Classification vs Regression</a></span></li></ul></li></ul></li><li><span><a href="#Health-Analytics" data-toc-modified-id="Health-Analytics-2">Health Analytics</a></span><ul class="toc-item"><li><ul class="toc-item"><li><span><a href="#Can-healthcare-providers-use-data-analytics-to-predict-diseases-(e.g.,-2nd-heart-attack)-and-hospital-readmission?" data-toc-modified-id="Can-healthcare-providers-use-data-analytics-to-predict-diseases-(e.g.,-2nd-heart-attack)-and-hospital-readmission?-2.0.1">Can healthcare providers use data analytics to predict diseases (e.g., 2nd heart attack) and hospital readmission?</a></span></li><li><span><a href="#Dataset" data-toc-modified-id="Dataset-2.0.2">Dataset</a></span></li><li><span><a href="#Examining-Variables" data-toc-modified-id="Examining-Variables-2.0.3">Examining Variables</a></span></li><li><span><a href="#1.-Import-Packages" data-toc-modified-id="1.-Import-Packages-2.0.4">1. Import Packages</a></span></li><li><span><a href="#2.-Loading-data" data-toc-modified-id="2.-Loading-data-2.0.5">2. Loading data</a></span></li><li><span><a href="#3.-Data-wrangling-&amp;-ETL:-Data-cleaningg-&amp;-transformation" data-toc-modified-id="3.-Data-wrangling-&amp;-ETL:-Data-cleaningg-&amp;-transformation-2.0.6">3. Data wrangling &amp; ETL: Data cleaningg &amp; transformation</a></span></li><li><span><a href="#4.-A.-Exploratory-data-analysis" data-toc-modified-id="4.-A.-Exploratory-data-analysis-2.0.7">4. A. Exploratory data analysis</a></span></li><li><span><a href="#4.-B.-Data-visualization-&amp;-business-intelligence" data-toc-modified-id="4.-B.-Data-visualization-&amp;-business-intelligence-2.0.8">4. B. Data visualization &amp; business intelligence</a></span></li><li><span><a href="#Model-Building-(Predictive/Classification-analytics)" data-toc-modified-id="Model-Building-(Predictive/Classification-analytics)-2.0.9">Model Building (Predictive/Classification analytics)</a></span><ul class="toc-item"><li><span><a href="#Top-10-algorithms-&amp;-methods-used-by-Data-Scientists." data-toc-modified-id="Top-10-algorithms-&amp;-methods-used-by-Data-Scientists.-2.0.9.1">Top 10 algorithms &amp; methods used by Data Scientists.</a></span></li></ul></li></ul></li></ul></li><li><span><a href="#Decision-Tree" data-toc-modified-id="Decision-Tree-3">Decision Tree</a></span><ul class="toc-item"><li><ul class="toc-item"><li><span><a href="#Categorical-to-Dummy-Variables" data-toc-modified-id="Categorical-to-Dummy-Variables-3.0.1">Categorical to Dummy Variables</a></span></li><li><span><a href="#Model-Building-&amp;-Validation" data-toc-modified-id="Model-Building-&amp;-Validation-3.0.2">Model Building &amp; Validation</a></span></li><li><span><a href="#Visualizing-decision-tree" data-toc-modified-id="Visualizing-decision-tree-3.0.3">Visualizing decision tree</a></span><ul class="toc-item"><li><span><a href="#Create-a-decision-tree-(This-is-a-new-appoach-using-scikit-learn,-instead-of-other-packages)" data-toc-modified-id="Create-a-decision-tree-(This-is-a-new-appoach-using-scikit-learn,-instead-of-other-packages)-3.0.3.1">Create a decision tree (This is a new appoach using scikit-learn, instead of other packages)</a></span></li><li><span><a href="#Interpreting-decision-tree" data-toc-modified-id="Interpreting-decision-tree-3.0.3.2">Interpreting decision tree</a></span></li><li><span><a href="#What-if-your-decision-tree-looks-too-complicated-to-be-practical?" data-toc-modified-id="What-if-your-decision-tree-looks-too-complicated-to-be-practical?-3.0.3.3">What if your decision tree looks too complicated to be practical?</a></span></li></ul></li></ul></li><li><span><a href="#Model-Deployement:-Make-Predictions-on-the-new-dataset-(scoring-dataset)" data-toc-modified-id="Model-Deployement:-Make-Predictions-on-the-new-dataset-(scoring-dataset)-3.1">Model Deployement: Make Predictions on the new dataset (scoring dataset)</a></span></li></ul></li><li><span><a href="#Appendixes" data-toc-modified-id="Appendixes-4">Appendixes</a></span><ul class="toc-item"><li><span><a href="#10-fold-cross-validation" data-toc-modified-id="10-fold-cross-validation-4.1">10 fold cross validation</a></span><ul class="toc-item"><li><ul class="toc-item"><li><span><a href="#Split-validation" data-toc-modified-id="Split-validation-4.1.0.1">Split validation</a></span></li><li><span><a href="#Cross-validation-(CV)-or-10-fold-CV" data-toc-modified-id="Cross-validation-(CV)-or-10-fold-CV-4.1.0.2">Cross validation (CV) or 10-fold CV</a></span></li></ul></li></ul></li><li><span><a href="#Random-Forest-(Ensemble-model):-Very-Important-!!!" data-toc-modified-id="Random-Forest-(Ensemble-model):-Very-Important-!!!-4.2">Random Forest (Ensemble model): Very Important !!!</a></span><ul class="toc-item"><li><ul class="toc-item"><li><span><a href="#Feature-Selection-(or-Feature-Engineering):-Selecting-important-variables" data-toc-modified-id="Feature-Selection-(or-Feature-Engineering):-Selecting-important-variables-4.2.0.1">Feature Selection (or Feature Engineering): Selecting important variables</a></span></li><li><span><a href="#Make-predictions-on-the-new-dataset-(scoring-dataset-without-y-value)" data-toc-modified-id="Make-predictions-on-the-new-dataset-(scoring-dataset-without-y-value)-4.2.0.2">Make predictions on the new dataset (scoring dataset without y value)</a></span></li></ul></li></ul></li><li><span><a href="#Model-Evaluation-with-Receiver-Operating-Characteristic-(ROC)" data-toc-modified-id="Model-Evaluation-with-Receiver-Operating-Characteristic-(ROC)-4.3">Model Evaluation with Receiver Operating Characteristic (ROC)</a></span><ul class="toc-item"><li><span><a href="#ROC-&amp;-AUC-Score" data-toc-modified-id="ROC-&amp;-AUC-Score-4.3.1">ROC &amp; AUC Score</a></span></li><li><span><a href="#Examples" data-toc-modified-id="Examples-4.3.2">Examples</a></span><ul class="toc-item"><li><span><a href="#AUC-(Area-Under-Curve),-perhaps-the-most-widely-used-measure,-is-considered-more-important-than-accuracy-(confusion-matrix)" data-toc-modified-id="AUC-(Area-Under-Curve),-perhaps-the-most-widely-used-measure,-is-considered-more-important-than-accuracy-(confusion-matrix)-4.3.2.1">AUC (Area Under Curve), perhaps the most widely used measure, is considered more important than accuracy (confusion matrix)</a></span></li></ul></li></ul></li><li><span><a href="#Decision-Tree-Algorithm" data-toc-modified-id="Decision-Tree-Algorithm-4.4">Decision Tree Algorithm</a></span><ul class="toc-item"><li><ul class="toc-item"><li><span><a href="#Let's-consider-another-example:" data-toc-modified-id="Let's-consider-another-example:-4.4.0.1">Let's consider another example:</a></span></li><li><span><a href="#How-about-this-split?" data-toc-modified-id="How-about-this-split?-4.4.0.2">How about this split?</a></span></li></ul></li></ul></li></ul></li><li><span><a href="#k-Nearest-Neighbor-(KNN)" data-toc-modified-id="k-Nearest-Neighbor-(KNN)-5">k-Nearest Neighbor (KNN)</a></span><ul class="toc-item"><li><ul class="toc-item"><li><span><a href="#Appendix-1:-10-fold-cross-validation" data-toc-modified-id="Appendix-1:-10-fold-cross-validation-5.0.1">Appendix 1: 10 fold cross validation</a></span></li><li><span><a href="#Appendix-2:-Search-for-the-optimal-k-value-(GridSearch)" data-toc-modified-id="Appendix-2:-Search-for-the-optimal-k-value-(GridSearch)-5.0.2">Appendix 2: Search for the optimal k value (GridSearch)</a></span></li><li><span><a href="#Appendix-3:-Model-Evaluation-with-ROC" data-toc-modified-id="Appendix-3:-Model-Evaluation-with-ROC-5.0.3">Appendix 3: Model Evaluation with ROC</a></span></li><li><span><a href="#Appendix-4.-Who-are-my-neighbors?-Determining-Neighbors-in-KNN" data-toc-modified-id="Appendix-4.-Who-are-my-neighbors?-Determining-Neighbors-in-KNN-5.0.4">Appendix 4. Who are my neighbors? Determining Neighbors in KNN</a></span></li></ul></li></ul></li><li><span><a href="#Logistic-Regression-(Scikit-Python-package)-&amp;-Logit-(statsmodels-Python-package)" data-toc-modified-id="Logistic-Regression-(Scikit-Python-package)-&amp;-Logit-(statsmodels-Python-package)-6">Logistic Regression (Scikit Python package) &amp; Logit (statsmodels Python package)</a></span><ul class="toc-item"><li><span><a href="#What-is-logistic-regression?" data-toc-modified-id="What-is-logistic-regression?-6.1">What is logistic regression?</a></span><ul class="toc-item"><li><span><a href="#Logistic-regression-vs-Linear-regression" data-toc-modified-id="Logistic-regression-vs-Linear-regression-6.1.1">Logistic regression vs Linear regression</a></span></li><li><span><a href="#Modely-Deployment-:-Make-Predictions-on-the-new-data" data-toc-modified-id="Modely-Deployment-:-Make-Predictions-on-the-new-data-6.1.2">Modely Deployment : Make Predictions on the new data</a></span></li><li><span><a href="#Appendix-1:-10-fold-cross-validation" data-toc-modified-id="Appendix-1:-10-fold-cross-validation-6.1.3">Appendix 1: 10 fold cross validation</a></span></li><li><span><a href="#Appendix-2:-Model-Evaluation-with-ROC" data-toc-modified-id="Appendix-2:-Model-Evaluation-with-ROC-6.1.4">Appendix 2: Model Evaluation with ROC</a></span></li><li><span><a href="#Appendix-3.-Logit-with-Statsmodels" data-toc-modified-id="Appendix-3.-Logit-with-Statsmodels-6.1.5">Appendix 3. Logit with Statsmodels</a></span></li></ul></li><li><span><a href="#Logit" data-toc-modified-id="Logit-6.2">Logit</a></span></li></ul></li><li><span><a href="#Compare-Algorithms" data-toc-modified-id="Compare-Algorithms-7">Compare Algorithms</a></span></li><li><span><a href="#References" data-toc-modified-id="References-8">References</a></span></li></ul></div>
