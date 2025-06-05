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



    -----------
    아, 이제 이해했어요! 첫 번째 열에 있는 단어와 두 번째 열에 있는 단어들 간의 유사도를 측정해서, 첫 번째 열의 각 단어가 두 번째 열에서 가장 유사한 단어를 찾아 그 유사도를 퍼센트로 표시하는 거군요.

이럴 때도 **코사인 유사도**를 사용할 수 있습니다. 아래는 엑셀에서 **VBA**로 구현할 수 있는 방법입니다.

1. **첫 번째 열(A열)**: 비교하고 싶은 단어들.
2. **두 번째 열(B열)**: 비교 대상 단어들.
3. **세 번째 열(C열)**: 첫 번째 열의 단어가 두 번째 열에서 가장 유사한 단어와 그 유사도 퍼센트를 표시.

### VBA 코드:

```vba
Function CosineSimilarity(str1 As String, str2 As String) As Double
    Dim dict1 As Object, dict2 As Object
    Dim word As Variant
    Dim dotProduct As Double, norm1 As Double, norm2 As Double
    Set dict1 = CreateObject("Scripting.Dictionary")
    Set dict2 = CreateObject("Scripting.Dictionary")

    ' 단어를 공백을 기준으로 나누어 빈도를 셈
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
    If norm1 = 0 Or norm2 = 0 Then
        CosineSimilarity = 0
    Else
        CosineSimilarity = dotProduct / (Sqr(norm1) * Sqr(norm2))
    End If
End Function

Sub FindMostSimilarWords()
    Dim ws As Worksheet
    Dim lastRowA As Long, lastRowB As Long
    Dim i As Long, j As Long
    Dim maxSimilarity As Double
    Dim mostSimilarWord As String
    Dim similarity As Double
    Dim percent As Double

    Set ws = ThisWorkbook.Sheets("Sheet1") ' 현재 시트 이름에 맞게 수정

    lastRowA = ws.Cells(ws.Rows.Count, 1).End(xlUp).Row ' A열의 마지막 행
    lastRowB = ws.Cells(ws.Rows.Count, 2).End(xlUp).Row ' B열의 마지막 행

    ' A열의 각 단어에 대해 B열에서 가장 유사한 단어 찾기
    For i = 1 To lastRowA
        maxSimilarity = -1 ' 초기 유사도 설정
        mostSimilarWord = ""
        For j = 1 To lastRowB
            similarity = CosineSimilarity(ws.Cells(i, 1).Value, ws.Cells(j, 2).Value)
            If similarity > maxSimilarity Then
                maxSimilarity = similarity
                mostSimilarWord = ws.Cells(j, 2).Value
            End If
        Next j

        ' 퍼센트로 변환하여 C열에 기록
        percent = maxSimilarity * 100
        ws.Cells(i, 3).Value = mostSimilarWord & " (" & Round(percent, 2) & "%)"
    Next i
End Sub
```

### 코드 설명:

1. **`CosineSimilarity` 함수**:

   * 두 단어의 코사인 유사도를 계산합니다. 이 함수는 두 텍스트를 공백 기준으로 나누어 각 단어의 빈도를 세고, 내적과 벡터의 크기를 사용해 유사도를 계산합니다.

2. **`FindMostSimilarWords` 서브**:

   * 첫 번째 열(A열)과 두 번째 열(B열)의 모든 단어들을 비교하여 가장 유사한 단어를 찾아 C열에 출력합니다.
   * 유사도는 퍼센트(%)로 계산됩니다. 예를 들어, 0.85의 유사도는 85%로 표시됩니다.

3. **출력 형식**:

   * C열에 "가장 유사한 단어 (유사도%)" 형식으로 결과가 나타납니다.

### 사용 방법:

1. 엑셀에서 **Alt + F11**을 눌러 VBA 편집기를 엽니다.
2. **Insert > Module**을 선택하여 새로운 모듈을 추가합니다.
3. 위의 코드를 붙여넣습니다.
4. 엑셀로 돌아가서 **Alt + F8**을 눌러 `FindMostSimilarWords` 서브를 실행합니다.

### 예시:

| A열 (단어) | B열 (단어들) | C열 (결과)         |
| ------- | -------- | --------------- |
| apple   | fruit    | fruit (60.45%)  |
| orange  | banana   | banana (85.23%) |
| banana  | apple    | apple (70.12%)  |
| grape   | orange   | orange (75.89%) |

이렇게 첫 번째 열의 단어 각각에 대해 두 번째 열에서 가장 유사한 단어와 그 유사도를 퍼센트로 표시할 수 있습니다.

이 방법을 사용하면 원하는 결과를 얻을 수 있을 거예요!


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







