# -XNH-XGBoost-Neural-Network-Hyper-Parameter-Auto-Tuner
This is an XGBoost Guided Neural Network Hyperparameter Auto Tuner to optimize the effectiveness of your neural networks.

I initially conceptualized the idea of stacking neural network architectures—one as the base neural network, and another as a hyperparameter tuner. Later, I realized that XGBoost, one of the top-performing ML models, could be combined effectively with a PyTorch neural network architecture for hyperparameter optimization.

This Auto XGBoost Hyperparameter Tuner was my original idea. While I used ChatGPT to generate the initial code, I meticulously reviewed and understood every line.

The tuner is highly adaptable and user-friendly—you can customize iterations, hyperparameters, activation functions, and more. The beauty of this project lies in its flexibility and ease of modification.

I also used the python libraries described in the code.

# ---- UPDATE! ------

Okay. On July 30th, I came up with a new idea. XGBoost functions sequentialy right? That must take a lot of time computationally. So, how do we parallelize it? It's simple. You create a 3 dimensional XGBoost Model space. X is equal to the number of trees, y is equal to the depth of the model, and z is equal to the number of xgboost models. So, what do we do. We randomly intialize trees based on the original dataset for all models (this is how XGBoost works). Then we calculate the residuals of those first trees and apply them to the next trees by multiply the residuals of other trees by a very small alpha (reducing the influence of other trees on the next tree in a specific xgboost model). We do this for all trees and all models, allowing or xgboost models to influence each other in parallel until the trees eventually become the same (as refined as possible). 

For this section I used ChatGPT to code the XGBoost 3D model and did not rewrite the code myself. Also, when testing the model on the same dataset, it worked in far less the time as a pose to the previous model code I had made earlier (the previous model code on the same dataset took about 1-3 minutes while the updated code took less than 20 seconds).
