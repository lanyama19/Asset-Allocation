# Asset-Allocation
Lecture notes on CFRM503 
<h1 align=center>
    Asset Allocation And Portfolio Management</h1>
### 1. Mean-Variance Optimizations

Let us have a review of mean-variance portfolio optimization. As many of the results will reappear in some form in future aspects of this course, so many of the interpretations and  intuitions also hold in some way or another. Shortly, we will discuss several weaknesses of mean-variance optimization. It helps to reminder what it is all about before doing this. 
The problem we address is the following: an investor wishes to divide an amount of wealth $W_0$ among a collection of assets. Denote $W_1$ as the value of wealth in the future, and $\theta$ as an abstract parameter which determine the investment choice. If the investor wishes to choose the investment with greatest future wealth, mathematically, we want to find $\theta^{*}$ such that 
$$
W_1(\theta^{*}) \geq W_1(\theta) ,\text{for all} \ \theta
$$
The issue here is, $W_1$as random variables, this inequality should be interpreted in the almost surely sense. 
$$
\mathbb{P}\left(W_1(\theta^{*}) \geq W_1(\theta)\right ) = 1
$$
This is impossible for any reasonable setting. It does not make sense to find the investment with greatest wealth. We need to specify preferences of the investors which results in a well posed problem. 
Let us lay out 2 assumptions about how investors choose investments. 
*Assumption 1:* all other things being equal, an investor prefers a greater expected value of future wealth. 
*Assumption 2*: all other things being equal, an investor prefers lower variance of future wealth. 
The objective we shall propose is to maximize and explicitly trade-off between these two preferences. Let 
$$
f(\theta) = \mathbb{E}\left[W_1(\theta)\right] - \psi \mathbb{V} \left[W_1(\theta)\right]
$$
where $\psi$ is a conversion factor between units of variance of future wealth to expectation of future wealth.  Investor's goal can now be stated: find $\theta^{*}$ such that $f(\theta^{*}) \geq f(\theta)$ for $\theta$.  Suppose a finite collection of assets has current prices 
$$
\{ P_0^{(1)}, \dots, P_0^{(N)} \}
$$
 which are known constants. Let the prices in the future be denoted by:
$$
\{ P_1^{(1)}, \dots, P_1^{(N)} \}
$$
which are random variables. At this point, we need to write $W_1(\theta)$. Let 
$$
\{\theta^{(1)},\dots , \theta^{(N)} \}
$$
represents the number of shares of each asset put into the portfolio. Then the future wealth
$$
W_1(\boldsymbol{\theta}) = \sum_{n=1}^N \theta^{(n)}P_1^{(n)}
$$
We also have the constraint: $W_0 =  \sum_{n=1}^N \theta^{(n)}P_0^{(n)}$. 
The optimization problem we need to solve: 
$$
\max_{\boldsymbol{\theta}} \mathbb{E}\left[W_1(\theta)\right] - \psi \mathbb{V} \left[W_1(\theta)\right] \\
\text{subject to:} \ \ W_0 =  \sum_{n=1}^N \theta^{(n)}P_0^{(n)}
$$
Problem well become more tractable if written in terms of relative wealth rather than absolute units of shares. Recall the definition of arithmetic returns:
$$
r^{(i)} = \frac{P_1^{(i)} - P_0^{(i)}}{P_0^{(i)}}
$$
also recall that
$$
r_p = \frac{W_1 - W_0}{W_0}
$$
then we can write
$$
r_p = \sum^{N}_{n=1} \pi^{(n)}r^{(n)}
$$
where 
$$
\pi^{(n)} = \frac{\theta^{(n)}P_0^{(n)}}{W_0}
$$
In particular, $\sum^N_{n=1} \pi^{(n)} =1$ is equivalent to our previous constraint. Go back up to thing we try to maximize
$$
\begin{aligned}
	\mathbb{E}\left[W_1(\theta)\right] & = W_0 \mathbb{E} \left[1+r_p\right] \\
    																 & = W_0 \mathbb{E} \left[1+ 	\boldsymbol{\pi}^{T}\mathbf{r}  \right]   \\
    																 & = W_0 + W_0 \boldsymbol{\pi}^{T} \boldsymbol{\mu}
\end{aligned}
$$
where $\mu^{(n)} = \mathbb{E} \left[r^{(n)}\right]$. 
$$
\begin{aligned}
	\mathbb{V} \left[W_1(\boldsymbol{\theta})\right] & = \mathbb{V}\left[W_0(1+r_p)\right] \\
	& = W_0^2 \mathbb{V} \left[1+r_p\right] \\
	& = W_0^2 \mathbb{V} \left[r_p\right] \\ 
	& = W_0^2 \mathbb{V}[\boldsymbol{\pi}^{T}\mathbf{r}] \\ 
	& = W_0^2 \boldsymbol{\pi}^{T} \Omega \boldsymbol{\pi} 
\end{aligned}
$$
where $\Omega = \mathbb{C}[\boldsymbol{r}]$, the covariance of returns. Thus the objective function
$$
\begin{aligned}
	\max_{\boldsymbol{\theta}} \mathcal{F}(\boldsymbol{\theta}) & = W_0 + W_0 \boldsymbol{\pi}^{T} 	 \boldsymbol{\mu} - \psi W_0^2 \boldsymbol{\pi}^{T} \Omega \boldsymbol{\pi} \\
	& = W_0 + W_0 \max_{\boldsymbol{\theta}} \{\boldsymbol{\pi}^{T} \boldsymbol{\mu} - \psi W_0 \boldsymbol{\pi}^{T} \Omega \boldsymbol{\pi}  \}
\end{aligned}
$$
We define function
$$
\mathcal{G}(\boldsymbol{\theta}) = \boldsymbol{\pi}^{T} \boldsymbol{\mu} - {\gamma \over 2}\boldsymbol{\pi}^{T} \Omega \boldsymbol{\pi}
$$
where $\gamma = 2 \psi W_0$. Posed in terms of relative  amount, the problem becomes
$$
\begin{aligned}
 & \max_{\boldsymbol{\pi \in \mathbb{R}^N}} \boldsymbol{\pi}^{T} \boldsymbol{\mu} - {\gamma \over 2}\boldsymbol{\pi}^{T} \Omega \boldsymbol{\pi} \\
 & \text{s.t.} \quad \boldsymbol{\pi}^{T}\mathbf{1}  =1
\end{aligned}
$$
The additional assumption is: $\Omega$ is invertible. In particular, there is no risk-free asset(with risk-free asset, the matrix would not be invertible).  
The solution to the above optimization problem is to introduce **Lagrangian multipliers**: 
$$
\mathcal{L} (\boldsymbol{\pi},\lambda) = \boldsymbol{\pi}^{T} \boldsymbol{\mu} - {\gamma \over 2}\boldsymbol{\pi}^{T} \Omega \boldsymbol{\pi} + \lambda(\boldsymbol{\pi}^{T}\mathbf{1} - 1) \\
$$
Take the gradient and set to 0
$$
\nabla_{\mathbb{\pi}} \mathcal{L}(\boldsymbol{\pi},\lambda) = \boldsymbol{\mu} - \gamma \Omega \boldsymbol{\pi} + \lambda \mathbf{1} = \mathbf{0} \\
\Rightarrow  \boldsymbol{\pi} = {1 \over \gamma} \Omega^{-1} (\boldsymbol{\mu} + \lambda \mathbf{1})
$$
Substitute this into the equality constraint:
$$
{1 \over \gamma} \mathbf{1}^T \Omega^{-1} \boldsymbol{\mu} + {\lambda \over \gamma} \mathbf{1}^T \Omega^{-1} \mathbf{1} = 1 \\
\lambda = \frac{\gamma - \mathbf{1}^T \Omega^{-1}\boldsymbol{\mu}}{ \mathbf{1}^T \Omega^{-1}\mathbf{1}}
$$
  It will be helpful to introduce
$$
A =  \mathbf{1}^T \Omega^{-1}\mathbf{1} \\
B = \mathbf{1}^T \Omega^{-1}\boldsymbol{\mu} \\
C = \mathbf{\boldsymbol{\mu}}^T \Omega^{-1}\boldsymbol{\mu}
$$
Substitute the expression for $\lambda$ into the expression for $\boldsymbol{\pi}$: 
$$
\begin{aligned}
	\boldsymbol{\pi} & = {1 \over \gamma} \Omega^{-1} (\boldsymbol{\mu} + \lambda 	\mathbf{1}) \\
	& = {1 \over \gamma} \Omega^{-1}\boldsymbol{\mu} + {1 \over \gamma} \Omega^{-1} \mathbf{1} \left(\frac{\gamma - \mathbf{1}^T \Omega^{-1}\boldsymbol{\mu}}{ \mathbf{1}^T \Omega^{-1}\mathbf{1}}\right) \\
	& = {1 \over \gamma} \Omega^{-1}\boldsymbol{\mu} + \frac{\Omega^{-1}\mathbf{1}}{A} - \frac{\Omega^{-1}\mathbf{1}B}{\gamma A} \\
\end{aligned}
$$

$$
\boldsymbol{\pi}^{*} =  \frac{\Omega^{-1}\mathbf{1}}{A} + {1 \over \gamma}\left(  \frac{A\Omega^{-1}\boldsymbol{\mu} - B\Omega^{-1}\mathbf{1}}{A}\right)
$$



#### 1.1. Global minimum variance portfolio

What is risk aversion $\gamma$?  Next steps: for a particular $\gamma$, we will compute $\boldsymbol{\pi}^{T} \boldsymbol{\mu}$ and $\boldsymbol{\pi}^{T} \Omega \boldsymbol{\pi}$. By now letting $\gamma$ vary continuously we obtain a curve in $(\mathbb{E},\mathbb{V})- $space. Then rather than choosing a personal value of $\gamma$, an investor may choose a particular point on the curve which best reflect their risk tolerance. With $\boldsymbol{\pi}^{*}$
$$
\begin{aligned}
	\mathbb{E}\left[r_p\right] & = \boldsymbol{\mu}^T \boldsymbol{\pi} \\
	                           & = \frac{B}{A} + \frac{1}{\gamma}\frac{AC-B^2}{A}
\end{aligned}
$$

$$
\begin{aligned}
	\mathbb{V} \left[r_p\right]&  =  \boldsymbol{\pi}^{*T}\Omega \boldsymbol{\pi}^{*} \\
	         & = \boldsymbol{\pi}^{*T} \left(\frac{\mathbf{1}}{A} + \frac{1}{\gamma} \frac{A\boldsymbol{\pi} - B\mathbf{1}}{A} \right) \\
	         & = \left(\frac{\mathbf{1}^T\Omega^{-1}}{A} + {1 \over \gamma}  
	         \frac{A\boldsymbol{\mu}^T\Omega^{-1} - B\mathbf{1}^T\Omega^{-1}}{A}\right) 
	           \left(\frac{\mathbf{1}}{A} + \frac{1}{\gamma} \frac{A\boldsymbol{\pi} - B\mathbf{1}}{A} \right) \\
	           & =   \frac{1}{A} + \frac{AB-BA}{\gamma A^2} + \frac{AB-BA}{\gamma A^2} + \frac{AC-B^2}{\gamma^2A} \\
	           & = \frac{1}{A} + \frac{AC-B^2}{\gamma^2A}
\end{aligned}
$$

When $\gamma \mapsto \infty $ we have the global minimum variance $\sigma^2_{gm}$and global minimum expected returns $\mu_{gm}$. 
$$
\begin{aligned}
	\mu_{gm} & = \frac{B}{A} \\
	\sigma^2_{gm} & = \frac{1}{A}
\end{aligned}
$$


#### 1.2. Frontier boundary

We now can derive the curve
$$
\mu_p = \mu_{gm} + \frac{1}{\gamma} \frac{D}{A} \\
\Rightarrow \frac{1}{\gamma} = (\mu_p - \mu_{gm})\frac{A}{D}\\
\frac{1}{\gamma^2} = (\mu_p - \mu_{gm})^2\frac{A^2}{D^2}\\
$$

$$
\begin{aligned}
	\sigma^2_p & = \frac{1}{A} + \frac{D}{A} \frac{A^2}{D^2}\left(\mu_p - \mu_{gm}\right)^2 \\
	& = \sigma^2_{gm} + \frac{\left(\mu_p - \mu_{gm}\right)^2}{\sigma^2_{gm}D}
\end{aligned}
$$

This relation defines a curve in the $(\sigma_p, \mu_p)$ plane. 
<img src="C:\Users\24410\OneDrive\桌面\WeChat Image_20190429004913.jpg" alt="Image" height="300" width="600">

#### 1.3. Tangency portfolios

Consider portfolio with risk-free asset. Let $r_f$ be the deterministic return of a risk-free asset. Let $\pi^{(0)}$ be the proportion of wealth invested in the risk-free asset. 
$$
\sum^{N}_{n=0} \pi^{(n)} = 1
$$
The issue here is when incorporating risk-free asset in the portfolio, the associated covariance matrix would        not be invertible. We still want the covariance to be invertible. In this case, let $\pi ^{(0)} = 1- \sum^{N}_{n=1} \pi^{(n)}$. 
$$
\begin{aligned}
r_p & = \pi^{(0)} r_f + \boldsymbol{\pi}^T\mathbf{r} \\
	  & = r_f - \sum^{N}_{n=1} \pi^{(n)}r_f + \boldsymbol{\pi}^T\mathbf{r} \\
	  & = r_f +  \boldsymbol{\pi}^T\mathbf{r_e}
\end{aligned}
$$

$$
\boldsymbol {\pi} =  \left[
 \begin{matrix}
   \pi^{(1)}  \\
   \vdots  \\
   \pi^{N}  \\
  \end{matrix}
  \right]
$$

$$
\boldsymbol {r_e} =  \left[
 \begin{matrix}
   r^{(1)} - r_f  \\
   \vdots  \\
   r^{N} - r_f  \\
  \end{matrix}
  \right]
$$

where $\boldsymbol {r_e} $ denotes the excessive returns
$$
\begin{aligned}
	& \mathbb{E} [r_p] = r_f + \boldsymbol{\pi}^T \boldsymbol{\mu_e}\\
	& \mathbb{V} [r_p] = \boldsymbol{\pi}^T \boldsymbol{\Omega_e}\boldsymbol{\pi} =\boldsymbol{\pi}^T \boldsymbol{\Omega}\boldsymbol{\pi}
