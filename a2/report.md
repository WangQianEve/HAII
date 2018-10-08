# Report

qianwan2

##### Smoothing

I used savgol_filter from scipy to smooth my gesture set.

### (i) shape matching approach and performance

#### Method

- I first use a 6-d vector to represent each gesture case. The 6 dimensions are DTW distance of the two cases’ Accelerometer’s x,y,z and Gyroscope’s x,y,z.

- Then I define the distance of two gesture cases as the norm of this 6-d vector
- For each test case, I simply calculate all the distance between it and all training cases, and find the nearest, use its gesture as the recognition result

#### Performance

##### Jon’s Dataset - Shape Matching

###### Confusion matrix

```
[[2 1 0 0 2 0 0 0 0 0]
 [0 5 0 0 0 0 0 0 0 0]
 [0 0 5 0 0 0 0 0 0 0]
 [0 0 0 5 0 0 0 0 0 0]
 [0 0 0 0 5 0 0 0 0 0]
 [0 0 0 0 0 5 0 0 0 0]
 [0 0 0 0 0 0 5 0 0 0]
 [0 0 0 0 0 0 0 5 0 0]
 [0 0 0 0 0 0 0 0 5 0]
 [0 0 0 0 0 0 0 0 0 5]]
```

###### Accuracy

0.94

###### Per gesture accuracy

```
                            precision    recall  f1-score   support

                   At Rest     1.0000    0.4000    0.5714         5
           Backhand Tennis     0.8333    1.0000    0.9091         5
            Baseball Throw     1.0000    1.0000    1.0000         5
           Forehand Tennis     1.0000    1.0000    1.0000         5
        Midair Clockwise O     0.7143    1.0000    0.8333         5
Midair Counter Clockwise O     1.0000    1.0000    1.0000         5
                  Midair S     1.0000    1.0000    1.0000         5
            Midair Zorro Z     1.0000    1.0000    1.0000         5
                     Shake     1.0000    1.0000    1.0000         5
         Underhand Bowling     1.0000    1.0000    1.0000         5

               avg / total     0.9548    0.9400    0.9314        50
```

##### Jon’s Dataset - Model

###### Confusion matrix

```
[[5 0 0 0 0 0 0 0 0 0]
 [0 4 0 1 0 0 0 0 0 0]
 [0 0 3 0 0 1 1 0 0 0]
 [0 1 0 4 0 0 0 0 0 0]
 [0 0 0 0 4 0 1 0 0 0]
 [0 0 0 0 0 5 0 0 0 0]
 [0 1 0 0 0 1 3 0 0 0]
 [0 0 0 0 0 0 0 5 0 0]
 [0 1 0 0 0 0 0 1 3 0]
 [0 0 0 0 0 0 0 1 0 4]]
```

###### Accuracy

0.8

###### Per gesture accuracy

```
                           precision    recall  f1-score   support

                   At Rest     1.0000    1.0000    1.0000         5
           Backhand Tennis     0.5714    0.8000    0.6667         5
            Baseball Throw     1.0000    0.6000    0.7500         5
           Forehand Tennis     0.8000    0.8000    0.8000         5
        Midair Clockwise O     1.0000    0.8000    0.8889         5
Midair Counter Clockwise O     0.7143    1.0000    0.8333         5
                  Midair S     0.6000    0.6000    0.6000         5
            Midair Zorro Z     0.7143    1.0000    0.8333         5
                     Shake     1.0000    0.6000    0.7500         5
         Underhand Bowling     1.0000    0.8000    0.8889         5

               avg / total     0.8400    0.8000    0.8011        50
```

##### My Dataset - Shape Matching

###### Confusion matrix

