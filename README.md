# Decision-Tree-from-Scratch
fetch_20newsgroups dataset


First, data with categories 'comp.graphics', 'sci.space' were taken from fetch_20newsgroups                       
dataset. Later, punctuation marks, numbers, irrelevant words such as "from" and "subject"
in the data were cleared. Words with the same root such as "fishing", "fishes", "fish" were
identified and translated into the same word. Generated a word vector with CountVectorizer
and calculated how many specific word the document contains. Meanwhile, stopwords were
removed and words were reduced to lower. The ratio of word count to document size was
calculated using TfidfTransformer. The dataset was converted to a dataframe. Since
calculating the information gain by reworking the created model for thousands of columns
will cause a waste of time, the correlations were examined. The most effective 40 words
(features) on the targets were selected. The data was converted to binary, 0 if it does not
contain the word, and 1 if it contains one or more.

Two functions that calculate entropy and information gain for use in Decision tree model
are created. While calculating informatin gain, “Informatin Gain(X,S)=H(S)-H(X,S)”
formula was used. While H (S) is the entropy value of the 'newsgroup' attribute, H (X, S) is
the entropy value of other attributes based on 'newsgroup'. While creating the Decision tree
model, the max-depth value is taken as the parameter. Information gain was calculated for
each property of the dataframe and the maximum was selected. This selected value is set as
root node. The unique values of the root node are sent to the function named tree_insert as
"each" in a loop. In this function that works recursively, 'newsgroup' attributes are
controlled by bringing only the data with "each" from the dataframe. Since the unique
lengths equals to 1 means that all of them are 0 or 1, the result is reached and the step is
terminated. If not, it is checked max-depth. If it is the max-depth and still do not yield a
single result, the one with the majority of 0 and 1 values is selected. If the maximum depth
is not reached, the information gain values are calculated again for this data and attribute
with the maximum information gain is taken. This value is set as a new node and assigned
to its parent as child. The function is called over for the unique values of this value and the
same processes are repeated for it. The unique values of each node value are kept with the
category list to draw the tree and use in predict functions. The function returns the root
node. Test data was also cleared and converted into word vectors. It was then converted to
binary. The predictions are made by starting with the root of the tree with the predict
function and going to the related childs.

During the training phase, different models were created by giving parameters between
max-depth 4-30. For instance, decision tree for Maximum depth = 4 as in Figure 1.

![image](https://user-images.githubusercontent.com/45537416/120244579-3d46a680-c273-11eb-9d1c-111a14d187fb.png)

Train and test accuracy values related to max-depth are given in Figure 2 and Figure 3.

![image](https://user-images.githubusercontent.com/45537416/120244596-4d5e8600-c273-11eb-86d1-bb5262fee5f5.png)

Test data were also estimated using the Decision Tree available within Sklearn

![image](https://user-images.githubusercontent.com/45537416/120244612-5c453880-c273-11eb-8749-705b4b100175.png)

Graph showing the training and testing accuracy as the maximum depth increases is showed
in Figure 5.

![image](https://user-images.githubusercontent.com/45537416/120244638-77b04380-c273-11eb-97c0-27430d0a4fd1.png)