\end{aligned}
$$
Therefore the performance criteria is
$$
r_f + \boldsymbol{\pi}^T \boldsymbol{\mu_e} - \frac{\gamma}{2}\boldsymbol{\pi}^T \boldsymbol{\Omega}\boldsymbol{\pi}
$$
The optimization problem now is
$$
\max_{\boldsymbol{\pi}} \boldsymbol{\pi}^T \boldsymbol{\mu_e} - \frac{\gamma}{2}\boldsymbol{\pi}^T \boldsymbol{\Omega}\boldsymbol{\pi}
$$
The associated lagrangian is
$$
\mathcal{L}(\boldsymbol{\pi}) =\boldsymbol{\pi}^T \boldsymbol{\mu_e} - \frac{\gamma}{2}\boldsymbol{\pi}^T \boldsymbol{\Omega}\boldsymbol{\pi}\\
\nabla_{\boldsymbol \pi} \mathcal{L}(\boldsymbol{\pi}) = \boldsymbol{\mu_e} - \gamma\boldsymbol{\Omega}\boldsymbol{\pi} = \mathbf{0} \\
\Rightarrow \boldsymbol{\pi^{*}} = \frac{1}{\gamma}\boldsymbol{\Omega}^{-1}\boldsymbol{\mu_e}
$$
The next step is to compute $\mu_p$ and $\sigma_p^2$
$$
\begin{aligned}
	\mu_p &= r_f +\boldsymbol{\pi}^{*T}\boldsymbol{\mu_e} \\
				&= r_f +  \frac{1}{\gamma} \boldsymbol{\mu_e}^T \boldsymbol {\Omega}^{-1} \boldsymbol{\mu_e} \\
				\frac{1}{\gamma^2} &= \frac{(\mu_p - r_f)^2}{(\boldsymbol{\mu_e}^T \boldsymbol 						{\Omega}^{-1} \boldsymbol{\mu_e})^2}\\
				\sigma^2_p& = \frac{1}{\gamma^2}\boldsymbol{\mu_e}^T \boldsymbol {\Omega}^{-1} \boldsymbol{\mu_e}
\end{aligned}
$$
Substitute the expression of $\gamma^2$ into the expression of $\sigma^{2}_p$
$$
\sigma_p^2 = \frac{(\mu_p - r_f)^2}{\boldsymbol{\mu_e}^T \boldsymbol 						{\Omega}^{-1} \boldsymbol{\mu_e}}\\
\Rightarrow  \sigma_p = \frac{\mu_p - r_f}{\sqrt{\boldsymbol{\mu_e}^T \boldsymbol 						{\Omega}^{-1} \boldsymbol{\mu_e}}}
$$
<img src="C:\Users\24410\OneDrive\桌面\WeChat Image_20190429142658.jpg" alt="Image" height="300" width="500">

#### 1.4. Indifference curves

Consider the expression of the following form
$$
\mu-\frac{\gamma}{2}\sigma^2 = K
$$
For fixed $K$ and $\gamma$, this gives a relation between $\mu$ and $\sigma$. All points on that curve have the same utility. It cannot be the case that the indifference curve corresponding with risk-free 1) lower than without risk-free
$$
\sup_{x \in A} f(x) \leq \sup_{x \in B} f(x), \ \text{if} \ A \subseteq B
$$
All of this together eliminate the green curve lies below the tangency curve. To eliminate blue, we will show that there is one particular portfolio which is fully invested in the risky assets.
$$
\begin{aligned}
\pi^{(0)} & = 1- \boldsymbol{\pi}^{*T}\mathbf{1}\\
					& = 1- \frac{1}{\gamma}\mathbf{1}^T \Omega^{-1}\boldsymbol{\mu_e}
\end{aligned}
$$
If $\gamma= \mathbf{1}^T \Omega^{-1}\boldsymbol{\mu_e}$ then $\pi^{(0)} = 0$. Show that $\gamma$ is positive
$$
\begin{aligned}
\gamma &= \mathbf{1}^T \Omega^{-1}\boldsymbol{\mu_e} \\
			 &= \mathbf{1}^T \Omega^{-1}(\boldsymbol{\mu} - \mathbf{1}^T r_f) \\
			 &= \mathbf{1}^T \Omega^{-1}\mathbf{1}\left(\frac{\mathbf{1}^T \Omega^{-1} \boldsymbol{\mu}}{\mathbf{1}^T \Omega^{-1}\mathbf{1}} -r_f \right) \\
			 &= \frac{1}{\sigma^2_{gm}}(\mu_{gm} - r_f) 
\end{aligned}
$$
Let us revisit some of our idealized assumptions
1) Assets are infinitely divisible. For large $W_0$ this becomes a negligible issue. If it is significant, better optimization can be done by integer programming.
2) Constraints are binding in the sense of strict equality. Our constraint thus far is fundamental and cannot be violated. Regarding constraints, one we have not enforced is a constraint on short-selling. Why might we be interested in a constraint on short-selling? One reason might be that not everyone is allowed to do so. And short-selling is more expensive than taking a long position. 
3)  What are $\boldsymbol{\mu}$ and $\boldsymbol{\Omega}$ ? There are several methods by which $\boldsymbol{\mu}$ and $\boldsymbol{\Omega}$  can be estimated. The first one leads to robust statistical estimation of parameters. The second one can be done through robust optimization which the results are not sensitive to changes in the input. The last one comes to uncertainty averse optimization or ambiguity averse optimization. 
4) What is the associated time period? This is related to the assumption that the portfolio is static. Moving beyond static portfolio allows incorporating news, change in investor preferences and possibly better strategies. 

Now we get back to our constraints 2) ask why and how. 
1) Short-selling might not be allowed
2) Investor may simply have preference for some assets over others. 
3) Static portfolio can become over-concentrated in small subset of assets. 
How we can modify our objective to take these into account? 
1) No short-selling of asset $n$ means $\pi^{(n)}\geq 0$
$$
\begin{aligned}
\max_{\boldsymbol{\pi}}& \ \boldsymbol{\pi}^T\boldsymbol{\mu}- \frac{\gamma}{2}\boldsymbol{\pi}^T\boldsymbol{\Omega}\boldsymbol{\pi} \\
\text{s.t.} & \ \boldsymbol{\pi}^T\mathbf{1} = 1\\
&\ \boldsymbol{\pi} \geq \mathbf{0}
\end{aligned}
$$
2) Preferences for specific assets: perhaps investor wants $\pi^{(n)} \geq k^{(n)}$. 
3) No over-concentration in specific assets $\pi^{(n)} \leq c^{(n)}$. No concentration in specific sectors
$$
\sum_{n \in \mathcal{A}} \pi^{(n)} \leq C^{\mathcal{A}}, \ \mathcal{A} \subset \{1,\dots,N\}
$$
In general
$$
\begin{aligned}
\max_{\boldsymbol{\pi}} & \ f(\boldsymbol{\pi})\\
\text{s.t.} & \ \mathbf{A}\boldsymbol{\pi} = \mathbf{a} \\
					  & \ \mathbf{B}\boldsymbol{\pi} \leq \mathbf{b} \\
					  & \ \mathcal{G}_k(\boldsymbol{\pi} ) = 0 \\
					  & \ \mathcal{H}_k(\boldsymbol{\pi}) \leq 0 
\end{aligned}
$$
The constraints listed above are linear equality constraint, linear inequality constraint, nonlinear equality and nonlinear inequality constraint respectively. KKT conditions, are a system of equalities and inequalities based on $\mathbf{A}, \mathbf{a}, \mathbf{B}, \mathbf{b}, \mathcal{G}_k, \mathcal{H}_k$ which must be satisfied at a point $\boldsymbol \pi^{*}$ if it is optimal. They are necessary conditions not sufficient. 

### 2. Multiperiod discrete time trading strategies

We now get into dynamic trading strategies. Why are we interested in dynamic trading strategies? What are the disadvantages of static trading strategies? The mean-variance optimization is implicit in the framework of our problems, we set the problems up, everything is static. Static versus dynamic has nothing to do with mean, variance. It is just we solved a mean-variance optimization under the assumption that we are using a static trading strategy. We enter a position at time $0$. We will do nothing until time $1$ and liquidate the positions. The disadvantages are 1) a static strategy is a vert strong constraint. This means optimal performance may be increased significantly by allowing rebalancing. 2) We cannot incorporate changing market conditions for example as a result of news (may change our specification of $\vec{\mu}$ and $ \Sigma$ or other model parameters). Simply for risk aversion $\delta$, investors' preferences may change over time. 

#### 2.1. Self-financing condition

Much of the lecture will revolve around the theme of "book-keeping". Much of our work will try to derive dynamic wealth through time depending on trading strategies, keeping track of where money flows from one source to another. It seems tedious at some time, but it is quite important when we move from discrete time to continuous time. In following chapter, we focus on discrete time. And after that, we will use the results of discrete time as motivation on how to model things in continuous time. 
Denote $\theta^{(i)}_n$ as number of units of asset $i$ held at time $n$, where $n \in \{0, \cdots, N\}$, $i \in \{0, \cdots, K\}$. And $P_n^{(i)}$ as price of asset. We let $X_n$ be amount of cash we put in the money market at time $n$. $W_n$ will be the total wealth which can be represented as
$$
W_n = X_n + \sum_{i=1}^K \theta_n^{(i)}P_n^{(i)}
$$
Next step is to find $W_{n+1}$ in when trading strategy is changing. $W_{n+1}$ can be changed as a result of:

1) Prices change and interest is earned on the money market.
$$
\begin{aligned}
& X_n \mapsto X_n(1+r) \\
& P_n^{(i)} \mapsto P_{n+1}^{(i)}
\end{aligned}
$$
​	So the total wealth after these changes will be
$$
W_{n+1}^{-} =X_n(1+r) + \sum_{i=1}^K \theta_n^{(i)}P_{n+1}^{(i)}
$$
2)  Rebalancing occurs: 
$$
\theta_n^{(i)} \mapsto \theta_{n+1}^{(i)}
$$
​	Hence by writing the total wealth as a result of rebalancing
$$
\begin{aligned}
W_{n+1} & = X_{n+1} + \sum_{i=1}^k \theta_{n+1}^{(i)}P_{n+1}^{(i)} \\
				& = X_n(1+r) + \sum_{i=1}^k \theta_{n}^{(i)}P_{n+1}^{(i)}
\end{aligned}
$$
​	we have the following constraint: 
$$
X_{n+1} = X_n (1+r) - \sum_{i=1}^k (\theta_{n+1}^{(i)} - \theta_{n}^{(i)})P_{n+1}^{(i)}
$$
The equation above is the self-financing condition. Simply be rebalancing your portfolio, your total wealth will not change. It tells the amount of money withdrawn from the money market in order to rebalance. 

What assumptions we have gone into deriving these equation of evolution? 

* We have made no assumption about constraint on trading strategy. Possibly, we can specify constraint such as Ⅰ) no short selling $\theta_n^{(i)} \geq 0$ or Ⅱ) no borrowing from the money market $X_n \geq 0$ Ⅲ) assets are not infinitely divisible $\theta_n ^{(i)} \in \mathbb{Z}$ 
* Assumptions about price dynamics or price distributions. No strong assumption, but one can argue that we have no price impact effects. We will cover topics in this later. And we certainly do not have modeling assumptions on $P_n^{(i)}$. But we will do this shortly in order to perform an actual optimizations. 
* No transaction costs. The cost of rebalancing of particular assets is exactly $(\theta_{n+1}^{(i) } - \theta_{n}^{(i) })P_{n+1}^{(i)}$ . We will now drop this assumption and discuss two different way of interpreting transaction costs. 

#### 2.2. Accounting for transaction costs

When including transaction costs in our model, our main challenge is to derive the appropriate self-financing conditions when there are transaction costs. 
There are generally two methods of express transaction cost: 1) explicit transaction costs which as known as direct cost in implementation 2) bid-ask spread

**Method 1: ** explicit transaction costs.  We will solve this using book-keeping. We start with the wealth dynamics
$$
W_n = X_n + \sum_{i=1}^K \theta_n^{(i)}P_n^{(i)}
$$
At time $n+1$1, 
$$
W_{n+1}^{-} = X_n(1+r) +\sum_{i=1}^K \theta_n^{(i)}P_{n+1}^{(i)}
$$
$W_{n+1}^{-}$ denotes the wealth before rebalancing. In order to find the self-financing condition, we need to find how much money we should add or withdraw from the money market. The new condition is given by
$$
X_{n+1} = X_n (1+r) - \sum_{i=1}^k \left[(\theta_{n+1}^{(i)} - \theta_{n}^{(i)})P_{n+1}^{(i)} + C^{(i)}(\theta_{n}^{(i)} , \theta_{n+1}^{(i)},P^{(i)}_{n+1})\right]
$$
There are generally four appropriate choices of $C^{(i)}(.)$

1) Absolute transaction costs
$$
C^{(i)} = \alpha^{(i)}|\theta_{n+1}^{(i)} - \theta_{n}^{(i)}|,\  \alpha^{(i)} \geq 0
$$
2) Relative or proportional costs
$$
C^{(i)} = \beta^{(i)}|\theta^{(i)}_{n+1} - \theta^{(i)}_{n}|P_{n+1}^{(i)}
$$
3) Power costs
$$
C^{(i)} = \gamma^{(i)}|\theta^{(i)}_{n+1} - \theta^{(i)}_{n}|^{\delta^{(i)}}
$$
4) Flat fee
$$
C^{(i)} = \lambda^{(i)},\ \text{if} \ \  \theta^{(i)}_{n+1} \neq \theta^{(i)}_{n}
$$
**Method 2:** Implement bid-ask spread. The fundamental idea under this is that buying and selling of asset does not occur at the same prices.  Let us go through the book-keeping again with this in mind, derive the appropriate self-financing condition. 
$$
W_n = X_n + \sum_{i=1}^K \theta_n^{(i)}P_n^{(i)}
$$
With bid-ask spread, rebalancing the portfolio occurs at different prices
$$
\begin{aligned}
	& X_{n+1} = X_n(1+r) - \sum_{i=1}^k D^{(i)}(\theta_{n}^{(i)} , \theta_{n+1}^{(i)},P^{(i)}_{n+1}) \\
\end{aligned}
$$

