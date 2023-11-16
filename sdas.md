# Experiment No: 02
## Experiment Name: Modeling of OR gate with single layer perceptron

**Theory:**
The single-layer perceptron is the fundamental building block of artificial neural networks. Comprising a single layer of interconnected nodes, it transforms input features through weighted connections and produces an output. Each connection weight represents the significance of a respective input feature. The perceptron applies a weighted sum to the inputs and passes the result through an activation function, often a step function. This process enables binary classification by determining whether the aggregated input falls above or below a threshold. While powerful for linearly separable problems, the single-layer perceptron has limitations and cannot handle non-linear relationships. Its simplicity and interpretability make it a foundational concept in neural network history, setting the stage for the development of more complex models and architectures.

**Code:**
```python
import numpy as np
import matplotlib.pyplot as plt

def step_function(x):
    return 1 if x >= 0 else 0

X = np.array([[0, 0],
              [0, 1],
              [1, 0],
              [1, 1]])

y = np.array([0, 1, 1, 1])

weights = np.random.random(2)
bias = np.random.random()

learning_rate = 0.1
epochs = 100

errors = []

for epoch in range(epochs):
    total_error = 0
    for i in range(len(X)):
        weighted_sum = np.dot(X[i], weights) + bias
        prediction = step_function(weighted_sum)
        error = y[i] - prediction
        total_error += np.abs(error)
        weights += learning_rate * error * X[i]
        bias += learning_rate * error
    mean_error = total_error / len(X)
    errors.append(mean_error)

# Test data
test_inputs = np.array([[0, 0], [1, 0], [1, 1], [1, 0]])

# Evaluating the model on test data
test_predictions = np.vectorize(step_function)(np.dot(test_inputs, weights) + bias)

# Displaying the test input and the model's predictions
for i in range(len(test_inputs)):
    print(f"Test Input: {test_inputs[i]}, Predicted Output: {test_predictions[i]}")

plt.plot(range(epochs), errors)
plt.title('Epoch vs. Error')
plt.xlabel('Epoch')
plt.ylabel('Error')
plt.show()
```
**Output:**

```Output Table (Actual vs Predicted):
Test Input: [0 0], Predicted Output: 0
Test Input: [1 0], Predicted Output: 1
Test Input: [1 1], Predicted Output: 1
Test Input: [1 0], Predicted Output: 1
```
Epoch vs Erro graph:

![Alt text](https://github.com/AbuSyeedShihab/ECE-4124-Digital-Signal-Processing-Sessiona/blob/main/epoch%20vs%20error.png?raw=true)


**Discussion:**
In this Python code, we trained the single-layer perceptron model on a 2-bit OR gate input and output. Here 100 epochs were used to update the weights and biases according to the error in each step, And so the model learned the weight and bias. Then we use the learnt weight and bias to find predictions on some test inputs. From the graph, we can see that the model gave an error for the first 10-15 epochs and then there is no error. So the model successfully learned the weight and bias.

**Conclusion::**
All the codes associated with the experiment ran without any issues, and we were able to find the class accurately.

