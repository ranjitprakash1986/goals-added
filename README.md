# Soccer analytics metrics using meta-metrics: Discrimination and Stability

## Soccer analytics

Just like any major sport, soccer is replete with statistics. Unlike games such as NFL, NHL or cricket, soccer is a fluid game with momentary stoppages in the flow. The game result is decided by a scoreline of goals and teams often go in long spells goal-less period. A vast majority of the games yield a total of less than 3 goals. Thus it becomes a challenge to evaluate the game performance of players when there are very few visibly decisive moments in the game. Player performance evaluation is thus largely based on his/her on-ball moments. These include metrics such as pass completion percentage, shots on target, header won, tackle completion percentage and so on. Some of these metrics are aggregated to assess the performance of the team, while others such as expected goals are popular in the media to indicate the attacking intent of the team during the course of the game. How do we determine whether a metric is good or bad - i.e. does the metric reflect the true performance levels of the players/team. How can we assess this? 

## Meta-metrics

Meta-metrics are aimed to assess the quality of an evaluation metric. They can be useful in the process of constructing new metrics by enabling us to refine the evaluation metric. Two such meta metrics that I found insightful are Discrimination and Stability. These are discussed in depth in the paper "Meta-Analytics: Tools for Understanding the Statistical properties of Sports Metrics" by Alexander Franks et. al.

I will briefly describe these two meta metrics and delve into their application on data collected on Major League Soccer. The meta-metrics in this article are written with respect to assessing evaluation metrics for players.

### Discrimination

Discrimination is an indicator of how effective is the evaluation metric in differentiating between the players in a specific season. The discrimination value indicates the fraction of between-player variance in the evaluation metric `m` that can be attributed to the player's ability.


$$D_{sm} = 1 - \frac{E[V_{spm}[X]]}{V_{sm}[X]}$$

where,

$m$: evaluation metric

$s$: season

$E[V_{spm}[X]]$: expected value (mean) of the metric variance (sample) of each player in that season.

$V_{sm}$: metric variance (sample) in that season.

If we have several season to evaluate, the overall discrimination score  can be compute by taking the mean.

$$D_{m} = E_m[D_{sm}]$$ 

The Discrimination score ranges from 0 to 1, where a higher score indicates that the players can be differentiated from each based on the evaluation metric.


#### Example

Let's explain the Discrimination formula using a toy example


### Stability

Stability is an indicator of how consistent is the evaluation metric across the seasons. An evaluation metric can be unstable if it is highly dependent on context or confounding factors. For example, player performance fluctuating due to change in teammates from season to season, player performance drop due to injuries. Thus without the blocking of these confounding factors the evaluation metric cannot reliably provide a true indication of the player ability. The stability score is low for such evaluation metrics. With several confounding factors present in a soccer game such as the aforementioned teammates', injury, home/away games, weather conditions, etc. it can be challenging to design evaluation metrics that can be stable.

Stability is computed using the following formula. The formula returns a score between 0 and 1, where a higher score reflects the evaluation metric being more stable, and vice versa.

$$ S_m = 1 - \frac{E_m[V_{pm}[X]-V_{spm}[X]]}{V_{m}[X]-E_m[V_{spm}[X]]} $$

where,

$V_m[X]$ represents the total variance of the metric (sample).

$V_{pm}[X]$ represents the between-season variance of the metric (sample).

$V_{spm}[X]$ represents variance of the metric (sample) of each player in each season.


#### Example

Let's explain the Stability formula using a toy example

## American Soccer Analytics

## Meta metrics on MLS data


### Inference

### Limitations

### Recommendations

## References
github repository, itscalledsoccer: https://github.com/American-Soccer-Analysis/itscalledsoccer/tree/main

api page: https://app.americansocceranalysis.com/api/v1/__docs__/#/