$$
D_n^{(i)} = 
\left\{
		\begin{array}\
				 (\theta^{(i)}_{n+1} - \theta^{(i)}_{n}) \overline{P_{n+1}^{(i)}} \\
				 (\theta^{(i)}_{n+1} - \theta^{(i)}_{n}) \underline{P_{n+1}^{(i)}}
		\end{array}
\right.
$$

​	Where $\underline{P_{n+1}^{(i)}} \leq P_n^{(i)} \leq \overline{P_{n+1}^{(i)}} $
Next, we define three classes of trading strategy. Introduce numerous example of performance criteria.

#### 2.3. Buy and hold, constant mix, and dynamic linear

**Buy and hold strategy**: The number of units of each asset hold does not change through time, which is defined by
$$
\theta_n^{(i)} = \theta^{(i)}
$$
It is therefore a static strategy. What is the disadvantage of this strategy? If $P_n^{(i)}$ goes up and $P_n^{(j)}$ goes down, what to happen to the distribution of wealth over the entire portfolio? Compute the proportion of wealth invested on asset $i$
$$
\pi_n^{(i)} = \frac{\theta^{(i)}_nP^{(i)}_n}{W_n}
$$
Thus, buy and hold strategy leads to over concentration of wealth in the assets which tend to increase. 
The advantages of this are 1) no transaction costs beyond the initial position 2) very simple to execute, no management of the portfolio over time.

**Constant mix :** we have constant relative proportion of wealth in the asset over time: $\pi_n^{(i)} = \pi^{(i)}$ . This strategy requires investor to change absolute positions through time. 
The advantages of constant mix are 1) diversification stays constant 2) simple and straightforward conceptually, the rule of rebalancing is well defined. 
The disadvantages of constant mix are 1) frequent rebalancing may in fact be an overreaction to some market behavior, which means it would suffer from transaction costs. 2) if $P^{(i)}_n \uparrow$ and $P_n^{(j)}\downarrow$, in order to main constant mix, we must sell the asset that perform well and buy the asset perform poorly. This can have a negative psychological effect. 
Issues with implementation of constant mix:
$$
\pi_n^{(i)} = \frac{\theta^{(i)}_nP^{(i)}_n}{W_n}
$$
At time $n+1 $, prices change
$$
\pi_n^{(i)-} = \frac{\theta^{(i)}_nP^{(i)}_{n+1}}{W_{n+1}^{-}}
$$
The question here is how do we select $\theta^{(i)}_{n+1}$? We need to choose  $\theta^{(i)}_{n+1}$ such that 
$$
\frac{\theta^{(i)}_{n+1} P^{(i)}_{n+1}}{W_{n+1}} = \pi^{(i)}
$$
remain constant. Hence, 
$$
\theta^{(i)}_{n+1} = \frac{W_{n+1}\pi^{(i)}}{P^{(i)}_{n+1}}
$$
where $W_{n+1}$ should incorporate the transaction costs of other rebalancing. The above equation gives us a system of $K$ equations in the unknows $\{\theta_{n+1}^{(1)}, \cdots, \theta_{n+1}^{(K)} \}$ which appear in the $W_{n+1}$ term. How do we get around this application? Recall that 
$$
W_{n+1} = W_{n+1}^{-} - \sum^K_{i=1}C^{(i)}(\theta_{n+1}^{(i)},\theta_{n}^{(i)},P^{(i)}_{n+1})
$$
We will make the assumption $W_{n+1} \approx W_{n+1}^{-}$ then set
$$
\theta^{(i)}_{n+1} = \frac{W_{n+1}^{-}\pi^{(i)}}{P^{(i)}_{n+1}}
$$
The assumption above will hold when 1) you have large wealth and absolute transaction costs or 2) the true     rebalancing values are small. 

**Dynamic linear trading strategy :** Define
$$
\pi^{(i)}_{n+1} = \pi^{(i)}_{n}\left( 1+L\left( \frac{r^{(i)}_{n+1}-r_{n+1}^{(w)}}{1+r_{n+1}^{(w)} } \right)\right), \ L \in \mathbb{R}
$$
where
$$
\begin{aligned}
& r^{(i)}_{n+1} = \frac{P^{(i)}_{n+1}}{P_n^{(i)}} - 1 \\
& r^{(w)}_{n+1} = \frac{W^{-}_{n+1}}{W_n} - 1 \\
\end{aligned}
$$
The advantage of dynamic linear strategy is that it offers flexibility in tailoring performance to investor's preferences. The disadvantage of this strategy is that it has the same implementation problem as constant mix. Rewrite the definition above
$$
\frac{\theta^{(i)}_{n+1} P^{(i)}_{n+1}}{W_{n+1}} =\pi^{(i)}_{n}\left( 1+L\left( \frac{r^{(i)}_{n+1}-r_{n+1}^{(w)}}{1+r_{n+1}^{(w)} } \right)\right)
$$
where $W_{n+1}$ depends on all $\{\theta_{n+1}^{(1)}, \cdots, \theta_{n+1}^{(K)} \}$. We can eliminate this complication if replace  $W_{n+1}$ with $W_{n+1}^{-}$ above. 
Dynamic linear strategy define relative weights in terms of other relative weights. We can check that the formula given results in $\sum^{K}_{i=1} \pi^{(i)}_{n+1} = 1$.

#### 2.4 Alternative performance criteria

Most of the performance criteria involve a tradeoff between some measurement of risk or "bad performance" and some measurement of reward or "good performance". 
Examples of rewards: 
	1)  expected portfolio returns $ \mu_p$ 
	2)  diversification $\delta_n $ 
$$
\delta_n = 1 - \sum_{i=1}^{N} (\pi^{(i)}_n)^2 \\
$$
​		average diversification
$$
\bar{\delta_n} = \frac{1}{N} \sum_{n=0}^{N}\delta_n
$$
​	3)  $\alpha_p$: the $\alpha$ of the portfolio in the expected return $\beta$ relationship from CAPM. 
$$
\mu^{i} - r_f = \alpha^{(i)} + \beta^{(i)}(\mu_m - r_f)\\
\mu_p - r_f = \alpha_p + \beta_p(\mu_m - r_f)
$$
Examples of risk measures: 
	1) variance of portfolio $\sigma_p^2 $
	2) value at risk $\text{VaR}_{\alpha}(r)$ and conditional value at risk(expected shortfall) $\text{CVaR}_{\alpha}(r)$
	3) $\beta_p$ from the CAPM

Some of combinations of these are made to create performance criteria
$$
\begin{aligned}
& \frac{\mu_p - r_f}{\sigma_p}    &\text{Sharpe ratio} \\
&\frac{\mu_p - r_f}{\beta_p}   &\text{Treynor ratio} \\
& \frac{\alpha_p}{\beta_p}  &\text{Treynor-Black ratio} \\
\end{aligned}
$$
One more risk measures : Maximum Drawdown. Define drawdown
$$
\begin{aligned}
	& M_n = \max \{W_k:k \leq n\} \\
	& D_n = M_n - W_n
\end{aligned}
$$
Relative Drawdown
$$
R_n = \frac{D_n}{M_n}
$$


### 3. Dynamic utility maximization in discrete time

#### 3.1 Dynamic consistency and stochastic dominance

Two issues with $M-V$ optimization which motivate moving on. 
	1) By example, consider the following price dynamics

<img src="C:\Users\24410\OneDrive\桌面\WeChat Image_20190429170308.jpg" alt="Image" height="275" width="475">

​	Given $\theta$, we can draw a trace for portfolio value

<img src="C:\Users\24410\OneDrive\桌面\WeChat Image_20190429172301.jpg" alt="Image" height="270" width="470">

​	now we have 4 possible outcomes of $W_2$ for any fixed $\boldsymbol \theta $. We can compute $\mathbb{E}(W) $ and $ \mathbb{V}(W)$ as a function 	of $\boldsymbol{\theta}$. Then using the mean-variance optimization. the problem here is
$$
\max \ \mathbb{E}(W_2) - \frac{\gamma}{2}\mathbb{V}(W_2)
$$
​	Now consider the sub-tree of the above two step binomial tree: 

<img src="C:\Users\24410\OneDrive\桌面\WeChat Image_20190429194720.jpg" alt="Image" height="225" width="475">
$$
\max_{\theta_0} \ \mathbb{E}(W_1) - \frac{\gamma}{2}\mathbb{V}(W_1)
$$
​	The result is that $\theta^u_1$ in the original problem $\neq \theta_0$ in the "subproblem". Mean-variance optimization is 	   dynamically  inconsistent. Future trading strategy is no longer optimal once you arrive in the future. 
​	2) By example. Consider the following distribution of future wealth:
$$
W_1 = 
\left\{
		\begin{array}\
				 a, \ p \\
				 b, \ 1-p
		\end{array}
\right.
$$

$$
\begin{aligned}
&\mathbb{E}(W_1) = ap + b(1-p)\\
&\mathbb{V}(W_1) = a^2p + b^2(1-p) - \left(ap+b(1-p)\right)^2
\end{aligned}
$$

$$
\begin{aligned}
&\mathbb{E}(W_1) - \frac{\gamma}{2}\mathbb{V}(W_1) \\
& = ap + b(1-p) - \frac{\gamma}{2}\left(a^2p + b^2(1-p) \right) + \frac{\gamma}{2} (ap+b(1-p))^2 \\
& = -\frac{\gamma}{2}p(1-p)a^2 + K
\end{aligned}
$$

Given two choices: $W_1(a_1)$ or $W_1(a_2)$ with $a_2>a_1$. Common sense says always choose greater $a$ for fixed $b$ and $p$. But M-V criteria for sufficient large $a$, performance begin to decrease. Suppose that 2 distributions of future wealth. 

<img src="C:\Users\24410\OneDrive\桌面\WeChat Image_20190429213158.jpg" alt="Image" height="225" width="475">

The CDF of two distributions.Which continuous CDF is preferred? We would prefer the green one. If two CDF's have this type of behavior, we say 
$$
X >^{d_1} Y \Longleftrightarrow F_x(z) < F_y(z)
$$
X is greater than Y by first order stochastic dominance. So the second problem with M-V is that it is inconsistent with performance dictated by first-order stochastic dominance.  Common sense says any good performance criteria should agree with decisions based on first-order stochastic dominance. Next we will show that expected utility maximization solves both problems. 
1) Suppose $X  \geq_{d_1} Y$ . Need to show that $\mathbb{E}\left[u(X)\right] \geq \mathbb{E}\left[u(Y)\right]$. Where $U $ is an increasing function. Assume $F_x$ and $F_y$ are continuous strictly increasing. Define a new random variable $\tilde Y $. 
$$
\tilde Y = F_y^{-1}\left(F_x(X)\right)
$$
Then $\tilde Y \sim F_y$. 
$$
\begin{aligned}
	&   \quad \ \mathbb{P}(\tilde Y \leq z) \\
	& = \mathbb{P} \left( F_y^{-1}\left(F_x(X) \right) \leq z\right) \\
  & = \mathbb{P} \left( F_x(X) \leq F_y(z)\right) \\
  & = \mathbb{P}(X \leq F_x^{-1}(F_y(z))) \\
  & = F_x(F_x^{-1}(F_y(z))) \\
  & = F_y(z)
\end{aligned}
$$
Therefore $\mathbb{E} [u(Y)] = \mathbb{E}[u(\tilde Y)]$. By construction we have 
$$
\begin{aligned}
\tilde Y \leq X \ \ a.s. & \Rightarrow\mathbb{E}[u(\tilde Y)] \leq \mathbb{E}[u(X)] \\
 & \Rightarrow \mathbb{E}[u( Y)] \leq \mathbb{E}[u(X)]
\end{aligned}
$$
Hence problem 2) solved. Go back to problem 1).  

#### 3.2 Dynamic programming principle

##### Derive the Dynamic Programming Principle of Maximum Expected Utility

Recall our objective 
$$
\sup_{\boldsymbol{\theta}} \mathbb{E}\left[ u(W_N)\right]
$$
we will derive a dynamic programming principle which does not hold for M-V. To make this slightly easier, we will make two assumptions: 
1) $\{P\}_{n=0}^N$ has Markov property. 
2) At any time, the trading strategy $\theta_n  = f_n(P_n,W_n)$.

Definition: A stochastic process $\{X_n\}^N_{n=0}$ is said to have the Markov property if: 
$$
\mathbb{E}\left[g(X_n)|\mathcal{F}_m\right] = \mathbb{E}\left[g(X_n)|X_m\right], \ n \geq m
$$
for any function $g$. Filtration $\mathcal{F}_m$ represents all information in the history of the market up to time $m$.  The Markov property above is equivalent to 
$$
\mathbb{P}\left(X_n \leq x|\mathcal{F}_m\right)=\mathbb{P}\left(X_n \leq   x|X_m\right), \ n \geq m
$$
Assumptions 1) and 2) together imply that the joint process $\{(P_n,W_n)\}^N_{n=0}$ also has the Markov property. Proof:  
$$
\begin{aligned}
& W_n = X_n + \theta_n P_n \\
& W_{n+1} = X_n(1+r) + \theta_n P_{n+1}\\
& W_{n+1} = (W_n - \theta_n P_n)(1+r) + \theta_nP_{n+1} \\
& W_{n+1} = W_n(1+r) - (1+r)f_n(P_n,W_n)P_n + f_n(P_n,W_n) P_{n+1}
\end{aligned}
$$
Thus the distribution of $W_{n+1}$ only depends on $P_n$ and $W_n $. The problem we try to solve is
$$
\sup_{\boldsymbol{\theta \in\mathcal{A}}} \mathbb{E}\left[ u(W_N)\right], \ \mathcal{A} = \{(\theta_{0},\dots,\theta_{N-1}): \theta_n = f_n(P_n,W_n)\}
$$
This is an infinite dimensional optimization. Our technique will be to define a large class of optimization problems of which one of them is our original optimization. Also we will find a relationship between all of the problems. It will change the dimension of the optimization: instead of one infinite dimension problem, we will have an infinite number (parameterized) of finite dimensional problems. 

Definition: The dynamic **value function** is defined by: 
$$
\begin{aligned}
& H(n,P_n,W_n) = \sup_{\boldsymbol{\theta \in\mathcal{A_n}}} \mathbb{E}\left[ u(W_N)\right | \mathcal{F_n}] \\
& \mathcal{A_n} = \{(\theta_n,\dots, \theta_{N-1}):\theta_K = f_K(P_K,W_K) \}
\end{aligned}
$$
Our original problem corresponds to $H(0,P_0,W_0)$. Consider at the end time horizon
$$
\begin{aligned}
H(N,P_N,W_N) & = \mathbb{E}\left[ u(W_N)\right | \mathcal{F}_N] \\
	 & = u(W_N)
