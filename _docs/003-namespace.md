# namespace:

## 2.6 控制器命名空间和路由
~~~
有时我们会把一组控制器放入同一个命名空间中。
最常见的例子，是把和管理相关的控制器放入 Admin:: 命名空间中。
为此，我们可以把控制器文件放在 app/controllers/admin 文件夹中，然后在路由文件中作如下声明：
~~~

```rb
namespace :admin do
  resources :articles, :comments
end
```
![](https://ws2.sinaimg.cn/large/0069RVTdgy1fubdi2f7z5j317u0mcdm5.jpg)

## 如果不要要 /admin 这个在前面
~~~
如果想把 /articles 路径（不带 /admin 前缀） 映射到 Admin::Articles 控制器上，可以这样声明：
~~~

```rb
scope module: 'admin' do
  resources :articles, :comments
end

# 对于单个资源的情况，还可以这样声明：
resources :articles, module: 'admin'

# 如果想把 /admin/articles 路径映射到 Articles 控制器上（不带 Admin:: 前缀），可以这样声明：
scope '/admin' do
  resources :articles, :comments
end

# 对于单个资源的情况，还可以这样声明：
resources :articles, path: '/admin/articles'
```