# route_as

## 3.6 为路由命名
~~~
通过 :as 选项，我们可以为路由命名：
~~~

```rb
get 'exit', to: 'sessions#destroy', as: :logout
```