\end{aligned}
$$
Now consider 
$$
\begin{aligned}
H(N-1,P_{N-1},W_{N-1}) & = \sup_{\boldsymbol{\theta \in\mathcal{A}_{N-1}}} \mathbb{E}\left[ u(W_{N})\right | \mathcal{F}_{N-1}] \\
& = \sup_{\boldsymbol{\theta \in\mathcal{A}_{N-1}}} \mathbb{E}\left[H(N,P_N,W_N)| \mathcal{F}_{N-1} \right]
\end{aligned}
$$
for any fixed value of $P_{N-1}$ and $W_{N-1}$, this is a finite dimensional optimization. This optimization results in a value of $\theta_{N-1}$ which will depend on the given $P_{N-1}$ and $W_{N-1} $. The maximizer $\theta^{*}_{N-1}$ 
$$
\theta^{*}_{N-1}  = f_{N-1}(P_{N-1},W_{N-1})
$$
Suppose we know $\theta^{*}_{N-1}  = f_{N-1}(P_{N-1},W_{N-1})$, now we want to consider 
$$
\begin{aligned}
H(N-2,P_{N-2},W_{N-2})  & = \sup_{\boldsymbol{\theta \in\mathcal{A}_{N-2}}} \mathbb{E}\left[ u(W_{N})\right | \mathcal{F}_{N-2}] \\
& =  \sup_{\boldsymbol{\theta \in\mathcal{A}_{N-2}}} \mathbb{E}\left[ H(N,P_N,W_N)\right | \mathcal{F}_{N-2}] \\

\end{aligned}
$$
Introduce the Law of Iterated Expectation: 
$$
\mathbb{E}\bigg[ \mathbb{E}\big[ H(N,P_N,W_N) | \mathcal{F}_{N-1}\big] |\mathcal{F}_{N-2}\bigg] = \mathbb{E}\left[ H(N,P_N,W_N)\right | \mathcal{F}_{N-2}]
$$
$ \mathbb{E}\big[ H(N,P_N,W_N) | \mathcal{F}_{N-1}\big] \longrightarrow$ your "best guess" of $H(N,P_N,W_N)$ from the perspective of time $N-1$. 
$\mathbb{E}\bigg[ \mathbb{E}\big[ H(N,P_N,W_N) | \mathcal{F}_{N-1}\big] |\mathcal{F}_{N-2}\bigg]  \longrightarrow$ your "best guess" of time $N-2$ of your "best guess" at time $N-1 $. $\mathbb{E}\left[ H(N,P_N,W_N)\right | \mathcal{F}_{N-2}] \longrightarrow$  your "best guess" of the terminal value at time $N-2 $. 

