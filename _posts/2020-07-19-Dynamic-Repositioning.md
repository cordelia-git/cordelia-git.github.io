

> Li, Yexin, Yu Zheng, and Qiang Yang. "Dynamic bike reposition: A spatio-temporal reinforcement learning approach." Proceedings of the 24th ACM SIGKDD International Conference on Knowledge Discovery & Data Mining. 2018.

### Target : minimizing the customer loss

- a user can rent or return a bike at a random station
- as the bike usage in a city is very unbalanced -> empty stations without bikes | lacking available docks -> customer loss
- how to efficiently repositioning to minimize the customer loss in a long period.

#### 3 Challenges 

1. daiy rent pattern fluctuates largely, being impacted by multiple complex factors (external factors)
    - (to do) daily rent pattern mining (e.g. hour, weekdays)
    - (to do) impact factor analysis (e.g. weather, events, correlation between stations) 
2. long-term effects of single bike resposition 
3. uncertainties in practical reposition : model error and random noise, severe weather condition, traffic congestion..

### 1. Clustring algorithm 

- Inter-dependent inner-balance clustering algorithm -> cluster stations into groups
    - 2-step clustering algorithm
    - each cluster is inner-balanced and independent from the others.
    
        1. individual station -> regions : more stable rent demand and transition patterns at each region 
        2. regions -> groups : based on the inter-region transition -> each cluster is inner-balances and independext form the others
    - dividing the entire system into clusters -> largely reduce the problem complexity
        

### 2. System simulators 

- System simulator based on two predictors -> to train and evaluate the reposition model
    - O-Model : to predict the rent demand at each region by a similarity-based KNN method
    - I-Model : to predict the return demand at each region by a transition-based inference method
    - (to do) convLSTM modeling for rent and return demand predict
    - (to do) research other demand predict model (for bike sharing) 
    

### 3. Spatio-temporal reinforcement learning model

- Spatio-temporal reinforcement learning model -> to learn optimal inner-cluster reposition policy
    - targeting at minimizing its customer loss in a long period
    - designing a deep neural network to estimate its optimal long-term value function
    - state of STRL : designed to capture the system dynamics and real-time uncertainties
    - very large state and action spaces -> DNN -> to estimate the optimal long-term value function for each STRL
    
    
(TDB..)
