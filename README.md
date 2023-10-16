# Questions

(25%)  Given the data set, do a quick exploratory data analysis to get a feel for the distributions and biases of the data.  Report any visualizations and findings used and suggest any other impactful business use cases for that data.

This data is has extremely skewed distributions of values. To get an idea of how this data is layed out, I computed the counts of each unique value in each column, and made a bar graph representing this (one per column). For the "Year" column, there are almost no entries that contain "Year 1" or "Year 4". For the rest, they seem to follow an exponential growth curve. The graphs are saved in the "graphs" folder.
Other impactful business use cases that can be derived from this data, apart from predicting what order a student will have based on their data, this dataset can be used to find the times that students order food the most frequently (perahps on a per-campus basis), and which items are ordered the most. If the business had these insights, they would know the ideal timeframe to set up a food truck on a given campus, and which food resources they should have more/less of.

(30%) Consider implications of data collection, storage, and data biases you would consider relevant here considering Data Ethics, Business Outcomes, and Technical Implications

1. Discuss Ethical implications of these factors
2. Discuss Business outcome implications of these factors
3. Discuss Technical implications of these factors

(35%) Build a model to predict a customers order from their available information.  You will be graded largely on your intent and process when designing the model, performance is secondary. It is strongly suggested that you use SKLearn for this model as to not take too much time.  You may use any kind implementation you would like though, but it must be pickelable and have a “.predict()” method similar to SKLearn

Outline your process for model selection, training and testing. Including data preparation.
1. Design a function that prepares your data by loading the provided dataset and processes it into an appropriate machine readable format if necessary.
2. Design a function to train your model and pickle it.
3. Train and test your model.  Submit any training, testing and model selection visuals or metrics.
4. Upload your work to GitHub and link the repository, make sure it is public.

(10%) Given the work required to bring a solution like this to maturity and its performance, what considerations would you make to determine if this is a suitable course of action?
