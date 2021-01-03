---  
toc: true
toc_label: "Context-Execution"
toc_icon: "cog"

categories:
  - Javascript
tags:
  - Javascript 핵심 개념 알아보기 - JS Flow
  - Javascript
  - 
---   
# 실행컨텍스트 : '실행에 필요한' 코드 흐름상의 배경이 되는 조건 / 환경   

## 함수 or 전역공간을 실행할 때 필요한 조건 및 환경정보 를 담은 객체  

```javascript  
var a = 1;
function outer() {
	console.log(a);
	
	function inner() {
		console.log(a);
		var a = 3;
	}
	inner();
	console.log(a);
}
outer();
console.log(a);
```  

# call stack  
현재 어떤 함수가 동작하고 있는지, 다음에 어떤 함수가 호출되어야 하는 지 등을 제어하는 자료구조!  

>  전역 컨텍스트 > outer > inner  

# Lexical Environment  
## environmentRecord : 현재 문맥의 식별자 정보  
ㄴ HOISTING  (식별자 정보를 실행컨텍스트의 맨 위로 끌어올리다.)  

함수는 전체를 끌어올림. 변수는 변수만 위로 끌어올려짐.  
environmentRecord의 정보를 수집함.  

## outerEnvironmentReference : 현재 문맥에 관련이 있는 '외부' 식별자 정보  
ㄴSCOPE CHAIN ( 외부 변수는 가져올수 있으나 내부 변수는 외부에서 사용불가)  : 가장 가까운 컨텍스트 내부 변수를 가져오는 행위  

손코딩하고 실행결과 및 실행콘텍스트 순서 직접 해보기!



