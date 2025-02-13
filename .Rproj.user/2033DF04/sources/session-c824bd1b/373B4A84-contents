library(tidytext)
library(tidyverse)
library(ggplot2)

top_ten <- read.csv("data/top_ten.csv")

#learning how to split into words
abstract <- top_ten$Abstract[1]
abstract_df <- tibble(line = 1, text = abstract)
abstract_df %>% unnest_tokens(word, text)

#splitting into tidy format words for all abstracts and removing stop words (like "the")
data("stop_words")
all_abs <- top_ten %>% 
  unnest_tokens(word, Abstract) %>% 
  anti_join(stop_words)

#counting and plotting the most common words
all_abs %>% 
  count(word, sort = TRUE) %>% 
  filter(n > 5) %>% 
  mutate(word = reorder(word, n)) %>% 
  ggplot(aes(n, word)) + 
  geom_col() +
  labs(y = NULL)

