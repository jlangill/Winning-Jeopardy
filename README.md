# Winning-Jeopardy
Analyzing text while figuring out strategies to win at Jeopardy.

Read the dataset into a Dataframe called jeopardy using Pandas.
Print out the first 5 rows of jeopardy.
Print out the columns of jeopardy using jeopardy.columns.
Some of the column names have spaces in front.
Remove the spaces in each item in jeopardy.columns.
Assign the result back to jeopardy.columns to fix the column names in jeopardy.
Make sure you pay close attention to the format of each column.

Write a function to normalize questions and answers. It should:
Take in a string.
Convert the string to lowercase.
Remove all punctuation in the string.
Return the string.
Normalize the Question column.
Use the Pandas apply method to apply the function to each item in the Question column.
Assign the result to the clean_question column.
Normalize the Answer column.
Use the Pandas apply method to apply the function to each item in the Answer column.
Assign the result to the clean_answer column.

Write a function to normalize dollar values. It should:
Take in a string.
Remove any punctuation in the string.
Convert the string to an integer.
If the conversion has an error, assign 0 instead.
Return the integer.
Normalize the Value column.
Use the Pandas apply method to apply the function to each item in the Value column.
Assign the result to the clean_value column.
Use the pandas.to_datetime function to convert the Air Date column to a datetime column.

Write a function that takes in a row in jeopardy, as a Series. It should:
Split the clean_answer column on the space character (), and assign to the variable split_answer.
Split the clean_question column on the space character (), and assign to the variable split_question.
Create a variable called match_count, and set it to 0.
If the is in split_answer, remove it using the remove method on lists. The is commonly found in answers and questions, but doesn't have any meaningful use in finding the answer.
If the length of split_answer is 0, return 0. This prevents a division by zero error later.
Loop through each item in split_answer, and see if it occurs in split_question. If it does, add 1 to match_count.
Divide match_count by the length of split_answer, and return the result.
Count how many times terms in clean_answer occur in clean_question.
Use the Pandas apply method on Dataframes to apply the function to each row in jeopardy.
Pass the axis=1 argument to apply the function across each row.
Assign the result to the answer_in_question column.
Find the mean of the answer_in_question column using the mean method on Series.
Write up a markdown cell with a short explanation of how finding this mean might influence your studying strategy for Jeopardy.

Create an empty list called question_overlap.
Create an empty set called terms_used.
Use the iterrows Dataframe method to loop through each row of jeopardy.
Split the clean_question column of the row on the space character (), and assign to split_question.
Remove any words in split_question that are less than 6 characters long.
Set match_count to 0.
Loop through each word in split_question.
If the term occurs in terms_used, add 1 to match_count.
Add each word in split_question to terms_used using the add method on sets.
If the length of split_question is greater than 0, divide match_count by the length of split_question.
Append match_count to question_overlap.
Assign question_overlap to the question_overlap column of jeopardy.
Find the mean of the question_overlap column and print it.
Look at the value, and think about what this might mean for questions being recycled. Write up your thoughts in a markdown cell.

Create a function that takes in a row from a Dataframe, and:
If the clean_value column is greater than 800, assign 1 to value.
Otherwise, assign 0 to value.
Return value.
Determine which questions are high and low value.
Use the Pandas apply method on Dataframes to apply the function to each row in jeopardy.
Pass the axis=1 argument to apply the function across each row.
Assign the result to the high_value column.
Create a function that takes in a word, and:
Assigns 0 to low_count.
Assigns 0 to high_count.
Loops through each row in jeopardy using the iterrows method.
Split the clean_question column on the space character ().
If the word is in the split question:
If the high_value column is 1, add 1 to high_count.
Else, add 1 to low_count.
Returns high_count and low_count. You can return multiple values by separating them with a comma.
Create an empty list called observed_expected.
Convert terms_used into a list using the list function, and assign the first 5 elements to comparison_terms.
Loop through each term in comparison_terms, and:
Run the function on the term to get the high value and low value counts.
Append the result of running the function (which will be a list) to observed_expected.

Find the number of rows in jeopardy where high_value is 1, and assign to high_value_count.
Find the number of rows in jeopardy where high_value is 0, and assign to low_value_count.
Create an empty list called chi_squared.
Loop through each list in observed_expected.
Add up both items in the list (high and low counts) to get the total count, and assign to total.
Divide total by the number of rows in jeopardy to get the proportion across the dataset. Assign to total_prop.
Multiply total_prop by high_value_count to get the expected term count for high value rows.
Multiply total_prop by low_value_count to get the expected term count for low value rows.
Use the scipy.stats.chisquare function to compute the chi-squared value and p-value given the expected and observed counts.
Append the results to chi_squared.
Look over the chi-squared values and the associated p-values. Are there any statistically significant results? Write up your thoughts in a markdown cell.