In general, we have
$$
\mathbb{E} \Big[ \mathbb{E}\big[X_N|\mathcal{F}_n\big]\Big| \mathcal{F}_m\Big] = \mathbb{E} \big[X_N\big|\mathcal{F}_m\big], \ m \leq n \leq N
$$
Law of Iterated Expectation gives
$$
H(N-2,P_{N-2},W_{N-2}) =  \sup_{\boldsymbol{\theta \in\mathcal{A}_{N-2}}} \mathbb{E}\bigg[ \mathbb{E}\big[ H(N,P_N,W_N) | \mathcal{F}_{N-1}\big] \bigg|\mathcal{F}_{N-2}\bigg] \tag{*1}
$$
Recall that
$$
H(N-1,P_{N-1},W_{N-1}) = \sup_{\boldsymbol{\theta \in\mathcal{A}_{N-1}}} \mathbb{E}\left[H(N,P_N,W_N)| \mathcal{F}_{N-1} \right] \\
\Longrightarrow H(N-1,P_{N-1},W_{N-1}) \geq \ \mathbb{E}\left[H(N,P_N,W_N)| \mathcal{F}_{N-1} \right]
$$
Replace the inner conditional expectation in (*1) with $H(N-1,P_{N-1},W_{N-1}) $ which makes it bigger: 
$$
H(N-2,P_{N-2},W_{N-2}) \leq \sup_{\boldsymbol{\theta \in\mathcal{A}_{N-2}}} \mathbb{E}\big[H(N-1,P_{N-1},W_{N-1}) \big|\mathcal{F}_{N-2} \big] \tag{*2}
$$
Return to (*1)
$$
H(N-2,P_{N-2},W_{N-2}) =  \sup_{\boldsymbol{\theta \in\mathcal{A}_{N-2}}} \mathbb{E}\bigg[ \mathbb{E}\big[ H(N,P_N,W_N) | \mathcal{F}_{N-1}\big] \bigg|\mathcal{F}_{N-2}\bigg] \tag{*1}
$$
Consider a subset of the original solution, this gives
$$
\begin{aligned}
& H(N-2,P_{N-2},W_{N-2}) \geq  
\sup_ {\boxed {{\boldsymbol{\theta \in \mathcal{A}_{N-2}^{'}}} }}
\mathbb{E}\bigg[ \mathbb{E}\big[ H(N,P_N,W_N) | \mathcal{F}_{N-1}\big] \bigg|\mathcal{F}_{N-2}\bigg] \\

& \mathcal{A}_{N-2}^{'} = \Big\{(\theta_{N-2},\theta_{N-1}):\theta_{N-2} = f_{N-2}(P_{N-2},W_{N-2}) \ \text{and} \ \theta_{N-1} = \theta_{N-1}^{*} \Big\} \subseteq \mathcal{A}_{N-2}
\end{aligned}
$$

The second parameter $\theta_{N-1}^{*}$ is fixed and already solved. If  $\theta_{N-1} = \theta_{N-1}^{*}$, then 
$$
\begin{aligned}
\mathbb{E}\big[H(N,P_N,W_N)| \mathcal{F}_{N-1}\big] & = \sup_{\theta \in\mathcal{A}_{N-1}} \mathbb{E}\big[H(N,P_N,W_N)| \mathcal{F}_{N-1}\big] \\
& = H(N-1,P_{N-1},W_{N-1})
\end{aligned}
$$
In the above inequality, replace the inner conditional expectation with $H(N-1,P_{N-1},W_{N-1})$: 
$$
H(N-2,P_{N-2},W_{N-2}) \geq  
\sup_ {\boxed {{\boldsymbol{\theta \in \mathcal{A}_{N-2}^{'}}} }}
\mathbb{E}\bigg[ H(N-1,P_{N-1},W_{N-1}) \bigg|\mathcal{F}_{N-2}\bigg] \\
$$
But $P_{N-1}, W_{N-1} $ conditional on $\mathcal{F}_{N-2}$ does not depend on $\theta_{N-1} $. 
$$
H(N-2,P_{N-2},W_{N-2}) \geq \sup_{\boldsymbol{\theta \in\mathcal{A}_{N-2}}} \mathbb{E}\big[H(N-1,P_{N-1},W_{N-1}) \big|\mathcal{F}_{N-2} \big] \tag{*3}
$$
Combine (*2) and (\*3): 
$$
\begin{aligned}
H(N-2,P_{N-2},W_{N-2}) & = \sup_{\boldsymbol{\theta \in\mathcal{A}_{N-2}}} \mathbb{E}\big[H(N-1,P_{N-1},W_{N-1}) \big|\mathcal{F}_{N-2} \big] \\
& =\ \sup_{\boldsymbol{\theta_{N-2} }} \ \ \ \mathbb{E}\big[H(N-1,P_{N-1},W_{N-1}) \big|\mathcal{F}_{N-2} \big]
\end{aligned}
$$
**In general**
$$
H(n-1,P_{n-1},W_{n-1}) = \sup_{\boldsymbol{\theta_{n-1} }} \ \ \ \mathbb{E}\big[H(n,P_{n},W_{n}) \big|\mathcal{F}_{n-1} \big]
$$
With the starting point
$$
H(N,P_N,W_N) = u(W_N)
$$
This is called **Dynamic Programming Principle**. 

Example: One asset: $P_n = P_{n-1}(1+r_n)$ where all $r_n$'s are independent. $r_n \sim \mathcal{N}(\mu,\sigma^2)$ . Risk free rate $r_f $. And assume no transaction costs. With the exponential utility $u(W) = - e^{-\gamma w}$. Find $\theta_0,\dots,\theta_{N-1}$ which maximize $\mathbb{E} \big[ -e^{-\gamma W_N}\big]$
$$
\begin{aligned}
&H(N,P_N,W_N) = -e^{-\gamma W_N} \\
\end{aligned}
$$

$$
\begin{aligned}
H(N-1,P_{N-1},W_{N-1}) & = \sup_{\boldsymbol{\theta_{N-1} }}  \ \ \mathbb{E}\big[H(N,P_{N},W_{N}) \big|\mathcal{F}_{N-1} \big] \\
& = \sup_{\boldsymbol{\theta_{N-1} }} \  \  \mathbb{E} \big[-e^{-\gamma W_N}\big| \mathcal{F}_{N-1}\big]
\end{aligned}
$$

For general $n$: 
$$
\begin{aligned}
	W_n  	  &= X_n + \theta_n P_n \\
	W_{n+1} &= X_n(1+r_f) + \theta_n P_{n+1} \\
  W_{n+1} &= (W_n - \theta_n P_n)(1+r_f) + \theta_n P_{n+1} \\
  W_{n+1} &= W_n(1+r_f) - \theta_n P_n r_f + \theta_n P_n r_{n+1}
\end{aligned}
$$
Thus we have
$$
\begin{aligned}
& H(N-1,P_{N-1},W_{N-1}) = \sup_{\boldsymbol{\theta_{N-1} }} \  \mathbb{E} \bigg[ -\mathbb{exp}\Big(-\gamma \big(W_{N-1}(1+r_f)-\theta_{N-1}P_{N-1}r_f + \theta_{N-1}P_{N-1}r_N \big) \Big) \bigg| \mathcal{F}_{N-1} \bigg ] \\
& \quad =\sup_{\boldsymbol{\theta_{N-1} }} \ -\mathbb{exp}\Big[ -\gamma \big( W_{N-1}(1+r_f)-\theta_{N-1}P_{N-1}r_f\big)\Big] \mathbb{E} \Big[ \mathbb{exp}\big( -\gamma\theta_{N-1}P_{N-1}r_N \big)\Big|\mathbb{F}_{N-1} \Big] \\
& \quad = \sup_{\boldsymbol{\theta_{N-1} }} \ -\mathbb{exp}\Big[ -\gamma \big( W_{N-1}(1+r_f)-\theta_{N-1}P_{N-1}r_f\big)\Big] \mathbb{exp} \Big(-\gamma\theta_{N-1}P_{N-1}\mu + \frac{\gamma^2}{2}\theta_{N-1}^2 P_{N-1}^2\sigma^2 \Big) \\
& \quad \quad \  \Longrightarrow \theta_{N-1}^{*} = \frac{\mu- r_f}{\gamma \sigma^2 P_{N-1}}
\end{aligned}
$$

$$
H(N-1,P_{N-1},W_{N-1})  =  -\mathbb{exp}\Big(-\gamma\big( W_{N-1}(1+r_f) + \frac{(\mu - r_f)^2}{2\sigma^2\gamma}\big) \Big)
$$

Make an assumption about the general form of $H(n,P_n,W_n)$
$$
H(n,P_n,W_n) = - \mathbb{exp}\big(-\gamma(a_nW_n + b_n )\big) \tag{*4}
$$
carry out the following:  
$$
\sup_{\boldsymbol{\theta_{n-1} }} \  \mathbb{E} \Big[ - \mathbb{exp}\big( -\gamma (a_nW_n + b_n)\big)\Big| \mathcal{F}_{n-1}\Big]
$$
If this can be written in the form $- \mathbb{exp}\big(-\gamma(a_{n-1}W_{n-1} + b_{n-1} )\big)$. 
$$
W_{n} = W_{n-1}(1+r_f) - \theta_{n-1} P_{n-1} r_f + \theta_{n-1} P_{n-1} r_{n}
$$

$$
\begin{aligned}
& \quad \ \sup_{\boldsymbol{\theta }} \  \mathbb{E} \bigg[ -\mathbb{exp} \Big( -\gamma\big( a_n[w(1+r_f)-\theta P r_f +\theta P r_n] + b_n\big)\Big) \bigg|\mathcal{F}_{n-1} \bigg] \\
&= \sup_{\boldsymbol{\theta }} -\mathbb{exp} \bigg\{ -\gamma a_n \Big[ W(1+r_f)-\theta P r_f\Big] - \gamma b_n \bigg\} \ \mathbb{E} \bigg[e^{-\gamma a_n\theta P r_n}\bigg|\mathcal{F}_{n-1}\bigg ] \\
&= \sup_{\boldsymbol{\theta }} -\mathbb{exp} \bigg\{ -\gamma a_n \Big[ W(1+r_f)-\theta P r_f\Big] - \gamma b_n \bigg\} \ \mathbb{exp} \bigg(-\gamma a_n \theta P\mu + \frac{\gamma^2}{2}a_n^2\theta^2P^2\sigma^2\bigg)

\end{aligned}
$$

Then the maximizer $\theta^{*}_{n-1}$ is thus 
$$
\begin{aligned}
& \quad \quad \theta^{*}_{n-1} = \frac{\mu-r_f}{\gamma a_n P_{n-1}\sigma^2} \\
& \Rightarrow H(n-1,P_{n-1},W_{n-1}) = -\mathbb{exp} \bigg\{ -\gamma\Big[ a_n(1+r_f)W_{n-1} + b_n + \frac{(\mu-r_f)^2}{2\gamma\sigma^2} \Big] \bigg\} 
\end{aligned}
$$
Recall our assumption (*4), this allows us to set up a recursion
$$
\begin{aligned}
& a_{n-1} = a_n(1+r_f), a_N = 1   \\
& b_{n-1} = b_n + \frac{(\mu-r_f)^2}{2\gamma \sigma^2}, b_N =0
\end{aligned}
$$
This can be solved:
$$
\begin{aligned}
	& a_n = (1+r_f)^{N-n} \\
	& b_n = \frac{(\mu-r_f)^2}{2\gamma\sigma^2} (N-n)
\end{aligned}
$$
By induction, 
$$
H(n,P_n,W_n) = -\mathbb{exp}\Big[-\gamma \big(a_nW_n + b_n \big)\Big] \\
\theta^{*}_{n} = \frac{\mu-r_f}{\gamma a_{n+1} P_{n}\sigma^2}
$$
The general steps to outline solving a dynamic utility maximization problem. 

​	***Step 1:***  $H(N,P_N,W_N) = u(W_N)$ 

​	***Step 2:***  Write $W_N$ in terms of $W_{N-1}, P_{N-1},\theta_{N-1}$ and some random driver.

​	***Step 3:***  Compute $\mathbb{E} \big[u(W_N)\big| \mathcal{F}_{N-1}\big] $

​	***Step 4:***  Maximize with respect to $\theta_{N-1}$ and substitute $\theta_{N-1}^{*}$ back to get $ H(N-1,P_{N-1},W_{N-1}) $

​	***Step 5:***  a) Hopefully we can identify a general form for $H(n,P_n,W_n) $ based on the first step. b) perform 				  steps 2-4 on the general form of $H(n,P_n,W_n) $. c) ask yourself if the general form also hold for 	   				 $H(n-1,P_{n-1},W_{n-1})$. 

​	***Step 6:***  If Step 5 checks, then we're done, we have $H(n,P_n,W_n) $ and $\theta_{n}^{*}$ from step 4. 

##### Practice problems for Dynamic Utility Maximization. 

1) $P_{n+1} = P_n + Z_{n+1},\ Z_{n}\sim \mathcal{N}(\mu,\sigma^2)$ . Suppose $r_f = 0$. Maximize $\mathbb{E} \big[ -\mathbb{exp}(-\gamma W_N )\big]$ 

2) Exactly the same as 1) but with $r_f \neq 0$ . Hint: doing this requires the formula for $\mathbb{E} \big[ e^{az+bz^2}\big]$

3) Multivariate version: $P^{(i)}_{n+1} = P^{(i)}_n + Z^{(i)}_{n+1}$, $i \in \{1,\dots,K\}$, $\mathbf{Z}_n \sim \mathcal{N}(\boldsymbol{\mu},\boldsymbol{\Omega})$. And $\mathbf{Z}_n \perp \mathbf{Z}_m$ for $n \neq m$. 	   	Assume $r_f = 0$. The goal is to $\max \mathbb{E} \big[ -\mathbb{exp}(-\gamma W_N )\big]$. 

4) Price dynamics $P_{n+1} = P_n(1+r_{n+1})$ or $P_{n+1} = P_n + Z_{n+1}$ same assumptions for $r_{n+1}$ or $Z_{n+1}$. But the 	 objective is $\max \mathbb{E} \big[ W_N - \frac{\gamma}{2}W_N^2\big]$.  $r_f = 0? $

***Solution for problem 2)*** : Find value function and optimal trading strategy. 

The dynamics of wealth through time: 
$$
\begin{aligned}
W_{n+1} & = X_n(1+r) + \theta_n P_{n+1}\\
W_n     &= X_n + \theta_nP_n \\
W_{n+1} 		& = (W_n - \theta_n P_n)(1+r) + \theta_n P_{n+1} \\
 				& = W_n(1+r) - \theta_n P_n - r\theta_nP_n + \theta_n P_n + \theta_nZ_{n+1}\\
        & = W_n(1+r) - r\theta_nP_n + \theta_nZ_{n+1}
\end{aligned}
$$
Step 1: compute
$$
\begin{aligned}
& \ \ \quad \mathbb{E} \Big[ -\mathbb{exp} \big( -\gamma W_N\big)\Big|\mathcal{F}_{N-1} \Big] \\
& = \mathbb{E} \bigg\{ -\mathbb{exp}\Big[ -\gamma \big( W_{N-1}(1+r)-r\theta_{N-1}P_{N-1} + \theta_{N-1}Z_N \big) \Big] \bigg | \mathcal{F}_{N-1} \bigg\}\\
& = - \mathbb{exp} \bigg[-\gamma \Big( W_{N-1}(1+r) - r\theta_{N-1}P_{N-1} \Big) \bigg]  \ \mathbb{E} \bigg[ \mathbb{exp} \Big( -\gamma\theta_{N-1} Z_N\Big) \bigg| \mathcal{F}_{N-1} \bigg] \\
&= - \mathbb{exp} \bigg[-\gamma \Big( W_{N-1}(1+r) - r\theta_{N-1}P_{N-1} \Big) \bigg]  \ \mathbb{exp} \bigg[ -\gamma\theta_{N-1}\mu + \frac{\gamma^2}{2}\theta_{N-1}^2 \sigma^2 \bigg] \\
& = - \mathbb{exp} \bigg\{ -\gamma\Big[ W_{N-1}(1+r) -r\theta_{N-1}P_{N-1}+ \theta_{N-1}\mu - \frac{\gamma}{2}\theta^2_{N-1}\sigma^2 \Big] \bigg\}
\end{aligned}
$$
Step 2: 
$$
\max_{\theta_{N-1}} \ \theta_{N-1}\mu -r\theta_{N-1}P_{N-1} - \frac{\gamma}{2}\theta^2_{N-1}\sigma^2 \\
\Longrightarrow \theta^{*}_{N-1} = \frac{\mu-rP_{N-1}}{\gamma\sigma^2}
$$
Step 3: substitute $\theta^{*}_{N-1}$ into the value function
$$
H(N-1,P_{N-1},W_{N-1}) = -\mathbb{exp} \Big\{ -\gamma\Big[ W_{N-1}(1+r) + \frac{(\mu-rP_{N-1})^2}{2\gamma\sigma^2}\Big]\Big\}
$$
Step 4: assume the following general form
$$
H(n,P_n,W_n) = -\mathbb{exp}\Big[ -\gamma\big(a_nW_n + b_n + c_nP_n + d_nP_n^2 \big)\Big]
$$
Step 5: compute
$$
\mathbb{E} \Big[H\big( n,P_n,W_n\big) \Big|\mathcal{F}_{n-1} \Big] \\
$$
With the dynamics:
$$
\begin{aligned}
	& W_n  = W_{n-1}(1+r) - r\theta_{n-1}P_{n-1} + \theta_{n}Z_{n} \\
	& P_n = P_{n-1} + Z_n
\end{aligned}
$$
Grouping the random and non-random terms together gives the following form:
$$
-\mathbb{exp}\Big[ -\gamma\big( a_nW_{n-1} + b_n + c_nP_{n-1} + d_nP_{n-1}^2 - a_nr\theta_{n-1}P_{n-1} \big)\Big] \ \mathbb{E} \Big[\mathbb{exp}\Big( -\gamma\big( g_nZ_n + h_nZ_n^2\big)\Big) \Big| \mathcal{F}_{n-1}\Big]
$$
Requires use of the following formula: if $X \sim \mathcal{N}(0,\sigma^2)$
$$
\mathbb{E} \Big[ \mathbb{exp}\big(\alpha X + \beta X^2 \big) \Big] = \frac {\mathbb{exp( \frac{\alpha^2\sigma^2}{2\sqrt{1-\beta\sigma^2}})}} {\sqrt{1-\beta\sigma^2}}
$$
Exponent will still be quadratic in $\theta $. Then maximize  it gives $\theta^{*}_{n-1} $, then resubstitute $\theta^{*}_{n-1} $ gives quadratic form in $P_{n-1}$. Thus general form assumed appears to apply, and we can identify $a_{n-1},b_{n-1},c_{n-1},d_{n-1}$ in terms of $a_n, b_n,c_n,d_n$ This recursion along with $a_N = 1$, $b_N = c_N = d_N= 0$ defines the value function of all time. 

***Solution for problem 3)***: 
$$
\begin{aligned}
&P^{(i)}_{n+1} = P^{(i)}_n + Z^{(i)}_{n+1},\ i \in \{1,\dots,K\}\\ 
&  \mathbf{Z}_n \sim \mathcal{N}(\boldsymbol{\mu},\boldsymbol{\Omega}), \mathbf{Z}_n \perp \mathbf{Z}_m,r_f= 0 \\
& \max \mathbb{E} \big[ -\mathbb{exp}(-\gamma W_N )\big]
\end{aligned}
$$
Write down the evolution of wealth
$$
\begin{aligned}
W_n  &= X_n + \boldsymbol{\theta_n^TP_n} +  \\
W_{n+1}  & = X_n + \boldsymbol{\theta_n^TP_{n+1}} \\
& = W_n - \boldsymbol{\theta_n^TP_n} +  \boldsymbol{\theta_n^TP_{n+1}} \\ 
& =  W_n - \boldsymbol{\theta_n^TP_n} +  \boldsymbol{\theta_n^T}(\boldsymbol{P_n} + \boldsymbol{Z_{n+1}}) \\
& = W_n +  \boldsymbol{\theta_n^T}\boldsymbol{Z_{n+1}}
\end{aligned}
$$
The value function
$$
H(N,W_N) = - \mathbb{exp}(-\gamma W_N)
$$
The Dynamic Programming Principle says
$$
H(N-1,W_{N-1}) = \max_{\boldsymbol{\theta_{N-1}}} \ \mathbb{E} \big[-\mathbb{exp}(-\gamma W_N) \big|\mathcal{F}_{N-1}\big]
$$
The expectation:
$$
\begin{aligned}
& \quad \ \mathbb{E} \big[-\mathbb{exp}(-\gamma W_N) \big|\mathcal{F}_{N-1}\big] \\
& = \mathbb{E} \Big[ -\mathbb{exp}\big(-\gamma (W_{N-1} + \boldsymbol{\theta_{N-1}^T}\boldsymbol{Z_{N}})\big) \Big| \mathcal{F}_{N-1} \Big] \\
& = -\mathbb{exp}\big(-\gamma (W_{N-1})\big) \mathbb{E} \big[ \mathbb{exp}(-\gamma \boldsymbol{\theta_{N-1}^T}\boldsymbol{Z_{N}}) \big|\mathcal{F}_{N-1}\big] \\
& = -\mathbb{exp}\big(-\gamma (W_{N-1})\big) \mathbb{exp}\big(-\gamma \boldsymbol {\theta^T}\boldsymbol{\mu}+ \frac{1}{2}\gamma^2 \boldsymbol{\theta^T\Omega\theta}\big) \\
& = - \exp \Big\{ -\gamma \big[W_{N-1} + \boldsymbol{\theta^T}\boldsymbol{\mu} - \frac{1}{2}\gamma \boldsymbol{\theta^T\Omega\theta} \big]\Big\} 
\end{aligned}
$$
The term $-\gamma \boldsymbol{\theta_{N-1}^T}\boldsymbol{Z_{N}} $ is univariate Gaussian: 
$$
-\gamma \boldsymbol{\theta_{N-1}^T}\boldsymbol{Z_{N}}  \sim \mathcal{N} (-\gamma\boldsymbol{\theta^T}\boldsymbol{\mu}, \gamma^2 \boldsymbol{\theta^T\Omega\theta})
$$
Maximization of the expectation:
$$
\max_{\boldsymbol{\theta}} \ \boldsymbol{\theta^T}\boldsymbol{\mu} - \frac{1}{2}\gamma \boldsymbol{\theta^T\Omega\theta} \\
\Rightarrow \boldsymbol{\theta}^{*} = \frac{1}{\gamma} \boldsymbol{\Omega^{-1}\mu}
$$
Resubstitute $\boldsymbol{\theta}^{*}$ 
$$
H(N-1,W_{N-1}) = - \exp \bigg[-\gamma\left(W_{N-1} + \frac{\boldsymbol{\mu^T \Omega^{-1}\mu}}{2\gamma}\right)\bigg]
$$
Make an assumption
$$
H(n,W_n) = -\exp\Big[-\gamma\big(W_n + a_n\big)\Big]
$$
Apply the DPP
$$
H(n,W_n) = \max_{\boldsymbol{\theta}} \ \mathbb{E}\Big\{-\exp\big[-\gamma(W_{n+1}+a_{n+1})\big]\Big| \mathcal{F}_n\Big\}
$$
Compute the expectation 
$$
\begin{aligned}
& \ \quad \mathbb{E}\Big\{-\exp\big[-\gamma(W_{n+1}+a_{n+1})\big]\Big| \mathcal{F}_n\Big\} \\
& = \mathbb{E}\Big\{-\exp\big[-\gamma(W_n+\boldsymbol{\theta^TZ_{n+1}}+a_{n+1})\big]\Big| \mathcal{F}_n\Big\} \\
& =- \exp\Big[-\gamma\big(W_n + a_{n+1}\big)\Big] \mathbb{E}\Big[\exp\big(-\gamma \boldsymbol{\theta^TZ_{n+1}}\big)\Big|\mathcal{F}_n\Big] \\
& = - \exp\Big[-\gamma\big(W_n + a_{n+1} + \boldsymbol{\theta^TZ_{n+1}} -\frac{\gamma}{2}\boldsymbol{\theta^T\Omega\theta}\big) \Big] 
\end{aligned}
$$
The Maximizer gives
$$
\boldsymbol{\theta}^{*} = \frac{1}{\gamma} \boldsymbol{\Omega^{-1}\mu}
$$
Resubstitute we will have
$$
H(n,W_n) = - \exp \Big[-\gamma \left( W_n + a_{n+1} + \frac{\boldsymbol{\mu^T \Omega^{-1}\mu}}{2\gamma}\right)\Big]
$$
Identify recursion, we must choose $a_n$ such that 
$$
a_n = a_{n+1} + \frac{\boldsymbol{\mu^T \Omega^{-1}\mu}}{2\gamma}, a_{N} = 0 \\
\Rightarrow a_n = \frac{\boldsymbol{\mu^T \Omega^{-1}\mu}}{2\gamma} (N-n)
$$
The final answer
$$
H(n,W_n) = -\exp\Big[-\gamma\big(W_n + a_n\big)\Big], \ a_n = \frac{\boldsymbol{\mu^T \Omega^{-1}\mu}}{2\gamma} (N-n)
$$
And the optimal strategy
$$
\boldsymbol{\theta}^{*}(n,P_n,W_n) = \frac{1}{\gamma} \boldsymbol{\Omega^{-1}\mu}
$$
is a constant. 

***Solution for problem 4)*** 
$$
P_{n+1} = P_n(1+r_{n+1}), \ r_n \sim \mathcal{N}(\mu,\sigma^2), r_f \neq 0
$$
The objective is 
$$
\max \mathbb{E} \left[W_N - \frac{\gamma}{2}W_N^{2}\right]  
$$

$$
\begin{aligned}
W_n &= X_n + \theta_n P_n \\
W_{n+1} &= X_n(1+r_f) + \theta_{n}P_{n+1} \\
&= (W_n - \theta_n P_n)(1+r_f) + \theta_n P_n(1+r_{n+1}) \\
& = W_{n}(1+r_f) +  \theta_n P_n(r_{n+1}-r_f)
\end{aligned}
$$

Make an assumption
$$
H(n,W_n) = a_n + b_n W_n + c_n W_n^2
$$
With Dynamic Programming Principle:
$$
\begin{aligned}
H(n-1,W_{n-1}) &= \max_{\theta} \ \mathbb{E}\big[ a_n + b_n W_n + c_n W_n^2 \big| \mathcal{F}_{n-1}\big] \\
& = a_n + \max_{\theta} \bigg\{b_n \mathbb{E}\Big[W_n \Big| \mathcal{F}_{n-1}\Big]+ c_n \mathbb{E}\Big[W_{n}^2\Big| \mathcal{F}_{n-1}\Big] \bigg\}  
\end{aligned}
$$

