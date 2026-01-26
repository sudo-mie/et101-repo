## J.1

1. How do you divide your time on Java vs Python research
2. do you like your job? Which is the ideal part? And least ideal part? (No exposure to decision-making)
3. What do you envision yourself to be 3-5 years? Let’s say you have a ideal job like WQ
4. Role: help build our tool in schedule optimization. 5 years model. Built quick. Want to improve now. Collaboration with other team as well. Value: coding, quant research, experience with production system, collaboration (communication art with external team)
5. What do you think should be done, if you were to build this schedule optimization system? What are some important components/considerations?
6. You have a portfolio to trade. The portfolio rebalance every couple hours. Goal of the firm is to maximize our pnl. And it is a satirical arbitrage portfolio. Let’s say we trade five day reversion, every day, look at five day reversion and decide to trade on that signal. This is the portfolio. Then what do you think would be the execution objective should be designed so that it matches the overall pnl improvement
7. If the market impact model says it is creating too much impact, you should tell them to trade less? Is it the feedback you are looking for?
8. How do we connect our execution to the overall goal of having more PNL? Why do you think minimizing slippage is maximizing PNL? What should be the metrics? Arrival?
11. If I’m trading pattern like a Ponzi schema (just infinitely size it up): arrival slippage is low, but good PnL. They are contradicting, right? Give me a counter argument? Like more impact is wrong because XYZ
13. How do you construct a proper measure in terms of execution?
14. Have you get any exposure to the propagator model? Can you tell me more?
15. LGBM, do you code it up, the solver? or use existing solver? Have you had experience with optimizers?
16. LGBM vs other model? Do you have prior experience with it? So You actually don’t know how much slippage it improved from this?
17. When you compare, let’s say, in a year, you have collected enough data points, how are you measuring the improvements? Can you tell me the math behind all these? What’s the computation method? 
18. What are you measuring? What are you computing? For example, you have a prior that slippage will improve by 1bps, for each order. And each day receiving 1000 orders across 2000 symbols. How long would it take for us to gain 90% confidence that it makes a difference? You can assume stock std deviation, daily volatility is about 2% roughly. How do you compute this?
19. Instance A and B. A bunch of order going though both. We assume delta being, on average, you’ll have 9bps; for B, you are expecting 8bps. Your std deviation for both daily symbols is 2%. And we want to gain 90% confidence. Receiving 1000 orders a day. On 200 symbols. Give me some rule of thumbs. E.g. if this number changed from 200 to 500, what is the effect; or this changed from 1000 to 100, what is the effect. How long does it take to converge? Make any assumptions. 
20. Expected difference is 1bps. For now we just want to know it is significantly larger than 0 or not. 
21. Quick following up on variance. If variant not 2% is 3%, how much longer would it take?
22. Do you know the form of t-test? You have a variable X, you are doing t-test on X, what are you computing? How do we know its significantly difference?
23. Why t-test works? What’s the Theorem behind it? Do you know law of large numbers?


## J.2

1. Daily correlation 7%, Weekly correlation 8%, Monthly correlation 9%. This is not coincidence, what could be happening here? If you are constructing 2 random variables, how do you construct them so their correlation like this? (Answer - it is noise, follow-up: how do I add noise this way? how to construct it? To guarantee this. From time series perspective) 
2. What’s the relationship to p value? Is it possible to have a 0.9 correlation, but have a very high p value? Assume we have enough data points.
3. Let’s do formula for t stats and correlation, what’s the relationship? Are they connected? 
4. Residual x fitted plot, observed heterodasticity? Why need homodasticity for linear regression? Besides t-stats/p-value, would it affect the estimation?
5. QQ plot, within this area, is it fat tail or thin tail? Can you explain why? 
6. Can you explain qq plot, how  do you construct QQ plot? You have sample, distribution, how do you construct the qq plot?
7. Can you draw to show that? Lets valid quickly. Check these points, we know it’s outlier, they are way out of range, does it match with what you have?
8. WLS - what’s the weight you used? Should be variance or standard deviation? How does it work when you run WLS? Is the weight applied before or after we compute L2? (OLS, get variance, use this for WLS)
9. Can you validate heterosdaticity in steps? Not just visuals. Any test to check/validate that? (run LR regression)
10. Have you thought about cross-impact? In the propagator model settings?
11. From your understanding of market, Cross-impact is symmetric? If A move x, B move y, can you say the other way around? 
12. Not symmetric - follow-up: small-cap on large-cap is bigger? Or large-cap on small-cap bigger? Or something else?
13. And do you think it is stronger short-term or stronger long-term? Like we measure in minutes vs measure in hours, do we small more cross-impact or less?
14. Back to the previous question, based on what we discussed, how would you construct the random variables so you can simulate the relationship between long-term correlation and short-term correlation?


