# python

### shutil
  - Standard library to manage file and directory
  - copy, rmtree, move, make_archive, unpack_archive
    
    ```python
    import shutil

    # copy file
    shutil.copy("report.pdf", "backup/report_copy.pdf")
    
    # copy dir
    shutil.copytree("data/", "data_backup/")
    
    # rm dir
    shutil.rmtree("temp/")
    
    # mv file
    shutil.move("temp/report.pdf", "archive/report.pdf")
    
    # compress dir
    shutil.make_archive("archive_backup", "zip", "archive/")
    
    # decompress
    shutil.unpack_archive("archive_backup.zip", "restored/")
    ```
    clearing
    ```python
    shutil.rmtree(UPLOAD_DIR, ignore_errors=True)
    os.makedirs(UPLOAD_DIR, exist_ok=True)
    ```

### os

  - file path managing
  - file system control
  - environment variables
    
    ```python
    import os
  
    os.path.join(DIR_PATH, "file.txt")
    
    os.makedirs(path, exist_ok=True)
    
    os.remove(path)
    
    os.listdir(path)
    
    os.path.exists(path)
    
    os.getenv("KEY")
    ```

### collections

  - a module in python standard library.
  - provide helpful data structures beyond the basic(`list`, `dict`, `tuple`)
  - efficient and simlplify for complex data struture

    ```python
    lst = ["a", "b", "a", "c", "a", "b"]
    → {'a': 3, 'b': 2, 'c': 1}
    ```
    - without collections
    ```python
    for item in lst:
    if item in count:      # <class 'dict'>
        count[item] += 1
    else:
        count[item] = 1
                          # d = {}
                          # d["a"] += 1  # ❌ KeyError: 'a'
    
    print(count)  # {'a': 3, 'b': 2, 'c': 1}

    most_common = sorted(count.items(), key=lambda x: x[1], reverse=True)
    print(count)          # {'a': 3, 'b': 2, 'c': 1}
    print(most_common[:1])  # [('a', 3)]
    ```
    - with collections.Counter
    ```python
    from collections import Counter

    lst = ["a", "b", "a", "c", "a", "b"]
    count = Counter(lst)    # <class 'collections.Counter> -> inherited dict class
    print(count)  # Counter({'a': 3, 'b': 2, 'c': 1})

    # most_common(n)
    print(count.most_common(1))  # [('a', 3)]
    print(count.most_common(2))  # [('a', 3), ('b', 2)]
    ```
    - with collections.defaultdict
    ```python
    from collections import defaultdict
                                # <class 'collections.defaultdict'>
    count = defaultdict(int)    # set default as int 0
    for item in lst:
        count[item] += 1
    
    print(count)  # defaultdict(<class 'int'>, {'a': 3, 'b': 2, 'c': 1})

    most_common = sorted(count.items(), key=lambda x: x[1], reverse=True)
    print(dict(count))     # {'a': 3, 'b': 2, 'c': 1}
    print(most_common[:1]) # [('a', 3)]
    ```

### re
  - python standard library to enable to use **Regular Expression**
  - split, detect, find pattern in string
  
    ```python
    import re
    
    # detect numeric
    re.findall(r'\d+', "abc123def456")
  
    # split string
    re.split(r'\n+', text)
  
    # search email type pattern
    re.search(r'\w+@\w+\.\w+', s)
  
    # search string pattern such as section header
    re.search(r'\b\d+(\.\d+)*\s+[^\n]+', text)    # 1. Introduction / 2.3. Methods
    ```


### nltk
  - Natural Language Toolkit
  - library for **NLP**

    - nltk.stem
    ```python
    import nltk
    from nltk.stem import WordNetLemmatizer, PorterStemmer

    nltk.download('wordnet')     # download words dictionary(WordNet) for lemmatization
    
    lemmatizer = WordNetLemmatizer()
    
    lemmatizer.lemmatize("running", pos="v")  # → 'run', default pos = n , "am", "are", "is" → "be"
    print(lemmatizer.lemmatize("flies", pos="v"))    # 'fly'
    print(lemmatizer.lemmatize("universities", pos="n"))  # 'university'
    
    stemmer = PorterStemmer()    # Stemming: trun words into root form []
    print(stemmer.stem("running"))   # 'run'
    print(stemmer.stem("flies"))     # 'fli' ❌
    print(stemmer.stem("universities"))  # 'univers' ❌
    ```

    - nltk.tokenize
    ```python
    import nltk
    from nltk.tokenize import word_tokenize, sent_tokenize
    
    nltk.download('punkt')

    sent_tokenize("Hello. How are you?")  
    # → ['Hello.', 'How are you?']

    sentence = "This is an example sentence."
    tokens = word_tokenize(sentence)
    print(tokens)
    # ['This', 'is', 'an', 'example', 'sentence', '.']
    ```

    - nltk.corpus 
    ```python
    from nltk.corpus import stopwords
    
    nltk.download('stopwords')   # meaningless words, used for grammatic reason [the, is, in, at]

    stop_words = set(stopwords.words('english'))

    words = ["this", "is", "an", "example"]
    filtered = [w for w in words if w not in stop_words]
    
    print(filtered)  # ['example']
    ```






#### Type Hint
  ```python
  def process_uploaded_pdfs(pdf_dir):
  def process_uploaded_pdfs(pdf_dir: str) -> List[dict]:
  ```









  