$$
\begin{aligned}
\mathbb{E}\Big[W_n \Big| \mathcal{F}_{n-1}\Big] &= \mathbb{E}\Big[W_{n-1}(1+r_f)+\theta_n P_n(r_{n+1}-r_f)\ \Big|\mathcal{F}_{n-1} \Big] \\
 & = W_{n-1}(1+r_f) + \theta_n P_n \mu_e\\
 \end{aligned}
$$

$$
\begin{aligned}
\mathbb{E}\big[W_n^2 \big| \mathcal{F}_{n-1}\big] &= \mathbb{V}\big[W_n\big| \mathcal{F}_{n-1}\big] + \Big(\mathbb{E}\big[W_n\big|\mathcal{F}_{n-1}\big]\Big)^2 \\
& =\theta^2_{n-1}P^{2}_{n-1}\sigma^2 + [W_{n-1}(1+r_f) + \theta_n P_n \mu_e]^2
\end{aligned}
$$

$$
H(n-1,W_{n-1}) = a_n + b_nW_{n-1}(1+r_f) + \max_{\theta} \bigg\{ b_n\theta_{n-1}P_{n-1}\mu_e + \\
c_n\Big[\theta^2_{n-1}P^{2}_{n-1}\sigma^2 + [W_{n-1}(1+r_f) + \theta_n P_n \mu_e]^2\Big] \bigg\}
$$

Then the maximizer
$$
\theta^{*} = \frac{-\mu_e\big(b_n + 2W_{n-1}(1+r_f)c_n\big)}{2c_nP_{n-1}(\sigma^2+\mu_e^2)}
$$
Resubstitute
$$
\begin{aligned}
H(n-1,W_{n-1}) & = a_n +b_nW_{n-1}(1+r_f)+ c_n W_{n-1}^2(1+r_f)^2 + \\
&\max_{\theta}\big\{ b_n\theta_{n-1}P_{n-1}\mu_e + c_n\theta_{n-1}^2P^2_{n-1}\sigma^2 +  c_n\theta_{n-1}^2P^2_{n-1}\mu^2 + 2c_nW_{n-1}(1+r_f)\theta_{n}P_{n}\mu_e \big\} \\
& = a_n  +b_nW_{n-1}(1+r_f)+ c_n W_{n-1}^2(1+r_f)^2 - \frac{\mu_e^2\Big(b_n +2c_nW_{n-1}(1+r_f)\Big)^2}{4c_n(\sigma^2 + \mu_e^2)} \\
& = a_n- \frac{\mu_e^2b_n^2}{4c_n(\sigma^2+\mu_e^2)} + W_{n-1}\left\{ b_n(1+r_f)- \frac{\mu_e^2b_n(1+r_f)}{(\sigma^2 +\mu_e^2)}\right\} \\
 & \quad + W_{n-1}^2 \left\{ c_n(1+r_f)^2-\frac{\mu_e^2c_n(1+r_f)}{(\sigma^2 +\mu_e^2)} \right\}
\end{aligned}
$$
Then we can identify the recursion:
$$
\begin{aligned}
	& a_{n-1} = a_n- \frac{\mu_e^2b_n^2}{4c_n(\sigma^2+\mu_e^2)} \ ,a_N= 0 \\
	& b_{n-1} = b_n(1+r_f)- \frac{\mu_e^2b_n(1+r_f)}{(\sigma^2 +\mu_e^2)} \ , b_N=1\\
	& c_{n-1} =  c_n(1+r_f)^2-\frac{\mu_e^2c_n(1+r_f)}{(\sigma^2 +\mu_e^2)} \ , c_N = \frac{-\gamma}{2}
\end{aligned}
$$

$$
b_n = K_b^{N-n}, K_b = (1+r_f)\left(1- \frac{\mu_e^2}{\mu_e^2+\sigma^2}\right) \\
c_n = -\frac{\gamma}{2}K_c^{N-n}, K_c = (1+r_f)^2\left(1- \frac{\mu_e^2}{\mu_e^2+\sigma^2}\right) \\
$$

What does the optimal trading strategy tells us? 
$$
\theta^{*} = \frac{-\mu_e\big(b_n + 2W_{n-1}(1+r_f)c_n\big)}{2c_nP_{n-1}(\sigma^2+\mu_e^2)} 
$$
With large wealth, we have to take short positions. 

This mess is one piece of motivation for why we will move to continuous time. Previously, we derive the Dynamic Programming Principle for expected utility optimization.  We know by example that there is no DPP for mean-variance optimization. Where does the derivation of DP break down for M-V?  This is because the Law of iterated expectation does not have a mean-variance equivalent.  



### 4.Continuous Time Stochastic Processes

Now let us move to continuous time models. We start by looking at the dynamics of wealth:
$$
\left\{
		\begin{array}\
				 W_{n+1} = X_n(1+r) + \theta_n P_{n+1} \\
				 W_n = X_n + \theta_n P_n
		\end{array}
\right.
$$

$$
\longrightarrow 
\left\{
		\begin{array}\
				 W_{t} = X_t + \theta_t P_{t} \\
				 W_{t+\Delta t} = X_t(1+r \Delta t)
		\end{array}
\right.
$$

Where $r$ is annualized. Take a difference:
$$
W_{t+\Delta t} - W_t= X_tr \Delta t + \theta_t(P_{t+\Delta t} - P_t) \\
\Delta W_t = X_t r\Delta t + \theta_t \Delta P_t
$$
If we are to think about continuous time models, we want "$\Delta \mapsto d$"
$$
dW_t = rX_tdt + \theta_t dP_t
$$
This equation of evolution along with $W_t = X_t  + \theta_{t}P_t$ ensure that self-financing is enforced. The limiting procedure "$\Delta t \mapsto dt$" is fairly non-rigorous. We will just take the continuous dynamics as our starting point. 

*Exercise:* redo the above limits with transaction costs. You will have a problem here. 

Why might me care about solving problems in continuous time? 1) as we have seen above, even simple dynamics in discrete time become intractable very quickly. 2) Discrete time has a lot restrictions on the dynamics and utility function we may use. For example: consider the following problem. With power utility function 
$$
\max_{\theta} \ \mathbb{E}\left[\frac{W_N^{1-\gamma}}{1-\gamma}\right]
$$
Recall that the power utility is only defined for $W >0 $. We can extend the problem to negative wealth. Then there is restriction on the price dynamics or the distribution of returns. In particular, it is bounded below which results in non-Gaussian, no lower tail.  
3) We have many more power tools at analysis and many more models have been extensively studied in continuous time. 

Definition: A stochastic process $\{ X_t\}_{0 \leq t \leq T}$ is a collection of random variables indexed by some set, in this case the interval $[0,T]$. There are at least 2 conceptual ways to think about a stochastic process, depending on context:
$$
t \mapsto X_t(\omega) \quad \text{for fixed } \omega \\
\omega \mapsto X_t(\omega) \quad \text{for fixed } \omega
$$

#### 4.1 Markov property and Matingales

<u>Definition of Markov Property :</u>  $\{X_t\}$ is said to have the Markov property if for any $g,s$ and $t$ there is a function $f(.)$ such that 
$$
\mathbb{E} \big[g(X_t) \big| \mathcal{F}_s\big] = f(X_s), \ s \leq t
$$
Why is the Markov property useful? It will drastically reduce the dimension of our computation. Rather than keeping track of an entire path, we only need to keep track of a single point. 

<u>Definition of Martingale Property:</u> $\{X_t\}$ is said to be a Martingale if :

​	1) $\mathbb{E} \big[ |X_t| \big] < \infty$ for all $0 \leq t \leq T$

​	2) $\mathbb{E} \big[ X_t \big | \mathcal{F}_s \big] = X_s$ for $s \leq t$ 

Expected value of $X$ in the future is wherever X is now. Why are Martingales important? Often we will have some kind of process that through various methods we may deduce it is a Martingale. This will put restrictions on other related quantities. If we notice something is a Martingale, we get as equation for free. 

#### 4.2 Brownian Motion 

<u>Definition of Brownian Motion</u>: $\{B_t\}$ is a Brownian Motion if 

​	1) $B_0 =0 $  almost surely

​	2) $B_t \sim \mathcal{N}(0,t)$. $\sigma^2 = t$

​	3) $B_{t_4} - B_{t_3} \perp B_{t_2} - B_{t_1}$, for $t_1 \leq t_2 \leq t_3 \leq t_4$

​	4) $B_{t_2} - B_{t_1} \sim \mathcal{N} (0, t_2- t_1)$

Properties of Brownian Motion.  

​	1) $B_t$ has the Markov property

​	2) $B_t$ is a Martingale

​	3) for each $\omega$, the function $t \mapsto B_t(\omega)$ is continuous 

​	4) for each $\omega$, the function $t \mapsto B_t(\omega)$ is nowhere differentiable. 

Property 1) of Brownian motion. We want to show that for any function $g$, and any $s < t$ we can find a function $f$ such that 
$$
\mathbb{E} \big[g(B_t)\big| \mathcal{F}_s\big] = f(X_s)
$$
Compute
$$
\begin{aligned}
\mathbb{E}\big[g(B_t)\big|\mathcal{F}_s\big]& = \mathbb{E}\big[g(B_s + B_t - B_s)\big| \mathcal{F_s}\big] \\ 
 & = \mathbb{E}\big[g(B_s + Z)\big|\mathcal{F}_s\big] \\
 & = \int^{\infty}_{-\infty}g(B_s + x) \frac{\mathbb{exp}\big(-x^2/2(t-s)\big)}{\sqrt{2\pi(t-s)}}dx \\
 & =f(B_s)
\end{aligned}
$$
Property 2) we need to show that
$$
\mathbb{E} \big[B_t \big| \mathcal{F}_s\big] = B_s
$$
Again, we just compute 
$$
\begin{aligned}
\mathbb{E}\big[g(B_t)\big|\mathcal{F}_s\big]& = \mathbb{E}\big[g(B_s + B_t - B_s)\big| \mathcal{F_s}\big] \\ 
 & = \mathbb{E}\big[g(B_s + Z)\big|\mathcal{F}_s\big] \\ 
 & = B_s + \mathbb{E} \big[Z\big|\mathcal{F}_s\big] \\
 & =B_s
 \end{aligned}
$$

#### 4.3 Ito' Lemma

We will introduce two methods of constructing new stochastic processes from old ones, and relate these methods by Ito's Lemma. 
1) Given a process $\{X_t\}$, define $ Y_t = f(X_t) $ . Then $Y_t$ is a new process. 
2) Define a new process using stochastic differential equations. Let us draw some intuition from ODEs'. In 	particular, the numerical solutions of ODEs.  

Example of Ordinary Differential Equations. 
$$
\begin{aligned}
& \frac{df(x)}{dx} = \sin\big(f(x)\big) + x,\ f(0) = 0 \\
& f'(0) = \sin\big(f(0)\big) + 0 = 0 \\
& f'(\Delta x) \approx \sin\big(f(\Delta x)\big) + \Delta x = \Delta x \\
& f'(2\Delta x) \approx \sin\big(f(2\Delta x)\big) + 2\Delta x = (\Delta x)^2 + 2\Delta x \\ 
& \  \ \vdots \\
& f'(T-\Delta x) \approx  \cdots \Longrightarrow f(T) \ \ \text{as an approximation}
\end{aligned}
$$
as $\Delta x \rightarrow 0 $ the accuracy improves. Generally, 
$$
\frac{f\big(n \Delta x\big)- f\big((n-1)(\Delta x)\big)}{\Delta x} \approx \sin \Big( f\big((n-1)\Delta x\big)\Big) + (n-1) \Delta x
$$
We will use the same idea, but at each time step we add a small random component. 
$$
d X_t = \mu(X_t)dt + \sigma(X_t)dW_t \tag{*1}
$$
should interpret it in the discrete form analogous to ODEs'. 
$$
X_{t+\Delta t} - X_t = \mu(X_t) \Delta t + \sigma(X_t)(B_{t+\Delta t}- B_t)
$$
Where $B_{t+\Delta t}- B_t \sim \mathcal{N}(0,\Delta t )$. As $\Delta t \rightarrow 0$, we end up with a stochastic process at all times. The discrete approximation of $X_t$ will end up having the correct distribution to the solution of *1

SDEs' provide a method of constructing stochastic process using Brownian motion as our driver or building block. Given $X_t$ which is constructed through
$$
d X_t = \mu(t,X_t)dt + \sigma(t,X_t)dW_t
$$
Properties: 
	1) $X_t$ has the Markov property
	2) If $\mu \equiv 0$ for all index $(t,x) $then $X_t$ is a martingale. 
	3) If $X_t$ is martingale, then $\mu \equiv 0$.
	4) $t \mapsto X_t$ is continuous, and if $\sigma^2 >0$ non-differentiable. 
	5) If $\mu$ and $\sigma$ are function only of $t$ and not $X_t$, then $X_t$ has Gaussian distribution.
$$
\begin{aligned}
\mathbb{E}\big[X_t\big] &= x + \int_0^t \mu(s)ds \\
\mathbb{V}\big[X_t\big] &= \int_0^t \sigma^2(s)ds \\
\end{aligned}
$$
Question: Given $d X_t = \mu(t,X_t)dt + \sigma(t,X_t)dW_t, X_0 = x$ and $Y_t = f(t,X_t)$, is there an SDE for $Y_t$? The answer is given by Ito's Lemma. Let us start with discrete form of the problem.
$$
\begin{aligned}
Y_{t+\Delta t} & = f(t+ \Delta t, X_{t+\Delta t}) \\
 & \approx f(t,X_t) + \frac{\partial{f}}{\partial t}\Delta t + \frac{\partial{f}}{\partial x}\Delta X_t + \frac{1}{2} \frac{\partial^2f}{\partial x^2} (\Delta X_t)^2 \\
 & =   Y_t + \frac{\partial{f}}{\partial t}\Delta t + \frac{\partial{f}}{\partial x} \Big[ \mu\big(t,X_t\big)\Delta t + \sigma \big( t,X_t\big)\Delta B_t\Big] + \frac{1}{2} \frac{\partial^2f}{\partial x^2} \Big[ \mu\big(t,X_t\big)\Delta t + \sigma \big( t,X_t\big)\Delta B_t\Big]^2 \\
 &  = Y_t + \Big[\frac{\partial{f}}{\partial t} + \frac{\partial{f}}{\partial x}\mu\big(t,X_t\big) + \frac{1}{2} \frac{\partial^2f}{\partial x^2}\sigma^2\big(t,X_t\big) \Big]\Delta t + \\ 
 &  \quad \ \frac{\partial{f}}{\partial x}\sigma\big(t,X_t\big) \Delta B_t + \frac{\partial^2f}{\partial x^2}\mu\big(t,X_t\big)\sigma\big(t,X_t\big) \Delta t \Delta B_t