## K

1. Project most proud of. What is the objective function? Does the model use the real time data? 
2. How to define eligible volume? Dark pool included in the volume? Just top of the book or depth of book? Is it coming from direct feed, or SIP?
3. When you train LGBM, how do you avoid overfitting?
4. Pegging implementation: you peg from algo, or rely on dark pool pegging for you?
5. What’s the primary reason for you to look around? 
6. what is the most optimal schedule? On our side, we don’t care about vwap, we care about arrival more. Question is, how should the schedule for order to minimize the initial arrival? More intra day, we have some forecast that we use, propagator impact model, volume predictions, integrated optimizer that would decide the scheduling part. Then integration with algo part and smart order router on our side
7. Do you know any of market impact model? It’s definitely good to know what’s  the impact you created, so you can optimize for 2nd or subsequent orders, right?
8. Assume you have a performance sensitive client, they come to you like, hey I have a full day order but you should minimize the situation of arrival. What would be your approach to this problem? E.g. I come to you say I’m trading 2% ADV 3000 stocks every day, give you orders 9:30. You can use any algo, front load or back load or target close. Goal is to minimize slippage to arrival. How would you approach that?
9. You need to 100% fill it end of day, but I’m not telling you what my urgency is
10. I’ll give you order at 9:30 start trading. Price starts moving, you’ll look at the reversion or momentum. Going back to market impact modeling. How would you know that this momentum is due to market or due to the impact you created? How would you know what would happen in absence of a trade?
11. What is linear propagator model, what do you know about this?
12. Lit venues in US, they have different pricing? What kind of pricing model do you know for venues? Do you guys take that into account as well? Say you post on nasdaq getting rebate, do you deal with any of that?
13. You measured the spread cost. You also get a rebate on that fill. Post or take I think that makes a big difference. If you take that fee/rebate into account?
14. Are you aware of that some venues, how they charge rebates?
15. What trade on this (inverted venues)? Why you have to pay for provision? Don’t you think it will leak more information? Do you know much about these venues? Total % of US flow is executed in those venues?
16. SQL - 1 table 1 column, this column is tickers. Multiple tickers in that column. Like IBM, Microsoft, Tesla etc. how would you output tickers that appear more than once in a table?
17. Exactly same problem, in Python?Just walk me through the logic. Don’t use pandas. 
18. Same question, like I’m emailing you the file. Cannot use programming languages, don’t write code. How to do it?
19. Same problem, Linux?
20. AI at work, LLM? Outside of work?
21. How would you test candidate not using AI?


## V

1. 3 Random Variables。Correlation A,B = 1/2; B and C is 1/2. Question: value of correlation A and C
2. How do you define yourself, dev or researcher?
3. Tell me about linear regression. What kind of LR. Start simple ones, and what can be improved. (What is OLS, what is ridge/lasso, why we need this)
4. If we need feature selection, we’ll use lasso. Then why we need ridge? (Why lasso cannot help for this case)
5. OLS. 1-D data (1 variable). We have 10 groups of 100 data points. Could this happen: fit each independent group, beta > 0; fit 1000 data together, beta < 0
6. Can you tell me about gradient descent methods? What is a gradient descent? What’s its simplest form, and what kind of improvement exist? 
7. Follow-up: mathematically how it works. And for multi-dimensional case, loss function is from NxN dimensional space to Nx1 dimensional space (e.g. 10 features about people -> predict their level) for this function, we want to do gradient descent. what is the gradient (functional form), what is the shape of matrix?
8. Stochastic gradient descent, can you talk about that? (Follow-up: converge faster, what do you mean by faster? Probably less step, but at each step is more complicated?)
9. Why we use stochastic gradient descent often? 
10. What kind of optimization method is used for LGBM, or at least what you used?
11. Tell me what is LGBM? Why use lightGBM? How does gradient descent fit in here? What happens to decision trees? How is the set of trees decide? How do you construct those trees? How does LgBm decides what kind of trees to build? Are the trees fixed?
12. You mention LGBM is resilient to outliers. But decision trees, it is very easy to fit outliers. You have freedom of tree construction to allow you overfit. What intervention makes it not happening in LGBM? Is there something special in LGBM. 
13. Python - what’s your experience with Python, like what of task you use Python? Do you use LLM?
14. What is decorator in Python?
15. Do you use any linter for Python? Like binding, general wifi? 
16. Do you work with GPUs?

