# concern-routing:
~~~
路由 concern 用于声明公共路由，公共路由可以在其他资源和路由中重复使用。
定义路由 concern 的方式如下：
~~~

```rb
# 路由 concern 用于声明公共路由，公共路由可以在其他资源和路由中重复使用。定义路由 concern 的方式如下
concern :commentable do
  resources :comments
end
 
concern :image_attachable do
  resources :images, only: :index
end

# 我们可以在资源中使用已定义的路由 concern，以避免代码重复，并在路由间共享行为：
resources :messages, concerns: :commentable
resources :articles, concerns: [:commentable, :image_attachable]

```

## 等价于：
```rb
resources :messages do
  resources :comments
end

resources :articles do
  resources :comments
  resources :images, only: :index
end
```