\end{aligned}
$$
Let $\Delta t \rightarrow 0$ 
$$
Y_{t+ \Delta t} \approx Y_t + \Big\{ \frac{\partial{f}}{\partial t} + \frac{\partial{f}}{\partial x}\mu\big(t,X_t\big) + \frac{1}{2} \frac{\partial^2f}{\partial x^2}\sigma^2\big(t,X_t\big) \Big\}dt + \frac{\partial{f}}{\partial x}\sigma\big(t,X_t\big) d B_t \\
\Rightarrow dY_t =  \Big\{ \frac{\partial{f}}{\partial t} + \frac{\partial{f}}{\partial x}\mu\big(t,X_t\big) + \frac{1}{2} \frac{\partial^2f}{\partial x^2}\sigma^2\big(t,X_t\big) \Big\}dt + \frac{\partial{f}}{\partial x}\sigma\big(t,X_t\big) d B_t
$$

#### 4.4 Feyman-Kac Formula 

Suppose we want to compute $\mathbb{E} [u(X_T)]$ where
$$
dX_t = \mu(t,X_t)dt + \sigma(t,X_t)dB_t,\ X_0 = x
$$
Idea is steps: write a general class of similar problems of ours is one specific case. Base on the structure of all these problems, we will use the Markov property of $X_t$ to deduce that there is a function which solves each of these problems. Also based on the structure of all these problems, we will identify a stochastic process which is a Martingale. Apply Ito's lemma to said martingale, and we know it must have zero drift. This last step will end up providing a PDE which must be solved by the function in last step. 
Step 1: consider instead 
$$
\mathbb{E} \big[u(X_T)\big|\mathcal{F}_t\big],t \leq T
$$
Then our original problem is corresponding to $t=0$. 
Step 2: $X_t$ is Markovian, then there is a function $f$ such that 
$$
\mathbb{E} \big[u(X_T)\big|\mathcal{F}_t\big] = f(t,x_t)
$$
Step 3: Let $Y_t = f(t,X_t)$. Then $Y_t$ is a martingale. We need to show  
$$
\mathbb{E} \big[Y_s \big|\mathcal{F}_t\big] = Y_t
$$
$$
\begin{aligned}
\mathbb{E} \big[Y_s \big|\mathcal{F}_t \big] &= \mathbb{E} \Big[\mathbb{E}\big[u(X_T)\big|\mathcal{F}_s \big]\Big|\mathcal{F}_t\Big] \\
 & = \mathbb{E} \big[u(X_T)\big|\mathcal{F}_t\big]
 \end{aligned}
$$

Step 4: Apply Ito's Lemma to $Y_t = f(t,X_t)$
$$
dY_t =  \Big\{ \frac{\partial{f}}{\partial t} + \frac{\partial{f}}{\partial x}\mu\big(t,X_t\big) + \frac{1}{2} \frac{\partial^2f}{\partial x^2}\sigma^2\big(t,X_t\big) \Big\}dt + \frac{\partial{f}}{\partial x}\sigma\big(t,X_t\big) d B_t
$$
Step 5: The drift is 
$$
\frac{\partial{f}}{\partial t} + \frac{\partial{f}}{\partial x}\mu\big(t,X_t\big) + \frac{1}{2} \frac{\partial^2f}{\partial x^2}\sigma^2\big(t,X_t\big) = 0
$$
We also have terminal condition for $f$ given by step2
$$
f(T,X_T) = \mathbb{E} \big[u(X_T)\big|\mathcal{F}_T\big] = u(X_T)
$$
Then value of our original problem is $f(0,x)$

**General Feyman-Kac Formula**: 
Let 
$$
\begin{aligned}
f(t,X_t) &= \mathbb{E} \Big[ e^{-r(T-t)}u(X_T) + \int_{t}^{T}e^{-r(s-t)}g(s,X_s)ds\Big| \mathcal{F}_t\Big] \\
dX_t &= \mu(t,X_t)dt + \sigma(t,X_t)dB_t 
\end{aligned}
$$
Then $f$ satisfies a PDE with terminal conditions:
$$
\left\{
		\begin{array}\
				 \frac{\partial{f}}{\partial t} + \frac{\partial{f}}{\partial x}\mu + \frac{1}{2} \frac{\partial^2f}{\partial x^2}\sigma^2 + g = rf\\
				 f(T,x) = u(x)
				 
		\end{array}
\right.
$$

More meaning behind the Feyman-Kac Formula. We can compute $f(t,X_t)$ through Monte-Carlo simulations. With Markov property, we can generate $N$ paths from $t$ to $T$ $X^{(1)},\dots,X^{(N)}$. For each path, we compute 
$$
\phi^{(n)} =  e^{-r(T-t)}u(X_T) + \int_{t}^{T}e^{-r(s-t)}g(s,X_s)ds
$$
Then we compute
$$
\frac{1}{N} \sum^{N}_{n=1} \phi^{(n)}
$$
The results depends on the starting coordinates $(t_0,X_0)$. Different $(t_0,X_0)$ will give different $\frac{1}{N} \sum^{N}_{n=1} \phi^{(n)}$. That's what it means to be a function $f(t,x)$. 

Example of using Feyman-Kac to solve PDE. 
$$
\left\{
		\begin{array}\
				 \frac{\partial{V}}{\partial t} + \frac{\partial{V}}{\partial x}\mu x + \frac{1}{2} \frac{\partial^2 V}{\partial x^2}\sigma^2x^2 + x = rV\\
				 V(T,x) = x^2
		\end{array}
\right.
$$
Step 1) identify the appropriate dynamics for $X_t$: 
$$
dX_t = \mu X_t dt + \sigma X_t dB_t
$$
Step 2) Solve for $X_t$: 
$$
X_t = X_0 \exp \Big[\big(\mu-\frac{1}{2}\sigma^2\big)t + \sigma B_t\Big]
$$
Step 3) Evaluate the expectation. It will help to write $X_T$ and $X_s$ in terms of $X_t$. 
$$
X_T= X_t \exp \Big[\big(\mu-\frac{1}{2}\sigma^2\big)(T-t) + \sigma (B_T-B_t)\Big]\\
X_s= X_t \exp \Big[\big(\mu-\frac{1}{2}\sigma^2\big)(s-t) + \sigma (B_s-B_t)\Big]
$$

$$
\begin{aligned}
	V(t,X_t) &= \mathbb{E} \bigg[e^{-r(T-t)}X^2_T + \int^T_t e^{-r(s-t)}X_sds \bigg| \mathcal{F}_t\bigg] \\
	&= \mathbb{E}\Big[e^{-r(T-t)}X_T^2\Big| \mathcal{F}_t\Big] + \mathbb{E}\left[\int _t^Te^{-r(s-t)}X_sds\Big|\mathcal{F}_t\right]  \\
\end{aligned}
$$

In the second term, in most practical cases the expectation and the integral can be interchanged. 
$$
\mathbb{E}\left[\int _t^Te^{-r(s-t)}X_sds\Big|\mathcal{F}_t\right] = \int_t^T e^{-r(s-t)} \mathbb{E}\big[X_s \big| \mathcal{F}_t\big]ds \\
$$



### 5. Dynamic utility maximization in continuous time

Going back to the portfolio optimization we wanted to solve: 
$$
\begin{aligned}
W_t & = X_t + \theta_tP_t \\
W_{t+\Delta t} &= X_t(1+r\Delta t) + \theta_t P_{t+\Delta t}
\end{aligned}
$$

Take difference and a formal limit, we have
$$
\begin{aligned}
W_{t+\Delta t} -W_t &= rX_t \Delta t+ \theta_t(P_{t+\Delta t} - P_{t}) \\
dW_t &= rX_tdt + \theta_t dP_t
\end{aligned}
$$
eliminate $X_t$ using equation above:
$$
dW_t = rW_tdt - \theta_t P_t dt+ \theta_t dP_t
$$
We will use this as our definition of self-financing wealth dynamics. We have made no assumptions of the dynamics of the price $P_t$. Now we assume
$$
dP_t = \mu(t) P_tdt + \sigma(t) P_tdB_t
$$
This is essentially the geometric Brownian motion with time changing coefficients. Then
$$
\begin{aligned}
dW_t &= r W_tdt + \big(\mu(t) - r\big) \theta_t P_tdt + \sigma(t)\theta_tP_tdB_t \\
		 &= W_t \left[\left( r+(\mu(t)-r)\frac{\theta_t P_t}{W_t}\right)dt + \sigma(t) \frac{\theta_t P_t}{W_t}dB_t\right]
\end{aligned}
$$
Then
$$
\frac{dW_t}{W_t} = \left( r+(\mu(t)-r)\frac{\theta_t P_t}{W_t}\right)dt + \sigma(t) \frac{\theta_t P_t}{W_t}dB_t
$$
Let $\pi_t = \theta_t P_t/W_t$
$$
\frac{dW_t}{W_t} = \left( r+(\mu(t)-r)\pi_t\right)dt + \sigma(t) \pi_tdB_t
$$
Recall that:
$$
\begin{aligned}
\mathbb{E}\left[r_p\right] &= r+ \boldsymbol{\mu}_e^T \boldsymbol{\pi} \\
\mathbb{V} [r_p] &= \boldsymbol{\pi}^T \boldsymbol{\Omega} \boldsymbol{\pi}
\end{aligned}
$$
Our goal is to maximize expectation of utility of terminal wealth.  
$$
\sup_{\theta} \  \mathbb{E}\left[u(W_T)\right] \Leftrightarrow \sup_{\pi} \  \mathbb{E}\left[u(W_T)\right]
$$
The left hand side problem is easier because state space will be lower dimension.

How we maximize such an expression? 1) Derive the continuous time Dynamic Programming Principle. 2) Use the Dynamic Programming Principle to derive the Hamilton-Jacob-Bellman equation. This style of optimization is also called Merton Portfolio Optimization. 

Start with the dynamics that allow for controls
$$
dX_t^{\pi} = \mu(t,X_t^{\pi},\pi_t)dt + \sigma(t,X_t^{\pi},\pi_t) dB_t
$$
What is $\pi_t$ allowed to depend on? We will restrict our control such that it may only depend on the state of the system at the current time: 
$$
\pi_t = \pi(t,X_t^{\pi}) \\
\Longrightarrow dX_t^{\pi} = \mu(t,X_t^{\pi}, \pi(t,X_t^{\pi}))dt + \sigma(t,X_t^{\pi}, \pi(t,X_t^{\pi})) dB_t
$$
For any function $\pi$ of two variables, the resulting $X^{\pi}$ will have the Markov property. For this reason, we call $\pi(t,X_t^{\pi})$. For this reason, we will call $\pi(t,X_t^{\pi})$ a Markov control. 
We want to find the function $\pi$ which maximizes
$$
\mathbb{E} \big[ g(X_T^{\pi})\big]
$$
Strategy: embed our control problem in a large class of similar problems. For fixed $\pi$, let 
$$
\mathcal{J}^{\pi}(t,X_t) = \mathbb{E}\Big[g\left(X_T^{\pi}\right) \Big|\mathcal{F}_t\Big]
$$
Let 
$$
\mathcal{H}(t,X_t) = \sup_{\pi\in \mathcal{A}_{t,T}} \mathbb{E} \big[g(X_T^{\pi})\big|\mathcal{F}_t\big]
$$
Where 
$$
\mathcal{A}_{t,T} = \left\{\pi(\tau,x): t \leq \tau \leq T\right\}
$$
We call $\mathcal{J}^{\pi}$ the performance criteria, and $\mathcal{H}$ is the value function. Note: our original problem amounts to finding $\mathcal{H} (0,X_0)$. Also, $\mathcal{J}^{\pi}(t,x) \leq \mathcal{H}(t,x)$. Recall the law of iterated expectation (tower property).
$$
\mathbb{E} \Big[g(X_T^{\pi})\Big|\mathcal{F}_t\Big] = \mathbb{E} \bigg[\mathbb{E}\Big[g\big(X_T^{\pi}\big) \Big| \mathcal{F}_s\Big]\bigg|\mathcal{F_t}\bigg] , \ s \geq t \tag{*1} \\
$$

$$
\mathcal{J}^{\pi}(t,X_t) = \mathbb{E} \big[\mathcal{J}^{\pi}(s,X_s^{\pi})\big|\mathcal{F}_t\big] \leq \mathbb{E} \big[\mathcal{H}(s,X_s^{\pi})\big|\mathcal{F}_t\big]
$$

Then 
$$
\begin{aligned}
& \ \ \mathcal{J}^{\pi}(t,X_t) \leq \sup_{\pi\in \mathcal{A}_{t,s}} \mathbb{E} \big[\mathcal{H}(s,X_s^{\pi})\big|\mathcal{F}_t\big] \\
& \sup_{\pi\in \mathcal{A}_{t,T}}\mathcal{J}^{\pi}(t,X_t) \leq \sup_{\pi\in \mathcal{A}_{t,s}} \mathbb{E} \big[\mathcal{H}(s,X_s^{\pi})\big|\mathcal{F}_t\big] 
\end{aligned}
$$

$$
\mathcal{H}(t,X_t) \leq \sup_{\pi\in \mathcal{A}_{t,s}} \mathbb{E} \big[\mathcal{H}(s,X_s^{\pi})\big|\mathcal{F}_t\big] \tag{*2}
$$

