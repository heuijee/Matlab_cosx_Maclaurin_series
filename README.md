# Matlab_cosx_Maclaurin_series
## 1. Maclaurin series
함수를 멱급수 형태로 나타냈을때의 모습

![f(x)](https://user-images.githubusercontent.com/58385691/98422679-bb710f00-20cf-11eb-9d49-78f2bf13bbae.JPG)

a=0일때의 형태를 매클로린 급수라고 한다.

## 2. Matlab으로 cos 함수의 매클로린 급수를 표현한 코드

함수이름, 변수 정의
```
function [cosx,ea,iter] = cosx_Maclaurin_series(x,es,maxit)
```
input: x, es(stopping criterion), maxit(maximum iterations)
output: fx(estimated value), ea(approximate relative error), iter(number of iterations)

    if nargin < 2|isempty(es),es = 0.0001; end

    if nargin < 3|isempty(maxit),maxit = 50; end
    
    iter=1; sol=1; ea=100;

변수의 초기값 설정(default)

    while (1)
    
무한 루프를 돌며
        
        solold=sol;
        
        sol=sol+(-1)^(iter)*x^(2*iter)/factorial(2*iter);

각 iteration마다의 추정값을 계산한뒤 갱신해준다.        
        
        iter=iter+1;
    
    if sol ~=0
        
        ea=abs((sol-solold)/sol)*100;
        
   approximate relative error의 기본식을 정의해준다.
    
    end
    
    if ea <= es | iter >=maxit , break, end

approximate relative error가 앞서 정해둔 값보다 작아지면 루프를 break한다.
    
    end
    
```
