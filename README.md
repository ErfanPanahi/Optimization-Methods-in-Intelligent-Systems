# Optimization-Methods-in-Intelligent-Systems
In this repository, I intend to focus on implementing various optimization methods. The first section employs binary logistic regression for classifying MNIST dataset. The second section deals with optimizing a non-convex cost function, using the genetic algorithm for this purpose. Lastly, in the third section, we acquaint ourselves with SVM.

**Part 1:** Binary Logistic Regression

Consider the MNIST dataset, where we aim to have a binary classifier; such that it determines whether a digit is the number 2 or 7. To achieve this, we assume that for the digits 7 in the dataset, 𝑌 = 1, and for the digits 2, 𝑌 = -1.

The following images depict the cost function values versus the number of iterations for both the training and testing datasets using all three steps.

![image](https://github.com/ErfanPanahi/Optimization-Methods-in-Intelligent-Systems/assets/107314081/068aefca-30bb-4d5d-a161-c8c7a9d4e2d7)

![image](https://github.com/ErfanPanahi/Optimization-Methods-in-Intelligent-Systems/assets/107314081/731b4811-a2ff-480e-a421-234763501519)

*Results:* As can be seen in the above image, the machine is better learned on the training data, and the value of the cost function is slightly more descending (lower). The reason for this is the larger number of training data. It is also observed that as the value of the Learning Rate approaches 1, the value of the cost function decreases more quickly.

![image](https://github.com/ErfanPanahi/Optimization-Methods-in-Intelligent-Systems/assets/107314081/a5911e34-35a1-4daf-ba3a-8daa5f861d39)

![image](https://github.com/ErfanPanahi/Optimization-Methods-in-Intelligent-Systems/assets/107314081/72fc51e1-8f98-4aef-98a4-17bd582140ee)

![image](https://github.com/ErfanPanahi/Optimization-Methods-in-Intelligent-Systems/assets/107314081/bfa3ade5-b459-4b7d-9c3c-a10155846d0c)

***Stochastic Gradient Descent:*** In this section, we perform the same steps as parts B and C with a difference in the algorithm. To do this, in each iteration, we select a randomly sized batch of data from the entire training dataset and use it to update the parameters b and ω. We carry out this process for batch sizes of 1 and 100. Subsequently, we obtain the accuracies for the newly designed machines in part C.

***Packet size = 1***

![image](https://github.com/ErfanPanahi/Optimization-Methods-in-Intelligent-Systems/assets/107314081/cce01eba-e35c-436e-ad3c-83b9a3d69529)

![image](https://github.com/ErfanPanahi/Optimization-Methods-in-Intelligent-Systems/assets/107314081/9a70fc71-3ac0-4b51-b6a3-294de9e81493)

![image](https://github.com/ErfanPanahi/Optimization-Methods-in-Intelligent-Systems/assets/107314081/290d41b0-de88-41da-86ae-23edae48fea8)

***Packet size = 100***

![image](https://github.com/ErfanPanahi/Optimization-Methods-in-Intelligent-Systems/assets/107314081/edc7b22c-000b-4e99-8d44-5acdd3225638)

![image](https://github.com/ErfanPanahi/Optimization-Methods-in-Intelligent-Systems/assets/107314081/1630edc5-a1fa-4b67-b227-9fd7b0e729e6)

![image](https://github.com/ErfanPanahi/Optimization-Methods-in-Intelligent-Systems/assets/107314081/59383bf1-7304-43bf-8ea4-b0be87206dc1)

*Results:* As observed in the images, for larger batch sizes during each iteration, the machine learns better from the training data, and the value of the cost function is slightly more decreasing (lower).

**Part 2:** Optimization in Non-Convex Functions

$f(x_1,x_2 )=2x_1^2+2x_2^2-17x_2  cos⁡(0.2πx_1 )-x_1 x_2$

***Newton Method*** 

- **Close:** If the distance is less than 5.
- **Far:** If the distance is between 5 and 50.
- **Farther:** If the distance is greater than 50.

![image](https://github.com/ErfanPanahi/Optimization-Methods-in-Intelligent-Systems/assets/107314081/34f9fd4b-e67d-4b91-aee8-26d35d1b2613)

***Metaheuristic Approach - Genetic Algorithm***

In this section, we consider a population of N arbitrary points. In the selection phase, we choose the best specimen (with the minimum value of the objective function) and introduce it into the new population. We select N-1 other samples as follows: from two randomly chosen points out of the previous N points, we pick the one with the lower value of the objective function and introduce it into the new population. In the crossover stage, we represent the selected numbers as an 8-bit binary number.

For this purpose, considering the given explanations, we treat each of x_2 and x_1 as an array ranging from -15 to +15 with 255 elements. We then shuffle the order of the population. Considering two adjacent members as a pair, we choose a random number from 1 to 7 and pair the two pairs by taking that number of bits from the left side. We repeat this process to create another child, and similarly, we generate a new population with the same number N.

In the mutation stage, with a probability of mutation_rate, we select a number of mutation_select from the population. Then, we randomly choose mutation_window bits from the selected group and flip them (if 0, make it 1; if 1, make it 0). Finally, we convert the numbers back from binary representation and return to the first stage. We repeat all these stages ITR times.

    ITR = 100
    Pop_size = 1000
    mutation_rate = 0.1
    mutation_window = 1
    mutation_select = 5

![image](https://github.com/ErfanPanahi/Optimization-Methods-in-Intelligent-Systems/assets/107314081/bc42f4c7-f696-4eea-afeb-8e30225f0e75)

**Part 3:** Support Vector Machine

In this section, we intend to perform classification on the iris dataset using Support Vector Machine. First, load the dataset using the code snippet below.

    from sklearn import datasets
    iris = datasets.load_iris()
    data = iris.data[:, :2] #data
    label = iris.target #label

*Results:*

![image](https://github.com/ErfanPanahi/Optimization-Methods-in-Intelligent-Systems/assets/107314081/fc72afb7-b5b2-4230-b47e-dc6cc75611d7)

![image](https://github.com/ErfanPanahi/Optimization-Methods-in-Intelligent-Systems/assets/107314081/05eb3bf0-e877-4809-8a52-183214d4f1d5)

![image](https://github.com/ErfanPanahi/Optimization-Methods-in-Intelligent-Systems/assets/107314081/9c82392d-1fa7-4017-8dc7-a11d5b5a6ae6)


