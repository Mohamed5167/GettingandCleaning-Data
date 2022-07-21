# Human Activity Recognition Using Smartphones Dataset

## Version 1.0

Jorge L. Reyes-Ortiz, Davide Anguita, Alessandro Ghio, Luca Oneto.  
Smartlab - Non Linear Complex Systems Laboratory  
DITEN - Università degli Studi di Genova.  
Via Opera Pia 11A, I-16145, Genoa, Italy.  
<activityrecognition@smartlab.ws>  
www.smartlab.ws

# Data Information

The experiments have been carried out with a group of 30 volunteers
within an age bracket of 19-48 years. Each person performed six
activities (WALKING, WALKING\_UPSTAIRS, WALKING\_DOWNSTAIRS, SITTING,
STANDING, LAYING) wearing a smartphone (Samsung Galaxy S II) on the
waist. Using its embedded accelerometer and gyroscope, we captured
3-axial linear acceleration and 3-axial angular velocity at a constant
rate of 50Hz. The experiments have been video-recorded to label the data
manually. The obtained dataset has been randomly partitioned into two
sets, where 70% of the volunteers was selected for generating the
training data and 30% the test data.

The sensor signals (accelerometer and gyroscope) were pre-processed by
applying noise filters and then sampled in fixed-width sliding windows
of 2.56 sec and 50% overlap (128 readings/window). The sensor
acceleration signal, which has gravitational and body motion components,
was separated using a Butterworth low-pass filter into body acceleration
and gravity. The gravitational force is assumed to have only low
frequency components, therefore a filter with 0.3 Hz cutoff frequency
was used. From each window, a vector of features was obtained by
calculating variables from the time and frequency domain.

# Features Information

The features selected for this database come from the accelerometer and
gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ. These time domain
signals (prefix ‘t’ to denote time) were captured at a constant rate of
50 Hz. Then they were filtered using a median filter and a 3rd order low
pass Butterworth filter with a corner frequency of 20 Hz to remove
noise. Similarly, the acceleration signal was then separated into body
and gravity acceleration signals (tBodyAcc-XYZ and tGravityAcc-XYZ)
using another low pass Butterworth filter with a corner frequency of 0.3
Hz.

Subsequently, the body linear acceleration and angular velocity were
derived in time to obtain Jerk signals (tBodyAccJerk-XYZ and
tBodyGyroJerk-XYZ). Also the magnitude of these three-dimensional
signals were calculated using the Euclidean norm (tBodyAccMag,
tGravityAccMag, tBodyAccJerkMag, tBodyGyroMag, tBodyGyroJerkMag).

Finally a Fast Fourier Transform (FFT) was applied to some of these
signals producing fBodyAcc-XYZ, fBodyAccJerk-XYZ, fBodyGyro-XYZ,
fBodyAccJerkMag, fBodyGyroMag, fBodyGyroJerkMag. (Note the ‘f’ to
indicate frequency domain signals).

These signals were used to estimate variables of the feature vector for
each pattern:  
‘-XYZ’ is used to denote 3-axial signals in the X, Y and Z directions.

tBodyAcc-XYZ  
tGravityAcc-XYZ  
tBodyAccJerk-XYZ  
tBodyGyro-XYZ  
tBodyGyroJerk-XYZ  
tBodyAccMag  
tGravityAccMag  
tBodyAccJerkMag  
tBodyGyroMag  
tBodyGyroJerkMag  
fBodyAcc-XYZ  
fBodyAccJerk-XYZ  
fBodyGyro-XYZ  
fBodyAccMag  
fBodyAccJerkMag  
fBodyGyroMag  
fBodyGyroJerkMag

The set of variables that were estimated from these signals are:

mean(): Mean value  
std(): Standard deviation  
meanFreq(): Weighted average of the frequency components to obtain a
mean frequency

# Attribute Information

-   Triaxial acceleration from the accelerometer (total acceleration)
    and the estimated body acceleration.
-   Triaxial Angular velocity from the gyroscope.
-   A 561-feature vector with time and frequency domain variables.
-   Its activity label.
-   An identifier of the subject who carried out the experiment.

# Variable Description

    run <- run_analysis()
    my_df <- data.frame(row.names = NULL, "ID" = c(1:ncol(run)),
                        "colName" = names(run),
                        "class" = sapply(run, class),
                        "range" = sapply(run, function(x)
                            if (class(x) == "integer" || class(x) == "numeric") {
                                paste(min(x), max(x), sep = " --> ")
                            }
                            else {
                                paste(unique(x), collapse = " / ")
                            }
                        ))
    kable(my_df, align = "l")

