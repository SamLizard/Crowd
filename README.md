# Crowd

Write me code in python that takes a list of numbers and plot a graph that will show crowd wisdom. Each number in the list is a prediction of someone on how much jellybeans they are in a jar. Explain me how it show crowd wisdom. 


Sure, I can help you with that!

Here's the code to plot the graph and show the crowd wisdom:

python

import matplotlib.pyplot as plt
import statistics

def plot_crowd_wisdom(predictions):
    """
    This function takes a list of numbers (predictions) and plots a graph that shows crowd wisdom.
    Each number in the list is a prediction of someone on how much jellybeans are in a jar.
    """

    # Calculate the mean and standard deviation of the predictions
    mean = statistics.mean(predictions)
    stdev = statistics.stdev(predictions)

    # Create a histogram of the predictions
    plt.hist(predictions, bins=range(min(predictions), max(predictions) + 2, 1), align='left')

    # Add a vertical line to indicate the mean
    plt.axvline(x=mean, color='red', label='Mean: {:.2f}'.format(mean))

    # Add a shaded region to indicate one standard deviation from the mean
    plt.axvspan(mean - stdev, mean + stdev, alpha=0.2, color='gray', label='1 Std Dev')

    # Set the plot title and labels
    plt.title('Crowd Wisdom: How Many Jellybeans in a Jar?')
    plt.xlabel('Number of Jellybeans')
    plt.ylabel('Number of Predictions')
    plt.legend()

    # Show the plot
    plt.show()

To use this function, simply call it with a list of predictions:

python

predictions = [50, 60, 55, 65, 70, 60, 62, 58, 63, 61]
plot_crowd_wisdom(predictions)

This will create a histogram of the predictions, with a vertical line indicating the mean and a shaded region indicating one standard deviation from the mean.

The graph shows crowd wisdom by demonstrating how the predictions of many individuals can converge to a more accurate estimate of the true value (in this case, the number of jellybeans in a jar). The central tendency of the predictions (the mean) is a more accurate estimate than any single prediction, and the standard deviation provides a measure of the uncertainty or variability in the crowd's estimate. By visualizing the distribution of the predictions and the degree of agreement among them, we can see how the wisdom of the crowd can be harnessed to make more accurate predictions.






Create me another graph that will show how crowd size has an impact on his accuracy.

Sure! Here's some code to create a scatter plot that shows how the size of the crowd impacts the accuracy of their predictions:

python

import matplotlib.pyplot as plt
import random

def simulate_crowd_predictions(true_value, max_crowd_size):
    """
    This function simulates a crowd of different sizes making predictions about a true value,
    and returns a list of tuples, where each tuple represents a (crowd_size, prediction_error) pair.
    """
    crowd_predictions = []
    for crowd_size in range(1, max_crowd_size+1):
        predictions = [random.randint(true_value-20, true_value+20) for _ in range(crowd_size)]
        mean_prediction = sum(predictions) / len(predictions)
        prediction_error = abs(mean_prediction - true_value)
        crowd_predictions.append((crowd_size, prediction_error))
    return crowd_predictions

# Set the true value and maximum crowd size
true_value = 50
max_crowd_size = 50

# Simulate crowds of different sizes making predictions
crowd_predictions = simulate_crowd_predictions(true_value, max_crowd_size)

# Extract the crowd sizes and prediction errors from the simulation results
crowd_sizes = [x[0] for x in crowd_predictions]
prediction_errors = [x[1] for x in crowd_predictions]

# Create a scatter plot of crowd size vs. prediction error
plt.scatter(crowd_sizes, prediction_errors)

# Set the plot title and labels
plt.title('Impact of Crowd Size on Prediction Accuracy')
plt.xlabel('Crowd Size')
plt.ylabel('Prediction Error')

# Show the plot
plt.show()

This code simulates a crowd of different sizes making predictions about a true value (in this case, true_value = 50). For each crowd size, it generates a list of predictions with random values between true_value-20 and true_value+20, calculates the mean prediction, and computes the prediction error as the absolute difference between the mean prediction and the true value. The function then returns a list of tuples, where each tuple represents a (crowd_size, prediction_error) pair.

The scatter plot shows the relationship between the size of the crowd and the accuracy of their predictions. As the crowd size increases, the prediction error tends to decrease, indicating that larger crowds are generally more accurate. However, there is also a lot of variability in the prediction error for small crowds, and even large crowds can sometimes be inaccurate. This demonstrates that while crowd wisdom can be a powerful tool, it is not always foolproof, and other factors such as the diversity and expertise of the crowd may also impact its accuracy.
