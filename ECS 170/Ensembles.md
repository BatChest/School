**Bootstrap** 
- Takes random samples from your training data _with replacement_ (meaning the same data point can be picked multiple times)
- In the image, this is shown by the multiple boxes of colored dots, each representing different random samples from the original training data

**Aggregation**
- Each random sample is used to train a separate model (classifier or regressor)
- The image shows this with multiple "Classifier/Regressor" boxes (labeled 1 to N)
- All models' predictions are combined to make a final decision:
	- For classification: typically uses majority voting
	- For regression: typically uses averaging

**Key Benefits**
- Reduces overfitting because each model sees different versions of the data
- Decreases variance while keeping the bias the same
- Makes the overall prediction more robust and reliable

**Process Flow (as shown in image)**
![[Pasted image 20241030210536.png]]
1) Start with training data
2) Create multiple bootstrap samples
3) Train separate models on each sample
4) Combine predictions through the ensemble
5) Generate final outcome
- illustrates how bagging takes one dataset and creates multiple trained models that work together to make a final prediction on test data.

![[Pasted image 20241030210752.png]]
- **Process Overview**
	- Starts with a population (shown as blue dots)
	- Takes a random sample from population
	- Creates multiple resamples from original sample with replacement
	- Computes statistics from each resample
	- Creates a distribution of these statistics (shown in histogram)
- **Key Components**
	- Population: Original complete dataset (blue dots)
	- Original Sample: Initial random selection (brown/orange dots)
	- Resamples: Multiple new samples drawn with replacement (red dots)
	- Statistic (x): Can be "almost anything" (mean, median, variance, etc.)
	- Final Distribution: Histogram showing frequency of computed statistics
- **Confidence Interval**
	- Shown by the range on the histogram
	- Represents where "most of the probability mass for x" falls
	- Typically captures the middle portion of the distribution
	- Used to estimate uncertainty in the statistic
- **Key Purpose**
	- Useful when traditional confidence interval methods aren't practical
	- Helps estimate uncertainty in statistics through simulation
	- Provides empirical rather than theoretical confidence intervals
- **Important Note**
	- The "draw with replacement" means same data points can be selected multiple times
	- This is essential for bootstrapping to work properly
	- Creates variation in resamples while maintaining sample size


![[Pasted image 20241030211324.png]]

**Ensemble**
- Combining predictions from multiple learners is a recurring theme in machine learning

**Ensemble Improvisation** 
• **Core Concept**
  - Ensemble Improvisation is about making real-time adjustments to the model's prediction strategy
  - Unlike fixed ensemble methods (like bagging), it adapts its combination approach based on input data

• **Key Aspects**
  - Dynamic Weighting: Models in the ensemble get different weights based on their recent performance
  - Adaptive Selection: Can choose which models to use based on the specific input
  - Online Learning: Continuously updates its strategy as new data comes in

• **Common Approaches**
  - Meta-learning: Using another model to learn how to combine base models
  - Dynamic model selection: Choosing different subset of models for different inputs
  - Confidence-based weighting: Giving more weight to models that are more confident for specific cases

• **Benefits**
  - Better handles concept drift (when patterns in data change over time)
  - Can adapt to different types of inputs more effectively
  - Often performs better than static ensemble methods in dynamic environments

• **Challenges**
  - More complex to implement than static ensembles
  - Requires more computational resources
  - Need to balance adaptation speed with stability

![[Pasted image 20241030211719.png]]
- **Similarity to Bagging**
    - Uses multiple models (pool of models)
    - Takes training data and creates multiple samples
    - Uses classifiers/regressors to make predictions
    - Combines results through an ensemble
- **Key Difference from Bagging**
    - Sequential learning: Models are trained in sequence (shown by downward arrows)
    - Error correction: Each subsequent model focuses on correcting errors from previous models
    - Adaptive learning: Models build upon each other's strengths and weaknesses
- **Process Flow**
    - Starts with training data
    - Creates bootstrap samples
    - First classifier makes predictions
    - Subsequent classifiers specifically target errors from previous models
    - Final ensemble combines all predictions for outcome
- **Visual Structure**
    - Similar diagram to bagging but with important directional flow
    - Shows N different classifiers/regressors
    - Arrows indicate sequential dependency between models
    - Final ensemble combines all results for test data
- **Main Advantage**
    - More focused learning approach than bagging
    - Each model specifically addresses weaknesses in the ensemble
    - Can achieve better accuracy through targeted error correction