<table>
<colgroup>
<col style="width: 2%" />
<col style="width: 31%" />
<col style="width: 7%" />
<col style="width: 58%" />
</colgroup>
<thead>
<tr class="header">
<th style="text-align: left;">ID</th>
<th style="text-align: left;">colName</th>
<th style="text-align: left;">class</th>
<th style="text-align: left;">range</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;">1</td>
<td style="text-align: left;">SubjectID</td>
<td style="text-align: left;">integer</td>
<td style="text-align: left;">1 –&gt; 30</td>
</tr>
<tr class="even">
<td style="text-align: left;">2</td>
<td style="text-align: left;">Activities</td>
<td style="text-align: left;">character</td>
<td style="text-align: left;">LAYING / SITTING / STANDING / WALKING /
WALKING_DOWNSTAIRS / WALKING_UPSTAIRS</td>
</tr>
<tr class="odd">
<td style="text-align: left;">3</td>
<td style="text-align: left;">tBodyAcc-mean()-X_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">0.22159824394 –&gt; 0.3014610196</td>
</tr>
<tr class="even">
<td style="text-align: left;">4</td>
<td style="text-align: left;">tBodyAcc-mean()-Y_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.0405139534294 –&gt;
-0.00130828765170213</td>
</tr>
<tr class="odd">
<td style="text-align: left;">5</td>
<td style="text-align: left;">tBodyAcc-mean()-Z_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.152513899520833 –&gt;
-0.07537846886</td>
</tr>
<tr class="even">
<td style="text-align: left;">6</td>
<td style="text-align: left;">tBodyAcc-std()-X_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.996068635384615 –&gt;
0.626917070512821</td>
</tr>
<tr class="odd">
<td style="text-align: left;">7</td>
<td style="text-align: left;">tBodyAcc-std()-Y_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.990240946666667 –&gt;
0.616937015333333</td>
</tr>
<tr class="even">
<td style="text-align: left;">8</td>
<td style="text-align: left;">tBodyAcc-std()-Z_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.987658662307692 –&gt;
0.609017879074074</td>
</tr>
<tr class="odd">
<td style="text-align: left;">9</td>
<td style="text-align: left;">tGravityAcc-mean()-X_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.680043155060241 –&gt; 0.974508732</td>
</tr>
<tr class="even">
<td style="text-align: left;">10</td>
<td style="text-align: left;">tGravityAcc-mean()-Y_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.479894842941176 –&gt;
0.956593814210526</td>
</tr>
<tr class="odd">
<td style="text-align: left;">11</td>
<td style="text-align: left;">tGravityAcc-mean()-Z_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.49508872037037 –&gt; 0.9578730416</td>
</tr>
<tr class="even">
<td style="text-align: left;">12</td>
<td style="text-align: left;">tGravityAcc-std()-X_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.996764227384615 –&gt;
-0.829554947808219</td>
</tr>
<tr class="odd">
<td style="text-align: left;">13</td>
<td style="text-align: left;">tGravityAcc-std()-Y_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.99424764884058 –&gt;
-0.643578361424658</td>
</tr>
<tr class="even">
<td style="text-align: left;">14</td>
<td style="text-align: left;">tGravityAcc-std()-Z_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.990957249538462 –&gt;
-0.610161166287671</td>
</tr>
<tr class="odd">
<td style="text-align: left;">15</td>
<td style="text-align: left;">tBodyAccJerk-mean()-X_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">0.0426880986186441 –&gt;
0.130193043809524</td>
</tr>
<tr class="even">
<td style="text-align: left;">16</td>
<td style="text-align: left;">tBodyAccJerk-mean()-Y_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.0386872111282051 –&gt;
0.056818586275</td>
</tr>
<tr class="odd">
<td style="text-align: left;">17</td>
<td style="text-align: left;">tBodyAccJerk-mean()-Z_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.0674583919268293 –&gt;
0.0380533591627451</td>
</tr>
<tr class="even">
<td style="text-align: left;">18</td>
<td style="text-align: left;">tBodyAccJerk-std()-X_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.994604542264151 –&gt;
0.544273037307692</td>
</tr>
<tr class="odd">
<td style="text-align: left;">19</td>
<td style="text-align: left;">tBodyAccJerk-std()-Y_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.989513565652174 –&gt;
0.355306716915385</td>
</tr>
<tr class="even">
<td style="text-align: left;">20</td>
<td style="text-align: left;">tBodyAccJerk-std()-Z_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.993288313333333 –&gt;
0.0310157077775926</td>
</tr>
<tr class="odd">
<td style="text-align: left;">21</td>
<td style="text-align: left;">tBodyGyro-mean()-X_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.205775427307692 –&gt;
0.19270447595122</td>
</tr>
<tr class="even">
<td style="text-align: left;">22</td>
<td style="text-align: left;">tBodyGyro-mean()-Y_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.204205356087805 –&gt;
0.0274707556666667</td>
</tr>
<tr class="odd">
<td style="text-align: left;">23</td>
<td style="text-align: left;">tBodyGyro-mean()-Z_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.0724546025804878 –&gt;
0.179102058245614</td>
</tr>
<tr class="even">
<td style="text-align: left;">24</td>
<td style="text-align: left;">tBodyGyro-std()-X_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.994276591304348 –&gt;
0.267657219333333</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25</td>
<td style="text-align: left;">tBodyGyro-std()-Y_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.994210471914894 –&gt;
0.476518714444444</td>
</tr>
<tr class="even">
<td style="text-align: left;">26</td>
<td style="text-align: left;">tBodyGyro-std()-Z_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.985538363333333 –&gt;
0.564875818162963</td>
</tr>
<tr class="odd">
<td style="text-align: left;">27</td>
<td style="text-align: left;">tBodyGyroJerk-mean()-X_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.157212539189362 –&gt;
-0.0220916265065217</td>
</tr>
<tr class="even">
<td style="text-align: left;">28</td>
<td style="text-align: left;">tBodyGyroJerk-mean()-Y_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.0768089915604167 –&gt;
-0.0132022768074468</td>
</tr>
<tr class="odd">
<td style="text-align: left;">29</td>
<td style="text-align: left;">tBodyGyroJerk-mean()-Z_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.0924998531372549 –&gt;
-0.00694066389361702</td>
</tr>
<tr class="even">
<td style="text-align: left;">30</td>
<td style="text-align: left;">tBodyGyroJerk-std()-X_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.99654254057971 –&gt;
0.179148649684615</td>
</tr>
<tr class="odd">
<td style="text-align: left;">31</td>
<td style="text-align: left;">tBodyGyroJerk-std()-Y_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.997081575652174 –&gt;
0.295945926186441</td>
</tr>
<tr class="even">
<td style="text-align: left;">32</td>
<td style="text-align: left;">tBodyGyroJerk-std()-Z_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.995380794637681 –&gt;
0.193206498960417</td>
</tr>
<tr class="odd">
<td style="text-align: left;">33</td>
<td style="text-align: left;">tBodyAccMag-mean()_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.986493196666667 –&gt;
0.644604325128205</td>
</tr>
<tr class="even">
<td style="text-align: left;">34</td>
<td style="text-align: left;">tBodyAccMag-std()_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.986464542615385 –&gt;
0.428405922622222</td>
</tr>
<tr class="odd">
<td style="text-align: left;">35</td>
<td style="text-align: left;">tGravityAccMag-mean()_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.986493196666667 –&gt;
0.644604325128205</td>
</tr>
<tr class="even">
<td style="text-align: left;">36</td>
<td style="text-align: left;">tGravityAccMag-std()_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.986464542615385 –&gt;
0.428405922622222</td>
</tr>
<tr class="odd">
<td style="text-align: left;">37</td>
<td style="text-align: left;">tBodyAccJerkMag-mean()_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.99281471515625 –&gt;
0.434490400974359</td>
</tr>
<tr class="even">
<td style="text-align: left;">38</td>
<td style="text-align: left;">tBodyAccJerkMag-std()_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.994646916811594 –&gt;
0.450612065720513</td>
</tr>
<tr class="odd">
<td style="text-align: left;">39</td>
<td style="text-align: left;">tBodyGyroMag-mean()_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.980740846769231 –&gt;
0.418004608615385</td>
</tr>
<tr class="even">
<td style="text-align: left;">40</td>
<td style="text-align: left;">tBodyGyroMag-std()_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.981372675614035 –&gt;
0.299975979851852</td>
</tr>
<tr class="odd">
<td style="text-align: left;">41</td>
<td style="text-align: left;">tBodyGyroJerkMag-mean()_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.997322526811594 –&gt;
0.0875816618205128</td>
</tr>
<tr class="even">
<td style="text-align: left;">42</td>
<td style="text-align: left;">tBodyGyroJerkMag-std()_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.997666071594203 –&gt;
0.250173204117966</td>
</tr>
<tr class="odd">
<td style="text-align: left;">43</td>
<td style="text-align: left;">fBodyAcc-mean()-X_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.995249932641509 –&gt;
0.537012022051282</td>
</tr>
<tr class="even">
<td style="text-align: left;">44</td>
<td style="text-align: left;">fBodyAcc-mean()-Y_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.989034304057971 –&gt;
0.524187686888889</td>
</tr>
<tr class="odd">
<td style="text-align: left;">45</td>
<td style="text-align: left;">fBodyAcc-mean()-Z_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.989473926666667 –&gt;
0.280735952206667</td>
</tr>
<tr class="even">
<td style="text-align: left;">46</td>
<td style="text-align: left;">fBodyAcc-std()-X_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.996604570307692 –&gt;
0.658506543333333</td>
</tr>
<tr class="odd">
<td style="text-align: left;">47</td>
<td style="text-align: left;">fBodyAcc-std()-Y_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.990680395362319 –&gt; 0.560191344</td>
</tr>
<tr class="even">
<td style="text-align: left;">48</td>
<td style="text-align: left;">fBodyAcc-std()-Z_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.987224804307692 –&gt;
0.687124163703704</td>
</tr>
<tr class="odd">
<td style="text-align: left;">49</td>
<td style="text-align: left;">fBodyAcc-meanFreq()-X_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.635913046346154 –&gt;
0.159123629063636</td>
</tr>
<tr class="even">
<td style="text-align: left;">50</td>
<td style="text-align: left;">fBodyAcc-meanFreq()-Y_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.379518455061538 –&gt;
0.466528231788462</td>
</tr>
<tr class="odd">
<td style="text-align: left;">51</td>
<td style="text-align: left;">fBodyAcc-meanFreq()-Z_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.520114793584906 –&gt;
0.402532553395833</td>
</tr>
<tr class="even">
<td style="text-align: left;">52</td>
<td style="text-align: left;">fBodyAccJerk-mean()-X_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.994630797358491 –&gt;
0.474317256051282</td>
</tr>
<tr class="odd">
<td style="text-align: left;">53</td>
<td style="text-align: left;">fBodyAccJerk-mean()-Y_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.989398823913043 –&gt;
0.276716853307692</td>
</tr>
<tr class="even">
<td style="text-align: left;">54</td>
<td style="text-align: left;">fBodyAccJerk-mean()-Z_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.992018447826087 –&gt;
0.157775692377778</td>
</tr>
<tr class="odd">
<td style="text-align: left;">55</td>
<td style="text-align: left;">fBodyAccJerk-std()-X_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.995073759245283 –&gt;
0.476803887476923</td>
</tr>
<tr class="even">
<td style="text-align: left;">56</td>
<td style="text-align: left;">fBodyAccJerk-std()-Y_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.990468082753623 –&gt;
0.349771285415897</td>
</tr>
<tr class="odd">
<td style="text-align: left;">57</td>
<td style="text-align: left;">fBodyAccJerk-std()-Z_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.993107759855072 –&gt;
-0.00623647528983051</td>
</tr>
<tr class="even">
<td style="text-align: left;">58</td>
<td style="text-align: left;">fBodyAccJerk-meanFreq()-X_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.576044001875 –&gt;
0.331449281481482</td>
</tr>
<tr class="odd">
<td style="text-align: left;">59</td>
<td style="text-align: left;">fBodyAccJerk-meanFreq()-Y_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.601971415384615 –&gt;
0.195677336307692</td>
</tr>
<tr class="even">
<td style="text-align: left;">60</td>
<td style="text-align: left;">fBodyAccJerk-meanFreq()-Z_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.62755547372549 –&gt;
0.230107945944444</td>
</tr>
<tr class="odd">
<td style="text-align: left;">61</td>
<td style="text-align: left;">fBodyGyro-mean()-X_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.99312260884058 –&gt;
0.474962448333333</td>
</tr>
<tr class="even">
<td style="text-align: left;">62</td>
<td style="text-align: left;">fBodyGyro-mean()-Y_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.994025488297872 –&gt;
0.328817010088889</td>
</tr>
<tr class="odd">
<td style="text-align: left;">63</td>
<td style="text-align: left;">fBodyGyro-mean()-Z_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.985957788 –&gt; 0.492414379822222</td>
</tr>
<tr class="even">
<td style="text-align: left;">64</td>
<td style="text-align: left;">fBodyGyro-std()-X_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.994652185217391 –&gt;
0.196613286661538</td>
</tr>
<tr class="odd">
<td style="text-align: left;">65</td>
<td style="text-align: left;">fBodyGyro-std()-Y_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.994353086595745 –&gt;
0.646233637037037</td>
</tr>
<tr class="even">
<td style="text-align: left;">66</td>
<td style="text-align: left;">fBodyGyro-std()-Z_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.986725274871795 –&gt;
0.522454216314815</td>
</tr>
<tr class="odd">
<td style="text-align: left;">67</td>
<td style="text-align: left;">fBodyGyro-meanFreq()-X_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.395770150677419 –&gt;
0.249209411510602</td>
</tr>
<tr class="even">
<td style="text-align: left;">68</td>
<td style="text-align: left;">fBodyGyro-meanFreq()-Y_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.666814815306122 –&gt;
0.273141323315789</td>
</tr>
<tr class="odd">
<td style="text-align: left;">69</td>
<td style="text-align: left;">fBodyGyro-meanFreq()-Z_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.507490866734694 –&gt; 0.3770740968</td>
</tr>
<tr class="even">
<td style="text-align: left;">70</td>
<td style="text-align: left;">fBodyAccMag-mean()_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.986800645362319 –&gt;
0.586637550769231</td>
</tr>
<tr class="odd">
<td style="text-align: left;">71</td>
<td style="text-align: left;">fBodyAccMag-std()_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.987648484461539 –&gt;
0.178684580868889</td>
</tr>
<tr class="even">
<td style="text-align: left;">72</td>
<td style="text-align: left;">fBodyAccMag-meanFreq()_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.312338030213846 –&gt;
0.435846931652174</td>
</tr>
<tr class="odd">
<td style="text-align: left;">73</td>
<td style="text-align: left;">fBodyBodyAccJerkMag-mean()_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.993998275797101 –&gt;
0.538404846128205</td>
</tr>
<tr class="even">
<td style="text-align: left;">74</td>
<td style="text-align: left;">fBodyBodyAccJerkMag-std()_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.994366667681159 –&gt;
0.316346415348718</td>
</tr>
<tr class="odd">
<td style="text-align: left;">75</td>
<td style="text-align: left;">fBodyBodyAccJerkMag-meanFreq()_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.125210388757581 –&gt;
0.488088499666667</td>
</tr>
<tr class="even">
<td style="text-align: left;">76</td>
<td style="text-align: left;">fBodyBodyGyroMag-mean()_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.986535242105263 –&gt;
0.203979764835897</td>
</tr>
<tr class="odd">
<td style="text-align: left;">77</td>
<td style="text-align: left;">fBodyBodyGyroMag-std()_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.981468841692308 –&gt;
0.236659662496296</td>
</tr>
<tr class="even">
<td style="text-align: left;">78</td>
<td style="text-align: left;">fBodyBodyGyroMag-meanFreq()_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.456638670923077 –&gt;
0.409521611525424</td>
</tr>
<tr class="odd">
<td style="text-align: left;">79</td>
<td style="text-align: left;">fBodyBodyGyroJerkMag-mean()_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.997617389275362 –&gt;
0.146618569064407</td>
</tr>
<tr class="even">
<td style="text-align: left;">80</td>
<td style="text-align: left;">fBodyBodyGyroJerkMag-std()_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.99758523057971 –&gt;
0.287834616098305</td>
</tr>
<tr class="odd">
<td style="text-align: left;">81</td>
<td style="text-align: left;">fBodyBodyGyroJerkMag-meanFreq()_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.182923596577778 –&gt;
0.426301679855072</td>
</tr>
<tr class="even">
<td style="text-align: left;">82</td>
<td style="text-align: left;">angle(tBodyAccMean,gravity)_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.163042575021277 –&gt;
0.129153963587755</td>
</tr>
<tr class="odd">
<td style="text-align: left;">83</td>
<td
style="text-align: left;">angle(tBodyAccJerkMean),gravityMean)_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.120553975717391 –&gt;
0.203259965863014</td>
</tr>
<tr class="even">
<td style="text-align: left;">84</td>
<td style="text-align: left;">angle(tBodyGyroMean,gravityMean)_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.389305120341463 –&gt;
0.444101172307692</td>
</tr>
<tr class="odd">
<td style="text-align: left;">85</td>
<td
style="text-align: left;">angle(tBodyGyroJerkMean,gravityMean)_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.223672056052174 –&gt;
0.182384802705085</td>
</tr>
<tr class="even">
<td style="text-align: left;">86</td>
<td style="text-align: left;">angle(X,gravityMean)_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.947116527659574 –&gt;
0.737784354819277</td>
</tr>
<tr class="odd">
<td style="text-align: left;">87</td>
<td style="text-align: left;">angle(Y,gravityMean)_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.874567701929825 –&gt;
0.42476122745098</td>
</tr>
<tr class="even">
<td style="text-align: left;">88</td>
<td style="text-align: left;">angle(Z,gravityMean)_mean</td>
<td style="text-align: left;">numeric</td>
<td style="text-align: left;">-0.873649367 –&gt; 0.390444368518519</td>
</tr>
</tbody>
</table>
