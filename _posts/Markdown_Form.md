# Markdown 문법 알아보기  
> Update : 2020-11-12

이 글은 devinlife의 git page 블로그 따라하기 시리즈를 보며 md 파일 작성법을 익히기 위해서 작성하였음.  
> Refer : https://devinlife.com/howto%20github%20pages/markdown-syntax/  

## 1. markdown 특징  
markdown은 github에서 md파일 생성하면서 알고 있었던 언어임.   
github repo 생성 시에 README.md 파일을 보았던 사람이라면 알고 있는 언어일거라고 생각함.  

텍스트 기반으로 작성되며 규무니 같은 경우에는 온라인 md editor 사이트 들을 자주 이용하는 편임 ^ㅠ^ (stackedit.io)  

## 2. markdown 문법  
마크다운 언어는 줄바꿈을 인식하지 않아서 space bar 2번을 통해서 줄바꿈을 하며, 여러가지 강조 표시가 있다고 함.  
1. *강조1 인가 ?*  
2. _이렇게 강조2 도 되는건가 ?_ 
3. **강조3 예시 인건가**  
4. __double underbar 강조 4예시__
5. ~~cancelline예시 5번~~  


### 2.2 글머리 종류.  
차례대로 H1 tag ~ H6 tag 까지 '#' 의 개수로 html로 바꿔주는 듯 함.  
(h2 태그는 지킬 이 테마에서 우측에 On this page를 지원하게 되어있음)  

# This is a H1  
## This is a H2  
### This is a H3  
#### This is a H4  
##### This is a H5  
###### This is a H6    


### 2.3 인용
인용문 역시 '>' 문자를 이용해서 단계별로 인용 가능함 계속되는듯(?)
> 인용 하는 규무늬  
>> 인용인용 하는 규무늬  
>>>인용인용인용 하는 규무늬   
>>>>인용인용인용인용 하는 규무늬  

### 2.4 비정렬 목록
```
* 과자
  * 라면
    * 사탕
```
```
+ 과자
  + 라면
    + 사탕
```
```
- 과자
  - 라면
    - 사탕
```

### 2.5 코드 인용
코드 인용 같은 경우에 키보드 1 옆에 ` 문자 세개로 표현함
```
const doSomething = () => {
   ...
}
```
- 루비
```ruby
require 'redcarpet'
markdown = Redcarpet.new("Hello World!")
puts markdown.to_html
```  
- C  
```C
int main() {
  int y = SOME_MACRO_REFERENCE;
  int x = 5 + 6;
  cout << "Hello World! " << x << std::endl();
}
```
- Python
```python
s = "Python syntax highlighting"
print(s)
```
## 2.7 링크  
```
- 링크 표시법 : [Title](link)
```
[규문이 티스토리 링크](https://kyumoonhan.tistory.com/)

- 주소 직접 표시법
```
<https://kyumoonhan.tistory.com/>
```
<https://kyumoonhan.tistory.com/>  

## 2.8 이미지 삽입
```
![](https://gksrbans.github.io/assets/images/pikachu.png)  
```
![](https://gksrbans.github.io/assets/images/pikachu.png)  

```
![내 프로필 사진](![](https://gksrbans.github.io/assets/images/pikachu.png "내 프로필"){: .align-center}
```


![내 프로필 사진](![](https://gksrbans.github.io/assets/images/pikachu.png){: .align-center}  

## 2.9 표 만들기
- 표 내용 중앙 정렬 (' |:---:|')
```
| 항목 | 가격 | 개수 |
|:---:|:----:|:----|
| 라면 | 800원 | 10개 |
| 과자 | 900원 | 20개 |
```
| 항목 | 가격 | 개수 |
|:---:|:----:|:----|
| 라면 | 800원 | 10개 |
| 과자 | 900원 | 20개 |
  
  
- 표 내용 왼쪽 정렬 (' |:---|')
```
| 항목 | 가격 | 개수 |
|:----|:----:|----:|
| 라면 | 800원 | 10개 |
| 과자 | 900원 | 20개 |
```

| 항목 | 가격 | 개수 |
|:----|:----:|----:|
| 라면 | 800원 | 10개 |
| 과자 | 900원 | 20개 |


> Reference : https://devinlife.com/howto%20github%20pages/markdown-syntax/
