This file describes the data for COMP30027 2019S1, Project 2. It has been collected directly from Twitter (https://twitter.com) using the Twitter API (https://developer.twitter.com/en/docs.html) for research purposes, in line with the Twitter Terms of Service.

This tarball contains 13 files:

- train-raw.tsv: This is a file of 103364 training instances, one per line. Each one contains the raw text of a tweet. The format of the file is as follows:
    Instance_ID TAB Location TAB Text
  A detailed description of the fields:
    Instance_ID: a number from 1 to 103364, prefixed by the character "1" - so "11" to "1103364"; it should have no significance otherwise
    Location: this is one of the following classes: {Sydney, Melbourne, Brisbane, Perth};
    Text: this is the raw text of the message; it is enclosed in quotation marks, but has otherwise not been altered (much) from the Twitter dump; it may contain any (unescaped) characters between the quotation marks, including the quotation mark character, comma character, and class labels, in any character encoding.

- train-top10.csv: This is a file of 103364 training instances, one per line. Each one is a CSV representation of some token frequencies within the blog text. The format of the file is as follows:
    Instance_ID,List_of_token_frequencies,Class
  A detailed description of the fields:
    Instance_ID: a number from 1 to 103364, prefixed by the character "1" - so "11" to "1103364"; it should have no significance otherwise
    List_of_token_frequencies: The frequency within the tweet text (case-folded, and stripped of non-alphabetic characters) of the 34 tokens whose presence/absence corresponded to one of the top 10 Mutual Information/Chi-Square attributes for one of the four classes.
    Class: this is one of the following classes: {Sydney, Melbourne, Brisbane, Perth}.

- train-top50.csv: This is a file of 103364 training instances, one per line. It is identical to train-top10.csv, except that there are 185 tokens whose frequency is recorded, corresponding to one of the top 50 Mutual Information/Chi-Square attribute for one of the four classes.

- train-top100.csv: This is a file of 103364 training instances, one per line. It is identical to train-top10.csv, except that there are 366 tokens whose frequency is recorded, corresponding to one of the top 100 Mutual Information/Chi-Square attribute for one of the four classes.

- dev-raw.tsv: This is a file of 37316 development instances, one per line. Its format is otherwise identical to the format of train-raw.tsv, except as follows:
    Instance_ID: a number from 1 to 37316, prefixed by the character "2" - so "21" to "237316"

- dev-top10.csv: This is a file of 37316 development instances, one per line. Its format is identical to the format of train-top10.csv, except as follows:
    Instance_ID: a number from 1 to 45332, prefixed by the character "2" - so "21" to "237316"

- dev-top50.csv: This is a file of 37316 development instances, one per line. Its format is identical to the format of train-top50.csv, except as follows:
    Instance_ID: a number from 1 to 45332, prefixed by the character "2" - so "21" to "237316"

- dev-top100.csv: This is a file of 37316 development instances, one per line. Its format is identical to the format of train-top100.csv, except as follows:
    Instance_ID: a number from 1 to 45332, prefixed by the character "2" - so "21" to "237316"

- test-raw.tsv: This is a file of 108148 test instances, one per line. Its format is identical to the format of train-raw.tsv, except that the content of the following field has been replaced by "?":
    Location

- test-top10.csv: This is a file of 108148 test instances, one per line. Its format is identical to the format of train-top10.csv, except as follows:
    Instance_ID: a number from 1 to 108148, prefixed by the character "3" - so "31" to "3108148"
    Class: all instances have been recorded as "?"

- test-top50.csv: This is a file of 108148 development instances, one per line. Its format is identical to the format of train-top50.csv, except as follows:
    Instance_ID: a number from 1 to 108148, prefixed by the character "3" - so "31" to "3108148"
    Class: all instances have been recorded as "?"

- test-top100.csv: This is a file of 108148 development instances, one per line. Its format is identical to the format of train-top100.csv, except as follows:
    Instance_ID: a number from 1 to 108148, prefixed by the character "3" - so "31" to "3108148"
    Class: all instances have been recorded as "?"

- README.txt: This is the file you are currently reading.


The features in the {train,dev,test}-{top10,top50,top100} CSV files were determined as follows:
   - the tweets in train-raw.tsv were case-folded, and non-alphabetic characters were removed (tr/[A-Z]/[a-z]/;s/[^a-z ]//g)
   - 184674 different alphabetical "word" types were identified
   - for each class, predictive features were automatically identified based on the presence of the "word" (n.b. not the frequency):
     - the top 10/50/100 types, according to Mutual Information
     - the top 10/50/100 types, according to Chi-Square
   - In the case of top10, these 80 "word" types were sorted, and duplicates were removed, leaving 34 to be used as features
   - In the case of top50, these 400 "word" types were sorted, and duplicates were removed, leaving 185 to be used as features
   - In the case of top100, these 800 "word" types were sorted, and duplicates were removed, leaving 366 to be used as features
