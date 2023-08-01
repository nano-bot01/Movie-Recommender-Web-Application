# Movie Recommendation System 


Movie Recommendation System based on TfidfVectorizer and cosine similarity function 

### Cosine Similarity : 
   Cosine similarity is a measure used to determine the similarity between two vectors in a high-dimensional space. It calculates the cosine of the angle between the two vectors and returns a value between -1 and 1.

![image](https://user-images.githubusercontent.com/78251168/227769415-0367c033-f3fe-4b32-bf5d-36d05879e3fc.png)


In simpler terms, imagine two vectors as arrows pointing in a particular direction. The angle between these arrows can be used to measure their similarity. If the arrows are pointing in the same direction, then the angle between them is 0 and the cosine similarity is 1. If the arrows are perpendicular, the cosine similarity is 0, and if the arrows are pointing in opposite directions, the cosine similarity is -1.

Cosine similarity is commonly used in information retrieval and text mining to compare the similarity of documents or text snippets based on the frequency of words. It is also used in recommendation systems to find similar items or products.

### TfidfVectorizer *"Term Frequency-Inverse Document Frequency Vectorizer"*  : 
   TfidfVectorizer is a popular method used for text analysis and is often used in natural language processing (NLP). It stands for "Term Frequency-Inverse Document Frequency Vectorizer".

In simpler terms, TfidfVectorizer is a tool that converts a collection of documents into a matrix of features that can be used to analyze the text. It takes into account the frequency of each word in a document and in the entire corpus (collection of documents) to determine the importance of each word.

The "term frequency" refers to the number of times a word appears in a particular document. The "inverse document frequency" measures how important a word is across all the documents in the corpus. Words that are common across all documents will have a lower IDF value, while words that are unique to a particular document will have a higher IDF value.

TfidfVectorizer creates a sparse matrix representation of the text, which can be used for further analysis, such as clustering, classification, and information retrieval. It is commonly used in applications such as search engines, content recommendation systems, and sentiment analysis.

![Screenshot 2023-07-24 123420](https://github.com/nano-bot01/Movie-Recommender-Web-Application/assets/78251168/e86a4319-c187-45d3-bb3e-fbde6b622357)



## Recommendation function 
```
def recommend(name):
  find_close_match = difflib.get_close_matches(movie_name, list_of_all_titles)
  
  try:
    close_match = find_close_match[0]
  except IndexError:
    close_match = 'null'
    print("No result found with this title")
    return 
  index_of_movie = dataset[dataset.title == close_match]['index'].values[0]
  score = list(enumerate(similarity[index_of_movie]))
  sorted_list = sorted(score, key = lambda x:x[1], reverse = True)


  print("Movies Results : \n")

  i = 1

  for movie in sorted_list:
    index = movie[0]
    title_of_movie = dataset[dataset.index == index]['title'].values[0]
    if(i<=5):
      print(i, '. ', title_of_movie)
      i += 1
```

```
movie_name = input('Enter your favourite movie name : ')

recommend(movie_name)
```



### Collaborated by : [Ankit Nainwal](https://github.com/nano-bot01)

### Please ⭐⭐⭐⭐
