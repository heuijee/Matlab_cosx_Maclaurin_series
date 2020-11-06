# Matlab_cosx_Maclaurin_series
#1. Maclaurin series

![f(x)](https://user-images.githubusercontent.com/58385691/98422679-bb710f00-20cf-11eb-9d49-78f2bf13bbae.JPG, width=300)


```
function [cosx,ea,iter] = cosx_Maclaurin_series(x,es,maxit)
```
    if nargin < 2|isempty(es),es = 0.0001; end

    if nargin < 3|isempty(maxit),maxit = 50; end
    
    iter=1; sol=1; ea=100;

    while (1)
        
        solold=sol;
        
        sol=sol+(-1)^(iter)*x^(2*iter)/factorial(2*iter);
        
        iter=iter+1;
    
    if sol ~=0
        
        ea=abs((sol-solold)/sol)*100;
    
    end
    
    if ea <= es | iter >=maxit , break, end

    end
    cosx=sol;
        fprintf('absolute relative error: %d\n number of iterations: %d ',ea, iter);
    end

```
