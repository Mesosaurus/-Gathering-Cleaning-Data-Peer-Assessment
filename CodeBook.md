#### Gathering & Cleaning Data_PeerAssessment - Codebook
##### This codebook contains information about the variables listed in the "Merged_table_avg_final" dataset.

###### Background

The features (variables) selected for this database come from the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ. These time domain signals (prefix 't' to denote time) were captured at a constant rate of 50 Hz. Then they were filtered using a median filter and a 3rd order low pass Butterworth filter with a corner frequency of 20 Hz to remove noise. Similarly, the acceleration signal was then separated into body and gravity acceleration signals (tBodyAcc-XYZ and tGravityAcc-XYZ) using another low pass Butterworth filter with a corner frequency of 0.3 Hz. 

Subsequently, the body linear acceleration and angular velocity were derived in time to obtain Jerk signals (tBodyAccJerk-XYZ and tBodyGyroJerk-XYZ). Also the magnitude of these three-dimensional signals were calculated using the Euclidean norm (tBodyAccMag, tGravityAccMag, tBodyAccJerkMag, tBodyGyroMag, tBodyGyroJerkMag). 

Finally a Fast Fourier Transform (FFT) was applied to some of these signals producing fBodyAcc-XYZ, fBodyAccJerk-XYZ, fBodyGyro-XYZ, fBodyAccJerkMag, fBodyGyroMag, fBodyGyroJerkMag. (Note the 'f' to indicate frequency domain signals). 

These signals were used to estimate variables of the feature vector for each pattern:  
'-XYZ' is used to denote 3-axial signals in the X, Y and Z directions.

The set of variables that were estimated from these signals and included in the dataset are: 
mean(): Mean value
std(): Standard deviation

Additional vectors obtained by averaging the signals in a signal window sample. These are used on the angle() variable:
gravityMean
tBodyAccMean
tBodyAccJerkMean
tBodyGyroMean
tBodyGyroJerkMean

As stated in the README.md file, an independent tidy data set was created that contains the average of each variable for each activity and each subject. There are 180 subject-activity pairs in total and 88 variables, which are listed in the table below along with their units.


