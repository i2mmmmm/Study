from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.metrics.pairwise import cosine_similarity
import pandas as pd

# 단어 목록
words = ["apple", "orange", "fruit", "banana", "grape"]

# 코사인 유사도 계산
vectorizer = TfidfVectorizer()
X = vectorizer.fit_transform(words)
similarity_matrix = cosine_similarity(X)

# 가장 유사한 단어 찾기
most_similar = similarity_matrix[0].argsort()[-2]  # 첫 번째 단어와 가장 유사한 단어 찾기

print(f"가장 유사한 단어: {words[most_similar]}")



excel

Function CosineSimilarity(str1 As String, str2 As String) As Double
    Dim dict1 As Object, dict2 As Object
    Dim word As Variant
    Dim dotProduct As Double, norm1 As Double, norm2 As Double
    Set dict1 = CreateObject("Scripting.Dictionary")
    Set dict2 = CreateObject("Scripting.Dictionary")

    ' 단어들로 분리하여 각 단어의 빈도를 셈
    For Each word In Split(LCase(str1), " ")
        dict1(word) = dict1(word) + 1
    Next word

    For Each word In Split(LCase(str2), " ")
        dict2(word) = dict2(word) + 1
    Next word

    ' 내적 계산
    dotProduct = 0
    For Each word In dict1.Keys
        If dict2.exists(word) Then
            dotProduct = dotProduct + dict1(word) * dict2(word)
        End If
    Next word

    ' 벡터의 크기 계산
    norm1 = 0
    norm2 = 0
    For Each word In dict1.Keys
        norm1 = norm1 + dict1(word) ^ 2
    Next word
    For Each word In dict2.Keys
        norm2 = norm2 + dict2(word) ^ 2
    Next word

    ' 코사인 유사도 계산
    CosineSimilarity = dotProduct / (Sqr(norm1) * Sqr(norm2))
End Function

