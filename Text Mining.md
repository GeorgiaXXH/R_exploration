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
    data(stopwords)
    Stopwords=stopwords
    Stopswords$word=Hsmic::capitalize(stopwords$word)
    the output of unnest_tokens %>% anti_join(stopwords)%>%anti_join(Stopwords)         
remove stop words such as "the", "of", "a/an"......and the A, The version of them.
# C."fuzzyjoin"
## 1.stringdist_join(df1,df2,mode="left/inner..",by="colname",max.dist=0.1,)
# Little tricks:
## 1. keep the max records within each group
        slice_max(order_by=``,n=1) 
## 2. realize group_concat in sql in R
        group_by() %>% summarise(``=toString(``))
## 3. capitalize：Hsmic::capitalize
## 4. stringr::str_to_title() 
To capitalize every word in the sentence
## 5. regular expression
### 1) parenthesis and context within 
    gsub("\\s*\\([^\\)]+\\)","",string)
### 2) ,and content behind
    gsub(",[:alpha:]*","",string)
### 3) ,and content behind
    strsplit(string,pattern="[aA]\\s[Cc]ommunication\\s(to|from)\\s")[[1]][2]
To extract the content after "a/A C/communication from/to ".
## 6.countif in R 
    sum(logic)
## 7.use multiple variables to filter unique rows but keeping all the columns
    distinct(.,var1,var2,.keep_all=T)
