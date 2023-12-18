# Analysis of the performance of the Monte Carlo Simulation of Markov Chain
## Single threaded execution
As a benchmark for the parallel execution I ran the simulation code without passing it into concurrent futures or with any batching. As you can see from the image below the single threaded performance is rather linear on my 32 core AMD Epyc 7551P with 192Gb DDR4 up to 25,000 itterations I didn't go any futher than this as I only wanted something to compare the multi-threaded performance to.  

<p align="center">
<img width=50% alt="Single Threaded" src="https://github.com/chriswilson2020/MonteCarloMarkov/blob/09ee354dfcbfbef9774a99eb4e287c59b41fa3d9/images/Single%20Threaded%20Performance.png"><br>
<em>Plot of single threaded performance of the Monte Carlo Markov Chain Simulation</em><br>
<em>Tabulated Data of Single Threaded Performance</em>
|**Simulations**|**Wall Time 1**|**Wall Time 2**|**Wall Time 3**|**Average Wall Time**|
|---|---|---|---|---|
|5000|9.6885|9.6359|9.6588|9.66|
|10000|19.0933|19.181|19.2397|19.17|
|15000|28.751|28.5117|28.8839|28.72|
|20000|38.2594|38.3063|38.1841|38.25|
|25000|48.2842|47.3016|47.7972|47.79|
</p>
