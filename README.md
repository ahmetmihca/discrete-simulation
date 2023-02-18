# Discrete Event Simulation 

Project aims to apply data mining techniques to improve decision-making in a dynamic job-shop manufacturing environment. This will be done by creating a simulation model of the job shop in Python, generating data from the simulation, and using feature selection to identify important job and shop characteristics. A decision tree will then be created to develop rules for assigning due dates to jobs. The efficacy of the resulting due dates will be evaluated through computational experiments with different dispatching rules and shop utilization levels.


![image](https://user-images.githubusercontent.com/58208924/219903381-219df088-aadb-4f84-a6d7-eb65aa15af0a.png)

![image](https://user-images.githubusercontent.com/58208924/219903393-239f1a03-1f00-467f-9df4-9a88714368fa.png)

### Features of Train Set
    "Type","SRT4","WIP","k"

### Target of Train Set
    “k”

### Hyperparameters of Decision Tree
    DecisionTreeClassifier(min_samples_leaf=50, max_depth=10,max_leaf_nodes=10)
    
### Visualization of Decision Tree   
![image](https://user-images.githubusercontent.com/58208924/219903788-4f401d28-80f5-435a-89d5-a62318f3ffc5.png)

### Train Accuracy Score: 0.62

## Rules of Decision Tree

    |--- SRT4 <= 9.50
    |   |--- SRT4 <= 6.50
    |   |   |--- class: A
    |   |--- SRT4 >  6.50
    |   |   |--- Type <= 3.50
    |   |   |   |--- class: B
    |   |   |--- Type >  3.50
    |   |   |   |--- class: A
    |--- SRT4 >  9.50
    |   |--- SRT4 <= 17.50
    |   |   |--- SRT4 <= 12.50
    |   |   |   |--- class: B
    |   |   |--- SRT4 >  12.50
    |   |   |   |--- Type <= 3.50
    |   |   |   |   |--- class: C
    |   |   |   |--- Type >  3.50
    |   |   |   |   |--- class: B
    |   |--- SRT4 >  17.50
    |   |   |--- SRT4 <= 28.50
    |   |   |   |--- SRT4 <= 22.50
    |   |   |   |   |--- class: C
    |   |   |   |--- SRT4 >  22.50
    |   |   |   |   |--- class: D
    |   |   |--- SRT4 >  28.50
    |   |   |   |--- SRT4 <= 35.50
    |   |   |   |   |--- class: E
    |   |   |   |--- SRT4 >  35.50
    |   |   |   |   |--- class: F

## Rules in Human Readable From with Confidences 

* if (SRT4 <= 9.5) and (SRT4 <= 6.5) then class: A (proba: 84.88%) | based on 24,062 samples
* if (SRT4 > 9.5) and (SRT4 <= 17.5) and (SRT4 <= 12.5) then class: B (proba: 60.99%) | based on 16,786 samples
* if (SRT4 > 9.5) and (SRT4 <= 17.5) and (SRT4 > 12.5) and (Type <= 3.5) then class: C (proba: 44.31%) | based on 13,593 samples
* if (SRT4 > 9.5) and (SRT4 > 17.5) and (SRT4 <= 28.5) and (SRT4 <= 22.5) then class: C (proba: 52.3%) | based on 11,104 samples
* if (SRT4 <= 9.5) and (SRT4 > 6.5) and (Type <= 3.5) then class: B (proba: 47.15%) | based on 10,968 samples
* if (SRT4 > 9.5) and (SRT4 > 17.5) and (SRT4 <= 28.5) and (SRT4 > 22.5) then class: D (proba: 49.21%) | based on 7,641 samples
* if (SRT4 > 9.5) and (SRT4 > 17.5) and (SRT4 > 28.5) and (SRT4 <= 35.5) then class: E (proba: 45.05%) | based on 4,528 samples
* if (SRT4 > 9.5) and (SRT4 <= 17.5) and (SRT4 > 12.5) and (Type > 3.5) then class: B (proba: 71.58%) | based on 4,500 samples
* if (SRT4 <= 9.5) and (SRT4 > 6.5) and (Type > 3.5) then class: A (proba: 75.38%) | based on 3,655 samples
* if (SRT4 > 9.5) and (SRT4 > 17.5) and (SRT4 > 28.5) and (SRT4 > 35.5) then class: F (proba: 83.21%) | based on 3,163 samples

## Average k values in Prediction

- A: 1.5540089009052753
- B: 2.5209883170150995
- C: 3.5495000056873023
- D: 4.583997017104734
- E: 5.624066692991111
- F: 7.398589033376673



## Performance Metrics
* MAL: 1.76496988
* MSL: 311511.868

