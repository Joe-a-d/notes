- Cross Industry Standard Process for Data Mining is a methodology for organising ML projects

![[Pasted image 20210909205214.png]]

### Stages

1. Business Understanding : Identify the problem to be solved
2. Data Understanding : Dataset size? reliable?
3. Data Preparation : transform so that it can be used in ML algo
4. Modelling : decide on modelling techniques
5. Evaluation : measure and compare the metrics against our original goal
6. Deployment : how stakeholders access results

### Use Case - Spam Detection
1. Users complain about spam
	1.  is ML helpful?
	2.  is it widespread so that ROI warants tackling
	3.  define concrete goal *reduce spam by 50%*
2.  Is the spam flag fidedigne?
	1.  do we have enough data
	2.  is it clean and reliable
3. Convert features in emails to [1,0] matrix , e.g. contains words "Nigerian Prince" -> 1
	1. clean data
	2. build pipeline
4. Train the spam classifier
	1. try different models 
	2. add new features
5. Measure the model performance
	1. do a retrospective , can help if initial goal not realistic
6. Incremental roll out
	1. often happens together with 5.
	2. evaluate using a subset live users
	3. roll feature to all users