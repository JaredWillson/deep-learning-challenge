# deep-learning-challenge
This repository is organized as follows:
- `charity_data.csv` contains the raw data that were used to train and test the neural network
- `AlphabetSoupCharity.ipynb` contains the Jupyter notebook for building the model prior to optimization
- `AlphabetSoupCharity_Optimization.ipynb` contains the Jupyter notebook after the model was optimized to improve performance
- `AlphabetSoupCharity.h5` and `AlphabetSoupCharify_Optimized.h5` contain the models themselves for use against new datasets
- `Neural_Network_Analysis.md` contains a summary report of the approach and findings

All code is my own, but XPert Learning Assistant was used to quickly lookup syntax.

In a tutoring session, fellow student Karuna Kesavan Kothandath learned that pulling `name` back into the dataset and using that as an additional feature can bring up the accuracy since the name is not actually a unique identifier.  I used this knowledge and adjusted my optimized code.
