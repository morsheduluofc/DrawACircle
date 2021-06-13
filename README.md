# Draw A Circle (DAC)
DAC is a challenge-response based behavioral authentication system. It constructs a profile for each user, based on their circle drawing activity, and stores it at the server. During an authentication session, the collected user data is compared against stored profile to make an authentication decision. DAC is implemented as an app for Android user. One can download and install it from Google Play (use the given link: https://play.google.com/store/apps/details?id=ucal.example.dacF).

## DAC Game Design. 
DAC has four challenges in each round of registration and verification. Here, first three challenges are three random circles with starting point is presented to the user. Fourth challenge is also a random circle that is shown to the user for 3 seconds and then disappears. For registration user have to be response 10 rounds challenges and for verification it will reduce to 5 rounds.

## Feature Selection.
DAC uses 65 features in each challenge-response and they are related with: i) vector of user errors, each component corresponding to the discrepancy between challenge and response, ii)features related to physical characteristics and drawing skills, and iii)short-term memory ability. All those features are selected through extensive experiments. It required the following properties for the features: i) distinctiveness: to distinguish users, ii) stability (permanence): for consistent measurement, iii) non-delegation: to provide security against passing credential to others, and iv) non-inferable cognitive ability: not to allow feature values to be inferred by observation.

## Verification Algorithm. 
DAC compares the claimed verification profile with stored profile to generate a matching scores by measuring the similarity/distance between them. In our case, the matching algorithm can be either feature distribution based or vector based.
The feature distribution based verification algorithm uses two sample Kolmogorov-Smirnov test ( one sample set come from registration and one from verification data) for each individual feature and produces a distance as well as confidence value. A meta-data analyzer (Fisher's method) combines all confidence values to a singel confidence value for final authentication decision.
Vector based verification algorithm measures the distance among the vectors. Different vector-based verification algorithms have different verification accuracy. We tried k-NN, weighted k-NN, SVM, KL-divergengence estimator based verification algorithms in DAC. We also used deep neural network classifer as the verification algorithm of DAC.  