ID  |   Variables                                   |   Units                                       |   
--- |   ------------------------------------------  |   --------------------------------------      |    
1   |   Activity                                    |   N/A                                         | 
2   |   Subject                                     |   N/A                                         |
3   |   tBodyAcc.mean...X                           |   standard gravity units "g", i.e. m/s^2      |
4   |   tBodyAcc.mean...Y                           |   standard gravity units "g", i.e. m/s^2      |
5   |   tBodyAcc.mean...Z                           |   standard gravity units "g", i.e. m/s^2      |
6   |   tGravityAcc.mean...X                        |   standard gravity units "g", i.e. m/s^2      |
7   |   tGravityAcc.mean...Y                        |   standard gravity units "g", i.e. m/s^2      |
8   |   tGravityAcc.mean...Z                        |   standard gravity units "g", i.e. m/s^2      |
9   |   tBodyAccJerk.mean...X                       |   standard gravity units "g", i.e. m/s^2      |
10  |   tBodyAccJerk.mean...Y                       |   standard gravity units "g", i.e. m/s^2      |
11  |   tBodyAccJerk.mean...Z                       |   standard gravity units "g", i.e. m/s^2      |
12  |   tBodyGyro.mean...X                          |   radians/second                              |
13  |   tBodyGyro.mean...Y                          |   radians/second                              |
14  |   tBodyGyro.mean...Z                          |   radians/second                              |
15  |   tBodyGyroJerk.mean...X                      |   radians/second                              |
16  |   tBodyGyroJerk.mean...Y                      |   radians/second                              |
17  |   tBodyGyroJerk.mean...Z                      |   radians/second                              |
18  |   tBodyAccMag.mean..                          |   standard gravity units "g", i.e. m/s^2      |
19  |   tGravityAccMag.mean..                       |   standard gravity units "g", i.e. m/s^2      |
20  |   tBodyAccJerkMag.mean..                      |   standard gravity units "g", i.e. m/s^2      |
21  |   tBodyGyroMag.mean..                         |   standard gravity units "g", i.e. m/s^2      |
22  |   tBodyGyroJerkMag.mean..                     |   standard gravity units "g", i.e. m/s^2      |
23  |   fBodyAcc.mean...X                           |   Hz                                          |
24  |   fBodyAcc.mean...Y                           |   Hz                                          |
25  |   fBodyAcc.mean...Z                           |   Hz                                          |
26  |   fBodyAcc.meanFreq...X                       |   Hz                                          |
27  |   fBodyAcc.meanFreq...Y                       |   Hz                                          |
28  |   fBodyAccJerk.mean...X                       |   Hz                                          |
29  |   fBodyAccJerk.mean...                        |   Hz                                          |
30  |   fBodyAcc.meanFreq...Z                       |   Hz                                          |
31  |   fBodyAccJerk.mean...Z                       |   Hz                                          |
32  |   fBodyAccJerk.meanFreq...X                   |   Hz                                          |
33  |   fBodyAccJerk.meanFreq...Y                   |   Hz                                          |
34  |   fBodyAccJerk.meanFreq...Z                   |   Hz                                          |
35  |   fBodyGyro.mean...X                          |   Hz                                          |
36  |   fBodyGyro.mean...Y                          |   Hz                                          |
37  |   fBodyGyro.mean...Z                          |   Hz                                          |
38  |   fBodyGyro.meanFreq...X                      |   Hz                                          |
39  |   fBodyGyro.meanFreq...Y                      |   Hz                                          |
40  |   fBodyGyro.meanFreq...Z                      |   Hz                                          |
41  |   fBodyAccMag.mean..                          |   Hz                                          |
42  |   fBodyAccMag.meanFreq..                      |   Hz                                          |
43  |   fBodyBodyAccJerkMag.mean..                  |   Hz                                          |
44  |   fBodyBodyAccJerkMag.meanFreq..              |   Hz                                          |
45  |   fBodyBodyGyroMag.mean..                     |   Hz                                          |
46  |   fBodyBodyGyroMag.meanFreq..                 |   Hz                                          |
47  |   fBodyBodyGyroJerkMag.mean..                 |   Hz                                          |
48  |   fBodyBodyGyroJerkMag.meanFreq..             |   Hz                                          | 
49  |   angle.tBodyAccMean.gravity.                 |   Degrees                                     |  
50  |   angle.tBodyAccJerkMean..gravityMean.        |   Degrees                                     |    
51  |   angle.tBodyGyroMean.gravityMean.            |   Degrees                                     |
52  |   angle.tBodyGyroJerkMean.gravityMean.        |   Degrees                                     |
53  |   angle.X.gravityMean.                        |   Degrees                                     |
54  |   angle.Y.gravityMean.                        |   Degrees                                     |
55  |   angle.Z.gravityMean.                        |   Degrees                                     |
56  |   tBodyAcc.std...X                            |   standard gravity units "g", i.e. m/s^2      |
57  |   tBodyAcc.std...Y                            |   standard gravity units "g", i.e. m/s^2      |
58  |   tBodyAcc.std...Z                            |   standard gravity units "g", i.e. m/s^2      |
59  |   tGravityAcc.std...X                         |   standard gravity units "g", i.e. m/s^2      |
60  |   tGravityAcc.std...Y                         |   standard gravity units "g", i.e. m/s^2      |
61  |   tGravityAcc.std...Z                         |   standard gravity units "g", i.e. m/s^2      |
62  |   tBodyAccJerk.std...X                        |   standard gravity units "g", i.e. m/s^2      |
63  |   tBodyAccJerk.std...Y                        |   standard gravity units "g", i.e. m/s^2      |
64  |   tBodyAccJerk.std...Z                        |   standard gravity units "g", i.e. m/s^2      |
65  |   tBodyGyro.std...X                           |   standard gravity units "g", i.e. m/s^2      |
66  |   tBodyGyro.std...Y                           |   standard gravity units "g", i.e. m/s^2      |
67  |   tBodyGyro.std...Z                           |   standard gravity units "g", i.e. m/s^2      |
68  |   tBodyGyroJerk.std...X                       |   standard gravity units "g", i.e. m/s^2      |
69  |   tBodyGyroJerk.std...Y                       |   standard gravity units "g", i.e. m/s^2      |
70  |   tBodyGyroJerk.std...Z                       |   standard gravity units "g", i.e. m/s^2      |
71  |   tBodyAccMag.std..                           |   standard gravity units "g", i.e. m/s^2      | 
72  |   tGravityAccMag.std..                        |   standard gravity units "g", i.e. m/s^2      |
73  |   tBodyAccJerkMag.std..                       |   standard gravity units "g", i.e. m/s^2      | 
74  |   tBodyGyroMag.std..                          |   standard gravity units "g", i.e. m/s^2      |
75  |   tBodyGyroJerkMag.std..                      |   standard gravity units "g", i.e. m/s^2      |
76  |   fBodyAcc.std...X                            |   Hz                                          |
77  |   fBodyAcc.std...Y                            |   Hz                                          |
78  |   fBodyAcc.std...Z                            |   Hz                                          |
79  |   fBodyAccJerk.std...X                        |   Hz                                          |
80  |   fBodyAccJerk.std...Y                        |   Hz                                          |
81  |   fBodyAccJerk.std...Z                        |   Hz                                          |
82  |   fBodyGyro.std...X                           |   Hz                                          |
83  |   fBodyGyro.std...Y                           |   Hz                                          |
84  |   fBodyGyro.std...Z                           |   Hz                                          |
85  |   fBodyAccMag.std..                           |   Hz                                          |
86  |   fBodyBodyAccJerkMag.std..                   |   Hz                                          |
87  |   fBodyBodyGyroMag.std..                      |   Hz                                          |  
88  |   fBodyBodyGyroJerkMag.std..                  |   Hz                                          |
  

