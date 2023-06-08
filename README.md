# The WearableLearning Game Analysis Tool
Recently, educators and computer science researchers have begun partnering to develop new pedagogical tools based on wearable technology. Wearable Learning (WL) provides students with the tools to play physically active math games using mobile devices, as well as design their own games through the WL Platform. The games created by children are stored as JSON files.

This tool enables the analysis of the finite state machine JSON representations of WearableLearning games for research. In other words, we will identify what characteristics can be extracted from student game designs.

The code is divided into two parts: 
1. The Finding Loops and Conditionals part that is used to detect and count loops and if-else structures in the Finite State Machine representation of the children games; .
2. The Model to classify children's text: We analyze the games using text descriptions written by children. To do that, we use BERT to encode the input vectors (the numerical data that comes from embedded text) into hidden states that capture contextual information of the inputs. The hidden states are then put into a neural network which then processes and learns from the states and adjusts the weights/strengths of connections between the nodes based on patterns and relationships in the data. In the end, we have 54 output nodes corresponding to our 54 classes (54 attributes of the games).

# Working on this Project

# Code based, Analysis, and Result
## Set up: Tools and Modules
+ For local IDE: Setting up environment for **Ipython notebook** - just like Jupiter
+ For Google Colab: 
    * Either use Google Drive or Upload manually data folder to Google Colab
    * Go to Edit > Notebook Settings > Select GPU 
    * Currently, Google Colab runs the code without any problem. However, some of the modules/libraries used may change over time, and new versions may have different syntax, so please check for the version if any error occurs. 
    * Modules uses: transformers, torch, BERT
    * Simple Run all when use Google Colab

## FSM and Manual data folder
For the data that you passed into the fsm-data and manual-analysis folder, it is important to use the same name (the JSON file name should match with the csv name file).

## The Code
Finding Loops and Conditional Part:
+ The results are now available in the “result_loop_if_else.txt” file. Data retrieval can be found in that file and treat it like a csv file.
+ Since the scarcity of the data we have, we actually remove 3 json files and wait until we get the manual analysis then we can re-add them. References are already presented in the code! All you have to do is comment out to re-add them.
+ The implementation of loops derives from the study of [detect cycle in a directed Graph by Geek For Geek](https://www.geeksforgeeks.org/detect-cycle-in-a-graph/)

Model to classify the children's text
+ The code is fully commented on in the ipynb file. The process would be extracting all of the text and then tokenizing them, creating a DataFrame that contains the input text and the output classes, building a model and then feeding the DataFrame to the model. 
+ Users also have to make sure that the json and csv files are in the same name. 
+ Currently, the complete version of the code is on Google Colab: [Text analyzation](https://colab.research.google.com/drive/1unju8IEMUfNFuNSi4zmcik0s6QUaCtzs). Currently, the complete version of the code is on Google Colab: Text analyzation. The file NLP_Colab.ibynb is the exact copy from Google Colab. Please note that running on local IDE and Google Colab will have some differences.
+ To use the model, please ensure the type of the input feeding into the model. All input should be converted to the DataFrame, and follow the same step of preprocessing as the data that was used to train the model. 
+ The Result1.csv file contains the result of the model when running the following games (in this exact order):
    * Hackers_IN
    * IndianBoys_IN
    * IndianGirls_IN
    * MathParkour_US
    * Raistar_IN
    * fireballs20-us
+ Reference: Some of the code in this project (mainly the model) is adapted from the “Toxic Comment Classification Challenge” by Sebastion Raschka which can be found [here](https://www.kaggle.com/code/rasbtn/distilbert-v0/notebook). 