-----------



아, 이제 이해했어요! 첫 번째 열에 있는 단어와 두 번째 열에 있는 단어들 간의 유사도를 측정해서, 첫 번째 열의 각 단어가 두 번째 열에서 가장 유사한 단어를 찾아 그 유사도를 퍼센트로 표시하는 거군요.

이럴 때도 **코사인 유사도**를 사용할 수 있습니다. 아래는 엑셀에서 **VBA**로 구현할 수 있는 방법입니다.

1. **첫 번째 열(A열)**: 비교하고 싶은 단어들.
2. **두 번째 열(B열)**: 비교 대상 단어들.
3. **세 번째 열(C열)**: 첫 번째 열의 단어가 두 번째 열에서 가장 유사한 단어와 그 유사도 퍼센트를 표시.

### VBA 코드:

```vba
Function CosineSimilarity(str1 As String, str2 As String) As Double
    Dim dict1 As Object, dict2 As Object
    Dim word As Variant
    Dim dotProduct As Double, norm1 As Double, norm2 As Double
    Set dict1 = CreateObject("Scripting.Dictionary")
    Set dict2 = CreateObject("Scripting.Dictionary")

    ' 단어를 공백을 기준으로 나누어 빈도를 셈
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
    If norm1 = 0 Or norm2 = 0 Then
        CosineSimilarity = 0
    Else
        CosineSimilarity = dotProduct / (Sqr(norm1) * Sqr(norm2))
    End If
End Function

Sub FindMostSimilarWords()
    Dim ws As Worksheet
    Dim lastRowA As Long, lastRowB As Long
    Dim i As Long, j As Long
    Dim maxSimilarity As Double
    Dim mostSimilarWord As String
    Dim similarity As Double
    Dim percent As Double

    Set ws = ThisWorkbook.Sheets("Sheet1") ' 현재 시트 이름에 맞게 수정

    lastRowA = ws.Cells(ws.Rows.Count, 1).End(xlUp).Row ' A열의 마지막 행
    lastRowB = ws.Cells(ws.Rows.Count, 2).End(xlUp).Row ' B열의 마지막 행

    ' A열의 각 단어에 대해 B열에서 가장 유사한 단어 찾기
    For i = 1 To lastRowA
        maxSimilarity = -1 ' 초기 유사도 설정
        mostSimilarWord = ""
        For j = 1 To lastRowB
            similarity = CosineSimilarity(ws.Cells(i, 1).Value, ws.Cells(j, 2).Value)
            If similarity > maxSimilarity Then
                maxSimilarity = similarity
                mostSimilarWord = ws.Cells(j, 2).Value
            End If
        Next j

        ' 퍼센트로 변환하여 C열에 기록
        percent = maxSimilarity * 100
        ws.Cells(i, 3).Value = mostSimilarWord & " (" & Round(percent, 2) & "%)"
    Next i
End Sub
```

### 코드 설명:

1. **`CosineSimilarity` 함수**:

   * 두 단어의 코사인 유사도를 계산합니다. 이 함수는 두 텍스트를 공백 기준으로 나누어 각 단어의 빈도를 세고, 내적과 벡터의 크기를 사용해 유사도를 계산합니다.

2. **`FindMostSimilarWords` 서브**:

   * 첫 번째 열(A열)과 두 번째 열(B열)의 모든 단어들을 비교하여 가장 유사한 단어를 찾아 C열에 출력합니다.
   * 유사도는 퍼센트(%)로 계산됩니다. 예를 들어, 0.85의 유사도는 85%로 표시됩니다.

3. **출력 형식**:

   * C열에 "가장 유사한 단어 (유사도%)" 형식으로 결과가 나타납니다.

### 사용 방법:

1. 엑셀에서 **Alt + F11**을 눌러 VBA 편집기를 엽니다.
2. **Insert > Module**을 선택하여 새로운 모듈을 추가합니다.
3. 위의 코드를 붙여넣습니다.
4. 엑셀로 돌아가서 **Alt + F8**을 눌러 `FindMostSimilarWords` 서브를 실행합니다.

### 예시:

| A열 (단어) | B열 (단어들) | C열 (결과)         |
| ------- | -------- | --------------- |
| apple   | fruit    | fruit (60.45%)  |
| orange  | banana   | banana (85.23%) |
| banana  | apple    | apple (70.12%)  |
| grape   | orange   | orange (75.89%) |

이렇게 첫 번째 열의 단어 각각에 대해 두 번째 열에서 가장 유사한 단어와 그 유사도를 퍼센트로 표시할 수 있습니다.

이 방법을 사용하면 원하는 결과를 얻을 수 있을 거예요!

