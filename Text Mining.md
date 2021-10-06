# A. "tokenizer" package
## 1. The text can be truncated into paragraph, sentence, word and single character. 
## 2. The output would be list.
# B. "tidytext"
## 1. unnest_tokens(tokentype,colname of interest)
The df should be converted into tibble using dplyr::tibble(df) and only keep the id and column of interests.
Tokentype is word by default, but could be characters, n-grams, sentences, lines, paragraphs, or separation around a regex pattern
to_lower=TRUE is by default
The output would be one word in one row with original id keeps the same.
## 2.anti_join()
` data(stopwords) \
anti_join(the output of unnest_tokens)`         
remove stop words such as "the", "of", "a/an"......