Now return to (*1) 
$$
\mathbb{E} \Big[g(X_T^{\pi})\Big|\mathcal{F}_t\Big] = \mathbb{E} \bigg[\mathbb{E}\Big[g\big(X_T^{\pi}\big) \Big| \mathcal{F}_s\Big]\bigg|\mathcal{F_t}\bigg] , \ s \geq t \tag{*1} \\
$$
Let $\hat \pi$ be an $\varepsilon$-optimal control. 
$$
\mathcal{H}(t,x) \geq \mathcal{J}^{\hat \pi}(t,x) \geq \mathcal{H}(t,x) - \varepsilon
$$
Let $\pi$ be arbitrary control. Define  
$$
\widetilde{\pi_\tau} =
	\left\{
			\begin{array}\
				 \hat{\pi}_{\tau},\ \text{if} \ \tau \geq s \\
				 \pi_{\tau}, \text{if} \ \tau <s \\
				 
			\end{array}
	\right.
$$

$$
\begin{aligned}
&\mathbb{E} \Big[g(X_T^{\widetilde{\pi}})\Big|\mathcal{F}_t\Big] = \mathbb{E} \bigg[\mathbb{E}\Big[g\big(X_T^{\widetilde{\pi}}\big) \Big| \mathcal{F}_s\Big]\bigg|\mathcal{F_t}\bigg] , \ s \geq t \\
&\mathbb{E} \Big[g(X_T^{\widetilde{\pi}})\Big|\mathcal{F}_t\Big] = \mathbb{E} \left[\mathcal{J}^{\widetilde{\pi}}(s,X_s^{\widetilde{\pi}})|\mathcal{F}_t \right]\\
&\mathbb{E} \Big[g(X_T^{\widetilde{\pi}})\Big|\mathcal{F}_t\Big] = \mathbb{E} \left[\mathcal{J}^{\boxed{\hat{\pi}}}(s,X_s^{\boxed{\pi}})|\mathcal{F}_t \right]\\
\end{aligned}
$$

because $\mathcal{J}$ is only evaluated at time $s$. With the $\varepsilon $-optimal control,
$$
\begin{aligned}
	& \mathbb{E} \Big[g(X_T^{\widetilde{\pi}})\Big|\mathcal{F}_t\Big] \geq \mathbb{E}      \Big[\mathcal{H}(s,x_s^{\pi}) - \varepsilon|\mathcal{F}_t \Big] \\
	& \mathbb{E} \Big[g(X_T^{\widetilde{\pi}})\Big|\mathcal{F}_t\Big] \geq \mathbb{E}      \Big[\mathcal{H}(s,x_s^{\pi}) |\mathcal{F}_t \Big] - \varepsilon
\end{aligned}
$$
Maximize the l.h.s
$$
\sup_{\pi \in \mathcal{A}_{t,T}} \mathbb{E} \Big[g(X_T^{{\pi}}) \Big|\mathcal{F}_t\Big] \geq \mathbb{E}  \Big[\mathcal{H}(s,x_s^{\pi}) |\mathcal{F}_t \Big] - \varepsilon \\
\Longrightarrow \mathcal{H}(t,X_t) \geq \sup_{\pi \in \mathcal{A}_{t,T}} \mathbb{E}  \Big[\mathcal{H}(s,x_s^{\pi}) |\mathcal{F}_t \Big] - \varepsilon
$$
This holds for any positive constant $\varepsilon$. Then 
$$
\mathcal{H}(t,X_t) \geq \sup_{\pi \in \mathcal{A}_{t,T}} \mathbb{E}  \Big[\mathcal{H}(s,x_s^{\pi}) |\mathcal{F}_t \Big] \tag{*3}
$$
Put together (*3) and (\*2) to get
$$
\mathcal{H}(t,X_t) = \sup_{\pi \in \mathcal{A}_{t,T}} \mathbb{E}  \Big[\mathcal{H}(s,x_s^{\pi}) |\mathcal{F}_t \Big]
$$
This is the Dynamic Programming Principle in continuous time. Compare with the DPP in the discrete time:
$$
H(n,X_n) = \sup_{\pi_n} \  \mathbb{E} \big[H(n+1,X_{n+1}^{\pi_n})\big| \mathcal{F}_n\big]
$$
We need to develop further tools to make optimization step easier. To do this, let $\pi$ be any control and define process:
$$
\begin{aligned}
	& Y_t^{\pi} = \mathcal{H}(t,X_t^{\pi}) \\
	& dX_t^{\pi} = \mu(t,X_t^{\pi}, \pi(t,X_t^{\pi}))dt + \sigma(t,X_t^{\pi}, \pi(t,X_t^{\pi})) dB_t
\end{aligned}
$$
Apply Ito's Lemma to $Y_t^{\pi}$. 
$$
\begin{aligned}
	& dY_t^{\pi} = \underbrace{\Big[\frac{\partial \mathcal{H}}{\partial t} + \mu\frac{\partial \mathcal{H}}{\partial x} + \frac{1}{2}\sigma^2\frac{\partial^2 \mathcal{H}}{\partial x^2}\Big]}_{\mathcal{L}^{\pi}\mathcal{H}(t,X_t^{\pi})}dt + \sigma \frac{\partial \mathcal{H}}{\partial x} dB_t \\
& Y_s^{\pi} - Y_t^{\pi} = \int_t^{s} \mathcal{L}^{\pi}\mathcal{H}(u,X_u^{\pi})du + \int_t^{s} \sigma \frac{\partial \mathcal{H}}{\partial x} dB_t \\
\end{aligned}
$$

Take expectation conditioning on time $t$
$$
\begin{aligned}
&\mathbb{E} [Y_s^{\pi}|\mathcal{F}_t] - Y_t^{\pi}= \mathbb{E} \left[\int_t^s  \mathcal{L}^{\pi}\mathcal{H}(u,X_u^{\pi})du\bigg| \mathcal{F}_t\right] \\
&\mathbb{E} [Y_s^{\pi}|\mathcal{F}_t] = \mathcal{H}(t,X_t) + \mathbb{E} \left[\int_t^s  \mathcal{L}^{\pi}\mathcal{H}(u,X_u^{\pi})du\bigg| \mathcal{F}_t\right]
\end{aligned}
$$

With the DPP,we have the following inequality
$$
\begin{aligned}
0 & \geq \mathbb{E} \left[\int_t^s  \mathcal{L}^{\pi}\mathcal{H}(u,X_u^{\pi})du\bigg| \mathcal{F}_t\right] \\
0 & \geq \mathbb{E} \left[\frac{1}{s-t}\int_t^s  \mathcal{L}^{\pi}\mathcal{H}(u,X_u^{\pi})du\bigg| \mathcal{F}_t\right]
\end{aligned}
$$
Now let $s \rightarrow t$ from above. 
$$
\begin{aligned}
0 & \geq \mathbb{E} \left[ \mathcal{L}^{\pi}\mathcal{H}(t,X_t^{\pi})\bigg| \mathcal{F}_t\right] \\
0 & \geq  \mathcal{L}^{\pi}\mathcal{H}(t,X_t^{\pi}) 
\end{aligned}
$$
Then we have
$$
\frac{\partial \mathcal{H}}{\partial t} + 
\mu^{\pi}\frac{\partial \mathcal{H}}{\partial x} + \frac{1}{2}(\sigma^\pi)^2\frac{\partial^2 \mathcal{H}}{\partial x^2} \leq 0 \tag{*4}
$$
for any function $\pi $. Go through the above $\pi^{*}$ is optimal, then
$$
\frac{\partial \mathcal{H}}{\partial t} + 
\mu^{\pi}\frac{\partial \mathcal{H}}{\partial x} + \frac{1}{2}(\sigma^\pi)^2\frac{\partial^2 \mathcal{H}}{\partial x^2} = 0
$$
(*4) only depends on $\pi$ at $(t,x)$. So for fixed $(t,x)$ think of $\pi$ as a constant. Then we can write:
$$
\sup_{\pi_o} \left\{ \frac{\partial \mathcal{H}}{\partial t} + 
\mu(t,x,\pi_0)\frac{\partial \mathcal{H}}{\partial x} + \frac{1}{2}\sigma^2(t,x,\pi_0)\frac{\partial^2 \mathcal{H}}{\partial x^2} \right\} = 0
$$
This equation is called Hamilton-Jacob-Bellman equation. This is highly nonlinear PDE. Recall Feynman-Kac:
$$
\left\{
		\begin{array}\
				 \frac{\partial{V}}{\partial t} + \frac{\partial{V}}{\partial x}\mu + \frac{1}{2} \frac{\partial^2V}{\partial x^2}\sigma^2 + f(x) = rV\\
				 V(T,x) = g(x)
		\end{array}
\right.
$$

$$
V(t,X_t) = \mathbb{E}\left[e^{-\int_t^Trdu}g(x_T) + \int_t^Te^{-\int_t^srdu}f(x_s)ds \bigg|\mathcal{F}_t\right]
$$

The HJB:
$$
\begin{aligned}
		\sup_{\pi_o} \left\{ \frac{\partial \mathcal{H}}{\partial t} + 
	  \mu^{\pi}\frac{\partial \mathcal{H}}{\partial x} + \frac{1}	 			 
	  {2}(\sigma^\pi)^2\frac{\partial^2 \mathcal{H}}{\partial x^2}+f^{\pi}(x)-r^{\pi}\mathcal{H} \right\} &= 0 \\
	  H(T,x) &= g(x)
\end{aligned}
$$

$$
H(t,x_t) = \sup_\pi \mathbb{E}\left[e^{-\int_t^Tr^{\pi}du}g(x^{\pi}_T) + \int_t^Te^{-\int_t^sr^{\pi}du}f(x^{\pi}_s)ds \bigg|\mathcal{F}_t\right]
$$

**Examples of application of H.J.B equation: **

$\boxed {\text{Example 1}}$: Let
$$
\begin{aligned}
	& dX_t^{\pi} = (\mu + \pi_t)dt + \sigma\pi_tdB_t \\
	& \sup_{\pi} \mathbb{E} \left[X_T^{\pi} -\frac{\gamma}{2}(X_T^{\pi})^2\right]
\end{aligned}
$$
Define value function:
$$
H(t,X_t) = \sup_{\pi} \mathbb{E} \left[X_T^{\pi} -\frac{\gamma}{2}(X_T^{\pi})^2\Big|\mathcal{F}_t\right] 
$$
We know from previous work that there is a PDE which $H$ must satisfy. The H-J-B:
$$
\begin{aligned}
\sup_{\pi}\left\{\frac{\partial H}{\partial t}+(\mu + \pi)\frac{\partial H}{\partial x} + \frac{1}{2}\sigma^2\pi^2\frac{\partial^2H}{\partial x^2}\right\} &= 0 \\
H(T,x) &= x- \frac{\gamma}{2}x^2
\end{aligned}
$$
We will go through my original thought process on how to solve this, including dead ends and mistakes. First thing to always do with H-J-B is find $\pi^{*}$. Take derivative w.r.t $\pi$:
$$
\partial_{\pi}: \frac{\partial H}{\partial \pi} + \sigma^2\pi \frac{\partial^2 H}{\partial x^2} = 0
$$

$$
\pi^{*} = \frac{1}{\sigma^2}\frac{-\partial H/\partial x}{\partial^2H/\partial x^2}
$$

Note that we need to verify that $ \frac{\partial^2H}{\partial x^2} <0$. Resubstitute $\pi^{*} $ into the H-J-B equation:
$$
\begin{aligned}
\frac{\partial H}{\partial t} + \mu \frac{\partial H}{\partial x} - \frac{1}{2\sigma^2}\frac{(\partial H/\partial x)^2}{\partial^2H/\partial x^2} &= 0 \\
H(T,x) & = x - \frac{\gamma}{2}x^2
\end{aligned}
$$
Guess: 
$$
H(t,x) = f(t)g(x)
$$
Then we have 
$$
H(T,x) = f(T)g(x) = x- \frac{\gamma}{2}x^2 \\
\Rightarrow f(T) = 1, \ g(x) =  x- \frac{\gamma}{2}x^2
$$

$$
\Rightarrow
	\begin{aligned}
		&\frac{\partial H}{\partial t} = f'(t)\left(x- \frac{\gamma}{2}x^2\right) \\
		&\frac{\partial H}{\partial x} = f(t)(1- \gamma x) \\ 
		& \frac{\partial^2H}{\partial x^2} = -\gamma f(t)
	\end{aligned}
$$

Substitute the above expressions into PDE 
$$
f'(t)\left(x-\frac{\gamma}{2}x^2\right) + \mu f(t)(1-\gamma x) + \frac{1}{2 \sigma^2}\frac{f(t)(1-\gamma x)^2}{\gamma} = 0
$$
But we cannot have the above to be true for all $x$. Thus the initial guess is incorrect form. Suppose
$$
H(t,x) = f(t) + h(t)g(x)
$$
Substitute this into the terminal condition:
$$
\begin{aligned}
	& f(T) + h(T)g(x) = x- \frac{\gamma}{2}x^2 \\
	& \Rightarrow f(T) = 0,\ h(T) = 1, g(x) = x- \frac{\gamma}{2}x^2
\end{aligned}
$$

$$
\left.
	\begin{aligned}
		\frac{\partial H}{\partial t} = f' + h'g \\
		\frac{\partial H}{\partial x} = h(1-\gamma x) \\
		\frac{\partial^2 H}{\partial x^2} = -\gamma h
	\end{aligned}
\right\}
$$

Substitute into PDE:
$$
f' + h'\left(x- \frac{\gamma}{2}x^2\right) + \mu h (1-\gamma x)+ \frac{1}{2 \sigma^2} \frac{h(1-\gamma x)^2}{\gamma} = 0
$$

$$
\left(f' + \mu h + \frac{1}{2\sigma^2 \gamma} h\right) + \left(h' - \mu \gamma h - \frac{1}{\sigma^2}h\right)x + \left(-\frac{\gamma}{2}h'+\frac{\gamma}{2\sigma^2}h\right)x^2 = 0
$$

As we want this holds for all value of $x$, the three terms in the parenthesis must be $0 $ independently. But the second and the third give two different ODEs. There is no single function $h$ which make both of these zero simultaneously. Then the second guess is incorrect. Next guess:  
$$
\begin{aligned}
	& H(t,x) = f_0(t) + f_1(t)x + f_2(t)x^2 \\
	& f_0(T) + f_1(T)x + f_2(T)x^2 = x - \frac{\gamma}{2} x^2 \\
	& \Rightarrow f_0(T) = 0, \ f_1(T) = 1, \ f_2(T) = -\frac{\gamma}{2}
\end{aligned}
$$

$$
\left.
	\begin{aligned}
		\frac{\partial H}{\partial t} = f_0' + f_1'x + f'_2x^2 \\
		\frac{\partial H}{\partial x} = f_1+ 2 f_2 x \\
		\frac{\partial^2 H}{\partial x^2} = 2f_2
	\end{aligned}
\right\}
$$

Substitute these into PDE:
$$
f_0' + f_1'x + f'_2x^2  + \mu( f_1+ 2 f_2 x) - \frac{1}{2\sigma^2}\frac{(f_1+ 2 f_2 x)^2}{2f_2} = 0
$$

$$
\left(f_0' +\mu f_1 - \frac{f_1^2}{4\sigma^2 f_2} \right) + \left(f_1'+ 2\mu f_2 - \frac{f_1}{\sigma^2}\right)x + \left( f_2' - \frac{f_2}{\sigma^2}\right)x^2 = 0
$$

Set all these terms to zero simultaneously, this will give a system of three ODEs. 
$$
\left\{
	\begin{aligned}
		& f_0' +\mu f_1 - \frac{f_1^2}{4\sigma^2 f_2} = 0 \\
		& f_1'+ 2\mu f_2 - \frac{f_1}{\sigma^2} =0 \\
		& f_2' - \frac{f_2}{\sigma^2} = 0
	\end{aligned}
\right.
$$
