# Questions

### (25%) Given the data set, do a quick exploratory data analysis to get a feel for the distributions and biases of the data. Report any visualizations and findings used and suggest any other impactful business use cases for that data.

This data is has extremely skewed distributions of values. To get an idea of how this data is layed out, I computed the counts of each unique value in each column, and made a bar graph representing these (one per column). For the "Year" column, there are almost no entries that contain "Year 1" or "Year 4". For the rest of the input columns ("Major", "University", and "Time"), they seem to follow an exponential growth curve. For the output column, "Order", all counts of the values seem to be approximately equal. The graphs are saved in "images/graphs/column_counts".

Additionally, I created temporal graphs for each university's Year, Major, and Order column. For example, the temporal graph for the Year column of a particular university would represent the how many students at that university in a particular year showed up to the food truck throughout the day. I noticed with pretty much all of these graphs that the counts peaked around lunch time. These graphs are saved in "images/graphs/trends".

Other impactful business use cases that can be derived from this data, apart from predicting what order a particular student will have, include using this dataset to find the times that students order food the most frequently (perahps on a per-campus basis), and which items are ordered the most. If the business had these insights, they would know the ideal timeframe to set up a food truck on a given campus, and which kinds of food they should have more/less of.

### (30%) Consider implications of data collection, storage, and data biases you would consider relevant here considering Data Ethics, Business Outcomes, and Technical Implications

1. Discuss Ethical implications of these factors

- When discussing data collection, there are ethical concerns when it comes to the consent of the student to have their data be collected for the business. They must be informed about how their data is collected, and ensured that it will be kept safe.
- For data storage, there may be some datapoints that could potentially be used to identify an individual, especially if there are rare/unique combinations of Year, Major, University, Time, and Order values in the dataset.
- For data biases, there are can be ethical concerns if patterns in the data are used in the future to stereotype a particular student based on their attributes, such as their University and Major.

2. Discuss Business outcome implications of these factors

- For data collection, the business outcome implications of this are that this data can be analyzed and used to gain insights into the preferences of students. With this information, the business can cater to these preferences and make more money. Additionally, trends in the time and place of particular orders can be analyzed to inform the business about what the best time period would be to set up at a particular location.
- When it comes to data storage, the business can keep adding to their database over time, and eventually be able to discern potential temporal patterns in the data, in terms of what menu items are the most popular throughout the year. This would allow the business to market specific items at specific periods in the year, and have knowledge about what food items they should prioritize making. Overall, this would allow for increased profits and less food waste.
- For data biases, the business can examine said biases and try to balance their dataset by catering more to underrepresented groups in the data. This would allow for any analysis done in the future to be more accurate, due to reduced bias.

3. Discuss Technical implications of these factors

- Technical implications of data collection come with ensuring that the data is securely and consistently collected (ideally for each order).
- In terms of data storage, it must be compliant with the law and with the university itself. This data also needs to be secure, and accessible only to trusted parties. Additionally, an established, trustworthy platform must be used to host this data, such as AWS.
- For data bias, there must be techniques in place that can mitigate biases from being drawn from the data, as this can lead to inaccurate analyses down the road.

### (35%) Build a model to predict a customers order from their available information. You will be graded largely on your intent and process when designing the model, performance is secondary. It is strongly suggested that you use SKLearn for this model as to not take too much time. You may use any kind implementation you would like though, but it must be pickelable and have a “.predict()” method similar to SKLearn

### Outline your process for model selection, training and testing. Including data preparation.

1. Design a function that prepares your data by loading the provided dataset and processes it into an appropriate machine readable format if necessary.
2. Design a function to train your model and pickle it.
3. Train and test your model. Submit any training, testing and model selection visuals or metrics.
4. Upload your work to GitHub and link the repository, make sure it is public.

For data preparation, I first loaded the data in via pandas and looked at the preview for the it. I noticed all of this data, aside from the "Time" column, contains categorical values (i.e. string values). This immediately told me I would need to encode these values numerically before passing the dataset into a machine learning model. Therefore, I looked into how I could do this with SKLearn, and saw they have something called a Label Encoder. I used this to encode the values of each categorical column into numbers that represent their original value.

With the data ready to pass into a model, I assigned the values of the "Year", "Major", "University", and "Time" columns to an X variable, and the values in the "Order" column to a y variable. All that was left was to split this data into train and test data, via train_test_split from SKLearn, with an 80/20 split.

For selecting a model, I needed something that could do classification, as there are several classes, or values (representing the different orders), that the model must be able to classify data into. Random Forests are powerful classification models for achieving this task, as they introduce an element of randomness that decreases variance and the likelihood of overfitting. Therefore, I decided to use one for this task.

I fit a random forest model on the X_train and y_train data, then tested it on both the train and test data using the score() method of the model. Finally, I pickled the model, saving it into the file directory.

The model ended up having a train accuracy of 0.734 and a test accuracy of 0.651.

After this, I generated a confusion matrix, saved in "images". Then, I tested various values of hyperparameters for a random forest model on the training data, and graphed how different values affects a model's score. These graphs are saved in "images/graphs/hyperparameters". Finally, I graphed the feature importance of each input column, and saved this in "images/graphs". The "Major" column ended up being the most important feature in determining what a student would order.

### (10%) Given the work required to bring a solution like this to maturity and its performance, what considerations would you make to determine if this is a suitable course of action?

I would need to consider if it is even necessary to collect data on a student's major, year, university, and the time they order. After all, these things, except maybe time, intuitively don't make sense to try to correlate to a food order. These would be interesting datapoints to gather for other purposes, such as seeing when the food truck is the busiest at a particular university. I would consider additional datapoints to gather about the student though, that would, in theory, correlate better with their food preferences.

Above all, I would need to consider how to prevent my dataset from becoming biased, and make efforts to cater to as wide an audience as possible.
