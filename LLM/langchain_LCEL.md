```
from langchain_core.runnables import (
    RunnableParallel,
    RunnablePassthrough,
    RunnableLambda,
)
```


```
model = ChatOpenAI()

chain1 = {"country" : RunnablePassthrough()} | prompt1 | model
chain2 = {"country" : RunnablePassthrough()} | prompt2 | model

map_chain = RunnableParallel(a=chain1, b=chain2)
map_chain.invoke("대한민국") ## 결과 확인해보기

def combine_text(text):
    return text{"a"}.content + " " + text{"b"}.content

final_chain = {
    map_chain
    | {"info"| RunnableLambda(combine_text)} 
    | PromptTemplate.from_template("다음의 내용을 자연스럽게 교정해줘. 이모티콘을 적절한 곳에 추가해줘:\n{info}")  
    | model


final_chain.invoke("대한민국") ## 결과 확인해보기
```