```
[[5 0 0 0 0 0 0 0 0 0 0]
 [0 3 0 2 0 0 0 0 0 0 0]
 [0 0 5 0 0 0 0 0 0 0 0]
 [0 2 0 2 0 1 0 0 0 0 0]
 [0 0 0 0 2 2 0 1 0 0 0]
 [0 0 0 0 1 4 0 0 0 0 0]
 [0 0 0 0 1 0 2 2 0 0 0]
 [0 0 0 0 1 0 2 2 0 0 0]
 [0 0 0 0 0 0 0 0 5 0 0]
 [0 0 0 0 0 0 0 0 0 5 0]
 [0 0 0 0 0 0 0 0 0 0 5]]
```

###### Accuracy

0.73

###### Per gesture accuracy

```
                            precision    recall  f1-score   support

                   At Rest     1.0000    1.0000    1.0000         5
           Backhand Tennis     0.6000    0.6000    0.6000         5
            Baseball Throw     1.0000    1.0000    1.0000         5
           Forehand Tennis     0.5000    0.4000    0.4444         5
        Midair Clockwise O     0.4000    0.4000    0.4000         5
Midair Counter Clockwise O     0.5714    0.8000    0.6667         5
                  Midair S     0.5000    0.4000    0.4444         5
            Midair Zorro Z     0.4000    0.4000    0.4000         5
                     Shake     1.0000    1.0000    1.0000         5
         Underhand Bowling     1.0000    1.0000    1.0000         5
       Your Custom Gesture     1.0000    1.0000    1.0000         5

               avg / total     0.7247    0.7273    0.7232        55
```

##### My Dataset - Model

###### Confusion matrix

```
[[4 1 0 0 0 0 0 0 0 0 0]
 [0 3 0 1 1 0 0 0 0 0 0]
 [0 1 4 0 0 0 0 0 0 0 0]
 [0 2 0 2 0 1 0 0 0 0 0]
 [0 1 0 0 1 2 0 1 0 0 0]
 [0 0 0 0 2 3 0 0 0 0 0]
 [1 0 0 0 1 0 2 1 0 0 0]
 [0 0 0 0 1 0 1 3 0 0 0]
 [0 0 0 0 0 0 0 0 5 0 0]
 [1 0 0 0 0 0 0 0 0 4 0]
 [1 1 1 0 0 0 0 0 0 0 2]]
```

###### Accuracy

0.6

###### Per gesture accuracy

```
                            precision    recall  f1-score   support

                   At Rest     0.5714    0.8000    0.6667         5
           Backhand Tennis     0.3333    0.6000    0.4286         5
            Baseball Throw     0.8000    0.8000    0.8000         5
           Forehand Tennis     0.6667    0.4000    0.5000         5
        Midair Clockwise O     0.1667    0.2000    0.1818         5
Midair Counter Clockwise O     0.5000    0.6000    0.5455         5
                  Midair S     0.6667    0.4000    0.5000         5
            Midair Zorro Z     0.6000    0.6000    0.6000         5
                     Shake     1.0000    1.0000    1.0000         5
         Underhand Bowling     1.0000    0.8000    0.8889         5
       Your Custom Gesture     1.0000    0.4000    0.5714         5

               avg / total     0.6641    0.6000    0.6075        55
```



### (ii) model-based classification approach and performance

##### Method

- I used ts-fresh on the dataset to extract all the possible features it provides, then rule out those contains NaN, log the features in “features.json”.
- I used the DecisionTreeClassifier.

##### Performance



### (iii) an enumeration of key challenges; 

- Lack of knowledge for signal processing, which show in:
  - Visualization: I don’t know how to adjust the parameters when there’s error.
  - Extracting features: I have no idea what features to extract.
- I didn’t know there’s a notebook providing some scaffolds, so I hard coded everything, which was exhausting for me.

### (iv) a reflection of what you learned. 

- I learned about DTW, what was very interesting. And using it on gesture recognition seems good.
- I learned about ts-fresh (a feature extraction tool for time-series) and its limit (only support binary classification if you wan’t to select relevant features).
- Although I know about machine learning theories, this is the first time I encounter time series. DTW is exciting.