#### Here's how the flow from a healthy state to death works:
|  0    | p_stay|   0   |p_adverse1|p_adverse2|p_death|
|-------|-------|-------|-------|-------|-------|
|  0    |0.87 - (0.05 * 2)|  0   |0.05 * 3|0.05|0.03|
|  0    |   0   |0.82 - (0.08 + 0.07)|0.08 * 2|0.07 * 2|0.03|
|  0    |  0.9  |   0   |   0.1   |   0   |   0   |
|  0    |  0.7  |   0   |   0   |  0.3  |   0   |
|  0    |   0   |   0   |   0   |   0   |   1   |


The person begins in a healthy state, which is represented in the first row of the matrix. They have some chance of staying healthy and not experiencing any adverse events, which is given by the probability p_stay. This means there's a certain likelihood that they will remain healthy in the next time period.

#### However, there are also other possibilities:
They may experience adverse events (such as illness or injury) with probabilities p_adverse1 and p_adverse2, which could move them to other states that represent worsening health conditions.
There's a small chance of death, represented by the probability p_death. If this happens, the person's journey ends in death.
The probabilities in the first row of the matrix show how these different possibilities affect the person's health over time. The value in the "death" column of the first row represents the probability of transitioning from a healthy state to death in the next time period.

In the context of the transition matrices, each column represents the potential next health state or condition that a person can transition to from their current state. Each element within a column represents the probability of making that specific transition.

**Column 1:** This column represents the probability of transitioning to the same health state or staying in the current state. It indicates the likelihood of remaining in the current condition without any changes.

**Column 2:** This column represents the probability of transitioning to a specific health state associated with adverse event 1 (p_adverse1). It indicates the likelihood of moving to a different state due to the occurrence of adverse event 1.

**Column 3:** This column represents the probability of transitioning to a specific health state associated with adverse event 2 (p_adverse2). It indicates the likelihood of moving to a different state due to the occurrence of adverse event 2.

**Column 4:** This column represents the probability of transitioning to a specific health state associated with disease progression. In this scenario, it is used for transitions other than adverse events and death.

**Column 5:** This column represents the probability of transitioning to a specific health state associated with a fatal event or death (p_death). It indicates the likelihood of moving from the current state to the state of death, which is a terminal state in this model.

**Column 6:** This column is used as a terminal state, where a person's health journey ends.
