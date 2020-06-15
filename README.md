# Book-Recommender-system
#### This is a User Based CF Recommender System.

Link to dataset files :-
http://www2.informatik.uni-freiburg.de/~cziegler/BX/

#### about the dataset :-
This dataset has been compiled by Cai-Nicolas Ziegler in 2004, and it comprises of three tables for users, books and ratings. Explicit ratings are expressed on a scale from 1-10 (higher values denoting higher appreciation) and implicit rating is expressed by 0

#### about preprocessing and loading data :-

Reference for data loading and preprocessing :-
https://github.com/csaluja/JupyterNotebooks-Medium/blob/master/Book%20Recommendation%20System.ipynb

I have followed Chhavi Saluja for data loading and preprocessing

She did a wonderfull job in cleaning , processing and analysing the data.

#### About the User Based CF Recommender System :-

After data loading and preprocessing data, I have taken the input from the user, the input is in the form of "ISBN":"rating",where ISBN represents International Standard Book Number and rating represents the rating given by the user to the respective books.Then I have merged the books dataset with it in order to get the book's title and removed all the unnecessary data.

Now with the book ID's in our input, we can now get the subset of users that have read and reviewed the books in our input. Then i have grouped those users who have rated multiple similar books as that of our input. In this group several sub dataframes are created where they all have the same value in the column specified as the parameter.

Next, we are going to compare all users (not really all !!!) to our specified user and find the one that is most similar.

We're going to find out how similar each user is to the input through the Pearson Correlation Coefficient. It is used to measure the strength of a linear association between two variables.

Now ,top 50 users that are most similar to the input are taken.

Now, let's start recommending Books to the input user. We're going to do this by taking the weighted average of the ratings of the books using the Pearson Correlation as the weight. But to do this, we first need to get the books readed by the users in our pearsonDF from the ratings dataframe and then store their correlation in a new column.

Now all we need to do is simply multiply the books rating by its weight (The similarity index), then sum up the new ratings and divide it by the sum of the weights.

We can easily do this by simply multiplying two columns, then grouping up the dataframe by ISBN and then dividing two columns:

It shows the idea of all similar users to candidate books for the input user. Then the values are sorted and top 20 books are recommended to the user
